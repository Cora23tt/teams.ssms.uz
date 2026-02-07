<script setup>
import AppCard from '../components/AppCard.vue';
import BaseButton from '../components/BaseButton.vue';
import AppIcon from "../components/AppIcon.vue";

const weather = {
  location: 'Ваш город',
  temperature: '+12°',
  condition: 'Переменная облачность',
  humidity: '48%',
  wind: '3 м/с',
  pressure: '758 мм рт. ст.'
};

const rates = [
  {code: 'EUR', value: '0.92', delta: '+0.01'},
  {code: 'GBP', value: '0.79', delta: '-0.01'},
  {code: 'JPY', value: '148.3', delta: '+0.4'}
];
</script>

<template>
  <div class="view view--home">
    <section class="stagger">

      <AppCard title="Не можете присутствовать?">
        <div class="rate-grid">
          <BaseButton size="lg">
            <AppIcon name="flag_2" :fill="1" :weight="700" color="primary"/>
            Отпроситься
          </BaseButton>
          <BaseButton size="lg">
            <AppIcon name="warning" :fill="1" :weight="700" color="primary"/>
            Предупредить
          </BaseButton>
        </div>
      </AppCard>

      <AppCard title="Запрос к HR">
        <p class="muted">Оставьте свой запрос к HR тут, рассмотрим в ближайшее время!</p>
        <BaseButton variant="filled">Написать</BaseButton>
      </AppCard>

      <AppCard title="Погода" subtitle="Локальный прогноз" meta="Демо">
        <div class="weather">
          <div>
            <p class="weather__location">{{ weather.location }}</p>
            <p class="weather__condition">{{ weather.condition }}</p>
          </div>
          <p class="weather__temp">{{ weather.temperature }}</p>
        </div>
        <div class="info-list">
          <div class="info-list__row">
            <span>Влажность</span>
            <strong>{{ weather.humidity }}</strong>
          </div>
          <div class="info-list__row">
            <span>Ветер</span>
            <strong>{{ weather.wind }}</strong>
          </div>
          <div class="info-list__row">
            <span>Давление</span>
            <strong>{{ weather.pressure }}</strong>
          </div>
        </div>
        <p class="muted">Подключите API, чтобы показывать реальные данные.</p>
      </AppCard>

      <AppCard title="Курс валют" subtitle="Базовая валюта: USD" meta="Демо">
        <div class="rate-grid">
          <div v-for="rate in rates" :key="rate.code" class="rate-card">
            <span class="rate-card__code">{{ rate.code }}</span>
            <strong class="rate-card__value">{{ rate.value }}</strong>
            <span class="rate-card__delta">{{ rate.delta }}</span>
          </div>
        </div>
        <p class="muted">Данные локальные. Добавьте обновление из API и кэш.</p>
      </AppCard>
    </section>
  </div>
</template>
