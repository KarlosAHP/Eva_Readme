# 🔋 Eva Green Battery — Sucursal 3: Notaría Digital Industrial

> **Gestión Industrial de Flotas, Portal de Clientes y Agenda Inteligente tipo CRM.**
> Sistema productivo de trazabilidad forense para activos industriales (baterías, UPS, rectificadores) con portal transaccional para clientes finales y agenda corporativa para despacho de técnicos.

---

## 🏗️ 1. Arquitectura y Principios Operativos

La Sucursal 3 es el **Cerebro Industrial** del ecosistema Eva. Está construida sobre tres módulos sincronizados que conviven en una misma plataforma pero con responsabilidades y superficies de seguridad claramente separadas:

* **Núcleo Forense Industrial:** Notarización blockchain del ciclo de vida de cada activo (nacimiento, mantenimientos preventivos/correctivos, visitas de diagnóstico, pruebas de autonomía, retiros). Auditoría humana del administrador sobre cada informe antes de publicación al cliente.
* **Portal de Clientes:** Aplicación transaccional para que el cliente final gestione su cuenta, consulte sus sedes y activos, descargue reportes autorizados por Green Battery y solicite visitas técnicas desde un panel propio.
* **Agenda Inteligente tipo CRM:** Calendario corporativo centralizado con despacho de técnicos, semáforos de visita, festivos laborales, notas internas, bitácora profesional con timer, jerarquía de proyectos y registro de evidencias/habilidades por actividad.

### Principios Rectores

* **Estanqueidad absoluta:** La lógica industrial de Green Battery nunca se mezcla con la lógica de trading de otras sucursales del ecosistema.
* **Trazabilidad inmutable por diseño:** Cada evento técnico pasa por un protocolo de revisión humana antes de ser visible para el cliente.
* **Segregación de dominios en la agenda:** Los registros de tipo *Agenda* solo pueden ser modificados por el administrador; los registros de tipo *Nota* solo por su propietario o el administrador.
* **Doble perímetro de datos:** Las tablas internas (forenses) operan con privilegios de servicio; las tablas del portal del cliente operan además con políticas de seguridad a nivel de fila.

---

## 📊 2. Magnitud del Proyecto

Eva Green Battery es un sistema de producción real, desplegado y con operación cotidiana verificable:

| Indicador | Valor |
|-----------|-------|
| **Routers de negocio** | 11 routers FastAPI especializados (equipos, sedes, sub_sedes, autonomía, finanzas, notas y agenda, portal de clientes, propuestas, historial operativo, libro contable, notificaciones) |
| **Endpoints productivos** | Más de 100 endpoints REST documentados con Pydantic V2 |
| **Tablas operativas** | 25+ tablas activas en el núcleo industrial + 4 tablas del portal del cliente |
| **Bases de datos** | 2 instancias PostgreSQL administradas (Supabase) con propósitos diferenciados |
| **Lenguaje de reportes** | Generación de reportes técnicos con firma institucional y código QR |
| **Notarización** | Anclaje de eventos críticos en blockchain pública (red de pruebas y red principal) |

### Capacidades funcionales verificables

* **Equipos registrados:** gestión integral de activos industriales con atributos técnicos completos (voltaje, amperaje, celdas, tecnología, conectores, ADN de celdas, matriz de baterías).
* **Historial clínico forense:** bitácora auditable de cada intervención técnica con fotografías, mediciones y observaciones del técnico y del auditor.
* **Pruebas de autonomía:** captura de curvas de descarga para certificación de rendimiento del activo.
* **Notarización criptográfica:** cada hito relevante queda anclado en blockchain con explorador público para verificación de terceros.
* **Catálogo de precios y facturación maestra:** motor de cálculo de márgenes de utilidad y consolidación financiera por cliente.
* **Portal transaccional del cliente:** registro con validación de NIT/Cédula contra las sedes registradas, login con sesión temporal, solicitud de visitas con tipo y fecha preferida, y descarga de reportes autorizados.
* **Agenda corporativa centralizada:** vista única del administrador con todas las agendas, ocupación por técnico, asignación idempotente de tareas y auto-reparación de sincronizaciones.
* **Semáforo de visita:** protocolo de control de tiempos en campo (asignado → llegada → salida) con timestamp automático del servidor.
* **CRM profesional ligero:** bitácora con timer activo, proyectos jerárquicos, evidencias por actividad y catálogo de habilidades técnicas por nota.
* **Email transaccional:** confirmación automática de visitas agendadas al cliente final.

---

## 🛠️ 3. Stack Tecnológico

* **Backend:** Python 3.11+, FastAPI, Uvicorn, Pydantic V2, passlib con bcrypt, asyncio para tareas en segundo plano.
* **Frontend Web:** React 18 + TypeScript + Vite + Tailwind CSS, con patrón de componentes especializados por dominio (activos, sedes, técnicos, autonomía, reportes, chat).
* **Dashboard legacy:** Streamlit para herramientas administrativas internas y panel de auditoría del administrador.
* **Bases de datos:** 2 instancias Supabase (PostgreSQL administrado) con sincronización bidireccional controlada entre ellas.
* **Generación de PDFs:** fpdf2 y reportlab para informes técnicos con firma digital y código QR de verificación.
* **Blockchain:** pycardano + Blockfrost para anclaje y consulta de eventos en redes públicas.
* **Inteligencia Artificial:** integración con modelos de lenguaje de gran tamaño vía Groq para asistencia conversacional industrial basada en datos reales.
* **Email transaccional:** servicio propio con envío en segundo plano desde FastAPI.
* **Procesamiento de imágenes:** Pillow para evidencias fotográficas.
* **Códigos QR:** qrcode con PIL para verificación de certificados.
* **Infraestructura:** Docker multi-stage, plataforma de Web Services en la nube, secret managers y health checks.

---

## 🧠 4. Protocolo de Notarización y Auditoría

La Sucursal 3 implementa un protocolo de **revisión por auditor humano** antes de cualquier publicación:

1. El técnico registra la intervención en el **historial clínico** del activo con estado de *en revisión*.
2. El sistema dispara automáticamente la **notarización criptográfica** del evento.
3. El administrador visualiza el informe en su panel de auditoría, evalúa las mediciones, fotos y observaciones, y emite un veredicto:
   * **Aprobado y publicado:** el informe se promueve a la vista oficial del cliente y queda anclado en blockchain.
   * **Rechazado para corrección:** el informe se devuelve al técnico con observaciones del auditor.
4. Cualquier inserción en tablas principales dispara automáticamente la sincronización con el bus de eventos para alimentar el portal corporativo del ecosistema.

---

## 👥 5. Portal de Clientes — Autoservicio Transaccional

El cliente final dispone de un portal propio con las siguientes capacidades:

* Registro validado contra el NIT/Cédula previamente registrado en las sedes de Green Battery (no se permiten cuentas duplicadas por documento ni por correo).
* Inicio de sesión con sesión temporal gestionada por tokens.
* Consulta de sus sedes, sub-sedes y equipos vinculados.
* Solicitud de visitas técnicas con tipo (diagnóstico, preventivo, correctivo, prueba de autonomía) y lugar (sede, sub-sede, dirección personalizada).
* Seguimiento del estado de sus solicitudes en tiempo real (pendiente, asignada, confirmada, cancelada).
* Recepción automática de confirmación por correo electrónico cuando una visita es agendada.
* Descarga de los reportes autorizados por Green Battery.

La información del portal se sincroniza bidireccionalmente con el núcleo industrial, garantizando que el cliente siempre vea el estado real del servicio.

---

## 📅 6. Agenda Inteligente — CRM Corporativo

La agenda de Green Battery funciona como un CRM ligero con foco operativo:

* **Calendario centralizado del administrador:** vista única de todas las agendas y solicitudes con agrupación por técnico.
* **Consulta de ocupación por fecha:** evita sobre-asignaciones antes de despachar.
* **Asignación idempotente:** si ya existe una nota con la misma solicitud o los mismos criterios, la asignación actualiza el registro en lugar de duplicarlo.
* **Auto-reparación de sincronizaciones:** si una solicitud queda huérfana en una de las bases de datos, el sistema la recrea automáticamente al despacho.
* **Semáforo de visita en campo:** amarillo al asignar, morado al marcar llegada, verde al marcar salida, con timestamps del servidor.
* **Bitácora profesional:** notas con timer activo (iniciar / pausar), proyectos jerárquicos padre-hijo, evidencias adjuntas y catálogo de habilidades técnicas etiquetadas por actividad.
* **Festivos laborales:** calendario de festivos colombianos integrado para planificación operativa.

---

## 🧠 7. Destrezas y Conocimientos Aplicados

* Diseño e implementación de sistemas de trazabilidad forense con auditoría humana sobre datos críticos.
* Modelado de ciclos de vida de activos industriales y representación inmutable mediante anclaje criptográfico.
* Arquitectura de doble base de datos relacional con sincronización bidireccional controlada y auto-reparación de inconsistencias.
* Implementación de políticas de seguridad por segregación de dominios (administrador vs. propietario) en módulos compartidos.
* Diseño de portales transaccionales con validación de identidad contra catálogos internos preexistentes.
* Construcción de CRM ligero con timer de actividades, jerarquía de proyectos y catálogo de habilidades técnicas.
* Generación de reportes PDF institucionales con firma digital, código QR y exploración blockchain.
* Integración de modelos de lenguaje con datos operativos reales (cero mocks, cero alucinaciones permitidas).
* Operación de pipelines asíncronos con tareas en segundo plano para notificaciones transaccionales.
* Diseño de experiencia de usuario diferenciada para técnicos en campo, administradores y clientes finales.

---

## 🎯 8. Casos de Uso Reales

* **UPS:** Seguimiento de sistemas de alimentación de respaldo en centros de datos y puntos de venta.
* **Baterías industriales:** Gestión y trazabilidad de bancos de baterías para infraestructura crítica.
* **Cargadores industriales:** Registro de cargadores de baterías y su historial de mantenimiento.
* **Montacargas eléctricos:** Trazabilidad de flotas de montacargas con historial clínico por equipo.
* **Gestión multi-sede:** Administración jerárquica sede → sub-sede con reportes autónomos por cliente.

---

*Notaría Digital Industrial — trazabilidad soberana para activos críticos.*