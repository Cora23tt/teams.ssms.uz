<script setup>
import AppCard from '../components/AppCard.vue';

const air = {
  index: 42,
  status: 'Хорошее',
  pm25: '8 μg/m³',
  pm10: '18 μg/m³',
  o3: '40 ppb'
};
</script>

<template>
  <div class="view view--air">
    <section class="stagger">
      <AppCard title="Качество воздуха" subtitle="Индекс AQI" meta="Демо">
        <div class="air-index">
          <div class="air-index__value">{{ air.index }}</div>
          <div class="air-index__status">{{ air.status }}</div>
        </div>
        <div class="info-list">
          <div class="info-list__row">
            <span>PM2.5</span>
            <strong>{{ air.pm25 }}</strong>
          </div>
          <div class="info-list__row">
            <span>PM10</span>
            <strong>{{ air.pm10 }}</strong>
          </div>
          <div class="info-list__row">
            <span>O₃</span>
            <strong>{{ air.o3 }}</strong>
          </div>
        </div>
        <p class="muted">Добавьте источники датчиков и историю измерений.</p>
      </AppCard>
    </section>
  </div>
</template>
