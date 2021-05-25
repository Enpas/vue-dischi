<template>
  <div id="app">
    <div v-if="!loading">
      <Header 
      :genders="arrGenders"
      @searhGender = 'searchingGender'
      />
      <Main 
      :discs="arrDiscsGenders"/>
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
      arrGenders:[],
      strGender:'',
      arrDiscsGenders:[],
    }
  },
  
  created(){
    axios.get('https://flynn.boolean.careers/exercises/api/array/music')
    .then(res =>{
      this.arrDiscs = res.data.response;

      this.arrDiscsGenders = this.arrDiscs;

      this.arrGenders = res.data.response.filter( item =>{
        if(!this.arrGenders.includes(item.genre)){
          return this.arrGenders.push(item.genre)
        }
        /* console.log(this.arrGenders); */
      });
      this.loading = false;
    })
    .catch(err =>{
      console.log(err);
    })
  },

  computed:{
    

  },

  methods:{

    searchingGender(text){
      this.strGender = text;

      this.arrDiscsGenders = this.arrDiscs.filter( item =>{
        if(this.strGender === item.genre){
          return true
        }else if(this.strGender === ''){
          return this.arrDiscsGenders = this.arrDiscs
        }
      });

    }
    
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