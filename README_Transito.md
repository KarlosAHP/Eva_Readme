# 🚦 Transito Vueltas — Sucursal 6: Trámites de Tránsito sin Filas

> **Landing page institucional para Alex Piedrahíta en Medellín, Colombia.**
> Resuelve comparendos, fotomultas, prendas, traspasos, duplicados de licencia y trámites vehiculares de forma integral. WhatsApp-first funnel, landing page monolítica HTML/CSS, cero frameworks, cero backend.

---

## 🏗️ 1. Arquitectura y Principios Operativos

Transito Vueltas es el proyecto **más simple** de la cartera EVA. Es una **landing page institucional monolítica** — un único archivo `index.html` que contiene toda la estructura y estilos, sin backend, sin base de datos, sin frameworks JavaScript.

### Arquitectura Dual-Workflow (modelo EVA)

| Capa | Gestor | Territorio | Regla |
|---|---|---|---|
| **A. Diseño Visual** | Google AI Studio | `index.html`, estructura HTML5, CSS3, tipografía, SVG, responsive | Nunca se modifica desde fuera de Studio |
| **B. Infraestructura** | Agentes / Render | Deploy estático en Render.com, HTTPS, dominio | No toca diseño visual |

```
┌──────────────────────────────────────┐        ┌──────────────────────────────────────┐
│          DISEÑO VISUAL               │        │         INFRAESTRUCTURA              │
│      (Google AI Studio)              │        │      (Agentes / Render)              │
├──────────────────────────────────────┤        ├──────────────────────────────────────┤
│  HTML5 semántico                    │        │  Render.com (hosting estático)       │
│  CSS3: Variables, Flexbox, Grid      │  ↔     │  HTTPS auto gestionado                │
│  Web Fonts (Roboto Slab, Inter)      │        │  WhatsApp-first conversion            │
│  SVG inline                          │        │                                        │
│  Responsive media queries            │        │                                        │
└──────────────────────────────────────┘        └──────────────────────────────────────┘
```

### Principios Rectores

- **Monolito estático:** todo en un archivo `index.html`. Cero dependencias, cero frameworks. Carga instantánea.
- **WhatsApp-first:** el canal de conversión principal es WhatsApp. Cualquier CTA (botón, enlace, dock flotante) abre el enlace de WhatsApp del cliente.
- **Confianza visual:** testimonios reales con ubicación geográfica, estadísticas verificadas (900+ trámites), disclaimer legal ("no somos entidad pública").
- **Cliente independiente:** Transito Vueltas no consume APIs de EVA Blockseer, no se sincroniza con Supabase, no integra blockchain. Es un cliente externo que recibe servicios de desarrollo web.

---

## 📊 2. Magnitud del Proyecto

| Indicador | Valor |
|---|---|
| **Cliente** | Alex Piedrahíta — Trámites y Servicios |
| **Servicio** | Trámites de tránsito, fotomultas, comparendos, asesorías jurídicas |
| **Ubicación** | Medellín, Antioquia, Colombia |
| **Archivo principal** | `index.html` (662 líneas) |
| **Componentes de presentación** | 9 secciones semánticas (header, hero, pain, services, process, stats, testimonials, faq, final-cta) |
| **Servicios verificados** | 9 servicios técnicos (1 insignia + 8 trámites) |
| **Endpoints API** | 0 (sitio estático, cero backend) |
| **Base de datos** | 0 (cero Supabase, cero MongoDB) |
| **Frameworks** | 0 (HTML + CSS vanilla puro) |

### Capacidades funcionales verificables

* **Landing page institucional responsive:** 662 líneas de HTML5 semántico con CSS3 puro, 4 breakpoints responsivos.
* **WhatsApp-first funnel:** todos los CTAs enlazan directamente a WhatsApp (canal único de conversación del cliente).
* **Social dock flotante:** barra lateral con acceso a WhatsApp, Facebook, Instagram y sitio web.
* **Sistema de 4 pasos operativos:** "Nos cuenta su caso" → "Revisamos su situación" → "Hacemos la diligencia" → "Le entregamos resuelto".
* **Gestión de servicios:** 8 trámites + asesoría jurídica (tutelas, derechos de petición, apelaciones).
* **Testimonios reales:** 3 testimonios de clientes con ubicación específica (Laureles, Belén, Envigado).
* **FAQ colapsable:** 4 preguntas frecuentes con `details`/`summary` semántico.
* **Estadísticas verificables:** 900+ trámites gestionados, 100% particular, 1 contacto, 0 filas.

---

## 🛠️ 3. Stack Tecnológico

```html
<div style="display:flex; flex-wrap:wrap; gap:8px; margin:15px 0;">
  <div style="background:#0a2e7a; border:1px solid #7FD1FF; color:#7FD1FF; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">📄 HTML5 Semántico</div>
  <div style="background:#0a2e7a; border:1px solid #7FD1FF; color:#7FD1FF; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">🎨 CSS3 Puro</div>
  <div style="background:#0a2e7a; border:1px solid #7FD1FF; color:#7FD1FF; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">🔵 Flexbox + Grid</div>
  <div style="background:#0a2e7a; border:1px solid #7FD1FF; color:#7FD1FF; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">🔤 Web Fonts</div>
  <div style="background:#0a2e7a; border:1px solid #7FD1FF; color:#7FD1FF; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">🔵 SVG Inline</div>
</div>

**Frontend:** HTML5 semántico (`header`, `section`, `footer`, `details`/`summary`), CSS3 con variables personalizadas, Flexbox/Grid, animaciones `@keyframes`, media queries responsivas.
```

```html
<div style="display:flex; flex-wrap:wrap; gap:8px; margin:15px 0;">
  <div style="background:#0a2e7a; border:1px solid #25D366; color:#25D366; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">☁️ Render.com</div>
  <div style="background:#0a2e7a; border:1px solid #25D366; color:#25D366; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">🔗 HTTPS Auto</div>
  <div style="background:#0a2e7a; border:1px solid #25D366; color:#25D366; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">💬 WhatsApp-first</div>
  <div style="background:#0a2e7a; border:1px solid #25D366; color:#25D366; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">📱 Responsive</div>
</div>

**Infraestructura:** Hosting estático en Render.com con HTTPS auto-gestionado. WhatsApp como canal de conversión principal (WhatsApp-first funnel).
```

### Sin Backend / Zero Framework

| Tecnología | Estado |
|---|---|
| Express / Node.js | ❌ No aplica — sitio estático |
| Supabase / MongoDB | ❌ No aplica — cero base de datos |
| React / Vue / Angular | ❌ No aplica — HTML/CSS puro |
| Gemini / Groq / IA | ❌ No aplica — no consume APIs de IA |
| Blockchain / Cardano | ❌ No aplica — cliente independiente |
| Docker | ❌ No aplica — hosting estático en Render |

---

## 📋 4. Servicios

Servicio insignia: **Asesorías de Tránsito, Fotomultas y Comparendos** — Consulta estado real de multa, verificación de descuentos vigentes y gestión de pago.

Trámites:
1. Levantamiento de prenda (gestión ante entidad financiera y organismo de tránsito)
2. Traspaso de vehículo (preparación, radicación y seguimiento hasta inscripción)
3. Duplicados de licencia (pérdida, hurto o deterioro)
4. Paz y salvo y certificados RUNT
5. Citas y radicación de trámites (Secretaría de Movilidad)
6. Acompañamiento a revisión técnico-mecánica (CDA)
7. Matrículas y trámites vehiculares (matrícula inicial, cambio de características)

Asesoría jurídica:
8. Tutelas y derechos de petición (apelaciones e impugnaciones)

### Estadísticas verificadas

| Métrica | Valor |
|---|---|
| Trámites gestionados | 900+ en Medellín |
| Tipo de atención | 100% particular |
| Contactos | 1 solo de principio a fin |
| Filas del usuario | 0 |

---

## 🎨 5. Componentes del Frontend (Secciones HTML)

| Componente | Selector | Descripción |
|---|---|---|
| **Header / Nav** | `header > nav.nav` | Navegación sticky: logo árbol, menú y botón WhatsApp |
| **Hero** | `section.hero.grain` | Hero con eyebrow, headline, CTAs y tarjeta de documento con stamp animado |
| **Pain Points** | `section.pain` | 3 problemas del usuario: tiempo, desplazamiento, confusión |
| **Servicios** | `section.services#servicios` | 9 tarjetas de servicios (1 insignia + 8 trámites) |
| **Proceso** | `section.process#proceso` | 4 pasos operativos con timeline |
| **Stats** | `.stats` | 4 métricas: trámites, particular, contacto, filas |
| **Testimonios** | `section > .testi-grid` | 3 testimonios reales con ubicación |
| **FAQ** | `section.faq#preguntas` | 4 preguntas colapsables (`details`/`summary`) |
| **Final CTA** | `section.final-cta` | Call-to-action final con WhatsApp + contact card |
| **Footer** | `footer` | Copy institucional + disclaimer legal |
| **Social Dock** | `.dock` | Botones flotantes: WhatsApp, Facebook, Instagram, web |

---

## 🌈 6. Paleta de Colores

| Variable | Hex | Uso |
|---|---|---|
| `--blue-900` | `#0A2E7A` | Background principal / header |
| `--blue-800` | `#123A96` | Section backgrounds |
| `--blue-600` | `#1D56D6` | Acentos, borders, botones |
| `--sky` | `#7FD1FF` | Eyebrow, stats, acentos |
| `--whatsapp` | `#25D366` | CTAs primarios (WhatsApp verde) |
| `--paper` | `#F3F7FF` | Background secciones claras |
| `--ink` | `#0B2545` | Texto sobre fondo claro |
| `--muted-onblue` | `#AFC5F2` | Texto secundario sobre azul oscuro |

### Tipografía

```html
<div style="display:flex; flex-wrap:wrap; gap:8px; margin:15px 0;">
  <div style="background:rgba(11,37,69,0.3); border:1px solid #7FD1FF; color:#7FD1FF; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">🖋️ Roboto Slab (serif, títulos)</div>
  <div style="background:rgba(11,37,69,0.3); border:1px solid #7FD1FF; color:#7FD1FF; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">📄 Inter (body)</div>
  <div style="background:rgba(11,37,69,0.3); border:1px solid #7FD1FF; color:#7FD1FF; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">🔢 IBM Plex Mono (labels)</div>
</div>
```

- **Roboto Slab** (serif, 800/600) — títulos, headlines
- **Inter** (sans-serif) — texto del cuerpo, interfaz
- **IBM Plex Mono** (monospace) — numeración, folios, eyebrow, contadores

---

## 🔐 7. Notas de Veracidad

- **No somos entidad pública** ni estamos afiliados a la Secretaría de Movilidad — disclaimer legal visible en footer.
- **Zero Mocks:** todos los testimonios, estadísticas y servicios son verídicos. No hay datos inventados.
- **Cliente independiente:** no consume APIs de EVA, no se conecta a blockchains, no usa Supabase ni MongoDB. Es un proyecto aislado.
- **`.venv/` no usado:** existe una carpeta `.venv/` de Python que no aplica a este proyecto (HTML/CSS puro). No afecta el funcionamiento.
- **Sitio productivo:** https://transitovueltas.onrender.com

---

## 🚀 8. Integración con el Ecosistema EVA

| Sucursal | Rol | Stack |
|---|---|---|
| **S1 Blockseer** | Inteligencia on-chain (whales) | Python, FastAPI, MongoDB Atlas |
| **S2 Eva Connect** | Datos macro/retail | Python, FastAPI, Supabase |
| **S3 Green Battery** | Notaría digital industrial | Python, FastAPI, Supabase, Blockchain |
| **S4 EVA Web** | Fachada corporativa | React, Vite, TypeScript |
| **S5 GT_Trax_Power** | Presencia digital (baterías) | React 19, Vite, Tailwind, Express, Gemini |
| **S6 Transito Vueltas** | Trámites de tránsito | HTML5, CSS3, Render.com (landing page) |
| **MCP Suprema** | Orquestador / Director | FastAPI, Groq, Gemini, Supabase |

> **Nota:** Transito Vueltas (S6) es el proyecto más simple de la cartera. No participa en la arquitectura técnica del ecosistema EVA (no consume datos on-chain, no expone APIs). Es un cliente que recibe servicios de desarrollo web bajo el mismo modelo dual-workflow, pero con un stack monolítico frontend-puro.

---

## 💼 9. Para Reclutadores y Clientes

**Transito Vueltas** demuestra cómo un proyecto full-stack puede ser minimalista y efectivo: una landing page monolítica de HTML/CSS vanilla que convierte visitas en leads calificados sin necesidad de frameworks, backend o base de datos.

La arquitectura WhatsApp-first (todos los CTAs abren WhatsApp directamente) combinada con testimonios reales, estadísticas verificables y un diseño institucional profesional (paleta azul marino + verde WhatsApp) crea un funnel de conversión ultra-limpio.

*Trámites de tránsito sin filas — Medellín y área metropolitana.*
