<template>
    <div class="spinner-fade" v-bind:style="sizeStyle">
          <div class="spinner-fade-item" v-for="i in 12"></div>
    </div>
</template>

<script type="text/javascript">
    export default{  
        name: 'FadeCircle',
        props: {
            size: {
              type: String,
            },
            color: {
              type: String,
            }
        },
        mounted(){
          if(this.color && this.color!='#444'){
            this.colorType();
          }  
        },
        methods:{
          colorType: function(){
            let style = document.createElement('style');
            style.setAttribute('type', 'text/css');
            style.innerHTML = this.bgc;
            document.head.appendChild(style);
          }
        },
        data() {
            return {
                sizeStyle: {
                    height: this.size + 'px',
                    width: this.size + 'px',
                },
                bgc: `.spinner-fade .spinner-fade-item::before{background-color:${this.color}}`
            }
        }       
    }
</script>

<style lang="scss">
  .spinner-fade{
    position: relative;
    .spinner-fade-item{
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
        background-color: #444;
        animation: circleFadeDelay 1s infinite ease-in-out both;     
      }       
      $line-rotation: 0deg;
      $animation-delay: 0s;
      @for $i from 1 through 12{
        &:nth-child(#{$i}){
          transform: rotate($line-rotation); 
          $line-rotation: $line-rotation + 30;
          &::before{
            animation-delay: $animation-delay;
            $animation-delay: $animation-delay + 0.083;
          }                   
        }
      }   
    }   
  }
  @keyframes circleFadeDelay {
    0%, 100% { opacity: 0.4; }
    50% { opacity: 1; } 
  }    
</style>