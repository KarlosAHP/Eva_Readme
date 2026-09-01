# 🌐 EVA Connect — Minoristas & Inteligencia Macro

> **Capa Operativa, Recolección en Tiempo Real e Inteligencia de Mercado.**
> Sistema autónomo de ingesta, normalización y publicación de datos del ecosistema Cardano y mercados financieros: clasificación de fauna minorista (Pez / Delfín / Tiburón), métricas retail 24/7, monitoreo macroeconómico, alertas on-chain y endpoints públicos normalizados sin acceso directo a base de datos.

---

## 🏗️ 1. Arquitectura y Principios Operativos

EVA Connect es el **recolector, validador y publicador de datos** del ecosistema EVA. Opera desacoplado de las capas analíticas superiores para garantizar aislamiento, resiliencia y escalabilidad en producción:

```
┌──────────────────────────────────────┐        ┌──────────────────────────────────────┐
│        FUENTES DE INGESTA            │        │         BACKEND / API HTTP           │
│   Blockfrost · APIs Mercado · News   │        │     (FastAPI + Uvicorn + EventBus)   │
├──────────────────────────────────────┤        ├──────────────────────────────────────┤
│  Cardano Mainnet (transacciones)     │        │  /api/v1/s2/bridge-data (Bridge S1)  │
│  Feeds macroeconómicos               │  →     │  /api/header_metrics                 │
│  Cables financieros & RSS            │  Queue │  /api/volume_24h                     │
│  Oráculos de precios (Binance ADA)   │        │  /api/raw_alerts & capitulation      │
└──────────────────────────────────────┘        └──────────────────────────────────────┘
                  │                                                │
                  ▼                                                ▼
┌──────────────────────────────────────┐        ┌──────────────────────────────────────┐
│        WORKERS AUTÓNOMOS             │        │       PERSISTENCIA & EVENTOS         │
├──────────────────────────────────────┤        ├──────────────────────────────────────┤
│  Scout Minorista V3.0                │        │  PostgreSQL / Supabase               │
│  Economic Monitor (Macro)            │        │  Circuit Breaker & Retención 2 Capas │
│  Intel Noticias Obrero               │        │  SSE / WebSockets (StreamContext)    │
└──────────────────────────────────────┘        └──────────────────────────────────────┘
```

### Principios Rectores de Ingeniería

* 🔒 **Aislamiento y Estanqueidad Estricta:** La base de datos de EVA Connect es privada del módulo. Ninguna sucursal externa (como Blockseer S1) o cliente consulta PostgreSQL/Supabase directamente; consumen datos exclusivamente vía **API HTTP con Bearer Tokens**.
* ✅ **Protocolo Zero-Mocks:** Cero datos simulados o placeholders. Todas las métricas de mercado y transacciones provienen de la red principal de Cardano Mainnet y oráculos oficiales verificados.
* 🛡️ **Resiliencia & Supervivencia:** Implementación de **Circuit Breaker** para resguardo de la base de datos, sistema **Fail-Safe** en modo degradado seguro frente a caídas externas, y cola asíncrona (`async_queue`) para absorber picos de carga.
* 📡 **Bus de Eventos Reactivo:** Transmisión unidireccional y bidireccional mediante **SSE (Server-Sent Events)** y **WebSockets**, permitiendo sincronización instantánea con el frontend (`StreamContext`).

---

## 📊 2. Magnitud del Proyecto

EVA Connect es un sistema productivo real con orquestación multi-worker y monitoreo continuo 24/7:

| Indicador / Componente | Descripción |
|---|---|
| **Arquitectura Backend** | FastAPI V8.0 + Uvicorn + Python 3.12+ asíncrono |
| **Worker Principal** | `scout_minorista_s2.py` V3.0 (recorrido on-chain via Blockfrost) |
| **Obreros Especializados** | Economic Monitor (macro), Intel Noticias (cables RSS), Header Oracle (precios ADA) |
| **Cron Workers** | Purga de retención en 2 capas (`db_retention_purger.py`), Censo Histórico diario, Snapshots |
| **Clasificación Retail** | Segmentación por comportamiento y volumen (Pez 🐟 / Delfín 🐬 / Tiburón 🦈) |
| **Protocolo de Integración** | Bridge seguro `/api/v1/s2/bridge-data` con cache en memoria y Bearer Token |
| **Observabilidad** | Auditoría local de conexión, health checks, colas en memoria y logs estructurados |

### Capacidades funcionales verificables

* ⛓️ **Recolección On-Chain 24/7:** Ingesta de transacciones y wallets de flujo minorista desde Cardano Mainnet vía API Blockfrost.
* 🦈 **Clasificación de Fauna Retail:** Motor de scoring cuantitativo para categorización automática de wallets (Pez 🐟 / Delfín 🐬 / Tiburón 🦈).
* 📈 **Oráculos de Mercado & Precios:** Ingesta y consolidación continua de precios ADA/USD con cache TTL y resiliencia ante caídas externas.
* 🌍 **Inteligencia Macro & Noticias:** Agregador de calendario económico semanal, eventos globales y cables financieros (World Monitor + RSS).
* 🧱 **Muro de Capitulación:** Snapshots diarios y métricas en tiempo real de pánico, liquidez y presión vendedora minorista.
* 🚨 **Detector de Anomalías:** Algoritmo en vivo para identificación de picos inusuales de volumen o concentración en tiempo real.
* 🔄 **Bus de Eventos Asíncrono:** Event Bus Pub/Sub sin bloqueo de hilos con soporte de SSE y WebSockets para dashboards reactivos.
* 🎟️ **Bridge de Consumo Cifrado:** Pasarela pública `/api/v1/s2/bridge-data` protegida por Bearer Tokens y cache en memoria para consumo seguro entre capas.
* 🧹 **Purga e Higiene de Datos:** Cron jobs de retención en dos capas (`db_retention_purger.py`) para optimizar espacio en base de datos.
* 📊 **Censo Histórico Diario:** Programación de censos diarios de wallets para seguimiento de distribución de poder retail en Cardano.

---

## 🛠️ 3. Stack Tecnológico

<div style="display:flex; flex-wrap:wrap; gap:8px; margin:15px 0;">
  <div style="background:#0f3460; border:1px solid #00eaec; color:#00eaec; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">🐍 Python 3.12+</div>
  <div style="background:#0f3460; border:1px solid #00eaec; color:#00eaec; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">⚡ FastAPI</div>
  <div style="background:#0f3460; border:1px solid #00eaec; color:#00eaec; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">🌐 Uvicorn</div>
  <div style="background:#0f3460; border:1px solid #00eaec; color:#00eaec; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">🔄 asyncio</div>
  <div style="background:#0f3460; border:1px solid #00eaec; color:#00eaec; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">📡 httpx asíncrono</div>
  <div style="background:#0f3460; border:1px solid #00eaec; color:#00eaec; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">⚙️ Workers Multi-Proceso</div>
</div>

**Backend:** Python 3.12+, FastAPI, Uvicorn (ASGI), asyncio, httpx asíncrono, colas de trabajo y subprocesos autónomos.

<div style="display:flex; flex-wrap:wrap; gap:8px; margin:15px 0;">
  <div style="background:#053b05; border:1px solid #44ff44; color:#44ff44; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">🐘 PostgreSQL</div>
  <div style="background:#053b05; border:1px solid #44ff44; color:#44ff44; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">🔌 Supabase</div>
  <div style="background:#053b05; border:1px solid #44ff44; color:#44ff44; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">📋 psycopg2-binary</div>
  <div style="background:#053b05; border:1px solid #44ff44; color:#44ff44; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">🛡️ Circuit Breaker</div>
  <div style="background:#053b05; border:1px solid #44ff44; color:#44ff44; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">🧹 Purga Inteligente</div>
</div>

**Persistencia & Datos:** PostgreSQL / Supabase, cliente `psycopg2`, estrategias de purga periódica en dos capas, resiliencia con Circuit Breaker.

<div style="display:flex; flex-wrap:wrap; gap:8px; margin:15px 0;">
  <div style="background:#002535; border:1px solid #00eaec; color:#00eaec; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">📡 SSE / Server-Sent Events</div>
  <div style="background:#002535; border:1px solid #00eaec; color:#00eaec; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">🔌 WebSockets Real-time</div>
  <div style="background:#002535; border:1px solid #00eaec; color:#00eaec; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">🔄 Bus de Eventos Pub/Sub</div>
  <div style="background:#002535; border:1px solid #00eaec; color:#00eaec; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">📦 Async Write Queue</div>
</div>

**Streaming & Eventos:** Bus de eventos propio, canales SSE y WebSockets para transmisión reactiva sin bloqueo de hilos.

<div style="display:flex; flex-wrap:wrap; gap:8px; margin:15px 0;">
  <div style="background:#4b0082; border:1px solid #b444ff; color:#b444ff; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">⚛️ React + Vite</div>
  <div style="background:#4b0082; border:1px solid #b444ff; color:#b444ff; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">🔷 TypeScript</div>
  <div style="background:#4b0082; border:1px solid #b444ff; color:#b444ff; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">🎨 Tailwind CSS</div>
  <div style="background:#4b0082; border:1px solid #b444ff; color:#b444ff; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">📡 StreamContext en vivo</div>
</div>

**Frontend:** React, Vite, TypeScript, Tailwind CSS con arquitectura de contextos reactivos en tiempo real.

<div style="display:flex; flex-wrap:wrap; gap:8px; margin:15px 0;">
  <div style="background:#4a2a0a; border:1px solid #ffaa44; color:#ffaa44; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">🐳 Docker Multi-Stage</div>
  <div style="background:#4a2a0a; border:1px solid #ffaa44; color:#ffaa44; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">☁️ Render.com</div>
  <div style="background:#4a2a0a; border:1px solid #ffaa44; color:#ffaa44; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">⏱️ Cron Jobs Programados</div>
  <div style="background:#4a2a0a; border:1px solid #ffaa44; color:#ffaa44; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">🔐 Secret Managers</div>
</div>

**Infraestructura:** Docker multi-stage, Render.com (Web Service + Workers + Cron Jobs), Secret Managers para credenciales aisladas.

<div style="display:flex; flex-wrap:wrap; gap:8px; margin:15px 0;">
  <div style="background:#3a0a0a; border:1px solid #e94560; color:#e94560; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">⛓️ Blockfrost (Cardano Mainnet)</div>
  <div style="background:#3a0a0a; border:1px solid #e94560; color:#e94560; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">📈 Oráculos de Mercado</div>
  <div style="background:#3a0a0a; border:1px solid #e94560; color:#e94560; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">📰 Feeds RSS Macro</div>
  <div style="background:#3a0a0a; border:1px solid #e94560; color:#e94560; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">🤖 IA Documental</div>
  <div style="background:#3a0a0a; border:1px solid #e94560; color:#e94560; padding:6px 14px; border-radius:20px; font-size:0.85em; font-weight:bold;">🎟️ Bearer Tokens</div>
</div>

**Integraciones & Seguridad:** API Blockfrost en tiempo real, oráculos de precio ADA, feeds de noticias financieras, autenticación por Bearer tokens y políticas de estanqueidad.

---

## 🦈 4. Clasificación de Fauna Minorista (Tiering System)

El motor de clasificación analiza patrones de volumen, concentración y frecuencia sobre wallets minoristas en Cardano:

* 🐟 **Pez (Retail Flujo Menor):** Wallets de bajo volumen transaccional diario. Representan el pulso orgánico de la red.
* 🐬 **Delfín (Mid-Tier Acumulador):** Wallets medianas con patrones recurrentes de acumulación y holding en ciclos de mercado.
* 🦈 **Tiburón (Heavy Retail / Concentrador):** Wallets de alta densidad minorista con capacidad de generar picos de volumen local.

---

## 🔌 5. Endpoints de Integración Pública

| Método | Endpoint | Descripción | Lógica & Acceso |
|---|---|---|---|
| `GET` | `/api/v1/s2/bridge-data` | Bridge de consumo seguro entre sucursales | Requiere Bearer Token. Retorna balance, métricas y estado sin exponer base de datos |
| `GET` | `/api/header_metrics` | Indicadores globales en vivo | Precios, volumen 24h, estado del circuit breaker y salud del sistema |
| `GET` | `/api/volume_24h` | Volumen transaccional normalizado | Consolidado de transacciones procesadas en la red |
| `GET` | `/api/raw_alerts` | Bus de alertas on-chain | Anomalías matemáticas y movimientos detectados en tiempo real |
| `GET` | `/api/capitulation` | Muro de capitulación | Snapshots diarios de pánico y presión vendedora |

---

## 🧠 6. Destrezas y Conocimientos Aplicados

* ⚡ **Ingeniería de backends de alta precisión** con FastAPI, Python 3.12+ y procesamiento asíncrono no bloqueante.
* 📑 **Diseño de contratos de API rigurosos** para consumo seguro entre módulos con validación de tokens y cache.
* 🔬 **Procesamiento de datos on-chain en producción:** ingesta desde Cardano Mainnet, clasificación por fauna, scoring y métricas cuantitativas.
* 🛡️ **Arquitectura de resiliencia avanzada:** Circuit Breaker, colas asíncronas offline, Fail-Safe en modo degradado y backoff exponencial.
* ⚛️ **Desarrollo frontend en tiempo real** con React, TypeScript y Tailwind CSS orientado a dashboards de monitoreo en vivo (SSE/WebSocket).
* ⚙️ **Operación de workers autónomos y cron jobs** en contenedores Docker multi-stage con auto-deploy continuo.
* 🔐 **Criptografía aplicada a la soberanía de datos:** estanqueidad por dominios, resguardo de propiedad intelectual y Zero-Knowledge de credenciales.
* 📄 **Documentación técnica profunda** orientada a auditores, reclutadores y desarrolladores integradores.

---

## 💼 7. Para Reclutadores, Clientes y Socios Estratégicos

**EVA Connect** demuestra dominio integral en la captura, normalización y publicación de grandes volúmenes de datos financieros en tiempo real. Combina ingeniería asíncrona de alto rendimiento en Python, resiliencia arquitectónica probada en producción y un frontend reactivo moderno.

<div style="display:flex; flex-wrap:wrap; gap:12px; margin:20px 0;">
  <div style="background:rgba(0,234,236,0.1); border:1px solid rgba(0,234,236,0.3); border-radius:10px; padding:12px 20px; flex:1; min-width:160px; text-align:center;">
    <div style="font-size:1.8em;">🏗️</div>
    <div style="color:#00eaec; font-weight:bold; font-size:0.9em; margin-top:5px;">Ingeniería Asíncrona</div>
  </div>
  <div style="background:rgba(68,255,68,0.1); border:1px solid rgba(68,255,68,0.3); border-radius:10px; padding:12px 20px; flex:1; min-width:160px; text-align:center;">
    <div style="font-size:1.8em;">🐘</div>
    <div style="color:#44ff44; font-weight:bold; font-size:0.9em; margin-top:5px;">PostgreSQL / Supabase</div>
  </div>
  <div style="background:rgba(0,234,236,0.1); border:1px solid rgba(0,234,236,0.3); border-radius:10px; padding:12px 20px; flex:1; min-width:160px; text-align:center;">
    <div style="font-size:1.8em;">📡</div>
    <div style="color:#00eaec; font-weight:bold; font-size:0.9em; margin-top:5px;">SSE & WebSockets</div>
  </div>
  <div style="background:rgba(233,69,96,0.1); border:1px solid rgba(233,69,96,0.3); border-radius:10px; padding:12px 20px; flex:1; min-width:160px; text-align:center;">
    <div style="font-size:1.8em;">⛓️</div>
    <div style="color:#e94560; font-weight:bold; font-size:0.9em; margin-top:5px;">Cardano Mainnet</div>
  </div>
  <div style="background:rgba(180,68,255,0.1); border:1px solid rgba(180,68,255,0.3); border-radius:10px; padding:12px 20px; flex:1; min-width:160px; text-align:center;">
    <div style="font-size:1.8em;">🛡️</div>
    <div style="color:#b444ff; font-weight:bold; font-size:0.9em; margin-top:5px;">Circuit Breakers</div>
  </div>
</div>

No importa la magnitud del proyecto: **Eva Blockseer, tu mundo digital en un solo ecosistema, en paralelo y continuo crecimiento.**

---

*Documento técnico preparado para difusión pública. Cero datos sensibles, credenciales o llaves expuestas.*
