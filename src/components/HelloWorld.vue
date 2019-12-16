<template>
  <div class="hello">
    <h3>New Cat</h3>
    <form @submit.prevent="addCat">
      <input type="text" placeholder="name" v-model="newCat.name" />
      <input type="text" placeholder="imgUrl" v-model="newCat.imgUrl" />
      <button type="submit">Meow</button>
    </form>
    <div class="cats">
      <div class="cat" v-for="cat in cats" :key="cat.name">
        <img :src="cat.imgUrl" alt="" />
        <h1 :class="{ angry: cat.pets > 10 }">Name: {{ cat.name }}</h1>
        <h2>Pets: {{ cat.pets }}</h2>
        <h3 v-if="cat.pets > 10">Careful he is Angry!</h3>
        <p v-else>Pet Away M'lord' or M'lady'</p>
        <button @click="cat.pets++">Pet</button>
        <button @click="autoPet(cat)">Begin AutoPet</button>
      </div>
    </div>
  </div>
</template>

<script>
import { log } from "util";
export default {
  name: "HelloWorld",
  data() {
    return {
      newCat: {
        name: "",
        imgUrl: ""
      },
      cats: [
        {
          name: "Mr Snibbley",
          pets: 0,
          imgUrl: "https://i.huffpost.com/gen/191974/CAT-TOP-HAT.jpg"
        },
        {
          name: "Mr Snibbley Jr",
          pets: 0,
          imgUrl:
            "http://www.wcyt.org/wp-content/uploads/2012/09/fancy-cat1.jpg"
        },
        {
          name: "Mrs Snibbley",
          pets: 0,
          imgUrl:
            "https://media.istockphoto.com/photos/white-maine-coon-girl-cat-wearing-golden-bow-on-head-sitting-up-with-picture-id871380166?k=6&m=871380166&s=612x612&w=0&h=bHdiwk6kD0_SduCFp7ur8dx1nOlTIulMtvJYpG2zQe0="
        },
        {
          name: "Mrs Snibbley Jr",
          pets: 0,
          imgUrl:
            "https://821872984941288636.weebly.com/uploads/3/9/1/9/39199659/1968045_orig.jpg"
        }
      ]
    };
  },
  methods: {
    autoPet(cat) {
      setInterval(() => {
        cat.pets++;
        this.meow();
      }, 1000);
    },
    meow() {
      console.log("meow");
    },
    addCat() {
      debugger;
      let cat = {
        name: this.newCat.name,
        imgUrl: this.newCat.imgUrl,
        pets: 0
      };
      this.cats.unshift(cat);
      this.newCat = {
        name: "",
        imgUrl: ""
      };
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.angry {
  color: red;
}

.cat img {
  max-height: 10rem;
}
</style>
