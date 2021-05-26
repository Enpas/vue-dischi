<template>
  <div class="ep-filter-container">
    <section>
      <select 
        class="form-select" 
        aria-label="Genre selection"
        v-model="selectedValue"
        @change="filterSelection()"
      >
        <option selected value="1">Clicca qui per selezionare un genere</option>
        <option
          v-for="(genre, index) in genres" :key="index"
          :value="genre">{{ genre }}
        </option>
      </select>

      <input 
        type="text" 
        placeholder="Cerca per autore"
        class="form-control"
        v-model="authorSearch"
        @keyup="filterAuthor()"
      >

    </section>
  </div>
</template>

<script>
export default {
  name: 'FilterDiscs',
  props: {
    genres: Array
  },
  data() {
    return {
      selectedValue: '1',
      authorSearch: ''
    }
  },
  methods: {
    filterSelection() {
      this.$emit('selectGenre', this.selectedValue);
    },
    filterAuthor() {
      this.$emit('searchAuthor', this.authorSearch);
    }
  }
}
</script>

<style lang="scss" scoped>
  @import '../assets/style/vars.scss';
  .ep-filter-container {
    position: relative;
    width: 25%;
    min-width: 400px;
    padding: 0;
    section {
      position: absolute;
      top: -75px;
      left: 40px;
    }
    select {
      border: 0;
      border-radius: 0;
      outline: 0;
      color: #FFF;
      text-transform: uppercase;
      font-size: 1rem;
      font-weight: 500;
      background-color: $header-color;
    }
    input {
      background-color: $header-color;
      border: 0;
      border-radius: 0;
      outline: 0;
      color: #FFF;
      &::placeholder {
        color: #FFF;
      }
    }
  }
</style>