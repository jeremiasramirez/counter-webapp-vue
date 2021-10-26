<template>
        <article class="set__container__timing">  </article>
</template>








<style>
    .set__container__timing{
    width: 250px;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-wrap: wrap;
  height: 250px;
  top:360px;
  background-color: #eee;
  position:absolute;
  z-index:-10;
  border-radius: 50%;
  animation: bouncingShadow 1s infinite linear alternate-reverse;
  transition: 1s;
}

@keyframes bouncingShadow {
    from{
         border: 4px solid rgb(201, 34, 243);
    }
    to{
        border: 15px solid rgb(119, 12, 146);
    }
}
</style>