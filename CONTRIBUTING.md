# Convenciones del proyecto

Estas convenciones fueron indicadas expresamente por el usuario y se aplican a los cambios posteriores del proyecto.

## Idiomas

| Elemento | Convención |
| --- | --- |
| Clases, interfaces, funciones, propiedades y variables | Inglés. |
| Paquetes, archivos de código, rutas internas e identificadores de recursos nuevos | Inglés. |
| Pruebas y sus identificadores cuando se autorice Verification | Inglés. |
| Mensajes de commit | Inglés. |
| Textos visibles en pantallas, botones, errores, estados vacíos e instrucciones del juego | Español. |
| Etiquetas de accesibilidad destinadas al usuario | Español. |
| Comentarios, KDoc y explicaciones descriptivas del código | Pueden estar en español. |
| Documentos Markdown y comunicación del proyecto | Pueden estar en español. |

Los nombres propios de Death Note se conservan. Las claves editoriales que aparecen en el inventario de contenido identifican placeholders; los identificadores de código que se creen para representarlos serán en inglés.

Ejemplos de nombres previstos: `CharacterDetailScreen`, `GameStatsRepository`, `appleCount` y `MomentDetailScreen`. Sus títulos visibles pueden ser «Personajes», «Juega Conmigo» y «Momentos».

## Commits

Usar mensajes breves en inglés que expliquen el cambio, agrupando trabajo relacionado en cada commit. Se adopta el formato `type: description`, con tipos como `chore`, `docs`, `feat` y `fix`.

Ejemplos:

- `chore: initialize Kotlin Android project`
- `docs: add specification plan tasks and project conventions`
- `feat: add notebook navigation and page transitions`
- `fix: pause game when app loses foreground`

Los commits iniciales separarán la base Android existente de la documentación SDD y las convenciones. El repositorio usará la rama inicial `main` y el remoto `origin` con la dirección `git@github.com:GabrielAlcequiez/deathnote_app.git`.

## Archivos locales

Excluir del historial cachés, resultados de compilación, configuración local de Android Studio, `local.properties`, almacenes de claves y directorios locales de herramientas o credenciales. Mantener el wrapper de Gradle, sus archivos de configuración y el código fuente necesarios para abrir el proyecto.

## Fases y aprobación

Specification → Plan → Tasks → Implementation → Verification.

Cada cambio de fase requiere aprobación expresa del usuario. Preparar el repositorio y sus commits iniciales es una acción autorizada por separado; no supone aprobar Tasks ni iniciar la programación de las funcionalidades. El estado vigente se mantiene en [README.md](README.md).
