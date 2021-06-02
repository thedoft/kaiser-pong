<template>
  <main class="main">
    <h1 class="main__title">Kaizer-pong</h1>
    <Points />
    <button class="main__button" @click="btnClick">Статистика</button>
    <Table :show="show" />
  </main>
</template>

<script>
import Points from './Points.vue';
import Table from './Table.vue';
import sound from '@/assets/ping-pong.mp3';

export default {
  name: 'Main',
  components: { Points, Table },
  data() {
    return {
      show: false,
    };
  },
  methods: {
    btnClick() {
      this.show = !this.show;

      if (this.show) {
        this.audio && this.audio.pause();
        this.audio = new Audio(sound);
        this.audio.play();
      }
    },
  },
};
</script>

<style>
.main {
  padding: 60px 0;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.main__title {
  text-transform: uppercase;
  font-weight: 900;
  font-size: 64px;
  line-height: 1.2;
  margin: 0 auto 60px;
}

.main__button {
  margin: 40px 0;
  border: none;
  background: transparent;
  padding: 0;
  text-decoration: underline;
  cursor: pointer;
}

@media screen and (max-width: 767px) {
  .main {
    padding: 30px 0;
  }

  .main__title {
    margin-bottom: 30px;
  }

  .main__button {
    margin: 20px 0;
  }
}
</style>
