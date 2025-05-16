<template>
  <ApiApiTable :headers="headers">
    <template #row="{ props, item }">
      <tr v-bind="props">
        <ApiNameCell :name="kebabCase(item.name)" :new-in="item.newIn" section="props" />

        <td>
          <ApiPrismCell :code="item.formatted" />
        </td>

        <td>
          <ApiPrismCell :code="item.default" />
        </td>

        <td>
          <AppMarkdown
            v-if="localeStore.locale !== 'eo-UY'"
            :content="item.description"
            class="mb-0"
          />
          <span v-else>{{ item.description }}</span>
        </td>
      </tr>
    </template>
  </ApiApiTable>
</template>

<script setup lang="ts">
  const localeStore = useLocaleStore()
  const headers = ['name', 'type', 'default', 'description']
</script>
