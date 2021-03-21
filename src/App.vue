<template>
  <div id="app">
    <main>
      <section>
        <Header :showList="showList" :showMenMeds="showMenMeds" :showMeds30Plus="showMeds30Plus"/>
        <List v-if="isListActive" :patients="patients" :meds="meds"/>
        <MenMedsList v-if="isMenMedsActive" :maleMeds="maleMeds" :meds="meds"/>
        <MedsAfter30List v-if="isMeds30PlusActive" :meds30Plus="meds30Plus"/>
        <footer class="footer">&#169; Copyright by TechKir</footer>
      </section>
    </main>
  </div>
</template>

<script>
import Header from './components/Header';
import List from './components/List';
import MenMedsList from './components/MenMedsList';
import MedsAfter30List from './components/MedsAfter30List';

export default {
  name: 'App',
  components: {
    Header,
    List,
    MenMedsList,
    MedsAfter30List
  },
  data(){
    return {
      patients:[],
      patients30PlusIds:[],
      meds:[],
      malePatients:[],
      maleIds:[],
      maleMeds:[],
      meds30Plus:[],
      isListActive:true,
      isMenMedsActive:false,
      isMeds30PlusActive:false
    }
  },
  methods: {
    showList: function (){
      this.isListActive=true;
      this.isMenMedsActive=false;
      this.isMeds30PlusActive=false;
    },
    showMenMeds: function (){
      this.isMenMedsActive=true;
      this.isListActive=false;
      this.isMeds30PlusActive=false;
    },
    showMeds30Plus: function (){
      this.isMeds30PlusActive=true;
      this.isListActive=false;
      this.isMenMedsActive=false;
    }
  },
  beforeCreate() {
      fetch('https://cerber.pixel.com.pl/api/patients')
        .then(async res => this.patients= await res.json())
        .then(patients => {
          patients.filter(patient => patient.age>=30 && this.patients30PlusIds.push(patient.id))
          return this.malePatients  = patients.filter(patient => patient.gender==='male' && patient)
          })
        .then(patients => {
          this.maleIds = patients.map(patient=>patient.id)
          return this.maleIds.filter(e=> e!==undefined)})
        .catch(err => console.error(err))

      fetch('https://cerber.pixel.com.pl/api/medicine')
        .then(async res => this.meds= await res.json())
        .then( meds => {
          meds.forEach( med => {
            med.patientIds.every( patientId => {
              if(this.maleIds.includes(patientId)){
                this.maleMeds.push(med.medicationName)
                return false
              }
              return true
              })
          }) 

          meds.forEach( med => {
            med.patientIds.every( patientId => {
              if(this.patients30PlusIds.includes(patientId)){
                this.meds30Plus.push(med.medicationName)
                return false
              }
              return true
              })
          }) 
        })
        .catch(err => console.error(err))
  },
}

</script>

<style>
*{
  margin:0;
  padding:0;
  box-sizing: border-box;
}

body {
  font-family: 'Open Sans', sans-serif;
  font-size: 18px;
  background-image: linear-gradient(to right bottom, #c7dcd9, #9dd3c7, #73c9af, #4abd93, #18b171);
}

.footer {
  text-align: center;
  font-size: 0.7em;
  background-color: whitesmoke;
  padding: 0.5em 0;
}
</style>
