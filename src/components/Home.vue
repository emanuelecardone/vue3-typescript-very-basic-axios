<template>
  <div class="home">
    <h1 class="text-success">{{ msg }}</h1>
    <ButtonsWrapper :buttonsTexts="['Start']" :buttonsActions="['start']" :currentPage="currentPage"  />
  </div>
</template>

<script lang="ts">
import { Options, Vue } from 'vue-class-component';
import ButtonsWrapper from './ButtonsWrapper.vue';

@Options({
  name: 'Home',
  components: {
    ButtonsWrapper
  },
  props: {
    msg: String,
    currentPage: Object
  },
  methods: {
    setCurrentPage: function(direction: string){
      direction === 'ahead' ? this.currentPage.page = 'start' : null;
    }
  }
})
export default class Home extends Vue {
  msg!: string;
  currentPage!: {page: string};
  setCurrentPage!: (direction: string) => void;
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

</style>
