Práctica 1. Introducción a software SIG de código abierto (QGIS + GRASS
GIS + R + Python) aplicados a la cartografía geomorfológica.
================
José Ramón Martínez Batlle
29-08-2022

# Fecha de entrega

-   9 de septiembre de 2022

# Introducción

Desde su origen en el siglo pasado (sin considerar momentáneamente los
orígenes de la cartografía), los sistemas de información geográfica
(SIG) han experimentado una densa evolución. Diría que la confusión más
común entre usuarios ha sido el asociar SIG con el software que nos dan
acceso a ellos propiamente. Aunque el software es una pieza (importante)
de los SIG, no es lo único ni lo que los define, puesto que también se
incluyen los usuarios, los datos y modelos, el hardware, las fuentes,
entre otros elementos (Olaya, 2020).

Lo que hoy conocemos como software SIG está en crisis. La irrupción del
software como servicio en el mercado, ha traigo consigo el hecho de que
muchas aplicaciones se ofrezcan alternativa o únicamente en la nube,
relegando así la tradicional aplicación de escritorio o ejecutada
localmente en la consola. Trabajar en la nube tiene muchas ventajas, una
de las más importantes es que se reduce el riesgo de fallos en la
aplicación (o al menos se pueden corregir con mayor facilidad) y se
elimina la necesidad de una instalación previa (el “infierno de
dependencias” desaparece). También, las aplicaciones en la nube, ofrecen
la posibilidad de conectar con grandes y diversas bases de datos grandes
(“*big data*”). Entre las desventajas, las más importante es que, como
usuarios, perdemos libertad, puesto que cada vez estamos más atados a la
nube para hacer nuestro trabajo, y dependemos más de la voluntad de los
proveedores. Asimismo, estos servicios en la nube terminan
convirtiéndose en una cuota mensual más que se añade a nuestra factura.

Mientras nos preparamos para ese “promisorio futuro,” todavía tenemos la
posibilidad de hacer análisis en la PC propia. Tratándose de
geomorfología, los software SIG son fundamentales para nuestros
análisis, sobre todo para realizar cartografía del relieve de forma
masiva.

En esta práctica usarás dos aplicaciones y dos lenguajes de programación
punteros para SIG, algunas de las cuales quizá ya las conoces.
Comenzarás desde lo básico, la instalación de las aplicaciones y los
lenguajes en cuestión; aunque parecería algo rutinario, instalar
software puede ser desafiante y, por tal razón, además de valorar tus
destrezas de uso, también te asigno puntuación por realizar la
instalación adecuadamente. Luego, usarás la interfaz gráfica de QGIS y
de GRASS GIS para operaciones básicas. Finalmente, te introducirás en
los lenguajes de programación R y Python con operaciones sencillas. En
todos los casos aplicarás estas herramientas a ejemplos muy básicos
sobre cartografía geomorfológica.

# Objetivos de aprendizaje

Al terminar esta práctica deberías ser capaz de:

-   Instalar y poner en marcha software y lenguajes de programación para
    SIG en una PC.

-   Cargar una capa de prueba.

# Lecturas previas recomendadas, preparación, recursos disponibles

-   Olaya (2020), páginas 1-28 de la versión PDF. En el [Drive de la
    asignatura](https://drive.google.com/drive/folders/1orlvmg86kad08FznStkmYaesxaTbzAQD?usp=sharing),
    bajo el nombre “OLAYA-Sistemas-de-Informacion-Geografica.pdf.”

-   QGIS Development Team (2022). En el [Drive de la
    asignatura](https://drive.google.com/drive/folders/1orlvmg86kad08FznStkmYaesxaTbzAQD?usp=sharing),
    bajo el nombre
    “QGIS-Guia-de-usuario-version-escritorio-de-QGIS-3.22.pdf.”

-   GRASS Development Team (2022). Disponible sólo en línea. Ver vínculo
    en [Referencias](#referencias)

-   Wickham & Grolemund (2019). Capítulos 1 a 7. Ver vínculo en
    [Referencias](#referencias)

-   Martínez-Batlle (2022). Específicamente, leer el tutorial
    “Introducción a R, simple features y análisis exploratorio de datos
    espaciales (ESDA)” (vínculo en [Referencias](#referencias)).

-   Demostraciones en aula.

# Informe

Entregarás tu informe en formato PDF, el cual podrás elaborar con tu
procesador de texto favorito (por ejemplo, LibreOffice Writer, LaTeX,
Word) o mediante entornos de desarrollo integrado (e.g. Atom, Visual
Studio Code, Jupyter Notebooks, RMarkdown-RStudio). Características del
documento:

-   Número máximo de páginas: 10.

-   En la primera página, deberás incluir nombre, matrícula, asignatura,
    nombre de la práctica, fecha.

-   Para evitar la proliferación de tipografías y formatos, debes usar
    estilos. Lo más fácil es basarse en plantillas. Hay muchos recursos
    en la web sobre cómo usar estilos (término de búsqueda recomendado:
    estilos en procesadores de texto).

-   Debes incluir tu código informático en las respuestas de los
    ejercicios donde uses lenguajes de programación (e.g. R, Python). El
    código debe ser incluido como texto, no como imagen (e.g. captura de
    pantalla).

-   Realiza doble revisión de ortografía y gramática.

-   Las páginas deben estar numeradas.

-   Si aplica, incluir ilustraciones y tablas de apoyo (a ambas debes
    incluirles título, “*caption*”), así como lista de referencias
    bibliográficas.

-   Puedes usar un apéndice para incluir información complementaria que
    no te quepa en las 10 páginas centrales.

-   Podré solicitar los archivos fuente empleados para elaborar el PDF y
    los resultados intermedios generados en cada ejercicio.

# Criterios de evaluación

| Concepto                                                                                                                                                             | Porcentaje |
|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------|:-----------|
| Instalación adecuada de aplicaciones y lenguajes de programación. Si decides usar aplicaciones en la nube, sólo se evaluarán los dos restantes sobre la base de 100% | 30%        |
| Redacción, que incluye organización de las ideas, gramática, ortografía                                                                                              | 40%        |
| Presentación, que incluye uso apropiado de estilos, tablas y figuras (legibilidad, uso de *caption*), numeración de páginas                                          | 30%        |

# Ejercicios

## Ejercicio 1. Instala y prueba QGIS, R + RStudio, GRASS GIS, y Python

En este ejercicio demostrarás que sabes instalar y poner en marcha
cuatro aplicaciones útiles en SIG, y cargarás una capa vectorial sólo
para probar las instalaciones. Instalar software localmente es,
probablemente, una tarea que realizarás menos en el futuro, puesto que
el software en la nube se está convirtiendo en estándar. Sin embargo,
instalar aplicaciones localmente siempre será necesario, sobre todo si
tu trabajo es muy especializado. Las aplicaciones QGIS y GRASS GIS, así
como los lenguajes R (con su IDE RStudio) y Python, ofrecen muchas
funcionalidades de SIG que no encontrarás en otro software.

Instalar las aplicaciones localmente (en tu PC) tiene como principal
ventaja el que no necesitas entornos intermediarios entre las
aplicaciones y tu escritorio (no necesitas Internet). Por otra parte, la
desventaja más común es que podrían no satisfacerse todas las
dependencias en tu PC.

> IMPORTANTE. Nunca instales software de fuentes no seguras. Identifica
> en cada caso el sitio web del proveedor de la aplicación o del
> lenguaje que vayas a instalar. Si tienes dudas, escríbeme.

No obstante, ten presente que existen al menos tres opciones distintas
para instalar o usar software SIG (al menos algunos de ellos), y que son
alternativas válidad también.

1.  Instalar una máquina virtual, a la cual le instalarías las
    aplicaciones, o elegirías una que ya los tenga (por ejemplo,
    OSGeoLive). Ventaja: no tendrías que preocuparte por dependencias.
    Desventaja: tendrías que habilitar la virtualización en tu PC,
    instalar un gestor de máquinas virtuales (e.g. Oracle Virtual Box) y
    familiarizarte con dicha tecnología.

2.  Instalar contenedores Docker ya preconfigurados con las
    aplicaciones. Ventaja: no tendrías que preocuparte por dependencias.
    Desventaja: tendrías que instalar Docker y familizarizarte con esa
    tecnología.

3.  Usar servicios en la nube. No instalas aplicaciones ni lenguajes,
    simplemente usas el navegador para conectarte al servicio en
    cuestión. Ventajas: cero instalación. Desventajas: necesitas
    conexión a internet estable, no todos los flujos de trabajo se
    pueden realizar con estos servicios y no todas las aplicaciones se
    ofrecen en línea.

De todas formas, para este práctica, asumiré que usas software instalado
localmente y en tu PC física, es decir, sin virtualizaciones ni
servicios en la nube.

### 1A. Instala y prueba QGIS

> Capas asignadas. Nota: el símbolo “/” separa subdirectorios. La ruta
> de partida, es decir, lo que está antes de `data` es la raíz de este
> repo.

<table>
<thead>
<tr>
<th style="text-align:left;">
Nombre completo
</th>
<th style="text-align:left;">
e1
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left;">
Linette Altagracia Turbi Tejeda
</td>
<td style="text-align:left;">
data/d001/VJQg5DHG.gpkg
</td>
</tr>
<tr>
<td style="text-align:left;">
Yerlyn Florentino Laurencio
</td>
<td style="text-align:left;">
data/d001/cQeZ7aMQ.gpkg
</td>
</tr>
<tr>
<td style="text-align:left;">
Jose Abreu Diaz
</td>
<td style="text-align:left;">
data/d001/3GOprcmM.gpkg
</td>
</tr>
<tr>
<td style="text-align:left;">
Jennifer Maldonado G
</td>
<td style="text-align:left;">
data/d001/PhpElMX5.gpkg
</td>
</tr>
<tr>
<td style="text-align:left;">
Carlos David Alcantara Vidal
</td>
<td style="text-align:left;">
data/d001/AtQkpxgV.gpkg
</td>
</tr>
<tr>
<td style="text-align:left;">
José Ramón Martínez Batlle
</td>
<td style="text-align:left;">
data/d001/HE0jF91U.gpkg
</td>
</tr>
<tr>
<td style="text-align:left;">
Reynaldo Rafael Espaillat Santos
</td>
<td style="text-align:left;">
data/d001/6nLwFTBa.gpkg
</td>
</tr>
</tbody>
</table>

0.  Para mantener el orden de archivos, te recomiendo que crees una
    carpeta, por ejemplo `practica1` dentro de “Mis Documentos,” donde
    colocarás tu informe entregable, donde copiarás los datos fuente
    (por ejemplo, puedes clonar este repo completo allí) y donde también
    alojarás los proyectos de GRASS, R y Python de los incisos
    siguientes.

1.  Instala QGIS. Prefiere la versión más reciente (la 3.26 cuando
    escribí esta práctica).
    [Este](https://www.youtube.com/watch?v=7aK1nT7iBlc) tutorial podría
    servirte.

2.  Carga la capa vectorial asignada.

3.  Añade fuentes de referencia, como OpenStreetMap, GoogleSatellite,
    Bing Maps. Te será de utilidad el plugin QuickMapServices.

4.  Captura la pantalla y pégala en tu informe.

5.  Pregunta, reflexión.

    1.  Sobre el proceso de instalación. Descríbelo.

    2.  Sobre la capa: descríbela y explica qué representa en el
        contexto territorial donde se encuentra, y escribe cuál crees
        que es la fuente de esta capa.

### 1B. Instala y prueba GRASS GIS

> Capas asignadas: las mismas que en 1A.

1.  Instala GRASS GIS. Prefiere la versión más reciente (la 8 cuando
    escribí esta práctica).
    [Este](https://www.youtube.com/watch?v=pEeI8BO7jRw) tutorial podría
    servirte.

2.  Crea una localización, y carga la capa vectorial asignada.

3.  Captura la pantalla y pégala en tu informe.

4.  Pregunta, reflexión. Menciona al menos 3 fortalezas de GRASS GIS.

### 1C. Instala y prueba R y RStudio

> Capas asignadas: las mismas que en 1A. Tal como indiqué arriba, no
> olvides incluir el código que emplees en las respuestas.

1.  Instala R, RStudio.
    [Este](https://www.youtube.com/watch?v=_2sewGCA0y4) tutorial podría
    servirte.

2.  Inicia de R o de RStudio, instala el paquete `sf`.

3.  Carga la capa vectorial asignada y represéntala.

4.  Captura la pantalla y pégala en tu informe.

5.  Pregunta, reflexión. ¿Qué fortalezas entiendes que tiene R+RStudio?

### 1D. Instala y prueba Python, Pip, entornos virtuales y Jupyter Notebooks

> Capas asignadas: las mismas que en 1A. Tal como indiqué arriba, no
> olvides incluir el código que emplees en las respuestas.

1.  Instala Python 3, Pip, entornos virtuales (paquete `virtualenv`) y
    Jupyter Notebooks. “Python 3” se refiere al lenguaje como tal, Pip
    es el sistema de gestión de paquetes escritos en Python, y Jupyter
    Notebooks es un entorno interactivo basado en la web para crear
    documentos de Jupyter.
    [Este](https://phoenixnap.com/kb/how-to-install-python-3-windows)
    tutorial te ayudará a instala Python 3, Pip y `virtualenv` (en el
    asistente de instalación, asegúrate de marcar la casilla
    `Add Python 3.# to PATH`). [Este
    vídeo](https://www.youtube.com/watch?v=AuTkAWEa06E), del minuto 4:18
    al 4:47, muestra cómo instalar Jupyter Notebooks.

> Como alternativa a lo anterior, puedes instalar Anaconda, una
> distribución completa de Python y R que facilita el cumplimiento de
> dependencias y la instalación de paquetes (por ejemplo, los paquetes
> de ciencia de datos y los espaciales son fáciles de instalar), pero
> como desventaja tiene que ocupa más espacio en disco que la
> instalación de las aplicaciones por separado. Si eliges Anaconda,
> [este vídeo](https://www.youtube.com/watch?v=FTkUcSicRIA) podría
> servirte.

> Una última alternativa: usa Google Colab; si tienes cuenta en Google,
> bastaría con activar dicho servicio, pero tiene como desventaja que
> tendrías que subir los archivos que necesites en tu procesamiento.

<!-- 2. Instala un editor de código. Si no tienes uno, te recomiendo que investigues sobre los siguientes y elijas uno: Atom (se anunció su fin recientemente), Visual Studio Code, Sublime Text, PyCharm, Spyder. El más popular actualmente es Visual Studio Code que, aunque no es de código abierto, ofrece múltiples herramientas. -->
<!-- 3. (Opcional) Si tu sistema operativo es Windows, instala una consola para administrar tu máquina sin interfaz gráfica. Windows viene con una de serie, el CMD, pero también puedes evaluar Power Shell o Cmder; esta última tiene la ventaja de que puedes usar comandos UNIX de manera natural. -->

2.  Crea y activa un entorno virtual. [Este vídeo hasta el minuto
    3:08](https://www.youtube.com/watch?v=jY2g1erTTZI) te explica qué es
    un entorno virtual y te enseña cómo instalarlo y activarlo en
    Windows. Quizá ya tiene instalado el paquete `virtualenv` y sólo
    necesitas activa el entorno virtual. IMPORTANTE: activa tu entorno
    virtual en la carpeta de tu proyecto de trabajo, por ejemplo,
    aquella donde tienes los datos de la práctica. Si usas Linux, [este
    script](crear_activar_entorno_virtual.sh) te resultará útil para
    crear tu entorno virtual.

3.  Instala los paquetes `geopandas` y `geoplot`. Instálalos una vez
    tengas tu entorno virtual activo.

4.  Activa Jupyter Notebooks, ejecutando la sentencia `jupyter notebook`
    desde la consola localizada en tu carpeta de la práctica.
    Probablemente se abra el navegador mostrando el cuaderno de Jupyter.
    En caso contrario, dirígete a la ruta <http://localhost:8888/> y
    crea un cuaderno Jupyter mediante el botón
    `New`&gt;`Python 3 (ipykernel)`. Aprende cómo crear y ejecutar tus
    sentencias de Python en este cuaderno. [Esta intro
    básica](https://www.youtube.com/watch?v=Xsrr15_c7JY) te podría
    ayudar y [este otro
    vídeo](https://www.youtube.com/watch?v=6Vr9ZUntCyE) profundiza un
    poco más.

5.  Carga la capa vectorial asignada con `geopandas` y represéntala con
    `plot` y `geoplot`. Guíate de [este](mapa_de_mi_capa.ipynb) cuaderno
    de Jupyter, adaptándolo a tu capa asignada.

6.  Captura la pantalla y pégala en tu informe.

7.  Describe lo que has realizado. Obviando los pasos de instalación,
    creación y activación de entorno virtual e instalación de paquetes,
    resume los pasos necesarios para representar tu capa asignada
    (remítete a los pasos dados en el cuaderno de Jupyter).

8.  Reflexiona. ¿Qué fortalezas entiendes que tiene Python?

# Referencias

<div id="refs" class="references csl-bib-body hanging-indent"
line-spacing="2">

<div id="ref-grass2022grass" class="csl-entry">

GRASS Development Team. (2022). *GRASS GIS 8.0.3dev Reference Manual*.
<https://grass.osgeo.org/grass80/manuals/index.html>.

</div>

<div id="ref-jose_ramon_martinez_batlle_2022_7028143" class="csl-entry">

Martínez-Batlle, J. R. (2022). <span
class="nocase">maestria-geotel-master/material-de-apoyo: First
release</span> (Version v0.0.0.9000).
<https://doi.org/10.5281/zenodo.7028143>

</div>

<div id="ref-olaya2020sistemas" class="csl-entry">

Olaya, V. (2020). *<span class="nocase">Sistemas de Informaci<span
class="nocase">ó</span>n Geogr<span class="nocase">á</span>fica. Un
libro libre de V<span class="nocase">í</span>ctor Olaya</span>*. Versión
en línea: <https://volaya.github.io/libro-sig/>. Versión PDF:
<https://github.com/volaya/libro-sig/releases/download/v3.0/Sistemas.de.Informacion.Geografica.pdf>.

</div>

<div id="ref-qgis2022qgis" class="csl-entry">

QGIS Development Team. (2022). *QGIS Desktop 3.22 User Guide*. Versión
en línea: <https://docs.qgis.org/3.22/es/docs/user_manual/>. Versón PDF:
<https://docs.qgis.org/3.22/pdf/es/QGIS-3.22-DesktopUserGuide-es.pdf>.

</div>

<div id="ref-Wickham2019Res" class="csl-entry">

Wickham, H., & Grolemund, G. (2019). *R para ciencia de datos*.
Retrieved from <https://es.r4ds.hadley.nz/>

</div>

</div>
