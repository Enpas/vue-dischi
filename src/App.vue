<template>
  <div id="app">
      <div v-if="!loading">
        <Header/>
        <Main />
      </div>
      <div v-else>
        <Loading str="Spotify" />
      </div>
  </div>
</template>

<script>
import Header from '@/components/Header.vue';
import Main from '@/components/Main.vue';
import Loading from './components/Loading.vue';
import axios from 'axios';

export default {
  name: 'App',
  components: {
    Header,
    Main,
    Loading
  },

  data(){
    return{
      axios,
      loading:true
    }
  },

   created() {
    axios.get('https://flynn.boolean.careers/exercises/api/array/music')
      .then(res => {
        this.records = res.data.response;
        this.loading = false;
      })
      .catch(err => {
        console.log(err);
      })
  }
}
</script>

<style lang="scss">
@import 'assets/style/general.scss';
@import '~bootstrap/scss/bootstrap';
</style>  