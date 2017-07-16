<template>
  <button class='btn btn-1e small-12 large-8 rows'><i class='fa fa-2x' :class='icon'></i><span class='btn__text'> {{text}}</span></button>
</template>

<script>
export default {
  props: ['icon', 'text']
}
</script>

<style lang='scss' scoped>
  .btn {
      font-family: 'Raleway', sans-serif;
      font-weight: 400;
      font-size: responsive 0.8rem 1.2rem;
      color: $white;
      background: rgba(0, 0, 0, 0.3);
      cursor: pointer;
      padding: 15px 10%;
      display: flex;
      justify-content: space-between;
      margin: 15px 0;
      text-transform: uppercase;
      letter-spacing: 2px;
      outline: none;
      position: relative;
      transition: all 0.3s;
      box-shadow: 3px 4px 10px black;
      overflow: hidden;
      border: 2px solid $primary;
      border-radius: 2px;

      &__text {
        width: 80%;
        text-align: center;
        align-self: center;
      }

      i.fa {
        align-self: flex-start;        
        &:before{
          transform: translateY(-7px);
          width: 38px;
          height: 38px;
          overflow: hidden;
        }
      }

      &.btn-1e:after {
        width: 100%;
        height: 0;
        top: 50%;
        left: 50%;
        background: $primary;
        opacity: 0;
        transform: translateX(-50%) translateY(-50%) rotate(45deg);
      }

      &.btn-1e:hover,
      &.btn-1e:active {
        color: $black;
        border-color: #16863B;
        box-shadow: 0px 0px 15px black;
      }

      &.btn-1e:hover:after {
        height: 320%;
        opacity: 1;
      }

      &.btn-1e:active:after {
        height: 400%;
        opacity: 1;
      }
    }
    .btn:after {
      content: '';
      position: absolute;
      z-index: -1;
      transition: all 0.3s;
    }
</style>
