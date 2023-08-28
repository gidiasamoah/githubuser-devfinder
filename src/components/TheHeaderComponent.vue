<script setup>

</script>

<template>
    <header>
        <h2 class="logo">devfinder</h2>
        
        <button class="toggler">
           <span class="text"> </span><span><img class="sun" src="../assets/dark.png" alt=""></span>
        </button>
    </header>
</template>

<style scoped>
header{
    display: flex;
    justify-content: space-between;
    align-items: center;
}
header.logo {
    color: #222731;
font-family: Space Mono;
font-size: 26px;
font-style: normal;
font-weight: 700;
line-height: normal;
}

.text{
    color:#0000;
    font-size: 13px;
    font-weight: 700;
    letter-spacing: 2.5px;
}
    
button{
    background-color: transparent;
    border: none;
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 10px;
    padding: 0;
}

</style>