# ⚡ Eva Blockseer — Ballenas: Inteligencia Forense On-Chain

> **Central Autónoma de Inteligencia de Red y Análisis Institucional.**
> Subsistema especializado en la recolección, procesamiento y correlación de métricas a gran escala sobre redes blockchain, con alertas en tiempo real vía Telegram Bot y persistencia soberana en MongoDB Atlas.

---

## 🏗️ 1. Arquitectura y Principios Operativos

Eva Blockseer (Ballenas) opera como el **Cerebro de Inteligencia On-Chain** del ecosistema, estructurado bajo un diseño modular de doble vertiente:

* 🧠 **Cerebro 1 (Analítico e Integrador):** Responsable de la correlación de flujos de datos macro, gestión de interfaces de usuario estáticas, consumo seguro de capas externas mediante pasarelas HTTP cifradas y escritura de series históricas en MongoDB Atlas.
* ⚡ **Cerebro 2 (Operativo de Alta Precisión):** Motor de cálculo matemático especializado en la detección de anomalías, brechas de valor institucional (FVG) y emisión de alertas hacia canales privados de Telegram Bot para toma de decisiones en tiempo real.
* 🛡️ **Estanqueidad Estricta:** Separación absoluta entre la capa de análisis de grandes volúmenes y los motores relacionales externos, garantizando la resiliencia operativa ante fallos de infraestructura.

Ambos componentes comparten una base de datos común en MongoDB Atlas con series históricas on-chain, pero cada uno mantiene su propio ciclo de vida, despliegue independiente y dominio funcional exclusivo.

---

## 📊 2. Magnitud del Proyecto

Eva Blockseer es un sistema de producción real con métricas verificables:

| Indicador | Valor | Descripción |
|---|---|---|
| **Archivos de código fuente** | 122+ archivos | Python, TypeScript, HTML, JavaScript |
| **Líneas de código** | 58,000+ líneas | Lógica productiva real |
| **Scripts activos** | 35+ scripts | Workers, orquestadores, agentes y servicios |
| **Despliegues en producción** | 2 servidores | Instancias cloud independientes |
| **Bases de datos** | MongoDB Atlas | Base on-chain principal + capas relacionales externas |

### Volumen de datos procesados

* 🔷 **Transacciones indexadas:** decenas de miles de registros on-chain con precios de mercado reales.
* 🔷 **Reportes predictivos:** miles de modelos de comportamiento institucional generados y persistidos en MongoDB Atlas.
* 🔷 **Jerarquías de entidades:** miles de billeteras clasificadas por poder de concentración.
* 🔷 **Alertas de Telegram:** miles de señales enviadas en tiempo real al ecosistema visual y canales operativos.
* 🔷 **Historial matemático:** miles de brechas de valor (FVG) calculadas en tiempo real.

---

## 🛠️ 3. Stack Tecnológico

<div style="display:flex; flex-wrap:wrap; gap:8px; margin:15px 0;">
  <div style="background:#0f3460; border:1px solid #44aaff; color:#44aaff; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">🐍 Python 3.12+</div>
  <div style="background:#0f3460; border:1px solid #44aaff; color:#44aaff; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">⚡ FastAPI</div>
  <div style="background:#0f3460; border:1px solid #44aaff; color:#44aaff; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">🌐 Uvicorn</div>
  <div style="background:#0f3460; border:1px solid #44aaff; color:#44aaff; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">🔄 asyncio</div>
  <div style="background:#0f3460; border:1px solid #44aaff; color:#44aaff; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">📡 httpx</div>
  <div style="background:#0f3460; border:1px solid #44aaff; color:#44aaff; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">⚙️ Workers</div>
</div>

**Backend:** Python 3.12+, FastAPI, Uvicorn, asyncio, httpx, workers y orquestación multi-cerebro.

<div style="display:flex; flex-wrap:wrap; gap:8px; margin:15px 0;">
  <div style="background:#053b05; border:1px solid #44ff44; color:#44ff44; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">🍃 MongoDB Atlas</div>
  <div style="background:#053b05; border:1px solid #44ff44; color:#44ff44; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">🐘 psycopg2</div>
  <div style="background:#053b05; border:1px solid #44ff44; color:#44ff44; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">📋 Migraciones</div>
</div>

**Datos:** MongoDB Atlas (NoSQL distribuido), psycopg2, migraciones versionadas, auditorías locales.

<div style="display:flex; flex-wrap:wrap; gap:8px; margin:15px 0;">
  <div style="background:#002535; border:1px solid #27a7e7; color:#27a7e7; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">🤖 Bot Extractor de Datos</div>
  <div style="background:#002535; border:1px solid #27a7e7; color:#27a7e7; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">🚨 Bot de Alertas</div>
  <div style="background:#002535; border:1px solid #27a7e7; color:#27a7e7; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">📬 python-telegram-bot</div>
  <div style="background:#002535; border:1px solid #27a7e7; color:#27a7e7; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">⚡ Tiempo Real</div>
</div>

**Telegram Integration:** python-telegram-bot — Bot extractor de datos en tiempo real y Bot de alertas de mercado.

<div style="display:flex; flex-wrap:wrap; gap:8px; margin:15px 0;">
  <div style="background:#4b0082; border:1px solid #b444ff; color:#b444ff; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">🖥️ HTML / JS Avanzado</div>
  <div style="background:#4b0082; border:1px solid #b444ff; color:#b444ff; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">📊 Dashboards Interactivos</div>
  <div style="background:#4b0082; border:1px solid #b444ff; color:#b444ff; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">📱 PWA</div>
  <div style="background:#4b0082; border:1px solid #b444ff; color:#b444ff; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">🔒 Seguridad Web</div>
</div>

**Frontend:** HTML/JS avanzado, dashboards interactivos, PWA, estándares de seguridad web.

<div style="display:flex; flex-wrap:wrap; gap:8px; margin:15px 0;">
  <div style="background:#4a2a0a; border:1px solid #ffaa44; color:#ffaa44; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">🐳 Docker Multi-Stage</div>
  <div style="background:#4a2a0a; border:1px solid #ffaa44; color:#ffaa44; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">☁️ Cloud Web Services</div>
  <div style="background:#4a2a0a; border:1px solid #ffaa44; color:#ffaa44; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">🔐 Secret Managers</div>
  <div style="background:#4a2a0a; border:1px solid #ffaa44; color:#ffaa44; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">♻️ CI/CD</div>
  <div style="background:#4a2a0a; border:1px solid #ffaa44; color:#ffaa44; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">✅ Health Checks</div>
</div>

**Infraestructura:** Docker multi-stage, despliegue en la nube (Web Service + Workers), secret managers, health checks.

<div style="display:flex; flex-wrap:wrap; gap:8px; margin:15px 0;">
  <div style="background:#3a0a0a; border:1px solid #e94560; color:#e94560; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">⛓️ Blockfrost</div>
  <div style="background:#3a0a0a; border:1px solid #e94560; color:#e94560; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">📈 APIs de Mercado</div>
  <div style="background:#3a0a0a; border:1px solid #e94560; color:#e94560; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">🤖 Groq / Gemini</div>
  <div style="background:#3a0a0a; border:1px solid #e94560; color:#e94560; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">🛡️ Circuit Breaker</div>
  <div style="background:#3a0a0a; border:1px solid #e94560; color:#e94560; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">🔑 AES-GCM</div>
  <div style="background:#3a0a0a; border:1px solid #e94560; color:#e94560; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">⏳ Backoff</div>
</div>

**Integraciones & Seguridad:** Blockfrost (Cardano), APIs de mercado, IA generativa (Groq/Gemini), circuit breaker, cifrado AES-GCM, backoff exponencial.

<div style="display:flex; flex-wrap:wrap; gap:8px; margin:15px 0;">
  <div style="background:#003300; border:1px solid #44ff44; color:#44ff44; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">🔷 SSE</div>
  <div style="background:#003300; border:1px solid #44ff44; color:#44ff44; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">🔌 WebSocket</div>
  <div style="background:#003300; border:1px solid #44ff44; color:#44ff44; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">⚡ WebSockets Real-time</div>
  <div style="background:#003300; border:1px solid #44ff44; color:#44ff44; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">🔄 Colas Asíncronas</div>
</div>

**Eventos & tiempo real:** bus de eventos propio, SSE, WebSocket, colas asíncronas desacopladas.

---

## ✈️ 3b. Telegram Bots — Integración en Tiempo Real

### 🤖 Bot Extractor de Datos
* 📡 Consulta APIs externas de mercado en tiempo real.
* 🍃 Escribe datos crudos directamente en MongoDB Atlas de forma asíncrona.
* ⏱️ Orquestado por workers con Cron programado.
* 🔄 Reintento automático ante fallas de fuente (backoff exponencial).
* 🔒 Credenciales gestionadas via Secret Manager (nunca hardcoded).

### 🚨 Bot de Alertas de Mercado
* 📉 Detecta FVG, anomalías estadísticas y señales institucionales en tiempo real.
* 📲 Envía alertas formateadas a canales privados de Telegram.
* ⚡ Disparo asíncrono con latencia mínima al detectar evento.
* 🎯 Permite tomar decisiones de operaciones en tiempo real.
* 🛡️ Desacoplado: un fallo de Telegram **nunca detiene** la ingesta analítica.

---

## 🧠 4. Destrezas y Conocimientos Aplicados

* ⚡ **Ingeniería de backends de alta precisión** con FastAPI, Python 3.12+, Uvicorn y procesamiento asíncrono no bloqueante.
* 🧬 **Diseño de arquitectura de doble cerebro:** desacoplamiento estricto entre dominios analíticos (Cerebro 1) y analítica matemática reactiva (Cerebro 2).
* 🔬 **Procesamiento forense on-chain:** ingesta a gran escala sobre Cardano Mainnet, modelado de acumulación/distribución y detección de FVG (Fair Value Gaps).
* 🛡️ **Sistemas de alta resiliencia:** implementación de Circuit Breaker, colas asíncronas offline, modo degradado y recuperación automática (fail-safe).
* ✈️ **Integración de Telegram Bots:** construcción de bots asíncronos para recolección de mercado y alertas operativas en tiempo real.
* 🍃 **Persistencia distribuida en MongoDB Atlas:** gestión de colecciones NoSQL optimizadas para series históricas de alta frecuencia.
* 🔐 **Criptografía y soberanía de datos:** cifrado AES-GCM, hashing criptográfico y resguardo estricto de propiedad intelectual.
* 📄 **Documentación técnica profunda:** guías orientadas a auditores, reclutadores e integradores de software.

---

## 🗄️ 5. Bases de Datos y Persistencia

* 🍃 **MongoDB Atlas (base on-chain principal):** almacenamiento NoSQL distribuido con series históricas, reportes predictivos, jerarquías de entidades y estado operativo del sistema.
* 🔗 **Capas relacionales externas:** datos relacionales para métricas macroeconómicas y retail, consumidos por el Cerebro 1 via pasarelas HTTP seguras.
* ✅ **Protocolo Zero-Mocks:** ningún dato es inventado ni simulado. Toda la información proviene de APIs oficiales y bloques de cadena pública (Blockfrost). Si una fuente falla, el sistema entra en **estado degradado seguro** sin romper la experiencia.

---

## 💼 6. Para Reclutadores, Clientes y Socios Estratégicos

**Eva Blockseer (Ballenas)** representa la cúspide en análisis e inteligencia forense de red sobre ecosistemas blockchain. Combina arquitectura distribuida, persistencia NoSQL distribuida con MongoDB Atlas y alertas reactivas por Telegram Bot.

<div style="display:flex; flex-wrap:wrap; gap:12px; margin:20px 0;">
  <div style="background:rgba(68,170,255,0.1); border:1px solid rgba(68,170,255,0.3); border-radius:10px; padding:12px 20px; flex:1; min-width:160px; text-align:center;">
    <div style="font-size:1.8em;">🏗️</div>
    <div style="color:#44aaff; font-weight:bold; font-size:0.9em; margin-top:5px;">Ingeniería Asíncrona</div>
  </div>
  <div style="background:rgba(68,255,68,0.1); border:1px solid rgba(68,255,68,0.3); border-radius:10px; padding:12px 20px; flex:1; min-width:160px; text-align:center;">
    <div style="font-size:1.8em;">🍃</div>
    <div style="color:#44ff44; font-weight:bold; font-size:0.9em; margin-top:5px;">MongoDB Atlas</div>
  </div>
  <div style="background:rgba(39,167,231,0.1); border:1px solid rgba(39,167,231,0.3); border-radius:10px; padding:12px 20px; flex:1; min-width:160px; text-align:center;">
    <div style="font-size:1.8em;">✈️</div>
    <div style="color:#27a7e7; font-weight:bold; font-size:0.9em; margin-top:5px;">Telegram Bots</div>
  </div>
  <div style="background:rgba(233,69,96,0.1); border:1px solid rgba(233,69,96,0.3); border-radius:10px; padding:12px 20px; flex:1; min-width:160px; text-align:center;">
    <div style="font-size:1.8em;">⛓️</div>
    <div style="color:#e94560; font-weight:bold; font-size:0.9em; margin-top:5px;">Cardano Mainnet</div>
  </div>
</div>

No importa la magnitud del proyecto: **Eva Blockseer, tu mundo digital en un solo ecosistema, en paralelo y continuo crecimiento.**

---

*Documento técnico preparado para difusión pública. Cero datos sensibles, credenciales o llaves expuestas.*
