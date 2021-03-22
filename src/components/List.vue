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
                <!-- TODO: replacte v-if with something different-->
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