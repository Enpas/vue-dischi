<template>
  <header>
    <div class="logo-box">
        <img src="../assets/img/logo.png" alt="Logo">
    </div>
  </header>
</template>

<script>
export default {
 name:'Header'
}
</script>

<style lang="scss" scoped>

header{
  height: 70px;
  background-color:#2E3A46 ;
  display: flex;
  align-items: center;
  .logo-box{
    margin-left: 15px;
    img{
      height: 50px;
    };
  };
}
</style>