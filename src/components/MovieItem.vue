<template>
  <li v-show="!isFiltered || isLike">
    <a :href="`https://movie.douban.com/subject/${movie.id}`" target="_blank">
      <img class="poster" :src="movie.images.small" :alt="movie.title">
      <p v-text="movie.title"></p>
      <p v-text="`${movie.year} | ${movie.rating.average}`"></p>
    </a>
    <a @click="isLike = !isLike" class="like" href="javascript:void(0);">
      <img v-show="isLike" class="like-icon" src="../assets/heart-in.png" alt="like">
      <img v-show="!isLike" class="like-icon" src="../assets/heart-out.png" alt="like">
      like
    </a>
  </li>
</template>

<script>
export default {
  name: 'MovieItem',
  props: ['movie', 'isFiltered'],
  data () {
    return {
      isLike: false
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
li {
  box-sizing: border-box;
  color: #2c3e50;
  display: inline-block;
  font-size: 0.8rem;
  list-style-type: none;
  padding: 5px 10px 10px;
  text-decoration: none;
  vertical-align: top;
  width: calc(100% / 3);
  max-width: 200px;
}
.poster {
  width: 100%;
}
.like {
  border: dotted 1px #2e963d;
  border-radius: 2px;
  color: #2e963d;
  display: block;
  font-size: 1rem;
  line-height: 1;
  margin: 5px;
  padding: 3px 0;
}
.like-icon {
  height: 1rem;
  vertical-align: top;
}
</style>
