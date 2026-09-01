# 🚦 Transito Vueltas — Trámites de Tránsito sin Filas

> **Landing page institucional para Alex Piedrahíta en Medellín, Colombia.**
> Resuelve comparendos, fotomultas, prendas, traspasos, duplicados de licencia y trámites vehiculares de forma integral. Funnel WhatsApp-first, landing page monolítica HTML/CSS, cero frameworks, cero backend.

---

## 🏗️ 1. Arquitectura y Principios Operativos

Transito Vueltas es el proyecto **más simple** de la cartera EVA. Es una **landing page institucional monolítica** — un único archivo `index.html` que contiene toda la estructura y estilos, sin backend, sin base de datos, sin frameworks JavaScript.

### Arquitectura Dual-Workflow (Modelo EVA)

| Capa | Gestor | Territorio | Regla |
|---|---|---|---|
| **A. Diseño Visual** | Google AI Studio | `index.html`, estructura HTML5, CSS3, tipografía, SVG, responsive | Nunca se modifica desde fuera de Studio |
| **B. Infraestructura** | Agentes / Render | Deploy estático en Render.com, HTTPS, canal de conversión WhatsApp | No toca diseño visual |

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

* 📄 **Monolito estático:** Todo en un archivo `index.html`. Cero dependencias, cero frameworks. Carga instantánea.
* 💬 **WhatsApp-first:** El canal de conversión principal es WhatsApp. Cualquier CTA (botón, enlace, dock flotante) abre el enlace de WhatsApp del cliente.
* 🛡️ **Confianza visual:** Testimonios reales con ubicación geográfica, estadísticas verificadas (900+ trámites), disclaimer legal ("no somos entidad pública").
* 🔗 **Cliente independiente:** Transito Vueltas no consume APIs de EVA Blockseer, no se sincroniza con Supabase, no integra blockchain. Es un cliente externo que recibe servicios de desarrollo web.

---

## 📊 2. Magnitud del Proyecto

| Indicador | Valor |
|---|---|
| **Cliente** | Alex Piedrahíta — Trámites y Servicios |
| **Servicio** | Trámites de tránsito, fotomultas, comparendos, asesorías jurídicas |
| **Ubicación** | Medellín, Antioquia, Colombia |
| **Sitio web productivo** | https://transitovueltas.onrender.com |
| **Archivo principal** | `index.html` (662 líneas) |
| **Componentes de presentación** | 9 secciones semánticas (header, hero, pain, services, process, stats, testimonials, faq, final-cta) |
| **Servicios verificados** | 9 servicios técnicos (1 insignia + 8 trámites) |
| **Endpoints API** | 0 (sitio estático, cero backend) |
| **Base de datos** | 0 (cero Supabase, cero MongoDB) |
| **Frameworks** | 0 (HTML + CSS vanilla puro) |

### Capacidades funcionales verificables

* 📱 **Landing page institucional responsive:** 662 líneas de HTML5 semántico con CSS3 puro, 4 breakpoints responsivos.
* 💬 **Funnel WhatsApp-first:** Todos los CTAs enlazan directamente a WhatsApp (canal único de conversación del cliente).
* ⚓ **Social dock flotante:** Barra lateral con acceso a WhatsApp, Facebook, Instagram y sitio web.
* 🔄 **Sistema de 4 pasos operativos:** "Nos cuenta su caso" → "Revisamos su situación" → "Hacemos la diligencia" → "Le entregamos resuelto".
* 📑 **Gestión de servicios:** 8 trámites + asesoría jurídica (tutelas, derechos de petición, apelaciones).
* 🌟 **Testimonios reales:** 3 testimonios de clientes con ubicación específica (Laureles, Belén, Envigado).
* ❓ **FAQ colapsable:** 4 preguntas frecuentes con `details`/`summary` semántico.
* 📊 **Estadísticas verificables:** 900+ trámites gestionados, 100% particular, 1 contacto, 0 filas.

---

## 🛠️ 3. Stack Tecnológico

<div style="display:flex; flex-wrap:wrap; gap:8px; margin:15px 0;">
  <div style="background:#0a2e7a; border:1px solid #7FD1FF; color:#7FD1FF; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">📄 HTML5 Semántico</div>
  <div style="background:#0a2e7a; border:1px solid #7FD1FF; color:#7FD1FF; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">🎨 CSS3 Puro</div>
  <div style="background:#0a2e7a; border:1px solid #7FD1FF; color:#7FD1FF; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">🔵 Flexbox + Grid</div>
  <div style="background:#0a2e7a; border:1px solid #7FD1FF; color:#7FD1FF; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">🔤 Web Fonts</div>
  <div style="background:#0a2e7a; border:1px solid #7FD1FF; color:#7FD1FF; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">🔵 SVG Inline</div>
</div>

**Frontend:** HTML5 semántico (`header`, `section`, `footer`, `details`/`summary`), CSS3 con variables personalizadas, Flexbox/Grid, animaciones `@keyframes`, media queries responsivas.

<div style="display:flex; flex-wrap:wrap; gap:8px; margin:15px 0;">
  <div style="background:#0a2e7a; border:1px solid #25D366; color:#25D366; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">☁️ Render.com</div>
  <div style="background:#0a2e7a; border:1px solid #25D366; color:#25D366; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">🔗 HTTPS Auto</div>
  <div style="background:#0a2e7a; border:1px solid #25D366; color:#25D366; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">💬 WhatsApp-first</div>
  <div style="background:#0a2e7a; border:1px solid #25D366; color:#25D366; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">📱 Responsive</div>
</div>

**Infraestructura:** Hosting estático en Render.com con HTTPS auto-gestionado. WhatsApp como canal de conversión principal (WhatsApp-first funnel).

### Sin Backend / Zero Framework

| Tecnología | Estado | Razón |
|---|---|---|
| **Express / Node.js** | ❌ No aplica | Sitio estático puro |
| **Supabase / MongoDB** | ❌ No aplica | Cero base de datos necesaria |
| **React / Vue / Angular** | ❌ No aplica | HTML + CSS vanilla puro |
| **Gemini / Groq / IA** | ❌ No aplica | No requiere APIs de IA generativa |
| **Blockchain / Cardano** | ❌ No aplica | Cliente independiente |
| **Docker** | ❌ No aplica | Hosting estático directo en Render |

---

## 📋 4. Servicios Verificados

Servicio insignia: **Asesorías de Tránsito, Fotomultas y Comparendos** — Consulta estado real de multa, verificación de descuentos vigentes y gestión de pago.

Trámites:
1. 📜 **Levantamiento de prenda:** gestión ante entidad financiera y organismo de tránsito.
2. 🚗 **Traspaso de vehículo:** preparación, radicación y seguimiento hasta inscripción.
3. 📄 **Duplicados de licencia:** por pérdida, hurto o deterioro.
4. 📋 **Paz y salvo y certificados RUNT:** certificados de tradición y paz y salvo.
5. 📲 **Citas y radicación de trámites:** programación y radicación en Secretaría de Movilidad.
6. 🔧 **Acompañamiento a revisión técnico-mecánica:** indicaciones y agendamiento CDA.
7. 🏷️ **Matrículas y trámites vehiculares:** matrícula inicial, cambio de características.

Asesoría jurídica:
8. ⚖️ **Tutelas y derechos de petición:** apelaciones, impugnaciones y defensas legales.

### Estadísticas verificadas

| Métrica | Valor | Descripción |
|---|---|---|
| **Trámites gestionados** | 900+ | En Medellín y área metropolitana |
| **Tipo de atención** | 100% particular | Sin intermediarios costosos |
| **Contactos** | 1 solo | Atención directa de principio a fin |
| **Filas del usuario** | 0 | Gestión 100% remota |

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
| **Testimonios** | `section > .testi-grid` | 3 testimonios reales con ubicación (Laureles, Belén, Envigado) |
| **FAQ** | `section.faq#preguntas` | 4 preguntas colapsables (`details`/`summary`) |
| **Final CTA** | `section.final-cta` | Call-to-action final con WhatsApp + contact card |
| **Footer** | `footer` | Copy institucional + disclaimer legal |
| **Social Dock** | `.dock` | Botones flotantes: WhatsApp, Facebook, Instagram, web |

---

## 🌈 6. Paleta de Colores y Tipografía

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

<div style="display:flex; flex-wrap:wrap; gap:8px; margin:15px 0;">
  <div style="background:rgba(11,37,69,0.3); border:1px solid #7FD1FF; color:#7FD1FF; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">🖋️ Roboto Slab (serif, títulos)</div>
  <div style="background:rgba(11,37,69,0.3); border:1px solid #7FD1FF; color:#7FD1FF; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">📄 Inter (body)</div>
  <div style="background:rgba(11,37,69,0.3); border:1px solid #7FD1FF; color:#7FD1FF; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">🔢 IBM Plex Mono (labels)</div>
</div>

- **Roboto Slab** (serif, 800/600) — títulos, headlines institucionales
- **Inter** (sans-serif) — texto del cuerpo, interfaz de usuario
- **IBM Plex Mono** (monospace) — numeración, folios, eyebrow, contadores

---

## 🧠 7. Destrezas y Conocimientos Aplicados

<div style="display:flex; flex-wrap:wrap; gap:8px; margin:15px 0;">
  <div style="background:#0a2e7a; border:1px solid #7FD1FF; color:#7FD1FF; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">📄 HTML5 / CSS3 Vanilla</div>
  <div style="background:#0a2e7a; border:1px solid #7FD1FF; color:#7FD1FF; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">💬 WhatsApp Funnel</div>
  <div style="background:#0a2e7a; border:1px solid #7FD1FF; color:#7FD1FF; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">🎨 Diseño Monolítico</div>
  <div style="background:#0a2e7a; border:1px solid #25D366; color:#25D366; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">☁️ Render Static</div>
</div>

* 📄 **Desarrollo web monolítico de alta velocidad:** maquetación semántica pura en HTML5 y CSS3 vanilla sin dependencias externas ni frameworks.
* 💬 **Arquitectura de conversión WhatsApp-first:** diseño de embudos directos a WhatsApp para maximizar tasa de respuesta e interacción inmediata.
* 🎨 **Diseño e identidad institucional:** paleta cromática profesional (`#0A2E7A` azul marino + `#25D366` verde WhatsApp) con jerarquía tipográfica triple (Roboto Slab, Inter, IBM Plex Mono).
* 📱 **Adaptabilidad responsive completa:** 4 breakpoints CSS estratégicos para experiencia fluida en smartphones, tablets y escritorio.
* ☁️ **Despliegue y optimización en Render.com:** hosting de archivos estáticos con HTTPS automático, tiempos de carga mínimos y disponibilidad 24/7.
* 🛡️ **Gobernanza y veracidad de datos (Zero Mocks):** información de testimonios, trámites y servicios 100% verídicos para Alex Piedrahíta en Medellín.

---

## 🔐 8. Protocolo de Veracidad y Transparencia

- **Disclaimer Legal:** No somos entidad pública ni estamos afiliados a la Secretaría de Movilidad — disclaimer legal visible en footer.
- **Zero Mocks:** Todos los testimonios, estadísticas y servicios son verídicos. No hay datos inventados.
- **Cliente Independiente:** No consume APIs de EVA, no se conecta a blockchains, no usa Supabase ni MongoDB. Es un proyecto aislado.
- **`.venv/` no usado:** Existe una carpeta `.venv/` de Python que no aplica a este proyecto (HTML/CSS puro). No afecta el funcionamiento.
- **Sitio Productivo:** https://transitovueltas.onrender.com

---

## 💼 9. Para Reclutadores y Clientes

**Transito Vueltas** demuestra cómo un proyecto de desarrollo web puede ser ultra-efectivo y minimalista: una landing page monolítica de HTML/CSS vanilla que convierte visitas en leads calificados directamente en WhatsApp, sin necesidad de frameworks, backend o base de datos.

<div style="display:flex; flex-wrap:wrap; gap:12px; margin:20px 0;">
  <div style="background:rgba(127,209,255,0.1); border:1px solid rgba(127,209,255,0.3); border-radius:10px; padding:12px 20px; flex:1; min-width:160px; text-align:center;">
    <div style="font-size:1.8em;">📄</div>
    <div style="color:#7FD1FF; font-weight:bold; font-size:0.9em; margin-top:5px;">HTML5 / CSS3 Vanilla</div>
  </div>
  <div style="background:rgba(37,211,102,0.1); border:1px solid rgba(37,211,102,0.3); border-radius:10px; padding:12px 20px; flex:1; min-width:160px; text-align:center;">
    <div style="font-size:1.8em;">💬</div>
    <div style="color:#25D366; font-weight:bold; font-size:0.9em; margin-top:5px;">WhatsApp-First</div>
  </div>
  <div style="background:rgba(127,209,255,0.1); border:1px solid rgba(127,209,255,0.3); border-radius:10px; padding:12px 20px; flex:1; min-width:160px; text-align:center;">
    <div style="font-size:1.8em;">☁️</div>
    <div style="color:#7FD1FF; font-weight:bold; font-size:0.9em; margin-top:5px;">Render Static</div>
  </div>
  <div style="background:rgba(255,170,68,0.1); border:1px solid rgba(255,170,68,0.3); border-radius:10px; padding:12px 20px; flex:1; min-width:160px; text-align:center;">
    <div style="font-size:1.8em;">⚡</div>
    <div style="color:#ffaa44; font-weight:bold; font-size:0.9em; margin-top:5px;">Carga Instantánea</div>
  </div>
</div>

No importa la magnitud del proyecto: **Eva Blockseer, tu mundo digital en un solo ecosistema, en paralelo y continuo crecimiento.**

*Trámites de tránsito sin filas — Medellín y área metropolitana.*
