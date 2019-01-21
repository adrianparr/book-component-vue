<template>
  <div class="book">
    <div class="book__rect">
      <h3 class="book__title">{{ title }}</h3>
      <h4 class="book__author">{{ author }}</h4>
      <img class="book__img" :src="imgSrc" alt="Cover of book">
      <h5 class="book__age">aimed at <span>{{ ageGroup }}</span></h5>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Book',
  props: {
    id: Number,
    title: String,
    author: String,
    coverImage: String,
    ageGroup: String,
    coverImagePath: String
  },
  computed: {
    imgSrc: function() {
      return this.coverImagePath + this.coverImage
    }
  }
}
</script>

<style scoped>
.book {
  background-image: url(~@/assets/shelf.svg);
  background-repeat: no-repeat;
  background-size: contain;
  background-position: bottom;
  margin: 0 auto;
  max-width: 320px;
  padding-bottom: 38px;
}
.book__rect {
  background-color: #e4dfda;
  margin: 0 auto;
  max-width: 267px;
  text-align: left;
}
.book__title {
  font-size: 1.3rem;
  line-height: 1.1;
  margin-bottom: 0.3rem;
  margin-top: 0;
  padding: 1rem 1rem 0 1rem;
}
.book__author {
  font-size: 1rem;
  font-weight: 500;
  margin: 0;
  padding: 0 1rem;
}
.book__img {
  display: block;
  margin: 0 auto;
  transform: translateY(17px);
}
.book__age {
  background-color: #efece9;
  font-size: 1rem;
  font-weight: 500;
  padding: 1rem 1rem 0.6rem 1rem;
  margin: 0;
}
.book__age span {
  font-size: 1.5rem;
  font-weight: 800;
}
</style>
