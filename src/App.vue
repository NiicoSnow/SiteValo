<script setup>
import { ref } from 'vue'
import SearchBar from './components/SearchBar.vue'
import RoleFilter from './components/RoleFilter.vue'
import AgentSelec from './components/AgentSelec.vue'
import AgentDetails from './components/AgentDetails.vue'
import AgentListe from './components/AgentListe.vue'

// Données "mockées" (exemple minimal)
const agents = ref(AgentListe)

// États UI
const query = ref('')
const role = ref('Tous') // Tous | Duelist | Initiator | Sentinel | Controller
const selectedAgent = ref(null)

// Quand on clique une carte, on sélectionne l'agent
function handleSelect(agent) {
  selectedAgent.value = agent
}

// Réinitialiser la sélection
function clearSelection() {
  selectedAgent.value = null
}

// Fonction utilitaire de filtrage (utilisée dans le template)
function matchAgent(a) {
  const matchText =
    a.name.toLowerCase().includes(query.value.toLowerCase()) ||
    a.role.toLowerCase().includes(query.value.toLowerCase())

  const matchRole = role.value === 'Tous' ? true : a.role === role.value
  return matchText && matchRole
}
</script>

<template>
  <div class="container">
    <h1>Mini-guide des agents (Valorant)</h1>

    <!-- Barre de recherche et filtre -->
    <div class="toolbar">
      <SearchBar v-model="query" placeholder="Rechercher un agent ou un rôle…" />
      <RoleFilter v-model="role" />
    </div>

    <!-- Liste d'agents filtrée -->
    <AgentSelec
      :agents="agents.filter(matchAgent)"
      @select="handleSelect"
    />

    <!-- Panneau de détails -->
    <AgentDetails
      v-if="selectedAgent"
      :agent="selectedAgent"
      @close="clearSelection"
    />

    <!-- Message si aucun résultat -->
    <p v-if="agents.filter(matchAgent).length === 0" class="empty">
      Aucun agent ne correspond à la recherche.
    </p>
  </div>
</template>

<style scoped>
.container {
  max-width: 900px;
  margin: 32px auto;
  padding: 0 16px;
  font-family: system-ui, -apple-system, Segoe UI, Roboto, sans-serif;
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
