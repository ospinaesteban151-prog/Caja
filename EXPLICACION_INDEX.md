# Explicación detallada de `index.html`

Este documento explica la estructura, sintaxis y propósito del archivo [`index.html`](./index.html). Los números corresponden a las líneas del archivo fuente. El HTML define el contenido, el CSS (incluido dentro de `<style>`) define su apariencia y el JavaScript (incluido dentro de `<script>`) calcula y actualiza la interfaz.

> Las líneas vacías no ejecutan instrucciones: separan bloques para que el código sea más fácil de leer. En las explicaciones siguientes se indican los rangos completos, incluidos esos espacios, para que ninguna parte del archivo quede sin ubicar.

## 1. Documento y cabecera HTML

| Línea | Sintaxis y funcionamiento | Por qué se usa |
|---|---|---|
| 1 | `<!DOCTYPE html>` es la declaración del tipo de documento. | Indica al navegador que interprete la página con el estándar moderno de HTML, en lugar de un modo antiguo de compatibilidad. |
| 2 | `<html lang="es">` abre el elemento raíz y define `lang`, un atributo global con el idioma principal. | El idioma español ayuda a lectores de pantalla, motores de búsqueda y herramientas de traducción. |
| 3 | `<head>` inicia la sección de metadatos y recursos; no es contenido principal visible. | Agrupa la configuración que el navegador necesita antes de mostrar el cuerpo. |
| 4 | `<meta charset="UTF-8">` declara la codificación de caracteres. | UTF-8 permite mostrar correctamente tildes, eñes, signos y emojis usados en la página. |
| 5 | `<meta name="viewport" content="width=device-width, initial-scale=1.0">` configura el área visible en dispositivos móviles. `width=device-width` usa el ancho del dispositivo y `initial-scale=1.0` evita un zoom inicial artificial. | Hace que el diseño se adapte al ancho real de teléfonos y tabletas. |
| 6 | `<title>…</title>` establece el título del documento. | El texto aparece en la pestaña del navegador y puede usarse como título del marcador. |
| 7 | `<style>` abre una hoja de estilos CSS escrita directamente en el HTML. | Mantiene los estilos de este prototipo en el mismo archivo. |

## 2. CSS: variables y estilos generales

En CSS, un selector indica qué elementos se van a modificar; las llaves `{}` delimitan el bloque y cada declaración tiene la forma `propiedad: valor;`. Los comentarios CSS se escriben entre `/*` y `*/`.

| Línea(s) | Sintaxis y funcionamiento | Por qué se usa |
|---|---|---|
| 8–17 | `:root { ... }` selecciona el elemento raíz. Las propiedades `--primary`, `--bg`, `--card`, `--text`, `--border`, `--success`, `--warning` y `--danger` son variables CSS; sus valores `#...` son colores hexadecimales. | Centraliza la paleta y permite reutilizarla con `var(--nombre)`. La línea 17 cierra el bloque. |
| 18 | Línea vacía para legibilidad. | Separa variables y reglas generales. |
| 19 | `* { ... }` usa `*` como selector universal. `box-sizing: border-box` incluye relleno y borde dentro de las dimensiones; `font-family` declara una lista de fuentes alternativas. | Da a todos los elementos un cálculo de tamaño y tipografía coherentes. |
| 20–27 | `body { ... }` selecciona el cuerpo. Las líneas 21–22 definen fondo y color de texto; 23 elimina margen predeterminado; 24 agrega relleno; 25 activa Flexbox; 26 centra horizontalmente el contenido. `rem` es una unidad relativa al tamaño base de fuente. | Establece el aspecto general y centra el contenedor. La línea 27 cierra el bloque. |
| 28 | Línea vacía. | Separa reglas. |
| 29–32 | `.container` selecciona la clase `container`. `max-width` limita el ancho a 900 píxeles; `width: 100%` permite ocupar todo el espacio menor disponible. | Evita que la página sea demasiado ancha y permite adaptarse a pantallas estrechas. |
| 33 | Línea vacía. | — |
| 34–38 | `header` selecciona el encabezado. Las declaraciones fijan separación inferior, borde inferior y espacio bajo el contenido. | Separa el encabezado del resto de la interfaz. |
| 39–40 | `header h1` y `header p` son selectores descendientes: afectan respectivamente el título y párrafo dentro del encabezado. `margin`, `font-size` y `color` ajustan sus detalles. | Controlan la jerarquía y el aspecto del título y subtítulo. |
| 41 | Línea vacía. | Separa reglas. |
| 42 | Comentario CSS ignorado por el navegador. | Describe la cuadrícula que sigue. |
| 43–47 | `.grid` crea CSS Grid, con dos columnas iguales mediante `1fr 1fr` y espacio de `1.5rem` entre ellas. `fr` significa fracción del espacio disponible. | Coloca los dos paneles lado a lado. |
| 48 | Línea vacía. | — |
| 49–55 | `.panel` define fondo, borde sólido, esquinas redondeadas, relleno y sombra. `rgba(0,0,0,0.05)` es negro con 5 % de opacidad. | Da aspecto de tarjeta a cada panel. |
| 56 | Línea vacía. | — |
| 57–62 | `.panel h2` selecciona subtítulos `h2` dentro de un panel y ajusta margen, tamaño, borde inferior y relleno. | Separa el título del contenido de su tarjeta. |
| 63 | Línea vacía. | — |
| 64–66 | `.form-group` agrega margen inferior a cada grupo de campo. | Mantiene una separación vertical uniforme. |
| 67 | Línea vacía. | — |
| 68–73 | `label` hace que las etiquetas sean bloques, establece grosor, margen y tamaño de texto. | Coloca cada etiqueta encima de su control y facilita su lectura. |
| 74 | Línea vacía. | — |
| 75–82 | `input, select` aplica las mismas propiedades a los dos tipos de control: ancho, relleno, borde, radio, tamaño y transición. La coma separa selectores. | Da aspecto consistente a los campos y suaviza el cambio de borde. |
| 83 | Línea vacía. | — |
| 84–87 | `:focus` es una pseudoclase activa cuando el control está enfocado. Se quita el `outline` nativo y se cambia el color del borde. | Señala visualmente el campo activo. |
| 88 | Línea vacía. | — |
| 89 | Comentario CSS sobre feedback de error. | Documenta el bloque siguiente. |
| 90–93 | `input.input-error` selecciona un `input` con la clase `input-error`; cambia borde y fondo a tonos rojos. | JavaScript agrega la clase cuando la cantidad no pasa validación. |
| 94 | Línea vacía. | — |
| 95–100 | `.error-hint` da color, tamaño, margen y `display: none`. | Oculta el mensaje inicialmente; JavaScript lo muestra cuando hay error. |
| 101 | Línea vacía. | — |
| 102–106 | `.btn-group` activa Flexbox, separa botones y agrega margen superior. | Organiza las acciones en una fila. |
| 107 | Línea vacía. | — |
| 108–117 | `button` da estilo común a botones. `flex: 1` reparte el espacio; las otras declaraciones configuran relleno, borde, radio, tipografía, cursor y transición. | Hace que ambos botones tengan igual base visual y sean reconocibles como interactivos. |
| 118 | Línea vacía. | — |
| 119–122 | `.btn-primary` pone fondo principal y texto blanco. | Resalta “Procesar Venta” como acción principal. |
| 123 | Línea vacía. | — |
| 124–127 | `:disabled` selecciona el botón principal deshabilitado; cambia color y cursor. | Comunica que no se puede procesar en ese estado. |
| 128 | Línea vacía. | — |
| 129–132 | `.btn-secondary` aplica gris claro al botón de restablecer y usa el color normal del texto. | Distingue la acción secundaria. |
| 133 | Línea vacía. | — |
| 134 | Comentario que identifica las cajas de resultados. | — |
| 135–141 | `.dependent-box` establece fondo, borde, radio, relleno y margen inferior. | Separa total, stock y autorización en tarjetas internas. |
| 142 | Línea vacía. | — |
| 143–148 | `.total-display` agranda y engrosa el total, le da el color principal y define sus márgenes. | Hace que el valor a pagar destaque. |
| 149 | Línea vacía. | — |
| 150 | Comentario que anuncia la barra de stock. | — |
| 151–158 | `.stock-bar-bg` define carril, altura, color de fondo, bordes, recorte y márgenes. `overflow: hidden` evita que el relleno sobresalga de los bordes redondeados. | Sirve de fondo para la proporción de stock restante. |
| 159 | Línea vacía. | — |
| 160–165 | `.stock-bar-fill` define altura, ancho inicial completo, color y transición de ancho/color. | JavaScript modifica ancho y color según el inventario. |
| 166 | Línea vacía. | — |
| 167 | Comentario que anuncia los estados de autorización. | — |
| 168–178 | `.status-badge` usa Flexbox y centra verticalmente; `gap` separa icono y texto. También configura relleno, radio, tipografía y colores normales. | Crea la insignia del semáforo. |
| 179 | Línea vacía. | — |
| 180–183 | `.status-badge.warning` selecciona el elemento que tenga ambas clases y aplica colores naranjas. | Estiliza el estado de advertencia. |
| 184 | Línea vacía. | — |
| 185–188 | `.status-badge.danger` aplica tonos rojos al elemento con ambas clases. | Estiliza el estado bloqueado. |
| 189 | Línea vacía. | — |
| 190 | Comentario que anuncia los estilos de progreso. | — |
| 191–194 | `.progress-container` pone margen superior y oculta el componente con `display: none`. | El progreso solo aparece durante la simulación. |
| 195 | Línea vacía. | — |
| 196–203 | `.progress-bar-bg` define el carril: ancho, altura, fondo, radio, recorte y margen. | Es el fondo de la barra animada. |
| 204 | Línea vacía. | — |
| 205–210 | `.progress-bar-fill` define altura, ancho inicial cero, color y transición lineal. | Permite animar el avance de 0 a 100 %. |
| 211 | Línea vacía. | — |
| 212–221 | `.toast` define margen, relleno, borde redondeado, colores y tipografía; `display: none` lo oculta inicialmente. | El aviso de éxito se muestra cuando termina la simulación. |
| 222 | `</style>` cierra el CSS. | El navegador continúa leyendo HTML. |
| 223 | `</head>` cierra la cabecera del documento. | Termina los metadatos y recursos. |

## 3. HTML: contenido y controles

Los elementos HTML normalmente tienen una etiqueta de apertura (`<p>`) y una de cierre (`</p>`). Los atributos se escriben dentro de la etiqueta de apertura como `nombre="valor"`. `id` identifica un elemento de forma única; `class` permite asignar estilos compartidos. La indentación no cambia el significado, pero muestra qué elementos están anidados dentro de otros.

| Línea(s) | Sintaxis y funcionamiento | Por qué se usa |
|---|---|---|
| 224 | `<body>` abre el cuerpo visible de la página. | Todo el contenido que sigue hasta `</body>` forma parte de la interfaz. |
| 225 | Línea vacía: separación visual. | — |
| 226 | `<div class="container">` abre el contenedor principal. `div` es un contenedor genérico y `class` lo conecta con la regla CSS `.container`. | Limita y centra el ancho global del simulador. |
| 227 | `<header>` inicia el encabezado semántico del contenido. | Agrupa el título y la explicación breve del prototipo. |
| 228 | `<h1>` define el encabezado principal de la página. | Presenta el nombre del prototipo con la jerarquía más alta. |
| 229 | `<p>` define un párrafo con la descripción del objetivo. | Añade contexto bajo el título. |
| 230 | `</header>` cierra el encabezado. | Mantiene el título y subtítulo agrupados. |
| 231 | Línea vacía. | Separa encabezado y contenido principal. |
| 232 | `<div class="grid">` abre la cuadrícula de paneles. | La clase `.grid` aplica la disposición en dos columnas. |
| 233 | Comentario HTML `<!-- ... -->`, ignorado visualmente por el navegador. | Identifica el panel izquierdo para quien inspecciona el código. |
| 234 | `<section class="panel">` inicia una sección semántica con aspecto de tarjeta. | Agrupa los controles que componen la entrada de la venta. |
| 235 | `<h2>` presenta el título del primer panel. | Explica que los campos sirven para ingresar los datos de la venta. |
| 236 | Línea vacía. | Separa título y formulario. |
| 237 | `<div class="form-group">` abre un grupo de etiqueta y control. | La clase añade separación inferior común a cada campo. |
| 238 | `<label for="producto">` crea la etiqueta del selector. `for` debe coincidir con el `id` del control asociado. | Al hacer clic en la etiqueta, el foco se dirige al selector de producto; también mejora accesibilidad. |
| 239 | `<select id="producto">` abre una lista desplegable identificada como `producto`. | Permite escoger un producto; JavaScript localiza el control con este `id`. |
| 240–242 | Cada `<option>` representa una opción. `value` almacena el precio numérico que leerá JavaScript; `data-stock` es un atributo de datos personalizado que guarda el inventario; el texto entre etiquetas es lo que ve el usuario. | Vincula a cada producto su precio y stock inicial. El navegador conserva el `data-stock` como `option.dataset.stock`. |
| 243 | `</select>` cierra la lista desplegable. | Finaliza el control del producto. |
| 244 | `</div>` cierra el grupo de producto abierto en la línea 211. | Delimita el grupo para aplicar su margen. |
| 245 | Línea vacía. | Separa los campos del formulario. |
| 246 | `<div class="form-group">` abre el grupo del campo cantidad. | Mantiene la misma presentación y espaciado del formulario. |
| 247 | `<label for="cantidad">` vincula el texto con el campo cuyo `id` es `cantidad`. | Hace explícito qué dato se debe ingresar y mejora el uso con tecnologías de asistencia. |
| 248 | `<input type="text" ...>` crea un campo de texto. `id` lo identifica; `value="1"` establece el valor inicial; `placeholder` muestra una pista cuando está vacío. | El usuario escribe la cantidad. Se usa texto para validar explícitamente los caracteres mientras escribe; JavaScript exige un entero positivo. |
| 249 | `<div id="cantidadError" class="error-hint">...` crea el mensaje de error, identificado por `cantidadError`, con estilo de error. | JavaScript cambia su `display` y la clase del campo para indicar que la cantidad no cumple la regla. |
| 250 | `</div>` cierra el grupo de cantidad. | — |
| 251 | Línea vacía. | Separa los campos. |
| 252 | `<div class="form-group">` abre el grupo del descuento. | Aplica el espaciado estándar a este campo. |
| 253 | `<label for="descuento">` etiqueta el selector con el `id` correspondiente. | Explica el dato que se selecciona. |
| 254 | `<select id="descuento">` abre la lista de descuentos. | JavaScript lee el valor elegido para calcular el ahorro y total. |
| 255–257 | Las tres etiquetas `<option>` ofrecen descuentos de 0 %, 10 % y 25 %. Sus `value` son números decimales (`0`, `0.10`, `0.25`), mientras el texto incluye una descripción legible. | El decimal es directamente utilizable como factor en una multiplicación: subtotal por descuento. |
| 258 | `</select>` cierra la lista de descuentos. | — |
| 259 | `</div>` cierra su grupo de formulario. | — |
| 260 | Línea vacía. | Separa los controles de las acciones. |
| 261 | `<div class="btn-group">` abre el contenedor de botones. | La regla Flexbox coloca las acciones juntas. |
| 262 | `<button id="btnProcesar" class="btn-primary">...` crea el botón de acción principal. | El `id` permite conectar el evento JavaScript; la clase da el estilo azul y sirve para la regla de deshabilitado. |
| 263 | `<button id="btnCancelar" class="btn-secondary">...` crea el botón de restablecer. | Su `id` se usa en JavaScript; la clase lo diferencia del botón principal. Aunque se llama `btnCancelar`, su texto aclara que restablece los valores. |
| 264 | `</div>` cierra el grupo de botones. | — |
| 265 | Línea vacía. | Separa los botones del indicador de progreso. |
| 266 | Comentario HTML que anuncia el feedback de demora. | Documenta el objetivo del siguiente bloque. |
| 267 | `<div id="progressContainer" class="progress-container">` crea el contenedor oculto inicialmente para el progreso. | JavaScript lo muestra al procesar y lo oculta al finalizar. |
| 268 | `<div style="...">` crea un contenedor con CSS en línea. `display: flex` alinea los textos; `justify-content: space-between` los separa a extremos; también define tamaño y grosor de texto. | Coloca la descripción del proceso a la izquierda y el porcentaje a la derecha. |
| 269 | `<span>` agrupa texto en línea: mensaje de validación y actualización. | Sirve como etiqueta del progreso. |
| 270 | `<span id="progressText">0%</span>` muestra el porcentaje inicial y proporciona un `id` actualizable. | JavaScript reemplaza el texto con 5 %, 10 % y así sucesivamente. |
| 271 | `</div>` cierra la fila de texto. | — |
| 272 | `<div class="progress-bar-bg">` abre el carril de la barra de progreso. | Recibe el estilo del fondo de la barra. |
| 273 | `<div id="progressFill" class="progress-bar-fill"></div>` crea el relleno vacío de la barra. | JavaScript cambia su ancho inline para representar el porcentaje. |
| 274 | `</div>` cierra el carril. | — |
| 275 | `</div>` cierra `progressContainer`. | Finaliza el componente completo. |
| 276 | Línea vacía. | Separa feedback y aviso final. |
| 277 | `<div id="toastSuccess" class="toast">...` crea el mensaje de éxito con símbolo de verificación. | JavaScript lo muestra cuando termina la simulación. |
| 278 | `</section>` cierra el primer panel. | Termina la sección de entrada. |
| 279 | Línea vacía. | Separa los paneles. |
| 280 | Comentario HTML que anuncia el panel derecho. | Explica que los objetos de ese panel dependen de los valores ingresados. |
| 281 | `<section class="panel">` abre la segunda tarjeta semántica. | Agrupa los resultados y estados calculados. |
| 282 | `<h2>` presenta el título del panel de resultados. | Aclara que los indicadores se actualizan en vivo. |
| 283 | Línea vacía. | Separa encabezado y primer resultado. |
| 284 | `<div class="dependent-box">` abre el bloque del total y ahorro. | Aplica tarjeta interna con el estilo `.dependent-box`. |
| 285 | `<span style="...">` muestra una etiqueta con estilos inline: tamaño, color y texto. | Describe el valor que aparece debajo. |
| 286 | `<div id="totalDisplay" class="total-display">` contiene el total inicial. | JavaScript actualiza el contenido y CSS lo destaca en grande. |
| 287 | `<small id="ahorroDisplay" ...>` muestra el ahorro en texto pequeño y color de éxito. | JavaScript actualiza el monto ahorrado. |
| 288 | `</div>` cierra el bloque del total. | — |
| 289 | Línea vacía. | Separa indicadores. |
| 290 | `<div class="dependent-box">` abre el bloque del stock disponible. | Presenta el inventario en otra tarjeta. |
| 291 | `<div style="...">` crea una fila Flexbox con contenido en extremos y texto pequeño. | Separa el rótulo del stock de la cantidad disponible. |
| 292 | `<span>` contiene el rótulo de disponibilidad restante. | Describe el indicador. |
| 293 | `<strong id="stockText">` contiene el valor inicial de unidades y lo marca como importante. | JavaScript sustituye el texto según cantidad e inventario. |
| 294 | `</div>` cierra la fila de rótulo y valor. | — |
| 295 | `<div class="stock-bar-bg">` abre el fondo de la barra de inventario. | Aloja el relleno visual del stock. |
| 296 | `<div id="stockBar" class="stock-bar-fill"></div>` crea el segmento que representa el stock. | JavaScript cambia ancho y color de acuerdo con las unidades restantes. |
| 297 | `</div>` cierra el fondo de la barra. | — |
| 298 | `</div>` cierra la caja de stock. | — |
| 299 | Línea vacía. | Separa la siguiente tarjeta. |
| 300 | `<div class="dependent-box">` abre la tarjeta de autorización. | Agrupa el estado de la venta. |
| 301–303 | `<span style="display: block; ...">` crea un rótulo en bloque con tamaño, color y margen inferior; el texto está en su propia línea y el cierre `</span>` finaliza el elemento. | Presenta el contexto de la insignia de autorización. |
| 304 | `<div id="statusBadge" class="status-badge">` inicia la insignia del estado normal. | JavaScript cambia sus clases y contenido según stock y total. |
| 305 | `<span>🟢</span>` muestra el indicador verde inicial. | Comunica visualmente una venta normal. |
| 306 | `<span id="statusText">...` contiene el texto inicial del estado. | Tiene un `id` útil para selección directa, aunque el código actual reemplaza el `innerHTML` del contenedor padre en vez de modificar este nodo por separado. |
| 307 | `</div>` cierra la insignia. | — |
| 308 | `</div>` cierra la tarjeta de autorización. | — |
| 309 | `</section>` cierra el panel derecho. | Termina los resultados. |
| 310 | `</div>` cierra la cuadrícula. | Termina el contenedor Flex/Grid de ambos paneles. |
| 311 | `</div>` cierra el contenedor principal. | Finaliza el contenido de `.container`. |

## 4. JavaScript: conexión con la página

JavaScript usa `const` para declarar referencias que no se reasignarán y `let` para variables cuyo valor cambiará. `document.getElementById(...)` busca un elemento por su `id`. El punto (`.`) permite acceder a propiedades o métodos del objeto, y los paréntesis pasan argumentos a una función.

| Línea(s) | Sintaxis y funcionamiento | Por qué se usa |
|---|---|---|
| 312 | Línea vacía. | Separa HTML y código de comportamiento. |
| 313 | `<script>` abre un bloque JavaScript interno. | Permite que la lógica interactiva se entregue junto al HTML, sin cargar un archivo externo. |
| 314–319 | Cada línea declara una constante que guarda el elemento DOM asociado a producto, cantidad, mensaje de error, descuento y botones. | Evita repetir búsquedas del DOM y permite leer o modificar esos controles con nombres claros. |
| 320 | Línea vacía. | Separa grupos de referencias. |
| 321 | Comentario JavaScript de una línea, iniciado por `//`. | Identifica referencias a resultados dependientes. |
| 322–327 | Declaraciones `const` para total, ahorro, texto/barra de stock e insignia/texto de autorización. | Son referencias que la función actualizará al cambiar datos. `statusText` se conserva como referencia, aunque en el código presente no se usa después de declararse. |
| 328 | Línea vacía. | Separa referencias. |
| 329 | Comentario JavaScript que describe los elementos de progreso. | Facilita identificar el siguiente grupo. |
| 330–333 | Se guardan referencias al contenedor de progreso, relleno, texto de porcentaje y aviso de éxito. | El manejador del botón las usa para mostrar, actualizar y ocultar el feedback. |
| 334 | Línea vacía. | Separa configuración de formato y variables del DOM. |
| 335–339 | `const formatoMoneda = new Intl.NumberFormat('es-CO', { ... });` crea un formateador internacional. El primer argumento define la configuración regional; el objeto define `style: 'currency'`, `currency: 'COP'` y `maximumFractionDigits: 0`. Las comas separan propiedades del objeto; las llaves lo delimitan. | Presenta valores con formato de moneda colombiana, sin decimales. `.format(valor)` se invoca más adelante. |
| 340 | Línea vacía. | Separa configuración y función. |

## 5. Función `actualizarDependencias`

Esta función recalcula la vista cuando se modifica un campo. El nombre es descriptivo; `function nombre() {}` declara una función sin parámetros. Sus instrucciones se ejecutan cuando alguien la llama.

| Línea(s) | Sintaxis y funcionamiento | Por qué se usa |
|---|---|---|
| 341 | `function actualizarDependencias() {` declara e inicia la función. | Centraliza los cálculos y actualizaciones para reutilizarlos desde varios eventos y al cargar la página. |
| 342 | Oculta el aviso de éxito usando `style.display`. | Si el usuario cambia los datos después de una venta, elimina el aviso anterior. |
| 343 | `productoSelect.options` accede a las opciones del selector; `selectedIndex` indica el índice de la opción elegida. | Obtiene el objeto de opción que contiene el precio y el stock del producto seleccionado. |
| 344 | `parseFloat(option.value)` convierte el valor del atributo `value` a número decimal. | Convierte el precio textual del HTML en un número para hacer operaciones. |
| 345 | `parseInt(option.dataset.stock)` lee el atributo `data-stock` y lo convierte a entero. | Obtiene el inventario inicial como número. |
| 346 | `parseFloat(descuentoSelect.value)` convierte el descuento seleccionado a número. | Permite multiplicarlo por el subtotal. |
| 347 | `.value.trim()` toma el texto ingresado y quita espacios al principio y al final. | Normaliza la entrada antes de validarla. |
| 348 | Línea vacía. | Separa la lectura de datos de la validación. |
| 349 | Comentario que indica validación mientras se escribe. | Documenta la validación inmediata. |
| 350 | `const esNumeroValido = /^[1-9]\d*$/.test(rawValor);` usa una expresión regular y el método `.test()`. `^` marca inicio, `[1-9]` exige que el primer dígito sea del 1 al 9, `\d*` permite cero o más dígitos adicionales y `$` marca final. | Acepta solo enteros positivos sin signo, cero inicial ni espacios internos. Por ejemplo, acepta `1` y `25`, pero no `0`, `-2`, `2.5` o texto. |
| 351 | El operador ternario `condición ? valorSiVerdadero : valorSiFalso` asigna `parseInt(rawValor)` si es válido y `0` si no. | Mantiene una cantidad numérica segura para cálculos posteriores; los inválidos se detienen enseguida en el `if`. |
| 352 | Línea vacía. | Separa validación y decisión. |
| 353 | `if (!esNumeroValido) {` abre una condición. `!` niega el valor booleano. | Entra a la rama de error cuando la cadena no pasa la expresión regular. |
| 354 | `classList.add('input-error')` agrega una clase CSS al campo. | Aplica borde y fondo de error. |
| 355 | Asigna `block` a `display` del mensaje de error. | Hace visible la explicación del formato requerido. |
| 356 | Asigna `true` a `disabled` del botón. El comentario en línea después de `//` no se ejecuta. | Impide procesar una cantidad no válida y señala el feedback preventivo. |
| 357 | Cambia el texto visible del total a `$0`. `textContent` trata el valor como texto plano. | Evita dejar un total anterior que ya no corresponde a los datos. |
| 358 | Cambia el texto visible del ahorro a cero. | Mantiene coherente el resultado cuando no se puede calcular una cantidad válida. |
| 359 | `return;` termina la ejecución de la función en ese punto. | Evita calcular stock, importe y autorización con entrada inválida. |
| 360 | `} else {` cierra el `if` y abre la rama para datos válidos. | Permite limpiar el estado de error cuando el usuario corrige el campo. |
| 361 | `classList.remove('input-error')` quita la clase. | Restaura el estilo normal del campo. |
| 362 | Oculta el mensaje de error. | Limpia el feedback tras corregir la entrada. |
| 363 | `}` cierra el bloque `else` (y la decisión `if`). | Continúa a cálculos solo en el caso válido. |
| 364 | Línea vacía. | Separa validación y cálculos. |
| 365 | Comentario que identifica el cálculo de total y ahorro. | Organiza las dependencias del formulario. |
| 366 | Multiplica precio por cantidad y guarda el subtotal. | Calcula el precio antes de aplicar descuentos. |
| 367 | Multiplica subtotal por la tasa de descuento y calcula el ahorro. | Convierte la tasa seleccionada en dinero ahorrado. |
| 368 | Resta el ahorro al subtotal. | Obtiene el valor que debe pagar el cliente. |
| 369 | Línea vacía. | Separa los cálculos de las actualizaciones visuales. |
| 370 | `formatoMoneda.format(total)` formatea el número y `textContent` lo escribe en el nodo. | Muestra el total en pesos colombianos legibles. |
| 371 | Una plantilla literal, delimitada por acentos graves, permite insertar una expresión `${...}` dentro de texto. Aquí escribe el ahorro ya formateado. | Actualiza el ahorro con formato de moneda sin concatenaciones difíciles de leer. |
| 372 | Línea vacía. | Separa el cálculo financiero del inventario. |
| 373 | Comentario de la dependencia de stock. | Señala el siguiente conjunto de cálculos. |
| 374 | Calcula unidades restantes restando cantidad vendida del stock máximo. | Determina cuánto inventario queda después de la venta hipotética. |
| 375 | `if (restante < 0) {` comprueba si el pedido excede el stock. | Activa el caso de inventario insuficiente. |
| 376 | Plantilla literal con `Math.abs(restante)` muestra cuántas unidades faltan. | Presenta un mensaje concreto; `Math.abs` convierte el número negativo en su magnitud positiva. |
| 377 | Establece el ancho de barra al 100 %. | En el caso de error, mantiene una barra llena como indicador visual de bloqueo; no representa literalmente un stock negativo. |
| 378 | Coloca el color de la barra en el valor CSS `var(--danger)`. | Resalta que el pedido excede inventario. |
| 379 | Deshabilita el botón procesar. | Impide completar una venta con stock insuficiente. |
| 380 | `} else {` abre la rama cuando el pedido cabe en el stock. | Solo en este caso se calcula el porcentaje disponible. |
| 381 | `(restante / stockMax) * 100` calcula el porcentaje restante. | Convierte las unidades en una proporción visual para el ancho de la barra. |
| 382 | La plantilla literal forma el texto `restante / stockMax unidades`. | Informa unidades reales además de la barra. |
| 383 | Asigna el ancho de la barra en porcentaje. | Representa gráficamente la proporción de inventario restante. |
| 384 | Habilita el botón procesar. | La cantidad es válida respecto del stock. |
| 385 | `if (porcentajeStock <= 25)` comprueba primero el umbral de stock crítico. | Aplica rojo cuando queda una cuarta parte o menos. |
| 386 | Asigna color de peligro a la barra. | Comunica inventario bajo. |
| 387 | `else if (porcentajeStock <= 50)` comprueba el siguiente umbral solo si no se cumplió el anterior. | Distingue nivel medio (más de 25 % y hasta 50 %). |
| 388 | Asigna el color de advertencia. | Señala que el stock se acerca a un nivel bajo. |
| 389 | `else` cubre los porcentajes superiores al 50 %. | Establece el estado normal. |
| 390 | Asigna el color de éxito. | Indica disponibilidad suficiente. |
| 391 | Cierra `else` del stock válido. | — |
| 392 | Cierra `if` de porcentaje. | — |
| 393 | Cierra `else` de stock no negativo. | Termina la decisión del inventario. |
| 394 | Línea vacía. | Separa stock de autorización. |
| 395 | Comentario que anuncia el semáforo de autorización. | Explica la última dependencia visual. |
| 396 | Restablece `className` a `status-badge`. | Elimina clases `warning` o `danger` de una evaluación anterior antes de calcular el estado nuevo. |
| 397 | Comprueba si el pedido supera el inventario. | El caso de stock tiene prioridad sobre el monto. |
| 398 | Agrega la clase `danger`. | Aplica el diseño rojo definido en CSS. |
| 399 | Asigna fragmentos HTML con un indicador rojo y texto de bloqueo a `innerHTML`. | Reemplaza el contenido de la insignia para mostrar el motivo del bloqueo. El contenido está fijo en el código, no proviene de entrada del usuario. |
| 400 | `else if (total >= 500000)` se evalúa solo si no faltó stock y comprueba un total de al menos 500 000. | Define el umbral de monto alto. |
| 401 | Agrega la clase `warning`. | Aplica los colores naranjas definidos en CSS. |
| 402 | Reemplaza el interior por el indicador naranja y el mensaje de supervisión. | Informa que la operación necesita autorización según la regla de negocio simulada. |
| 403 | `else` representa ventas con stock disponible y total inferior al umbral. | Maneja el estado normal. |
| 404 | Reemplaza el contenido por el indicador verde y el mensaje de aprobación inmediata. | Comunica que no se detecta una condición especial. |
| 405 | `}` cierra el bloque de decisión del estado. | Finaliza la actualización de la insignia. |
| 406 | `}` cierra la función `actualizarDependencias`. | Termina la función reutilizable. |

## 6. JavaScript: procesar, restablecer y reaccionar

| Línea(s) | Sintaxis y funcionamiento | Por qué se usa |
|---|---|---|
| 407 | Línea vacía. | Separa la función de los eventos. |
| 408 | Comentario que describe la simulación de demora. | Aclara que el progreso no representa una conexión real con un servidor. |
| 409 | `btnProcesar.addEventListener('click', () => {` registra una función flecha para el evento `click`. `addEventListener` permite reaccionar a eventos sin escribir JavaScript inline en el botón. | Inicia la simulación cuando el usuario presiona Procesar. |
| 410–414 | Pone en `true` `disabled` para los botones y controles del formulario. | Evita que se cambien los datos o se inicien varias simulaciones mientras el progreso está en marcha. |
| 415 | Línea vacía. | Separa bloqueo de feedback visual. |
| 416 | Oculta cualquier aviso de éxito anterior. | Evita mostrarlo durante un nuevo proceso. |
| 417 | Muestra el contenedor de progreso con `display: block`. | Hace visible la simulación. |
| 418 | `let progreso = 0;` declara una variable reasignable con el valor inicial cero. | El porcentaje aumenta en cada intervalo. |
| 419 | Línea vacía. | Separa inicialización y temporizador. |
| 420 | `setInterval(() => { ... }, 120)` ejecuta repetidamente la función flecha, con 120 milisegundos entre ejecuciones aproximadas. Devuelve un identificador guardado en `intervalo`. | Anima la barra en incrementos periódicos. |
| 421 | `progreso += 5` equivale a `progreso = progreso + 5`. | Incrementa cinco puntos porcentuales por ejecución. |
| 422 | Asigna el ancho de relleno a una plantilla literal como `5%`, `10%`, etc. | Actualiza la longitud visual de la barra. |
| 423 | Actualiza el texto del porcentaje usando el mismo valor. | Mantiene una lectura numérica junto a la barra. |
| 424 | Línea vacía. | Separa avance y condición de finalización. |
| 425 | `if (progreso >= 100) {` comprueba que el proceso llegó al máximo. | Inicia la finalización cuando la barra alcanza 100 %. |
| 426 | `clearInterval(intervalo)` cancela el temporizador periódico. | Evita que progreso siga aumentando indefinidamente. |
| 427 | `setTimeout(() => { ... }, 300)` programa una única función para ejecutarse unos 300 ms después. | Deja una pausa breve antes de cambiar al mensaje de finalización. |
| 428 | Oculta el contenedor de progreso. | Retira el indicador al concluir. |
| 429 | Muestra el aviso de éxito. | Informa que la simulación terminó correctamente. |
| 430–434 | Devuelve a `false` `disabled` para el botón y controles. | Permite volver a interactuar con el formulario. El botón procesar queda habilitado aunque el usuario edite, porque la función reactiva no se vuelve a llamar al reactivar; en la ejecución normal los valores ya eran válidos antes de hacer clic. |
| 435 | `}, 300);` cierra el callback de `setTimeout` y establece el retraso. | Completa la llamada de espera corta. |
| 436 | `}` cierra la condición que detecta el 100 %. | — |
| 437 | `}, 120);` cierra el callback de `setInterval` y fija la espera repetida en 120 ms. | Aproximadamente 20 incrementos × 120 ms = 2 400 ms, es decir, unos 2.4 segundos, además de la pausa final. |
| 438 | `});` cierra el callback y la llamada a `addEventListener`. | Finaliza el evento de procesar. |
| 439 | Línea vacía. | Separa los manejadores de eventos. |
| 440 | Comentario que anuncia la acción de restablecer. | Explica el propósito del siguiente listener. |
| 441 | Registra un evento `click` en el botón de restablecer. | Ejecuta el restablecimiento cuando se pulsa el botón. |
| 442 | `selectedIndex = 0` selecciona la primera opción del producto. | Restaura el teclado, primer producto de la lista. |
| 443 | `cantidadInput.value = '1'` restablece la cantidad a uno. | Define el valor inicial esperado. |
| 444 | Selecciona la primera opción de descuento (sin descuento). | Vuelve a la configuración base de precio. |
| 445 | Llama a `actualizarDependencias()`. | Recalcula de inmediato total, ahorro, stock, validación y estado con los valores restaurados. |
| 446 | `});` cierra el listener de restablecer. | — |
| 447 | Línea vacía. | Separa acciones puntuales de eventos reactivos. |
| 448 | Comentario sobre los eventos que recalculan la interfaz. | Documenta las conexiones automáticas. |
| 449 | En el selector de producto, `change` llama a `actualizarDependencias`. | Recalcula cuando se escoge otro producto. |
| 450 | En cantidad, `input` llama a la función durante la escritura o edición. | Da validación y resultados en vivo, sin esperar a perder el foco. |
| 451 | En descuento, `change` llama a la función cuando cambia la opción seleccionada. | Actualiza total y ahorro inmediatamente. |
| 452 | Línea vacía. | Separa listeners e inicialización. |
| 453 | Comentario de inicialización. | Indica que el siguiente llamado prepara el estado inicial. |
| 454 | `actualizarDependencias();` ejecuta la función una vez al cargar el script. | Sin esta llamada, los valores de resumen dependerían solo del texto estático del HTML hasta la primera interacción. |
| 455 | `</script>` cierra el bloque de JavaScript. | Termina el código ejecutable de esta página. |
| 456 | Línea vacía. | Separación visual antes de los cierres del documento. |
| 457 | `</body>` cierra el contenido visible. | Indica al navegador el final del cuerpo. |
| 458 | `</html>` cierra el elemento raíz. | Termina el documento HTML. |

## 7. Recorrido de funcionamiento completo

1. El navegador lee los metadatos y carga los estilos definidos en `<style>`.
2. Construye el formulario y los paneles de resultados del HTML. Los `id` permiten que el JavaScript encuentre cada elemento.
3. El script guarda esas referencias y prepara un formato de moneda para Colombia.
4. Al final, `actualizarDependencias()` lee producto, precio, stock, descuento y cantidad. Si la cantidad no es un entero positivo, muestra el error y detiene el cálculo.
5. Con datos válidos, calcula subtotal, ahorro y total; después calcula stock restante, actualiza la barra y determina el estado de autorización.
6. Cambiar producto o descuento, o escribir la cantidad, vuelve a ejecutar los cálculos.
7. El botón **Procesar Venta** simula una espera de unos 2.4 segundos con una barra animada y luego presenta el aviso de éxito. No guarda una venta ni modifica una base de datos: es una demostración de interfaz.
8. El botón **Restablecer** recupera el primer producto, cantidad uno y descuento cero, y recalcula todos los indicadores.

## 8. Detalles a tener en cuenta al estudiar el código

- El comentario inicial del HTML llama “caja de diálogo” al formulario, pero técnicamente no se usa el elemento `<dialog>`: es un panel de página.
- El valor de stock mostrado no se descuenta de forma permanente. Cada actualización calcula `stockMax - cantidad` desde el inventario inicial guardado en `data-stock`.
- `statusText` se obtiene del DOM pero no se vuelve a usar directamente; las ramas de autorización reemplazan el contenido del padre `statusBadge` con `innerHTML`.
- `input type="text"` permite validar paso a paso con la expresión regular. La validación acepta dígitos positivos sin ceros iniciales, por lo que `01` también se rechaza.
- `style="..."` en algunas etiquetas es CSS en línea: funciona, aunque en proyectos mayores suele trasladarse a reglas CSS con clases para mantener presentación y estructura separadas.
- El feedback de “transacción completada” es una simulación temporal del lado del navegador; no comprueba factura, servidor, pago ni inventario persistente.
