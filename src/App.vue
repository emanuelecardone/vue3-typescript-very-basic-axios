<template>
  <Home v-if="currentPage.page === 'home'" :currentPage="currentPage" msg="Welcome"/>
  <Start v-else-if="currentPage.page === 'start'" :currentPage="currentPage"/>
</template>

<script lang="ts">
import { Options, Vue } from 'vue-class-component';
import Home from './components/Home.vue';
import Start from './components/Start.vue';

@Options({
  components: {
    Home,
    Start
  },
  data(){
    return {
      currentPage: {
        page: 'home'
      }
    };
  }
})
export default class App extends Vue {
currentPage!: { page: string; };
}
</script>

<style lang="scss">
@import './style/general';

  #app{

    & > div{
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      gap: 1rem;
    }
  }
</style>
