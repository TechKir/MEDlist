<template>
    <ul class="list">
        <li class="list__li"><h2>Medicines for men:</h2></li>
        <li class="list__li" v-for="maleMed in maleMeds" :key="maleMed.name">
            <div class="list__div">
                <p> {{maleMed}}</p>
            </div>
        </li>
    </ul>
</template>

<script>        
export default {
    name: 'MenMedsList',
    props: {
        maleMeds: Array,
        meds: Array
    },
}
</script>