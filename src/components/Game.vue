<template>
  <div id="playing_field" >
    <h1>Какое слово начинается на букву:</h1>
    <div id="letter">{{lettersArr[index]}}</div>
    <div class="flex_container">
     
      <card v-for="i in 3" :key="i"
       :letters="lettersArr" :index="imagesArr[i-1]" :check="check"
      />

    </div>
  </div>
</template>
<script>
import Card from "@/components/GameCard"

export default {
  props: {
    indexOfArr: {
      type: Number,
    },
  },
  components: {
    card: Card,
  },
  data() {
    return {
        lettersArr: ['А', 'Б', 'В', 'Г', 'Д', 'Е', 'Ё', 'Ж', 'З', 'И', 'Й', 'К', 'Л', 'М', 'Н', 'О', 'П', 'Р', 'С', 'Т', 'У', 'Ф', 'Х', 'Ц', 'Ч', 'Ш', 'Щ', 'Э', 'Ю', 'Я'],
    index: 0,
    imagesArr: [1, 3, 0],
    
    };
   
  },
  
methods: {
  check(e, index) {
      console.log(e);
      if (this.index == index) {
e.target.classList.add('animateTrue')
        setTimeout(this.changeLetter, 1000);
        setTimeout(() => e.target.classList.remove('animateTrue'), 1000);
      } else {
        e.target.classList.add('animateFalse')
        setTimeout(() => e.target.classList.remove('animateFalse'), 1000);
      }
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
  background: url(../assets/images/bgrnd.jpg);
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
  color: red;
  margin: 0 auto;
  font-family: "Times New Roman", Times, serif;
  font-size: 126px;
  text-transform: uppercase;

}
.flex_container {
  display: flex;
  width: 80%;
  margin: 0 auto;
  margin-top: 20px;
}
.images {
  height: 270px;
  width: 270px;
  margin: 0 auto;
  img {
      width: 250px;
      height: 250px;
      border: 7px rgb(150, 93, 86) solid;
      border-radius: 15px;
  }
}

.animateTrue {
  animation: animBorderTrue 0.2s linear infinite;
}
@keyframes animBorderTrue {
  0% {
    border-color: rgb(47, 201, 68);

  }
  50% {
    border-color: rgb(156, 231, 173) ;
    
  }
  100% {
    border-color: rgb(47, 201, 68);
   
  }
}

.animateFalse {
  animation: animBorderFalse 0.2s linear infinite;
}
@keyframes animBorderFalse{
  0% {
    border-color: rgb(240, 36, 9);
  }
  50% {
    border-color: rgb(238, 160, 160) ;
  }
  100% {
    border-color: rgb(240, 36, 9);
  }
}
</style>