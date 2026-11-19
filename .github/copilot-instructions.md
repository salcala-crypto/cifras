# Instrucciones del proyecto

## Propósito

Este workspace contiene una visualización editorial en español llamada **“Las cifras de la ausencia”**. El proyecto usa scrollytelling para explicar datos sobre desapariciones y localizaciones en México.

- Archivo principal: `las_cifras_de_la_ausencia_scrollytelling.html`
- Datos: `resultado_final_desapariciones.csv`
- Tecnología: HTML, CSS y JavaScript sin compilación ni framework.
- Visualización: D3.js v7, Scrollama y Papa Parse, cargados desde CDN.

## Reglas generales

- Mantener una única página autocontenida en el archivo HTML salvo que se solicite explícitamente una separación de recursos.
- Preservar el enfoque periodístico, editorial y respetuoso al trabajar con temas de desaparición y violencia.
- Responder y redactar textos en español, usando lenguaje claro y neutral.
- Mantener las funciones modulares y separadas por los bloques existentes.
- No introducir frameworks, paquetes locales ni procesos de compilación innecesarios.
- Evitar cambios globales de diseño que no estén relacionados con la solicitud.
- No borrar ni reemplazar textos, datos o secciones pendientes sin indicación explícita.

## Datos

- El CSV principal usa estas columnas: `entidad`, `hombres`, `mujeres`, `localizadas_sin_vida`, `localizadas_vivas`, `no_localizadas` y `total_sumado`.
- Mantener la validación de encabezados requeridos antes de normalizar datos.
- Convertir números de forma segura y evitar valores implícitamente incorrectos.
- Mantener la propiedad `rawEntidad` cuando sea necesario conservar el nombre original del registro.
- El CSV normaliza `México` como `Estado de México` solamente para presentación. No alterar el CSV fuente ni asumir que esta transformación cambia el dato original.
- El desglose por sexo puede tener diferencias entre `hombres + mujeres` y `total_sumado`; conservar esta realidad y representarla explícitamente como brecha o registros sin asignar.
- No inventar cifras, fuentes, unidades ni conclusiones periodísticas.
- Las modificaciones de cargas CSV deben preservar el flujo existente con Papa Parse y el estado compartido `APP_STATE`.

## Visualización y diseño

- Conservar la jerarquía editorial: portada, secciones scrollytelling, piezas gráficas y metodología/nota final.
- Mantener la paleta definida en `:root` y `COLORS`:
  - total: `#E07A5F`
  - hombres: `#6F90CC`
  - mujeres: `#D98196`
  - no localizadas: `#E9C46A`
  - localizadas con vida: `#52B788`
  - localizadas sin vida: `#C56A7A`
- Usar las tipografías existentes: Newsreader para títulos/editorial, Inter para cuerpo e interfaz y JetBrains Mono para cifras y etiquetas técnicas.
- Preservar fondos oscuros, tarjetas translúcidas y contraste accesible.
- Mantener la estructura sticky de Scrollama y el estado activo de cada paso.
- Toda visualización debe seguir siendo legible en escritorio y móvil.
- Al modificar SVG o D3, tener en cuenta el redimensionado de ventana y volver a calcular dimensiones y transiciones.
- Evitar animaciones excesivas o que dificulten la lectura de cifras.

## Accesibilidad e interacción

- Conservar atributos semánticos existentes: `role`, `aria-label`, estados activos y texto alternativo cuando corresponda.
- Los controles deben seguir siendo operables con teclado.
- Mantener etiquetas claras en español para filtros, carga de archivos y navegación.
- No depender exclusivamente del color para comunicar categorías.
- El tooltip debe cerrar o ocultarse correctamente y ubicarse dentro del viewport.
- Conservar soporte táctil y evitar controles demasiado pequeños en móvil.

## JavaScript

- Mantener `APP_STATE` como fuente central de datos, pasos activos y criterios de ordenamiento.
- Las piezas son independientes, pero deben consumir la misma carga normalizada.
- Actualizar los tres archivos visuales afectados al cargar otro CSV: Pieza 1, Pieza 3 y Pieza 4.
- Las funciones de renderizado deben tolerar datasets vacíos o contenedores inexistentes.
- Preservar las claves de ordenamiento existentes: `total`, `alpha`, `diff`, `pct_noloc`.
- No hacer cálculos de presentación a partir de cadenas no validadas.
- Si se modifica Scrollama, mantener `initScrollama`, el offset y la activación de las piezas.

## CSS y HTML

- Respetar las variables CSS existentes y evitar valores codificados repetidos si ya existe un token.
- Mantener estilos responsivos definidos por media queries.
- Usar selectores existentes antes de agregar clases nuevas.
- Agrupar cambios por secciones dentro del HTML para facilitar revisión.
- Evitar modificaciones masivas de formato; aplicar cambios pequeños y localizados.

## Validación

- Antes de entregar cambios, revisar sintaxis HTML y JavaScript.
- Probar al menos:
  - carga del CSV incluido;
  - carga de un CSV alternativo válido;
  - filtros de cada pieza;
  - avance entre pasos de Scrollama;
  - comportamiento móvil y redimensionado;
  - ausencia de errores en consola.
- Validar que las cifras mostradas coincidan con los valores normalizados y que los porcentajes tengan denominadores correctos.
- No modificar el CSV fuente para probar la interfaz.
- Si la página se abre por `file://`, mantener compatibles las cargas locales y documentar limitaciones de navegador.

## Flujo de trabajo

- Hacer cambios mínimos y verificables.
- Explicar antes de aplicar una modificación importante qué se cambiará y por qué.
- Tras una edición, revisar el diff y comprobar que no haya texto pendiente accidentalmente eliminado.
- Mantener comentarios útiles en español y no comentar código obvio.
