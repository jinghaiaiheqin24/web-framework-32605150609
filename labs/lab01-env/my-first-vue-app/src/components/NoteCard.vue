<template>
  <div class="note-card">
    <h3>{{ title }}</h3>
    <p>这是一个单文件组件</p>
    <p>{{ message }}</p>
    <p>{{ message.toUpperCase() }}</p>
    <p>{{ 1 + 2 * 3 }}</p>
    <p v-text="rawText"></p> 
    <p v-html="htmlText"></p> 
    <p>count = {{ count }}</p>
    <p>这是我的第一条笔记</p>
    <img :src="imgSrc" :title="tipTitle" width="96" />
    <p :class="{ active: count > 0 }">count 大于 0 时这行变高亮</p>
    <button @click="count++">count +1(内联语句)</button>
    <button @click="say('你好', $event)">say(方法 + 传参)</button>
    <p>实时展示 → 姓名：{{ form.name }}｜性别：{{ form.gender }}｜爱好：{{ form.hobbies.join('、') }}</p>

    <input v-model="form.name" placeholder="输入姓名" />
    <label><input type="radio" value="男" v-model="form.gender" /> 男</label>
    <label><input type="radio" value="女" v-model="form.gender" /> 女</label>
    <label><input type="checkbox" value="篮球" v-model="form.hobbies" /> 篮球</label>
    <label><input type="checkbox" value="编程" v-model="form.hobbies" /> 编程</label>
    <button @click="show = !show">切换显隐（观察 DevTools 元素面板）</button>
<p v-if="show">v-if:条件为真我才被"渲染"出来</p>
<p v-else>v-else:上面条件为假时才轮到我</p>
<p v-show="show">v-show:我一直存在,只是被 display:none 藏起来</p>
<ul>
  <li v-for="(subject, index) in subjects" :key="index">
    {{ index }} - {{ subject }}
  </li>
</ul>
<button @click="subjects[1] = '英语（索引赋值）'">数组索引赋值</button>
<button @click="form.school = '成都理工大学工程技术学院'">对象新增属性</button>
<p v-if="form.school">{{ form.school }}</p>
  </div>
  <!-- 嵌套盒子：内层点击会"冒泡"触发外层 -->
<div class="bubble" @click="log('outer 触发（外层 @click）')">
  <button @click.stop="log('inner 触发（.stop：冒泡被阻止）')">内层 .stop</button>
  <button @click="log('inner 触发（无 .stop：冒泡到外层）')">内层 无.stop</button>
</div>
<!-- .prevent：替代任务 1 里手写的 e.preventDefault() -->
<a href="https://vuejs.org" @click.prevent="log('.prevent 阻止了跳转')">Vue 官网（.prevent 版）</a>

<!-- .once：只触发一次的"抽奖" -->
<button @click.once="log('`.once` 抽奖按钮：只触发这一次！')">抽奖按钮 .once</button>

<!-- .self：只有点击盒子本身才触发，点子元素不算 -->
<div class="self-box" @click.self="log('.self：点到盒子本身才触发')">
  点盒子本身（.self）<button>我是子元素（点我没用）</button>
</div>
<input
  @keyup.enter="log('回车 .enter 触发')"
  @keyup.esc="log('Esc .esc 触发')"
  placeholder="这里按 Enter / Esc 试试"
/>
</template>
<script>

export default {
  name: 'NoteCard',
  data() {
    return {
      title: '我的第一条笔记',
      message: 'hello vue',
      count: 0,
      rawText: '<b>我是 v-text 的纯文本</b>',    // 页面原样显示这串字符     
      htmlText: '<b>我是 v-html 解析出的加粗</b>' ,// 页面显示被 <b> 加粗的文字
      imgSrc: 'https://vuejs.org/images/logo.svg',
      tipTitle: '悬停提示' ,
      form: { name: '', gender: '', hobbies: [] },
      subjects: ['语文', '数学', 'Vue']
    }
  },
  methods: {
    say(word, event) {
      alert(word + '｜事件类型：' + event.type)
    }
  },
  mounted() {                    // 挂载完成后自动执行一次（与 data、methods 平级）
    setTimeout(() => {
      this.count = 100           // 只改数据，不碰 DOM
    }, 3000)
  }
}
</script>

<style scoped>
.note-card { border: 1px solid #42b883; padding: 10px 16px; border-radius: 6px; }
.active { color: #42b883; font-weight: bold; }

</style>



