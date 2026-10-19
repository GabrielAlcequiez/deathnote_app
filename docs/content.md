# Contenido y placeholders

Versión: 1.0 · Estado: contenido base aprobado junto con Specification; recursos del usuario pendientes.

Este documento define el contenido inicial y las claves editoriales para identificar recursos. **Las claves no son rutas ni archivos existentes.** Las rutas reales y las instrucciones de sustitución se documentarán durante Implementation.

Los textos son propuestas originales para la aplicación. Se permiten spoilers de toda la serie. Las frases de la portada no se presentan como citas de los personajes.

## 1. Portada

| Clave de imagen | Frase propuesta | Placeholder visible |
| --- | --- | --- |
| portada_01 | Un nombre. Una decisión. Un destino. | Imagen de portada 1 pendiente. |
| portada_02 | Cada página esconde una nueva sospecha. | Imagen de portada 2 pendiente. |
| portada_03 | Abre el cuaderno y sigue las pistas. | Imagen de portada 3 pendiente. |

Tres diapositivas con avance automático cada cinco segundos y navegación manual. Acción principal: «Abrir cuaderno».

## 2. Personajes

### Light Yagami

- Clave: `personaje_light`.
- Foto: `foto_light`, pendiente de archivo local.
- Rol: protagonista y portador de la Death Note.
- Descripción propuesta: «Un estudiante brillante encuentra un cuaderno capaz de matar a quien tenga su nombre escrito en él. Bajo la identidad de Kira, impone su idea de justicia y se enfrenta a quienes intentan descubrirlo. Su inteligencia y su ambición alimentan el conflicto central de la historia».

### L

- Clave: `personaje_l`.
- Foto: `foto_l`, pendiente de archivo local.
- Rol: detective que investiga a Kira.
- Descripción propuesta: «Reservado y poco convencional, L convierte la investigación de Kira en un duelo de observación y estrategia. Sus deducciones lo acercan a Light, mientras ambos intentan descubrir cuánto sabe su adversario».

### Ryuk

- Clave: `personaje_ryuk`.
- Foto: `foto_ryuk`, pendiente de archivo local.
- Rol: shinigami vinculado al cuaderno que encuentra Light.
- Descripción propuesta: «Ryuk deja caer su Death Note en el mundo humano y observa lo que ocurre cuando Light la encuentra. Su fascinación por las decisiones humanas y su afición a las manzanas inspiran el juego de esta aplicación».

## 3. Momentos

Los siguientes textos describen las escenas elegidas por el usuario. No se incluirán números de episodio ni marcas de tiempo sin comprobarlos. Cada entrada pertenece a Momentos y tendrá su propio detalle.

| Clave | Título propuesto | Imagen | Video |
| --- | --- | --- | --- |
| momento_papita | La papita y el plan de Kira | `foto_momento_papita`, pendiente. | `youtube_momento_papita`, sin configurar. |
| momento_helicoptero | El regreso de los recuerdos | `foto_momento_helicoptero`, pendiente. | `youtube_momento_helicoptero`, sin configurar. |
| momento_final | La promesa de Ryuk | `foto_momento_final`, pendiente. | `youtube_momento_final`, sin configurar. |

### La papita y el plan de Kira

Light combina una aparente rutina de estudio con su actividad como Kira mientras está bajo vigilancia. La escena de la bolsa de papitas convierte un gesto cotidiano en parte de su estrategia para mantener su identidad oculta.

### El regreso de los recuerdos

Durante la operación contra Higuchi, Light toca la Death Note en el helicóptero y recupera los recuerdos que había perdido. La escena revela una pieza decisiva de su estrategia y cambia el rumbo de la investigación.

### La promesa de Ryuk

En el desenlace, Ryuk recuerda a Light que su relación tenía un final anunciado: él sería quien escribiría su nombre. El momento cierra la historia de Light y el cuaderno.

### Reglas para videos pendientes

- Inicialmente no habrá enlaces inventados ni videos ajenos utilizados como si fueran estas escenas.
- El usuario proporcionará un enlace de YouTube por momento.
- Los enlaces deberán permitir reproducción integrada. Según la [documentación oficial de YouTube](https://developers.google.com/youtube/iframe_api_reference#onError), un propietario puede impedir la inserción y un video puede dejar de estar disponible.
- La validación de los tres videos reales queda pendiente hasta contar con esos enlaces; el manejo del placeholder sí es un comportamiento verificable por separado.

## 4. Acerca de

### Sinopsis propuesta

Un estudiante encuentra un cuaderno con el poder de decidir la muerte de quienes aparecen en sus páginas. Su intento de transformar el mundo desencadena una persecución en la que la inteligencia, el engaño y los límites de la justicia ocupan el centro del conflicto.

### Ficha propuesta

| Campo | Contenido |
| --- | --- |
| Obra | Death Note, anime original. |
| Temporadas | 1 serie original completa; algunas plataformas pueden dividir su catálogo en partes. |
| Episodios | 37. |
| Obra de origen | Manga Death Note. |
| Guion del manga | Tsugumi Ohba. |
| Dibujo del manga | Takeshi Obata. |
| Estudio de animación | Madhouse. |

El número de temporadas se presentará en la interfaz como **«1 temporada · 37 episodios»**, siguiendo la convención de la serie original completa. No se contabilizan los especiales Relight como temporadas adicionales. Esta convención evita confundir las divisiones de catálogo de un distribuidor con series diferentes.

Fuentes primarias consultadas:

- [Ficha oficial de Nippon TV](https://www.ntv.co.jp/english/pc/2011/03/death-note-1.html): 37 episodios, producción Madhouse y autoría original; identifica los especiales por separado.
- [Sitio oficial de Death Note en VIZ](https://www.viz.com/death-note): obra, autores y edición identificada como Season 1. La presentación de una temporada es la convención editorial adoptada para esta aplicación.
- [Ficha editorial del manga en VIZ](https://www.viz.com/manga-books/manga/death-note/product/1768): distingue historia de Tsugumi Ohba y arte de Takeshi Obata.

## 5. Contrátame

| Clave | Valor inicial visible | Recurso que aportará el usuario |
| --- | --- | --- |
| perfil_foto | Foto de perfil pendiente. | Archivo de fotografía local. |
| perfil_nombre | Tu nombre aquí. | Nombre que se mostrará en la app. |
| perfil_descripcion | Tu presentación profesional aquí. | Descripción breve. |
| perfil_correo | Correo pendiente. | Correo de contacto. |
| perfil_telefono | Teléfono pendiente. | Número de contacto. |
| perfil_redes | Redes o portafolio pendientes. | Enlaces y sus etiquetas. |

Los placeholders no actúan como direcciones o teléfonos reales. No se requiere enviar datos personales durante Specification para aprobar el comportamiento de esta pantalla.

## 6. Recursos del juego

Ryuk, las manzanas y los obstáculos deben tener representaciones incluidas en el APK y permitir jugar desde la primera versión implementada. Las fotografías pendientes de Personajes o Momentos no bloquearán el juego. El plan aprobado prevé Compose Canvas y representaciones vectoriales locales, con una silueta reconocible de Ryuk, manzanas rojas y obstáculos diferenciados.

## 7. Inventario pendiente del usuario

| Tipo | Cantidad inicial | Estado |
| --- | --- | --- |
| Imágenes de portada | 3 | Pendientes. |
| Fotografías de personajes | 3 | Pendientes. |
| Fotografías de momentos | 3 | Pendientes. |
| Enlaces de YouTube de momentos | 3 | Pendientes y sin verificar reproducción integrada. |
| Fotografía personal | 1 | Pendiente. |
| Datos personales y enlaces | Campos de la sección 5 | Pendientes. |

Las imágenes se incorporarán como archivos locales. Para fotos inicialmente disponibles mediante enlaces, el usuario podrá aportar su archivo correspondiente al proyecto. Los enlaces de videos se configurarán como datos de cada momento.

La organización definitiva de archivos, formatos admitidos e instrucciones para generar el APK se documentará en las fases posteriores autorizadas.
