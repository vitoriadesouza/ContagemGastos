<template>

<div>

<h2>Lista do dia</h2>

<table class="table">

<thead>
<tr>
<th>Descrição</th>
<th>Categoria</th>
<th>Valor</th>
<th></th>
</tr>
</thead>

<tbody>

<tr v-for="item in despesas" :key="item.id">

<td>{{item.title}}</td>
<td>{{item.category}}</td>
<td>R$ {{item.value}}</td>

<td>
<button class="delete" @click="$emit('removerDespesa',item.id)">X</button>
</td>

</tr>

</tbody>

</table>

</div>

</template>

<script setup>

defineProps({
despesas:Array
})

</script>

<style scoped>

h2{
margin-bottom:10px;
font-size:18px;
}

.delete{
background:#ef4444;
color:white;
border:none;
padding:5px 8px;
border-radius:4px;
cursor:pointer;
}

.delete:hover{
background:#dc2626;
}
table{
overflow-x:auto;
display:block;
}
</style>