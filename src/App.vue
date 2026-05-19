<template>
  <div class="min-h-screen bg-[#0a0a0f] text-gray-100 overflow-x-hidden">
    <!-- Nav -->
    <nav class="fixed top-0 w-full z-50 backdrop-blur-xl bg-[#0a0a0f]/70 border-b border-white/5">
      <div class="max-w-5xl mx-auto px-6 h-16 flex items-center justify-between">
        <span class="text-lg font-bold tracking-wider bg-gradient-to-r from-indigo-400 to-purple-400 bg-clip-text text-transparent">Ahiose</span>
        <div class="hidden sm:flex items-center gap-8 text-sm text-gray-400">
          <a v-for="item in navItems" :key="item.href" :href="item.href"
             class="hover:text-white transition-colors duration-300">{{ item.label }}</a>
        </div>
        <a href="#contact"
           class="px-4 py-2 text-sm rounded-full bg-gradient-to-r from-indigo-600 to-purple-600 hover:from-indigo-500 hover:to-purple-500 transition-all duration-300">
          联系我
        </a>
      </div>
    </nav>

    <!-- Hero -->
    <section class="min-h-screen flex items-center justify-center relative pt-16">
      <div class="absolute inset-0 bg-gradient-to-b from-indigo-950/20 via-transparent to-transparent pointer-events-none" />
      <div class="max-w-5xl mx-auto px-6 text-center relative z-10">
        <div class="inline-flex items-center gap-2 px-4 py-2 rounded-full bg-white/5 border border-white/10 text-sm text-gray-400 mb-8">
          <span class="w-2 h-2 rounded-full bg-green-400 animate-pulse" />
          Open to opportunities
        </div>
        <h1 class="text-5xl sm:text-7xl font-extrabold leading-tight mb-6">
          <span class="bg-gradient-to-r from-indigo-300 via-purple-300 to-pink-300 bg-clip-text text-transparent">
            Hi, I'm Ahiose
          </span>
        </h1>
        <p class="text-xl sm:text-2xl text-gray-400 mb-4 font-light">Software Engineer · AI Agent Developer</p>
        <p class="text-gray-500 max-w-xl mx-auto mb-10 leading-relaxed">
          六年全栈开发经验，专注后端架构与 AI Agent 系统设计。
          从微服务到多智能体协作，从数据库设计到提示词工程。
        </p>
        <div class="flex items-center justify-center gap-4">
          <a href="#projects"
             class="px-8 py-3 rounded-full bg-gradient-to-r from-indigo-600 to-purple-600 hover:from-indigo-500 hover:to-purple-500 font-medium transition-all duration-300 shadow-lg shadow-indigo-600/25">
            看我的项目
          </a>
          <a href="#contact"
             class="px-8 py-3 rounded-full border border-white/20 hover:border-white/40 font-medium transition-all duration-300">
            联系我
          </a>
        </div>
      </div>
    </section>

    <!-- About -->
    <section id="about" class="py-24 relative">
      <div class="max-w-5xl mx-auto px-6">
        <h2 class="text-3xl font-bold mb-12 text-center">
          <span class="bg-gradient-to-r from-indigo-400 to-purple-400 bg-clip-text text-transparent">关于我</span>
        </h2>
        <div class="grid md:grid-cols-3 gap-8">
          <div v-for="item in aboutCards" :key="item.title"
               class="group p-8 rounded-2xl bg-white/[0.02] border border-white/5 hover:bg-white/[0.04] hover:border-indigo-500/20 transition-all duration-500">
            <div class="text-3xl mb-4">{{ item.icon }}</div>
            <h3 class="text-lg font-semibold mb-3">{{ item.title }}</h3>
            <p class="text-gray-500 text-sm leading-relaxed">{{ item.desc }}</p>
          </div>
        </div>
      </div>
    </section>

    <!-- Skills -->
    <section id="skills" class="py-24 bg-white/[0.01]">
      <div class="max-w-5xl mx-auto px-6">
        <h2 class="text-3xl font-bold mb-12 text-center">
          <span class="bg-gradient-to-r from-indigo-400 to-purple-400 bg-clip-text text-transparent">技术栈</span>
        </h2>
        <div class="space-y-8">
          <div v-for="group in skillGroups" :key="group.category" class="group">
            <h3 class="text-sm font-medium text-gray-500 mb-4 tracking-wider uppercase">{{ group.category }}</h3>
            <div class="flex flex-wrap gap-3">
              <span v-for="skill in group.items" :key="skill"
                    class="px-4 py-2 rounded-lg text-sm bg-white/5 border border-white/10 text-gray-300
                           hover:border-indigo-500/30 hover:text-indigo-300 hover:bg-indigo-950/20
                           transition-all duration-300 cursor-default">
                {{ skill }}
              </span>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Projects -->
    <section id="projects" class="py-24">
      <div class="max-w-5xl mx-auto px-6">
        <h2 class="text-3xl font-bold mb-12 text-center">
          <span class="bg-gradient-to-r from-indigo-400 to-purple-400 bg-clip-text text-transparent">项目</span>
        </h2>
        <div class="grid md:grid-cols-2 gap-6">
          <div v-for="(proj, i) in projects" :key="i"
               class="group p-6 rounded-2xl bg-white/[0.02] border border-white/5 hover:border-indigo-500/20 transition-all duration-500">
            <div class="flex items-center gap-3 mb-4">
              <span class="text-2xl">{{ proj.icon }}</span>
              <h3 class="font-semibold">{{ proj.title }}</h3>
            </div>
            <p class="text-gray-500 text-sm leading-relaxed mb-4">{{ proj.desc }}</p>
            <div class="flex flex-wrap gap-2">
              <span v-for="tag in proj.tags" :key="tag"
                    class="px-2 py-1 text-xs rounded-md bg-indigo-950/30 text-indigo-300 border border-indigo-900/30">
                {{ tag }}
              </span>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Contact -->
    <section id="contact" class="py-24 bg-white/[0.01]">
      <div class="max-w-3xl mx-auto px-6 text-center">
        <h2 class="text-3xl font-bold mb-6">
          <span class="bg-gradient-to-r from-indigo-400 to-purple-400 bg-clip-text text-transparent">联系我</span>
        </h2>
        <p class="text-gray-500 mb-10">有想法想聊聊？或者只是想认识一下？随时欢迎。</p>
        <div class="flex flex-wrap items-center justify-center gap-6">
          <a v-for="link in contactLinks" :key="link.label" :href="link.url"
             target="_blank" rel="noopener noreferrer"
             class="flex items-center gap-3 px-6 py-3 rounded-full border border-white/10 hover:border-indigo-500/30 hover:bg-white/[0.03] transition-all duration-300 text-sm">
            <span>{{ link.icon }}</span>
            <span>{{ link.label }}</span>
          </a>
        </div>
      </div>
    </section>

    <!-- Footer -->
    <footer class="py-8 border-t border-white/5">
      <div class="max-w-5xl mx-auto px-6 text-center text-sm text-gray-600">
        <p>© {{ new Date().getFullYear() }} Ahiose. Built with Vue 3 + Tailwind.</p>
      </div>
    </footer>
  </div>
</template>

<script setup>
const navItems = [
  { label: '关于', href: '#about' },
  { label: '技能', href: '#skills' },
  { label: '项目', href: '#projects' },
  { label: '联系', href: '#contact' },
]

const aboutCards = [
  { icon: '🧩', title: '后端架构', desc: '六年 Java 全栈经验，精通 Spring Boot 生态、DDD 领域驱动设计、六边形架构，擅长构建高可扩展的企业级系统。' },
  { icon: '🤖', title: 'AI Agent 开发', desc: '深入理解 ReAct 循环、Function Calling、Tool Registry 等 Agent 核心模式。从 Hermes Agent 源码到自研多工具编排引擎。' },
  { icon: '⚡', title: '全链路交付', desc: '从需求分析到架构设计到落地部署，精通 Docker 容器化、CI/CD、数据库设计，能独立完成项目全生命周期。' },
]

const skillGroups = [
  {
    category: 'Languages',
    items: ['Java', 'Python', 'JavaScript', 'TypeScript', 'SQL'],
  },
  {
    category: 'Backend',
    items: ['Spring Boot', 'FastAPI', 'MyBatis', 'JPA', 'RESTful API', 'gRPC'],
  },
  {
    category: 'AI / Agent',
    items: ['LangGraph', 'DeepSeek API', 'OpenAI SDK', 'Prompt Engineering', 'RAG', 'Tool Registry', 'ReAct Loop'],
  },
  {
    category: 'DevOps & Tools',
    items: ['Docker', 'PostgreSQL', 'Redis', 'Git', 'CI/CD', 'Linux'],
  },
]

const projects = [
  {
    icon: '🏗️',
    title: 'cocagent — 多租户自适应规划引擎',
    desc: '基于 DeepSeek 的 AI Agent 系统。完整的 ReAct 循环 + Tool Registry + Redis 会话管理 + Chroma 向量检索 + 动态上下文注入。DDD 架构，FastAPI 异步后端。',
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
    title: 'Hermes Agent 源码研究与扩展',
    desc: '深入研读 Hermes Agent 核心源码：run_conversation() 循环、Tool Registry 注册机制、多平台 Gateway 架构，提交功能性改进。',
    tags: ['Python', 'Agent Framework', 'Open Source'],
  },
  {
    icon: '📊',
    title: 'Sub2API — AI API 网关部署',
    desc: '搭建并维护 Sub2API 中转服务，管理多上游 API 的路由、负载均衡和令牌分发，支持多种 AI 提供商。',
    tags: ['Docker', 'PostgreSQL', 'Redis', 'DevOps'],
  },
]

const contactLinks = [
  { icon: '🐙', label: 'GitHub', url: 'https://github.com/ahiose' },
  { icon: '📧', label: 'Email', url: 'mailto:ahiose@example.com' },
]
</script>
