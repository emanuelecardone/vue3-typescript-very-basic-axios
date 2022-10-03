<template>
  <div class="start">
    <h2 class="text-success">Start</h2>
    <ButtonsWrapper :buttonsTexts="['Back', 'Ok']" :buttonsActions="['home', 'start']" :currentPage="currentPage" />
    <a href="#" class="btn btn-success" @click="showPics()">Show pics</a>
    <a href="#" class="btn btn-success" @click="hidePics()">Hide pics</a>
    <div class="photos_wrapper" v-if="clicked">
      <template v-if=" (photos?.length ?? 0) > 0">
        <div v-for="pic in photos" :key="pic.id" class="pic_card bg-success text-white my-5">
          <h4>{{ pic.title }}</h4>
          <img :src="pic.thumbnailUrl" :alt="pic.title">
        </div>
      </template>
      <h4 v-else class="text-success">Loading...</h4>
    </div>
  </div>
</template>

<script lang="ts">
import { Options, Vue } from 'vue-class-component';
import ButtonsWrapper from './ButtonsWrapper.vue';
import axios from 'axios';

@Options({
  name: 'Start',
  components: {
    ButtonsWrapper,
    currentPage: Object
  },
  props: {
    currentPage: Object
  },
  data(){
    return {
      clicked: false,
      photos: null
    };
  },
  methods: {
    showPics: async function(){
      this.clicked = true;
      const { data } = await axios.get('https://jsonplaceholder.typicode.com/photos');
      this.photos = data;
    },
    hidePics: function(){
      this.clicked = false;
    }
  }
})

export default class Start extends Vue{
  currentPage!: {page: string};
  clicked!: boolean;
  showPics!: () => void;
  hidePics!: () => void;
  photos!: null | Array<{
    albumId: number;
    id: number;
    thumbnailUrl: string;
    title: string;
    url: string;
  }>
}
</script>

<style lang="scss" scoped>
  .pic_card{
    border-radius: 10px;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    align-items: center;
    padding: 1rem;
  }
</style>