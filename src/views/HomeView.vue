<script setup lang="js">
import TheWelcome from '../components/TheWelcome.vue'
</script>

<template>
  <div class="content has-text-centered">
    <figure class="image is-100x100">
      <img src="@/assets/img/person-3062271_640.jpg">
      <p>技術をもっと自由に</p>
    </figure>

    <p class="title is-3 is-spaced">
      こちらのWebサイトは、WebRTCの特設サイトです。<br>
      こちらのサイトを使用して、様々な機能を使用することができます。
    </p>
  </div>

</template>

<style>
.title {
  color: rgba(12, 102, 161, 0.541);
  background-color: rgba(67, 78, 74, 0.123);
  margin-top: 10px;
  padding: 20px;
}

.image {
  margin-top: 10px;
  position: relative;
}

figure p{
  position: absolute;
  top:40%;
  left:10%;
  font-size:300%;
  color: rgb(0, 4, 255);
  background-color: rgba(0, 255, 255, 0.418);
  font-family: "游ゴシック";
  padding:20px;
  margin:0;
}

</style>