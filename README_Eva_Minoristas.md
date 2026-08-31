# EVA Connect — Sucursal 2

## ¿Qué es EVA Connect?

EVA Connect es la capa operativa y de inteligencia de mercado del ecosistema EVA. Su función es capturar, normalizar y exponer datos reales del ecosistema Cardano y mercados financieros, con foco en flujo minorista, métricas macroeconómicas y señales on-chain listas para consumo por otras capas analíticas y productos cliente.

No es un analytics engine: es el **recolector, validador y publicador** de datos del sistema.

---

## Arquitectura de alto nivel

El sistema se organiza en capas independientes para preservar estanqueidad, resiliencia y escalabilidad:

```text
[ Fuentes on-chain / APIs externas ]
                ↓
     [ Workers de recolección ]
                ↓
     [ Cola asíncrona + Circuit Breaker ]
                ↓
     [ Backend API — FastAPI ]
                ↓
     [ Frontend dashboard + endpoints públicos ]
```

- **Frontend**: Dashboard React para monitoreo operativo en tiempo real.
- **Backend API**: API REST y streams en vivo. Publica métricas normalizadas y protege el acceso mediante tokens y contratos de consumo claros.
- **Workers**: Procesos autónomos que recorren on-chain, agregan noticias, ingestan feeds macro y actualizan precios.
- **Persistence**: Base de datos operativa propia con estrategias de retención, purga y circuit breaker para alta disponibilidad.

> Regla de arquitectura: las capas externas consumen datos **exclusivamente por API pública**. No hay acceso directo a la base de datos desde fuera del módulo.

---

## Capacidades operativas

- **Detección y clasificación de wallets minoristas** en Cardano, con segmentación por perfil de flujo.
- **Métricas de mercado 24/7**: volúmenes, balances, presión compradora/vendedora y rankings por poder de wallet.
- **Alertas on-chain**: detección de movimientos relevantes y anomalías en tiempo real.
- **Inteligencia macro y noticias**: agregación de eventos económicos, calendario macro y cables de mercado.
- **Precio y profundidad**: tracking de activos y estados de mercado con fuentes múltiples y cache resiliente.
- **Muro de capitulación**: snapshots diarios y métricas de pánico del mercado.
- **Streams en vivo**: actualización continua hacia dashboards mediante SSE y WebSocket.

---

## Stack tecnológico

### Backend
- **Lenguaje**: Python 3.11+
- **Framework**: FastAPI + Uvicorn
- **Base de datos**: PostgreSQL / Supabase
- **Cliente HTTP**: httpx (asíncrono)
- **Colas y eventos**: asyncio + bus de eventos propio
- **Integraciones**: Blockfrost (Cardano), APIs de mercado, feeds de noticias, IA generativa para análisis de documentos

### Frontend
- **Framework**: React + Vite + TypeScript
- **Estilos**: Tailwind CSS
- **Tiempo real**: StreamContext con SSE / WebSocket
- **Despliegue**: Build estático servido por el backend

### Infraestructura
- **Contenedores**: Docker multi-stage
- **Orquestación**: Render.com
- **Workers**: Servicios worker independientes para scouts, monitores macro, orquestadores de noticias y oráculos de precio
- **Cron jobs**: Tareas programadas para censo histórico, purga de retención y snapshots periódicos

---

## Filosofía de diseño y seguridad

- **Zero mocks**: todas las métricas se calculan desde datos reales; no se usan simulaciones en producción.
- **Estanqueidad**: cada módulo cumple una única responsabilidad. No hay dependencias cruzadas ocultas entre capas analíticas y operativas.
- **Resiliencia by design**: circuit breaker, fail-safe, cache local, cola offline y backoff controlado para mantener servicio aunque fallen servicios externos.
- **Soberanía de datos**: la base operativa es privada del módulo; la única vía de integración oficial es la API pública con token compartido.
- **Secret management**: las credenciales y claves se manejan exclusivamente por variables de entorno y gestores de secretos en plataforma; nunca se versionan en repositorio.

---

## Despliegue y operación

- **Modelo**: despliegue continuo con contenedores optimizados.
- **Servicios**: API web + workers especializados por dominio (scout minorista, macro, noticias, precio).
- **Escalado**: cada worker puede escalarse de forma independiente según carga.
- **Monitoreo**: health checks, métricas de cola, estado de circuit breaker y auditorías locales de conexión.

---

## Integración en el ecosistema EVA

EVA Connect se integra con otras sucursales del ecosistema bajo contrato de API:

- **Entrada**: fuentes on-chain, APIs de mercado, noticias y documentos AI.
- **Salida**: endpoints normalizados para consumo por capas analíticas, dashboards y productos cliente.
- **Aislamiento**: otras sucursales no consultan directamente la base de S2; consumen endpoints públicos con validación de token.

---

## 🛠️ Herramientas, stack y conocimientos aplicados

Este módulo está construido con herramientas de producción real, seleccionadas para máxima resiliencia, rendimiento y soberanía de datos:

* **Backend:** Python 3.12+, FastAPI, Uvicorn, `asyncio`, `httpx`.
* **Datos:** PostgreSQL, Supabase, `psycopg2`, migraciones versionadas.
* **Eventos y tiempo real:** bus de eventos propio, SSE, WebSocket, colas asíncronas desacopladas.
* **Frontend:** React + Vite + TypeScript, Tailwind CSS, Context API en tiempo real.
* **Infraestructura:** Docker multi-stage, Render.com (Web Service + Workers + Cron Jobs), secret managers, health checks.
* **Integraciones:** Blockfrost (Cardano Mainnet), APIs de mercado, feeds de noticias, motores de IA generativa.
* **Seguridad:** tokens Bearer, circuit breaker, fail-safe, backoff exponencial, cache TTL, estanqueidad por módulos.
* **Gobernanza:** Git, GitHub, despliegue continuo, auditorías locales de conexión.

### 🧠 Destrezas y conocimientos que hacen posible este módulo

* Desarrollo de backends asíncronos de alto rendimiento con FastAPI y Python.
* Diseño de contratos de API claros, seguros y normalizados para consumo entre módulos.
* Procesamiento de datos on-chain en producción: ingesta, clasificación, score y métricas.
* Implementación de arquitecturas resilientes: circuit breaker, colas offline, degraded mode y recuperación automática.
* Desarrollo frontend moderno orientado a dashboards operativos con actualización en vivo.
* Operación de workers autónomos, cron jobs y orquestadores multi-proceso.
* Criptografía aplicada al servicio de la soberanía de datos y la integridad operativa.
* Documentación técnica orientada a integradores, clientes y equipos de desarrollo.

---

## 💼 Para reclutadores, clientes y socios estratégicos

**Eva Blockseer** es un stack tecnológico de vanguardia, diseñado a la medida de necesidades complejas en el ámbito de datos soberanos, inteligencia on-chain y automatización financiera. Combinamos ingeniería de software de alto nivel, arquitectura distribuida y segura, integración con ecosistemas blockchain reales, y despliegue en producción con observabilidad y control de fallos.

No importa la magnitud del proyecto: **Eva Blockseer, tu mundo digital en un solo ecosistema, en paralelo y continuo crecimiento.**

---

*Documento preparado para difusión pública. No contiene rutas internas detalladas, credenciales ni detalles de implementación sensibles.*

