<template>
  <div class="feature-row">
    <select v-model="selectedIcon" @change="updateFeature">
      <option value="✳️">✳️ Новая фича</option>
      <option value="❇️">❇️ Новый пакет</option>
      <option value="☢️">☢️ Чистка кода</option>
      <option value="⚙️">⚙️ Исправление бага</option>
      <option value="⚠️">⚠️ Исправление ошибок</option>
      <option value="⛔️">⛔️ Синтаксис</option>
    </select>
    <input type="text" v-model="featureDescription" @input="updateFeature" placeholder="Описание фичи" />
    <button @click="$emit('remove-feature')">Удалить</button>
  </div>
</template>

<script>
export default {
  props: ['value'],
  data() {
    return {
      selectedIcon: '✳️',
      featureDescription: ''
    };
  },
  methods: {
    updateFeature() {
      this.$emit('update-feature', {icon: this.selectedIcon, description: this.featureDescription});
    }
  }
};
</script>

<style>
.feature-row {
  display: flex;
  align-items: center;
  margin-bottom: 8px;
}

select, input {
  margin-right: 8px;
}
</style>
