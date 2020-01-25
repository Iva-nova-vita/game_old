<template>
  <div class="images" >
    <img :src="letterImgPath" v-on:click="check($event, index)" >
  </div>
</template>

<script>
export default {
  props: {
    letters: {
      type: Array,
      required: true,
    },
    index: {
      type: Number,
      required: true,
    },
    check: {
      type: Function,
      required: true,
    }
  },
  computed: {
    letter() {
      return this.letters[this.index];
    },
    letterImgPath() {
      return require(`../assets//images/letters/${this.letter}.jpeg`);
    },
  }
}
</script>
