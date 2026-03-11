<template>

<div class="summary">
Total do dia: <strong>R$ {{ total }}</strong>
</div>

</template>

<script setup>

defineProps({
total:Number
})

</script>

<style scoped>

.summary{
margin-top:15px;
font-size:16px;
background:#f1f5f9;
padding:10px;
border-radius:6px;
text-align:right;
}

</style>