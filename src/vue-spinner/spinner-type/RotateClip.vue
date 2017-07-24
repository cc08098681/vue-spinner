<template>
<div class="spinner-clip" v-show="loading">
    <div class="spinner-clip-item" v-bind:style="spinnerStyle">
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
    },
    size: {
      type: String,
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
  .spinner-clip-item{
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
      transform: rotate(180deg) scale(0.6);
    }
    100%
    {
      transform: rotate(360deg) scale(1);
    }
}
</style>