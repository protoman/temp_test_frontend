<script setup lang="ts">
import WelcomeItem from './WelcomeItem.vue'
import DocumentationIcon from './icons/IconDocumentation.vue'
import ToolingIcon from './icons/IconTooling.vue'
import EcosystemIcon from './icons/IconEcosystem.vue'
</script>

<template>
  <WelcomeItem>
    <template #icon>
      <DocumentationIcon />
    </template>
    <template #heading>Projects</template>

    <router-link :to="{ name: 'listProjects' }" replace>List Projects #1</router-link><br />
    <a href="https://vuejs.org/" target="_blank" rel="noopener">Create Project</a><br />
  </WelcomeItem>

  <WelcomeItem>
    <template #icon>
      <ToolingIcon />
    </template>
    <template #heading>Activities</template>

    <a href="https://vitejs.dev/guide/features.html" target="_blank" rel="noopener"
      >Create activity</a
    ><br />
  </WelcomeItem>

  <WelcomeItem>
    <template #icon>
      <EcosystemIcon />
    </template>
    <template #heading>Client</template>

    <a href="https://pinia.vuejs.org/" target="_blank" rel="noopener">Create Project</a>
  </WelcomeItem>
</template>
