<template>
    <div class="spinner-beat">
      <div class="spinner-beat-item" v-for="i in 3" v-bind:style="sizeStyle"></div>
    </div>
</template>

<script>
export default {
  
  name: 'BeatPoint',

  props: {
    size: {
      type: String,
    },
    color: {
      type: String,
    }
  },
  data () {
    return {
      sizeStyle: {
        height: this.size + 'px',
        width: this.size + 'px',
        backgroundColor: this.color
      }
    }
  }
}
</script>

<style lang="scss">
  .spinner-beat{
    .spinner-beat-item{
      animation: beatPointDelay 0.75s infinite linear;
      animation-fill-mode: both;
      display: inline-block;
      border-radius: 100%;
      &:nth-child(2){
        margin: 0 3px;
      }       
    }
    $animation-delay: 0.16s;
    @for $i from 1 through  3{
      .spinner-beat-item:nth-child(#{$i}){
        animation-delay: ($animation-delay * $i)
      }
    }
  }
  @keyframes beatPointDelay{
      50%{
        transform: scale(0.3);           
        opacity: 0.2;
      }
      100%{
        transform: scale(1);            
        opacity: 1;
      }
  }
</style>
