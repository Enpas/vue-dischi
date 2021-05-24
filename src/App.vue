<template>
  <div id="app">
    <div v-if="!loading">
      <Header/>
      <Main 
      :discs="arrDiscs"/>
    </div>
    <div v-else>
      <Loading str="Spotify" />
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import Header from './components/Header.vue';
import Main from './components/Main.vue';
import Loading from './components/Loading.vue';


export default {
  name: 'App',
  data(){
    return{
      axios,
      arrDiscs:[],
      loading:true,
    }
  },
  created(){
    axios.get('https://flynn.boolean.careers/exercises/api/array/music')
    .then(res =>{
      console.log(res.data.response);
      this.arrDiscs = res.data.response;
      this.loading = false;
    })
    .catch(err =>{
      console.log(err);
    })
  },
  components: {
    Header,
    Main,
    Loading

    
  },
  
}
</script>

<style lang="scss">
@import '@/assets/style/general.scss';
</style>