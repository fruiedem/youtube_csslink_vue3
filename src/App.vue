<template>
  <h1>영화정보</h1>
  <div v-for="(movie, i) in data" :key="i" class="item">
    <figure>
      <img :src="`${movie.imgUrl}`" :alt="movie.title">
    </figure>
    <div class="info">
      <h3 class="bg-yellow" >{{ movie.title }}</h3>
      <p>개봉 : {{ movie.year }} </p>
      <p>장르 : {{ movie.category }}</p>
      <button @:click="increaseLike(i)">좋아요 </button>
      <span>{{ movie.like }}</span>
      <p>
        <button @:click="isModal=true; selectedMovie=i">상세보기</button>
      </p>
    </div>

  </div>
  <!-- 모달창 추가 -->
  <div class="modal" v-if="isModal">
    <div class="inner">
      <h3>{{ data[selectedMovie].title }}</h3>
      <p>영화 상세정보</p>
      <p> {{ data[selectedMovie].details }}</p>
      <button @:click="isModal=false">닫기</button>
    </div>
  </div>
</template>

<script>
import data from './assets/movies';
console.log(data);
  export default {
    name: 'App',
    data() {
      return {
        isModal: false,
        data: data,
        selectedMovie: 0
      }
    },
    methods: {
      increaseLike(i) {
        this.data[i].like += 1;
      }
    }
  }
</script>

<style>
  * {
    box-sizing: border-box;
    margin: 0;
  }

  body {
    max-width: 768px;
    margin: 0 auto;
    padding: 20px;
  }

  h1, h2, h3 {
    margin-bottom: 1rem;
  }

  p {
    margin-bottom: 0.5 rem;
  }

  button {
    margin-right: 10px;
    margin-top: 1rem;
  }

  .item {
    width: 100%;
    border: 1px solid #ccc;
    display: flex;
    margin-bottom: 20px;
    padding: 1rem;
  }
  .item figure {
    width: 30%;
    margin-right: 1rem;
  }

  .item img {
    width : 100%;
  }
  
  .item .info {
    width: 100%;
  }

  .modal {
    background: rgba(0,0,0,0.7);
    position: fixed;
    left: 0;
    top: 0;
    width: 100%;
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .modal .inner {
    background: #fff;
    width: 80%;
    padding: 20px;
    border-radius: 10px;
  }
</style>
