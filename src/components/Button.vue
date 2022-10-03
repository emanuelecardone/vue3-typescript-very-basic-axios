<template>
  <a href="#" @click="setCurrentPage(newPage)" class="btn btn-success">{{ msg }}</a>
</template>

<script lang="ts">
import { Options, Vue } from 'vue-class-component';

@Options({
  name: 'Button',
  props: {
    msg: String,
    currentPage: Object,
    newPage: String
  },
  methods: {
    setCurrentPage: function(nextPage: string){
      this.currentPage.page = nextPage;
    }
  }
})

export default class Button extends Vue {
  msg!: string;
  currentPage!: {page: string};
  setCurrentPage!: ( nextPage: string) => void;
  direction!: string;
  newPage!: string;
}
</script>

<style scoped lang="scss">
  
</style>