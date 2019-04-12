# <a name="contributing-to-the-windows-10-iot-documentation"></a>Contribuir a la documentación de Windows 10 IoT

Le agradecemos su interés en nuestra documentación. Le agradecemos sus comentarios, las modificaciones, adiciones y ayuda para mejorar a nuestra documentación. Esta página tratan los pasos básicos y directrices de contribución.

## <a name="sign-a-cla"></a>Firmar un CLC

Si desea contribuir con más de un par de líneas y no es un empleado de Microsoft, deberá [firmar un contrato de licencia de colaboración (CLA) de Microsoft](https://cla.microsoft.com/). 

## <a name="proposing-a-change"></a>Método para proponer cambios

Para sugerir un cambio en los documentos, siga estos pasos:

1. Si está viendo la página de Docs.microsoft.com, haga clic en el **editar** botón en la esquina superior derecha de la página.  Se le redirigirá al archivo de código fuente Markdown correspondiente en el [repositorio de GitHub](https://github.com/MicrosoftDocs/windows-iotcore-docs).  Si ya están en el repositorio de GitHub, simplemente puede navegar al archivo de origen que desea cambiar.
2. Si aún no tiene una cuenta de GitHub, haga clic en **Sign Up** en la esquina superior derecha y crear una nueva cuenta.
3. En la página de GitHub que le gustaría cambiar, haga clic en el icono de lápiz. 
4. Modifique el archivo y use la ficha Vista previa para asegurarse de que los cambios aparezcan correctamente.
5. Cuando haya terminado, confirme los cambios y abra una solicitud de incorporación de cambios.

Después de crear la solicitud de incorporación de cambios, un miembro del equipo de Windows 10 IoT revisará. Si se aceptó la solicitud, las actualizaciones se publican en [ https://docs.microsoft.com/windows/iot-core ](https://docs.microsoft.com/windows/iot-core).

## <a name="making-more-substantial-changes"></a>Hacer cambios más sustanciales

Para realizar cambios sustanciales en un artículo existente, agregar o cambiar las imágenes o contribuir con un nuevo artículo, se recomienda realizar la bifurcación del repositorio en su cuenta de GitHub (haga clic en el botón "Bifurcación" en la esquina superior derecha de la [repositorio de GitHub](https://github.com/MicrosoftDocs/windows-iotcore-docs)y, a continuación, crear un clon local (haga clic en el botón verde "Clonar o descargar", escriba copiar al Portapapeles y luego en la línea de comandos `git clone <paste your repo clone link>`).

También le pediremos, antes de que contribuyen a un nuevo artículo, para Hágase las siguientes preguntas...
* ¿He incluí uno y solo otro título # nivel (equivalente a H1 en HTML)? 
* ¿Es el tiempo verbal verbo (si procede) en el título de mi nuevo artículo en el tiempo verbal presente y coherentes con la otra documentación?
* ¿Es todo mi gramática correcto?
* ¿He agregar mi artículo - si colabora en un artículo nuevo - a la categoría correspondiente así como actualizar TOC.md?
* He tiene el formato correcto direcciones URL para [este aspecto](https://github.com/MicrosoftDocs/windows-iotcore-docs/blob/master/CONTRIBUTING.md) en lugar de esto: https://github.com/MicrosoftDocs/windows-iotcore-docs/blob/master/CONTRIBUTING.md
* ¿Ha tenido al menos dos personas revisar el artículo nuevo?
* ¿Ya se contactó con Sara (saclayt) o Namrata (namkedia) si no está seguro acerca de nada?

Cuando se aceptan el nuevo artículo, se recomienda lo siguiente:
* Comparta el artículo con su equipo. No ocultar el logro - informar a sus colegas.
* Siga los comentarios para el artículo haciendo clic en el botón "Seguimiento" en el cuadro de comentarios. De este modo, se mantendrá actualizado en los comentarios que reciba el artículo.

Para obtener más información, consulte [bifurcar un repositorio](https://help.github.com/articles/fork-a-repo/). Tenga en cuenta que no se combinará los PR que se encuentran en la rama live. Asegúrese de que está enviando una solicitud a la rama principal.

Si no está familiarizado con el uso de Git, pruebe el [entrenamiento Lynda.com Git Essentials](https://www.lynda.com/Git-tutorials/Git-Essential-Training/100222-2.html).

## <a name="authoring-your-contribution"></a>Creación de su contribución

Una vez que ha bifurcado y clonado el repositorio en el equipo local, puede empezar a crear con el editor de texto que prefiera.  Por supuesto, recomendamos [Visual Studio Code](https://code.visualstudio.com/), un editor ligero gratuito de código abierto de Microsoft. Para obtener ayuda con la creación de markdown, pruebe esta [Markdown es DIVERTIDO durante todo el mundo! Póster](windows-iotcore/media/DocsMarkdownPoster.pdf) con todos los aspectos básicos que necesita saber. Incluso puede imprimirlo y bloqueo en su muro de como un recordatorio para contribuir. 

## <a name="submitting-your-contribution-and-filing-a-pull-request-pr"></a>Enviar su contribución y presentar una extracción de solicitud de incorporación de cambios

Una vez que esté listo para agregar los cambios en el repositorio remoto para que se almacenará provisionalmente para la publicación, escriba lo siguiente en la línea de comandos:
- `git status`: Este comando le mostrará qué archivos han cambiado para que pueda confirmar que desea realizar esos cambios. 
- `git add -A`: Este comando indica a git para agregar todos los cambios. Si prefiere agregar solo los cambios realizados en un archivo concreto, en su lugar, escriba el comando: `git add <file.md>`, donde "file.md" representa el nombre del archivo que contiene los cambios.
- `git commit -m “Fixed a few typos”`: Este comando indica a git para confirmar los cambios que agregó en el paso anterior, junto con un mensaje breve que describe los cambios realizados.
- `git push origin <yourbranchname>`: Este comando inserta los cambios en el repositorio remoto que ha realizado la bifurcación en GitHub (el "origen") en la rama que haya especificado. Ya ha bifurcado el repositorio en su propia cuenta de GitHub, es bienvenidas realizar su trabajo el **desarrollar** rama. 

Cuando esté satisfecho con los cambios y está listo para enviar una solicitud:
- Vaya a la bifurcación del repositorio de IoT: https://github.com/your-github-alias/windows-iotcore-docs.
- Haga clic en el botón "Nueva solicitud de extracción". (La "bifurcación base:" se mostrará como "MicrosoftDocs/windows-iotcore-docs," la "bifurcación principal:" debe mostrar la bifurcación del repositorio y la rama en la que ha realizado los cambios.) Puede revisar los cambios aquí también. 
- Haga clic en el botón "Create pull request" verde. A continuación, le pedirá que asigne a su solicitud de incorporación de cambios, un título y una descripción y luego haga clic en el botón "Create pull request" una vez más.

Después de insertar su contribución en el repositorio remoto, se le enviará un correo electrónico de *servicio de publicación abierta compilar* que le informa de si su contribución generado correctamente y vinculación a las advertencias de error, como vínculos rotos, haga clic en el vínculos para ver el contenido almacenado provisionalmente en el sitio.

Una vez que haya revisado su contribución en el [sitio de ensayo de la documentación de Windows 10 IoT](https://review.docs.microsoft.com/en-us/windows/iot-core/) y esté seguro de que desea que los cambios que se ha publicado en vivo, debe presentar una extracción de solicitud de incorporación de cambios.

Una vez que se envía su solicitud, un miembro del equipo de docs Windows 10 IoT revisará. Cuando los acepta, podrá ver los cambios en el [sitio de ensayo](https://review.docs.microsoft.com/en-us/windows/iot-core). Estas actualizaciones, finalmente, se publicará en vivo en [ https://docs.microsoft.com/windows/iot-core ](https://docs.microsoft.com/windows/iot-core).

## <a name="working-with-branches"></a>Trabajo con ramas

El [repositorio de GitHub de Windows 10 IoT Docs](https://github.com/MicrosoftDocs/windows-iotcore-docs) utiliza dos ramas principales: [Desarrollar](https://github.com/MicrosoftDocs/windows-iotcore-docs/tree/develop), puede consultar este contenido en el [sitio de ensayo](https://review.docs.microsoft.com/en-us/windows/iot-core), y [Live](https://github.com/MicrosoftDocs/windows-iotcore-docs/tree/live), para el contenido que aparece en el [sitio activo](https://docs.microsoft.com/windows/iot-core). 

Al realizar contribuciones, envíe la incorporación de cambios de solicitud (PR) a la **desarrollar** rama. Esta rama se puede ver en el sitio de ensayo y solo debe contener las contribuciones que están listas para ser publicado en vivo.

## <a name="using-issues-to-provide-feedback-on-iot-documentation"></a>Uso de problemas para proporcionar comentarios sobre la documentación de IoT

Para proporcionar comentarios en lugar de modificar directamente las páginas de documentación real, [cree un problema](https://github.com/MicrosoftDocs/windows-iotcore-docs/issues).

Asegúrate de incluir el título del tema y la dirección URL de la página.

## <a name="additional-resources"></a>Recursos adicionales
- [Cómo empezar a escribir y aplicar formato en GitHub](https://help.github.com/articles/getting-started-with-writing-and-formatting-on-github/)

## <a name="additional-resources-for-microsoft-employees"></a>Recursos adicionales para los empleados de Microsoft
- [Conecte su cuenta de GitHub y alias de MS](https://review.docs.microsoft.com/en-us/windows-authoring-guide/github-account#2-connect-your-github-account-and-ms-alias-on-the-microsoft-open-source-portal)
- [Recursos para la escritura de Markdown](https://review.docs.microsoft.com/en-us/windows-authoring-guide/writing-guidance/writing-markdown)
