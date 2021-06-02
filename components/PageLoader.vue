
 <template>
  <div class="page-loader" v-if="!isloaded">
    <img src="code.gif"  class="cube" alt="">
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
        this.activate()
    },
    methods: {
  activate() {
    setTimeout(() => this.isloaded = true, 4000);
  }
}
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
    background-color: white;
    z-index: 999;
  }
  // -----------------------------------------------------
  .cube{
    width: 650px;
    height:450px;
    margin-right: 10px;
  }
  // -----------------------------------------------------

</style>