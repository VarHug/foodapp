<template>
  <div class="cartcontrol">
    <transition name="move">
    <div class="cart-decrease" v-show="food.count>0" @click="decreaseCart">
      <div class="inner icon-remove_circle_outline"></div>
    </div>
    </transition>
    <div class="cart-count" v-show="food.count>0">{{food.count}}</div>
    <div class="cart-add icon-add_circle" @click="addCart"></div>
  </div>
</template>

<script type="text/ecmascript-6">
import Vue from 'vue';

export default {
  props: {
    food: {
      type: Object
    }
  },
  data() {
    return {

    };
  },
  methods: {
    addCart() {
      console.log('click');
      if (!this.food.count) {
        Vue.set(this.food, 'count', 1);
      } else {
        this.food.count++;
      }
    },
    decreaseCart() {
      if (this.food.count) {
        this.food.count--;
      }
    }
  }
};
</script>

<style lang="stylus" rel="stylesheet/stylus">
  .cartcontrol
    font-size 0
    .cart-decrease
      display inline-block
      padding 6px
      .inner
        display inline-block
        line-height 24px
        font-size 24px
        color rgb(0, 160, 220)
    .cart-count
      display inline-block
      vertical-align top
      width 12px
      padding-top 6px
      line-height 24px
      text-align center
      font-size 10px
      color rgb(147, 153, 159)
    .cart-add
      display inline-block
      padding 6px
      line-height 24px
      font-size 24px
      color rgb(0, 160, 220)

  &.move-enter-active, &.move-leave-active
    transition all .4s linear
    .inner
      transition all .4s linear
      transform rotate(0)
  &.move-enter, &.move-leave-to
    opacity 0
    transform translate3d(36px, 0, 0)
    .inner
      transform rotate(180deg)
</style>
