<template>
  <div class="app">

    <Header @mudarFiltro="filter = $event" />

    <div class="layout">

      <FormularioDespesa
        @adicionarDespesa="addExpense"
        @limparTudo="clearAll"
      />

      <div class="panel">
        <ListaDespesas
          :despesas="filtered"
          @removerDespesa="removeExpense"
        />

        <TotalDespesas
          :total="total"
        />
      </div>

    </div>

  </div>
</template>

<script setup>
import { ref, computed } from 'vue'

import Header from './components/Header.vue'
import FormularioDespesa from './components/FormularioDespesa.vue'
import ListaDespesas from './components/ListaDespesas.vue'
import TotalDespesas from './components/TotalDespesas.vue'

const expenses = ref([
  { id: 1, title: 'Cafe', value: 6, category: 'food' },
  { id: 2, title: 'Onibus', value: 4.5, category: 'transport' },
  { id: 3, title: 'Lanche', value: 12, category: 'food' }
])

const filter = ref('all')

const filtered = computed(() => {
  if (filter.value === 'all') return expenses.value
  return expenses.value.filter(e => e.category === filter.value)
})

const total = computed(() =>
  expenses.value.reduce((sum, item) => sum + Number(item.value || 0), 0)
)

function addExpense(expense) {
  expenses.value.push({
    id: Date.now(),
    ...expense
  })
}

function removeExpense(id) {
  expenses.value = expenses.value.filter(e => e.id !== id)
}

function clearAll() {
  if (!confirm('Tem certeza?')) return
  expenses.value = []
}
</script>