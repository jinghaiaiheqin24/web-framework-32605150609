<template>
  <div class="event-lab">
    <h3>🎯 事件实验室（2.4 事件对象 · 2.5 事件修饰符）</h3>

    <!-- 获取方式一：不传参，方法首参自动是事件对象 -->
    <button @click="showEvent">打印事件对象（不传参）</button>
    <!-- 获取方式二：传参时用 $event 占位 -->
    <button @click="showEventArg($event, 66)">showEventArg($event, 66)（传参版）</button>
    <!-- 原生阻止默认行为（2.5 将用 .prevent 替代这种手动写法） -->
    <a href="https://vuejs.org" @click="goVue">Vue 官网链接（手动 preventDefault）</a>

    <!-- 页面日志区：最新在上（Console 同步输出，便于展开完整对象） -->
    <ol class="logs">
      <li v-for="(item, index) in logs" :key="index">{{ item }}</li>
    </ol>
  </div>
</template>

<script>
export default {
  name: 'EventLab',
  data() {
    return { logs: [] }
  },
  methods: {
    log(msg) {
      this.logs.unshift(msg)          // 最新日志插到最前面
      console.log(msg)
    },
    showEvent(e) {                    // 不传参：首参就是事件对象
      this.log(`type=${e.type}｜target=<${e.target.tagName.toLowerCase()}>｜timeStamp=${Math.round(e.timeStamp)}ms`)
      console.log('完整事件对象：', e)   // 到 Console 展开看全貌！
    },
    showEventArg(e, number) {         // 传参版：模板里 $event 占位
      this.log(`传参版：target=<${e.target.tagName.toLowerCase()}>｜number=${number}`)
    },
    goVue(e) {
      e.preventDefault()              // 原生 API：阻止链接默认跳转
      this.log('手动 preventDefault() 阻止了跳转')
    }
  }
}

</script>

<!-- 修改后（</script> 后追加整段样式；其中 .bubble / .self-box 供下一任务的
     冒泡与 .self 实验用，先一起写好） -->
<style scoped>
.event-lab {                             /* 外层：金色虚线圆角卡片 */
  border: 1px dashed #b8860b;
  padding: 12px 16px;
  border-radius: 8px;
  line-height: 2;
}
.bubble {                                /* 冒泡实验：绿色实线盒（下一任务用） */
  border: 2px solid #42b883;
  padding: 6px 10px;
  margin: 6px 0;
}
.self-box {                              /* .self 实验：蓝色点线盒（下一任务用） */
  border: 2px dotted #646cff;
  padding: 6px 10px;
  margin: 6px 0;
}
.logs {                                  /* 日志区：浅灰底 + 金色左边线 */
  background: #fafafa;
  border-left: 3px solid #b8860b;
  margin: 8px 0 0;
  padding: 4px 8px 4px 28px;
  color: #555;
  min-height: 2em;
}
</style>
