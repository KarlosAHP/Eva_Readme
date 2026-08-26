# EVA Security Core

Backend FastAPI + Jinja2 + SQLAlchemy para el ecosistema EVA (EVA Vault + EVA Notary,
base para Authenticator y Verify). Construido siguiendo las reglas innegociables del
Documento Maestro del proyecto: cambios aditivos, cero datos ficticios, cifrado antes
de insertar, RLS pendiente de aplicar en Supabase.

## 1. Correr en local

```bash
python3 -m venv .venv
source .venv/bin/activate        # En Windows: .venv\Scripts\activate
pip install -r requirements.txt

cp .env.example .env
python -c "from cryptography.fernet import Fernet; print(Fernet.generate_key().decode())"
# pega esa clave en ENCRYPTION_KEY dentro de .env

uvicorn app.main:app --reload
```

Abre `http://localhost:8000`. Por defecto usa SQLite (`eva_local.db`), así que no
necesitas Supabase para probar. Las tablas se crean solas al arrancar (aditivo,
nunca destructivo — ver `app/database.py`).

Flujo: Bienvenida → Crear cuenta → Iniciar sesión → Dashboard → Bóveda / Notary.

Ya probado end-to-end (signup, login, guardar nota cifrada, generar sello,
verificación de que el payload nunca queda en texto plano en la base).

## 2. Qué hace hoy

- **Auth**: registro y login con `bcrypt` (nunca contraseñas en claro), sesión por
  cookie firmada (`itsdangerous`), sin tokens en localStorage.
- **EVA Vault**: cada nota se cifra con Fernet (AES autenticado) **en el servidor,
  antes de tocar la base de datos**. Nunca se guarda el contenido en claro, y la
  lista tampoco lo muestra descifrado.
  ⚠️ Esto es la medida interina descrita en la sección 5 del documento maestro,
  no el modelo zero-knowledge final (la clave hoy vive en el servidor).
- **EVA Notary**: genera un hash SHA-256 del dato + `policy_id`, y solo guarda el
  hash — nunca el contenido original.
- **Dashboard**: los contadores y la actividad reciente salen de consultas reales
  a la base. Sin datos de relleno (regla 2 del documento maestro).

## 3. Conectar a Supabase (cuando quieras salir de SQLite)

1. En Supabase, copia tu connection string de Postgres.
2. En `.env`, cambia:
   ```
   DATABASE_URL=postgresql://postgres:TU_PASSWORD@db.xxxxxxxx.supabase.co:5432/postgres
   ```
3. Vuelve a arrancar la app — `init_db()` crea las tablas que falten (aditivo,
   nunca hace `DROP` ni `ALTER` destructivo).
4. **Importante**: activa RLS por tabla en Supabase (regla 6). Las políticas
   actuales solo cubren `INSERT` en `vault_personal` y `notary_logs`. Antes de
   exponer esto públicamente, añade políticas de `SELECT/UPDATE/DELETE`
   filtradas por usuario (`auth.uid()` o equivalente) — como **políticas
   nuevas**, sin tocar ni reemplazar las existentes.

## 4. Subir a GitHub

```bash
git init
git add .
git commit -m "EVA Security Core: scaffold funcional (auth, vault, notary)"
git branch -M main
git remote add origin https://github.com/TU_USUARIO/eva-security-core.git
git push -u origin main
```

`.gitignore` ya excluye `.env`, `*.db` y `__pycache__/`. Nunca subas tu
`ENCRYPTION_KEY` real ni tu base local al repo.

## 5. Desplegar en Render

El repo ya incluye `render.yaml` y `Procfile`.

1. En Render → **New > Blueprint**, apunta al repo de GitHub.
2. Render detecta `render.yaml` y crea el servicio web automáticamente.
3. En **Environment**, define:
   - `DATABASE_URL` → tu connection string de Supabase (Postgres)
   - `ENCRYPTION_KEY` → una clave Fernet nueva, generada igual que en local
   - `POLICY_ID` → puedes dejar el valor por defecto o poner el tuyo
   - `SECRET_KEY` → Render la genera sola (`generateValue: true`)
4. Deploy. Render instala `requirements.txt` y corre
   `uvicorn app.main:app --host 0.0.0.0 --port $PORT`.

## 6. Siguientes pasos (secciones 4 y 5 del documento maestro)

- Resolver el checklist criptográfico completo (clave derivada por usuario,
  recuperación de cuenta sin admin, rotación de claves) antes de escalar
  Authenticator y Verify.
- Políticas RLS completas por usuario en Supabase (no solo `INSERT`).
- EVA Authenticator como capa de login/MFA propia.
- Botón "ver / descifrar" en la bóveda (hoy la lista solo muestra metadatos,
  nunca el contenido descifrado, a propósito).
- `corporate_files` / `corporate_announcements`: aún sin superficie en esta UI.

## Estructura

```
app/
  main.py            # arranque de FastAPI, monta routers y static
  config.py           # variables de entorno
  database.py          # modelos SQLAlchemy = esquema del documento maestro
  security.py          # hashing, sesión firmada, cifrado Fernet
  templating.py         # instancia compartida de Jinja2Templates
  routers/
    auth.py            # bienvenida, signup, login, logout
    dashboard.py         # dashboard con datos reales
    vault.py            # EVA Vault
    notary.py           # EVA Notary
  templates/           # Jinja2 (paleta y estilo de tus mockups)
  static/
requirements.txt
render.yaml / Procfile
.env.example
```
