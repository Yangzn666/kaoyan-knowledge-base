<script setup lang="ts">
import { ref } from 'vue'
import FeynmanLearning from '@/components/FeynmanLearning.vue'
import ExamFrequencyMap from '@/components/ExamFrequencyMap.vue'

const activeTab = ref('knowledge')

const subjects = [
  {
    icon: '🧮',
    name: '数据结构',
    desc: '线性表 · 树 · 图 · 查找 · 排序，算法设计与复杂度分析',
    meta: '47 分重点',
    route: '/cs408/datastructure',
    color: '#409EFF'
  },
  {
    icon: '💾',
    name: '计算机组成原理',
    desc: '数据表示 · 存储系统 · 指令系统 · CPU · 总线 · I/O',
    meta: '四大章节核心',
    route: '/cs408/composition',
    color: '#67C23A'
  },
  {
    icon: '🖥️',
    name: '操作系统',
    desc: '进程管理 · 内存管理 · 文件管理 · 输入输出管理',
    meta: '与计组强关联',
    route: '/cs408/os',
    color: '#E6A23C'
  },
  {
    icon: '🌐',
    name: '计算机网络',
    desc: '物理层 · 数据链路 · 网络层 · 传输层 · 应用层',
    meta: '协议栈体系',
    route: '/cs408/network',
    color: '#F56C6C'
  }
]
</script>

<template>
  <div class="cs408-container">
    <header class="page-hero">
      <div class="hero-grid"></div>
      <div class="hero-glow"></div>
      <div class="hero-inner">
        <span class="hero-kicker">CS408 · 计算机学科专业基础</span>
        <h1 class="hero-title">408计算机<span class="gold">科学综合</span></h1>
        <p class="hero-sub">数据结构 · 计算机组成原理 · 操作系统 · 计算机网络</p>
      </div>
    </header>

    <div class="tab-navigation">
      <el-tabs v-model="activeTab" class="cs408-tabs">
        <el-tab-pane label="知识点梳理" name="knowledge">
          <div class="knowledge-section">
            <!-- 四门课程知识点导航：点击进入对应科目的完整知识体系页 -->
            <p class="subject-lead">选择一门课程，查看完整的章节知识点、思维导图与考点梳理。</p>
            <div class="subject-grid">
              <router-link
                v-for="s in subjects"
                :key="s.route"
                class="subject-card"
                :to="s.route"
                :style="{ '--accent': s.color }"
              >
                <div class="sc-icon">{{ s.icon }}</div>
                <div class="sc-body">
                  <h3>{{ s.name }}</h3>
                  <p>{{ s.desc }}</p>
                  <span class="sc-meta">{{ s.meta }}</span>
                </div>
                <div class="sc-arrow">→</div>
              </router-link>
            </div>
          </div>
        </el-tab-pane>

        <el-tab-pane label="🧠 费曼学习法" name="feynman">
          <FeynmanLearning />
        </el-tab-pane>

        <el-tab-pane label="📊 考频地图" name="frequency">
          <ExamFrequencyMap />
        </el-tab-pane>
      </el-tabs>
    </div>
  </div>
</template>

<style scoped>
.cs408-container {
  --font-display: 'Barlow Condensed', 'FZCuHei', sans-serif;
  --font-mono: 'JetBrains Mono', monospace;
  --ink: #1f2d3d;
  --body: #303133;
  --muted: #5b6b7f;
  --gold: #ffc53d;
  --navy-deep: #0d2137;
  --navy: #16345c;
  --line: #e4ebf3;
  --bg-soft: #f5f8fc;
  --subject: #409EFF;
  max-width: 1400px;
  margin: 0 auto;
  padding: 0;
}

/* 作战室页头 */
.page-hero {
  position: relative;
  overflow: hidden;
  background: linear-gradient(150deg, var(--navy-deep) 0%, var(--navy) 60%, #1e4576 100%);
  border-radius: 14px;
  padding: 38px 40px 32px;
  margin-bottom: 24px;
}
.hero-grid {
  position: absolute;
  inset: 0;
  background-image:
    linear-gradient(rgba(255,255,255,0.035) 1px, transparent 1px),
    linear-gradient(90deg, rgba(255,255,255,0.035) 1px, transparent 1px);
  background-size: 44px 44px;
  pointer-events: none;
}
.hero-glow {
  position: absolute;
  top: -70%;
  right: -8%;
  width: 400px;
  height: 400px;
  background: radial-gradient(circle, rgba(255,197,61,0.13) 0%, transparent 70%);
  pointer-events: none;
}
.hero-inner {
  position: relative;
  z-index: 1;
}
.hero-kicker {
  font-family: var(--font-mono);
  font-size: 0.72rem;
  letter-spacing: 0.18em;
  color: var(--gold);
  text-transform: uppercase;
}
.hero-title {
  font-size: clamp(1.8rem, 3.5vw, 2.6rem);
  font-weight: 800;
  color: #fff;
  margin: 8px 0 6px;
  letter-spacing: 0.02em;
}
.hero-title .gold {
  color: var(--gold);
}
.hero-sub {
  color: #a8bdd4;
  font-size: 0.95rem;
  letter-spacing: 0.06em;
}

/* 内容卡片 */
.tab-navigation {
  background: #fff;
  border-radius: 14px;
  padding: 24px 28px;
  border: 1px solid var(--line);
  box-shadow: 0 4px 20px rgba(13, 33, 55, 0.06);
}

/* 页签重制 */
.cs408-tabs :deep(.el-tabs__header) {
  margin-bottom: 22px;
}
.cs408-tabs :deep(.el-tabs__nav-wrap)::after {
  background: var(--line);
}
.cs408-tabs :deep(.el-tabs__item) {
  font-size: 1.02rem;
  font-weight: 500;
  padding: 0 22px;
  height: 46px;
  line-height: 46px;
  color: var(--muted);
  white-space: nowrap;
  transition: color 0.25s;
}
.cs408-tabs :deep(.el-tabs__item:hover) {
  color: var(--navy);
}
.cs408-tabs :deep(.el-tabs__item.is-active) {
  color: var(--navy);
  font-weight: 700;
}
.cs408-tabs :deep(.el-tabs__active-bar) {
  background: linear-gradient(90deg, var(--gold), #f0a820);
  height: 3px;
  border-radius: 2px;
}

.knowledge-content {
  text-align: center;
  padding: 40px 20px;
  color: var(--muted);
}

.knowledge-section {
  display: flex;
  flex-direction: column;
  gap: 24px;
}

.subject-lead {
  margin: 0;
  font-size: 0.98rem;
  color: var(--muted);
  letter-spacing: 0.02em;
}
.subject-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(320px, 1fr));
  gap: 18px;
}
.subject-card {
  display: flex;
  align-items: flex-start;
  gap: 16px;
  text-decoration: none;
  background: #fff;
  border: 1px solid var(--line);
  border-left: 4px solid var(--accent);
  border-radius: 12px;
  padding: 22px 20px;
  transition: all 0.25s ease;
  box-shadow: 0 2px 12px rgba(13, 33, 55, 0.05);
}
.subject-card:hover {
  transform: translateY(-3px);
  box-shadow: 0 10px 24px rgba(13, 33, 55, 0.12);
}
.sc-icon {
  font-size: 1.9rem;
  line-height: 1;
  flex: none;
}
.sc-body {
  flex: 1;
  min-width: 0;
}
.sc-body h3 {
  margin: 0 0 6px;
  font-size: 1.12rem;
  font-weight: 700;
  color: var(--ink);
}
.sc-body p {
  margin: 0 0 10px;
  font-size: 0.88rem;
  color: var(--muted);
  line-height: 1.6;
}
.sc-meta {
  display: inline-block;
  font-size: 0.72rem;
  color: var(--accent);
  background: color-mix(in srgb, var(--accent) 10%, #fff);
  border: 1px solid color-mix(in srgb, var(--accent) 28%, #fff);
  border-radius: 999px;
  padding: 2px 10px;
  letter-spacing: 0.03em;
}
.sc-arrow {
  flex: none;
  color: #c3cede;
  font-size: 1.2rem;
  align-self: center;
  transition: transform 0.2s ease, color 0.2s ease;
}
.subject-card:hover .sc-arrow {
  transform: translateX(4px);
  color: var(--accent);
}

.knowledge-illustration {
  margin-bottom: 25px;
}

.knowledge-content h3 {
  font-size: 1.6rem;
  color: var(--ink);
  margin-bottom: 15px;
  font-weight: 700;
}

.knowledge-content p {
  font-size: 1.05rem;
  margin-bottom: 30px;
  color: var(--muted);
  line-height: 1.6;
}

.knowledge-features {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 18px;
  margin-bottom: 30px;
}

.feature-card {
  display: flex;
  align-items: flex-start;
  gap: 15px;
  padding: 20px;
  background: var(--bg-soft);
  border-radius: 10px;
  text-align: left;
  transition: all 0.25s ease;
  border: 1px solid var(--line);
}

.feature-card:hover {
  transform: translateY(-3px);
  box-shadow: 0 8px 20px rgba(13, 33, 55, 0.10);
  border-color: var(--subject);
  background: #fff;
}

.feature-card h4 {
  color: var(--ink);
  margin: 0 0 8px 0;
  font-size: 1.05rem;
  font-weight: 700;
}

.feature-card p {
  color: var(--muted);
  margin: 0;
  font-size: 0.92rem;
  line-height: 1.5;
}

/* 响应式 */
@media (max-width: 768px) {
  .page-hero {
    padding: 26px 20px 22px;
    border-radius: 10px;
  }
  .tab-navigation {
    padding: 14px;
  }
  .knowledge-features {
    grid-template-columns: 1fr;
    gap: 14px;
  }
  .feature-card {
    flex-direction: column;
    text-align: center;
    gap: 12px;
    padding: 15px;
  }
  .cs408-tabs :deep(.el-tabs__item) {
    padding: 0 10px;
    font-size: 0.85rem;
    height: 42px;
    line-height: 42px;
  }
}

@media (max-width: 480px) {
  .page-hero {
    padding: 20px 16px 18px;
  }
  .tab-navigation {
    padding: 10px;
  }
  .cs408-tabs :deep(.el-tabs__header) {
    margin-bottom: 14px;
  }
  .cs408-tabs :deep(.el-tabs__item) {
    padding: 0 8px;
    font-size: 0.8rem;
    height: 38px;
    line-height: 38px;
  }
  .knowledge-content {
    padding: 20px 10px;
  }
  .knowledge-content h3 {
    font-size: 1.3rem;
  }
}

@media (prefers-reduced-motion: reduce) {
  .feature-card {
    transition: none;
  }
}
</style>