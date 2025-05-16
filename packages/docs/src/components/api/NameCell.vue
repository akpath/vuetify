<template>
  <td :id="`${section}-${name.replace('$', '')}`">
    <div class="d-inline-flex align-center">
      <kbd class="name-item">
        <AppLink :href="href" class="font-weight-bold text-body-2">
          {{ name }}
        </AppLink>
      </kbd>
    </div>
  </td>
</template>

<script setup>
  const props = defineProps({
    section: String,
    name: String,
    newIn: String,
  })

  const href = computed(() => {
    return `#${props.section}-${props.name.replace('$', '')}`
  })
</script>

<style scoped>
  .app-link {
    margin-left: -14px;
  }

  .app-link :deep(.v-icon) {
    opacity: 0;
    margin: 0;
  }

  .app-link:hover :deep(.v-icon) {
    opacity: 1;
  }
</style>
