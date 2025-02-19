<template>
  <div id="app">
    <div class="form-section">
      <h2>Создание релиза</h2>
      <label>Версия и платформа:</label>
      <input type="text" v-model="version" placeholder="Введите версию и платформу" />

      <label>Дата и время релиза:</label>
      <input type="text" v-model="releaseDateTime" placeholder="Введите предполагаемую дату и время выката фичи"/>

      <label>Описание фич:</label>
      <div v-for="(feature, index) in features" :key="index">
        <FeatureRow
            @update-feature="updateFeature(index, $event)"
            @remove-feature="removeFeature(index)"
        />
      </div>
      <button @click="addFeature">Добавить описание фичи</button>

      <label>Влияние на окружение:</label>
      <textarea v-model="impact" placeholder="Что изменится для клиента?"></textarea>

      <label>Изменения в бизнес-процессах:</label>
      <textarea v-model="businessChanges" placeholder="Какие изменения внутри компании?"></textarea>

      <label>Напишите ники заинтересованных лиц:</label>
      <input type="text" v-model="nick" placeholder="Например: @test, @gachiMan" />

      <a class="guide-link" href="https://confluence.eltc.ru/pages/viewpage.action?pageId=290108200#id-16.[%D0%98%D0%BD%D1%81%D1%82%D1%80%D1%83%D0%BA%D1%86%D0%B8%D1%8F]%D0%A1%D0%BE%D0%B7%D0%B4%D0%B0%D0%BD%D0%B8%D0%B5%D0%B7%D0%B0%D0%B4%D0%B0%D1%87%D0%B2JIRA-%D0%9E%D0%BF%D0%B8%D1%81%D0%B0%D0%BD%D0%B8%D0%B5%D1%80%D0%B5%D0%BB%D0%B8%D0%B7%D0%BE%D0%B2" target="_blank">
        <button class="guide-button">Гайд по заполнению</button>
      </a>
    </div>
    <div class="final-release">
      <h3>Итоговый релиз:</h3>
      <div v-html="formattedReleaseText"></div>
    </div>
  </div>
</template>

<script>
import FeatureRow from './FeatureRow.vue';

export default {
  components: { FeatureRow },
  data() {
    return {
      version: '',
      releaseDateTime: '',
      impact: '',
      businessChanges: '',
      nick: '',
      features: [{ icon: '✳️', description: '' }]
    };
  },
  computed: {
    formattedReleaseText() {
      const featureDescriptions = this.features.map(
          (feature) => `- ${feature.icon} ${feature.description}`
      ).join('<br />');

      return `
        <strong>❗️ Релиз</strong> ${this.version} <br />
       ${this.releaseDateTime} <br />
        <strong>Описание фич:</strong><br />${featureDescriptions} <br />
        <strong>Влияние на окружение:</strong> <br /> ${this.impact} <br />
        <strong>Изменения в бизнес-процессах:</strong> <br /> ${this.businessChanges} <br />
       <br />  ${this.nick}
      `;
    }
  },
  methods: {
    addFeature() {
      this.features.push({icon: '✳️', description: ''});
    },
    updateFeature(index, feature) {
      this.features[index] = feature;
    },
    removeFeature(index) {
      if (this.features.length > 1) {
        this.features.splice(index, 1);
      }
    },
  }
};
</script>

<style>
.form-section {
  width: 500px;
  flex: 1;
  padding-right: 30px;
}

.final-release {
  font-size: 18px;
  width: 500px;
  padding: 20px;
  color: #F8F8FF;
  background-color: #355E3B;
  border-radius: 8px;
  border: 1px solid #ccc;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
}

.final-release h3 {
  font-size: 22px;
  color: #F8F8FF;
}

.final-release div {
  margin-top: 10px;
  line-height: 1.6;
}

.final-release p {
  margin: 5px 0;
}

textarea {
  min-height: 120px;
  resize: vertical;
}

textarea::placeholder {
  color: #adadb3;
  font-weight: 600;
}

.guide-link {
  text-decoration: none;
}

.guide-button {
  display: block;
  margin: 0 auto;
  background-color: #ff6666;
  text-decoration: none;
  color: white;
  padding: 10px 20px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

.guide-button:hover {
  background-color: #e05d5d;
}
</style>
