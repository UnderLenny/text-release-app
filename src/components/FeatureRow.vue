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
  text-align: center;
  margin-bottom: 15px;
  border-radius: 8px;
}

.feature-row select {
  width: 100px;
  margin-right: 15px;
}

.feature-row input {
  flex: 1;
}

.feature-row button {
  background-color: #ff6666;
  margin-left: 10px;
  margin-bottom: 10px;
}

.feature-row button:hover {
  background-color: #e05d5d;
}
</style>
