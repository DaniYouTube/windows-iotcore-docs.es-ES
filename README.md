## <a name="microsoft-open-source-code-of-conduct"></a>Código de conducta de código abierto de Microsoft

Este proyecto ha adoptado el [código de conducta de código abierto de Microsoft](https://opensource.microsoft.com/codeofconduct/).
Para obtener más información, vea las preguntas más [frecuentes sobre el código de conducta](https://opensource.microsoft.com/codeofconduct/faq/) o póngase en contacto [opencode@microsoft.com](mailto:opencode@microsoft.com) con si tiene preguntas o comentarios adicionales.

# <a name="how-to-contribute-to-windows-10-iotcore-documentation"></a>Cómo contribuir a la documentación de Windows 10 IoTCore

## <a name="legal-notices"></a>Avisos legales
Microsoft y sus colaboradores te conceden una licencia para la documentación de Microsoft y otros contenidos de este repositorio bajo la [licencia pública de Creative Commons Attribution 4.0 International](https://creativecommons.org/licenses/by/4.0/legalcode), consulta el archivo [LICENSE](LICENSE), y te conceden una licencia para cualquier código del repositorio bajo la [Licencia MIT](https://opensource.org/licenses/MIT), consulta el archivo [LICENSE-CODE](LICENSE-CODE).

Microsoft, Windows, Microsoft Azure y otros productos y servicios de Microsoft a los que se hace referencia en la documentación pueden ser marcas comerciales o marcas registradas de Microsoft en los Estados Unidos y en otros países o regiones.
Las licencias para este proyecto no te conceden derechos para usar los nombres, logotipos ni marcas comerciales de Microsoft.
Las directrices generales sobre marcas comerciales de Microsoft pueden encontrarse en http://go.microsoft.com/fwlink/?LinkID=254653.

La información sobre privacidad puede encontrarse en https://privacy.microsoft.com/en-us/.

Microsoft y sus colaboradores se reservan todos los demás derechos, ya sea bajo sus respectivos copyrights, patentes o marcas comerciales, y tanto de manera implícita, explícita como de otro modo.

## <a name="contributing"></a>Contribución

Este es el repositorio de la **documentación** de Windows 10 IoT hospedado en [https://docs.microsoft.com/windows/iot-core](https://docs.microsoft.com/windows/iot-core).

Si le gustaría ver la nueva cobertura o tiene algún comentario, considere la posibilidad de [**contribuir**](/CONTRIBUTING.md).  Puede editar el contenido existente, agregar contenido nuevo o simplemente crear [incidencias](https://github.com/MicrosoftDocs/windows-iotcore-docs/issues) nuevas. Examinaremos sus sugerencias y trabajaremos de forma conjunta para incorporarlas a la documentación.

Para editar contenido, simplemente haga clic en Editar en el artículo que quiera modificar:

![Gif sobre cómo editar la documentación](windows-iotcore/media/edit-doc.gif)


También puede clonar o descargar el repositorio para realizar cambios:

![Gif sobre cómo clonar o descargar el repositorio](windows-iotcore/media/download-repo.gif)

También tendrá que agregar un revisor o revisiones a las solicitudes de incorporación de cambios para que se aprueben:

![Adición de revisores a la solicitud de incorporación de cambios](windows-iotcore/media/reviewers.gif)

# <a name="conventions"></a>Convenciones
  - Al agregar una página, tendrá que agregar una entrada para ella en [toc.md](windows-iotcore/TOC.md) para que aparezca.
  - Una carpeta puede contener más carpetas o archivos `readme.md`.
  - Los nombres de directorio o carpeta están separados por guiones (p. ej., `f12-tools`) y en minúsculas. Se usan en las direcciones URL del sitio docs.microsoft.com. No use caracteres de subrayado ni los formatos PascalCase o camelCase.


## <a name="other-text-elements"></a>Otros elementos de texto

Estos otros elementos de texto tienen estilos disponibles:

* Listas sin ordenar
* Tienen viñetas normales
   * También puede anidar las viñetas
   * Las listas de viñetas deben tener más de una entrada.
* Bastante estándar

1. Listas ordenadas
2. Use la numeración de estilo occidental convencional.
3. Solo se debe usar cuando una lista incluya realmente un orden.

_________________________

Hay reglas horizontales disponibles. Se recomienda usarlas con moderación para reducir el desorden.
No combine reglas horizontales con etiquetas de encabezado; en algunas ya se usan estilos de línea para la jerarquía visual.
Además, no combine las notas (ver a continuación) en el medio de las listas numeradas. Esto afecta al orden de numeración.

## <a name="displaying-code"></a>Representación de código

Puede usar la sintaxis de Markdown `code` en línea (con los acentos graves).

O bien, puede mostrar los bloques de código de esta forma:

```css
body {
    background: #fff;
}
```

## <a name="tables"></a>Tablas

| Después, puede     | usar encabezados | en las tablas    |
|-------------|-------------|-------------:|
| Alineada a la izquierda| A menos que sea un número  | 456          |
| Valor de texto  | Más texto   | 0,00 USD        |

## <a name="notes"></a>Notas

Use las notas con moderación. Se trata de bloques diseñados para resaltar información "fundamental".

En la actualidad, hay cuatro versiones de estilo de nota diferentes:
- NOTA
- ADVERTENCIA
- SUGERENCIA
- IMPORTANTE


Para las notas de cita en bloque de varias líneas, use un signo > delante de cada una de las notas, como se muestra en el ejemplo siguiente.

## <a name="images"></a>Imágenes

Las imágenes se deben almacenar en una carpeta `media` y hacerles referencia con una ruta de acceso relativa:

`![Note patterns](media/notes.png)`


## <a name="code-of-conduct"></a>Código de conducta
Este proyecto ha adoptado el [código de conducta de código abierto de Microsoft](https://opensource.microsoft.com/codeofconduct/). Para obtener más información, vea las preguntas más [frecuentes sobre el código de conducta](https://opensource.microsoft.com/codeofconduct/faq/) o póngase en contacto [opencode@microsoft.com](mailto:opencode@microsoft.com) con si tiene preguntas o comentarios adicionales.
