<template>
  <div id="app">
    <postForm />
    <hr>
    <h1>{{ countPosts }}</h1>
    <div class="post" v-for="post in validPosts" :key="post.id">
      <h2>{{ post.title }}</h2>
      <p>{{ post.body }}</p>
    </div>
  </div>
</template>

<script>
import { mapGetters, mapActions } from 'vuex';
import postForm from './components/postForm.vue';

export default {
  name: 'App',
  computed: mapGetters(['validPosts', 'countPosts']),
  methods: mapActions(['fetchPosts']),
  components: { postForm },
  async mounted() {
    this.fetchPosts();
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 60px auto;
  width: 400px;
}

.post {
  border: 1px solid #ccc;
  border-radius: 5px;
  margin-bottom: 1rem;
  padding: 5px;
}
</style>
