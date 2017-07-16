<template>
  <div class='footer'>
    <span class='footer__text'>Copyright  ©  2017 Luis González. All rights reserved.</span>
    <span class='footer__text'>Picture: <a href='https://www.google.com/search?q=Mount+Roraima&oq=Mount+Roraima'>Mount Roraima</a></span>
  </div>
</template>

<script>
  export default {

  }
</script>

<style lang='scss'>

  .footer {
    margin-top: 30px;
    margin-bottom: 10px;
    font-family: 'Raleway', Helvetica, Arial, sans-serif;
    height: auto;
    flex-flow: column;
    justify-content: center;
    align-content: center;
    text-align: center;
    position:relative;
    bottom: 0;
    background: transparent;
    &__text {
      color: $white;
      width: auto;
      font-size: 0.8em;
    }
  }
</style>
