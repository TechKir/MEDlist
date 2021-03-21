<template>
    <ul class="list">
        <!-- eslint-disable vue/no-use-v-if-with-v-for -->
        <li class="list__li"><h2>Patients:</h2><h2>Medicines:</h2></li>
        <li class="list__li" v-for="patient in patients" :key="patient.id">
            <div class="list__div">
                <p>{{ patient.name + " " + patient.lastName}}</p>
                <span>adress: {{patient.adress}}</span>
                <span>phone: {{patient.phoneNumber}}</span>
                <span>age: {{patient.age}}</span>
            </div>

            <div class="list__div">
                
                <p v-for="med in meds" :key="med.id" v-if="med.patientIds.includes(patient.id)"> {{med.medicationName}}</p>
            </div>
        </li>
    </ul>
</template>

<script>        
export default {
    name: 'List',
    props: {
        patients: Array,
        meds: Array
    },
}
</script>

<style>
.list h2 {
    font-size: 1em;
    font-weight: 700;
}
.list__li {
    display: flex;
    justify-content: space-between;
    padding: 1.5em;
    border-bottom: whitesmoke 1px solid;
}
.list div:nth-child(2) {
    width:16vw;
}

.list__li h2:nth-child(2){
    width:16vw;
}

.list li:first-child {
    background-color: #c7dcd9;
    padding: 0.5em 1.5em;
}

.list__div span {
    display: block;
    padding: 0.2em 0;
    font-size: 0.8em;
}
</style>