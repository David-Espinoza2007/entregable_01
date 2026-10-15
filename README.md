# Guía de registro del proyecto FECI (punto 3.1 de la convocatoria)

Este documento explica, punto por punto, los 11 elementos que pide el protocolo de registro de la FECI Chihuahua 2026 (sección 3.1 de la convocatoria), con una explicación de qué espera cada sección y un ejemplo de cómo llenarla.

**Proyecto de referencia usado en los ejemplos:** sistema de IoT para monitoreo de agua en parcelas agrícolas (humedad del suelo y nivel de agua disponible, con alertas de riego en tiempo real). Es un proyecto de categoría Ingenierías, Sistemas Informáticos (Sistemas embebidos), así que en los ejemplos se llena la sección VIII (Ejecución y construcción) en vez de la VII (Hipótesis, que es solo para Proyectos de Ciencias).

## I. Introducción

**Qué pide:** una presentación breve del tema, el contexto general y de qué trata el proyecto, para que cualquier lector entienda de inmediato el panorama antes de entrar en detalles.

**Ejemplo:**

> El agua para riego agrícola es uno de los recursos más limitados en el estado de Chihuahua, y gran parte de las parcelas de la región siguen usando criterios manuales o intuitivos para decidir cuándo y cuánto riego aplicar. Este proyecto presenta el diseño e implementación de un sistema de Internet de las Cosas (IoT) capaz de medir en tiempo real la humedad del suelo y el nivel de agua disponible en una parcela, y de enviar alertas automáticas al productor cuando es necesario regar, con el fin de reducir el desperdicio de agua sin afectar el rendimiento del cultivo.

## II. Antecedentes

**Qué pide:** qué se sabe ya sobre el tema, qué se ha hecho antes (por otros investigadores, empresas o en la literatura) y qué datos o estudios previos sustentan el proyecto. Si es un proyecto de continuidad de uno anterior, aquí se declara.

**Ejemplo:**

> Según datos de la Comisión Nacional del Agua, el sector agrícola consume más del 75% del agua disponible en el estado de Chihuahua, y buena parte de ese volumen se pierde por riego excesivo o mal programado. Existen soluciones comerciales de riego inteligente (como sensores de humedad conectados a controladores de riego), pero su costo las hace poco accesibles para productores de pequeña y mediana escala. En el ámbito académico, diversos estudios de agricultura de precisión muestran que el monitoreo continuo de humedad del suelo puede reducir el consumo de agua entre 20% y 40% sin afectar el rendimiento del cultivo. Este proyecto no es de continuidad: es un desarrollo nuevo basado en esos antecedentes.

## III. Definición del problema de investigación o meta de ingeniería

**Qué pide:** para un proyecto de Ingenierías (como este), no se plantea una pregunta de investigación sino una meta de ingeniería: qué se quiere diseñar, construir o resolver de forma concreta, y bajo qué restricciones.

**Ejemplo:**

> Meta de ingeniería: diseñar y construir un prototipo funcional de bajo costo, basado en sensores de humedad de suelo y nivel de agua conectados a un microcontrolador con conexión a internet, que capture datos en tiempo real, los almacene en una base de datos, y genere alertas automáticas de riego visibles en un tablero de visualización, con un costo de implementación menor a $1,500 MXN por unidad de monitoreo.

## IV. Justificación

**Qué pide:** por qué vale la pena hacer este proyecto, a quién beneficia y qué relevancia tiene (social, ambiental, económica, tecnológica).

**Ejemplo:**

> Este proyecto es relevante porque atiende dos problemas simultáneos: la escasez de agua en el estado y la falta de herramientas accesibles de monitoreo para pequeños productores agrícolas. Un sistema de bajo costo que indique con precisión cuándo regar permite un uso más eficiente del agua, reduce costos de operación para el productor, y contribuye directamente a los Objetivos de Desarrollo Sostenible relacionados con agua limpia y saneamiento (ODS 6) y producción agrícola sostenible (ODS 2).

## V. Objetivos

**Qué pide:** el objetivo general del proyecto y los objetivos específicos (los pasos o componentes concretos que, juntos, cumplen el objetivo general).

**Nota:** un error común es confundir los objetivos con los pasos para construir el sistema (eso corresponde a la Metodología y a la Ejecución y construcción, secciones VI y VIII). Un objetivo describe qué se quiere lograr o comprobar, de forma medible, no qué se va a hacer para llegar ahí.

**Ejemplo:**

> **Objetivo general:** desarrollar un sistema de IoT que monitoree en tiempo real la humedad del suelo y el nivel de agua disponible en una parcela agrícola, y que notifique automáticamente al productor cuándo es necesario regar.
>
> **Objetivos específicos:**
> 1. Lograr una medición de humedad del suelo y nivel de agua con un margen de error menor al 10% respecto a mediciones de referencia tomadas manualmente.
> 2. Mantener el tablero de visualización y el flujo de datos en tiempo real con una disponibilidad de al menos 95% durante el periodo de prueba.
> 3. Generar alertas de riego que coincidan con el criterio de riego recomendado para el cultivo de referencia, con al menos 12 horas de anticipación.
> 4. Reducir el consumo de agua de riego en al menos 15% respecto a un esquema de riego por calendario fijo, en la parcela piloto donde se pruebe el sistema.
> 5. Operar el sistema de forma autónoma (alimentado por panel solar) durante al menos una semana sin intervención manual.

## VI. Metodología

**Qué pide:** cómo se va a desarrollar el proyecto, paso a paso: el proceso de diseño, las técnicas, herramientas y criterios que se van a seguir para llegar a los objetivos.

**Ejemplo:**

> El proyecto se desarrolla en cinco etapas. Primero, un análisis de requerimientos para definir qué variables medir (humedad de suelo, nivel de agua) y con qué frecuencia. Segundo, la selección y prueba individual de sensores y actuadores (sensor de humedad capacitivo, sensor de nivel de agua, microcontrolador con conectividad Wi-Fi). Tercero, el diseño de la base de datos (modelo entidad-relación) y su conexión con el microcontrolador para capturar los datos en tiempo real. Cuarto, el desarrollo del tablero de visualización con los indicadores clave y la lógica de alertas. Quinto, la validación integral del sistema mediante pruebas de campo en una parcela piloto durante un periodo de al menos dos semanas, comparando las lecturas del sistema contra mediciones manuales tomadas con un medidor de humedad de referencia.

## VII. Hipótesis (solo para Proyectos de Ciencias)

**Qué pide:** esta sección se llena únicamente si el proyecto está registrado en la modalidad de Ciencias, donde se plantea una afirmación comprobable sobre una relación entre variables. En un proyecto de Ingenierías, como este, **no se llena esta sección**: en su lugar se usa la sección VIII.

**Ejemplo de qué se vería si fuera de Ciencias (solo como referencia, no aplica aquí):**

> Si se mantiene la humedad del suelo dentro del rango óptimo mediante monitoreo continuo, entonces el consumo de agua de riego disminuye en comparación con un esquema de riego por calendario fijo.

## VIII. Ejecución y construcción (para Proyectos de Ingenierías)

**Qué pide:** el detalle de cómo se construyó realmente el prototipo: los materiales y componentes usados, el proceso de armado, la programación, y las decisiones de diseño tomadas durante la construcción.

**Ejemplo:**

> Se utilizó un microcontrolador ESP32 por su conectividad Wi-Fi integrada y bajo consumo de energía, conectado a un sensor capacitivo de humedad de suelo y a un sensor ultrasónico de nivel de agua. El firmware, programado en MicroPython, lee ambos sensores cada 5 minutos y envía los datos por HTTP a una base de datos MySQL alojada en una Raspberry Pi, que funciona como servidor local. Un tablero web, construido con Python (Flask) y una librería de gráficas, consulta la base de datos y muestra los indicadores en tiempo real. Cuando la humedad del suelo cae por debajo del 30% (umbral calibrado para el cultivo de referencia), el sistema envía una alerta por correo electrónico al productor. Todo el sistema se alimenta con un panel solar pequeño y una batería, para poder operarlo directamente en la parcela sin acceso a corriente eléctrica.

## IX. Resultados

**Qué pide:** qué se obtuvo realmente al ejecutar el proyecto: datos medidos, pruebas realizadas y su desempeño. Si el proyecto se registra con un avance parcial (ver la nota al final), aquí se reportan los resultados obtenidos hasta la fecha de registro, dejando claro que son preliminares.

**Ejemplo:**

> Durante las pruebas de campo (resultados preliminares al 13 de noviembre, el proyecto continúa en desarrollo), el sensor de humedad mostró una desviación promedio de 3.2% respecto al medidor de referencia, y el sensor de nivel de agua una desviación de 1.5 cm. El sistema generó correctamente 4 alertas de riego durante 10 días de monitoreo continuo, coincidiendo con los momentos en que la medición manual también indicaba necesidad de riego. El tablero mantuvo una disponibilidad del 98% durante el periodo de prueba, con 2 interrupciones breves por pérdida de conexión Wi-Fi.

## X. Conclusiones

**Qué pide:** qué se logró respecto a los objetivos planteados, qué limitaciones se encontraron, y qué se podría mejorar o ampliar a futuro. Las conclusiones deben apoyarse directamente en los resultados obtenidos, no en expectativas.

**Ejemplo:**

> Los resultados preliminares muestran que el sistema es capaz de monitorear humedad y nivel de agua con una precisión aceptable para apoyar decisiones de riego, cumpliendo parcialmente la meta de ingeniería planteada. Como limitación, la dependencia de la conexión Wi-Fi afectó la disponibilidad del sistema en dos ocasiones, por lo que una versión futura debería incluir almacenamiento local temporal (buffer) para no perder lecturas durante cortes de conectividad. Como trabajo futuro, se plantea escalar el sistema a múltiples puntos de medición dentro de la misma parcela y probarlo con distintos tipos de cultivo.

## XI. Referencias bibliográficas

**Qué pide:** las fuentes consultadas y citadas en el documento, en un formato consistente (por ejemplo APA), incluyendo literatura académica, reportes técnicos y, si aplica, hojas de datos (datasheets) de los sensores usados.

**Ejemplo:**

> - Food and Agriculture Organization of the United Nations. (2023). *Water use in agriculture: Global trends and precision irrigation*. FAO.
> - Hanes, D., Salgueiro, C., Grossetete, P., Barton, R., Henry, J., & Trollope, R. (2017). *IoT fundamentals: Networking technologies, protocols, and use cases for the internet of things*. Cisco Press.
> - Comisión Nacional del Agua. (2024). *Estadísticas del agua en México*. CONAGUA.
> - Espressif Systems. (2023). *ESP32 Series Datasheet*. https://www.espressif.com

## Nota sobre resultados y conclusiones preliminares

Como ya se había señalado al revisar los riesgos de participar en la FECI, el cierre de la convocatoria (13 de noviembre) cae antes del cierre del reto con SYSCOM (4 de diciembre), así que al momento de registrar el anteproyecto el prototipo probablemente no esté terminado. En las secciones IX y X conviene dejar explícito que se trata de resultados y conclusiones preliminares, obtenidos hasta la fecha de registro, y no de resultados finales del reto completo. Si hay duda sobre si esto es aceptado, vale la pena confirmarlo directamente con el Instituto de Innovación y Competitividad antes del cierre de la convocatoria.
