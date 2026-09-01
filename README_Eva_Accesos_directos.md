# 🛡️ Eva Blockseer — Accesos Directos

> **AVISO DE PROPIEDAD INTELECTUAL Y CONFIDENCIALIDAD**
> Este repositorio contiene arquitectura de software propietaria, sistemas de cifrado de extremo a extremo y gestión operativa de alta seguridad desarrollados bajo estricta soberanía de datos.
>
> **El acceso a este código fuente es estrictamente privado y restringido.** Queda prohibida su reproducción, distribución, ingeniería inversa o uso no autorizado bajo cualquier modalidad.

---

## 🏗️ 1. Arquitectura y Flujo del Sistema

EVA Accesos Directos opera como una extensión de navegador nativa (Manifest V3) con una arquitectura browser-side que separa estrictamente la interfaz de usuario de la capa de persistencia y cifrado. El flujo completo se resume en:

Popup Action → Consola Completa (tab) → Módulos funcionales → Chrome Storage Local → Backup Portable Cifrado.

┌──────────────────────────────────────┐        ┌──────────────────────────────────────┐
│          POPUP ACTION                │        │         CONSOLA COMPLETA             │
│      (popup.html + popup.js)         │        │      (accesos_directos.html)         │
├──────────────────────────────────────┤        ├──────────────────────────────────────┤
│  Ícono extensión                     │  ↔     │  Tabs: Accesos | Notas | Ideas | Agenda│
│  Botón "Abrir Consola Completa"      │  Tab   │  Formulario Nivel 1 (Perfil base)    │
│  Sin privilegios adicionales          │        │  Formulario Nivel 2 (Acceso hijo)    │
└──────────────────────────────────────┘        │  Landing / Políticas embebida         │
                                                 │  Drawer lateral de detalle            │
                                                 └──────────────────────────────────────┘
Regla de Oro del Flujo
Todo acceso directo se abre en nueva pestaña del navegador principal; la extensión no captura ni almacena tokens de sesión activos.
El usuario ya debe tener sus sesiones abiertas en los navegadores correspondientes; la extensión solo centraliza enlaces y credenciales locales.
Cero servidores centrales, cero bases de datos externas, cero sincronización cloud: toda la información vive y opera exclusivamente en el navegador del usuario.

---

## 📊 2. Magnitud del Proyecto

Indicador	Valor
Nombre comercial	EVA Accesos Directos / Eva Blockseer Búnker Soberano
Tipo	Extensión de navegador (Chrome Manifest V3)
Versión manifest	2.5.0
Permisos declarados	storage, tabs
Módulos funcionales	4 (Bóveda de Accesos, Bloc de Notas, Panel de Ideas, Agenda)
Perfiles de navegador base	5 (Gmail, Opera, Safari, Firefox, Explorer)
Iconos de acceso directo	23+ iconos oficiales (redes, desarrollo, correo, utilidades)
Formatos de backup	JSON cifrado portable (.json)
Esquema de cifrado	AES-GCM 256 bits + PBKDF2 200.000 iteraciones
Almacenamiento operativo	Chrome Storage Local (texto plano en navegador)
Ofuscación producción	javascript-obfuscator (control-flow flattening, string array)

Capacidades funcionales verificables
Bóveda de Accesos multi-cuenta: perfiles de navegador/correo base (Nivel 1) con accesos hijos (Nivel 2) incluyendo URL, usuario, clave, notas, icono y categoría.
Bloc de Notas categorizado: notas con título, contenido, categoría, estado pinned, búsqueda en tiempo real y filtrado por categoría.
Panel de Ideas (brainstorming): captura de conceptos con título, categoría, estado (concepto/progreso/completado) y color de tarjeta.
Agenda & Recordatorios: eventos con fecha, hora, categoría, prioridad (alta/media/baja), checkbox de completado y filtros por período.
Export/Import seguro: backup completo en JSON cifrado con AES-GCM. Modo portable (contraseña PBKDF2) o modo interno (clave almacenada en navegador).
Validación de autenticidad: cada contenedor cifrado incluye metadatos inmutables de marca y Policy ID. Si el archivo es alterado o proviene de otra fuente, se descarta automáticamente.

---

## 🛠️ 3. Stack Tecnológico

HTML5 Semántico
CSS3 Variables + Grid + Animaciones
JavaScript ES6+ Modular
Manifest V3 Chrome Extensions API
Extensión & Frontend: HTML5 semántico, CSS3 con variables y Grid, JavaScript modular sin frameworks, Chrome Extensions API con permisos mínimos.

🔑 AES-GCM 256 bits
🧂 PBKDF2 200K iteraciones
🔍 WebCrypto API nativa
🛡️ Validación Policy ID + Brand
Cifrado & Seguridad: AES-GCM 256 bits con nonce único por contenedor, derivación de claves PBKDF2 con salt aleatorio, WebCrypto API nativa del navegador, validación de metadatos de marca y Policy ID.

🔒 javascript-obfuscator
📦 Control-flow flattening
🔤 String array encoding (base64)
🗝️ Transform-object-keys
Producción: ofuscación de código con javascript-obfuscator aplicando control-flow flattening, string array encoding en base64 y transformación de claves de objeto.

---

## 📦 4. Componentes y Módulos del Frontend

Componente / Archivo	Responsabilidad
popup.html + popup.js	Popup compacto del action button: branding y botón para abrir consola completa en nueva tab.
accesos_directos.html	Dashboard principal: tabs de navegación, formularios Nivel 1/Nivel 2, landing embebida, drawer lateral.
dashboard.js	Lógica completa: CRUD de perfiles y accesos hijos, notas, ideas, agenda; backup cifrado; tabs; drawer; expansión de tarjetas.
landing_politicas.html	Página independiente de políticas, privacidad, landing y branding. Incluye guía operativa y advertencia crítica de acceso.
landing_politicas.js	Script auxiliar: detección de hash en URL para scroll suave, botón de regreso al panel principal.
accesos_inline.js	Script CSP-compliant: manejo de navegación entre panel y landing desde el HTML principal.

---

## 🔐 5. Protocolo de Veracidad y Seguridad

Reglas estrictas que preservan la soberanía y la veracidad del sistema:

Zero-Knowledge garantizado
Ningún dato confidencial transita por servidores de terceros. Todo opera en contenedores locales cifrados (AES-GCM) o en el almacenamiento local del navegador.

Almacenamiento operativo local
La extensión usa chrome.storage.local en texto plano durante la operación diaria. No hay sincronización cloud, no hay bases de datos externas, no hay APIs de persistencia.

Backup portable cifrado
Exportación/importación de bóveda completa en JSON cifrado. Transportable por USB, email o WhatsApp. Sin dependencia de servicios externos.
Modo portable: contraseña de usuario → PBKDF2 200K iteraciones → AES-GCM 256 bits.
Modo interno: clave generada en navegador y almacenada en chrome.storage.local (no portable entre equipos).

Validación de autenticidad
Cada contenedor cifrado incluye metadados inmutables de marca (Eva Blockseer) y Policy ID (34ebd85a43ed19d0e99d61076b3e207f909f5a36b10542b230fd09ff). Si el archivo es alterado, corrompido o proviene de otra fuente, se descarta automáticamente al intentar importar.

Sin recuperación centralizada
Al no existir servidores centrales ni bases de datos de recuperación, si el usuario pierde la contraseña en modo portable o elimina la clave interna en modo interno, el acceso al respaldo se pierde de forma permanente. La seguridad y la custodia de los datos recaen 100% sobre el operador.

Ofuscación de producción
El código JavaScript de producción se ofusca con javascript-obfuscator para dificultar la ingeniería inversa. El archivo original se mantiene en control de versiones; el artefacto ofuscado se usa solo en empaquetamiento final.

---

## 🔗 6. Integración con el Ecosistema EVA

Módulo / Proyecto	Rol	Stack
S1 Blockseer	Inteligencia on-chain (whales)	Python, FastAPI, MongoDB Atlas, Docker
S2 Eva Connect	Datos macro/retail	Python, FastAPI, Supabase, SSE/WebSocket
Green Battery	Notaría digital industrial	Python, FastAPI, Supabase, Blockchain (pycardano)
EVA Web	Fachada corporativa	React, Vite, TypeScript
GT_Trax_Power	Presencia digital cliente	React 19, Vite 6, Tailwind, Express 4, Gemini
EVA Accesos Directos	Bóveda soberana de credenciales	Manifest V3, HTML/CSS/JS, AES-GCM, PBKDF2
MCP Suprema	Orquestador / Director	FastAPI, Groq, Gemini, Supabase multi-instancia

---

## 💼 7. Para Reclutadores y Clientes

EVA Accesos Directos es una extensión de navegador soberana que demuestra dominio avanzado de seguridad cliente, cifrado aplicado y arquitectura browser-side sin dependencias externas. Combina ingeniería de software de alto nivel, arquitectura distribuida y segura, integración con ecosistemas blockchain reales, y despliegue en producción con observabilidad y control de fallos.

Características destacadas para evaluadores técnicos:
- Manifest V3 real con permisos mínimos (storage + tabs).
- Cifrado Zero-Knowledge con AES-GCM 256 bits y PBKDF2 200K iteraciones.
- Arquitectura modular browser-side: 4 módulos funcionales independientes (accesos, notas, ideas, agenda).
- Backup portable cifrado con validación de Policy ID y metadatos de marca.
- Ofuscación de producción con control-flow flattening y string array encoding.
- Cero servidores centrales, cero bases de datos externas, cero sincronización cloud.

No importa la magnitud del proyecto: **Eva Blockseer, tu mundo digital en un solo ecosistema, en paralelo y continuo crecimiento.**
