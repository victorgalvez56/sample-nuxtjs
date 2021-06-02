
 <template>
  <div class="page-loader" v-if="!isloaded">
    <img src="kakashi.png"  class="cube" alt="">
  </div> 
</template>

<script>
  export default {
    data: () => {
      return {
        isloaded: false
      }
    },
    mounted() {
      document.onreadystatechange = () => {
        if (document.readyState == "complete") { 
          this.isloaded = true;
        } 
      }
    },
  }
</script>

<style lang="scss" scoped>
  .page-loader {
    display: flex;
    justify-content: center;
    align-items: center;
    position: fixed;
    top: 0;
    left: 0;
    width: 100vw;
    height: 100vh;
    background-color: black;
    z-index: 999;
  }
  // -----------------------------------------------------
  .cube{
    width: 150px;
    height:150px;
    margin-right: 10px;
  }
  // -----------------------------------------------------
 @-webkit-keyframes cube /* Safari and Chrome */ {
  from {
    -webkit-transform: rotate(0deg);
    -o-transform: rotate(0deg);
    transform: rotate(0deg);
  }
  to {
    -webkit-transform: rotate(360deg);
    -o-transform: rotate(360deg);
    transform: rotate(360deg);
  }
}
@keyframes cube {
  from {
    -ms-transform: rotate(0deg);
    -moz-transform: rotate(0deg);
    -webkit-transform: rotate(0deg);
    -o-transform: rotate(0deg);
    transform: rotate(0deg);
  }
  to {
    -ms-transform: rotate(360deg);
    -moz-transform: rotate(360deg);
    -webkit-transform: rotate(360deg);
    -o-transform: rotate(360deg);
    transform: rotate(360deg);
  }
}
.cube {
  -webkit-animation: cube 2s linear infinite;
  -moz-animation: cube 2s linear infinite;
  -ms-animation: cube 2s linear infinite;
  -o-animation: cube 2s linear infinite;
  animation: cube 2s linear infinite;
}
</style>