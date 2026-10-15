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

## Rúbrica de evaluación del anteproyecto (antes de enviarlo a la FECI)

Esta rúbrica es para revisar el anteproyecto con el equipo antes de subirlo a la plataforma, usando los mismos criterios con los que después lo verán los evaluadores de la FECI (habilidades de investigación, comprensión del fenómeno o problema, manejo de información y comunicación).

| Criterio | Puntos | Excelente | Bueno | Suficiente | No suficiente |
|---|---|---|---|---|---|
| Problema o meta de ingeniería, justificación y antecedentes (I, II, III, IV) | 20 | El problema o la meta está claramente delimitada y es verificable; los antecedentes y la justificación se apoyan en datos o referencias reales y específicas al contexto del proyecto | El problema o la meta está bien planteada pero algo general; antecedentes y justificación presentes, con referencias limitadas o poco específicas | El problema o la meta es identificable pero vaga o difícil de verificar; antecedentes y justificación superficiales, con poco respaldo de datos | No queda claro qué problema resuelve el proyecto ni cuál es la meta de ingeniería; antecedentes y justificación ausentes o genéricos |
| Objetivos (V) | 15 | Los objetivos son medibles, verificables y están alineados con la meta; se distingue claramente el resultado esperado del método para llegar a él | Los objetivos son claros, aunque alguno se confunde con un paso de implementación o no es del todo medible | Los objetivos están presentes pero son vagos, difíciles de medir, o se mezclan con la metodología | Los "objetivos" son en realidad una lista de tareas o pasos de construcción, sin indicar qué se va a lograr |
| Metodología (VI) | 10 | El proceso de diseño está claramente estructurado en etapas lógicas, con las técnicas y criterios de cada etapa justificados y conectados con los objetivos | Las etapas del proceso están descritas, aunque la justificación de alguna técnica o criterio es limitada | Se mencionan las etapas generales del proceso, pero sin suficiente justificación de las técnicas o criterios usados | No hay un proceso claro, o las etapas no están conectadas entre sí ni con los objetivos |
| Ejecución y construcción (VIII) | 15 | Se detallan los materiales, componentes y decisiones de implementación (hardware y software) con suficiente precisión para que otra persona pueda replicar el prototipo | Se describen los materiales y el proceso de construcción, aunque faltan justificar algunas decisiones técnicas | Se mencionan los componentes usados, pero sin detalle suficiente del proceso de construcción o programación | La descripción es ambigua y no permite entender cómo se construyó realmente el prototipo |
| Resultados (IX) | 20 | Se presentan datos concretos (mediciones, porcentajes, tiempos) y, si aplica, se declaran explícitamente como preliminares | Hay datos, pero algunos resultados se reportan de forma cualitativa en vez de cuantitativa | Los resultados son vagos o incompletos, sin suficientes datos de respaldo | No hay resultados reales, solo expectativas o afirmaciones sin evidencia |
| Conclusiones (X) | 10 | Las conclusiones se fundamentan directamente en los resultados obtenidos, con limitaciones y trabajo futuro bien identificados | Las conclusiones son razonables, aunque alguna no se conecta claramente con los resultados reportados | Las conclusiones son genéricas y poco conectadas con los datos obtenidos | Las conclusiones se basan en lo que se esperaba lograr, no en lo que realmente se obtuvo |
| Referencias y redacción (XI, formato general) | 10 | Fuentes confiables y correctamente citadas; redacción clara; incluye apoyos visuales (diagramas, fotos) que ilustran el proyecto | Fuentes adecuadas, con errores menores de formato; redacción clara, con pocos apoyos visuales | Fuentes limitadas o poco relacionadas; redacción con errores que dificultan la lectura | Sin referencias o con referencias no verificables; redacción confusa, sin apoyos visuales |
| **Total** | **100** | | | | |

**Importante:** según la propia convocatoria, los evaluadores de la FECI no califican el dinero invertido en el proyecto, el impacto visual del material de exposición, ni el prestigio de la institución de procedencia. Esta rúbrica deliberadamente tampoco les da peso a esos elementos.
