<template>
    
    <section class="container__time">

        <article class="set__container">

            <div class="container__input">
                <input class="input__set" type="text" placeholder="Hour" />
                <input class="input__set" type="text" placeholder="Min" />
                <input class="input__set" type="text" placeholder="Secs" />
            </div>
        </article>

        <article class="buttoners">
          
          
            <md-button class="md-icon-button md-raised md-primary">
                <img src="../../assets/icons/play_arrow_white_24dp.svg" alt="icon">
            </md-button> 

            <md-button class="md-icon-button md-raised md-primary">
                <img src="../../assets/icons/replay_white_24dp.svg" alt="icon">
            </md-button>  

            <md-button class="md-icon-button md-raised md-accent">
                <img src="../../assets/icons/stop_white_24dp.svg" alt="icon">
            </md-button>   

            <md-button class="md-icon-button md-raised md">
                <img src="../../assets/icons/pause_black_24dp.svg" alt="icon">
            </md-button>    
        </article>


    </section>
</template>

<script>
import Vue from 'vue'
import { MdButton } from 'vue-material/dist/components'
import 'vue-material/dist/vue-material.min.css'
import 'vue-material/dist/theme/default.css'

Vue.use(MdButton)
 
export default {
    
}
</script>
    

<style>

    .set__container{
        width:200px;
        display: flex;
        justify-content: center;
        align-items: center;
        flex-wrap: wrap;
        height:200px;
        background-color:rgb(102, 22, 148);
        border-radius: 50%;
    }
    .container__input{
         display: flex;
        justify-content: center;
        flex-wrap: wrap;
    }
    .container__time{
        padding-top:50px;
        display: flex;
        justify-content: end;
        flex-wrap: wrap;
        align-items: center;
         flex-direction: column;
    }
    .buttoners{
        margin-top:25px;
        display: flex;
        justify-content: center;
        background-color: #eee;
        border-radius: 10px;
        padding:10px 20px;
        /* width: 290px; */
        flex-wrap: wrap;
    }
    
    .input__set{
        width:50px !important;
        height:50px;
        text-align:center;
        border-radius:10%;
        border: 1px solid #eee;
        outline:none;
        margin: 0 2px;
        background-color: white;
        font-weight: 600;
        font-size:17px;
        font-family:"ubuntu";
    }
 

</style>