<template>
  <div id="app">
    <h1>ch02-fundamentals｜第 2 章实验台</h1>
    <p class="muted">第 03 课上半场（2.5.3—2.8）：修饰符串联 · 计算属性 · 侦听器 · 样式绑定</p>

    <nav class="lab-nav">
      <a href="#exp-01">01 修饰符串联</a>
      <a href="#exp-02">02 计算属性</a>
      <a href="#exp-03">03 侦听器</a>
      <a href="#exp-04">04 样式绑定</a>
    </nav>

    <!-- 一个小实验一个 section：id 与菜单锚点对应，先占位、逐实验填充 -->
    <section id="exp-01"><ModifierChainLab/></section>
    <section id="exp-02"><ComputedLab/></section>
    <section id="exp-03"><WatchLab/></section>
    <section id="exp-04"><StyleBindingLab/></section>
  </div>
</template>

<script>
import ModifierChainLab from './experiments/01-modifier-chain/ModifierChainLab.vue'
import ComputedLab from './experiments/02-computed/ComputedLab.vue'
import WatchLab from './experiments/03-watch/WatchLab.vue'
import StyleBindingLab from './experiments/04-style-binding/StyleBindingLab.vue'
export default {
  name: 'App',
  components: {ModifierChainLab,ComputedLab,WatchLab,StyleBindingLab}, // 任务 1 完成后挂载 ModifierChainLab
    // 任务 1 完成后挂载 ModifierChainLab
    // 任务 2 完成后挂载 ComputedLab
    // 任务 3 完成后挂载 WatchLab
    // 任务 4 完成后挂载 StyleBindingLab
  } 

</script>

<style scoped>
.lab-nav {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
  margin: 12px 0 20px;
}

.lab-nav a {
  color: rgb(50, 205, 128);
  text-decoration: none;
  border: 1px solid var(--primary);
  border-radius: 999px;
  padding: 3px 14px;
  font-size: 14px;
}

.lab-nav a:hover {
  background: rgb(205, 115, 50);
}

section {
  margin: 18px 0;
}

.muted {
  color: rgb(114, 31, 178);
  margin-top: 0;
}
</style>