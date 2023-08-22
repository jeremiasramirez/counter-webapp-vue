<template>
    <div class="container__logo">
        <div class="logo">
            <img src="../../assets/logo.svg" class="animate" alt="logo">
        </div>
    <section class=" container__spinning__loading">
        <article class=" spinning__loading"></article>
    </section> 
    </div>
</template>

<style >
    
    .container__spinning__loading{
            display: flex;
            justify-content: center;
            align-items: center;
        }    
        .spinning__loading{
            width: 30px;
            height: 30px;
            
            border-radius: 50%;
            border-left:3px solid rgb(140, 147, 216); 
            animation: scaleOnScale .4s infinite linear;
        }

      
        @keyframes scaleOnScale {
            from{
                transform: rotate(-360deg);
            }
            to{
                transform: rotate(0);
            }
        }
         .container__logo{
             padding-top:20%;
             display:flex;
             margin-top: 50px;
             justify-content:end;
             flex-wrap: wrap;
             align-items:center;
             flex-direction:column;
         }
         .logo{
             background-color:#eee;
             padding: 26px 10px 10px 10px;;
             
             width:200px;
             height:200px;
             border-radius:50%;
            margin-top:-100px;
             text-align:center;
              margin-bottom:100px;
         }
        .logo img{
           
            width:150px;
            height:150px;
        }
</style>