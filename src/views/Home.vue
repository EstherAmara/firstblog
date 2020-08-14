<template>
  <div class="home container">
    <div class="row">
      <img alt="Vue logo" src="../assets/undraw_celebrating_bol5.svg" style="height: 80vh" class="col-xl-7">
      <div class="col-xl-5">
        <div class="mdown text-left">
          <div> Welcome to my first blog with Vue!!!!! </div>
          <div> In this Blog I shall fetch posts from an external api and display it with comments. <br/> Click on the button below to get started</div>
          <router-link class="btn btn-outline-purple mt-2" to="/posts"> Explore Posts <i class="fa fa-angle-double-right"></i> </router-link>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'

// export default {
//   name: 'Home',
//   components: {
//     HelloWorld
//   }
// }
</script>

<style>
  .btn-outline-purple {
    border-color: #663399;
    color: #663399;
  }
  .btn-outline-purple:hover {
    background-color: #663399;
    color: #fafafa;
    border: none;
  }
  .btn-outline-purple:active {
    background-color: rebeccapurple;
  }
  .mdown {
    margin-top: 30%;
    font-family: 'Baloo Tamma 2', cursive;
    font-size: 1.2em;
  }
</style>
