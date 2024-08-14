<template>
  <div @:click="toggleFavorite">
    <h2>
      {{ foodName }}
      <img src="https://www.w3schools.com/vue/img_quality.svg" v-show="foodIsFavorite">
    </h2>
    <p>{{ foodDesc }}</p>
  </div>
</template>

<script>
export default {
  data() {
    return {  
      foodIsFavorite: this.isFavorite
    }
  },
  // props: ['foodName', 'foodDesc', 'isFavorite']
  props: {
    foodName: {
      type: String,
      requried: true
    },
    foodDesc: {
      type: String,
      requried: false,
      default: "This is the default description.",
      validator: function (value) {
        if (20 < value.length && value.length < 50) {
          return true;
        }
        else {
          return false;
        }
      }
    },
    isFavorite: {
      type: Boolean,
      requried: false,
      default: false,
    }
  },
  methods: {
    toggleFavorite() {
      this.foodIsFavorite = !this.foodIsFavorite;
    }
  }
};
</script>

<style>
img {
  height: 1.5em;
  float: right;
}
</style>