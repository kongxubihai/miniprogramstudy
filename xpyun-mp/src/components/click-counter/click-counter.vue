<template>
  <div class="click-counter">
    <div class="counter-num">次数: {{num}}</div>
    <button class="counter-btn" @click="handleIncreaseClick">点我加1</button>
    <button class="counter-reset-btn" @click="handleResetClick">点我清零</button>
    <slot></slot>
  </div>  
</template>

<script>
export default {
  // 增加一个可从外部传入的属性initNum
  props: {
    initNum: {
      type: Number,
      default: 0
    }
  },

  data () {
    return {
      num: this.initNum
    }
  },

  methods: {
    handleIncreaseClick () {
      this.num += 1
      this.notifyNum()
    },
    handleResetClick () {
      this.num = 0
      this.notifyNum()
    },
    notifyNum () {
      this.$emit('clicknum', {
        num: this.num
      })
    }
  }
}
</script>

<style scoped>
.click-counter {
  display: flex;
  align-items: center;
  border: 1px red solid;
  padding: 10px;
  background-color: #ffffff;
}

.counter-num {
  margin: 3px;
  flex: 1
}
.counter-btn {
  margin: 3px;
  flex: 1
}
.counter-reset-btn {
  margin: 3px;
  flex: 1
}

</style>
