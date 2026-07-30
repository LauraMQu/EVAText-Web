# EVAText Web

EVAText es un complemento para Microsoft Word que permite insertar comentarios de retroalimentación académica sobre fragmentos de texto seleccionados.

Esta versión fue desarrollada como un **Office Add-in** con TypeScript y Office.js, por lo que puede funcionar en Word para Windows, Word para la web y Word para Mac, sujeto a la versión de Office y a la compatibilidad de la API utilizada.

## Funciones principales

- Pestaña personalizada **EVAText** en la cinta de Word.
- Panel lateral con un catálogo de comentarios.
- Buscador por grupo, categoría, nombre y contenido.
- Filtro por grupo.
- Inserción de comentarios sobre el texto seleccionado.
- Catálogo organizado de comentarios de retroalimentación.
- Funcionamiento desde una dirección pública mediante GitHub Pages.
- No requiere ejecutar un instalador `.exe`.

## Dirección pública

```text
https://lauramqu.github.io/EVAText-Web/
```

Panel:

```text
https://lauramqu.github.io/EVAText-Web/taskpane.html
```

Repositorio:

```text
https://github.com/LauraMQu/EVAText-Web
```

## Requisitos

- Microsoft Word compatible con complementos de Office.
- Conexión a Internet.
- Una cuenta de Microsoft que permita instalar o cargar complementos.
- Para pruebas manuales, el archivo `manifest.xml` de producción.

[## Instalación de prueba en Word de escritorio para Windows

Mientras EVAText no esté publicado en Microsoft Marketplace, puede instalarse manualmente para pruebas mediante una carpeta compartida de confianza.

La persona usuaria solo necesita el archivo de producción:

```text
manifest.xml : https://lauramqu.github.io/EVAText-Web/](https://lauramqu.github.io/EVAText-Web/)
1. Descargar el manifiesto
Abre el repositorio:
https://github.com/LauraMQu/EVAText-Web
Selecciona el archivo manifest.xml.
Pulsa Download raw file.
Guarda el archivo en el computador.
2. Crear una carpeta para el catálogo
Crea una carpeta, por ejemplo:
C:\EVAText-Catalogo
Copia dentro de ella el archivo:
manifest.xml
3. Compartir la carpeta
Haz clic derecho sobre la carpeta EVAText-Catalogo.
Selecciona Propiedades.
Abre la pestaña Compartir.
Pulsa Uso compartido avanzado.
Marca Compartir esta carpeta.
Pulsa Permisos.
Verifica que exista al menos permiso de lectura.
Copia la ruta de red de la carpeta.

La ruta puede verse así:

\\NOMBRE-DEL-EQUIPO\EVAText-Catalogo
4. Registrar la carpeta como catálogo de confianza
Abre Word de escritorio.
Entra en Archivo → Opciones.
Selecciona Centro de confianza.
Pulsa Configuración del Centro de confianza.
Entra en Catálogos de complementos de confianza.
En URL del catálogo, pega la ruta compartida.
Pulsa Agregar catálogo.
Marca Mostrar en el menú.
Pulsa Aceptar.
Cierra Word completamente.
Abre Word nuevamente.
5. Agregar EVAText
Abre un documento en Word.
Entra en Inicio → Complementos.
Selecciona Más complementos u Opciones avanzadas.
Abre la sección Carpeta compartida.
Selecciona EVAText Web.
Pulsa Agregar.
Espera a que aparezca la pestaña EVAText.
Pulsa Abrir EVAText.


## Instalación en Word web

1. Descarga el archivo `manifest.xml` del repositorio.
2. Abre Word para la web con una cuenta de Microsoft.
3. Crea o abre un documento.
4. Entra en **Insertar** o **Inicio**.
5. Abre **Complementos**.
6. Entra en **Mis complementos**.
7. Selecciona **Cargar mi complemento**.
8. Elige el archivo `manifest.xml`.
9. Espera a que aparezca la pestaña **EVAText**.
10. Pulsa **Abrir EVAText**.

> Algunas cuentas institucionales bloquean la carga manual de complementos. En ese caso puede ser necesario usar una cuenta personal de Microsoft o solicitar autorización al administrador de Microsoft 365.

## Uso

1. Abre la pestaña **EVAText**.
2. Pulsa **Abrir EVAText**.
3. Escribe o abre un texto en Word.
4. Selecciona una palabra, oración o fragmento.
5. Busca el comentario que necesites.
6. Puedes filtrar por grupo.
7. Pulsa **Insertar comentario**.
8. Word agregará el comentario al fragmento seleccionado.

El texto completo del comentario no se muestra en el panel para evitar redundancia. Solo aparece al insertarse en Word.

## Instalación  en Word para Mac

1. Descarga el archivo `manifest.xml`.
2. Cierra Word.
3. Abre Finder.
4. Selecciona **Ir → Ir a la carpeta…**
5. Escribe:

```text
~/Library/Containers/com.microsoft.Word/Data/Documents/wef
```

6. Si la carpeta `wef` no existe, créala.
7. Copia `manifest.xml` dentro de esa carpeta.
8. Abre Word nuevamente.
9. Crea o abre un documento.
10. Busca EVAText en los complementos disponibles.
11. Abre la pestaña **EVAText** y pulsa **Abrir EVAText**.

### Instalar dependencias

```powershell
cd "D:\Laura\Proyectos\EVAText-Web-Completo"
npm ci
```

### Iniciar el complemento localmente

```powershell
npm start
```

Esto inicia un servidor de desarrollo en:

```text
https://localhost:3000
```

Durante esta prueba, la terminal debe permanecer abierta.

### Detener el complemento

```powershell
npm stop
```

### Validar el manifiesto

```powershell
npm run validate
```

### Compilar la versión de producción

```powershell
npm run build
```

La compilación genera la carpeta `dist`. Los archivos de `dist` son los que se publican en GitHub Pages.

## Diferencia entre los manifiestos

### Manifiesto de desarrollo

```text
manifest.xml
```

Está en la raíz del proyecto y apunta a:

```text
https://localhost:3000
```

Se usa con `npm start`.

### Manifiesto de producción

```text
dist\manifest.xml
```

Apunta a:

```text
https://lauramqu.github.io/EVAText-Web/
```

Este es el archivo que debe usarse para probar la versión pública en Word web o Mac.

## Estructura principal del proyecto

```text
EVAText-Web-Completo/
├── .vscode/
├── assets/
├── src/
│   ├── commands/
│   └── taskpane/
│       ├── comentarios.ts
│       ├── taskpane.css
│       ├── taskpane.html
│       ├── taskpane.ts
│       └── word.ts
├── manifest.xml
├── package.json
├── package-lock.json
├── tsconfig.json
├── webpack.config.js
└── dist/
```

## Archivos importantes

### `src/taskpane/comentarios.ts`

Contiene el catálogo de comentarios de EVAText.

### `src/taskpane/word.ts`

Contiene la lógica del panel, el buscador, los filtros y la inserción del comentario.

### `src/taskpane/taskpane.html`

Define la estructura visible del panel lateral.

### `src/taskpane/taskpane.css`

Define los estilos visuales.

### `manifest.xml`

Configura el complemento, la pestaña de la cinta, el botón, los iconos, los permisos y las direcciones del panel.

### `webpack.config.js`

Configura la compilación local y de producción.

## Actualización de comentarios

1. Abre `src/taskpane/comentarios.ts`.
2. Busca el comentario por su nombre o identificador.
3. Modifica el valor de `texto`.
4. Guarda el archivo.
5. Prueba localmente con `npm start`.
6. Cuando esté validado, ejecuta `npm run build`.
7. Sube nuevamente el contenido actualizado de `dist` al repositorio publicado.

## Actualización de GitHub Pages

1. Ejecuta `npm run build`.
2. Abre la carpeta `dist`.
3. Selecciona todo su contenido.
4. Sube los archivos a la raíz del repositorio `EVAText-Web`.
5. Reemplaza los archivos anteriores.
6. Crea un nuevo commit.
7. Espera a que GitHub Pages termine de publicar.

La dirección pública no cambia.

## Iconos

Los iconos se encuentran en `assets/`:

```text
icon-16.png
icon-32.png
icon-64.png
icon-80.png
icon-128.png
logo-filled.png
```

Los nombres deben conservarse para que el manifiesto pueda encontrarlos.

## Solución de problemas

### El panel intenta conectarse a `localhost:3000`

Se cargó el manifiesto de desarrollo. Usa `dist\manifest.xml`.

### El panel no abre durante el desarrollo

Comprueba que la terminal esté ejecutando `npm start`.

### El panel muestra “Cargando EVAText…” en una pestaña normal del navegador

Es normal. EVAText está diseñado para ejecutarse dentro de Word.

### Word conserva una versión anterior

Cierra Word completamente y vuelve a abrirlo. Si continúa, elimina el complemento anterior desde **Mis complementos** y carga nuevamente el manifiesto correcto.

### El cambio no aparece en GitHub Pages

Comprueba que:

- Subiste el contenido de `dist`.
- Los archivos estén en la raíz del repositorio.
- GitHub Pages use la rama `main` y la carpeta `/(root)`.
- El despliegue haya terminado correctamente.

### La cuenta institucional no permite cargar el complemento

Prueba con una cuenta personal o solicita al administrador que permita o distribuya el complemento.

## Seguridad y privacidad

EVAText:

- No requiere un instalador ejecutable.
- No modifica Word fuera de las funciones autorizadas por el manifiesto.
- Solicita permiso de lectura y escritura sobre el documento para insertar comentarios.
- No debe recopilar información personal ni enviar el contenido del documento a servicios externos, salvo que en el futuro se agregue expresamente alguna función que lo requiera.

Antes de una publicación pública en Microsoft Marketplace se debe crear:

- Política de privacidad.
- Página de soporte.
- Términos de uso, si aplican.
- Información de contacto.

## Próximos pasos

- Completar la prueba en Word para Mac.
- Revisar todos los comentarios y textos.
- Probar accesibilidad y modo oscuro.
- Crear documentación para usuarios finales.
- Crear política de privacidad.
- Crear página de soporte.
- Preparar capturas e iconos para Microsoft Marketplace.
- Publicar EVAText en Microsoft Marketplace.

## Estado del proyecto

EVAText ya fue probado en:

- Word para Windows.
- Word para la web.
- GitHub Pages sin depender de `localhost`.

## Privacidad

Consulta la política de privacidad de EVAText:

https://lauramqu.github.io/EVAText-Web/privacy.html

## Autora y mantenimiento

Repositorio mantenido por `LauraMQu`.
