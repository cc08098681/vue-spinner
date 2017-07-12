<template>
    <div class="spinner">
        <component :is="spinner" :size="this.size" :color="this.color"></component>
    </div>
</template>

<script type="text/javascript">
    import BeatPoint from './spinner-type/BeatPoint.vue'
    import FadeCircle from './spinner-type/FadeCircle.vue'
    export default{
        name: 'spinner',
        props:{
            type:{
                type:String,
                required: true,
                default: 'fade'
            },
            size:{
                type:String,
                default: '20'
            },
            color:{
                type:String,
            }
        },
        components:{
           SpinnerBeat:BeatPoint,
           SpinnerFade:FadeCircle 
        },
        computed:{
            spinner(){
                return `spinner-${this.type}`
            }
        }
    }
</script>

<style type="text/css">
    .spinner {
        text-align: center;
    }
</style>