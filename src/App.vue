<template>
  <div class="relative font-sans transition-colors duration-500 min-h-screen selection:bg-purple-400/30"
       :class="isDark ? 'text-slate-300' : 'text-slate-600'">
    <div class="fixed inset-0 -z-50 overflow-hidden pointer-events-none">
      <div class="absolute inset-0 transition-colors duration-500" 
           :class="isDark ? 'bg-[#0A0118]' : 'bg-[#FFFFFF]'"></div>
      <div class="absolute inset-0">
        <div class="absolute -top-[20%] -right-[10%] w-[70vw] h-[70vw] rounded-full filter blur-[80px] animate-wave-slow transition-all duration-500"
             :class="isDark ? 'mix-blend-screen opacity-50' : 'mix-blend-multiply opacity-40'"
             :style="{ 
               background: 'radial-gradient(circle, rgba(233, 213, 255, 0.8) 0%, rgba(192, 132, 252, 0) 70%)',
               transform: 'rotate(-15deg) skewX(-20deg)'
             }">
        </div>
        <div class="absolute top-[20%] -left-[10%] w-[80vw] h-[60vw] rounded-full filter blur-[90px] animate-wave-slower animation-delay-2000 transition-all duration-500"
             :class="isDark ? 'mix-blend-screen opacity-50' : 'mix-blend-multiply opacity-40'"
             :style="{ 
               background: 'radial-gradient(circle, rgba(34, 211, 238, 0.8) 0%, rgba(34, 211, 238, 0) 70%)',
               transform: 'rotate(15deg) skewX(20deg)'
             }">
        </div>
        <div class="absolute -bottom-[30%] right-[0%] w-[80vw] h-[80vw] rounded-full filter blur-[100px] animate-pulse-slow transition-all duration-500"
             :class="isDark ? 'mix-blend-screen opacity-50' : 'mix-blend-multiply opacity-40'"
             :style="{ 
               background: 'radial-gradient(circle, rgba(167, 139, 250, 0.8) 0%, rgba(167, 139, 250, 0) 70%)' 
             }">
        </div>
      </div>
      <div class="absolute inset-0 transition-opacity duration-500" 
           :class="isDark ? 'opacity-[0.04]' : 'opacity-[0.02]'"
           style="background-image: url('https://grainy-gradients.vercel.app/noise.svg');">
      </div>
    </div>
    <nav :class="isDark ? 'bg-[#0A0118]/60 border-white/5' : 'bg-white/60 border-slate-200/40'" class="sticky top-0 z-50 w-full border-b backdrop-blur-md transition-all">
      <div class="mx-auto max-w-7xl px-6 py-4">
        <div class="flex justify-between items-center">
          <div class="group cursor-pointer" @click="scrollToTop">
            <div class="text-xl font-black tracking-tighter" :class="isDark ? 'text-white' : 'text-slate-800'">
              CRISTOBAL<span class="text-purple-200 group-hover:animate-pulse">.</span>DEV
            </div>
          </div>
          
          <div class="flex items-center gap-4 md:gap-10">
            <ul class="hidden md:flex gap-8 text-[10px] font-bold uppercase tracking-[0.2em]">
              <li v-for="link in ['about', 'skills', 'projects']" :key="link">
                <a :href="'#' + link" class="transition-colors relative group"
                   :class="isDark ? 'hover:text-purple-200' : 'text-slate-600 hover:text-purple-400'">
                  {{ link }}
                  <span class="absolute -bottom-1 left-0 w-0 h-0.5 bg-purple-200 transition-all group-hover:w-full"></span>
                </a>
              </li>
            </ul>
            
            <button @click="isDark = !isDark" class="relative w-12 h-6 rounded-full border transition-all flex items-center px-1" :class="isDark ? 'border-slate-700 bg-slate-900' : 'border-slate-300 bg-white'">
              <div class="w-4 h-4 rounded-full transition-all transform shadow-sm" :class="[isDark ? 'translate-x-6 bg-purple-200' : 'translate-x-0 bg-yellow-400']"></div>
            </button>

            <button @click="isMenuOpen = !isMenuOpen" class="md:hidden text-2xl focus:outline-none transition-transform active:scale-90" :class="isDark ? 'text-white' : 'text-slate-800'">
              <i :class="isMenuOpen ? 'fa-solid fa-xmark' : 'fa-solid fa-bars'"></i>
            </button>
          </div>
        </div>

        <transition enter-active-class="transition duration-300 ease-out" enter-from-class="transform -translate-y-4 opacity-0" enter-to-class="transform translate-y-0 opacity-100" leave-active-class="transition duration-200 ease-in" leave-from-class="transform translate-y-0 opacity-100" leave-to-class="transform -translate-y-4 opacity-0">
          <div v-show="isMenuOpen" class="md:hidden mt-4 pb-4 border-t" :class="isDark ? 'border-slate-800' : 'border-slate-200'">
            <ul class="flex flex-col gap-4 mt-4 text-xs font-bold uppercase tracking-[0.2em]">
              <li v-for="link in ['about', 'skills', 'projects']" :key="link">
                <a :href="'#' + link" @click="isMenuOpen = false" class="block py-2 hover:text-purple-200 transition-colors" :class="isDark ? 'text-slate-200' : 'text-slate-800'">
                  {{ link }}
                </a>
              </li>
            </ul>
          </div>
        </transition>
      </div>
    </nav>
    <transition appear name="fade-slide">
      <div class="mx-auto max-w-7xl px-6 py-20 lg:py-32">
        <div class="lg:flex lg:gap-24">
          
          <header class="lg:sticky lg:top-32 lg:h-fit lg:w-1/3 flex flex-col mb-20 lg:mb-0">
            <div class="space-y-8">
              <h1 class="text-5xl md:text-6xl font-black tracking-tight leading-none" :class="isDark ? 'text-white' : 'text-slate-800'">
                Building digital <br/>
                <span class="text-transparent bg-clip-text bg-gradient-to-r"
                      :class="isDark ? 'from-purple-400 to-cyan-500' : 'from-purple-200 to-blue-500'">
                  excellence.
                </span>
              </h1>
              <div class="flex flex-col gap-3">
                <p class="text-xl md:text-2xl font-medium" :class="isDark ? 'text-slate-300' : 'text-slate-600'">
                  Hi! I'm <span class="font-bold" :class="isDark ? 'text-purple-200' : 'text-purple-400'">Alexandra Nicole Cristobal</span>
                </p>
                <div>
                   <span class="px-4 py-1.5 text-[10px] font-bold tracking-[0.2em] uppercase rounded-full border transition-colors"
                        :class="isDark ? 'border-purple-400/30 text-purple-200 bg-purple-400/10' : 'border-purple-400/30 text-purple-400 bg-purple-400/5'">
                    Full Stack Web Developer
                  </span>
                </div>
              </div>
            </div>
            <div class="mt-10 flex flex-col gap-4">
              <a href="mailto:euniceoliveros970@gmail.com" class="w-fit px-8 py-3 rounded-xl font-bold text-sm transition-all hover:scale-105 active:scale-95 shadow-lg" 
                 :class="isDark ? 'bg-white text-black hover:shadow-purple-400/20' : 'bg-slate-900 text-white hover:shadow-purple-400/20'">
                Get in Touch
              </a>
              <div class="flex gap-6 mt-2">
                <a v-for="social in socialLinks" :key="social.icon" :href="social.url" target="_blank" class="transition-colors text-2xl"
                   :class="isDark ? 'hover:text-purple-200' : 'hover:text-purple-400'">
                  <i :class="social.icon"></i>
                </a>
              </div>
            </div>
          </header>
          <main class="lg:w-2/3 space-y-40">
            <section id="about" class="scroll-mt-32">
              <h3 class="text-xs font-bold uppercase tracking-[0.3em] mb-8" :class="isDark ? 'text-purple-200' : 'text-purple-400'">01. Overview</h3>
              <p class="text-xl md:text-2xl leading-relaxed font-medium" :class="isDark ? 'text-slate-200' : 'text-slate-700'">
                I am a <span class="font-bold" :class="isDark ? 'text-purple-200' : 'text-purple-400'">Full Stack Developer</span> dedicated to building efficient and scalable web systems. 
                With expertise in <span class="italic" :class="isDark ? 'text-cyan-500' : 'text-blue-500'">PHP, MySQL, and Vue.js</span>, I transform complex requirements into streamlined digital solutions—from AI integrations to enterprise management tools.
              </p>
            </section>
            <section id="skills" class="scroll-mt-32">
              <h3 class="text-xs font-bold uppercase tracking-[0.3em] mb-8" :class="isDark ? 'text-purple-200' : 'text-purple-400'">02. My Skills</h3>
              <div class="grid grid-cols-3 md:grid-cols-4 lg:grid-cols-4 gap-4">
                <div v-for="skill in techSkills" :key="skill.name" 
                  class="group p-4 rounded-2xl border transition-all flex flex-col items-center justify-center gap-3 cursor-default hover:scale-105 hover:shadow-xl" 
                  :class="isDark ? 'bg-slate-900/40 border-slate-800 hover:border-purple-400/50 hover:shadow-purple-400/10' : 'bg-white/60 border-white hover:border-purple-200 hover:shadow-purple-400/10'">
                  
                  <div class="w-10 h-10 flex items-center justify-center rounded-xl transition-transform group-hover:scale-110"
                       :class="isDark ? 'bg-purple-400/10 text-purple-200' : 'bg-purple-50 text-purple-400'">
                    <i :class="skill.icon + ' text-xl'"></i>
                  </div>
                  <span class="text-[10px] font-bold uppercase tracking-wider opacity-80 group-hover:opacity-100 transition-opacity">{{ skill.name }}</span>
                </div>
              </div>
            </section>
            <section id="projects" class="scroll-mt-32">
              <h3 class="text-xs font-bold uppercase tracking-[0.3em] mb-12" :class="isDark ? 'text-purple-200' : 'text-purple-400'">03. My Works & Projects</h3>
              <div class="space-y-10">
                <a v-for="project in projects" :key="project.title" :href="project.url" target="_blank"
                  class="block group p-8 md:p-12 rounded-[2.5rem] border transition-all cursor-pointer relative overflow-hidden" 
                  :class="isDark ? 'bg-slate-900/40 border-slate-800 hover:bg-slate-800/60' : 'bg-white/60 border-white hover:bg-white hover:shadow-xl hover:shadow-purple-400/10'">
                  <div class="absolute inset-0 bg-gradient-to-r transition-all duration-500"
                       :class="isDark ? 'from-purple-400/0 to-cyan-500/0 group-hover:from-purple-400/5 group-hover:to-cyan-500/5' : 'from-purple-400/0 to-blue-500/0 group-hover:from-purple-400/5 group-hover:to-blue-500/5'"></div>
                  <div class="relative z-10">
                    <div class="flex justify-between items-start mb-6">
                      <h4 class="text-3xl font-bold tracking-tighter" :class="isDark ? 'text-white' : 'text-slate-800'">{{ project.title }}</h4>
                      <div class="h-10 w-10 flex items-center justify-center rounded-full border transition-all"
                           :class="isDark ? 'border-purple-400/30 text-purple-200 group-hover:bg-purple-400 group-hover:text-white' : 'border-purple-400/30 text-purple-500 group-hover:bg-purple-500 group-hover:text-white'">
                        <i class="fa-solid fa-arrow-right -rotate-45"></i>
                      </div>
                    </div>
                    <p class="text-lg leading-relaxed mb-8 max-w-xl">{{ project.description }}</p>
                    <div class="flex flex-wrap gap-3">
                      <span v-for="tech in project.stack" :key="tech" class="px-4 py-1.5 text-[10px] font-black uppercase tracking-widest rounded-full border transition-colors" 
                            :class="isDark ? 'border-slate-700 bg-slate-800/50 text-slate-400 group-hover:border-purple-400 group-hover:text-purple-300' : 'border-slate-200 bg-white text-slate-500 group-hover:border-purple-500 group-hover:text-purple-600'">
                        {{ tech }}
                      </span>
                    </div>
                  </div>
                </a>
              </div>
            </section>
          </main>
        </div>
      </div>
    </transition>
  </div>
</template>

<script setup>
import { ref } from 'vue'
const isDark = ref(true)
const isMenuOpen = ref(false)

const techSkills = [
  { name: 'HTML5', icon: 'fa-brands fa-html5' },
  { name: 'Vite', icon: 'fa-solid fa-bolt' },
  { name: 'Oracle', icon: 'fa-solid fa-server' },
  { name: 'PHP', icon: 'fa-brands fa-php' },
  { name: 'Vue.js', icon: 'fa-brands fa-vuejs' },
  { name: 'Java', icon: 'fa-brands fa-java' },
  { name: 'C++', icon: 'fa-solid fa-microchip' },
  { name: 'MySQL', icon: 'fa-solid fa-database' },
  { name: 'Python', icon: 'fa-brands fa-python' },
  { name: 'Tailwind', icon: 'fa-solid fa-wind' },
  { name: 'C#', icon: 'fa-solid fa-gamepad' },
  { name: 'CSS', icon: 'fa-brands fa-css3-alt' },
  { name: 'Figma', icon: 'fa-brands fa-figma' }
]

const projects = [
  {
    title: 'Lumenify',
    description: 'An AI-Powered Quiz Generation System leveraging the Gemini API to transform PDF/PPTX files into interactive assessments.',
    stack: ['Vue.js', 'PHP', 'Gemini API'],
    url: 'https://lumenify.free.nf'
  },
  {
    title: 'NCST Management',
    description: 'A comprehensive Integrated Academic & Queuing Management System designed for institutional registration efficiency.',
    stack: ['PHP', 'MySQL', 'JavaScript'],
    url: 'https://ncst-e-system.wuaze.com'
  }
]

const socialLinks = [
  { icon: 'fa-brands fa-github', url: 'https://github.com/CristobalAlex' },
  { icon: 'fa-brands fa-instagram', url: 'https://www.instagram.com/nico_xandraa' },
  { icon: 'fa-solid fa-briefcase', url: 'https://ph.jobstreet.com/profiles/alexandranicole-cristobal-Q4CRjbcCTZ' },
  { icon: 'fa-solid fa-envelope', url: 'mailto:euniceoliveros970@gmail.com' }
]

const scrollToTop = () => {
  window.scrollTo({ top: 0, behavior: 'smooth' })
}
</script>

<style>
html { scroll-behavior: smooth; }
.fade-slide-enter-active { transition: opacity 1s ease, transform 1s ease; }
.fade-slide-enter-from { opacity: 0; transform: translateY(20px); }
.fade-slide-enter-to { opacity: 1; transform: translateY(0); }

@keyframes wave-slow {
  0% { transform: rotate(-15deg) skewX(-20deg) translate(0, 0); }
  50% { transform: rotate(-10deg) skewX(-10deg) translate(20px, -20px); }
  100% { transform: rotate(-15deg) skewX(-20deg) translate(0, 0); }
}

@keyframes wave-slower {
  0% { transform: rotate(15deg) skewX(20deg) translate(0, 0); }
  50% { transform: rotate(10deg) skewX(10deg) translate(-20px, 20px); }
  100% { transform: rotate(15deg) skewX(20deg) translate(0, 0); }
}

.animate-wave-slow { animation: wave-slow 15s infinite ease-in-out; }
.animate-wave-slower { animation: wave-slower 18s infinite ease-in-out; }
.animate-pulse-slow { animation: pulse 8s cubic-bezier(0.4, 0, 0.6, 1) infinite; }
</style>