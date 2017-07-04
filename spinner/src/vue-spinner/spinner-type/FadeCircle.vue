<template>
    <div class="spinner-fade" v-bind:style="sizeStyle">
          <div class="spinner-fade-line" v-for="i in 12"></div>
    </div>
</template>

<script type="text/javascript">
    export default{  
        name: 'FadeCircle',
        props: {
            size: {
              type: String,
              default: '40px'
            }
        },
        mounted(){
          console.log(this.size)
        },
        data() {
            return {
                sizeStyle: {
                    height: this.size + 'px',
                    width: this.size + 'px',
                }
            }
        }       
    }
</script>

<style lang="scss">
  .spinner-fade{
    position: relative;
    .spinner-fade-line{
      width: 100%;
      height: 100%;
      position: absolute;
      left: 0;
      top: 0;
      &::before{
        content: '';
        display: block;
        margin: 0 auto;
        width: 5%;
        height: 25%;
        background-color: #333;
        animation: circleFadeDelay 1.2s infinite ease-in-out both;     
      }       
      $line-rotation: 0deg;
      $animation-delay: -1.2s;
      @for $i from 1 through 12{
        &:nth-child(#{$i}){
          transform: rotate($line-rotation); 
          $line-rotation: $line-rotation + 30;
          &::before{
            animation-delay: $animation-delay;
            $animation-delay: $animation-delay + 0.1;
          }                   
        }
      }
      &:nth-child(1)::before{
        animation-delay: 1.2s;
      }    
    }   
  }
  @keyframes circleFadeDelay {
    0%, 100% { opacity: .3; }
    50% { opacity: 1; } 
  }    
</style>