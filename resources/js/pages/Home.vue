<script setup lang="ts">
import { Head, Link } from '@inertiajs/vue3';
import { computed, ref } from 'vue';
import { useAppearance } from '@/composables/useAppearance';

const navLinks = [
    { label: 'Skills', href: '#skills' },
    { label: 'Servicios', href: '#servicios' },
    { label: 'Proyectos', href: '#proyectos' },
    { label: 'Testimonios', href: '#testimonios' },
    { label: 'Contacto', href: '#contacto' },
];

const skillsPrimary = [
    { name: 'Laravel', level: 'Avanzado' },
    { name: 'Vue.js', level: 'Alto' },
    { name: 'Inertia.js', level: 'Intermedio' },
    { name: 'Git', level: 'Intermedio' },
];

const skillsOther = [
    'Docker',
    'Node',
    'WordPress',
    'Elementor',
    'Jira',
];

const skillsLearning = ['TS', 'TypeScript', 'Next.js', 'Astro', 'AI'];

const projects = [
    {
        title: 'Aurum Studio',
        tag: 'Brand + Web',
        summary: 'Landing editorial con transiciones por capas y CTA directo.',
    },
    {
        title: 'Ruta Verde',
        tag: 'E-commerce',
        summary: 'Experiencia clara, checkout optimizado y rendimiento alto.',
    },
    {
        title: 'Lumen Labs',
        tag: 'SaaS',
        summary: 'Dashboard modular con data storytelling y microinteracciones.',
    },
];

const testimonials = [
    {
        quote: 'Angel entiende el negocio y lo traduce a un sitio que vende.',
        name: 'Mariana Ruiz',
        role: 'Founder, Origen',
    },
    {
        quote: 'El proceso fue agil y con foco. El resultado se ve premium.',
        name: 'Sergio Vidal',
        role: 'CMO, Nova',
    },
];

const services = [
    {
        title: 'Desarrollo a medida',
        subtitle: 'Sistemas y sitios web pensados para crecer.',
        points: [
            'Arquitectura limpia y escalable',
            'Integraciones y automatizaciones',
            'Performance y SEO tecnico',
        ],
    },
    {
        title: 'Diseno web',
        subtitle: 'Interfaces claras con foco en conversion.',
        points: [
            'UX research + wireframes',
            'Identidad visual consistente',
            'Prototipos interactivos',
        ],
    },
    {
        title: 'Hosting y dominios',
        subtitle: 'Puesta en linea rapida y segura.',
        points: [
            'Configuracion y despliegue',
            'SSL, backups y monitoreo',
            'Soporte continuo',
        ],
    },
];

const { resolvedAppearance, updateAppearance } = useAppearance();
const isDark = computed(() => resolvedAppearance.value === 'dark');
const currentLang = ref<'ES' | 'EN'>('ES');

const toggleAppearance = () => {
    updateAppearance(isDark.value ? 'light' : 'dark');
};

const toggleLang = () => {
    currentLang.value = currentLang.value === 'ES' ? 'EN' : 'ES';
};
</script>

<template>

    <Head title="Angel | Woozie Dev">
        <link rel="preconnect" href="https://fonts.googleapis.com" />
        <link rel="preconnect" href="https://fonts.gstatic.com" />
        <link
            href="https://fonts.googleapis.com/css2?family=Instrument+Sans:wght@400;500;600;700&family=Unbounded:wght@400;500;700&display=swap"
            rel="stylesheet" />
    </Head>

    <div class="page-shell min-h-screen">
        <div class="hero-shell">
            <header class="site-header relative z-10 px-6 pt-2 sm:px-10 sm:pt-3">
                <nav class="mx-auto flex w-full max-w-6xl items-center justify-between gap-4">
                    <div class="flex items-center gap-3">
                        <img class="brand-logo" src="/images/logo-woozie.png" alt="Woozie Dev" />
                    </div>
                    <div class="hidden items-center gap-5 text-[15px] md:flex">
                        <Link v-for="link in navLinks" :key="link.href" :href="link.href"
                            class="text-white/70 transition hover:text-white">
                            {{ link.label }}
                        </Link>
                    </div>
                    <div class="flex items-center gap-3">
                        <button class="lang-switch cursor-pointer" type="button" @click="toggleLang">
                            <span class="lang-icon" aria-hidden="true">🌐</span>
                            <span class="lang-text">{{ currentLang }}</span>
                        </button>
                        <button class="theme-switch cursor-pointer" type="button" :aria-pressed="isDark"
                            aria-label="Cambiar tema" @click="toggleAppearance">
                            <span class="theme-icon is-active" aria-hidden="true">
                                <svg v-if="!isDark" viewBox="0 0 24 24" role="presentation">
                                    <path
                                        d="M12 4.5V2m0 20v-2.5m7.5-7.5H22M2 12h2.5m12.07-5.57 1.77-1.77M3.66 20.34l1.77-1.77m0-13.14L3.66 3.66m16.91 16.91-1.77-1.77M12 7.25a4.75 4.75 0 1 0 0 9.5 4.75 4.75 0 0 0 0-9.5Z"
                                        fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round"
                                        stroke-linejoin="round" />
                                </svg>
                                <svg v-else viewBox="0 0 24 24" role="presentation">
                                    <path d="M20.5 15.4A8.5 8.5 0 0 1 8.6 3.5a7 7 0 1 0 11.9 11.9Z" fill="none"
                                        stroke="currentColor" stroke-width="1.5" stroke-linecap="round"
                                        stroke-linejoin="round" />
                                </svg>
                            </span>
                        </button>
                    </div>
                </nav>
            </header>

            <section class="hero-section">
                <div
                    class="hero-content mx-auto grid w-full max-w-6xl items-center gap-10 px-6 py-14 sm:px-10 lg:grid-cols-[1.1fr_0.9fr]">
                    <div class="flex flex-col gap-6">
                        <div class="space-y-4">
                            <p class="hero-kicker">Hola, soy</p>
                            <h1 class="hero-title font-display text-4xl leading-tight sm:text-5xl lg:text-6xl">
                                <span class="hero-title__accent">Angel Rojas</span>
                            </h1>
                            <p class="hero-subtitle">
                                Desarrollador Full Stack
                            </p>
                            <p class="hero-copy text-base text-white/70 sm:text-lg">
                                Desarrollo soluciones digitales escalables con enfoque en negocio y experiencia de
                                usuario.
                            </p>
                        </div>
                        <div class="social-links">
                            <a href="https://www.linkedin.com" target="_blank" rel="noreferrer" aria-label="LinkedIn">
                                <svg viewBox="0 0 24 24" role="presentation">
                                    <path
                                        d="M4.98 3.5a2.5 2.5 0 1 1 0 5 2.5 2.5 0 0 1 0-5Zm-2 6.5h4v10h-4V10Zm7 0h3.8v1.4h.05c.53-1 1.82-2 3.75-2 4 0 4.7 2.6 4.7 6v4.6h-4v-4.1c0-1-.02-2.3-1.4-2.3-1.4 0-1.6 1.1-1.6 2.2v4.2h-4V10Z"
                                        fill="currentColor" />
                                </svg>
                            </a>
                            <a href="https://github.com" target="_blank" rel="noreferrer" aria-label="GitHub">
                                <svg viewBox="0 0 24 24" role="presentation">
                                    <path
                                        d="M12 2.5a9.5 9.5 0 0 0-3 18.5c.5.1.7-.2.7-.5v-2c-2.9.6-3.5-1.4-3.5-1.4-.5-1.2-1.2-1.5-1.2-1.5-1-.7.1-.7.1-.7 1.1.1 1.7 1.1 1.7 1.1 1 1.7 2.6 1.2 3.2.9.1-.7.4-1.2.7-1.5-2.3-.3-4.7-1.1-4.7-5a3.9 3.9 0 0 1 1-2.7c-.1-.3-.5-1.4.1-2.8 0 0 .9-.3 2.8 1a9.8 9.8 0 0 1 5.1 0c1.9-1.3 2.8-1 2.8-1 .6 1.4.2 2.5.1 2.8a3.9 3.9 0 0 1 1 2.7c0 3.9-2.4 4.7-4.7 5 .4.3.8 1 .8 2.1v3c0 .3.2.6.7.5A9.5 9.5 0 0 0 12 2.5Z"
                                        fill="currentColor" />
                                </svg>
                            </a>
                            <a href="https://www.youtube.com" target="_blank" rel="noreferrer" aria-label="YouTube">
                                <svg viewBox="0 0 24 24" role="presentation">
                                    <path
                                        d="M21.6 7.2a2.7 2.7 0 0 0-1.9-1.9C18 4.8 12 4.8 12 4.8s-6 0-7.7.5a2.7 2.7 0 0 0-1.9 1.9 28 28 0 0 0 0 9.6 2.7 2.7 0 0 0 1.9 1.9c1.7.5 7.7.5 7.7.5s6 0 7.7-.5a2.7 2.7 0 0 0 1.9-1.9 28 28 0 0 0 0-9.6ZM10.2 15.2V8.8l5.4 3.2-5.4 3.2Z"
                                        fill="currentColor" />
                                </svg>
                            </a>
                            <a href="https://www.tiktok.com" target="_blank" rel="noreferrer" aria-label="TikTok">
                                <svg viewBox="0 0 24 24" role="presentation">
                                    <path
                                        d="M15.5 4c.8 1.3 2 2.2 3.5 2.5v3c-1.5 0-2.9-.5-4.1-1.3v6.5a5.2 5.2 0 1 1-5.2-5.2c.5 0 1 .1 1.4.2v3.2a2.2 2.2 0 1 0 1.7 2.1V4h2.7Z"
                                        fill="currentColor" />
                                </svg>
                            </a>
                        </div>
                    </div>

                    <div class="relative flex items-center justify-center">
                        <div class="hero-logo">
                            <div class="hero-logo__glow" aria-hidden="true"></div>
                            <img src="/images/woozie-dev.png" alt="Woozie Dev" />
                        </div>
                    </div>
                </div>
            </section>
            <div class="hero-scroll" aria-hidden="true">
                <span>Desliza para explorar</span>
                <span class="mouse">
                    <span class="mouse-dot"></span>
                </span>
            </div>
            <div class="hero-wave" aria-hidden="true">
                <svg viewBox="0 0 1200 180" preserveAspectRatio="none" role="presentation">
                    <path d="M0,90 C200,160 420,170 640,140 C820,115 980,70 1200,110 L1200,180 L0,180 Z" />
                </svg>
            </div>
        </div>

        <main class="relative z-10 px-6 pb-24 sm:px-10">
            
            <section id="acerca" class="about-section mx-auto mt-32 w-full max-w-6xl">
                <div class="about-grid">
                    <div class="space-y-6">
                        <div class="about-title">
                            <h2 class="font-display text-3xl md:text-4xl">
                                Sobre mí
                            </h2>
                            <span class="about-line" aria-hidden="true"></span>
                        </div>
                        <div class="space-y-3 text-sm text-white/70 md:text-base">
                            <p class="about-name text-white">
                                Soy Angel — en internet me conocen como <span class="text-[#5bcb5f]"> Woozie DEV</span>
                            </p>
                            <p>
                                Empecé en tecnología a los 12 años armando computadoras.
                                Spoiler: al inicio desarmaba más de lo que arreglaba 😅.
                            </p>
                            <p>
                                Estudié diseño gráfico y multimedia (ya no me acuerdo mucho, tenía 12 años),
                                hasta que encontré mi verdadera pasión: la programación.
                            </p>
                            <p>
                                Hoy, con 12 años de experiencia, desarrollo sistemas y sitios web pensados para
                                negocio, escalabilidad y personas reales.
                            </p>
                            <p>
                                No prometo magia, prometo soluciones que funcionan.
                            </p>
                        </div>
                        <Link href="#proyectos"
                            class="about-cta inline-flex items-center gap-2 rounded-full border border-white/40 px-6 py-3 md:px-5 md:py-2 text-xs uppercase tracking-[0.2em] text-white/90 transition hover:border-white">
                            VER PROYECTOS REALES
                        </Link>
                    </div>
                    <div class="about-photos">
                        <div class="about-main">
                            <img src="/images/about-main-angel.jpg" alt="Foto principal de Angel" />
                        </div>
                        <div class="about-bubble about-bubble--top">
                            <img src="/images/about-bubble-gaming.jpg" alt="Foto secundaria de Angel" />
                        </div>
                        <div class="about-bubble about-bubble--bottom">
                            <img src="/images/angel-rojas-about-bw.jpg" alt="Foto secundaria de Angel" />
                        </div>
                    </div>
                </div>
                <div class="about-cards">
                    <div class="about-card">
                        <div class="about-card__icon">Dev</div>
                        <div>
                            <h3>Dev gaming skills</h3>
                            <p>Me adapto a tu sistema para entregar resultados reales.</p>
                        </div>
                    </div>
                    <div class="about-card">
                        <div class="about-card__icon">UX</div>
                        <div>
                            <h3>Humor dev con onda</h3>
                            <p>Me preocupo por una comunicación clara, cercana y humana.</p>
                        </div>
                    </div>
                    <div class="about-card">
                        <div class="about-card__icon">Web</div>
                        <div>
                            <h3>Experiencia real</h3>
                            <p>Trabajo en proyectos de alto impacto.</p>
                        </div>
                    </div>
                </div>
            </section>

            <section id="servicios" class="services-section mx-auto mt-32 w-full max-w-6xl">
                <div class="services-header">
                    <div class="section-heading">
                        <h2 class="font-display">Servicios</h2>
                        <span class="about-line" aria-hidden="true"></span>
                    </div>
                    <p class="text-white/70">
                        Soluciones digitales sin humo.
                    </p>
                    <p class="services-copy">
                        No vendo codigo por vender. Me adapto al problema, al
                        negocio y al cliente. Si algo no aporta, no lo hago.
                    </p>
                </div>
                <div class="services-grid">
                    <article v-for="service in services" :key="service.title" class="service-card">
                        <div class="service-card__top">
                            <div class="service-card__icon"></div>
                            <div>
                                <h3 class="font-display text-lg">
                                    {{ service.title }}
                                </h3>
                                <p class="text-sm text-white/70">
                                    {{ service.subtitle }}
                                </p>
                            </div>
                        </div>
                        <ul class="service-card__list">
                            <li v-for="point in service.points" :key="point">
                                {{ point }}
                            </li>
                        </ul>
                    </article>
                </div>
                <div class="services-footer">
                    <span class="text-white/70">
                        Necesitas algo que aporte? Yo hago eso.
                    </span>
                    <Link href="#contacto"
                        class="services-cta inline-flex items-center gap-2 rounded-full border border-[#5bcb5f] px-4 py-2 text-xs uppercase tracking-[0.2em] text-white transition hover:bg-[#5bcb5f] hover:text-[#000d48]">
                        Hablemos
                    </Link>
                </div>
            </section>

            <section id="skills" class="skills-section mx-auto mt-32 w-full max-w-6xl">
                <div class="skills-header">
                    <div class="section-heading">
                        <h2 class="font-display">Stack & Skills</h2>
                        <span class="about-line" aria-hidden="true"></span>
                    </div>
                    <p class="text-white/70">
                        Estas son mis herramientas, no adornos.
                    </p>
                    <div class="skills-badge">Siempre mejorando</div>
                </div>

                <div class="skills-panel">
                    <div class="skills-block">
                        <div class="skills-title">
                            Skills principales
                            <span class="skills-star">+</span>
                        </div>
                        <div class="skills-grid">
                            <div
                                v-for="skill in skillsPrimary"
                                :key="skill.name"
                                class="skill-card"
                            >
                                <div class="skill-card__name">
                                    {{ skill.name }}
                                </div>
                                <div class="skill-card__level">
                                    {{ skill.level }}
                                </div>
                            </div>
                        </div>
                    </div>

                    <div class="skills-block">
                        <div class="skills-title">
                            Otros skills
                            <span class="skills-star">+</span>
                        </div>
                        <div class="skills-tags">
                            <span
                                v-for="skill in skillsOther"
                                :key="skill"
                                class="skill-tag"
                            >
                                {{ skill }}
                            </span>
                        </div>
                    </div>

                    <div class="skills-block skills-block--inline">
                        <div class="skills-title">Siempre aprendiendo</div>
                        <div class="skills-pills">
                            <span
                                v-for="skill in skillsLearning"
                                :key="skill"
                                class="skill-pill"
                            >
                                {{ skill }}
                            </span>
                        </div>
                    </div>
                </div>
            </section>

            <section id="proyectos" class="mx-auto mt-20 w-full max-w-6xl">
                <div class="section-title">
                    <div class="section-heading">
                        <h2 class="font-display">Proyectos</h2>
                        <span class="about-line" aria-hidden="true"></span>
                    </div>
                    <p class="text-white/60">
                        Seleccion de trabajos con foco en impacto visual.
                    </p>
                </div>
                <div class="mt-10 grid gap-6 md:grid-cols-3">
                    <article v-for="project in projects" :key="project.title" class="project-card">
                        <div class="project-card__tag">{{ project.tag }}</div>
                        <h3 class="font-display text-xl">
                            {{ project.title }}
                        </h3>
                        <p class="mt-3 text-sm text-white/70">
                            {{ project.summary }}
                        </p>
                        <div class="project-card__cta">
                            Ver caso
                            <span aria-hidden="true">→</span>
                        </div>
                    </article>
                </div>
            </section>

            <section id="testimonios" class="mx-auto mt-20 w-full max-w-6xl">
                <div class="section-title">
                    <div class="section-heading">
                        <h2 class="font-display">Testimonios</h2>
                        <span class="about-line" aria-hidden="true"></span>
                    </div>
                    <p class="text-white/60">
                        Opiniones reales de clientes con los que colabore.
                    </p>
                </div>
                <div class="mt-10 grid gap-6 md:grid-cols-2">
                    <div v-for="testimonial in testimonials" :key="testimonial.name" class="testimonial-card">
                        <p class="text-lg text-white/80">
                            "{{ testimonial.quote }}"
                        </p>
                        <div class="mt-6 text-sm uppercase text-white/60">
                            {{ testimonial.name }} · {{ testimonial.role }}
                        </div>
                    </div>
                </div>
            </section>

            <section id="contacto" class="mx-auto mt-20 w-full max-w-6xl">
                <div class="cta-panel">
                    <div>
                        <div class="section-heading">
                            <h2 class="font-display">Hablemos de tu proximo sitio.</h2>
                            <span class="about-line" aria-hidden="true"></span>
                        </div>
                        <p class="mt-3 text-white/70">
                            Agenda una llamada o escribeme directo y creo una
                            propuesta a tu medida.
                        </p>
                    </div>
                    <Link href="mailto:hola@woozie.dev"
                        class="rounded-full bg-[#009829] px-6 py-3 text-xs font-semibold uppercase tracking-[0.25em] text-white shadow-[0_0_30px_rgba(0,152,41,0.4)] transition hover:bg-[#5bcb5f]">
                        Escribir
                    </Link>
                </div>
            </section>
        </main>

        <footer class="site-footer">
            <div class="site-footer__inner">
                <div class="site-footer__brand">
                    <img class="brand-logo" src="/images/logo-woozie.png" alt="Woozie Dev" />
                    <div>
                        <p class="font-display">Angel Rojas</p>
                        <p class="text-xs text-white/60">Desarrollador web</p>
                    </div>
                </div>
                <div class="site-footer__links">
                    <Link href="#acerca">Sobre mí</Link>
                    <Link href="#servicios">Servicios</Link>
                    <Link href="#skills">Skills</Link>
                    <Link href="#proyectos">Proyectos</Link>
                    <Link href="#contacto">Contacto</Link>
                </div>
                <div class="site-footer__meta">
                    <p class="text-sm text-white/60">Disponible para proyectos</p>
                    <a class="footer-cta" href="mailto:hola@woozie.dev">hola@woozie.dev</a>
                </div>
            </div>
            <div class="site-footer__bottom">
                <span>© 2026 Woozie Dev</span>
                <span>Hecho con Vue + Laravel</span>
            </div>
        </footer>
    </div>
</template>

<style scoped>
/* =========================================================
   1) TOKENS / VARIABLES
   ========================================================= */
.page-shell {
    --green-deep: #114c27;
    --green-core: #009829;
    --green-light: #5bcb5f;

    --navy-deep: #000d48;

    --bg-base: #070c1f;
    --bg-deep: #0a1333;

    --bg-spot-1: rgba(0, 152, 41, 0.35);
    --bg-spot-2: rgba(0, 13, 72, 0.55);
    --bg-spot-3: rgba(91, 203, 95, 0.22);

    --bg-grid: rgba(255, 255, 255, 0.05);

    --text-primary: #ffffff;
    --wave-fill: #0a1233;

    background-color: var(--bg-base);
    font-family: 'Instrument Sans', sans-serif;
    color: var(--text-primary);

    position: relative;
    overflow: hidden;
}

.font-display {
    font-family: 'Unbounded', sans-serif;
}

/* =========================================================
   2) THEME OVERRIDES (LIGHT / DARK)
   ========================================================= */
html[data-theme='light'] .page-shell {
    --bg-base: #f4f1e6;
    --bg-deep: #e2e9f3;

    --bg-spot-1: rgba(0, 152, 41, 0.18);
    --bg-spot-2: rgba(0, 13, 72, 0.14);
    --bg-spot-3: rgba(0, 152, 41, 0.12);

    --bg-grid: rgba(0, 0, 0, 0.06);

    --text-primary: #14182d;
    --wave-fill: #eaf0f8;
}

html[data-theme='dark'] .page-shell {
    --text-primary: #ffffff;
}

@media (prefers-color-scheme: light) {
    html:not([data-theme]) .page-shell {
        --bg-base: #f4f1e6;
        --bg-deep: #e2e9f3;

        --bg-spot-1: rgba(0, 152, 41, 0.18);
        --bg-spot-2: rgba(0, 13, 72, 0.14);
        --bg-spot-3: rgba(0, 152, 41, 0.12);

        --bg-grid: rgba(0, 0, 0, 0.06);

        --text-primary: #14182d;
        --wave-fill: #eaf0f8;
    }
}

/* =========================================================
   3) HEADER / NAV
   ========================================================= */
.site-header {
    background: transparent;
}

.brand-logo {
    width: 80px;
    height: auto;
    display: block;
    object-fit: contain;
}

/* Nav links en light (para que no dependan de Tailwind text-white/70) */
html[data-theme='light'] .site-header a {
    color: rgba(20, 24, 45, 0.65);
}

html[data-theme='light'] .site-header a:hover {
    color: rgba(20, 24, 45, 0.95);
}

/* =========================================================
   4) CONTROLS (LANG / THEME)
   ========================================================= */
.lang-switch {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    padding: 4px 10px;
    border-radius: 999px;

    border: 1px solid rgba(255, 255, 255, 0.2);
    background: rgba(0, 13, 72, 0.6);
    color: rgba(255, 255, 255, 0.8);

    font-size: 12px;
    letter-spacing: 0.18em;
    text-transform: uppercase;
}

.lang-icon {
    font-size: 12px;
}

.lang-text {
    font-weight: 600;
}

.theme-switch {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    padding: 4px 10px;
    border-radius: 999px;

    border: 1px solid rgba(255, 255, 255, 0.2);
    background: rgba(0, 13, 72, 0.6);

    font-size: 12px;
}

.theme-icon {
    width: 16px;
    height: 16px;
    display: inline-flex;
    align-items: center;
    justify-content: center;
    color: rgba(255, 255, 255, 0.7);
}

.theme-icon.is-active {
    color: #ffffff;
}

.theme-icon svg {
    width: 16px;
    height: 16px;
}

.theme-switch:hover .theme-icon {
    color: #ffffff;
}

/* Controls “glass” en light */
html[data-theme='light'] .lang-switch,
html[data-theme='light'] .theme-switch {
    background: rgba(255, 255, 255, 0.6);
    border-color: rgba(20, 24, 45, 0.14);
    color: rgba(20, 24, 45, 0.7);
}

/* =========================================================
   5) HERO (SHELL / CONTENT / TYPO)
   ========================================================= */
.hero-shell {
    background:
        radial-gradient(620px 420px at 18% 35%, rgba(0, 152, 41, 0.22), transparent 70%),
        radial-gradient(640px 420px at 82% 30%, rgba(0, 13, 72, 0.35), transparent 72%),
        linear-gradient(135deg, #05070f, #0b1430 55%, #0c2217);
    position: relative;
}

html[data-theme='light'] .hero-shell {
    background:
        radial-gradient(620px 420px at 18% 35%, rgba(0, 152, 41, 0.2), transparent 70%),
        radial-gradient(640px 420px at 82% 30%, rgba(0, 13, 72, 0.18), transparent 72%),
        linear-gradient(135deg, #ffffff, #eef6f1 55%, #f4f8ff);
}

.hero-section {
    position: relative;
    overflow: hidden;
}

.hero-content {
    position: relative;
}

.hero-badge {
    display: inline-flex;
    align-items: center;
    gap: 12px;
    width: fit-content;
    padding: 8px 16px;
    border-radius: 999px;

    background: rgba(255, 255, 255, 0.12);
    text-transform: uppercase;
    font-size: 12px;
    letter-spacing: 0.3em;
    color: rgba(255, 255, 255, 0.8);
}

.hero-kicker {
    text-transform: uppercase;
    letter-spacing: 0.35em;
    font-size: 12px;
    color: rgba(91, 203, 95, 0.9);
}

.hero-title__accent {
    color: #5bcb5f;
}

.hero-subtitle {
    font-size: 20px;
    font-weight: 600;
    color: rgba(255, 255, 255, 0.9);
}

.hero-copy {
    max-width: 520px;
}

/* Texto hero en light */
html[data-theme='light'] .hero-subtitle {
    color: rgba(20, 24, 45, 0.78);
}

html[data-theme='light'] .hero-copy {
    color: rgba(20, 24, 45, 0.62);
}

/* =========================================================
   6) HERO - SOCIAL
   ========================================================= */
.social-links {
    display: flex;
    flex-wrap: wrap;
    gap: 12px;
}

.social-links a {
    width: 44px;
    height: 44px;
    border-radius: 999px;

    display: inline-flex;
    align-items: center;
    justify-content: center;

    border: 1px solid rgba(255, 255, 255, 0.2);
    color: rgba(255, 255, 255, 0.85);
    background: rgba(0, 13, 72, 0.35);

    transition: transform 0.2s ease, border-color 0.2s ease, color 0.2s ease;
}

.social-links a:hover {
    transform: translateY(-2px);
    border-color: rgba(255, 255, 255, 0.4);
    color: #ffffff;
}

.social-links svg {
    width: 20px;
    height: 20px;
}

/* Social “glass” en light */
html[data-theme='light'] .social-links a {
    background: rgba(255, 255, 255, 0.55);
    border-color: rgba(20, 24, 45, 0.14);
    color: rgba(20, 24, 45, 0.72);
}

html[data-theme='light'] .social-links a:hover {
    border-color: rgba(20, 24, 45, 0.22);
    color: rgba(20, 24, 45, 0.92);
}

/* =========================================================
   7) HERO - LOGO / GLOW
   ========================================================= */
.hero-logo {
    position: relative;
    width: min(320px, 70vw);
    aspect-ratio: 1 / 1;
    display: grid;
    place-items: center;
    animation: float 6s ease-in-out infinite;
}

.hero-logo img {
    object-fit: contain;
    filter: drop-shadow(0 20px 40px rgba(0, 0, 0, 0.35));
}

.hero-logo__glow {
    position: absolute;
    inset: 0;
    border-radius: 999px;
    background:
        radial-gradient(250px circle at 50% 45%, rgba(0, 152, 41, 0.45), transparent 60%),
        radial-gradient(260px circle at 55% 60%, rgba(0, 13, 72, 0.55), transparent 68%);
    filter: blur(8px);
    opacity: 1;
    z-index: -1;
}

/* =========================================================
   8) HERO - SCROLL / WAVE
   ========================================================= */
.hero-scroll {
    position: absolute;
    left: 50%;
    transform: translateX(-50%);

    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 8px;

    color: rgba(255, 255, 255, 0.7);
    font-size: 13px;
    letter-spacing: 0.08em;
}

.hero-scroll .mouse {
    width: 22px;
    height: 34px;
    border-radius: 999px;
    border: 1px solid rgba(91, 203, 95, 0.7);

    display: inline-flex;
    align-items: flex-start;
    justify-content: center;
    padding-top: 6px;
}

.hero-scroll .mouse-dot {
    width: 4px;
    height: 6px;
    border-radius: 999px;
    background: #5bcb5f;
    animation: mouse-scroll 1.8s ease-in-out infinite;
}

/* Scroll text en light (más sutil) */
html[data-theme='light'] .hero-scroll {
    color: rgba(20, 24, 45, 0.45);
}

.hero-wave {
    width: 100%;
    line-height: 0;
}

.hero-wave svg {
    display: block;
    width: 100%;
    height: 180px;
}

.hero-wave path {
    fill: var(--bg-base);
}

/* =========================================================
   9) ABOUT
   ========================================================= */
.about-section {
    padding-top: 12px;
}

.about-grid {
    display: grid;
    gap: 32px;
    align-items: center;
}

.about-title {
    display: flex;
    align-items: center;
    gap: 16px;
}

.about-title h2,
.section-heading h2 {
    font-weight: 700;
    background: linear-gradient(90deg, #5bcb5f, #8ff09b, #5bcb5f);
    -webkit-background-clip: text;
    background-clip: text;
    color: transparent;
    text-shadow: 0 0 18px rgba(91, 203, 95, 0.35);
}

.about-line {
    height: 1px;
    flex: 1;
    background: linear-gradient(90deg,
            rgba(91, 203, 95, 0.4),
            rgba(255, 255, 255, 0.12),
            transparent);
}

.section-heading {
    display: flex;
    align-items: center;
    gap: 16px;
}

.section-heading h2 {
    font-size: 30px;
}

.about-name {
    font-size: 18px;
    font-weight: 600;
}

.about-cta {
    width: fit-content;
}

.about-photos {
    position: relative;
    display: flex;
    justify-content: center;
    padding: 18px 0;
}

.about-main {
    width: min(320px, 70vw);
    aspect-ratio: 3 / 4;
    border-radius: 28px;
    overflow: hidden;
}

.about-main img,
.about-bubble img {
    width: 100%;
    height: 100%;
    object-fit: cover;
}

.about-bubble {
    position: absolute;
    width: clamp(84px, 16vw, 120px);
    height: clamp(84px, 16vw, 120px);
    border-radius: 999px;
    overflow: hidden;
}

.about-bubble,
.about-main {
  border: 1px solid rgba(255,255,255,.16);
  box-shadow:
    0 18px 50px rgba(0,0,0,.45),
    inset 0 0 0 1px rgba(255,255,255,.06);
}

.about-bubble--top {
    top: -8px;
    right: 8%;
}

.about-bubble--bottom {
    bottom: -14px;
    left: 14%;
}

.about-cards {
    margin-top: 3rem;
    display: grid;
    gap: 18px;
    grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
}

.about-card {
    display: flex;
    gap: 14px;
    padding: 16px;
    border-radius: 18px;
    border: 1px solid rgba(255, 255, 255, 0.12);
    background: rgba(0, 13, 72, 0.45);
}

.about-card__icon {
    min-width: 48px;
    height: 48px;
    border-radius: 14px;
    display: grid;
    place-items: center;
    font-size: 12px;
    letter-spacing: 0.12em;
    text-transform: uppercase;
    color: #114c27;
    background: linear-gradient(135deg, #5bcb5f, #9af2aa);
    box-shadow: 0 12px 24px rgba(0, 0, 0, 0.2);
}

.about-card h3 {
    font-size: 15px;
    font-weight: 600;
}

.about-card p {
    margin-top: 6px;
    font-size: 13px;
    color: rgba(255, 255, 255, 0.68);
}

.services-section {
    position: relative;
}

.services-header {
    display: grid;
    gap: 16px;
}

.services-copy {
    max-width: 520px;
    color: rgba(255, 255, 255, 0.7);
    line-height: 1.6;
}

.services-grid {
    margin-top: 24px;
    display: grid;
    gap: 18px;
    grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
}

.service-card {
    border-radius: 20px;
    border: 1px solid rgba(91, 203, 95, 0.35);
    padding: 18px;
    background: rgba(9, 18, 38, 0.75);
    box-shadow: 0 20px 40px rgba(0, 0, 0, 0.35);
}

.service-card__top {
    display: flex;
    gap: 12px;
    align-items: flex-start;
}

.service-card__icon {
    width: 44px;
    height: 44px;
    border-radius: 14px;
    background: linear-gradient(135deg, rgba(91, 203, 95, 0.9), rgba(0, 152, 41, 0.6));
    box-shadow: 0 0 16px rgba(91, 203, 95, 0.5);
}

.service-card__list {
    margin-top: 16px;
    display: grid;
    gap: 10px;
    font-size: 13px;
    color: rgba(255, 255, 255, 0.7);
    padding-left: 16px;
}

.service-card__list li {
    list-style: disc;
}

.services-footer {
    margin-top: 20px;
    display: flex;
    flex-wrap: wrap;
    align-items: center;
    gap: 16px;
}

/* =========================================================
   10) SECTION TITLES + CHIPS + CARDS
   ========================================================= */
.section-title {
    display: flex;
    flex-direction: column;
    gap: 8px;
}

.skill-chip {
    border-radius: 999px;
    padding: 14px 18px;

    border: 1px solid rgba(255, 255, 255, 0.12);
    background: rgba(0, 13, 72, 0.55);

    text-transform: uppercase;
    letter-spacing: 0.16em;
    font-size: 12px;
}

.skills-section {
    position: relative;
}

.skills-header {
    display: flex;
    flex-wrap: wrap;
    align-items: center;
    justify-content: space-between;
    gap: 12px;
}

.skills-badge {
    border-radius: 999px;
    padding: 6px 14px;
    font-size: 11px;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    border: 1px solid rgba(91, 203, 95, 0.45);
    color: rgba(255, 255, 255, 0.8);
    background: rgba(0, 13, 72, 0.5);
}

.skills-panel {
    margin-top: 18px;
    border-radius: 22px;
    border: 1px solid rgba(255, 255, 255, 0.12);
    padding: 20px;
    background:
        radial-gradient(
            420px 220px at 10% 20%,
            rgba(91, 203, 95, 0.2),
            transparent 60%
        ),
        rgba(6, 12, 30, 0.75);
}

.skills-block {
    padding: 12px 0 18px;
    border-bottom: 1px solid rgba(255, 255, 255, 0.08);
}

.skills-block:last-child {
    border-bottom: none;
    padding-bottom: 0;
}

.skills-title {
    display: flex;
    align-items: center;
    gap: 10px;
    font-size: 14px;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    color: rgba(255, 255, 255, 0.8);
}

.skills-star {
    color: #5bcb5f;
}

.skills-grid {
    margin-top: 14px;
    display: grid;
    gap: 12px;
    grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
}

.skill-card {
    border-radius: 16px;
    padding: 14px;
    background: rgba(0, 13, 72, 0.6);
    border: 1px solid rgba(91, 203, 95, 0.2);
    box-shadow: inset 0 0 0 1px rgba(255, 255, 255, 0.04);
}

.skill-card__name {
    font-weight: 600;
}

.skill-card__level {
    margin-top: 8px;
    font-size: 12px;
    color: rgba(255, 255, 255, 0.6);
}

.skills-tags {
    margin-top: 14px;
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
}

.skill-tag {
    border-radius: 999px;
    padding: 8px 14px;
    border: 1px solid rgba(255, 255, 255, 0.14);
    font-size: 12px;
    text-transform: uppercase;
    letter-spacing: 0.16em;
    color: rgba(255, 255, 255, 0.75);
    background: rgba(0, 13, 72, 0.45);
}

.skills-block--inline {
    display: flex;
    flex-wrap: wrap;
    align-items: center;
    gap: 16px;
}

.skills-pills {
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
}

.skill-pill {
    border-radius: 10px;
    padding: 6px 10px;
    background: rgba(91, 203, 95, 0.2);
    border: 1px solid rgba(91, 203, 95, 0.4);
    font-size: 12px;
    letter-spacing: 0.14em;
    text-transform: uppercase;
}

.site-footer {
    margin-top: 70px;
    padding: 36px 24px 24px;
    border-top: 1px solid rgba(255, 255, 255, 0.08);
    background: rgba(4, 8, 18, 0.7);
}

.site-footer__inner {
    max-width: 1120px;
    margin: 0 auto;
    display: grid;
    gap: 24px;
    align-items: center;
    grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
}

.site-footer__brand {
    display: flex;
    align-items: center;
    gap: 16px;
}

.site-footer__links {
    display: grid;
    gap: 8px;
    font-size: 14px;
}

.site-footer__links a {
    color: rgba(255, 255, 255, 0.7);
    transition: color 0.2s ease;
}

.site-footer__links a:hover {
    color: #ffffff;
}

.site-footer__meta {
    display: grid;
    gap: 10px;
}

.footer-cta {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    padding: 8px 12px;
    border-radius: 999px;
    border: 1px solid rgba(91, 203, 95, 0.45);
    color: rgba(255, 255, 255, 0.9);
    font-size: 12px;
    letter-spacing: 0.18em;
    text-transform: uppercase;
}

.site-footer__bottom {
    max-width: 1120px;
    margin: 24px auto 0;
    padding-top: 16px;
    border-top: 1px dashed rgba(255, 255, 255, 0.12);
    display: flex;
    flex-wrap: wrap;
    gap: 12px;
    justify-content: space-between;
    font-size: 12px;
    color: rgba(255, 255, 255, 0.5);
}

.project-card {
    border-radius: 24px;
    padding: 24px;

    border: 1px solid rgba(255, 255, 255, 0.12);
    background: rgba(17, 76, 39, 0.6);

    display: flex;
    flex-direction: column;
    gap: 12px;
    min-height: 240px;
}

.project-card__tag {
    text-transform: uppercase;
    font-size: 11px;
    letter-spacing: 0.3em;
    color: rgba(255, 255, 255, 0.6);
}

.project-card__cta {
    margin-top: auto;
    text-transform: uppercase;
    font-size: 12px;
    letter-spacing: 0.2em;
    color: rgba(255, 255, 255, 0.7);

    display: inline-flex;
    align-items: center;
    gap: 8px;
}

.testimonial-card {
    border-radius: 24px;
    padding: 26px;

    border: 1px solid rgba(255, 255, 255, 0.12);
    background: rgba(0, 13, 72, 0.7);
}

.cta-panel {
    border-radius: 28px;
    border: 1px solid rgba(255, 255, 255, 0.15);

    background: linear-gradient(120deg,
            rgba(0, 152, 41, 0.35),
            rgba(0, 13, 72, 0.8));

    padding: 28px;
    display: flex;
    flex-wrap: wrap;
    align-items: center;
    justify-content: space-between;
    gap: 20px;
}

/* =========================================================
   11) EXTRA (DOT / PHOTO - si lo usas después)
   ========================================================= */
.pulse-dot {
    width: 10px;
    height: 10px;
    border-radius: 999px;
    background: #5bcb5f;
    box-shadow: 0 0 10px rgba(91, 203, 95, 0.8);
    animation: pulse 2.4s ease-in-out infinite;
}

.hero-photo {
    position: relative;
    width: min(360px, 80vw);
    aspect-ratio: 3 / 4;
    border-radius: 32px;
    overflow: hidden;

    border: 1px solid rgba(255, 255, 255, 0.2);
    background: linear-gradient(160deg,
            rgba(0, 152, 41, 0.45),
            rgba(0, 13, 72, 0.85));
    box-shadow: 0 30px 80px rgba(0, 0, 0, 0.35);
}

.hero-photo img {
    width: 100%;
    height: 100%;
    object-fit: cover;
}

.hero-photo__ring {
    position: absolute;
    inset: 18px;
    border-radius: 28px;
    border: 1px dashed rgba(255, 255, 255, 0.3);
    pointer-events: none;
}

/* =========================================================
   12) ANIMATIONS (AL FINAL)
   ========================================================= */
@keyframes float {

    0%,
    100% {
        transform: translateY(0);
    }

    50% {
        transform: translateY(-10px);
    }
}

@keyframes mouse-scroll {

    0%,
    100% {
        transform: translateY(0);
        opacity: 0.9;
    }

    50% {
        transform: translateY(6px);
        opacity: 0.4;
    }
}

@keyframes pulse {

    0%,
    100% {
        transform: scale(1);
        opacity: 1;
    }

    50% {
        transform: scale(1.25);
        opacity: 0.6;
    }
}

/* =========================================================
   13) MEDIA QUERIES (AL FINAL)
   ========================================================= */
@media (min-width: 640px) {
    .brand-logo {
        width: 108px;
    }
}

@media (min-width: 1024px) {
    .about-grid {
        grid-template-columns: 1.05fr 0.95fr;
    }
}

@media (max-width: 640px) {
    .about-bubble {
        width: 96px;
        height: 96px;
    }

    .about-bubble--top {
        top: 10px;
        left: 6%;
        right: auto;
    }

    .about-bubble--bottom {
        bottom: -10px;
        right: 8%;
        left: auto;
    }
}

@media (max-width: 639px) {
    .site-header {
        background: #050815;
        padding-bottom: 8px;
    }

    html[data-theme='light'] .site-header {
        background: #f2f0e7;
    }
}
</style>
