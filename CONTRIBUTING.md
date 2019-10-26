# <a name="contributing-to-the-windows-10-iot-documentation"></a>Contribución a la documentación de Windows 10 IoT

Gracias por interesarse en nuestra documentación. Agradecemos sus comentarios, ediciones, adiciones y ayuda para mejorar nuestros documentos. En esta página se describen los pasos básicos y las instrucciones para contribuir.

## <a name="sign-a-cla"></a>Firma de un CLA

Si quiere contribuir con algo más que un par de líneas y no es un empleado de Microsoft, deberá [firmar un contrato de licencia de colaboración (CLA) de Microsoft](https://cla.microsoft.com/). 

## <a name="proposing-a-change"></a>Proposición de un cambio

Para sugerir un cambio en los documentos, siga estos pasos:

1. Si está viendo la página de Docs.microsoft.com, haga clic en el botón **Editar** en la esquina superior derecha de la página.  Se le redirigirá al archivo de origen Markdown correspondiente en el [repositorio de GitHub](https://github.com/MicrosoftDocs/windows-iotcore-docs).  Si ya se encuentra en el repositorio de GitHub, puede simplemente navegar al archivo de origen que quiere cambiar.
2. Si aún no tiene una cuenta de GitHub, haga clic en **Registrarse** en la esquina superior derecha y cree una.
3. Desde la página de GitHub que quiere cambiar, haga clic en el icono del lápiz. 
4. Modifique el archivo y use la pestaña de vista previa para asegurarse de que los cambios aparezcan correctamente.
5. Cuando haya terminado, confirme los cambios y abra una solicitud de incorporación de cambios.

Después de crear la solicitud de incorporación de cambios, un miembro del equipo de Windows 10 IoT la revisará. Si se acepta la solicitud, las actualizaciones se publican en [https://docs.microsoft.com/windows/iot-core](https://docs.microsoft.com/windows/iot-core).

## <a name="making-more-substantial-changes"></a>Realización de cambios más sustanciales

Para realizar cambios sustanciales en un artículo existente, agregar o cambiar las imágenes, o contribuir con un nuevo artículo, se recomienda realizar una bifurcación del repositorio en su cuenta de GitHub (haga clic en el botón "Bifurcación" en la esquina superior derecha del [repositorio de GitHub](https://github.com/MicrosoftDocs/windows-iotcore-docs)) y, después, crear un clon local (haga clic en el botón verde "Clonar o descargar", copie al Portapapeles y luego escriba en la línea de comandos `git clone <paste your repo clone link>`).

Antes de que contribuya con un nuevo artículo, también le pediremos que conteste a las siguientes preguntas...
* ¿He incluido un título de nivel # (equivalente a H1 en HTML) y solo uno? 
* ¿El tiempo verbal (si procede) en el título de mi nuevo artículo está en presente y es coherente con la otra documentación?
* ¿Todo la gramática es correcta?
* ¿He agregado mi artículo, en caso de que contribuya con un artículo nuevo, a la categoría adecuada y he actualizado TOC.md?
* ¿He formateado las direcciones URL correctamente para que tengan [este aspecto](https://github.com/MicrosoftDocs/windows-iotcore-docs/blob/master/CONTRIBUTING.md) en lugar de este: https://github.com/MicrosoftDocs/windows-iotcore-docs/blob/master/CONTRIBUTING.md?
* ¿El artículo nuevo lo han revisado por lo menos dos personas?
* Póngase en contacto con Terry Warwick, twarwick@microsoft.com

Cuando se acepta el nuevo artículo, se recomienda realizar lo siguiente:
* Compartir el artículo con su equipo. No ocultar el logro e informar a sus colegas.
* Seguir los comentarios del artículo haciendo clic en el botón "Seguimiento" en el cuadro de comentarios. De este modo, estará actualizado sobre los comentarios que reciba el artículo.

Para obtener más información, vea [Bifurcación de un repositorio](https://help.github.com/articles/fork-a-repo/). Tenga en cuenta que no se combinarán las solicitudes de incorporación de cambios que se encuentren en la rama publicada. Asegúrese de que la solicitud de incorporación de cambios la envía a la rama principal.

Si no está familiarizado con el uso de Git, pruebe el [entrenamiento Lynda.com Git Essentials](https://www.lynda.com/Git-tutorials/Git-Essential-Training/100222-2.html).

## <a name="authoring-your-contribution"></a>Creación de la contribución

Una vez que ha bifurcado y clonado el repositorio en el equipo local, puede empezar a crear con el editor de texto que prefiera.  Por supuesto, recomendamos [Visual Studio Code](https://code.visualstudio.com/), un editor ligero gratuito de código abierto de Microsoft. Para obtener ayuda con la creación de Markdown, consulte este [Markdown es divertido para todo el mundo. Póster](windows-iotcore/media/DocsMarkdownPoster.pdf) con todos los aspectos básicos que debe conocer. Incluso puede imprimirlo y colgarlo en su pared como un recordatorio para contribuir. 

## <a name="submitting-your-contribution-and-filing-a-pull-request-pr"></a>Envío de la contribución y tramitación de una solicitud de incorporación de cambios

Una vez que esté listo para agregar los cambios en el repositorio remoto para que realicen una copia intermedia para la publicación, escriba los pasos siguientes en la línea de comandos:
- `git status`: este comando le mostrará los archivos que ha modificado para que pueda confirmar que ha previsto realizar esos cambios. 
- `git add -A`: este comando indica a GIT que agregue todos los cambios. Si prefiere agregar solo los cambios realizados en un archivo concreto, escriba el comando: `git add <file.md>`, donde "file.md" representa el nombre del archivo que contiene los cambios.
- `git commit -m “Fixed a few typos”`: este comando indica a GIT que confirme los cambios que ha agregado en el paso anterior, junto con un mensaje breve que describe los cambios realizados.
- `git push origin <yourbranchname>`: este comando envía los cambios al repositorio remoto que ha bifurcado en GitHub (el "origen") en la rama que ha especificado. Puesto que ya ha realizado la bifurcación del repositorio en su propia cuenta de GitHub, le invitamos a realizar su trabajo en la rama **En desarrollo**. 

Cuando esté satisfecho con los cambios y listo para enviar una solicitud, haga lo siguiente:
- Vaya a la bifurcación del repositorio de IoT: https://github.com/your-github-alias/windows-iotcore-docs.
- Haga clic en el botón "Nueva solicitud de incorporación de cambios". (La "bifurcación base:" se mostrará como "MicrosoftDocs/Windows-iotcore-docs", la "bifurcación Head:" debe mostrar la bifurcación del repositorio y la rama en la que realizó los cambios). También puede revisar los cambios aquí. 
- Haga clic en el botón verde "Crear solicitud de incorporación de cambios". Después, se le pedirá que asigne un título y una descripción a su solicitud de incorporación de cambios y, luego, haga clic otra vez en el botón "Crear solicitud de incorporación de cambios".

Después de insertar su contribución en el repositorio remoto, el *servicio de compilación de publicación abierta* le enviará un correo en el que se le informa si su contribución se ha compilado correctamente y se vinculan las advertencias de error, como vínculos rotos. Haga clic en los vínculos para ver el contenido del que se ha realizado una copia intermedia en el sitio.

Una vez que haya revisado su contribución en el [sitio de ensayo de documentos de Windows 10 IoT](https://review.docs.microsoft.com/en-us/windows/iot-core/) y esté seguro de que quiere que se publiquen los cambios, debe tramitar una solicitud de incorporación de cambios.

Una vez enviada la solicitud de incorporación de cambios, un miembro del equipo de documentos de Windows 10 IoT la revisará. Cuando se acepte, podrá ver los cambios en el [sitio de ensayo](https://review.docs.microsoft.com/en-us/windows/iot-core). Finalmente, estas actualizaciones se publicarán en [https://docs.microsoft.com/windows/iot-core](https://docs.microsoft.com/windows/iot-core).

## <a name="working-with-branches"></a>Trabajo con ramas

El [repositorio de github de documentos de IOT de Windows 10](https://github.com/MicrosoftDocs/windows-iotcore-docs) utiliza dos ramas principales: [desarrollar](https://github.com/MicrosoftDocs/windows-iotcore-docs/tree/develop), este contenido se puede revisar en el [sitio de ensayo](https://review.docs.microsoft.com/en-us/windows/iot-core)y en [directo](https://github.com/MicrosoftDocs/windows-iotcore-docs/tree/live), para el contenido que aparece en el [sitio activo](https://docs.microsoft.com/windows/iot-core). 

Al realizar contribuciones, envíe la solicitud de incorporación de cambios a la rama **En desarrollo**. Esta rama se puede ver en el sitio de ensayo y solo debe contener las contribuciones que están listas para ser publicadas.

## <a name="using-issues-to-provide-feedback-on-iot-documentation"></a>Uso de problemas para enviar comentarios en la documentación de IoT

Para enviar comentarios en lugar de modificar directamente las páginas de documentación reales, [cree un problema](https://github.com/MicrosoftDocs/windows-iotcore-docs/issues).

Asegúrate de incluir el título del tema y la dirección URL de la página.

## <a name="additional-resources"></a>Recursos adicionales
- [Introducción a la escritura y la aplicación de formato en GitHub](https://help.github.com/articles/getting-started-with-writing-and-formatting-on-github/)

## <a name="additional-resources-for-microsoft-employees"></a>Recursos adicionales para los empleados de Microsoft
- [Conectar la cuenta de GitHub y el alias de MS](https://review.docs.microsoft.com/en-us/windows-authoring-guide/github-account#2-connect-your-github-account-and-ms-alias-on-the-microsoft-open-source-portal)
- [Recursos para la escritura de Markdown](https://review.docs.microsoft.com/en-us/windows-authoring-guide/writing-guidance/writing-markdown)
