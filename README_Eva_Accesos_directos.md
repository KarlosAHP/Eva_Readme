# 🛡️ Eva Blockseer — Accesos Directos

> **AVISO DE PROPIEDAD INTELECTUAL Y CONFIDENCIALIDAD**
> Este repositorio contiene arquitectura de software propietaria, sistemas de cifrado de extremo a extremo y gestión operativa de alta seguridad desarrollados bajo estricta soberanía de datos.
>
> **El acceso a este código fuente es estrictamente privado y restringido.** Queda prohibida su reproducción, distribución, ingeniería inversa o uso no autorizado bajo cualquier modalidad.

---

## 🏗️ 1. Arquitectura y Principios Operativos

EVA Accesos Directos es una extensión de navegador nativa (Manifest V3) diseñada para operar íntegramente en el lado del cliente, sin dependencias externas ni servidores centrales. Separa estrictamente la interfaz de usuario de la capa de persistencia y cifrado para garantizar soberanía, aislamiento y escalabilidad offline:

┌──────────────────────────────────────┐        ┌──────────────────────────────────────┐
│          POPUP ACTION                │        │         CONSOLA COMPLETA             │
│      (popup.html + popup.js)         │        │      (accesos_directos.html)         │
├──────────────────────────────────────┤        ├──────────────────────────────────────┤
│  Ícono extensión                     │  ↔     │  Tabs: Accesos | Notas | Ideas | Agenda│
│  Botón "Abrir Consola Completa"      │  Tab   │  Formulario Nivel 1 (Perfil base)    │
│  Permisos: storage + tabs            │        │  Formulario Nivel 2 (Acceso hijo)    │
└──────────────────────────────────────┘        │  Landing / Políticas embebida         │
                                                 │  Drawer lateral de detalle            │
                                                 └──────────────────────────────────────┘
                           │                                               │
                           ▼                                               ▼
┌──────────────────────────────────────┐        ┌──────────────────────────────────────┐
│          LÓGICA DE NEGOCIO           │        │         PERSISTENCIA & BACKUP        │
│           (dashboard.js)             │        │                                      │
├──────────────────────────────────────┤        │  Chrome Storage Local (operación)     │
│  CRUD Perfiles (Nivel 1)             │  ↔     │  Export/Import JSON cifrado           │
│  CRUD Accesos Hijos (Nivel 2)        │  Data  │  AES-GCM 256 + PBKDF2 200K           │
│  Módulos: Notas · Ideas · Agenda     │        │  Validación Policy ID + Brand         │
│  Tabs, Drawer, Reveal, Copiar        │        │                                      │
└──────────────────────────────────────┘        └──────────────────────────────────────┘

Principios Rectores de Ingeniería
🔒 Estanqueidad Absoluta: Cero bases de datos externas. Cero APIs de persistencia. Toda la información vive y opera exclusivamente en el navegador del usuario (chrome.storage.local). Ninguna entidad externa accede a credenciales o notas.
✅ Protocolo Zero-Knowledge: En operación diaria los datos se almacenan en texto plano dentro del navegador. El cifrado AES-GCM + PBKDF2 se aplica exclusivamente en el momento de generar backups portables exportables.
🛡️ Soberanía del Operador: La custodia de las llaves recae 100% en el usuario. Sin contraseña o clave interna, la recuperación de datos es criptográficamente imposible por diseño.
📦 Backup Portable sin Dependencias: Exportación/importación de bóveda completa en archivos .json cifrados. Transportables por USB, email o WhatsApp. Sin necesidad de servicios externos, cuentas en la nube ni sincronización.

---

## 📊 2. Magnitud del Proyecto

EVA Accesos Directos es una herramienta productiva real con arquitectura browser-side, cifrado aplicado y múltiples módulos funcionales integrados:

Indicador / Componente	Descripción
Tipo	Extensión de navegador (Chrome Manifest V3)
Versión manifest	2.5.0
Permisos declarados	storage, tabs
Arquitectura	Popup action → Consola completa en tab → Módulos funcionales → Chrome Storage Local
Módulos funcionales	4 (Bóveda de Accesos, Bloc de Notas, Panel de Ideas, Agenda & Recordatorios)
Perfiles de navegador base	5 (Gmail, Opera, Safari, Firefox, Explorer)
Iconos de acceso directo	23+ iconos oficiales (redes sociales, desarrollo, correo, utilidades)
Esquema de cifrado	AES-GCM 256 bits + PBKDF2 200.000 iteraciones
Ofuscación producción	javascript-obfuscator (control-flow flattening, string array encoding, transform-object-keys)

Capacidades funcionales verificables
🔑 Bóveda de Accesos multi-cuenta: perfiles de navegador/correo base (Nivel 1) con accesos hijos (Nivel 2) incluyendo URL, usuario, clave, notas, icono y categoría. Aislamiento total entre perfiles.
📝 Bloc de Notas categorizado: notas con título, contenido, categoría (General, Credenciales, Proyectos EVA, Desarrollo, Personal, Urgente), estado pinned, búsqueda en tiempo real y filtrado por categoría.
💡 Panel de Ideas (brainstorming): captura de conceptos con título, categoría (Estrategia, IA & Automatización, Seguridad & Cripto, UI/UX, Infraestructura), estado (concepto/progreso/completado), color de tarjeta y descripción.
📅 Agenda & Recordatorios: eventos con fecha, hora, categoría (Reunión, Entregable, Mantenimiento, Pago/Facturación, Personal), prioridad (alta/media/baja), checkbox de completado y filtros por período.
🔐 Export/Import seguro: backup completo en JSON cifrado con AES-GCM. Modo portable (contraseña de usuario → PBKDF2 → AES-GCM) o modo interno (clave generada en navegador, no portable entre equipos).
🛡️ Validación de autenticidad: cada contenedor cifrado incluye metadatos inmutables de marca (Eva Blockseer) y Policy ID. Si el archivo es alterado, corrompido o proviene de otra fuente, se descarta automáticamente al intentar importar.
👁️ Reveal controlado: credenciales enmascaradas en la interfaz (••••••••) con botón de revelación bajo demanda del usuario. Sin exposición accidental.

---

## 🛠️ 3. Stack Tecnológico

HTML5 Semántico
CSS3 Variables + Grid + Animaciones
JavaScript ES6+ Modular
Manifest V3 Chrome Extensions API
Extensión & Frontend: HTML5 semántico, CSS3 con variables, Grid y animaciones, JavaScript ES6+ modular sin frameworks, Chrome Extensions API con permisos mínimos (storage + tabs).

🔑 AES-GCM 256 bits
🧂 PBKDF2 200K iteraciones
🔍 WebCrypto API nativa
🛡️ Validación Policy ID + Brand
Cifrado & Seguridad: AES-GCM 256 bits con nonce único por contenedor, derivación de claves PBKDF2 con salt aleatorio de 16 bytes, WebCrypto API nativa del navegador, validación de metadatos de marca y Policy ID en cada importación.

🔒 javascript-obfuscator
📦 Control-flow flattening
🔤 String array encoding (base64)
🗝️ Transform-object-keys
Producción: ofuscación de código con javascript-obfuscator aplicando control-flow flattening (threshold 0.75), string array encoding en base64 y transformación de claves de objeto para dificultar ingeniería inversa.

---

## 📦 4. Componentes y Módulos del Frontend

Componente / Archivo	Responsabilidad
popup.html + popup.js	Popup compacto del action button: branding Eva Blockseer y botón para abrir consola completa en nueva pestaña del navegador.
accesos_directos.html	Dashboard principal: tabs de navegación (Accesos, Notas, Ideas, Agenda), formularios Nivel 1/Nivel 2, landing embebida, drawer lateral de detalle y panel de configuración/backup.
dashboard.js	Lógica completa de la extensión: CRUD de perfiles y accesos hijos, notas, ideas y agenda; backup cifrado export/import; tabs; drawer; expansión/colapso de tarjetas; reveal de credenciales; copiado al portapapeles.
landing_politicas.html	Página independiente de landing: políticas de privacidad, filosofía de código, capacidades del sistema, branding y enlaces a redes sociales.
landing_politicas.js	Script auxiliar: detección de hash en URL para scroll suave, botón de regreso al panel principal, navegación entre landing y dashboard.
accesos_inline.js	Script CSP-compliant: manejo de navegación entre panel y landing desde el HTML principal, evitando inline scripts bloqueados por Content Security Policy.

---

## 🔐 5. Protocolo de Veracidad y Seguridad

Reglas estrictas que preservan la soberanía y la veracidad del sistema:

Zero-Knowledge garantizado
Ningún dato confidencial transita por servidores de terceros. La operativa descansa exclusivamente en el navegador del usuario. Los backups cifrados son archivos .json generados y consumidos localmente; ningún servicio externo tiene acceso a su contenido.

Almacenamiento operativo local
La extensión usa chrome.storage.local en texto plano durante la operación diaria. No hay sincronización cloud, no hay bases de datos externas, no hay APIs de persistencia, no hay tokens de sesión capturados. Los accesos directos asumen que el usuario ya tiene sus sesiones abiertas en los navegadores correspondientes.

Backup portable cifrado
Exportación/importación de bóveda completa en JSON cifrado. Transportable por USB, email o WhatsApp. Sin dependencia de servicios externos.
Modo portable: el usuario elige una contraseña → PBKDF2 200.000 iteraciones con salt aleatorio → AES-GCM 256 bits.
Modo interno: clave AES generada en el navegador y almacenada en chrome.storage.local. No portable entre equipos ni navegadores.

Validación de autenticidad
Cada contenedor cifrado incluye metadatos inmutables de marca (Eva Blockseer) y Policy ID (34ebd85a43ed19d0e99d61076b3e207f909f5a36b10542b230fd09ff). Si el archivo es alterado, corrompido o proviene de otra fuente, se descarta automáticamente al intentar importar.

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
- Estanqueidad absoluta entre perfiles de navegador.

No importa la magnitud del proyecto: **Eva Blockseer, tu mundo digital en un solo ecosistema, en paralelo y continuo crecimiento.**
