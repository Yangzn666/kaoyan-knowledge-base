<script setup lang="ts">
import { defineAsyncComponent } from 'vue'

// 真题阅读（含传统阅读 / 完型 / 新题型 + 内嵌精读面板），自包含组件
const ReadingPractice = defineAsyncComponent(() => import('@/components/ReadingPractice.vue'))
</script>

<template>
  <div class="english-container">
    <header class="page-hero">
      <div class="hero-grid"></div>
      <div class="hero-glow"></div>
      <div class="hero-inner">
        <span class="hero-kicker">ENGLISH · 英语一真题</span>
        <h1 class="hero-title">英语真题<span class="gold">精读</span></h1>
        <p class="hero-sub">历年真题 · 逐题解析 · 全文精读 —— 盖住答案自己练，作答仅保存在你自己的浏览器</p>
      </div>
    </header>

    <div class="content-deck">
      <ReadingPractice />
    </div>

    <footer class="page-note">
      <p>真题与解析仅供学习交流，作答记录保存在本地浏览器，不会上传或与他人共享。</p>
    </footer>
  </div>
</template>

<style scoped>
.english-container {
  --font-mono: 'JetBrains Mono', monospace;
  --muted: #5b6b7f;
  --gold: #ffc53d;
  --navy-deep: #0d2137;
  --navy: #16345c;
  --navy-mid: #1e4576;
  --line: #e4ebf3;
  max-width: 1400px;
  margin: 0 auto;
  padding: 0;
}

.page-hero {
  position: relative;
  overflow: hidden;
  background: linear-gradient(150deg, var(--navy-deep) 0%, var(--navy) 55%, var(--navy-mid) 100%);
  border-radius: 16px;
  padding: 40px 40px 34px;
  margin-bottom: 16px;
}
.hero-grid {
  position: absolute;
  inset: 0;
  background-image:
    linear-gradient(rgba(255,255,255,0.03) 1px, transparent 1px),
    linear-gradient(90deg, rgba(255,255,255,0.03) 1px, transparent 1px);
  background-size: 42px 42px;
  pointer-events: none;
}
.hero-glow {
  position: absolute;
  top: -80%;
  right: -6%;
  width: 420px;
  height: 420px;
  background: radial-gradient(circle, rgba(255,197,61,0.14) 0%, transparent 68%);
  pointer-events: none;
}
.hero-inner {
  position: relative;
  z-index: 1;
}
.hero-kicker {
  font-family: var(--font-mono);
  font-size: 0.72rem;
  letter-spacing: 0.2em;
  color: var(--gold);
  text-transform: uppercase;
}
.hero-title {
  font-size: clamp(1.9rem, 3.6vw, 2.7rem);
  font-weight: 800;
  color: #fff;
  margin: 10px 0 8px;
  letter-spacing: 0.02em;
}
.hero-title .gold {
  color: var(--gold);
}
.hero-sub {
  color: #a8bdd4;
  font-size: 0.96rem;
  letter-spacing: 0.05em;
  line-height: 1.7;
}

.content-deck {
  background: #fff;
  border-radius: 16px;
  border: 1px solid var(--line);
  box-shadow: 0 4px 24px rgba(13, 33, 55, 0.06);
  padding: 24px;
  min-height: 520px;
}

.page-note {
  margin-top: 22px;
  text-align: center;
}
.page-note p {
  font-size: 0.8rem;
  color: #9aa7b8;
  letter-spacing: 0.04em;
}

@media (max-width: 768px) {
  .page-hero {
    padding: 28px 20px 24px;
    border-radius: 12px;
  }
  .content-deck {
    padding: 12px;
    border-radius: 12px;
  }
}
</style>
