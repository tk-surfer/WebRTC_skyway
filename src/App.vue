<script setup lang="js">
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'
import { ref, reactive } from 'vue';
import axios from 'axios';

const show = ref(false);

const openByMouse = () => {
  // 本来は、listから表示する
  show.value = true;
}

const closeByMouse = () => {
  show.value = false;
}

const url = "http://localhost:3000";

const api = () => {
  axios.post('http://localhost:3000/authenticate',{
    "channelName" : "a",
    "memberName" : "a",
    "sessionToken" : "4CXS0f19nvMJBYK05o3toTWtZF5Lfd2t6Ikr2lID"
  })
  .then((response) => console.log(response))
  .catch((error) => console.log(error));
};


</script>

<template>
  <header>
    <v-app-bar app dark>
      <div class="content has-text-centered">
        <div class="columns is-gapless">
            <div class="column">
              <nav>
                <RouterLink to="/">
                  <figure class="image is-15x15">
                    <img src="@/assets/img/ミライを想像する.jpg">
                  </figure>
                </RouterLink>
              </nav>
            </div>

            <div class="column">
              <button class="button is-primary" @click="api"></button>

            </div>
            
            <div class="column">
              <a v-on="{mouseover:openByMouse}">機能</a>
                <div class="menu" v-show="show" v-on:mouseleave="closeByMouse">
                  <ul>
                    <nav class="breadcrumb" aria-label="breadcrumbs">
                      <RouterLink to="/video">Video</RouterLink><br>
                      <RouterLink to="/video">Video</RouterLink><br>
                      <RouterLink to="/video">Video</RouterLink>

                    </nav>
                  </ul>
                </div>
            </div>

            <div class="column">
              <div class="level-item">
                <div class="field has-addons">
                  <p class="control">
                    <input class="input" type="text" placeholder="Find a post">
                  </p>
                  <p class="control">
                    <button class="button">
                      Search
                    </button>
                  </p>
                </div>
              </div>
            </div>
        </div>
      </div>
    </v-app-bar>
  </header>

  <RouterView />

  <footer class="footer">
    <div class="content has-text-centered">
      <p>
          <strong>Copyright(C) T.K, Ltd. All Rights Reserved.</strong>
      </p>
    </div>
  </footer>
</template>


<style scoped>

header {
  border-bottom: solid 5px;
}

.menu {
  background-color: rgba(8, 199, 126, 0.973);
  border: grid;
  position: fixed;
  z-index: 1;
  text-align: center;
}

ul {
  text-align: center;
}


nav {
  font-size: 40px;
  text-align: center;
}

footer {
  background-color: rgba(80, 83, 83, 0.301);
}

</style>
