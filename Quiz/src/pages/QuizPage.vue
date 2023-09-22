<template>
  <q-page>
    <q-card>
      <q-card-title>Веб-технологии</q-card-title>
      <q-card-subtitle>Ответьте на вопросы</q-card-subtitle>
      <q-card-main>
        <q-list>
          <q-item v-for="(question, index) in questions" :key="index">
            <q-item-section>
              <div class="text-h6">{{ question.text }}</div>
              <div v-if="question.image" class="q-mt-md">
                <q-img :src="question.image" />
              </div>
              <div class="q-mt-md">
                <q-radio v-model="question.answer" :options="question.options" />
              </div>
            </q-item-section>
          </q-item>
        </q-list>
      </q-card-main>
      <q-card-actions>
        <q-btn label="Проверить ответы" @click="checkAnswers" />
      </q-card-actions>
    </q-card>
  </q-page>
</template>

<script>
export default {
  data() {
    return {
      questions: [
        {
          text: "Что такое HTML?",
          options: [
            { label: "Язык разметки гипертекста", value: "a" },
            { label: "Язык программирования", value: "b" },
            { label: "Язык стилей", value: "c" },
          ],
          answer: null,
        },
        {
          text: "Что такое CSS?",
          options: [
            { label: "Язык стилей", value: "a" },
            { label: "Язык программирования", value: "b" },
            { label: "Язык разметки гипертекста", value: "c" },
          ],
          answer: null,
        },
        {
          text: "Что такое JavaScript?",
          options: [
            { label: "Язык программирования", value: "a" },
            { label: "Язык разметки гипертекста", value: "b" },
            { label: "Язык стилей", value: "c" },
          ],
          answer: null,
        },
      ],
    };
  },
  methods: {
    checkAnswers() {
      let correctAnswers = 0;
      this.questions.forEach((question) => {
        if (question.answer === "a") {
          correctAnswers++;
        }
      });
      this.$q.dialog({
        title: "Результаты",
        message: `Вы ответили правильно на ${correctAnswers} из ${this.questions.length} вопросов`,
        ok: "Ок",
      });
    },
  },
};
</script>

Этот код создает страницу с тремя вопросами про веб-технологии (HTML, CSS и JavaScript). Каждый вопрос имеет три варианта ответа, из которых нужно выбрать один. После того, как пользователь ответит на все вопросы, он может нажать кнопку "Проверить ответы", чтобы узнать, сколько ответов он дал правильно. Результаты выводятся в диалоговом окне.
