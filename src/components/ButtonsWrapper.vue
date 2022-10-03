<template>
  <div class="buttons_wrapper d-flex justify-content-center align-items-center p-3">
    <Button v-for="(button, index) in buttonsTexts" :key="button" :msg="button" :currentPage="currentPage" :newPage="buttonsActions[index]" />
  </div>
</template>

<script lang="ts">
import { Options, Vue } from 'vue-class-component';
import Button from './Button.vue';

@Options({
  name: 'ButtonsWrapper',
  props: {
    buttonsTexts: Array,
    buttonsActions: Array,
    currentPage: Object
  },
  components: {
    Button
  }
})
export default class ButtonsWrapper extends Vue{
  buttonsTexts!: Array<string>;
  buttonsActions!: Array<string>;
  currentPage!: {page: string};
}
</script>

<style lang="scss" scoped>
  .buttons_wrapper{
    gap: 1rem;
  }
</style>