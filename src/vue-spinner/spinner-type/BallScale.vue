<template>
    <div class="spinner-ball" v-show="loading" v-bind:style="sizeStyle">
        <div class="spinner-ball-item" v-bind:style="sizeStyleItem" v-for="i in 3"></div>
    </div>
</template>

<script>
    export default {
        name: 'BallScale',
        props: {
            loading:{
                type: Boolean,
                default: true
            },
            color:{
                type: String,
                default: '#5dc596'
            },
            size:{
                type: String,
                defalut: '40px'
            }
        },    
        data(){
            return {
                sizeStyle:{
                    height: this.size + 'px',
                    width: this.size + 'px',
                },
                sizeStyleItem:{
                    height: this.size + 'px',
                    width: this.size + 'px',
                    background : this.color     
                }
            }    
        }        
    }
</script>

<style lang="scss">
    .spinner-ball {
        position: relative;
        .spinner-ball-item{
            border-radius: 100%;
            animation-fill-mode: both;
            position: absolute;
            left: 0px;
            top: 0px;
            opacity: 0;
            margin: 0;
            animation: ball-scale-multiple 1s 0s linear infinite;
            $animation-delay: 0.2s;
            @for $i from 1 through 3{
                &:nth-child(#{$i}){
                    animation-delay: ($animation-delay * $i);
                }
            }
        }
    }
    @keyframes ball-scale-multiple{
        0% {
            transform: scale(0);
            opacity: 0;
        }
        5% {
            opacity: 1;
        }
        100% {
            transform: scale(1);
            opacity: 0;
        }
    }
</style>