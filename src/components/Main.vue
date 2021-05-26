<template>
  <main>
    <div class="container-fluid">
        <div class="row justify-content-center">
            <FilterDiscs
            :genres="genres"
            @selectGenre="selecting"
            @searchAuthor="searching"
            />
        </div>

        <div class="row ep-disc-container justify-content-center">
          <Disc
            v-for="(disc, index) in filteredDiscs" :key="index"
            :disc="disc"
          />
        </div>
    </div> 
  </main>
</template>

<script>
import FilterDiscs from '@/components/FilterDiscs.vue'
import Disc from '@/components/Disc.vue'
import axios from 'axios';
export default {
  name: 'Main',
  components: {
    FilterDiscs,
    Disc
  },
  data() {
    return {
      axios,
      discs: [],
      genres: [],
      optSelect: '1',
      authSearch: ''
    }
  },
  methods: {
    selecting(opt) {
      this.optSelect = opt;
    },
    searching(text) {
      this.authSearch = text;
    }, 
  },
  computed: {
    filteredDiscs() {
      if (this.optSelect === '1' && this.authSearch === '') {
        return this.discs;
      }
      if (this.optSelect != '1') {
        return this.discs.filter(disc => disc.genre === this.optSelect);
      }
      return this.discs.filter(disc => disc.author.toLowerCase().includes(this.authSearch.toLowerCase()))
    },
  },
  created() {
    axios.get('https://flynn.boolean.careers/exercises/api/array/music')
      .then(res => {
        this.discs = res.data.response;
        this.loading = false;
        res.data.response.forEach(disc => {
          if (!this.genres.includes(disc.genre)) {
            this.genres.push(disc.genre);
          }
        });
      })
      .catch(err => {
        console.log(err);
      })
  }
}
</script>

<style lang="scss" scoped>
  .ep-disc-container {
    padding: 50px 10%;
  }
</style>