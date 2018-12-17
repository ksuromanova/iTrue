<template>   
    <div class="modal_video"> 
        <i @click="videoShow = !videoShow" class="icon-play"></i>
        <span v-show="videoShow" @click="videoShow = !videoShow" class="icon-cancel"></span>
        <iframe v-show="videoShow" src="https://www.youtube.com/embed/yE8RGafbuTU" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>        
    </div>       
</template>

<script>
export default {
  data() {
      return {
          videoShow: false
      }
  }
}
</script>

<style lang="scss" >
@import "./css/mixins.scss";
.modal_video {
    display: flex;
    i {
    font-size: 12px;
    line-height: 60px;
    width: 60px;
    height: 60px;
    text-align: center;
    background-color: $color-white;
    color: $color-blue;
    border-radius: 50%;
    margin: 33px 15px;
    cursor: pointer;
}
iframe {
    position: fixed;
    top: 20vh;    
    left: 20vw;
    width: calc(60vw - 60px);
    height: calc(60vh - 60px);
    z-index: 200;
    bottom: 20px;
}
span {
    position: fixed;
    z-index: 201;
    top: 17vh;
    right: 22vw;
    line-height: 40px;
    font-size: 20px;
    width: 40px;
    height: 40px;
    text-align: center;
    background-color: $color-white;
    color: $color-blue;
    border-radius: 50%;
    cursor: pointer;
}
}

</style>