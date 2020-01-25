<template>
  <div class="images" > 
    <!--  <img :src="`./static/${lettersArr[index]}.jpeg`" alt=""> -->
    <img :src="require(`../assets/${letter}.jpeg`)" :indexOfArr="index" v-on:click="check" >
  </div>
</template>

<script>
export default {
  props: {
    letter: {
      type: String,
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
  }
}
</script>
