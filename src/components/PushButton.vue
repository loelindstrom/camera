<script setup>

</script>

<template>
    <button class="button-side">
        <span class="button-top"></span>
    </button>
</template>

<style scoped>  
.button-side {
    background: hsl(40deg 100% 32%);
    border-radius: 50%;
    border: none;
    padding: 0;
    cursor: pointer;
    outline-offset: 4px;
}
.button-top {
    display: block;
    padding: 10% 15%;
    border-radius: 50%;
    font-size: 1.25rem;
    background: hsl(45deg 100% 47%);
    color: white;
    transform: translateY(-6px);
}

.button-side:active .button-top {
    transform: translateY(-2px);
}
</style>
