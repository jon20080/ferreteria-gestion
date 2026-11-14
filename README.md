# Ferretería El Tornillo — Gestión de Inventario y Proveedores

Aplicación web estática, dinámica y responsive (enfoque móvil primero) para la administración de **artículos**, **proveedores** y **control de existencias (stock)** en tiempo real con persistencia en **Supabase (PostgreSQL)**.

## Características principales

- **Panel de Inicio**: Hero corporativo, tarjetas de resumen (total de artículos, proveedores y alertas de stock bajo `≤ 5`) y sección de reposición rápida.
- **Control de Stock en tiempo real**: Botones táctiles `−` / `+` y campo numérico con botón **Aplicar** para ajustar existencias al instante.
- **CRUD completo de Artículos**: Crear, listar (vista Tarjetas o Tabla), buscar, filtrar por categoría/stock bajo, editar y eliminar.
- **CRUD completo de Proveedores**: Crear, listar, editar y eliminar proveedores vinculados a los artículos.
- **Validaciones y UX**: Campos obligatorios, precios y existencias no negativos, confirmación antes de eliminar, mensajes claros de éxito/error, imágenes con respaldo automático y modo claro/oscuro.

## Tecnologías utilizadas

- **HTML5, CSS3 y JavaScript (ES6+)** puro (sin frameworks ni herramientas de compilación).
- **Supabase JS v2** (`@supabase/supabase-js@2`) cargado vía CDN.
- **PostgreSQL + Row Level Security (RLS)** en Supabase.

## Ejecución local

1. Clona o descarga este repositorio.
2. Ejecuta el script `schema.sql` en el **SQL Editor** de tu proyecto en Supabase.
3. Abre `config.js` y reemplaza los valores de ejemplo con tu `SUPABASE_URL` y tu clave pública `SUPABASE_KEY` (`anon` / `publishable`).
4. Abre la carpeta con un servidor local (por ejemplo, la extensión **Live Server** de VS Code, o `npx serve .`, o `python3 -m http.server 8080`) y visita `http://localhost:8080`.

## Publicación en GitHub y Render (Static Site)

1. Sube los archivos (`index.html`, `config.js`, `schema.sql`, `README.md`) a un repositorio en **GitHub**.
2. Inicia sesión en [Render](https://render.com) y selecciona **New +** -> **Static Site**.
3. Conecta tu repositorio de GitHub.
4. Configura el servicio con:
   - **Build Command**: *(dejar vacío)*
   - **Publish Directory**: `.`
5. Haz clic en **Create Static Site**. En pocos segundos tu aplicación estará publicada con HTTPS.

## Nota de seguridad

- Las credenciales se encuentran aisladas en `config.js`.
- Utiliza **únicamente** la clave pública (`anon` / `publishable`) de Supabase; **nunca** expongas la clave `service_role` en código cliente.
- Las políticas RLS incluidas permiten lectura y escritura pública con fines educativos. Para un entorno de producción real, implementa **Supabase Auth** y restringe las políticas RLS a usuarios autenticados.
- Todo texto proveniente de la base de datos se escapa antes de renderizarse en el DOM para prevenir ataques **XSS**.
