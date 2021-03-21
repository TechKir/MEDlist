<template>
    <header class="header">
        <h1 class="header__title"><span>MED</span>list</h1>
        <nav class="header__nav">
            <button @click="showMeds30Plus" class="header__btn">Drugs administered after the age of 30</button>
            <button @click="showMenMeds" class="header__btn">Mens Meds</button>
            <button @click="showList" class="header__btn">Patients List</button>
        </nav>
    </header>
</template>

<script>
export default {
    name: 'Header',
    props: {
        showMenMeds:Function,
        showList:Function,
        showMeds30Plus:Function,
    },
}
</script>

<style>
.header {
    display:flex;
    justify-content: space-between;
    align-items: center;
    padding: 1.5em;
    background: whitesmoke;
}

.header__title span {
    color:#4abd93;
}

.header__btn{
    margin-left:1em;
    display: inline-block;
    border: none;
    padding: 1rem 2rem;
    text-decoration: none;
    background: #4abd93;
    color: #ffffff;
    font-family: sans-serif;
    font-size: 1rem;
    cursor: pointer;
    text-align: center;
    transition: background 250ms ease-in-out, 
    transform 150ms ease;
    -webkit-appearance: none;
    -moz-appearance: none;
}
</style>