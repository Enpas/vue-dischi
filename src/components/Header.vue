<template>
  <header>
    <div class="logo-box">
        <img src="../assets/img/logo.png" alt="Logo">
    </div>
    <div class="offset-9 col-1">
      <select name="album" id="generis" placeholder="Generi">
         <option
        @click="resetStr()" 
        value="tutti">
          Tutti
        </option>
        <option
        v-for="(gender, index) in genders" :key="index"
        @click="writeStr(gender.genre)"
        value="gender.genre">
        {{gender.genre}}
        </option>
      </select>
    </div>
  </header>
</template>

<script>
export default {
 name:'Header',
 data(){
   return{
     strSearchGender:'',
   } 
 },
 props:{
   genders:Array
 },

  methods:{
      writeStr(object){
        this.$emit("searchGender",this.strSearchGender = object);
        console.log(this.strSearchGender);
      },
      resetStr(){
          this.strSearchGender ="";
          this.writeStr('');
      }
   }
}
</script>

<style lang="scss" scoped>

header{
  height: 70px;
  background-color:#2E3A46;
  display: flex;
  align-items: center;
  .logo-box{
    margin-left: 15px;
    img{
      height: 50px;
    };
  };
  select{
    background-color:#1E2D3B;
    padding: 5px 30px;
    margin-left: 30px;
    color: #FFFFFF;
    border: none;
    border-radius: 5px;
    option{
      background-color: #3b4550;
    };
  };
}
</style>