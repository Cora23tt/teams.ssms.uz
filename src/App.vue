<script setup>
import {computed, ref} from 'vue';
import BottomNav from './components/BottomNav.vue';
import HomeView from './views/HomeView.vue';
import AirView from './views/AirView.vue';
import EmptyView from './views/EmptyView.vue';

const tabs = [
  {id: 'home', label: 'Главная', icon: 'home'},
  {id: 'air', label: 'Качество воздуха', icon: 'air'},
  {id: 'map', label: 'Карта', icon: 'map'},
  {id: 'settings', label: 'Настройки', icon: 'settings'}
];

const activeTab = ref('home');

const viewMap = {
  home: HomeView,
  air: AirView,
  map: EmptyView,
  settings: EmptyView
};

const currentView = computed(() => viewMap[activeTab.value] || EmptyView);
const pageTitle = computed(() => {
  const item = tabs.find((tab) => tab.id === activeTab.value);
  return item ? item.label : 'Приложение';
});
</script>

<template>
  <div class="app">
    <header class="top-bar">
      <div>
        <p class="top-bar__eyebrow">SSMS Teams</p>
        <h1 class="top-bar__title">{{ pageTitle }}</h1>
      </div>
      <div class="top-bar__badge">Light</div>
    </header>

    <main class="content" role="main">
      <component :is="currentView"/>
    </main>

    <BottomNav v-model="activeTab" :items="tabs"/>
  </div>
</template>
