## <a name="microsoft-open-source-code-of-conduct"></a>Código de conducta de código fuente de Microsoft Open

Este proyecto se ha adoptado el [Microsoft código de conducta de código abierto](https://opensource.microsoft.com/codeofconduct/).
Para obtener más información, consulte el [código de conducta preguntas más frecuentes sobre](https://opensource.microsoft.com/codeofconduct/faq/) o póngase en contacto con [ opencode@microsoft.com ](mailto:opencode@microsoft.com) con otras preguntas o comentarios.

# <a name="how-to-contribute-to-windows-10-iotcore-documentation"></a>Cómo contribuir a la documentación de Windows 10 IoTCore

## <a name="legal-notices"></a>Avisos legales
Microsoft y sus colaboradores te conceden una licencia para la documentación de Microsoft y otros contenidos de este repositorio bajo la [licencia pública de Creative Commons Attribution 4.0 International](https://creativecommons.org/licenses/by/4.0/legalcode), consulta el archivo [LICENSE](LICENSE), y concédete una licencia para cualquier código del repositorio bajo la [Licencia MIT](https://opensource.org/licenses/MIT), consulta el archivo [LICENSE-CODE](LICENSE-CODE).

Microsoft, Windows, Microsoft Azure y otros productos y servicios Microsoft a los que se hace referencia en la documentación pueden ser marcas comerciales o marcas registradas de Microsoft en los Estados Unidos y en otros países o regiones.
Las licencias para este proyecto no te conceden derechos para usar los nombres, logotipos o marcas comerciales de Microsoft.
Directrices generales de marca registrada de Microsoft pueden encontrarse en http://go.microsoft.com/fwlink/?LinkID=254653.

Puede encontrar información de privacidad en https://privacy.microsoft.com/en-us/

Microsoft y sus colaboradores se reservan todos los demás derechos, ya sea bajo sus respectivos derechos de autor, patentes o marcas comerciales, y tanto de manera implícita, explícita como de otro modo.

## <a name="contributing"></a>Contribución

Este es el repositorio de Windows 10 IoT **documentación** hospedado en [ https://docs.microsoft.com/windows/iot-core ](https://docs.microsoft.com/windows/iot-core).

Si le gustaría ver cobertura de nuevo o tiene algún comentario, considere la posibilidad de [ **contribución**](/CONTRIBUTING.md).  Puede editar el contenido existente, agregar contenido nuevo o simplemente crear nuevos [problemas](https://github.com/MicrosoftDocs/windows-iotcore-docs/issues). Le echaremos un vistazo a sus sugerencias y trabajarán juntos para incorporarlos a los documentos.

Para editar contenido, simplemente haga clic en Editar en el artículo que desee realizar cambios en:

![GIF sobre cómo editar docs](windows-iotcore/media/edit-doc.gif)


También puede clonar o descargar el repositorio para realizar cambios:

![GIF sobre cómo clonar o descargar repositorio](windows-iotcore/media/download-repo.gif)

También necesitará agregar un revisor o las revisiones a las solicitudes de extracción puede obtenerlos aprobados:

![Agregar revisores a la solicitud de incorporación de cambios](windows-iotcore/media/reviewers.gif)

# <a name="conventions"></a>Convenciones
  - Al agregar una página, debe agregar una entrada para él en [toc.md](windows-iotcore/TOC.md) para que aparezca.
  - Una carpeta puede contener más carpetas o `readme.md`s
  - Los nombres de directorio o carpeta están separados por guión (p. ej., `f12-tools`) y en minúsculas. Se usan en las direcciones URL en el sitio docs.microsoft.com. No utilice caracteres de subrayado o PascalCase/camelCase.


## <a name="other-text-elements"></a>Otros elementos de texto

Estos otros elementos de texto tienen estilos disponibles:

* Listas sin ordenar
* Tiene viñetas normales
   * También puede anidar viñetas
   * Las listas de viñetas deben tener más de una entrada.
* Bastante estándar

1. Listas ordenadas
2. Use la numeración occidental regular antiguo.
3. Debe usarse solo cuando una lista realmente tiene el orden.

_________________________

Las reglas horizontales están disponibles. Se recomienda su uso con moderación para reducir el desorden.
No se combinan las reglas horizontales con etiquetas de encabezado; ya algunos usan estilos de línea en una jerarquía visual.
Además, no combine notas (ver abajo) en el medio de listas numeradas. Esto se confunden con el orden de numeración.

## <a name="displaying-code"></a>Visualización de código

Puede usar en línea `code` sintaxis de Markdown (con los acentos graves).

O puede mostrar bloques de código de este modo:

```css
body {
    background: #fff;
}
```

## <a name="tables"></a>Tablas

| Después, puede     | usar encabezados | en las tablas    |
|-------------|-------------|-------------:|
| alineado a la izquierda| A menos que un #  | 456          |
| Valor de texto  | Más texto   | $0.00        |

## <a name="notes"></a>Notas

Utilice con moderación las notas. Se trata de bloques diseñados para resaltar la información de "no-error-it".

Tenemos cuatro versiones diferentes de notas con el estilo actualmente:
- NOTA
- ADVERTENCIA
- PROPINA
- IMPORTANTE


Notas de la cita en bloque de varias líneas, use un > delante de cada una de las notas tal como se muestra en el ejemplo siguiente.

## <a name="images"></a>Imágenes

Las imágenes deben almacenarse en un `media` carpeta y que se hace referencia con una ruta de acceso relativa:

`![Note patterns](media/notes.png)`


## <a name="code-of-conduct"></a>Código de conducta
Este proyecto se ha adoptado el [Microsoft código de conducta de código abierto](https://opensource.microsoft.com/codeofconduct/). Para obtener más información, consulte el [código de conducta preguntas más frecuentes sobre](https://opensource.microsoft.com/codeofconduct/faq/) o póngase en contacto con [ opencode@microsoft.com ](mailto:opencode@microsoft.com) con otras preguntas o comentarios.
