# Tareas — Death Note: El Cuaderno

Versión: 0.1 · Estado: pendientes de aprobación · Fase: Tasks.

Bases aprobadas: [Specification 1.0](specification.md), [Plan 1.0](plan.md), [criterios de aceptación](acceptance-criteria.md) y [contenido](content.md).

El usuario aprobó Plan mediante «Apruebo, pasa a Tasks». Esta autorización permite redactar el desglose. Ninguna de las tareas de implementación o verificación descritas aquí se ha ejecutado.

## 1. Convenciones y límites de fase

| Prefijo | Trabajo | Momento de ejecución |
| --- | --- | --- |
| T | Implementación, integración y documentación de uso | Después de aprobar Tasks e iniciar Implementation. |
| V | Comprobaciones, resultados y aceptación del APK | Después de presentar Implementation y obtener aprobación para Verification. |
| R | Recursos que proporcionará el usuario | Cuando estén disponibles; su recepción no autoriza cambios de fase. |

Estados previstos: pendiente, en curso, completada y bloqueada. Una tarea bloqueada debe indicar la causa concreta y qué necesita para continuar. Al redactar este documento, todas las tareas están pendientes.

Completar una tarea T significa haber realizado sus cambios y preparado su resultado para revisión. No equivale a aprobar los criterios CA asociados: estos se comprobarán y registrarán en las tareas V. La sincronización y compilación necesarias para integrar el código pertenecen a Implementation; la ejecución de pruebas y la aceptación funcional pertenecen a Verification.

Los cambios se limitarán a la especificación y el plan aprobados. Si aparece una decisión que cambie requisitos, se actualizará la documentación y se solicitará aprobación del cambio antes de implementarlo.

Convenciones añadidas por instrucción del usuario: programar e identificar elementos de código en inglés, mostrar la interfaz en español y escribir los commits en inglés. Los comentarios y textos descriptivos pueden estar en español. Antes de programar, preparar los commits iniciales y configurar `git@github.com:GabrielAlcequiez/deathnote_app.git` como remoto. Véase [CONTRIBUTING.md](../CONTRIBUTING.md). Esta preparación de Git fue solicitada expresamente; Tasks sigue pendiente de aprobación para iniciar Implementation.

## 2. Resumen de implementación

La numeración identifica tareas; el orden de trabajo lo determinan las dependencias. Todas son parte del alcance, incluidas las vistas Acerca de y Momentos como destinos diferentes.

| ID | Resultado previsto | Dependencias | Estado |
| --- | --- | --- | --- |
| T01 | Base Android y dependencias integradas | Aprobación de Tasks | Pendiente |
| T02 | Raíz de aplicación y contenedor de dependencias | T01 | Pendiente |
| T03 | Catálogo central de contenido y modelos | T02 | Pendiente |
| T04 | Tema oscuro y componentes de libreta | T02 | Pendiente |
| T05 | Índice, rutas y pila de navegación | T03, T04 | Pendiente |
| T06 | Transición animada de página | T05 | Pendiente |
| T07 | Carga de imágenes locales y placeholders | T03, T04 | Pendiente |
| T08 | Portada con slider y entrada al índice | T05, T07 | Pendiente |
| T09 | Personajes y detalles individuales | T05, T07 | Pendiente |
| T10 | Momentos y detalles de las tres escenas | T05, T07 | Pendiente |
| T11 | Acerca de y Contrátame como vistas propias | T05, T07 | Pendiente |
| T12 | Adaptación de enlaces y estados de video | T03 | Pendiente |
| T13 | Reproductor YouTube integrado en Momentos | T06, T10, T12 | Pendiente |
| T14 | Motor del juego y reglas | T02 | Pendiente |
| T15 | Repositorio de estadísticas persistentes | T02 | Pendiente |
| T16 | Coordinación de partida y estadísticas | T05, T14, T15 | Pendiente |
| T17 | Representación jugable de Ryuk y controles | T04, T16 | Pendiente |
| T18 | Integración de navegación y ciclo de vida | T06, T08, T09, T11, T13, T17 | Pendiente |
| T19 | Guía de recursos y documentación de uso | T03, T07, T13, T17, T18 | Pendiente |
| T20 | APK de revisión y cierre de Implementation | T19 y demás tareas T terminadas | Pendiente |

## 3. Detalle de implementación

### T01. Integrar la base Android

- **Trabajo:** revisar SDK y JVM disponibles, resolver las versiones declaradas, añadir Navigation Compose, Lifecycle, Preferences DataStore y los artefactos Compose necesarios. Mantener un módulo y minSdk 24. Configurar orientación vertical y permisos de internet y estado de red.
- **Áreas:** catálogo TOML, archivos Gradle, propiedades de integración y manifiesto, solo al llegar a Implementation.
- **Terminación:** sincronización y ensamblado de la base disponibles; versiones efectivas y cualquier ajuste de compatibilidad documentados en Plan. Si el entorno impide compilar, registrar el impedimento y no declarar el APK generado.
- **Trazabilidad:** RNF-03, RNF-06, RNF-07, RNF-09; CA-39, CA-40.

### T02. Crear la raíz y el contenedor

- **Trabajo:** conectar MainActivity con la raíz Compose y un contenedor de alcance de aplicación. Definir fábricas de ViewModel y los puntos de construcción del catálogo y repositorio, manteniendo una sola instancia de almacenamiento.
- **Áreas:** `MainActivity.kt`, paquetes `app/` y construcción de dependencias.
- **Terminación:** la raíz sustituye la pantalla de ejemplo y permite conectar navegación y servicios con propietarios y liberación definidos, sin retener referencias de actividades en componentes de aplicación.
- **Trazabilidad:** Plan, secciones 4 y 9; RNF-10; CA-35, CA-40.

### T03. Preparar el catálogo editable

- **Trabajo:** definir modelos e identificadores estables para tres diapositivas, Light, L, Ryuk, las tres escenas elegidas, ficha del anime y perfil. Centralizar los datos en `data/content/AppContent.kt` con rutas y enlaces opcionales.
- **Áreas:** `data/content/` y textos compartidos de interfaz.
- **Terminación:** contenido inicial conforme a `content.md`; datos personales, imágenes y videos pendientes claramente identificados. Cambiar datos del catálogo no requiere modificar lógica de pantalla.
- **Trazabilidad:** RF-01, RF-03, RF-04, RF-06, RF-08, RF-09; CA-01, CA-09 a CA-12, CA-19, CA-21 a CA-23.

### T04. Construir la identidad de libreta

- **Trabajo:** definir paleta carbón, marfil y rojo, tipografía, espaciados, encabezados y superficies de página. Dibujar lomo, márgenes y decoración local. Crear controles reutilizables con etiquetas accesibles e insets.
- **Áreas:** `ui/theme/`, `ui/components/` y recursos locales.
- **Terminación:** componentes listos para títulos, texto, tarjetas y acciones, con controles habituales de al menos 48 dp y contenido desplazable; tema oscuro fijo y sin sonidos.
- **Trazabilidad:** RNF-01 a RNF-05, RNF-08; CA-37, CA-39.

### T05. Implementar rutas e índice

- **Trabajo:** crear destinos para Portada, Índice, Personajes, detalle de personaje, Momentos, detalle de momento, Acerca de, Juega Conmigo y Contrátame. Construir el índice con seis entradas numeradas.
- **Áreas:** `navigation/`, raíz de aplicación y pantalla Índice.
- **Terminación:** reglas de Atrás y acceso al índice codificadas; regreso a Portada reutiliza su destino existente; navegación única por acción e identificadores desconocidos con regreso seguro. Momentos y Acerca de tienen rutas propias.
- **Trazabilidad:** RF-02, Specification sección 3; CA-05 a CA-08, CA-20.

### T06. Animar el cambio de página

- **Trabajo:** crear `BookPage` con giro desde el borde izquierdo, perspectiva, sombra y transición inversa. Coordinar el componente con la navegación y limitar nuevas acciones mientras termina la transición.
- **Áreas:** componentes de libreta y host de navegación.
- **Terminación:** animación de página aplicada al abrir y regresar de secciones, con duración inicial de 450 ms; exposición del estado de transición para coordinar el reproductor.
- **Trazabilidad:** RF-02, RNF-05; CA-05 a CA-08, CA-37.

### T07. Resolver imágenes y placeholders

- **Trabajo:** cargar rutas de `assets/images/` fuera del hilo principal, ajustar decodificación al tamaño y usar caché limitada. Añadir placeholders para ruta vacía, archivo ausente o imagen inválida.
- **Áreas:** componentes de imagen, cargador local y directorio de recursos de contenido.
- **Terminación:** un mismo componente sirve para portada, tarjetas, detalles y perfil; cada placeholder identifica el recurso pendiente y conserva el espacio sin un indicador de carga permanente.
- **Trazabilidad:** RF-03, RF-04, RF-08, RF-09; CA-09 a CA-11, CA-18, CA-21, CA-23, CA-38.

### T08. Completar la Portada

- **Trabajo:** construir el slider de tres diapositivas, indicadores, frases y botón «Abrir cuaderno». Configurar avance cada cinco segundos, ciclo al inicio e interacción manual con reinicio del contador.
- **Áreas:** pantalla Portada y su estado local.
- **Terminación:** portada conectada al índice; temporizador activo únicamente mientras está visible, en primer plano y sin interacción manual en curso.
- **Trazabilidad:** RF-01; CA-01 a CA-05.

### T09. Completar Personajes

- **Trabajo:** mostrar Light, L y Ryuk en un listado seleccionable; construir detalle con foto o placeholder, nombre, rol y descripción obtenidos por identificador.
- **Áreas:** pantallas de personajes y detalles.
- **Terminación:** tres fichas diferenciadas y navegación a listado o índice conforme a las rutas aprobadas; contenido local disponible offline.
- **Trazabilidad:** RF-03; CA-08, CA-09, CA-18, CA-38.

### T10. Completar Momentos

- **Trabajo:** construir las tarjetas de la papita, el helicóptero y la promesa de Ryuk; añadir detalles con imagen, explicación y espacio para conectar el reproductor.
- **Áreas:** pantallas de Momentos y detalle de momento.
- **Terminación:** tres escenas con contenido propio, detalle por identificador y regreso correcto; la pantalla funciona con video pendiente y mantiene independencia de Acerca de.
- **Trazabilidad:** RF-04, RF-05; CA-08, CA-10 a CA-12, CA-18, CA-20, CA-38.

### T11. Completar Acerca de y Contrátame

- **Trabajo:** crear una pantalla Acerca de con sinopsis, una temporada, 37 episodios, autores y estudio; crear otra pantalla Contrátame con foto y campos personales pendientes. Conectar ambas a sus entradas propias del índice.
- **Áreas:** dos pantallas independientes y catálogo de contenido.
- **Terminación:** Acerca de no comparte destino con Momentos; Contrátame conserva el estilo de libreta y no activa acciones hacia datos ficticios. Ambas vistas funcionan sin conexión; los datos reales permiten selección de texto según Plan.
- **Trazabilidad:** RF-06, RF-08; CA-19 a CA-21, CA-38.

### T12. Adaptar enlaces y estados de video

- **Trabajo:** extraer el identificador de los formatos de YouTube previstos en Plan; detectar enlace vacío o inválido. Definir estados de configuración pendiente, conexión, carga, listo, reproducción, pausa y error con mensajes en español.
- **Áreas:** adaptador de enlaces y modelos de `ui/player/`.
- **Terminación:** un enlace pendiente no inicia carga; un enlace inválido no se inyecta en el HTML; los errores permiten conservar el texto y ofrecer el reintento correspondiente.
- **Trazabilidad:** RF-05; CA-12 a CA-16.

### T13. Integrar el reproductor

- **Trabajo:** alojar un WebView en Compose con plantilla IFrame local, identidad de aplicación y origen conforme al plan. Conectar controles, estado de red, errores y tiempo máximo de carga. Activar el reproductor al terminar la transición de entrada y liberarlo al retirar el detalle.
- **Áreas:** `ui/player/`, `assets/player/` y detalle de momento.
- **Terminación:** los enlaces configurados usan el reproductor dentro de la app, sin autoplay ni redirección como alternativa; controles visibles, tamaño mínimo respetado y pausa al perder primer plano. El caso sin enlace continúa funcionando con placeholder.
- **Trazabilidad:** RF-05, RNF-06, RNF-08; CA-12 a CA-17, CA-38, CA-39.
- **Dependencia de contenido:** R02 es necesaria para aceptar los tres videos reales; su ausencia no impide terminar la integración y los estados pendientes.

### T14. Construir el motor de Ryuk y las manzanas

- **Trabajo:** modelar partida, Ryuk, objetos y eventos en Kotlin independiente de Android. Resolver límites horizontales, caída, colisiones, eliminación de objetos, puntos, vidas, invulnerabilidad y progresión de dificultad.
- **Áreas:** `game/`.
- **Terminación:** reglas RG-01 a RG-03 representadas; paso temporal controlado y azar sustituible para comprobaciones deterministas posteriores. Documentar la tabla inicial de velocidades y apariciones sin alterar tres vidas, diez puntos, un segundo de protección o los cinco niveles cada veinte segundos.
- **Trazabilidad:** RF-07, RG-01 a RG-03; CA-24 a CA-30, CA-36.

### T15. Implementar estadísticas persistentes

- **Trabajo:** crear el archivo único Preferences DataStore y `GameStatsRepository`; guardar récord, partidas y manzanas con eventos serializados y actualizaciones transaccionales. Usar alcance de aplicación para escrituras que continúen al retirar el destino.
- **Áreas:** `data/stats/` y contenedor de aplicación.
- **Terminación:** carga observable con estados de espera y error; máximo del récord y contadores preservados; operaciones pendientes con reintento sin reinicializar datos existentes. No se almacena la partida activa.
- **Trazabilidad:** RG-05, RNF-10; CA-26, CA-33 a CA-36.

### T16. Coordinar partida, acciones y estadísticas

- **Trabajo:** crear `GameViewModel` ligado al destino; conectar motor, repositorio y estados Preparado, Jugando, Pausado y Terminado. Gestionar Empezar, Reanudar, Reintentar y Abandonar sin duplicar inicios ni eventos de recogida.
- **Áreas:** `ui/game/`, fábricas y conexión con navegación.
- **Terminación:** cada partida nueva se registra una vez; las recogidas se remiten una vez al repositorio; salir descarta la partida conservando estadísticas. La partida no se restaura desde disco ni desde estado guardado del proceso.
- **Trazabilidad:** RF-07, RG-04, RG-05; CA-24, CA-26, CA-28, CA-30 a CA-36.

### T17. Crear el juego visible y sus controles

- **Trabajo:** dibujar Ryuk, manzanas y obstáculos con recursos locales; conectar arrastre y bucle por cuadros con tiempo monotónico. Construir instrucciones, marcador, pausa, resultado, récord y estadísticas.
- **Áreas:** pantalla Juega Conmigo, Canvas y componentes del juego.
- **Terminación:** experiencia jugable vertical y offline con controles fuera del área de colisión, protección visible y objetos limitados. Pausar congela la simulación; reanudar reinicia la referencia temporal. Sin música ni efectos.
- **Trazabilidad:** RF-07, RG-01 a RG-05, RNF-08; CA-24 a CA-39 en los comportamientos del juego.

### T18. Integrar navegación y ciclo de vida

- **Trabajo:** conectar pausa del juego al perder primer plano y reanudación explícita al volver; confirmar en el diseño de las acciones que salir abandona. Coordinar suspensión del slider, pausa y liberación de video, transiciones y Atrás. Completar integración de todas las vistas con insets y desplazamiento.
- **Áreas:** navegación, observación del ciclo de vida y pantallas integradas.
- **Terminación:** cada componente tiene activación y liberación definidas; no existen bucles de juego o slider activos fuera de su vista ni audio de video detrás de otra sección. Los estados pendientes conservan la navegación funcional.
- **Trazabilidad:** RF-01, RF-02, RF-05, RG-04, RNF-03, RNF-05; CA-04 a CA-08, CA-17, CA-30 a CA-32, CA-35, CA-37 a CA-39.

### T19. Documentar sustitución y uso

- **Trabajo:** escribir `docs/resource-guide.md` con rutas efectivas, nombres, formatos admitidos y ejemplos de fotos, enlaces y perfil; actualizar README con generación e instalación. Mantener inventario real de recursos y ajustes técnicos en los documentos existentes.
- **Áreas:** Markdown del proyecto.
- **Terminación:** las instrucciones corresponden a archivos existentes en la implementación; incluyen volver a generar el APK tras cambiar contenido y explican qué recursos siguen pendientes. No presentan placeholders como fotografías o videos finales aceptados.
- **Trazabilidad:** RF-09, RNF-11, Specification sección 8; CA-22, CA-41, CA-42.

### T20. Preparar el APK y presentar Implementation

- **Trabajo:** integrar el resultado final, ensamblar el APK de depuración y registrar su ruta, versiones efectivas e incidencias de integración. Actualizar las tareas según su estado real y presentar el resultado al usuario antes de solicitar Verification.
- **Áreas:** artefacto de compilación y documentación de estado.
- **Terminación:** APK de revisión disponible en la ruta prevista. Si no puede generarse, registrar la causa y mantener T20 bloqueada hasta resolverla. No marcar CA-40 como cumplido hasta instalar y abrir el artefacto en Verification. Solicitar aprobación de cambio de fase con el resultado revisable.
- **Trazabilidad:** RNF-09, RNF-11, Specification secciones 8 y 9; CA-40 a CA-42.

## 4. Orden de ejecución recomendado

| Tramo | Tareas | Propósito |
| --- | --- | --- |
| Base | T01 → T02 → T03 y T04 → T05 → T06 y T07 | Disponer de integración, contenido, navegación, estilo y recursos compartidos. |
| Reproductor temprano | T10 y T12 → T13 | Resolver la integración de YouTube antes de consumir el margen final. |
| Juego | T14 y T15 → T16 → T17 | Completar reglas, persistencia y experiencia jugable. |
| Otras vistas | T08, T09 y T11 | Completar portada, personajes, Acerca de y Contrátame. |
| Integración y presentación | T18 → T19 → T20 | Unificar comportamiento, documentar recursos y presentar el APK. |

Las conjunciones indican trabajo sin dependencia mutua, no una obligación de usar agentes ni de ejecutar cambios simultáneamente. La progresión seguirá las dependencias de la tabla principal y las restricciones del plazo aprobado.

## 5. Verificación prevista, con aprobación posterior

Estas tareas quedan definidas para la fase Verification. Su estado inicial es pendiente; no se crearán pruebas ni se ejecutarán comprobaciones funcionales durante Tasks.

| ID | Trabajo y resultado esperado | Dependencias al ejecutarse | Estado |
| --- | --- | --- | --- |
| V01 | Crear y ejecutar pruebas deterministas del motor: recogida única, objetos perdidos, límites, daño, protección, derrota, niveles y pausa sin avance temporal. Registrar resultados reales. | Aprobación de Verification, T14, T16, T17 | Pendiente |
| V02 | Comprobar transacciones y contadores del repositorio, doble inicio, actualización del máximo y persistencia tras abandonar y reabrir. Añadir pruebas automatizadas de reglas de actualización donde aporten cobertura; complementar con flujo real en Android. | Aprobación de Verification, T15 a T18 | Pendiente |
| V03 | Recorrer portada, índice, las seis vistas y detalles; comprobar slider, transiciones, Atrás, pulsaciones rápidas y el juego en pantalla. Verificar pausa al cambiar de app o bloquear y reanudación explícita. | Aprobación de Verification, T08 a T11, T17, T18 | Pendiente |
| V04 | Comprobar videos pendientes y errores, enlace inválido, conexión y reintento, ausencia de autoplay y pausa al salir; reproducir cada uno de los tres enlaces reales dentro de la app. | Aprobación de Verification, T13, T18; R02 para los tres videos reales | Pendiente |
| V05 | Comprobar recursos locales, ruta ausente o inválida, catálogo editable y guía; recorrer contenido y juego offline. Registrar por separado los placeholders y los recursos finales. | Aprobación de Verification, T07 a T11, T19; R01 para fotos finales, R03 para perfil final | Pendiente |
| V06 | Revisar legibilidad, tema, insets, desplazamiento y objetivos táctiles en los tamaños disponibles; confirmar orientación y ausencia de sonidos o permisos ajenos al alcance. | Aprobación de Verification, T18, T20 | Pendiente |
| V07 | Instalar y abrir el APK final, registrar Android y entorno disponibles, consolidar CA-01 a CA-42 en `docs/verification.md`, corregir fallos detectados dentro del alcance y repetir solo lo afectado. Presentar ruta del APK, evidencia y pendientes reales. | Aprobación de Verification, T20 y resultados de V01 a V06 | Pendiente |

V07 puede consolidar un informe con criterios pendientes por contenido o entorno; en ese caso, no se declarará la aceptación completa. Si V04 o V05 quedan parcialmente pendientes, se registrarán los resultados ya comprobados y la causa exacta de lo pendiente.

La compatibilidad mínima API 24 y una versión reciente se comprobarán si existen dispositivos o emuladores apropiados. El informe identificará las versiones realmente utilizadas; no afirmará cobertura de versiones no ejecutadas.

## 6. Trazabilidad de aceptación

La siguiente tabla enlaza todos los criterios aprobados con las tareas que producirán el comportamiento y las que comprobarán su resultado.

| Criterios | Implementación o documentación | Verificación |
| --- | --- | --- |
| CA-01 | T03, T07, T08 | V03 |
| CA-02, CA-03, CA-04 | T08, T18 | V03 |
| CA-05, CA-06, CA-07, CA-08 | T05, T06, T08 a T11, T18 | V03 |
| CA-09 | T03, T07, T09 | V03, V05 |
| CA-10, CA-11 | T03, T07, T10 | V03, V05 |
| CA-12 | T03, T10, T12, T13 | V04 |
| CA-13, CA-14, CA-15, CA-16 | T12, T13 | V04; CA-13 requiere R02 |
| CA-17 | T13, T18 | V04 |
| CA-18 | T07, T09, T10 | V05; fotos finales requieren R01 |
| CA-19, CA-20 | T03, T05, T11 | V03 |
| CA-21 | T03, T07, T11 | V03, V05 |
| CA-22 | T03, T07, T12, T19 | V05 |
| CA-23 | T03, T07, T12, T18 | V04, V05 |
| CA-24, CA-25 | T14, T16, T17 | V01, V03 |
| CA-26 | T14 a T17 | V01, V02, V03 |
| CA-27, CA-28, CA-29, CA-30 | T14, T16 a T18 | V01, V03 |
| CA-31, CA-32 | T05, T16 a T18 | V02, V03 |
| CA-33, CA-34, CA-35, CA-36 | T14 a T18 | V01, V02, V03 |
| CA-37 | T04, T06 a T11, T13, T17, T18 | V06 |
| CA-38 | T03, T07 a T11, T13, T15, T17, T18 | V03, V04, V05 |
| CA-39 | T01, T04, T13, T17, T18 | V06 |
| CA-40 | T01, T20 | V07 |
| CA-41 | T19, T20 | V05, V07 |
| CA-42 | Actualización del estado y aprobaciones de cada fase; T19, T20 | V07 |

## 7. Aportes pendientes del usuario

| ID | Aporte | Uso | Estado |
| --- | --- | --- | --- |
| R01 | Diez imágenes: tres de portada, tres personajes, tres momentos y una foto personal | Sustituir placeholders de T07 a T11; aceptar fotos finales en V05 | Pendiente |
| R02 | Tres enlaces de YouTube, uno por escena elegida, que permitan inserción | Configurar T13 y aceptar reproducción real en V04 | Pendiente |
| R03 | Nombre, presentación, correo, teléfono y enlaces de redes o portafolio | Sustituir campos de Contrátame; registrar perfil final en V05 | Pendiente |

La ausencia de R01 a R03 no impide construir las pantallas y sus placeholders, ni terminar el juego. El usuario puede sustituir estos datos desde el proyecto siguiendo la guía; no se añadirán pantallas de edición. Cuando se incorporen, se registrará qué se ha recibido y qué sigue pendiente, sin reemplazar el estado de verificación por una suposición.

## 8. Condiciones de terminación por fase

| Fase | Resultado revisable | Aprobación siguiente |
| --- | --- | --- |
| Tasks, actual | Tareas T, V y R definidas, dependencias explícitas y cobertura de CA-01 a CA-42 | El usuario debe aprobar Tasks antes de escribir código. |
| Implementation, futura | T01 a T20 realizadas y estado real documentado, APK disponible y guía de recursos; aportes R aún pendientes identificados | Presentar el resultado y solicitar aprobación antes de iniciar Verification. |
| Verification, futura | Resultados V01 a V07 documentados, criterios cumplidos o pendientes con evidencia, APK instalado en el entorno comprobado | Informar cumplimiento y limitaciones; nunca equiparar placeholders o comprobaciones no realizadas con aceptación completa. |

En Tasks se han modificado únicamente documentos Markdown. No se ha iniciado Implementation ni Verification.
