<template>

<div class="panel">

<h2>Nova despesa</h2>

<input v-model="title" class="input" placeholder="Descrição" />
<input v-model="value" class="input" placeholder="Valor" />
<input v-model="category" class="input" placeholder="Categoria" />

<div class="row">
<button class="small-btn" @click="enviar">Adicionar</button>
<button class="small-btn danger" @click="$emit('limparTudo')">Limpar tudo</button>
</div>

</div>

</template>

<script setup>
import { ref } from 'vue'

const emit = defineEmits(['adicionarDespesa','limparTudo'])

const title = ref('')
const value = ref('')
const category = ref('')

function enviar(){

if(!title.value.trim() || !value.value.trim()){
alert('Preencha tudo')
return
}

emit('adicionarDespesa',{
title:title.value,
value:value.value,
category:category.value || 'other'
})

title.value=''
value.value=''
category.value=''

}
</script>

<style scoped>

h2{
margin-top:0;
font-size:18px;
margin-bottom:10px;
}

.danger{
background:#dc2626;
}

.danger:hover{
background:#b91c1c;
}

</style>