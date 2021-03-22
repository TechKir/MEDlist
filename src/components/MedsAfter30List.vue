<template>
    <ul class="list">
        <li class="list__li"><h2>Drugs administered after the age of 30:</h2></li>
        <li class="list__li" v-for="med in meds30Plus" :key="med">
            <div class="list__div">
                <p> {{med.name}} <span>strength: {{med.strength}}</span></p>
            </div>
        </li>
    </ul>
</template>

<script>        
export default {
    name: 'MedsAfter30List',
    props: {
        meds30Plus: Array
    },
}
</script>