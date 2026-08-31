# ⚡ Eva Blockseer — Ballenas: Inteligencia Forense On-Chain

> **Central Autónoma de Inteligencia de Red y Análisis Institucional.**
> Subsistema especializado en la recolección, procesamiento y correlación de métricas a gran escala sobre redes blockchain, con alertas en tiempo real vía Telegram Bot y persistencia soberana en MongoDB Atlas.

---

## 🏗️ 1. Arquitectura y Principios Operativos

La Sucursal 1 opera como el **Cerebro de Inteligencia On-Chain** del ecosistema, estructurado bajo un diseño modular de doble vertiente:

* **Cerebro 1 (Analítico e Integrador):** Responsable de la correlación de flujos de datos macro, gestión de interfaces de usuario estáticas, consumo seguro de capas externas mediante pasarelas HTTP cifradas y escritura de series históricas en MongoDB Atlas.
* **Cerebro 2 (Operativo de Alta Precisión):** Motor de cálculo matemático especializado en la detección de anomalías, brechas de valor institucional (FVG) y emisión de alertas hacia canales privados de Telegram Bot para toma de decisiones en tiempo real.
* **Estanqueidad Estricta:** Separación absoluta entre la capa de análisis de grandes volúmenes y los motores relacionales externos, garantizando la resiliencia operativa ante fallos de infraestructura.

Ambos componentes comparten una base de datos común en MongoDB Atlas con series históricas on-chain, pero cada uno mantiene su propio ciclo de vida, despliegue independiente y dominio funcional exclusivo.

---

## 📊 2. Magnitud del Proyecto

Eva Blockseer es un sistema de producción real con métricas verificables:

| Indicador | Valor |
|-----------|-------|
| **Archivos de código fuente** | 122+ archivos (Python, TypeScript, HTML, JavaScript) |
| **Líneas de código** | 58,000+ líneas de lógica productiva |
| **Scripts activos** | 35+ workers, orquestadores, agentes y servicios |
| **Despliegues en producción** | 2 servidores independientes en la nube |
| **Bases de datos** | MongoDB Atlas (on-chain principal) + capas relacionales externas |

### Volumen de datos procesados

* **Transacciones indexadas:** decenas de miles de registros on-chain con precios de mercado reales.
* **Reportes predictivos:** miles de modelos de comportamiento institucional generados y persistidos en MongoDB Atlas.
* **Jerarquías de entidades:** miles de billeteras clasificadas por poder de concentración.
* **Alertas de Telegram:** miles de señales enviadas en tiempo real al ecosistema visual y canales operativos.
* **Historial matemático:** miles de brechas de valor (FVG) calculadas en tiempo real.

---

## 🛠️ 3. Stack Tecnológico

* **Backend:** Python 3.12+, FastAPI, Uvicorn, asyncio, httpx, workers y orquestación multi-cerebro.
* **Datos:** MongoDB Atlas (NoSQL distribuido), psycopg2, migraciones versionadas, auditorías locales.
* **Telegram Integration:** python-telegram-bot — Bot extractor de datos en tiempo real y Bot de alertas de mercado.
* **Eventos y tiempo real:** bus de eventos propio, SSE, WebSocket, colas asíncronas desacopladas.
* **Frontend:** HTML/JS avanzado, dashboards interactivos, PWA, estándares de seguridad web.
* **Infraestructura:** Docker multi-stage, despliegue en la nube (Web Service + Workers), secret managers, health checks.
* **Integraciones:** Blockfrost (Cardano), APIs de mercado, IA generativa (Groq/Gemini).
* **Seguridad:** cifrado AES-GCM, estanqueidad por módulos, circuit breaker, fail-safe, backoff exponencial.
* **Gobernanza:** Git, GitHub, despliegue continuo.

---

## ✈️ 3b. Telegram Bots — Integración en Tiempo Real

### 🤖 Bot Extractor de Datos
* Consulta APIs externas de mercado en tiempo real.
* Escribe datos crudos directamente en MongoDB Atlas de forma asíncrona.
* Orquestado por workers con Cron programado.
* Reintento automático ante fallas de fuente (backoff exponencial).
* Credenciales gestionadas via Secret Manager.

### 🚨 Bot de Alertas de Mercado
* Detecta FVG, anomalías estadísticas y señales institucionales en tiempo real.
* Envía alertas formateadas a canales privados de Telegram.
* Disparo asíncrono con latencia mínima.
* Permite tomar decisiones de operaciones en tiempo real.
* Desacoplado: un fallo de Telegram no detiene el análisis.

---

## 🧠 4. Destrezas y Conocimientos Aplicados

* Ingeniería de backends de alta precisión con FastAPI y procesamiento asíncrono.
* Diseño de arquitectura de doble cerebro con separación estricta de dominios.
* Procesamiento de datos on-chain a gran escala y detección matemática de anomalías institucionales.
* Implementación de sistemas resilientes, tolerantes a fallos y con recuperación automática.
* Construcción de Telegram Bots para extracción de datos y alertas de mercado en tiempo real.
* Gestión de MongoDB Atlas para persistencia de series históricas on-chain.
* Desarrollo de interfaces seguras, PWA y despliegue modular en producción.
* Criptografía aplicada, hashing y protección de propiedad intelectual.

---

## 🗄️ 5. Bases de Datos y Persistencia

* **MongoDB Atlas (base on-chain principal):** almacenamiento NoSQL distribuido con series históricas, reportes predictivos, jerarquías de entidades y estado operativo del sistema.
* **Capas relacionales externas:** datos relacionales para métricas macroeconómicas y retail, consumidos por el Cerebro 1 via pasarelas HTTP seguras.
* **Estrategia de datos:** ningún dato es inventado ni simulado. Toda la información proviene de APIs oficiales y bloques de cadena pública (Blockfrost). Si una fuente falla, el sistema entra en estado degradado seguro.

---

## 💼 6. Para reclutadores, clientes y socios estratégicos

**Eva Blockseer** es un stack tecnológico de vanguardia para datos soberanos, inteligencia on-chain y automatización financiera. Combinamos ingeniería de alto nivel, arquitectura distribuida y segura, integración con Cardano, bots de Telegram para operativas en tiempo real, persistencia soberana en MongoDB Atlas y despliegue en producción con observabilidad y control de fallos.

No importa la magnitud del proyecto: **Eva Blockseer, tu mundo digital en un solo ecosistema, en paralelo y continuo crecimiento.**
