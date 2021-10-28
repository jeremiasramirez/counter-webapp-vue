<template>
    <section>
        <article class="set__container__timing animate__clock"> 
            {{activatedClassWhenSecodnsIsTop()}}
            {{activatedWhenSecondsIsClose()}}
            <p>{{hours__props}}</p>:
            <p>{{minutes__props}}</p>:
            <p :class="activateWhenSecondIsTop">{{seconds__props}} </p>
              <!-- {{activateClassLastChild()}} -->
              
             <div class="timeout" v-if="timeout && hours__props ==0 && minutes__props==0 && seconds__props == 0 ">
                TIME OUT  </div>
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
        beforeCreate() {
            console.log("beforeCreate")
            this.hours__props=0;
            this.minutes__props=0;
            this.seconds__props=0;
             this.activateWhenSecondIsTop=""
             this.timeout=false
        },
        activatedWhenSecondsIsClose(){
            
            if(this.hours__props ==0 && this.minutes__props ==0 && this.seconds__props <= 5){
                this.timeout=true
               
             
            }
            
           
            
            
        },
        activatedClassWhenSecodnsIsTop(){
             


            if(this.hours__props ==0 && this.minutes__props ==0 && this.seconds__props <= 59){
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
    top:60px;
   
    animation: showtimeout  5s  linear;
     
}
@keyframes showtimeout {
    from{
        opacity:0;
        background-color: transparent;
    }
    to{
        opacity:1;
    }
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
  left:41%;
  z-index:-10;
  border-radius: 50%;
  animation: bouncingShadow 1.2s infinite ease-in;
 
}

@keyframes bouncingShadow {
    from{
        border: 8px solid rgb(230, 226, 231);
        
    }
    to{
         border: 4px solid rgb(105, 132, 250);
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
     transition:1s;
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