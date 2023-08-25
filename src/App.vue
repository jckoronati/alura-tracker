<template>
  <main class="columns is-gapless is-multiline">
    <div class="column is-one-quarter">
      <SideBar />
    </div>
    <div class="column is-three-quarter">
      <TimerForm />
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import SideBar from './components/SideBar.vue';
import TimerForm from './components/TimerForm.vue';

export default defineComponent({
  name: 'App',
  components: {
    SideBar,
    TimerForm
  }
});
</script>

<style></style>