<script setup>


</script>

<template>
    
<div class="searchbar">
    
<form action="" class="search">
    <slot></slot>
    </form>
</div>
        
</template>

<style scoped>


.searchbar {
    border-radius: 15px;
    padding: 0 10px;
    background: #FEFEFE;
    box-shadow: 0px 16px 30px -10px rgba(70, 96, 187, 0.20);
}

.search {
    display: flex;
    align-items: center;
    justify-content: center;
    font-family: Space Mono;
    
}


</style>