<template>
<div class="header">

<h1>Controle de Gastos</h1>

<div class="filtros">
<button class="small-btn" @click="$emit('mudarFiltro','all')">Tudo</button>
<button class="small-btn" @click="$emit('mudarFiltro','food')">Comida</button>
<button class="small-btn" @click="$emit('mudarFiltro','transport')">Transporte</button>
<button class="small-btn" @click="$emit('mudarFiltro','other')">Outros</button>
</div>

</div>
</template>

<style scoped>

.header{
display:flex;
justify-content:space-between;
align-items:center;
margin-bottom:20px;
padding-bottom:10px;
border-bottom:2px solid #ddd;
}

.header h1{
font-size:22px;
margin:0;
}

.filtros{
display:flex;
gap:8px;
}
.filtros{
display:flex;
gap:8px;
flex-wrap:wrap;
}
</style>