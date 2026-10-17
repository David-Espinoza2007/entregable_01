# Monitoreo de cadena de frío de vacunas con LoRaWAN

**Equipo:** (nombres de los integrantes)

**Categoría:** Ingenierías, Sistemas Informáticos (Sistemas embebidos / IoT)

## I. Introducción

Las vacunas deben guardarse en ambientes de 2—8 °C. Si se calientan o se congelan, pierden su efecto, pero se ven igual que una vacuna buena. En los centros de salud, la temperatura del refrigerador se revisa a mano solo dos veces al día. Si el refrigerador falla de noche o en fin de semana, nadie se entera a tiempo.

Este proyecto es un sistema de Internet de las Cosas que vigila las 24 horas la temperatura, la puerta y la energía eléctrica de un refrigerador de vacunas. Usa sensores LoRaWAN de batería que siguen funcionando durante un apagón. Cuando detecta un problema, avisa al personal y, si nadie responde, avisa a la siguiente persona responsable.

## II. Antecedentes

- **Cómo se hace hoy en México.** La NOM-036-SSA2-2012 y el Manual de Vacunación piden mantener las vacunas de 2—8 °C y registrar la temperatura dos veces al día, al inicio y al final de la jornada. Esto deja unas 16 horas sin vigilancia cada noche y más de 60 horas cada fin de semana.
- **Normas internacionales.** La OMS define alarmas para registradores de temperatura de refrigeradores de vacunas: calor a 8 °C o más durante 10 horas, y congelamiento a −0.5 °C o menos durante 60 minutos. El congelamiento se considera más urgente.
- **Nexleaf ColdTrace (Kenia y otros países).** Sensores con conexión celular que mandan SMS cuando la temperatura sale de rango o se va la luz. En Kilifi, Kenia, estas alertas ayudaron a salvar unas 2,000 dosis durante un apagón. Nexleaf estima que el 55% de los centros de salud dependen de refrigeradores que funcionan mal o no funcionan. Su limitación: cada refrigerador necesita su propia SIM y plan de datos, y un SMS no garantiza que alguien actúe.
- **eVIN (India).** Sistema nacional que monitorea temperatura e inventario en más de 29 mil puntos de cadena de frío. Un estudio de campo encontró registradores que dejaron de transmitir por semanas sin que nadie lo notara, mala conectividad y doble registro en papel y en el sistema.

Fuentes: [Manual de Procedimientos Técnicos de Vacunación](https://salud.gob.mx/unidades/cdi/documentos/DOCSAL7301.pdf), [OMS PQS E006/TR06.3](https://extranet.who.int/prequal/key-resources/documents/pqs-performance-specification-e006tr063-30-day-electronic-refrigerator), [Nexleaf](https://www.nexleaf.org/work/vaccines/), [UNDP – eVIN](https://www.undp.org/india/projects/improving-vaccination-systems-evin), [estudio de campo de eVIN](https://pmc.ncbi.nlm.nih.gov/articles/PMC13450870/).

Este proyecto es un desarrollo nuevo que toma estos antecedentes y busca resolver lo que les falta: conectividad barata para muchos refrigeradores, detectar sensores que dejan de reportar y asegurar que alguien atienda la alerta.

## III. Definición del problema o meta de ingeniería

**Problema:** en los centros de salud, nadie vigila los refrigeradores de vacunas fuera del horario laboral. Si hay un apagón, la puerta queda abierta o el refrigerador falla de noche, las vacunas pueden dañarse sin que nadie se entere.

**Meta de ingeniería:** diseñar y construir un prototipo funcional con equipo LoRaWAN Milesight que:

- mida la temperatura de un refrigerador de vacunas de forma continua, con un error máximo de +-0.5 °C;
- detecte corte de luz, puerta abierta, temperatura fuera de rango (2—8 °C) y sensores que dejan de reportar;
- envíe una alerta al celular del personal en menos de 2 minutos después de que se cumple la condición de alarma;
- escale la alerta a la siguiente persona si nadie la confirma;
- siga funcionando durante un apagón (sensores con batería).

## IV. Justificación

- **Salud:** una vacuna dañada no protege, y no se nota a simple vista. Vigilar el refrigerador todo el tiempo asegura que la vacuna que se aplica sí funcione.
- **Personal de salud:** hoy una persona carga con la responsabilidad de un refrigerador que no puede vigilar de noche. El sistema le avisa a tiempo y deja registro de qué pasó, para que las decisiones se tomen con datos.
- **Equidad:** las clínicas rurales tienen más apagones y menos recursos. LoRaWAN no necesita WiFi, los sensores funcionan con batería y un solo gateway cubre varios refrigeradores o clínicas cercanas.
- **Escalabilidad:** el mismo sistema sirve para bancos de sangre, laboratorios, farmacias, restaurantes y transporte refrigerado, cambiando solo los umbrales.
- **ODS:** contribuye al ODS 3 (Salud y bienestar).

## V. Objetivos

**Objetivo general:** desarrollar un sistema IoT con LoRaWAN que monitoree las 24 horas la temperatura, la puerta y la energía eléctrica de un refrigerador de vacunas, y que avise a tiempo al personal responsable para evitar que las vacunas se dañen.

**Objetivos específicos:**

1. Medir la temperatura con un error máximo de +-0.5 °C respecto a un termómetro de referencia.
2. Enviar la alerta de corte de luz, puerta abierta y temperatura fuera de rango en menos de 2 minutos en al menos el 95% de las pruebas.
3. Escalar la alerta al siguiente responsable en el tiempo configurado (10 minutos) en el 100% de las pruebas donde nadie la confirma.
4. Detectar un sensor que dejó de reportar en menos de 30 minutos.
5. Registrar automáticamente al menos el 99% de las lecturas durante 7 días de operación continua.

## VI. Metodología

El proyecto se desarrolla en cinco etapas:

1. **Validación del problema.** Entrevistar a personal de un centro de salud o farmacia para confirmar cómo se vigilan hoy los refrigeradores y qué pasa cuando fallan. Revisar la NOM-036-SSA2-2012 y el Manual de Vacunación para definir los rangos de temperatura y los tiempos de alarma.
2. **Selección y prueba de equipo.** Probar cada componente por separado:
   - sensor de temperatura TS302 con sonda PT100 dentro de un frasco con glicol, que imita la temperatura real de la vacuna y evita falsas alarmas al abrir la puerta;
   - contacto magnético SS21 para la puerta;
   - sensor EM300-DI con un relevador de 127 V para detectar el corte de luz;
   - gateway UG65.

   Se eligió LoRaWAN porque los sensores funcionan con batería, siguen transmitiendo durante un apagón, no necesitan WiFi y un solo gateway recibe a todos.
3. **Integración.** Conectar los sensores al gateway y el gateway a la plataforma en la nube (Milesight Development Platform, o el servidor LoRaWAN del propio gateway por MQTT/HTTP). Verificar que los datos lleguen completos y con la hora correcta.
4. **Alertas y escalamiento.** Programar las reglas de alarma con los umbrales de la etapa 1, el envío de mensajes al celular y el escalamiento: enfermera, director, velador y jurisdicción, hasta que alguien confirme.
5. **Validación.** Probar el sistema en un mini refrigerador:
   - comparar las lecturas contra un termómetro de referencia (objetivo 1);
   - simular apagones, puertas abiertas y temperaturas fuera de rango, y medir el tiempo de cada alerta (objetivo 2);
   - dejar alertas sin confirmar para medir el escalamiento (objetivo 3);
   - apagar un sensor para comprobar que se detecta (objetivo 4);
   - operar el sistema 7 días seguidos y contar las lecturas registradas (objetivo 5).

## VII. Hipótesis (solo para Proyectos de Ciencias)

Esta sección no se llena ya que el proyecto no está registrado en la modalidad de Ciencias, 

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
