<template>
  <div class="images" > 
    <!--  <img :src="`./static/${lettersArr[index]}.jpeg`" alt=""> -->
    <img :src="require(`../assets/${letter}.jpeg`)" v-on:click="check($event, index)" >
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
  }
}
</script>
