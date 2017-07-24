<template>
  <div id="app">
    <h1>vue-spinner</h1>
    <p>attribute  size="Number" color="String"</p>
    <ul>
      <li>
        <spinner type="fade" size="40" color="#444"></spinner>
        <p>type=fade</p>
      </li>
      <li>
        <spinner type="beat" size="10"></spinner>
        <p>type=beat</p>
      </li>
      <li>
        <spinner type="rotate" size="40"></spinner>
        <p>type=rotate</p>    
      </li>  
      <li>
        <spinner type="line" size="20"></spinner>
        <p>type=line</p>    
      </li>
      <li>
        <spinner type="ball" size="60"></spinner>
        <p>type=ball</p>    
      </li>                    
    </ul>
  </div>
</template>

<script>
import Spinner from './vue-spinner/spinner.vue';
export default {
  name: 'app',
  data () {
    return {
      
    }
  },
  components:{
    Spinner
  }
}
</script>

<style lang="scss">
body {
    min-width: 1200px;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;

  h1,p{
    text-align: center;
  }
  ul{
    list-style-type: none;
    padding: 0;
    margin: 0;
    li {
      float: left;
      min-width: 150px;
      height: 150px;
      position: relative;
      text-align: center;
      box-sizing: border-box;
      border: 1px solid #333;
      border-right: none;
      .spinner{
        position: absolute;
        left: 50%;
        top: 50%;
        transform: translate(-50% , -50%);
      }      
    }
    li:last-child {
      border-right: 1px solid #333;
    }    
  }
}

</style> 
