<template>
  <div class="container" >
    <div>计数结果: {{count}}</div>
    <a href="/pages/test/main" class="navlink">进入计数页面</a>
    <div class="message" @click="clickHandle">{{msg}}</div>
    <!-- 使用3个 click-counter 组件 -->
    <click-counter :init-num='10' @clicknum="handleClickNum" /> 
    <click-counter :init-num='20' @clicknum="handleClickNum" /> 
    <click-counter :init-num='30' @clicknum="handleClickNum" >
        <!-- 填坑用... -->
    <input type="checkbox" /> 禁用
    </click-counter>
  </div>
</template>
<script>
import ClickCounter from '@/components/click-counter/click-counter'
import golbalStore from '../../stores/global-store'

export default {
  // 声明在当前组件下使用 counter-click 组件
  components: { ClickCounter },
  data () {
    return {
      msg: 'Hello from zfd!'
    }
  },
  methods: {
    clickHandle () {
      this.msg = 'Click!!!!'
    },
    handleClickNum (data) {
      console.log('>>>>>>>>>', data.num)
    }
  },
  computed: {
    count () {
      return golbalStore.state.count
    }
  }
}
</script>

<style scoped>
  .message {
      color: red;
      padding: 10px;
      text-align: center;
  }
  .navlink {
    text-decoration: underline;
  }
</style>

