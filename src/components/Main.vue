<template>
  <main class="d-flex">
    <section class="discs-container col-10 offset-1">
      <div 
      v-for="(disc, index) in discs" :key="index"
      class="disc-box col-12 col-md-6 col-lg-2 p-3 m-0 p-lg-0 m-lg-3 text-center">

        <div class="background-box p-3">
          <img class="img-fluid" :src="disc.poster" :alt="disc.title">
          <h3>{{disc.title}}</h3>
          <h4>{{disc.author}}</h4>
          <h4>{{disc.year}}</h4>
        </div>

      </div>
    </section>

  </main>
</template>

<script>
export default {
 name:'Main',
 props:{
   discs: Array
 }
};
</script>

<style lang="scss" scoped>

main{
  padding: 90px 0;
  .discs-container{
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    .disc-box{
      .background-box{
        background-color:#2E3A46 ;
        display: flex;
        flex-direction: column;
        justify-content: space-between;
        align-items: center;
        height: 100%;
        img{
          width: 100%;
        };
        h3{
          color: #FFF;
          font-size: 20px;
          text-transform: uppercase;
          font-weight: bold;
          margin:20px 0 10px;
        };
        h4{
          font-size: 15px;
          color:#737771; 
          margin-bottom: 0;
           &:last-child{
            font-size: 13px
          };            
        };
      };
    };
  };
};
</style>