<template>
  <div class="container">
    <div v-for="(movie, i) in data" :key="i" class="item">
      <figure>
        <img :src="`${movie.imgUrl}`" :alt="movie.title">
      </figure>
      <div class="info">
        <h3 class="bg-yellow" >{{ movie.title }}</h3>
        <p>개봉 : {{ movie.year }} </p>
        <p>장르 : {{ movie.category }}</p>
        <button @:click="$emit('increaseLike')">좋아요 </button>
        <span>{{ movie.like }}</span>
        <p>
          <button @:click="isModal=true; selectedMovie=i">상세보기</button>
        </p>
      </div>
    </div>
  </div>
  <h1>영화정보</h1>

</template>
<script>
export default {
    name: "MoviesComponent",
    props: {
      data: Array
    }
}
</script>
<style >
    .container {
      padding: 20px;
    }
</style>