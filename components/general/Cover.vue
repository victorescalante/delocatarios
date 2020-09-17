<template>
  <div class="background-cover" :style=image>
    <div class="title-container">
      <p class="title">{{ title }}</p>
    </div>
  </div>
</template>

<script>
    export default {
      name: "Cover",
      props: ['title', 'cover_image'],
      data() {
        return {

        }
      },
      computed: {
        image(){
          let url = process.env.backend + this.cover_image;
          console.log(url);
          return "background-image: url("+url+")";
        }
      }
    }
</script>

<style lang="scss">
  .background-cover{
    position: relative;
    background-color: purple;
    width: 100%;
    height: 40vh;
    background-position: center;
    background-repeat: no-repeat;
    background-size: cover;
    &:after{
      position: absolute;
      content: '';
      width: 100%;
      height: 100%;
      background: rgba(4,4,4,.5);
      z-index: 1;
    }
    .title{
      width: 100%;
      text-align: center;
      position: absolute;
      font-size: 50px;
      color: white;
      top: 50%;
      margin-top: -50px;
      z-index: 2;
    }
  }
</style>
