<template>
<div class="spinner-clip" v-show="loading">
    <div class="clip-box" v-bind:style="spinnerStyle">
    </div>
  </div>
</template>

<script>
export default { 
  name: 'RotateClip',
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
      default: '35px'
    },
  },
  computed: {
    spinnerStyle () {
      return {
        height: this.size + 'px',
        width: this.size + 'px',
        borderColor: this.color + ' ' + this.color + ' ' + 'transparent' + ' ' + 'transparent'
      }
    }
  }
}
</script>

<style lang="scss">
.spinner-clip
{
  text-align: center; 
  .clip-box{
    animation: clipDelay 0.75s 0s infinite linear;
    animation-fill-mode: both;
    display: inline-block; 
    background: transparent;
    border-width: 2px;
    border-style: solid;
    border-radius: 100%;   
  }
}

@keyframes clipDelay
{
    0%
    {
      transform: rotate(0deg) scale(1);
    }
    50%
    {
      transform: rotate(180deg) scale(0.8);
    }
    100%
    {
      transform: rotate(360deg) scale(1);
    }
}
</style>