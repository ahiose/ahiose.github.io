<template>
  <div class="min-h-screen bg-[#07070b] text-gray-100 font-sans antialiased selection:bg-indigo-500/30">
    <!-- ========== NAV ========== -->
    <nav ref="navRef" class="fixed top-0 w-full z-50 transition-all duration-500"
         :class="scrolled ? 'bg-[#07070b]/80 backdrop-blur-xl border-b border-white/5' : 'bg-transparent'">
      <div class="max-w-6xl mx-auto px-6 h-16 flex items-center justify-between">
        <a href="#hero" class="text-lg font-bold tracking-wider">
          <span class="bg-gradient-to-r from-indigo-400 via-purple-400 to-pink-400 bg-clip-text text-transparent">Ahiose</span>
          <span class="text-gray-600 ml-1 font-mono text-xs">.dev</span>
        </a>
        <div class="hidden md:flex items-center gap-8 text-sm">
          <a v-for="item in navItems" :key="item.href" :href="item.href"
             class="text-gray-500 hover:text-white transition-colors duration-300 relative group">
            {{ item.label }}
            <span class="absolute -bottom-1 left-0 w-0 h-[2px] bg-gradient-to-r from-indigo-400 to-purple-400 group-hover:w-full transition-all duration-300"></span>
          </a>
        </div>
        <a href="#contact"
           class="px-5 py-2 text-sm rounded-full bg-gradient-to-r from-indigo-600 to-purple-600 hover:from-indigo-500 hover:to-purple-500 transition-all duration-300 shadow-lg shadow-indigo-600/20">
          联系我
        </a>
      </div>
    </nav>

    <!-- ========== HERO ========== -->
    <section id="hero" class="relative min-h-screen flex items-center justify-center overflow-hidden">
      <!-- Dynamic BG -->
      <div class="absolute inset-0">
        <div class="absolute inset-0 bg-gradient-to-br from-indigo-950/40 via-[#07070b] to-purple-950/30" />
        <div class="absolute top-1/4 left-1/4 w-96 h-96 bg-indigo-500/10 rounded-full blur-[120px] animate-pulse-slow" />
        <div class="absolute bottom-1/4 right-1/4 w-96 h-96 bg-purple-500/10 rounded-full blur-[120px] animate-pulse-slow animation-delay-2000" />
        <!-- Grid overlay -->
        <div class="absolute inset-0 opacity-[0.03]" style="background-image: linear-gradient(rgba(255,255,255,.1) 1px, transparent 1px), linear-gradient(90deg, rgba(255,255,255,.1) 1px, transparent 1px); background-size: 60px 60px;"></div>
      </div>

      <div class="relative z-10 max-w-4xl mx-auto px-6 text-center">
        <div class="inline-flex items-center gap-2 px-4 py-2 rounded-full bg-white/[0.03] border border-white/10 text-sm text-gray-400 mb-8
                    hover:border-indigo-500/30 transition-all duration-500">
          <span class="w-2 h-2 rounded-full bg-emerald-400 animate-pulse" />
          <span>Open to opportunities</span>
        </div>

        <div class="mb-6">
          <h1 class="text-5xl md:text-7xl lg:text-8xl font-extrabold leading-[1.1] mb-4">
            <span class="bg-gradient-to-r from-indigo-300 via-purple-300 to-pink-300 bg-clip-text text-transparent">
              Hi, I'm Ahiose
            </span>
          </h1>
          <div class="h-10 flex items-center justify-center">
            <span class="text-xl md:text-2xl text-gray-400 font-light">{{ currentRole }}</span>
            <span class="ml-1 w-[3px] h-7 bg-indigo-400 animate-blink" />
          </div>
        </div>

        <p class="text-gray-500 max-w-2xl mx-auto mb-10 leading-relaxed text-lg">
          六年全栈开发 · 专注后端架构与 AI Agent 系统设计。<br class="hidden sm:block">
          从微服务到多智能体协作，从数据库设计到提示词工程。
        </p>

        <div class="flex items-center justify-center gap-4 flex-wrap">
          <a href="#projects"
             class="group relative px-8 py-3 rounded-full bg-gradient-to-r from-indigo-600 to-purple-600 font-medium
                    transition-all duration-300 shadow-lg shadow-indigo-600/25 hover:shadow-indigo-600/40 hover:-translate-y-0.5">
            看我的项目
            <span class="inline-block transition-transform duration-300 group-hover:translate-x-1">→</span>
          </a>
          <a href="#contact"
             class="px-8 py-3 rounded-full border border-white/20 hover:border-white/40 hover:bg-white/[0.03] transition-all duration-300">
            联系我
          </a>
        </div>

        <!-- Social -->
        <div class="flex items-center justify-center gap-6 mt-12">
          <a v-for="s in socialLinks" :key="s.label" :href="s.url" target="_blank" rel="noopener noreferrer"
             class="text-gray-600 hover:text-white transition-all duration-300 hover:-translate-y-0.5"
             :title="s.label">
            <span class="text-xl">{{ s.icon }}</span>
          </a>
        </div>
      </div>

      <!-- Scroll indicator -->
      <div class="absolute bottom-8 left-1/2 -translate-x-1/2 flex flex-col items-center gap-2 text-gray-600 animate-bounce">
        <span class="text-xs">向下滚动</span>
        <svg class="w-4 h-4" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 14l-7 7m0 0l-7-7m7 7V3"/></svg>
      </div>
    </section>

    <!-- ========== ABOUT ========== -->
    <section id="about" class="py-24 relative">
      <div class="max-w-6xl mx-auto px-6">
        <div class="text-center mb-16">
          <span class="text-xs tracking-[0.2em] uppercase text-indigo-400 font-medium">About</span>
          <h2 class="text-3xl md:text-4xl font-bold mt-3">
            <span class="bg-gradient-to-r from-indigo-400 to-purple-400 bg-clip-text text-transparent">关于我</span>
          </h2>
        </div>

        <!-- Stats -->
        <div class="grid grid-cols-2 md:grid-cols-4 gap-4 mb-16">
          <div v-for="stat in stats" :key="stat.label"
               class="text-center p-6 rounded-2xl bg-white/[0.02] border border-white/5">
            <div class="text-2xl font-bold bg-gradient-to-r from-indigo-400 to-purple-400 bg-clip-text text-transparent">{{ stat.value }}</div>
            <div class="text-sm text-gray-500 mt-1">{{ stat.label }}</div>
          </div>
        </div>

        <div class="grid md:grid-cols-3 gap-6">
          <div v-for="(card, i) in aboutCards" :key="card.title"
               class="group p-8 rounded-2xl bg-white/[0.02] border border-white/5 hover:bg-white/[0.04] hover:border-indigo-500/20 transition-all duration-500"
               :style="{ transitionDelay: `${i * 100}ms` }">
            <div class="text-3xl mb-4 group-hover:scale-110 transition-transform duration-300">{{ card.icon }}</div>
            <h3 class="text-lg font-semibold mb-3">{{ card.title }}</h3>
            <p class="text-gray-500 text-sm leading-relaxed">{{ card.desc }}</p>
          </div>
        </div>
      </div>
    </section>

    <!-- ========== EXPERIENCE ========== -->
    <section id="experience" class="py-24 bg-white/[0.01]">
      <div class="max-w-4xl mx-auto px-6">
        <div class="text-center mb-16">
          <span class="text-xs tracking-[0.2em] uppercase text-indigo-400 font-medium">Experience</span>
          <h2 class="text-3xl md:text-4xl font-bold mt-3">
            <span class="bg-gradient-to-r from-indigo-400 to-purple-400 bg-clip-text text-transparent">经历</span>
          </h2>
        </div>

        <div class="relative">
          <div class="absolute left-6 md:left-1/2 top-0 bottom-0 w-[2px] bg-gradient-to-b from-indigo-500/50 via-purple-500/30 to-transparent" />
          <div class="space-y-12">
            <div v-for="(exp, i) in experiences" :key="exp.title"
                 class="relative flex flex-col md:flex-row gap-6 md:gap-0"
                 :class="i % 2 === 0 ? 'md:flex-row' : 'md:flex-row-reverse'">
              <div class="hidden md:block md:w-1/2" />
              <div class="absolute left-6 md:left-1/2 w-3 h-3 rounded-full bg-indigo-400 border-2 border-[#07070b] -translate-x-1/2 mt-1.5 z-10 shadow-lg shadow-indigo-500/30" />
              <div class="md:w-1/2 pl-12 md:pl-0"
                   :class="i % 2 === 0 ? 'md:pr-10 md:text-right' : 'md:pl-10'">
                <span class="text-xs text-indigo-400 font-mono">{{ exp.period }}</span>
                <h3 class="text-lg font-semibold mt-1">{{ exp.title }}</h3>
                <p class="text-sm text-gray-400">{{ exp.company }}</p>
                <p class="text-sm text-gray-500 mt-2 leading-relaxed">{{ exp.desc }}</p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- ========== SKILLS ========== -->
    <section id="skills" class="py-24">
      <div class="max-w-6xl mx-auto px-6">
        <div class="text-center mb-16">
          <span class="text-xs tracking-[0.2em] uppercase text-indigo-400 font-medium">Skills</span>
          <h2 class="text-3xl md:text-4xl font-bold mt-3">
            <span class="bg-gradient-to-r from-indigo-400 to-purple-400 bg-clip-text text-transparent">技术栈</span>
          </h2>
        </div>
        <div class="grid md:grid-cols-2 gap-8">
          <div v-for="group in skillGroups" :key="group.category"
               class="p-6 rounded-2xl bg-white/[0.02] border border-white/5">
            <h3 class="text-sm font-medium text-gray-400 mb-6 tracking-wider uppercase">{{ group.category }}</h3>
            <div class="flex flex-wrap gap-2">
              <span v-for="skill in group.items" :key="skill.name"
                    class="group/skill relative px-4 py-2 rounded-lg text-sm border transition-all duration-300 cursor-default"
                    :class="skill.active
                      ? 'bg-indigo-950/30 border-indigo-800/40 text-indigo-300 hover:bg-indigo-950/40 hover:border-indigo-600/50'
                      : 'bg-white/[0.02] border-white/10 text-gray-500 hover:border-gray-600/30 hover:text-gray-300'">
                {{ skill.name }}
                <span v-if="skill.level"
                      class="absolute -top-1 -right-1 w-2 h-2 rounded-full"
                      :class="skill.level === 'expert' ? 'bg-emerald-400' : skill.level === 'adv' ? 'bg-indigo-400' : 'bg-gray-500'" />
              </span>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- ========== PROJECTS ========== -->
    <section id="projects" class="py-24 bg-white/[0.01]">
      <div class="max-w-6xl mx-auto px-6">
        <div class="text-center mb-16">
          <span class="text-xs tracking-[0.2em] uppercase text-indigo-400 font-medium">Projects</span>
          <h2 class="text-3xl md:text-4xl font-bold mt-3">
            <span class="bg-gradient-to-r from-indigo-400 to-purple-400 bg-clip-text text-transparent">项目</span>
          </h2>
        </div>
        <div class="grid md:grid-cols-2 gap-6">
          <div v-for="(proj, i) in projects" :key="i"
               class="group p-6 rounded-2xl bg-white/[0.02] border border-white/5 hover:border-indigo-500/20 transition-all duration-500 hover:-translate-y-1">
            <div class="flex items-center gap-3 mb-4">
              <span class="text-2xl group-hover:scale-110 transition-transform duration-300">{{ proj.icon }}</span>
              <h3 class="font-semibold group-hover:text-indigo-300 transition-colors">{{ proj.title }}</h3>
            </div>
            <p class="text-gray-500 text-sm leading-relaxed mb-4">{{ proj.desc }}</p>
            <div class="flex flex-wrap gap-2">
              <span v-for="tag in proj.tags" :key="tag"
                    class="px-2 py-1 text-xs rounded-md bg-indigo-950/20 text-indigo-400/70 border border-indigo-900/20">
                {{ tag }}
              </span>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- ========== CONTACT ========== -->
    <section id="contact" class="py-24 relative overflow-hidden">
      <div class="absolute inset-0 bg-gradient-to-b from-purple-950/10 via-transparent to-transparent pointer-events-none" />
      <div class="max-w-3xl mx-auto px-6 text-center relative z-10">
        <div class="text-center mb-12">
          <span class="text-xs tracking-[0.2em] uppercase text-indigo-400 font-medium">Contact</span>
          <h2 class="text-3xl md:text-4xl font-bold mt-3">
            <span class="bg-gradient-to-r from-indigo-400 to-purple-400 bg-clip-text text-transparent">联系我</span>
          </h2>
          <p class="text-gray-500 mt-4">有想法想聊聊？或者只是想认识一下？随时欢迎。</p>
        </div>

        <div class="flex flex-wrap items-center justify-center gap-4 mb-12">
          <a v-for="link in contactLinks" :key="link.label" :href="link.url"
             target="_blank" rel="noopener noreferrer"
             class="flex items-center gap-3 px-6 py-3 rounded-full border border-white/10 hover:border-indigo-500/30 hover:bg-white/[0.03] hover:-translate-y-0.5 transition-all duration-300 text-sm">
            <span>{{ link.icon }}</span>
            <span>{{ link.label }}</span>
          </a>
        </div>

        <div class="max-w-md mx-auto">
          <form @submit.prevent="handleSubmit" class="space-y-4 text-left">
            <input v-model="form.name" type="text" placeholder="你的名字"
                   class="w-full px-4 py-3 rounded-xl bg-white/[0.03] border border-white/10 text-white placeholder-gray-600
                          focus:outline-none focus:border-indigo-500/40 focus:bg-white/[0.05] transition-all duration-300 text-sm">
            <input v-model="form.email" type="email" placeholder="邮箱"
                   class="w-full px-4 py-3 rounded-xl bg-white/[0.03] border border-white/10 text-white placeholder-gray-600
                          focus:outline-none focus:border-indigo-500/40 focus:bg-white/[0.05] transition-all duration-300 text-sm">
            <textarea v-model="form.message" rows="4" placeholder="想说什么？"
                      class="w-full px-4 py-3 rounded-xl bg-white/[0.03] border border-white/10 text-white placeholder-gray-600
                             focus:outline-none focus:border-indigo-500/40 focus:bg-white/[0.05] transition-all duration-300 text-sm resize-none"></textarea>
            <button type="submit"
                    class="w-full py-3 rounded-xl bg-gradient-to-r from-indigo-600 to-purple-600 hover:from-indigo-500 hover:to-purple-500
                           font-medium transition-all duration-300 shadow-lg shadow-indigo-600/20 hover:shadow-indigo-600/30 text-sm">
              {{ submitted ? '✓ 已发送' : '发送消息' }}
            </button>
          </form>
        </div>
      </div>
    </section>

    <!-- ========== FOOTER ========== -->
    <footer class="py-8 border-t border-white/5">
      <div class="max-w-6xl mx-auto px-6 flex flex-col md:flex-row items-center justify-between gap-4">
        <div class="text-sm text-gray-600">
          © {{ new Date().getFullYear() }} Ahiose. Built with Vue 3 + Tailwind.
        </div>
        <div class="flex items-center gap-4">
          <a v-for="s in socialLinks" :key="s.label" :href="s.url" target="_blank" rel="noopener noreferrer"
             class="text-gray-600 hover:text-white transition-colors text-sm">{{ s.label }}</a>
        </div>
        <a href="#hero" class="text-gray-600 hover:text-white transition-colors text-sm">↑ 回到顶部</a>
      </div>
    </footer>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

// ── Nav ──
const navItems = [
  { label: '关于', href: '#about' },
  { label: '经历', href: '#experience' },
  { label: '技能', href: '#skills' },
  { label: '项目', href: '#projects' },
  { label: '联系', href: '#contact' },
]

const scrolled = ref(false)
const navRef = ref(null)

const handleScroll = () => {
  scrolled.value = window.scrollY > 50
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll, { passive: true })
})
onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})

// ── Hero Typewriter ──
const roles = ['Software Engineer', 'AI Agent Developer', 'Backend Architect', 'Open Source Contributor']
const currentRole = ref(roles[0])
let roleIndex = 0

onMounted(() => {
  setInterval(() => {
    roleIndex = (roleIndex + 1) % roles.length
    currentRole.value = roles[roleIndex]
  }, 3000)
})

// ── Social ──
const socialLinks = [
  { icon: '🐙', label: 'GitHub', url: 'https://github.com/ahiose' },
  { icon: '📧', label: 'Email', url: 'mailto:ahiosea@gmail.com' },
  { icon: '💬', label: 'X(Twitter)', url: 'https://x.com/ahiose' },
]

// ── Stats ──
const stats = [
  { value: '6+', label: '年开发经验' },
  { value: '50+', label: '完成项目' },
  { value: '15+', label: '技术栈覆盖' },
  { value: '∞', label: '学习热情' },
]

// ── About ──
const aboutCards = [
  { icon: '🧩', title: '后端架构', desc: '六年 Java 全栈经验，精通 Spring Boot 生态、DDD 领域驱动设计、六边形架构，擅长构建高可扩展的企业级系统。' },
  { icon: '🤖', title: 'AI Agent 开发', desc: '深入理解 ReAct 循环、Function Calling、Tool Registry 等 Agent 核心模式。从 Hermes Agent 源码到自研多工具编排引擎。' },
  { icon: '⚡', title: '全链路交付', desc: '从需求分析到架构设计到落地部署，精通 Docker 容器化、CI/CD、数据库设计，能独立完成项目全生命周期。' },
]

// ── Experience ──
const experiences = [
  {
    period: '2024 — 至今',
    title: 'AI Agent 开发',
    company: '独立开发者 / 开源贡献',
    desc: '深入研读 Hermes Agent 核心源码，理解 ReAct 循环、Tool Registry 注册机制。独立开发 cocagent 多租户规划引擎，集成 DeepSeek + LangGraph + Chroma RAG。',
  },
  {
    period: '2020 — 2024',
    title: '高级后端工程师',
    company: '某科技公司',
    desc: '负责核心业务系统的架构设计与开发。主导从单体架构到微服务架构的演进，落地 DDD 领域驱动设计和六边形架构，服务 QPS 提升 3 倍。',
  },
  {
    period: '2018 — 2020',
    title: 'Java 开发工程师',
    company: '某互联网公司',
    desc: '参与电商中台系统建设，负责订单、支付、库存等核心模块。熟练 MySQL 调优、Redis 缓存策略、消息队列等中间件应用。',
  },
]

// ── Skills ──
const skillGroups = [
  {
    category: 'Languages',
    items: [
      { name: 'Java', level: 'expert', active: true },
      { name: 'Python', level: 'expert', active: true },
      { name: 'TypeScript', level: 'adv', active: true },
      { name: 'SQL', level: 'expert', active: true },
      { name: 'Go', level: 'beginner', active: false },
    ],
  },
  {
    category: 'Backend',
    items: [
      { name: 'Spring Boot', level: 'expert', active: true },
      { name: 'FastAPI', level: 'adv', active: true },
      { name: 'MyBatis / JPA', level: 'expert', active: true },
      { name: 'PostgreSQL', level: 'expert', active: true },
      { name: 'Redis', level: 'adv', active: true },
      { name: 'Docker', level: 'adv', active: true },
    ],
  },
  {
    category: 'AI / Agent',
    items: [
      { name: 'LangGraph', level: 'adv', active: true },
      { name: 'DeepSeek API', level: 'adv', active: true },
      { name: 'Prompt Engineering', level: 'expert', active: true },
      { name: 'RAG / Chroma', level: 'adv', active: true },
      { name: 'Function Calling', level: 'expert', active: true },
      { name: 'Hermes Agent', level: 'adv', active: true },
    ],
  },
  {
    category: 'DevOps & Tools',
    items: [
      { name: 'Git', level: 'expert', active: true },
      { name: 'Linux', level: 'adv', active: true },
      { name: 'Nginx', level: 'adv', active: true },
      { name: 'GitHub Actions', level: 'adv', active: true },
    ],
  },
]

// ── Projects ──
const projects = [
  {
    icon: '🏗️',
    title: 'cocagent — 多租户规划引擎',
    desc: '基于 DeepSeek 的 AI Agent 系统。完整 ReAct 循环 + Tool Registry + Redis 会话 + Chroma 向量检索。DDD 架构，FastAPI 异步后端，Docker 编排。',
    tags: ['Python', 'FastAPI', 'DeepSeek', 'LangGraph', 'PostgreSQL', 'Docker'],
  },
  {
    icon: '🎬',
    title: 'AI 连续剧内容工厂',
    desc: '从剧本到成片的自动化流水线。Imagen 角色一致性出图 + Edge TTS 双角色配音 + FFmpeg 合成，打通 Prompt→出图→配音→剪辑全链路。',
    tags: ['Prompt Engineering', 'Gemini Pro', 'FFmpeg', 'TTS', 'AppleScript'],
  },
  {
    icon: '🔌',
    title: 'Hermes Agent 源码研究',
    desc: '深入研读 Hermes Agent 核心源码：run_conversation() 循环、Tool Registry、Gateway 多平台架构。理解 Agent 框架的核心设计模式。',
    tags: ['Python', 'Agent Framework', 'Open Source'],
  },
  {
    icon: '📊',
    title: 'Sub2API — AI API 网关',
    desc: '搭建并维护 Sub2API 中转服务，管理多上游 API 的路由、负载均衡和令牌分发。生产级 Docker Compose + PostgreSQL + Redis 部署。',
    tags: ['Docker', 'PostgreSQL', 'Redis', 'DevOps'],
  },
]

// ── Contact ──
const contactLinks = [
  { icon: '🐙', label: 'GitHub', url: 'https://github.com/ahiose' },
  { icon: '📧', label: 'Email', url: 'mailto:ahiosea@gmail.com' },
]

const form = ref({ name: '', email: '', message: '' })
const submitted = ref(false)

const handleSubmit = () => {
  submitted.value = true
  setTimeout(() => { submitted.value = false }, 3000)
  // In production: send to your backend
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800&display=swap');

html { scroll-behavior: smooth; }
body { font-family: 'Inter', sans-serif; }

@keyframes blink {
  0%, 100% { opacity: 1; }
  50% { opacity: 0; }
}
@keyframes pulse-slow {
  0%, 100% { transform: scale(1); opacity: 0.3; }
  50% { transform: scale(1.05); opacity: 0.5; }
}
@keyframes bounce {
  0%, 100% { transform: translateY(0); }
  50% { transform: translateY(8px); }
}

.animate-blink { animation: blink 1s step-end infinite; }
.animate-pulse-slow { animation: pulse-slow 6s ease-in-out infinite; }
.animation-delay-2000 { animation-delay: 2s; }
.animate-bounce { animation: bounce 2s ease-in-out infinite; }
</style>
