<template>
  <div id="app">
    <main>
      <section>
        <Header/>
        <List :patients="patients" :meds="meds"/>
        <footer class="footer">&#169; Copyright by TechKir</footer>
      </section>
    </main>
  </div>
</template>

<script>
import Header from './components/Header';
import List from './components/List'

export default {
  name: 'App',
  components: {
    Header,
    List
  },
  data(){
    return {
      patients:[],
      meds:[]
    }
  },
  beforeCreate() {
      fetch('https://cerber.pixel.com.pl/api/patients')
        .then(async res => this.patients= await res.json())
        .catch(err => console.error(err))

      fetch('https://cerber.pixel.com.pl/api/medicine')
        .then(async res => this.meds= await res.json())
        .catch(err => console.error(err))
  },
  // methods: {
  //   createList: function () {
  //     this.patients.map(patient => <li>{patient.name + patient.lastName} drugs:{this.meds.forEach(med => med.patientIds.includes(patient.id) ? med.medicationName : null)}</li>)
  //   }
  // }
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
  background-image: linear-gradient(to right bottom, #c7dcd9, #9dd3c7, #73c9af, #4abd93, #18b171);
}

.footer {
  text-align: center;
  font-size: 0.7em;
  background-color: whitesmoke;
  padding: 0.5em 0;
}

</style>
