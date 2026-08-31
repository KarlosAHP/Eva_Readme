# ⚙️ GT Trax Power — Presencia Digital Industrial

> **Sitio web institucional y generador de leads para GT TRAX POWER — Motive Energy, empresa colombiana especializada en baterías industriales LiFePO4, cargadores y sistemas BMS para la industria, logística y movilidad pesada.**
> Desarrollado bajo un **flujo de trabajo dual estratégico**: Google AI Studio (diseño/UX) y VS Code (backend/API), con arquitectura de separación estricta de responsabilidades y datos 100% verificados.

---

## 🏗️ 1. Arquitectura y Flujo de Trabajo Dual

GT_Trax_Power opera bajo un **modelo de dos frentes estratégicamente particionado**, donde cada frente tiene un entorno, propósito y reglas estrictas. Este flujo de trabajo dual es el pilar del proceso de desarrollo:

| Frente | Gestor | Territorio | Herramientas | Regla |
|---|---|---|---|---|
| **A. Diseño Visual** | Google AI Studio | Layout, UX, componentes, animaciones, audio, generación creativa con IA | Gemini Code Assist, editor web | Nunca modifica `server.ts`, `companyData.ts` ni endpoints |
| **B. Backend/API** | Agentes de código (VS Code) | Endpoints, lógica de negocio, datos verificados, tipos | VS Code, Git, gestor de agentes Kilo | Nunca modifica diseño visual, layouts, animaciones |

```
┌──────────────────────────────────────┐        ┌──────────────────────────────────────┐
│          DISEÑO VISUAL               │        │         BACKEND / API                 │
│      (Google AI Studio)              │        │      (VS Code / Agentes)              │
├──────────────────────────────────────┤        ├──────────────────────────────────────┤
│  layout, colores, tipografía         │        │  server.ts (Express + Vite)           │
│  componentes React                   │  ↔     │  /api/company-info                   │
│  Motion (animaciones)                │  API   │  /api/generate-ad-copy (Gemini)      │
│  Audio: Web Speech + Web Audio API   │        │  /api/quote-request                   │
│  Google AI Studio + Gemini AI        │        │  /api/schedule-visit                 │
│  Validación visual por cliente       │        │  companyData.ts (verdad de datos)     │
└──────────────────────────────────────┘        └──────────────────────────────────────┘
```

### Regla de Oro del Dual-Workflow

- **Todo** cambio visual → Google AI Studio (iterativo, visual, validado por cliente).
- **Todo** cambio de backend, endpoints, datos, tipos → agentes en VS Code.
- El agente de código **nunca** edita diseño visual. El diseñador de Studio **nunca** toca backend.
- Imágenes subidas con **rutas fijas** (`baterias-lifepo4.jpg`, `jorge-foronda.jpg`), nunca nombres generados por IA.

### Reglas de Seguridad

1. **Nunca** se sube `.env` a GitHub — `GEMINI_API_KEY` vive solo como variable de entorno en Render.
2. Credenciales sensibles: cifradas antes de almacenar.
3. `.env` → `.gitignore` estricto.

---

## 📊 2. Magnitud del Proyecto

| Indicador | Valor |
|---|---|
| **Empresa** | F&R Servicios Industriales S.A.S. / GT TRAX POWER — Motive Energy |
| **Ubicación** | Medellín, Antioquia, Colombia |
| **Año de fundación** | 2017 |
| **Sitio web productivo** | https://traxpower.onrender.com |
| **Componentes de presentación** | 7 componentes React especializados |
| **Endpoints API productivos** | 4 endpoints REST reales |
| **Servicios técnicos verificados** | 6 servicios |
| **Productos verificados** | 3 familias (baterías, cargadores, BMS) |

### Capacidades funcionales verificables

* **Portal institucional responsive:** sitio web SPA con 7 secciones navegables (Hero, Servicios, Productos, ROI, Portal Interactivo, IA, Sobre Nosotros).
* **Catálogo de productos industriales:** baterías LiFePO4 TRAX POWER (24V–80V), cargadores de alta frecuencia (>93% eficiencia) y sistemas BMS con telemetría CAN-bus.
* **Calculadora de ROI:** simulador de ahorro energético y productividad multi-turno para baterías de litio vs. plomo-ácido.
* **Portal interactivo:** hotspots visuales sobre instalaciones, equipos y tecnología de la empresa.
* **Generador de copy publicitario:** asistente IA (Gemini 2.5 Flash) para generación de textos comerciales impactantes.
* **Anuncio comercial en vivo:** diapositivas interactivas con síntesis de voz en español colombiano y sonidos industriales Web Audio API.
* **Sistema de leads:** simulación de cotizaciones y programación de visitas técnicas con generación automática de enlaces de WhatsApp.
* **Datos verídicos:** toda la información corporativa proviene de `companyData.ts` + `server.ts` — cero inventos, cero mocks.

---

## 🛠️ 3. Stack Tecnológico

```html
<div style="display:flex; flex-wrap:wrap; gap:8px; margin:15px 0;">
  <div style="background:#0a1f2a; border:1px solid #38bdf8; color:#38bdf8; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">⚛️ React 19</div>
  <div style="background:#0a1f2a; border:1px solid #38bdf8; color:#38bdf8; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">🔷 TypeScript</div>
  <div style="background:#0a1f2a; border:1px solid #38bdf8; color:#38bdf8; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">⚡ Vite 6</div>
  <div style="background:#0a1f2a; border:1px solid #38bdf8; color:#38bdf8; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">🎨 Tailwind CSS 4</div>
  <div style="background:#0a1f2a; border:1px solid #38bdf8; color:#38bdf8; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">🌀 Motion</div>
  <div style="background:#0a1f2a; border:1px solid #38bdf8; color:#38bdf8; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">🪶 lucide-react</div>
</div>

**Frontend (Google AI Studio):** React 19, TypeScript, Vite 6, Tailwind CSS 4, Motion (animaciones), lucide-react (íconos). Renderizado SPA con componentes de presentación.
```

```html
<div style="display:flex; flex-wrap:wrap; gap:8px; margin:15px 0;">
  <div style="background:#2a0a0a; border:1px solid #e94560; color:#e94560; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">🐍 Node.js</div>
  <div style="background:#2a0a0a; border:1px solid #e94560; color:#e94560; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">⚡ Express 4</div>
  <div style="background:#2a0a0a; border:1px solid #e94560; color:#e94560; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">⚡ Vite Middleware</div>
  <div style="background:#2a0a0a; border:1px solid #e94560; color:#e94560; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">🤖 Gemini 2.5 Flash</div>
  <div style="background:#2a0a0a; border:1px solid #e94560; color:#e94560; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">📦 esbuild</div>
  <div style="background:#2a0a0a; border:1px solid #e94560; color:#e94560; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">🔷 TS Strict</div>
</div>

**Backend / API (VS Code):** Express 4, Vite middleware (SPA proxy en dev), Gemini 2.5 Flash (@google/genai), esbuild para bundling, TypeScript estricto.
```

```html
<div style="display:flex; flex-wrap:wrap; gap:8px; margin:15px 0;">
  <div style="background:#2a1a0a; border:1px solid #ffaa44; color:#ffaa44; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">🐳 Docker</div>
  <div style="background:#2a1a0a; border:1px solid #ffaa44; color:#ffaa44; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">☁️ Render.com</div>
  <div style="background:#2a1a0a; border:1px solid #ffaa44; color:#ffaa44; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">🔐 dotenv / Secrets</div>
  <div style="background:#2a1a0a; border:1px solid #ffaa44; color:#ffaa44; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">📊 Vite Build</div>
  <div style="background:#2a1a0a; border:1px solid #ffaa44; color:#ffaa44; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">🔁 Auto-deploy</div>
</div>

**Infraestructura:** Docker multi-stage, Render.com con auto-deploy desde `main`, secret managers para API keys, build de Vite para producción (SPA estático + Express server).
```

```html
<div style="display:flex; flex-wrap:wrap; gap:8px; margin:15px 0;">
  <div style="background:#052a05; border:1px solid #44ff44; color:#44ff44; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">🗣️ Web Speech API</div>
  <div style="background:#052a05; border:1px solid #44ff44; color:#44ff44; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">🔊 Web Audio API</div>
  <div style="background:#052a05; border:1px solid #44ff44; color:#44ff44; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">🎵 Voz es-CO</div>
  <div style="background:#052a05; border:1px solid #44ff44; color:#44ff44; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">⚡ Sonidos industriales</div>
</div>

**Audio & Accesibilidad:** Síntesis de voz en español colombiano (es-CO) para anuncios comerciales; sonidos industriales (zaps, power hum, UI clicks) via Web Audio API para inmersión táctil.
```

---

## 🔌 4. Endpoints API Productivos

| Método | Endpoint | Descripción | Lógica |
|---|---|---|---|
| `GET` | `/api/company-info` | Información corporativa verificada: empresa, contacto, redes sociales, servicios y productos | Datos estáticos desde `companyData.ts` — fuente única de verdad |
| `POST` | `/api/generate-ad-copy` | Generación de copy publicitario con Gemini 2.5 Flash | Prompt estructurado con datos de contacto reales; fallback estático si no hay API key |
| `POST` | `/api/quote-request` | Simulación de cotización de batería o servicio | Genera ID único `COT-XXXXX`, enlace de WhatsApp preformateado |
| `POST` | `/api/schedule-visit` | Programación de visita técnica o comercial | Genera ID único `VIS-XXXXX`, enlace de WhatsApp con todos los datos |

---

## 📦 5. Componentes del Frontend

| Componente | Archivo | Responsabilidad |
|---|---|---|
| **App** | `src/App.tsx` | Orquestación SPA — tabs de navegación y composición de componentes |
| **Header** | `src/components/Header.tsx` | Cabecera navegable con logo institucional |
| **LiveCommercialPoster** | `src/components/LiveCommercialPoster.tsx` | Anuncio comercial en vivo con slides, síntesis de voz y sonidos industriales |
| **RoiCalculator** | `src/components/RoiCalculator.tsx` | Calculadora de ROI para baterías LiFePO4 vs. plomo-ácido |
| **ProductsAndServices** | `src/components/ProductsAndServices.tsx` | Catálogo dinámico de productos y servicios desde datos verificados |
| **InteractivePortal** | `src/components/InteractivePortal.tsx` | Portal interactivo con hotspots visuales sobre la empresa |
| **AiCampaignGenerator** | `src/components/AiCampaignGenerator.tsx` | Generador de copy publicitario asistido por IA (Gemini) |
| **AboutUsBrochure** | `src/components/AboutUsBrochure.tsx` | Presentación institucional y datos corporativos |
| **VerifiedContactBar** | `src/components/VerifiedContactBar.tsx` | Barra de contacto con WhatsApp, correo y ubicación |

---

## 🧠 6. Destrezas y Conocimientos Aplicados

```html
<div style="display:flex; flex-wrap:wrap; gap:8px; margin:15px 0;">
  <div style="background:#0a1f2a; border:1px solid #38bdf8; color:#38bdf8; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">⚡ Ingeniería Full-Stack</div>
  <div style="background:#0a1f2a; border:1px solid #38bdf8; color:#38bdf8; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">🤖 IA Generativa</div>
  <div style="background:#2a0a0a; border:1px solid #e94560; color:#e94560; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">🏗️ Arquitectura Dual</div>
  <div style="background:#052a05; border:1px solid #44ff44; color:#44ff44; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">🗣️ Web Speech</div>
  <div style="background:#2a1a0a; border:1px solid #ffaa44; color:#ffaa44; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">🐳 Docker</div>
  <div style="background:#0a1f2a; border:1px solid #38bdf8; color:#38bdf8; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">🔐 Seguridad</div>
</div>

* **Desarrollo full-stack moderno** con React 19, TypeScript, Vite y Tailwind CSS para experiencias web industriales responsivas y performantes.
* **Diseño de arquitectura dual-workflow** con separación estricta entre interfaz visual (Google AI Studio) y lógica de negocio (VS Code/agentes), un patrón escalable reutilizable para futuros clientes.
* **Integración de IA generativa** (Gemini 2.5 Flash) para generación de copy publicitario asistido, con datos de contacto reales y fallback estático verificado.
* **Experiencia auditiva inmersiva** con Web Speech API (voz español colombiano) y Web Audio API (sonidos industriales personalizados) para anuncios comerciales en vivo.
* **API REST productiva** con Express 4 y Vite middleware, con endpoints para company-info, generación de copy, cotizaciones y programación de visitas.
* **Despliegue profesional** con Docker multi-stage y auto-deploy continuo en Render.com, con secret managers para protección de credenciales.
* **Datos verídicos** — cero inventos: toda la información corporativa, servicios y productos provienen verificados de `companyData.ts` y `server.ts`.
* **Calculadora de ROI** con lógica financiera aplicada al sector industrial — comparación de baterías LiFePO4 vs. plomo-ácido con métricas de ahorro energético y productividad multi-turno.

---

## 🔐 7. Protocolo de Veracidad y Dual-Workflow

Reglas estrictas que preservan la integridad del desarrollo:

1. **División estricta de responsabilidades**
   - Diseño/UX/estilos/animaciones → exclusivo de Google AI Studio
   - Backend/API/lógica/datos/tipos → exclusivo de agentes VS Code

2. **Nunca subir `.env`** — vive solo en `.gitignore` y en variables de entorno de Render

3. **Imágenes con rutas fijas** — `/src/assets/`, nombres descriptivos (nunca nombres aleatorios de IA)

4. **Datos verificados antes que creatividad** — toda la información proviene de `companyData.ts` o `server.ts`

5. **Síntesis de voz como complemento** — Web Speech en es-CO, nunca reemplaza contenido visual

6. **Export seguro desde AI Studio** — descomprimir zip nuevo en carpeta temporal; copiar solo archivos del frontend; preservar `server.ts`, `package.json`, `.env`

---

## 🚀 8. Integración con el Ecosistema EVA

| Módulo / Proyecto | Rol | Stack |
|---|---|---|
| **S1 Blockseer** | Inteligencia on-chain (whales) | Python, FastAPI, MongoDB Atlas, Docker |
| **S2 Eva Connect** | Datos macro/retail | Python, FastAPI, Supabase, SSE/WebSocket |
| **Green Battery** | Notaría digital industrial | Python, FastAPI, Supabase, Blockchain (pycardano) |
| **EVA Web** | Fachada corporativa | React, Vite, TypeScript |
| **GT_Trax_Power** | Presencia digital cliente | React 19, Vite 6, Tailwind, Express 4, Gemini |
| **MCP Suprema** | Orquestador / Director | FastAPI, Groq, Gemini, Supabase multi-instancia |

---

## 💼 9. Para Reclutadores y Clientes

**GT_Trax_Power** es un proyecto full-stack moderno que demuestra dominio integral de desarrollo web: desde el diseño visual iterativo en Google AI Studio hasta el backend con Express, integración con IA generativa (Gemini 2.5 Flash), experiencia de usuario inmersiva con audio (Web Speech + Web Audio API) y una arquitectura de doble frente que separa estrictamente diseño de lógica — un patrón escalable reutilizable para futuros clientes industriales.

La pila tecnológica combina **React 19 + Vite 6 + Tailwind CSS 4** en el frontend con **Express 4 + Gemini 2.5 Flash** en el backend, despliegue en **Render.com** con **Docker multi-stage** y auto-deploy continuo. Todo ello con datos 100% verificados y cero mocks.

*Presencia digital industrial — energía que impulsa tu operación.*