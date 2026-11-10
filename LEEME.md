# Boletas AXS (Voicewave)

Una sola base de código: **app Android (APK)** y **versión web instalable (PWA)**. Ambas funcionan sin internet y sincronizan con Supabase.

## 1. Crear los usuarios de los técnicos (una vez)
En Supabase: Authentication → Users → Add user (correo y contraseña, marca "Auto Confirm User").
Luego, en SQL Editor, registra a cada uno con su UUID (columna "User UID"):

    insert into public.tecnicos (id, nombre, rol) values
    ('UUID-OVIDIO','Ovidio Ajchura','tecnico'),
    ('UUID-EDDY','Eddy','tecnico'),
    ('UUID-REMBERTO','Remberto','tecnico'),
    ('UUID-CARLOS','Carlos López','tecnico'),
    ('UUID-SUPERVISOR','Supervisor','supervisor');

## 2. Obtener el APK y la web (sin instalar nada en tu PC)
1. Crea un repositorio en github.com y sube todo el contenido de esta carpeta.
2. En el repositorio: Settings → Pages → Source: **GitHub Actions**.
3. Pestaña **Actions** → "Construir app" → Run workflow.
4. Al terminar: descarga el APK en *Artifacts → boletas-axs-apk* (instálalo en el celular permitiendo "orígenes desconocidos"). La web queda en `https://TU-USUARIO.github.io/NOMBRE-REPO/` y se instala desde Chrome con "Agregar a pantalla de inicio".
(GitHub Pages en repositorios privados requiere plan de pago; si es privado, usa solo el APK.)

## 3. Uso diario
Entrar → **Importar PDF** (elige los PDF de AXS del día, incluido el de formularios) → llenar → **Cerrar boleta**. Se sincroniza solo al haber internet.

## Datos que se guardan
Tablas `ordenes`, `materiales_usados`, `bajas_detalle`, `equipos` y `cierres`. Vistas para tu planilla: `v_planilla_materiales` y `v_planilla_bajas`.
