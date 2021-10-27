<template>
    <section>
        <article class="set__container__timing animate__clock"> 
            {{activatedClassWhenSecodnsIsTop()}}
            {{activatedWhenSecondsIsClose()}}
            <p>{{hours__props}}</p>:
            <p>{{minutes__props}}</p>:
            <p :class="activateWhenSecondIsTop">{{seconds__props}} </p>
              <!-- {{activateClassLastChild()}} -->
              
             <div class="timeout" v-if="timeout==true">
                TIME OUT 
            </div>
        </article>

       
    </section>
      
</template>



<script>
 
export default {

    
    props: [
        'hours__props',
        'minutes__props',
        'seconds__props'
    ],

    data(){
        return {
            timeout:false,
            activateWhenSecondIsTop:false 
        }
    },
    methods: {
        activatedWhenSecondsIsClose(){
            
            if(this.hours__props ==0 && this.hours__props ==0 && this.seconds__props == 0){
                
                   this.timeout=true
                
            }
            
        },
        activatedClassWhenSecodnsIsTop(){
             


            if(this.hours__props ==0 && this.hours__props ==0 && this.seconds__props == 59){
                this.activateWhenSecondIsTop="animate-last-child"
            }
            
          
        }
       
    }
 
  
}
</script>




<style>

.timeout{
    background-color:Red;
    font-family:"ubuntu";
    font-size:12px;
    border-radius:5px;
    margin-top:-7px;
 
    position:absolute;
    padding: 3px 10px;
    color:white;
    font-weight:600;
    /* border:1px solid red; */
    top:50px;
     
}
    .set__container__timing{
    width: 250px;
  display: flex;
  justify-content: center;
  align-items: center;
  
  flex-wrap: wrap;
  height: 250px;
  /* top:360px; */
  background-color: white;
  position:absolute;
  left:40%;
  z-index:-10;
  border-radius: 50%;
  animation: bouncingShadow 3s infinite linear alternate-reverse;
 
}

@keyframes bouncingShadow {
    from{
         border: 4px solid rgb(246, 244, 247);
    }
    to{
        border: 15px solid rgb(230, 226, 231);
    }
}

.set__container__timing p{
    font-family: "ubuntu";
    font-size:22px;
    word-spacing:2px;
    /* margin-top:60px; */
    padding:3px;
    /* margin:0; */
    
}

.animate-last-child{
 
   border-radius:4px;
     color: white;
   animation: inof .7s infinite alternate-reverse;
}
@keyframes inof {
    from{
        background-color: red;
       
    }
    to{
       background-color: rgb(214, 200, 200);
        
    }
}
 
</style>