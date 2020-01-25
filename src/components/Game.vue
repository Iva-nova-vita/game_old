<template>
  <div id="playing_field" >
    <h1>Какое слово начинается на букву:</h1>
    <div id="letter">{{lettersArr[index]}}</div>
    <div class="flex_container">
     
      <div class="images" >
         
        <!--  <img :src="`./static/${lettersArr[index]}.jpeg`" alt=""> -->
        <img :src="require(`../assets/${lettersArr[imagesArr[0]]}.jpeg`)" :indexOfArr="`${imagesArr[0]}`" v-on:click="check" >
      </div>
      <div class="images" >
          <img :src="require(`../assets/${lettersArr[imagesArr[1]]}.jpeg`)" :indexOfArr="`${imagesArr[1]}`" v-on:click="check">

      </div>
      <div class="images">
<img :src="require(`../assets/${lettersArr[imagesArr[2]]}.jpeg`)" :indexOfArr="`${imagesArr[2]}`"  v-on:click="check">
      </div>
    </div>
  </div>
</template>
<script>
export default {
  props: {
    indexOfArr: {
      type: Number,
    },
    
  },
  data() {
    return {
        lettersArr: ['А', 'Б', 'В', 'Г', 'Д', 'Е', 'Ё', 'Ж', 'З', 'И', 'Й', 'К', 'Л', 'М', 'Н', 'О', 'П', 'Р', 'С', 'Т', 'У', 'Ф', 'Х', 'Ц', 'Ч', 'Ш', 'Щ', 'Э', 'Ю', 'Я'],
    index: 0,
    imagesArr: [1, 3, 0],
    
    };
   
  },
  
methods: {
  check(e) {
      console.log(e);
    if (this.index==e.target.attributes[1].value) {
this.changeLetter();
    } else return;
  },
changeLetter() {
  if (this.index<29) {
    this.index++;}
    else {
      this.index=0;
    }
    this.changeImagesArr();
    
},
changeImagesArr() {
 let randomIndex1 = Math.floor(Math.random() * this.lettersArr.length);
 let randomIndex2 = Math.floor(Math.random() * this.lettersArr.length);
 if (randomIndex1!==this.index && randomIndex2!==this.index && randomIndex1!==randomIndex2) {
this.imagesArr.splice(0, 3, randomIndex1, randomIndex2, this.index);
this.imagesArr.sort();
 } else (this.changeImagesArr());
}
},

};
  
</script>
<style lang="scss">
@import url("https://fonts.googleapis.com/css?family=Pacifico&display=swap&subset=cyrillic");
#playing_field {
  height: 97vh;
  text-align: center;
  background: url(../assets/bgrnd.jpg);
  background-repeat: no-repeat;
  background-size: cover;

  h1 {
    color: red;
    font-family: "Pacifico", cursive;
    font-size: 66px;
    margin: 0px;
    padding-top: 90px;
  }
}

#letter {
  // height: 150px;
  // width: 150px;
  // border: 5px brown solid;
  // border-radius: 100%;
  color: red;
  margin: 0 auto;
  font-family: "Times New Roman", Times, serif;
  font-size: 126px;

  text-transform: uppercase;
  //background: url(../assets/sky.jpeg);
}
.flex_container {
  display: flex;
  width: 80%;
  margin: 0 auto;
  margin-top: 20px;
}
.images {
  height: 250px;
  width: 250px;
  border: 5px brown solid;
  color: red;
  margin: 0 auto;
  img {
      width: 250px;
      height: 250px;
  }
}
</style>