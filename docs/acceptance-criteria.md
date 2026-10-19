# Criterios de aceptación

Versión: 1.0 · Estado: aprobados como parte de Specification; ejecución pendiente de Verification.

Estos escenarios definen resultados esperados. **No se han ejecutado y no representan funcionalidades implementadas.** El diseño y ejecución de verificaciones pertenecen a las fases correspondientes, después de su aprobación.

## Navegación y portada

| ID | Requisito | Escenario y resultado esperado |
| --- | --- | --- |
| CA-01 | RF-01 | Al iniciar la app se muestra la portada con el nombre aprobado, tres diapositivas y «Abrir cuaderno». |
| CA-02 | RF-01 | Con la portada visible, cada cinco segundos cambia la diapositiva; después de la tercera vuelve a la primera. |
| CA-03 | RF-01 | Deslizar cambia la diapositiva y su indicador; el avance automático espera cinco segundos desde la interacción. |
| CA-04 | RF-01 | Al ocultar la portada o pasar a segundo plano se suspende su avance automático. |
| CA-05 | RF-02 | «Abrir cuaderno» lleva a un índice con las seis entradas y una transición visual de libreta. |
| CA-06 | RF-02 | Cada entrada abre su sección con animación de página; Momentos y Acerca de tienen destinos diferentes. |
| CA-07 | RF-02 | Pulsaciones rápidas no duplican pantallas ni rompen la navegación; desde cada sección se puede volver al índice. |
| CA-08 | Sección 3 | Atrás desde un detalle lleva a su listado; desde una sección al índice; desde el índice a la portada; desde la portada permite salir. |

## Personajes, momentos y videos

| ID | Requisito | Escenario y resultado esperado |
| --- | --- | --- |
| CA-09 | RF-03 | El listado contiene Light Yagami, L y Ryuk; cada selección muestra el nombre, rol, descripción y foto o placeholder correctos. |
| CA-10 | RF-04 | Momentos muestra las tres escenas elegidas, con títulos e imágenes o placeholders diferenciados. |
| CA-11 | RF-04 | Seleccionar cada momento abre su propio detalle con descripción y espacio de video. |
| CA-12 | RF-05 | Sin enlace configurado aparece «Video pendiente de configurar» y se puede leer y abandonar el detalle normalmente. |
| CA-13 | RF-05 | Con internet y un enlace válido que permita inserción, el usuario reproduce y pausa el video dentro de la app; la navegación normal no abre otra aplicación. Comprobar los tres momentos por separado. |
| CA-14 | RF-05 | Al abrir el detalle de un momento no empieza a reproducirse el video automáticamente. |
| CA-15 | RF-05 | Sin internet se informa de la situación; al recuperarlo y reintentar, un enlace reproducible puede cargar dentro del detalle. |
| CA-16 | RF-05 | Con un enlace inválido, privado, eliminado o bloqueado para inserción se muestra un estado de error y no se redirige fuera de la app. |
| CA-17 | RF-05 | Abandonar el detalle o pasar a segundo plano interrumpe el video; no queda audio de ese reproductor detrás de otras vistas. |
| CA-18 | RF-03, RF-04, RF-09 | Tras sustituir los recursos desde el proyecto, las fotos locales de personajes y momentos se muestran también sin internet. |

## Acerca de, contacto y contenido

| ID | Requisito | Escenario y resultado esperado |
| --- | --- | --- |
| CA-19 | RF-06 | Acerca de presenta sinopsis, cantidad de temporadas, 37 episodios, autores con sus funciones y estudio del anime original. |
| CA-20 | RF-06 | Acerca de funciona sin conexión y no se presenta como parte del detalle o listado de Momentos. |
| CA-21 | RF-08 | Contrátame muestra foto y campos personales pendientes, sin datos reales inventados ni acciones hacia contactos ficticios. |
| CA-22 | RF-09 | La guía final identifica archivos y campos exactos para reemplazar fotos, enlaces y contacto; esos cambios no requieren alterar la lógica de las pantallas. |
| CA-23 | RF-09 | Un recurso opcional ausente conserva un placeholder legible y no impide acceder a las demás vistas. |

## Ryuk y las manzanas

| ID | Requisito | Escenario y resultado esperado |
| --- | --- | --- |
| CA-24 | RF-07, RG-01 | El juego presenta instrucciones y, al empezar, muestra tres vidas y cero puntos. Funciona sin conexión. |
| CA-25 | RG-02 | Arrastrar el dedo mueve a Ryuk horizontalmente sin salir del escenario. |
| CA-26 | RG-01 | Recoger una manzana suma diez puntos y una manzana histórica, una sola vez; dejarla caer no penaliza. |
| CA-27 | RG-02 | Una colisión resta una vida; durante el siguiente segundo no se acumula más daño. Tras la protección, otra colisión válida resta una vida. |
| CA-28 | RG-02 | Con cero vidas termina el movimiento y aparece el resultado con récord y botón de reintento. |
| CA-29 | RG-03 | Cada veinte segundos activos aumenta la dificultad hasta el quinto nivel, con mayor velocidad y frecuencia; el tiempo pausado no cuenta. |
| CA-30 | RG-04 | Pausar congela posición, puntos, vidas, objetos y dificultad; Reanudar continúa desde ese estado. |
| CA-31 | RG-04 | Cambiar de app o bloquear el teléfono pausa el juego. Al volver no avanza hasta pulsar Reanudar, mientras la partida permanezca en memoria. |
| CA-32 | RG-04 | Salir del juego al índice abandona la partida y conserva estadísticas; volver al juego permite empezar una nueva. |
| CA-33 | RG-05 | Una partida se cuenta una vez al empezar; abrir la sección, pausar y reanudar no aumentan el contador. |
| CA-34 | RG-05 | El récord refleja el máximo alcanzado, incluso al abandonar una partida; un resultado inferior no lo reduce. |
| CA-35 | RG-05 | Cerrar y reabrir la app conserva récord, partidas y manzanas ya registradas; no ofrece recuperar la partida anterior. |
| CA-36 | RG-05 | Reintentar conserva estadísticas, aumenta en una las partidas y reinicia puntos, vidas y dificultad. |

## Presentación y entrega

| ID | Requisito | Escenario y resultado esperado |
| --- | --- | --- |
| CA-37 | RNF-01 a RNF-05 | Las vistas mantienen la libreta oscura, textos legibles, controles accesibles y contenido desplazable cuando sea necesario, sin solaparse con barras del sistema. |
| CA-38 | RNF-06 | En modo sin conexión se puede recorrer portada, índice, personajes, momentos, acerca de, contacto y jugar; solo los videos requieren conexión. |
| CA-39 | RNF-07, RNF-08 | La experiencia no pide cuenta ni permisos ajenos al alcance; navegación y juego no generan música ni efectos. |
| CA-40 | RNF-09 | El APK se instala y abre en un dispositivo o emulador Android compatible; se registra la versión de Android utilizada y el resultado real. |
| CA-41 | Sección 8 | Antes de declarar la entrega completa, se identifican fotos, datos o videos aún pendientes y se separan de los criterios efectivamente comprobados. |
| CA-42 | Sección 9 | Cada fase se inicia únicamente después de aprobar la anterior; cambios de alcance quedan reflejados en la documentación. |

## Condición para la aceptación final

La aceptación técnica del comportamiento de placeholders puede realizarse con recursos pendientes. La aceptación de las fotografías y de los videos exigidos por la asignación requiere sustituirlos y comprobarlos realmente. Si siguen pendientes, los criterios correspondientes se registrarán como pendientes o bloqueados por contenido, nunca como cumplidos.
