<script setup>
import { ref } from 'vue'
import SearchBar from './components/SearchBar.vue'
import RoleFilter from './components/RoleFilter.vue'
import AgentSelec from './components/AgentSelec.vue'
import AgentDetails from './components/AgentDetails.vue'
import AgentListe from './components/AgentList.vue'
import Header from './components/header.vue'
import Footer from './components/footer.vue'

const agents = ref(AgentListe)

// États UI
const query = ref('')
const role = ref('Tous') 
const selectedAgent = ref(null)

function handleSelect(agent) {
  selectedAgent.value = agent
}

function clearSelection() {
  selectedAgent.value = null
}

function matchAgent(a) {
  const matchText =
    a.name.toLowerCase().includes(query.value.toLowerCase()) ||
    a.role.toLowerCase().includes(query.value.toLowerCase())

  const matchRole = role.value === 'Tous' ? true : a.role === role.value
  return matchText && matchRole
}
</script>

<template>
  <Header title="Valorant Agents/Stats"></Header>
  <div class="container">
    <h1>Mini-guide des agents de Valorant</h1>

    <div class="toolbar">
      <SearchBar v-model="query" placeholder="Rechercher un agent ou un rôle…" />
      <RoleFilter v-model="role" />
    </div>

    <AgentSelec
      :agents="agents.filter(matchAgent)"
      @select="handleSelect"
    />

    <AgentDetails
      v-if="selectedAgent"
      :agent="selectedAgent"
      @close="clearSelection"
    />

    <p v-if="agents.filter(matchAgent).length === 0" class="empty">
      Aucun agent ne correspond à la recherche.
    </p>
  </div>
  <Footer footer__title="Projet par Nicolas Lefebvre & Sahan Toksoz"></Footer>
</template>

<style scoped>
.container {
  max-width: 1000px;
  margin: 32px auto;
  padding: 0 16px;
  min-height: 700px;
}
h1 {
  text-align: center;
  margin-bottom: 16px;
}
.toolbar {
  display: flex;
  gap: 12px;
  flex-wrap: wrap;
  justify-content: center;
  margin-bottom: 16px;
}
.empty {
  text-align: center;
  color: #777;
  margin-top: 24px;
}
</style>
