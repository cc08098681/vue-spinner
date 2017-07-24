<template>
    <div class="spinner-stepline" v-show="loading">
        <div class="spinner-stepline-item" v-for="i in 5" v-bind:style="spinnerStyle"></div>
    </div>
</template>

<script>
export default {  
  name: 'StepLine',
  props: {
    loading: {
      type: Boolean,
      default: true
    },
    color: { 
      type: String,
      default: '#5dc596'
    },
    size: {
      type: String,
      default: '40px'
    }
  },
  computed: {
      spinnerStyle(){
          return {
              backgroundColor: this.color,
              height: this.size + 'px',
              width: this.size/10 + 'px'
          }        
        
      } 
    
  }

}
</script>

<style lang="scss">
    .spinner-stepline
    {
        text-align: center;         
          .spinner-stepline-item {
              display: inline-block;
              margin: 2px;
              border-radius: 2px;
              animation-name: scaleStretchDelay;
              animation-duration: 1s;
              animation-iteration-count: infinite;
              animation-timing-function: cubic-bezier(.2,.68,.18,1.08);
              animation-fill-mode: both;
              $animation-delay: 0.1s;
              @for $i from 1 through 5 {
                  &:nth-child(#{$i}){
                      animation-delay: ($animation-delay * $i)
                  }
              }         
          }
    }
    @keyframes scaleStretchDelay
    {
        0%,
        100%
        {
            transform: scaleY(1);
        }
        50%
        {
            transform: scaleY(0.2);
        }
    }
</style>