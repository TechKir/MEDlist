<template>
    <header class="header">
        <h1 class="header__title"><span>MED</span>list</h1>
        <nav class="header__nav">
            <button class="header__btn">Meds for patients after 30 years old</button>
            <button class="header__btn">Mens Meds</button>
            <button class="header__btn">Show All Data</button>
        </nav>
    </header>
</template>

<script>
export default {
    name: 'Header',
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