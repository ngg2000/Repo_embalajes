# Registro de embalajes — Etapa 1

Versión 0.1.0. Investigación técnica interna.

Esta primera etapa verifica GitHub → Vercel y el formulario. El registro inicial está vacío. Los cambios se guardan únicamente en el navegador; todavía no hay usuarios ni base compartida. Usar solo datos ficticios.

## 1. Subir a GitHub

1. Descomprimir el ZIP.
2. Entrar a GitHub y crear un repositorio privado llamado `registro-embalajes` (nombre sugerido).
3. En el repositorio, elegir **Add file → Upload files** (o **uploading an existing file** si está vacío).
4. Subir el contenido de esta carpeta conservando `public/index.html`. En la raíz deben quedar `vercel.json` y `README.md`. No subir el ZIP ni una carpeta adicional que envuelva todo.
5. Guardar con **Commit changes**. Si la carga web omite `.gitignore`, se puede crear luego con **Add file → Create new file**; no es necesario para ejecutar esta etapa.

## 2. Conectar Vercel

1. Entrar a Vercel y elegir **Add New → Project**.
2. Conectar GitHub y autorizar únicamente el repositorio elegido.
3. Importar `registro-embalajes`.
4. Framework: **Other**. Root Directory: raíz del repositorio. Output Directory: `public` (ya declarado en `vercel.json`). No requiere paquetes, variables de entorno, ni comando de compilación.
5. Elegir **Deploy** y esperar **Ready**. Abrir la dirección `.vercel.app`.

Si el asistente pide comandos de instalación o compilación, dejarlos vacíos. Si aparece 404, comprobar que el repositorio tenga `public/index.html`, que Root Directory sea la raíz y que Output Directory sea `public`.

## 3. Comprobación manual en la web

- Confirmar que aparece **Etapa 1 · versión 0.1.0 · prueba local** y 0 registros en un navegador que nunca haya usado esta versión.
- Crear un registro ficticio con Part Number `PRUEBA-001`, CQCA `CQCA-PRUEBA-001` y código secundario `CAJA-PRUEBA`.
- Ingresar largo 1 m, ancho 0,5 m, alto 0,4 m. Dejar M3 vacío: al guardar debe resultar 0,2 m³.
- Ingresar 4 primarios por secundario y 10 piezas por primario. Dejar piezas por secundario vacío: debe resultar 40.
- Guardar, buscar `PRUEBA-001`, abrir la ficha y cambiar un campo vacío.
- Recargar la página: debe conservar los datos en ese mismo navegador.
- Descargar JSON: debe contener 15 claves por registro; números como números, vacíos como null.
- Descargar XLSX: debe abrir en Excel con hoja `Registro` y 15 columnas.
- Abrir la dirección desde otro navegador: debe comenzar vacío. Eso confirma el almacenamiento local de esta etapa, no es un fallo de sincronización.

## 4. Comprobar la actualización automática

En GitHub, editar `public/index.html` y cambiar **solo el texto visible** `versión 0.1.0` por `versión 0.1.1`. Guardar el commit. Vercel debe generar otro despliegue automáticamente. Una vez Ready, recargar la misma dirección y confirmar el nuevo número visible. No cambiar las claves de almacenamiento.

## Criterio para cerrar esta etapa

La web abre, permite alta y edición, conserva la prueba tras recargar, exporta JSON/XLSX y muestra el cambio de versión hecho desde GitHub. La publicación real y estos pasos requieren verificación en la cuenta del usuario; las comprobaciones automatizadas incluidas son previas al despliegue.

## Etapas siguientes

2. Crear Supabase y conectar una tabla de prueba.
3. Habilitar usuarios autorizados y permisos sobre los registros.
4. Probar dos sesiones: altas, cambios remotos y conflicto sobre una misma ficha.
5. Importar el registro real validado y comprobar las exportaciones.

Los datos de embalajes y las claves privadas no se incluyen en el repositorio ni en esta publicación de prueba. Un repositorio privado no implica que la URL publicada sea privada. No conectar la base real hasta implementar y verificar los permisos.
