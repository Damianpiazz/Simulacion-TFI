# Compendio Teórico de Simulación de Sistemas y Teoría de Colas

## Segmento 1: Fundamentos Sistemotécnicos, Modelado y Taxonomía de la Simulación

### 1.1. Definición Formal de Sistema, Frontera, Entorno y Estructura
Un **sistema** se define formalmente como una colección organizada de elementos, entidades u componentes interrelacionados que interactúan dinámicamente entre sí dentro de una estructura delimitada, con el propósito de llevar a cabo una función específica o alcanzar un conjunto de objetivos predeterminados. Un sistema no es una mera yuxtaposición de partes aisladas, sino un todo integrado caracterizado por tres dimensiones fundamentales:
*   **Composición:** El conjunto de elementos o subsistemas constitutivos que integran la totalidad del objeto de estudio.
*   **Estructura:** La red de relaciones lógicas, físicas, funcionales y de dependencia que vinculan a dichos elementos entre sí.
*   **Entorno o Medio Ambiente:** El conjunto de factores, agentes y magnitudes externas que se ubican fuera del perímetro del sistema pero ejercen una influencia directa o indirecta sobre su comportamiento interno.

La separación entre el sistema y su entorno queda formalmente establecida por una **frontera** (física o abstracta). Según la permeabilidad de esta frontera frente al intercambio de materia, energía o información, los sistemas se clasifican en:
*   **Sistemas Abiertos:** Intercambian insumos, flujos de información y perturbaciones de manera continua con el medio externo (por ejemplo, un centro de atención telefónica, un router en una red de comunicación o una sucursal bancaria).
*   **Sistemas Cerrados o Aislados:** Operan sin interacción apreciable con el entorno externo durante el horizonte de análisis de interés.

Los sucesos que se originan fuera de la frontera e irrumpen en el sistema modificando sus variables se denominan **eventos exógenos** (como la llegada espontánea de una solicitud de servicio), mientras que las interacciones internas se traducen en **eventos endógenos** (como la liberación de un servidor tras finalizar una tarea).

### 1.2. Abstracción y Clasificación Sistemática de Modelos
Debido a que la experimentación directa sobre un sistema real suele ser inviable por restricciones presupuestarias, riesgos operacionales o la inexistencia física del sistema en etapas de diseño, la investigación científica recurre al uso de **modelos**. Un modelo es una representación simplificada, abstracta y conceptual de un sistema real o hipotético, estructurada de tal forma que conserva las propiedades dinámicas y relaciones de causalidad críticas necesarias para responder preguntas analíticas específicas sobre el comportamiento del sistema original.

Desde el punto de vista formal, los modelos matemáticos expresan las leyes de funcionamiento mediante ecuaciones, desigualdades y relaciones lógicas que vinculan variables de entrada con medidas de respuesta o desempeño. Ackoff propone una formulación explícita para la estructura de un modelo analítico general:

$$U = f(X, Y)$$

Sujeta al conjunto de restricciones operacionales o físicas:

$$R_k(X, Y) \ (\le, =, \ge) \ b_k, \quad \forall k \in \{1, 2, \dots, K\}$$

Donde:
*   $U$ representa la función de respuesta, utilidad o medida de rendimiento del sistema (por ejemplo, el tiempo promedio de permanencia o la tasa de utilización de recursos).
*   $X = (X_1, X_2, \dots, X_n)$ es el vector de **variables controlables** o de decisión, cuyos valores pueden ser fijados deliberadamente por el analista (por ejemplo, la cantidad de servidores o la capacidad de almacenamiento en búfer).
*   $Y = (Y_1, Y_2, \dots, Y_m)$ es el vector de **variables no controlables** o estocásticas, impuestas por la naturaleza o el entorno del sistema (por ejemplo, las tasas de arribo o la duración de las tareas).
*   $R_k(X, Y)$ traduce las restricciones físicas, lógicas o presupuestarias asociadas a la frontera del sistema.

### 1.3. La Simulación como Método Numérico y Experimento Computacional
Cuando las ecuaciones constitutivas de un modelo matemático $f(X, Y)$ resultan excesivamente complejas, no lineales o incorporan múltiples fuentes interrelacionadas de incertidumbre estocástica, la obtención de una solución analítica en forma cerrada se vuelve matemáticamente intratable. En estas circunstancias, la **simulación computarizada** se constituye como el paradigma numérico por excelencia.

La simulación no es una técnica de optimización matemática directa, sino un **método numérico de experimentación sobre computadoras**. Consiste en construir un modelo lógico-matemático del sistema y ejecutarlo en el tiempo computacional, generando artificialmente la historia del sistema y recolectando observaciones muestrales de sus salidas para inferir el comportamiento estadístico del sistema real. La simulación opera conceptualmente bajo la arquitectura de una **caja negra**:

1.  **Entradas Estocásticas (Inputs):** Secuencias de números o variables aleatorias que alimentan el simulador representando la incertidumbre ambiental.
2.  **Mecanismo de Estado (Caja Negra):** Las reglas lógicas y ecuaciones que actualizan las variables del sistema en función del tiempo.
3.  **Medidas de Respuesta (Outputs):** Serie temporal de resultados que se someten a inferencia estadística para estimar parámetros de rendimiento.

### 1.4. Taxonomía Tridimensional de la Simulación: Tiempo, Incertidumbre y Estado
La caracterización rigurosa de cualquier modelo de simulación exige categorizar su comportamiento en función de tres ejes ortogonales de clasificación:

#### Eje Temporal: Estática frente a Dinámica
*   **Simulación Estática:** Representa un sistema en un punto específico y congelado del tiempo, o modela fenómenos donde el paso del tiempo carece de relevancia estructural. El método de Montecarlo clásico para el cálculo de áreas o integrales es el ejemplo representativo.
*   **Simulación Dinámica:** Representa la evolución y mutación de las variables del sistema a lo largo del paso continuo o discreto del tiempo.

#### Eje de Incertidumbre: Determinística frente a Estocástica
*   **Simulación Determinística:** No contiene elementos inciertos o aleatorios en sus variables de entrada. Para un conjunto dado de entradas, el modelo producirá siempre exactamente la misma trayectoria de salida.
*   **Simulación Estocástica:** Incorpora una o más variables de entrada de carácter aleatorio, regidas por funciones de densidad de probabilidad. En consecuencia, las salidas del modelo son también variables aleatorias, lo que exige tratar los resultados mediante muestras estadísticas e intervalos de confianza.

#### Eje de Estado: Continua frente a Discreta
*   **Simulación Continua:** Las variables de estado del sistema mutan de manera ininterrumpida y continua a lo largo del tiempo. Se modela típicamente mediante sistemas de ecuaciones diferenciales ordinarias o parciales:
    $$\frac{d\vec{S}(t)}{dt} = g(\vec{S}(t), \vec{X}(t), t)$$
*   **Simulación Discreta:** Las variables de estado permanecen absolutamente constantes durante intervalos continuos y sufren modificaciones discontinuas únicamente en instantes aislados y cuantificables del tiempo, denominados instantes de evento.

### 1.5. Fases Metodológicas Completa de un Proyecto de Simulación
El desarrollo riguroso de un proyecto de simulación no se reduce a la codificación de un programa computacional, sino que exige cumplir una secuencia ordenada de etapas metodológicas interconectadas:

1.  **Formulación del Problema y Definición de Objetivos:** Establecer con precisión las preguntas de decisión que debe responder el estudio, el nivel de detalle requerido y las métricas de evaluación de desempeño.
2.  **Planificación del Proyecto y Determinación del Alcance:** Asignar recursos, fijar límites temporales y definir las fronteras lógicas del modelo.
3.  **Conceptualización del Modelo:** Traducir la realidad observada en diagramas de flujo, redes de colas, tablas de estado o pseudocódigo que especifiquen las entidades, eventos y leyes de transición.
4.  **Relevamiento y Toma de Datos Empíricos:** Colectar datos de campo sobre las entradas del sistema para caracterizar estadísticamente los procesos de arribo y tiempos de operación.
5.  **Traducción del Modelo (Codificación):** Implementar el modelo conceptual en un lenguaje de programación de propósito general o en un software especializado de simulación de eventos discretos.
6.  **Verificación del Código:** Comprobar rigurosamente que la lógica computacional programada responde exactamente a las especificaciones del modelo conceptual (ausencia de errores de programación).
7.  **Validación del Modelo:** Demostrar que el modelo simula el comportamiento del sistema real con un grado de precisión y fidelidad suficiente para los propósitos del estudio.
8.  **Diseño Experimental:** Planificar las corridas de simulación, definiendo las condiciones iniciales, la longitud de la corrida (período de calentamiento o estado estacionario), la semilla de aleatoriedad y el número de réplicas necesarias.
9.  **Ejecución de Experimentación y Producción:** Correr el modelo bajo las configuraciones experimentales establecidas.
10. **Análisis Estadístico de Resultados:** Procesar las salidas mediante intervalos de confianza, pruebas de hipótesis o análisis de varianza (ANOVA) para responder las hipótesis planteadas.
11. **Documentación, Implementación y Toma de Decisiones:** Presentar las recomendaciones soportadas por evidencias cuantitativas y documentar el modelo para su mantenimiento futuro.

### 1.6. Relevamiento y Toma de Datos Empíricos: Muestreo, Tamaño y Sesgo
Los datos de entrada constituyen la materia prima fundamental que alimenta un modelo estocástico. La validez de los resultados de salida está estrictamente acotada por la calidad de las distribuciones de probabilidad ajustadas a los datos de campo.

Para llevar a cabo una toma de datos empíricos metodológicamente sólida, deben observarse los siguientes lineamientos:
*   **Independencia Muestral:** Garantizar que las observaciones individuales no presenten autocorrelación temporal ni dependencias espaciales que distorsionen los supuestos de variabilidad.
*   **Representatividad y Homogeneidad:** Asegurar que los datos sean recolectados bajo condiciones operacionales estables y representativas. Por ejemplo, en un sistema de servicio, agrupar datos de horarios pico y valles en una misma muestra generaría una distribución bimodal espuria.
*   **Control de Sesgos:** Evitar sesgos de selección provocados por mediciones en intervalos no aleatorizados o por imprecisiones en los instrumentos de medición.
*   **Determinación del Tamaño Muestral ($n$):** Para estimar la media de una variable de entrada con una precisión relativa dada $\epsilon$ y un nivel de confianza $1 - \alpha$, el tamaño muestral mínimo $n$ se calcula iterativamente mediante:
    $$n \ge \left( \frac{z_{\alpha/2} \cdot s}{\epsilon \cdot \bar{x}} \right)^2$$
    Donde $\bar{x}$ es la media muestral preliminar, $s$ es la desviación estándar muestral y $z_{\alpha/2}$ es el valor crítico de la distribución normal estándar.

---

## Segmento 2: Ontología y Mecánica Operativa de la Simulación de Eventos Discretos (SED)

### 2.1. Componentes Ontológicos: Entidades, Atributos, Variables de Estado, Recursos y Colas
La Simulación de Eventos Discretos (SED) descompone la estructura dinámica de un sistema continuo en una serie de componentes ontológicos estandarizados:

*   **Entidad (Entity):** Es cualquier objeto dinámico o individuo que transita por el sistema exigiendo una representación explícita. Las entidades son generadas en los módulos de entrada (*Create/Source*), experimentan procesamientos y demoras, y finalmente son destruidas en los módulos de salida (*Dispose/Sink*). Ejemplos: clientes en una fila, paquetes en una red IP, piezas en una línea de montaje.
*   **Atributo (Attribute):** Es un valor o propiedad local e individual que se adhiere directamente a una entidad específica y viaja con ella a lo largo de todo su recorrido por el modelo. Ejemplos: prioridad de atención de una entidad, hora de llegada al sistema (timestamp), tipo de servicio requerido.
*   **Variable de Estado (State Variable):** Es una magnitud global que pertenece al entorno del modelo y describe la condición cuantitativa del sistema en un instante de tiempo $t$. Su valor es compartido por todas las entidades y subsistemas. Ejemplos: número de clientes en el sistema en el instante $t$, estado funcional del servidor (ocupado/ocioso), longitud actual de la cola $N(t)$.
*   **Recurso (Resource):** Es un elemento estático del sistema que provee un servicio a las entidades. Los recursos poseen una capacidad finita $C$ y en un instante dado pueden estar en estado *Libre*, *Ocupado* o *Falla/Mantenimiento*.
*   **Cola (Queue / List):** Es una estructura de datos o contenedor donde las entidades que no pueden ser atendidas de forma inmediata por indisponibilidad de recursos quedan retenidas temporalmente. Las colas se organizan bajo disciplinas de servicio específicas:
    *   **FIFO / FCFS:** *First-In, First-Out* (atención por orden estricto de llegada).
    *   **LIFO / LCFS:** *Last-In, First-Out* (atención del último elemento ingresado).
    *   **PRIO:** Atención por nivel de prioridad prefijado en un atributo de la entidad.

### 2.2. Dinámica Bi-Temporal: Eventos Instantáneos frente a Actividades y Demoras
En SED, el progreso de la simulación está determinado por la interacción de tres conceptos temporales diferenciados:

1.  **Evento (Event):** Es un suceso de ocurrencia **instantánea** (de duración $t = 0$) que altera de forma discontinua el valor de una o más Variables de Estado del sistema. Los eventos marcan el inicio o la finalización de lapsos temporales. Ejemplos: el instante exacto en que llega un cliente, el momento en que se libera un servidor.
2.  **Actividad (Activity):** Es un período de procesamiento o espera cuya duración está **predeterminada y se conoce en el instante en que inicia**. Su duración se calcula evaluando una expresión matemática o generando un valor de una variable aleatoria de entrada. Ejemplos: el tiempo de servicio de una máquina de 5 minutos, el tiempo entre arribos generado por una distribución exponencial.
3.  **Demora (Delay / Waiting Time):** Es un período de espera de **duración indeterminada a priori**. Su finalización no depende de un tiempo prefijado, sino de la ocurrencia de eventos futuros en el sistema que satisfagan ciertas condiciones de activación (por ejemplo, el tiempo que un cliente permanece bloqueado en la cola aguardando que se libere un recurso).

### 2.3. Mecanismos de Avance del Reloj de Simulación: Next-Event Scheduling frente a Time-Slicing
El **Reloj de Simulación** ($T_{sim}$) es la variable global encargada de registrar el tiempo operacional acumulado dentro del modelo. Existen dos aproximaciones algorítmicas para gestionar el progreso de este reloj:

#### Avance por Evento Inminente (Next-Event Time-Advance o Next-Event Scheduling)
Es el algoritmo estándar empleado en SED. Dado que las variables de estado permanecen rigurosamente constantes entre eventos consecutivos, el reloj de simulación no avanza de forma continua, sino que realiza **saltos discretos** de duración variable directamente hacia el instante de ocurrencia del evento más inminente programado en la arquitectura del simulador.

**Pasos del Algoritmo:**
1.  Inicializar $T_{sim} = 0$ y programar los eventos iniciales en la Lista de Eventos Futuros (FEL).
2.  Extraer de la FEL el evento $E_{next}$ con el menor instante de ejecución $t_{next}$.
3.  Avanzar el reloj de simulación al instante del evento: $T_{sim} = t_{next}$.
4.  Ejecutar la rutina de servicio lógica correspondiente a $E_{next}$, actualizando las variables de estado, generando nuevos eventos futuros si corresponde e insertándolos en orden cronológico en la FEL.
5.  Repetir el ciclo hasta alcanzar la condición de parada predefinida.

#### Avance por Intervalos Fijos (Fixed-Increment Time-Advance o Time-Slicing)
El reloj de simulación avanza en incrementos constantes de magnitud fija $\Delta t$ ($T_{sim} \leftarrow T_{sim} + \Delta t$). En cada paso, el motor de simulación escanea el modelo para verificar si ocurrió algún evento dentro del intervalo $(T_{sim} - \Delta t, T_{sim}]$. 

**Desventajas frente a SED:** Si $\Delta t$ es muy grande, se introducen errores de cuantización temporal al desplazar artificialmente los eventos al final del intervalo, o se omiten múltiples eventos. Si $\Delta t$ es muy pequeño, se incurre en un costo computacional masivo escaneando períodos donde el sistema no experimenta cambios de estado.

### 2.4. Arquitectura del Simulador: Lista de Eventos Futuros (FEL) e Interrupciones Lógicas
El motor de ejecución de SED se articula en torno a una estructura de datos dinámica denominada **Lista de Eventos Futuros (FEL - Future Event List)**. La FEL funciona como una cola de prioridad ordenada de manera estrictamente creciente por el tiempo de ejecución de cada aviso de evento:

$$\text{FEL} = \{ E_1(t_1), E_2(t_2), \dots, E_m(t_m) \}, \quad \text{donde } t_1 \le t_2 \le \dots \le t_m$$

Cada registro en la FEL contiene como mínimo:
*   `Event_Type`: Identificador del tipo de evento (ej. Arribo, Fin de Servicio, Falla de Recurso).
*   `Event_Time`: Instante de tiempo programado para su disparo ($t_k \ge T_{sim}$).
*   `Associated_Entity`: Puntero a la entidad que originó o experimenta el evento.

La ejecución del simulador consiste en un bucle continuo de procesamiento donde el evento que encabeza la FEL ($E_1$) determina el siguiente estado del sistema. Si durante la ejecución de una rutina de evento una entidad toma posesión de un servidor, se calcula la duración de la actividad $D$ y se agenda inmediatamente un nuevo evento de *Fin de Servicio* en el instante $T_{sim} + D$, insertándolo ordenadamente en la FEL.

### 2.5. Verificación, Validación y Análisis de Acreditación del Modelo
El análisis de confiabilidad de un modelo de simulación requiere distinguir claramente entre dos procesos complementarios:

*   **Verificación:** Es el proceso de evaluar si el modelo computarizado programado funciona de acuerdo con las especificaciones del modelo conceptual. Responde a la pregunta: *¿Construimos el modelo correctamente?* Incluye la depuración del código, pruebas unitarias de bloques lógicos, verificación de balances de masa y entidades, y ejecuciones determinísticas bajo condiciones límite.
*   **Validación:** Es el proceso de determinar si el modelo conceptual y computacional representa el sistema real con suficiente fidelidad respecto a los objetivos del estudio. Responde a la pregunta: *¿Construimos el modelo correcto?*

**Técnicas de Validación:**
1.  **Validación de Criterio Experto (Face Validity):** Consulta a personal operativo y expertos del dominio para evaluar la verosimilitud de las salidas.
2.  **Pruebas de Hipótesis Estadísticas sobre Datos Históricos:** Comparación cuantitativa de los vectores de salida del simulador ($\vec{Y}_{sim}$) frente a mediciones reales del sistema ($\vec{Y}_{real}$) mediante la prueba $t$ de Student para muestras independientes o emparejadas:
    $$t_0 = \frac{\bar{Y}_{sim} - \bar{Y}_{real}}{s_p \sqrt{\frac{1}{n_1} + \frac{1}{n_2}}}$$
    O mediante la comparación de distribuciones empíricas mediante la prueba de Kolmogorov-Smirnov.
3.  **Análisis de Sensibilidad:** Evaluar si las respuestas del modelo ante variaciones graduales en los parámetros de entrada se comportan en la dirección y magnitud esperadas por la teoría del sistema real.

---

## Segmento 3: Generación de Números Pseudoaleatorios y Pruebas Estadísticas de Auditoría

### 3.1. Justificación de la Pseudoaleatoriedad: Reproducibilidad, Control y Reducción de Varianza
Todas las simulaciones estocásticas requieren de una fuente ininterrumpida de números aleatorios distribuidos uniformemente en el intervalo $(0, 1)$, denotados como $R_i \sim U(0,1)$, los cuales actúan como la materia prima para generar variables aleatorias no uniformes.

Aunque físicamente es posible capturar eventos verdaderamente aleatorios (TRNG - *True Random Number Generators*) a partir de fenómenos cuánticos o ruido térmico, en simulación computacional se utilizan exclusivamente **Generadores de Números Pseudoaleatorios (PRNG - Pseudorandom Number Generators)**. Un PRNG es un algoritmo determinístico que produce una secuencia de números que aparenta ser aleatoria y supera las pruebas estadísticas de uniformidad e independencia.

El uso de números pseudoaleatorios frente a la aleatoriedad física pura es indispensable por los siguientes motivos metodológicos:
1.  **Reproducibilidad Estricta:** Un PRNG genera su secuencia a partir de un valor inicial denominado **semilla** ($X_0$). Al fijar la misma semilla, el algoritmo reproduce de forma idéntica la misma secuencia numérica. Esto es crucial para la depuración del código computacional y la verificación del modelo.
2.  **Comparación de Alternativas bajo Condiciones Idénticas:** Permite someter dos o más configuraciones de diseño de un sistema exactamente a las mismas cargas de entrada estocásticas (mismos arribos y tiempos de atención), garantizando que las diferencias observadas en el rendimiento se deban a los cambios de diseño y no al ruido del azar.
3.  **Técnicas de Reducción de Varianza:** Es la base para aplicar métodos estadísticos avanzados como **Variables Aleatorias Comunes (CRN)** o **Variables Antitéticas**, los cuales requieren un control determinístico sobre la corriente de números aleatorios para inducir correlaciones intencionales que reduzcan la varianza de las estimadores finales.

### 3.2. Algoritmos Heurísticos Clásicos y sus Degeneraciones Patológicas
Los primeros intentos de generación computacional de aleatoriedad se basaron en procedimientos heurísticos aritméticos simples sobre los dígitos de los números:

*   **Método de los Cuadrados Medios (Middle-Square Method):** Propuesto por John von Neumann. Toma un número inicial de $n$ dígitos ($X_0$), lo eleva al cuadrado produciendo una cifra de hasta $2n$ dígitos, y extrae los $n$ dígitos centrales para formar $X_1$.
    $$R_1 = \frac{X_1}{10^n}$$
*   **Método del Producto Medio:** Utiliza dos semillas $X_0$ y $X_1$ de $n$ dígitos. Las multiplica entre sí y extrae los $n$ dígitos centrales del resultado para obtener $X_2$.

**Degeneraciones Patológicas de los Métodos Heurísticos:**
Estos generadores son absolutamente obsoletos para la simulación moderna debido a graves fallas estructurales:
1.  **Agotamiento y Colapso a Cero:** Frecuentemente generan valores que al elevarse al cuadrado producen ceros en los dígitos centrales (por ejemplo, $0000$), bloqueando indefinidamente al generador en $0$.
2.  **Ciclos de Repetición Extremadamente Cortos:** Entran rápidamente en bucles cerrados de pequeña longitud, repitiendo de forma determinística secuencias de 3 o 4 números.
3.  **Presencia de Autocorrelación Severa:** Las secuencias muestran patrones espaciales y correlaciones estadísticas manifiestas.

### 3.3. Generadores Congruenciales Lineales (GCL): Mixtos y Multiplicativos
Los Generadores Congruenciales Lineales (GCL), formulados por Lehmer, utilizan la aritmética modular para calcular secuencias de números enteros pseudoaleatorios.

#### Generador Congruencial Lineal Mixto
La relación de recurrencia está dada por:

$$X_{n+1} = (a \cdot X_n + c) \pmod m, \quad n = 0, 1, 2, \dots$$

$$R_{n+1} = \frac{X_{n+1}}{m}$$

Donde:
*   $m$: El módulo del generador ($m > 0$).
*   $a$: El multiplicador ($0 \le a < m$).
*   $c$: La constante aditiva o incremento ($0 \le c < m$).
*   $X_0$: La semilla inicial ($0 \le X_0 < m$).

#### Generador Congruencial Multiplicativo
Es un caso especial del algoritmo congruencial donde la constante aditiva es nula ($c = 0$):

$$X_{n+1} = (a \cdot X_n) \pmod m$$

#### Teorema de Hull-Dobell (Condiciones de Período Completo)
El período de un generador es la cantidad de números generados antes de que la secuencia comience a repetirse. Como la operación módulo produce enteros en el conjunto $\{0, 1, \dots, m-1\}$, el período máximo teórico es $P = m$. 

El **Teorema de Hull-Dobell** establece que un GCL Mixto alcanzará un período completo igual a $m$ si y solo si se satisfacen simultáneamente las siguientes tres condiciones algebraicas:
1.  $c$ y $m$ son relativamente primos (su máximo común divisor es $\gcd(c, m) = 1$).
2.  Si $q$ es un número primo que divide a $m$, entonces $q$ divide a $(a - 1)$ [es decir, $(a - 1)$ es múltiplo de todos los factores primos de $m$].
3.  Si $4$ divide a $m$, entonces $4$ divide a $(a - 1)$.

Para un GCL Multiplicativo ($c=0$), el período máximo posible es $P = m - 1$ (si $m$ es primo) o $P = m/4$ (si $m = 2^b$), siempre que la semilla $X_0$ sea coprima con $m$.

### 3.4. Algoritmos de Grado Industrial: Mersenne Twister (MT19937), MRG y Lagged Fibonacci
Las limitaciones de los GCL en términos de período y correlaciones multidimensionales llevaron al desarrollo de generadores modernos de grado industrial:

*   **Mersenne Twister (MT19937):** Desarrollado por Matsumoto y Nishimura (1998). Es el generador estándar en entornos computacionales como MATLAB, Python, R y C++. Se basa en una recurrencia matricial sobre un espacio vectorial binario Galois $GF(2)$.
    *   **Período:** Es un número primo de Mersenne astronómico de $P = 2^{19937} - 1 \approx 4.3 \times 10^{6001}$.
    *   **Equidistribución Multidimensional:** Garantiza una distribución uniforme comprobada estadísticamente en hasta **623 dimensiones** para números de precisión doble (64 bits), eliminando los problemas de estructura de hiperplanos de los GCL.
*   **Generadores Multi-Recursivos (MRG - Multiple Recursive Generators):** Combinan múltiples términos pasados de la secuencia para calcular el nuevo estado:
    $$X_n = \left( a_1 X_{n-1} + a_2 X_{n-2} + \dots + a_k X_{n-k} \right) \pmod m$$
    Alcanzan períodos de $m^k - 1$ y excelentes propiedades estadísticas.
*   **Generadores de Fibonacci con Retraso (Lagged Fibonacci):** Utilizan la operación:
    $$X_n = \left( X_{n-r} \otimes X_{n-s} \right) \pmod m, \quad r > s$$
    Donde $\otimes$ representa un operador binario como la suma, la multiplicación o la función lógica XOR ($bit-wise$).

### 3.5. Pruebas Estadísticas de Rigor: Promedios, Frecuencias ($\chi^2$), Series y Distancias
Toda secuencia de números pseudoaleatorios $R_1, R_2, \dots, R_N$ propuesta para una simulación debe ser auditada mediante pruebas de hipótesis estadísticas para verificar la **Hipótesis Nula ($H_0$)**: *Los números están distribuidos uniformemente e de manera independiente ($R_i \sim \text{i.i.d. } U(0,1)$)*.

#### 1. Prueba de Promedios (Media Estadísticas)
Evalúa si el valor esperado de la muestra generada coincide con la media teórica de una variable uniforme $\mu = E[R] = 0.5$.

*   **Estadístico de Prueba:**
    $$\bar{R} = \frac{1}{N} \sum_{i=1}^{N} R_i$$
*   **Zona de Aceptación:** Bajo $H_0$, la variable $\bar{R}$ se distribuye normalmente con varianza $\sigma^2 = 1/(12N)$. Se acepta $H_0$ con un nivel de significancia $\alpha$ si:
    $$-z_{\alpha/2} \le Z_0 \le z_{\alpha/2}, \quad \text{donde } Z_0 = \frac{\bar{R} - 0.5}{\sqrt{1 / (12N)}}$$

#### 2. Prueba de Frecuencias (Chi-Cuadrado $\chi^2$)
Evalúa la propiedad de uniformidad dividiendo el intervalo $(0, 1)$ en $k$ subintervalos de igual amplitud $\Delta = 1/k$.

*   **Frecuencia Esperada por intervalo:** $FE_i = \frac{N}{k}$ (se requiere $FE_i \ge 5$).
*   **Estadístico de Prueba:**
    $$\chi_0^2 = \sum_{i=1}^{k} \frac{(FO_i - FE_i)^2}{FE_i} = \frac{k}{N} \sum_{i=1}^{k} \left( FO_i - \frac{N}{k} \right)^2$$
    Donde $FO_i$ es la frecuencia observada de números que cayeron en el subintervalo $i$.
*   **Criterio de Decisión:** Se no rechaza la uniformidad si $\chi_0^2 < \chi_{\alpha, k-1}^2$.

#### 3. Prueba de Series (Pares Sucesivos)
Audita la independencia analizando la uniformidad espacial bidimensional de pares de números consecutivos $(R_i, R_{i+1})$.
*   Se divide el cuadrado unitario $(0,1) \times (0,1)$ en una grilla de $k \times k = k^2$ celdas cuadradas de igual área.
*   Se contabiliza la frecuencia $FO_{ij}$ de los $N-1$ pares ordenados que caen en cada celda $(i, j)$.
*   El estadístico computado se compara contra una distribución $\chi^2$ con $k^2 - 1$ grados de libertad:
    $$\chi_0^2 = \frac{k^2}{N-1} \sum_{i=1}^{k} \sum_{j=1}^{k} \left( FO_{ij} - \frac{N-1}{k^2} \right)^2$$

#### 4. Prueba de la Distancia (Huecos / Gap Test)
Evalúa la independencia analizando la cantidad de números que se generan entre dos apariciones consecutivas de números que caen dentro de un intervalo específico $[\alpha, \beta] \subset (0, 1)$.

### 3.6. Auditoría mediante Baterías de Pruebas Compuestas (TestU01)
En la práctica profesional moderna, las pruebas individuales no son suficientes para certificar un generador. Se recurre a **baterías de auditoría empírica pesada**, entre las cuales **TestU01** (desarrollada por L'Ecuyer y Simard) representa el estándar de oro de la industria.

TestU01 somete a los generadores a tres baterías progresivas de rigor extremo:
1.  **SmallCrush:** Aplica 10 pruebas estadísticas rápidas consumiendo cerca de $10^7$ números aleatorios.
2.  **Crush:** Aplica 96 pruebas complejas sobre $10^{10}$ números aleatorios.
3.  **BigCrush:** Aplica 106 pruebas estadísticas de nivel crítico consumiendo más de $10^{11}$ números pseudoaleatorios, evaluando estructuras de reticulado, complejidad lineal y caminatas aleatorias.

Algoritmos clásicos como los GCL fallan masivamente en la batería *Crush*, mientras que el *Mersenne Twister* y los generadores *MRG32k3a* superan la totalidad de las pruebas de *BigCrush*.

---

## Segmento 4: Métodos Estocásticos de Transformación de Variables Aleatorias

### 4.1. Fundamentación del Consumo de Variables Uniformes como Materia Prima
Las variables que representan la incertidumbre de un sistema (tiempos de servicio, demoras, fallas) no suelen seguir distribuciones uniformes, sino distribuciones continuas o discretas no uniformes (Exponencial, Normal, Weibull, Poisson, etc.). 

El objetivo de este módulo es transformar una secuencia de números pseudoaleatorios uniformes $R \sim U(0, 1)$ en una variable aleatoria $X$ cuya función de densidad de probabilidad $f(x)$ o función de masa de probabilidad $p(x)$ coincida exactamente con la distribución objetivo deseada.

### 4.2. Método de la Transformada Inversa (Continua y Discreta)
Es el método directo más importante cuando la función de distribución acumulada (FDA) de la variable aleatoria $X$, definida como:

$$F(x) = P(X \le x) = \int_{-\infty}^{x} f(t) \, dt$$

posee una función inversa $F^{-1}$ que admite un despeje analítico explícito.

#### Fundamento Matemático (Teorema de la Transformación Integral de Probabilidad)
Sea $X$ una variable aleatoria continua con FDA $F(x)$ strictly creciente. Si $X$ se evalúa en su propia acumulada, la variable resultante $U = F(X)$ sigue rigurosamente una distribución uniforme en el intervalo $(0, 1)$. 

Por consiguiente, si se genera un número uniforme $R \sim U(0,1)$ y se iguala a la FDA:

$$R = F(X)$$

Se puede aplicar la función inversa para obtener la muestra simulada:

$$X = F^{-1}(R)$$

#### Ejemplo Derivado 1: Generación de una Variable Aleatoria Exponencial
Dada una variable exponencial de tasa $\lambda > 0$, con función de densidad $f(x) = \lambda e^{-\lambda x}$ para $x \ge 0$.
1.  Calcular la FDA:
    $$F(x) = \int_{0}^{x} \lambda e^{-\lambda t} \, dt = 1 - e^{-\lambda x}$$
2.  Igualar a $R \sim U(0,1)$:
    $$R = 1 - e^{-\lambda X}$$
3.  Despejar $X$:
    $$1 - R = e^{-\lambda X} \implies \ln(1 - R) = -\lambda X \implies X = -\frac{1}{\lambda} \ln(1 - R)$$
    Dado que si $R \sim U(0,1)$ entonces $(1-R)$ sigue numéricamente la misma distribución $U(0,1)$, la ecuación computacional equivalente es:
    $$X = -\frac{1}{\lambda} \ln(R)$$

#### Ejemplo Derivado 2: Generación de una Variable Aleatoria Uniforme $U(a, b)$
$$F(x) = \frac{x - a}{b - a} = R \implies X = a + (b - a)R$$

#### Caso Discreto (Inversión por Búsqueda en Tablas)
Si $X$ es discreta con valores $x_1, x_2, \dots$ y probabilidades $p(x_i) = P(X = x_i)$, se calculan las probabilidades acumuladas $P_k = \sum_{i=1}^{k} p(x_i)$. Se genera $R \sim U(0,1)$ y se asigna el valor $X = x_k$ tal que:

$$P_{k-1} < R \le P_k \quad (\text{definiendo } P_0 = 0)$$

### 4.3. Método de Composición y Mezclas de Distribuciones
El método de composición se aplica cuando la función de densidad de probabilidad $f(x)$ de la variable objetivo es compleja, pero puede descomponerse como una combinación lineal (mezcla) de $n$ funciones de densidad $f_i(x)$ más sencillas de simular:

$$f(x) = \sum_{i=1}^{n} w_i f_i(x), \quad \text{donde } w_i > 0 \quad \text{y} \quad \sum_{i=1}^{n} w_i = 1$$

Donde $w_i$ representa la probabilidad o ponderación de que la variable sea generada a partir de la subdensidad $f_i(x)$.

**Algoritmo de Composición (Requiere al menos 2 números uniformes):**
1.  Generar un primer número aleatorio $R_1 \sim U(0,1)$ para seleccionar cuál de las subdistribuciones $f_i(x)$ se activará.
2.  Determinar el índice $k$ tal que:
    $$\sum_{j=1}^{k-1} w_j < R_1 \le \sum_{j=1}^{k} w_j$$
3.  Generar un segundo número aleatorio $R_2 \sim U(0,1)$ y utilizarlo para obtener la muestra $X$ a partir de la subdensidad seleccionada $f_k(x)$ (por ejemplo, aplicando la transformada inversa sobre $F_k^{-1}(R_2)$).

### 4.4. Método de Convolución y Teorema Central del Límite
Se aplica cuando la variable aleatoria objetivo $X$ se puede expresar matemáticamente como la suma lineal de $k$ variables aleatorias independientes $Y_1, Y_2, \dots, Y_k$:

$$X = \sum_{i=1}^{k} Y_i$$

En lugar de invertir la distribución acumulada compleja de $X$, el algoritmo genera $k$ muestras individuales de las variables simples $Y_i$ (utilizando números $R_i$) y calcula su suma.

#### Caso 1: Generación de una Variable Erlang-$k$
Una variable aleatoria Erlang con parámetros de forma $k$ (entero) y tasa $\lambda$ es por definición la suma de $k$ variables aleatorias exponenciales independientes de tasa $\lambda$.
Dado que cada variable exponencial se simula como $Y_i = -\frac{1}{\lambda} \ln(R_i)$, por convolución:

$$X = \sum_{i=1}^{k} \left( -\frac{1}{\lambda} \ln(R_i) \right) = -\frac{1}{\lambda} \ln\left( \prod_{i=1}^{k} R_i \right)$$

#### Caso 2: Generación Normal Estándar por Teorema Central del Límite
Por el Teorema Central del Límite, la suma de $k$ variables uniformes independientes $R_i \sim U(0,1)$ tiende a una distribución normal. Si se eligen exactamente $k = 12$ variables uniformes:
Dado que para $U(0,1)$, $E[R] = 1/2$ y $Var(R) = 1/12$. La suma de 12 uniformes tiene media $\mu = 12 \cdot (1/2) = 6$ y varianza $\sigma^2 = 12 \cdot (1/12) = 1$.
Por lo tanto, se puede aproximar una variable normal estándar $Z \sim N(0,1)$ mediante:

$$Z = \sum_{i=1}^{12} R_i - 6$$

### 4.5. Método de Aceptación y Rechazo de Von Neumann
Se utiliza para simular variables aleatorias cuyas funciones de densidad de probabilidad $f(x)$ no admiten una transformada inversa analítica y no pueden ser descompuestas fácilmente por convolución o composición.

Sea $X$ una variable con densidad $f(x)$ acotada definida en un dominio $D$. Supóngase que existe una función de densidad proponedora o envolvente $g(x)$ y una constante $c \ge 1$ tales que:

$$f(x) \le c \cdot g(x), \quad \forall x \in D$$

**Algoritmo de Aceptación y Rechazo:**
1.  Generar una variable aleatoria candidata $Y$ que siga la densidad proponedora $g(x)$.
2.  Generar un número aleatorio uniforme $R \sim U(0, 1)$ independiente de $Y$.
3.  **Prueba de Aceptación:** Evaluar la condición:
    $$R \le \frac{f(Y)}{c \cdot g(Y)}$$
4.  Si la condición se satisface, **aceptar** y hacer $X = Y$.
5.  Si la condición falla, **rechazar** el valor candidato $Y$, descartar $R$ y regresar al paso 1 las veces que sea necesario.

**Eficiencia del Método:**
La probabilidad de aceptar un candidato en cualquier intento es $P(\text{Aceptación}) = 1/c$. El número de intentos requeridos hasta obtener una muestra válida sigue una distribución geométrica con media igual a $c$. Por ende, para maximizar la velocidad computacional se debe seleccionar una envolvente $g(x)$ tal que la constante $c$ sea lo más cercana a $1$ posible.

### 4.6. Mapeo de Distribuciones Clave
El siguiente cuadro resume las características de las distribuciones utilizadas en modelos de simulación:

| Distribución | Función / Expresión Matemática | Método de Generación Estándar | Campo de Aplicación Principal en Simulación |
| :--- | :--- | :--- | :--- |
| **Uniforme $U(a,b)$** | $f(x) = \frac{1}{b-a}, \quad x \in [a,b]$ | Inversión: $X = a + (b-a)R$ | Ausencia de datos; incertidumbre máxima acotada. |
| **Exponencial** | $f(x) = \lambda e^{-\lambda x}, \quad x \ge 0$ | Inversión: $X = -\frac{1}{\lambda}\ln(R)$ | Tiempos entre arribos (Poisson); tiempos de falla. |
| **Erlang-$k$** | $f(x) = \frac{\lambda^k x^{k-1} e^{-\lambda x}}{(k-1)!}$ | Convolución: $X = -\frac{1}{\lambda}\ln\left(\prod R_i\right)$ | Tiempos de servicio por etapas ordenadas. |
| **Normal $N(\mu, \sigma)$** | $f(x) = \frac{1}{\sigma\sqrt{2\pi}} e^{-\frac{(x-\mu)^2}{2\sigma^2}}$ | Box-Muller / Aceptación-Rechazo | Procesos de alto volumen de agregación. |
| **Poisson** | $p(x) = \frac{e^{-\lambda} \lambda^x}{x!}, \quad x \in \mathbb{N}_0$ | Convolución de uniformes (conteo) | Cantidad de arribos en un intervalo fijo $\Delta t$. |
| **Empírica (Piecewise)** | Interpolación lineal por tramos de FDA | Inversión sobre la FDA acumulada | Datos de campo que no ajustan a distribuciones teóricas. |

### 4.7. Procedimiento Estadístico de Ajuste de Distribuciones: Histogramas, AIC, BIC y Pruebas de Bondad de Ajuste
Cuando se dispone de una muestra empírica $x_1, x_2, \dots, x_n$ recolectada en el sistema real, el proceso metodológico para seleccionar la variable aleatoria teórica incluye cuatro pasos:

1.  **Construcción de Histogramas y Diagnóstico Visual:** Inspeccionar la simetría, sesgo y número de modas para seleccionar candidatos teóricos potenciales (ej. Exponencial, Gamma, Log-Normal).
2.  **Estimación de Parámetros:** Calcular los estimadores de máxima verosimilitud (MLE) para cada distribución candidata.
3.  **Criterios de Información para Selección de Modelos:** Comparar los candidatos utilizando métricas de penalización por complejidad de parámetros:
    *   **Criterio de Información de Akaike (AIC):**
        $$\text{AIC} = 2k - 2\ln(\hat{L})$$
    *   **Criterio de Información Bayesiano (BIC):**
        $$\text{BIC} = k\ln(n) - 2\ln(\hat{L})$$
        Donde $k$ es el número de parámetros ajustados y $\hat{L}$ es el valor máximo de la función de verosimilitud. Se selecciona el modelo que minimice estos criterios.
4.  **Pruebas de Bondad de Ajuste:**
    *   **Prueba Chi-Cuadrado ($\chi^2$):** Se aplica agrupando datos en $k$ intervalos de clase. Se calcula $\chi_0^2 = \sum \frac{(FO_i - FE_i)^2}{FE_i}$ y se rechaza la distribución si $\chi_0^2 > \chi_{\alpha, k - p - 1}^2$, donde $p$ es el número de parámetros estimados.
    *   **Prueba de Kolmogorov-Smirnov (K-S):** Es una prueba continua no paramétrica basada en la máxima diferencia absoluta entre la FDA empírica $F_n(x)$ y la FDA teórica propuesta $F_0(x)$:
        $$D_n = \sup_{x} |F_n(x) - F_0(x)|$$
        Se rechaza el ajuste si $D_n$ supera el valor crítico especificado para el tamaño muestral $n$.

---

## Segmento 5: Simulación Estática y el Método de Montecarlo

### 5.1. Concepto Fundamental y la Ley de los Grandes Números
El **Método de Montecarlo** comprende un conjunto de técnicas estadísticas y numéricas que utilizan muestras de números pseudoaleatorios para resolver problemas matemáticos, probabilísticos y físicos complejos.

A diferencia de la SED, el método de Montecarlo clásico corresponde a una **simulación estática**: el tiempo no interviene como una variable de estado y el orden cronológico de las ejecuciones no altera el resultado final. Cada iteración representa una muestra independiente de un experimento probabilístico.

El sustento matemático de Montecarlo radica en la **Ley Fuerte de los Grandes Números**. Sea $X_1, X_2, \dots, X_n$ una secuencia de variables aleatorias independientes e idénticamente distribuidas (i.i.d.) con valor esperado finito $E[X] = \mu$. Entonces, el promedio muestral converge casi seguramente (con probabilidad 1) hacia la media teórica a medida que el tamaño muestral tiende a infinito:

$$P\left( \lim_{n \to \infty} \bar{X}_n = \mu \right) = 1, \quad \text{donde } \bar{X}_n = \frac{1}{n} \sum_{i=1}^{n} X_i$$

### 5.2. Deducción Matemática Rigurosa de la Inversión de Densidades Acumuladas
Sea $R$ una variable aleatoria uniforme en $(0,1)$ con función de densidad $f_R(r) = 1$ para $r \in (0,1)$. Se busca transformar $R$ en una variable $Y$ con función de densidad de probabilidad objetivo $g(y)$ mediante una función continua y strictly creciente $y = h(R)$.

Por el principio de conservación de la masa de probabilidad:

$$P(R \le r) = P(Y \le h(r))$$

Expresando la probabilidad en términos de las funciones de distribución acumulada:

$$\int_{0}^{r} f_R(t) \, dt = \int_{-\infty}^{h(r)} g(y) \, dy$$

Dado que $\int_{0}^{r} 1 \, dt = r$, y la integral de la derecha es por definición la FDA acumulada de $Y$, denotada como $G(y)$:

$$r = G(h(r))$$

Aplicando la función inversa $G^{-1}$ a ambos miembros de la ecuación:

$$h(r) = G^{-1}(r) \implies Y = G^{-1}(R)$$

Queda rigurosamente demostrado que para simular cualquier variable aleatoria continua $Y$ con densidad $g(y)$, basta con aplicar la inversa de su función acumulada $G^{-1}$ sobre un número aleatorio uniforme $R$.

### 5.3. Integración Numérica por Montecarlo: Aceptación/Rechazo y Crude Monte Carlo
El método de Montecarlo es ampliamente utilizado para calcular el valor numérico de integrales definidas multidimensionales de la forma:

$$I = \int_{a}^{b} g(x) \, dx$$

#### Aproximación por Aceptación y Rechazo (Hit-or-Miss Monte Carlo)
Consiste en encerrar geométricamente la función $g(x)$ dentro de un rectángulo de base $(b-a)$ y altura $c \ge \max_{x \in [a,b]} g(x)$, con área total $A_{box} = c(b-a)$.
1.  Generar dos números aleatorios $R_1, R_2 \sim U(0,1)$ en cada iteraciones $i = 1, \dots, n$.
2.  Calcular las coordenadas del dardo aleatorio:
    $$X_i = a + (b-a)R_{1,i}, \quad Y_i = c \cdot R_{2,i}$$
3.  Evaluar la prueba de acierto: si $Y_i \le g(X_i)$, se incrementa el contador de aciertos $m$.
4.  La integral se aproxima por la proporción de aciertos sobre el área total:
    $$\hat{I} = A_{box} \cdot \left( \frac{m}{n} \right) = c(b-a) \frac{m}{n}$$

#### Aproximación por Media Muestral (Crude Monte Carlo)
Reescribe la integral dividiendo y multiplicando por la longitud del intervalo $(b-a)$:

$$I = (b-a) \int_{a}^{b} g(x) \left( \frac{1}{b-a} \right) \, dx = (b-a) \cdot E[g(X)]$$

Donde $X \sim U(a,b)$ es una variable aleatoria uniforme en $[a,b]$.

**Algoritmo de Crude Monte Carlo:**
1.  Generar $n$ números uniformes $R_i \sim U(0,1)$.
2.  Transformarlos al intervalo $[a,b]$ haciendo $X_i = a + (b-a)R_i$.
3.  Evaluar la función en cada punto $Y_i = g(X_i)$.
4.  Estimar la integral mediante la media aritmética muestral:
    $$\hat{I}_{crude} = (b-a) \cdot \bar{Y} = \frac{b-a}{n} \sum_{i=1}^{n} g(X_i)$$

Por el Teorema Central del Límite, el error de estimación de este método decrece a una tasa de $O(1/\sqrt{n})$, lo que lo hace computacionalmente superior a las reglas de integración numéricas clásicas (como Trapezoidal o Simpson) cuando se integran funciones en altas dimensiones ($d > 4$).

### 5.4. Aplicaciones Determinísticas y Estocásticas
El método de Montecarlo abarca tanto la resolución probabilística de problemas determinísticos como la evaluación de modelos de riesgo estocásticos:

*   **Estimación Geométrica Determinística ($\pi$):** Inscribiendo un círculo de radio $r=1$ dentro de un cuadrado de lado $L=2$ (área $A_{sq} = 4$). La proporción teórica de áreas es $\frac{A_{circle}}{A_{sq}} = \frac{\pi \cdot 1^2}{4} = \frac{\pi}{4}$. Disparando $n$ puntos aleatorios $(X_i, Y_i)$ uniformes en $[-1, 1] \times [-1, 1]$ y contando cuántos satisfacen la condición de pertenencia al círculo $X_i^2 + Y_i^2 \le 1$ ($m$ aciertos), la constante se estima como:
    $$\hat{\pi} \approx 4 \cdot \frac{m}{n}$$
*   **Gestión de Proyectos (PERT/CPM Estocástico):** En lugar de tratar la duración de las tareas como valores fijos determinísticos, se asigna a cada actividad una distribución de probabilidad (por ejemplo, Triangular o Beta PERT). El método de Montecarlo ejecuta miles de iteraciones del proyecto, muestreando en cada corrida las duraciones de las tareas y calculando la ruta crítica. Como resultado, se obtiene la distribución de probabilidad completa del tiempo total de finalización del proyecto y la probabilidad porcentual de cumplir con una fecha límite dada.

---

## Segmento 6: Procesos Estocásticos, Cadenas de Markov y Procesos de Renovación

### 6.1. Definición Formal de Proceso Estocástico y Espacio de Estados
Un **proceso estocástico** se define matemáticamente como una colección de variables aleatorias $\{X(t), t \in T\}$, parametrizadas por una variable de índice $t$ que representa típicamente el tiempo, todas definidas sobre un mismo espacio de probabilidad $(\Omega, \mathcal{F}, P)$.

*   **Espacio de Estados ($S$):** Es el conjunto de todos los posibles valores o estados que puede adoptar la variable aleatoria $X(t)$. Si $S$ es un conjunto discreto (numerable), el proceso es de estado discreto.
*   **Conjunto de Índice ($T$):** Si $T = \{0, 1, 2, \dots\}$, se trata de un proceso en **tiempo discreto**, denotado como $\{X_n, n \in \mathbb{N}_0\}$. Si $T = [0, \infty)$, se trata de un proceso en **tiempo continuo**, denotado como $\{X(t), t \ge 0\}$.

### 6.2. Cadenas de Markov en Tiempo Discreto (DTMC) y Tiempo Continuo (CTMC)
Una **Cadena de Markov** es un proceso estocástico en el cual la distribución de probabilidad de los estados futuros depende única y exclusivamente del estado presente del sistema, siendo completamente independiente de la historia pasada de transiciones.

#### Cadena de Markov en Tiempo Discreto (DTMC)
Un proceso discreto $\{X_n, n = 0, 1, 2, \dots\}$ posee la **Propiedad de Markov** si para todo orden $n$ y cualquier secuencia de estados $i_0, i_1, \dots, i_{n-1}, i, j \in S$:

$$P(X_{n+1} = j \mid X_n = i, X_{n-1} = i_{n-1}, \dots, X_0 = i_0) = P(X_{n+1} = j \mid X_n = i)$$

Si estas probabilidades son independientes del tiempo $n$ (estacionarias en el tiempo), se definen las **Probabilidades de Transición en un Paso**:

$$p_{ij} = P(X_{n+1} = j \mid X_n = i)$$

Las cuales se organizan en una **Matriz de Transición Estocástica $\mathbf{P}$**:

$$\mathbf{P} = \begin{bmatrix} p_{00} & p_{01} & p_{02} & \dots \\ p_{10} & p_{11} & p_{12} & \dots \\ \vdots & \vdots & \vdots & \ddots \end{bmatrix}, \quad \text{donde } p_{ij} \ge 0 \quad \text{y} \quad \sum_{j \in S} p_{ij} = 1, \, \forall i$$

#### Cadena de Markov en Tiempo Continuo (CTMC)
Un proceso continuo $\{X(t), t \ge 0\}$ es una CTMC si para todo $s, t \ge 0$ y estados $i, j, x(u) \in S$:

$$P(X(t+s) = j \mid X(s) = i, X(u) = x(u), 0 \le u < s) = P(X(t+s) = j \mid X(s) = i)$$

En una CTMC, la cantidad de tiempo que el sistema permanece en un estado $i$ antes de hacer una transición hacia otro estado debe distribuirse de forma obligatoria según una **variable aleatoria exponencial**.

### 6.3. Propiedad Markoviana (Olvido / Ausencia de Memoria) en la Distribución Exponencial
La distribución exponencial es la **única distribución de probabilidad continua** que posee la **Propiedad de Falta de Memoria (Memoryless Property)**.

#### Demostración Matemática Rigurosa
Sea $T$ una variable aleatoria continua exponencial con función de densidad $f(t) = \lambda e^{-\lambda t}$ y función de distribución acumulada $F(t) = 1 - e^{-\lambda t}$, para $t \ge 0$. La probabilidad de que $T$ supere una duración $t$ es la función de supervivencia $P(T > t) = 1 - F(t) = e^{-\lambda t}$.

Se busca evaluar la probabilidad condicional de que el proceso transcurra una duración adicional $t$, dado que ya ha transcurrido un tiempo acumulado $s$:

$$P(T > s + t \mid T > s) = \frac{P(T > s + t \cap T > s)}{P(T > s)}$$

Dado que el evento $T > s + t$ es un subconjunto estricto del evento $T > s$, la intersección de ambos eventos es simplemente $P(T > s + t)$:

$$P(T > s + t \mid T > s) = \frac{P(T > s + t)}{P(T > s)} = \frac{e^{-\lambda(s + t)}}{e^{-\lambda s}} = \frac{e^{-\lambda s} \cdot e^{-\lambda t}}{e^{-\lambda s}} = e^{-\lambda t} = P(T > t)$$

Queda demostrado que la probabilidad condicional remanente $P(T > s + t \mid T > s)$ es exactamente igual a la probabilidad marginal inicial $P(T > t)$, ignorando por completo el tiempo transcurrido $s$.

### 6.4. Procesos de Conteo de Poisson y su Dualidad con los Intervalos Exponenciales
Un **Proceso de Poisson** con tasa constante $\lambda > 0$ es un proceso estocástico de conteo $\{N(t), t \ge 0\}$, donde $N(t)$ representa la cantidad total de eventos ocurridos dentro del intervalo temporal $[0, t]$.

#### Axiomas Definitorios de un Proceso de Poisson
1.  $N(0) = 0$.
2.  **Incrementos Independientes:** El número de eventos que ocurren en intervalos de tiempo disjuntos son variables aleatorias estadísticamente independientes.
3.  **Incrementos Estacionarios:** La distribución de probabilidad del número de eventos que ocurren en cualquier intervalo de tiempo depende únicamente de la longitud del intervalo $\Delta t$ y no de su posición absoluta en el tiempo.
4.  **Proporcionalidad e Infinitesimalidad:**
    *   $P(N(t + \Delta t) - N(t) = 1) = \lambda \Delta t + o(\Delta t)$
    *   $P(N(t + \Delta t) - N(t) \ge 2) = o(\Delta t)$
    *(Donde $o(\Delta t)$ representa una función de orden inferior tal que $\lim_{\Delta t \to 0} \frac{o(\Delta t)}{\Delta t} = 0$).*

A partir de estos axiomas, la variable aleatoria $N(t)$ sigue una **Distribución de Poisson** de parámetro $\mu = \lambda t$:

$$P(N(t) = k) = \frac{(\lambda t)^k e^{-\lambda t}}{k!}, \quad k = 0, 1, 2, \dots$$

Con valor esperado $E[N(t)] = \lambda t$ y varianza $Var(N(t)) = \lambda t$.

#### Dualidad Fundamental con la Distribución Exponencial
Sean $A_1, A_2, \dots$ los tiempos entre arribos consecutivos (inter-arribos) de un proceso de conteo $N(t)$. Existe una relación de equivalencia dual estricta:

$$\text{El proceso de conteo } N(t) \text{ es de Poisson de tasa } \lambda \iff \text{Los tiempos entre arribos } A_i \text{ son i.i.d. Exponenciales de tasa } \lambda$$

#### Implicancia Metodológica Crítica
Para validar empíricamente si las llegadas a un simulador responden a un proceso de Poisson, **no es necesario muestrear la cantidad discreta de arribos por hora, sino medir de forma continua los tiempos transcurridos entre arribos consecutivos y verificar si ajustan a una distribución exponencial**. Validar la distribución exponencial de los tiempos entre arribos constituye la prueba necesaria y suficiente para certificar un proceso de entrada de Poisson.

### 6.5. Procesos de Renovación Generales (G) y su Relevancia Metodológica
Un **Proceso de Renovación** es una generalización de un proceso de Poisson en el cual los tiempos entre eventos consecutivos $A_1, A_2, \dots$ son variables aleatorias independientes e idénticamente distribuidas (i.i.d.) regidas por **cualquier función de distribución de probabilidad general $F(a)$**, sin restricción a la distribución exponencial.

*   En la Notación de Kendall, la letra **$G$** (*General*) o **$GI$** (*General Independent*) denota un proceso de entrada o tiempo de servicio de renovación arbitrario.
*   **Implicancia para la Simulación:** Cuando los tiempos entre llegadas siguen una distribución general $G$ diferente de la exponencial (por ejemplo, Uniforme, Weibull o Normal), el proceso pierde la propiedad de falta de memoria. Como consecuencia, el número de clientes en el sistema $N(t)$ deja de ser un proceso de Markov, invalidando los modelos teóricos analíticos cerrados y volviendo **obligatorio el uso de la simulación computacional de eventos discretos**.

---

## Segmento 7: Procesos de Nacimiento y Muerte y Ecuaciones de Balance

### 7.1. Definición de Procesos de Nacimiento y Muerte en Tiempo Continuo
Un **Proceso de Nacimiento y Muerte (Birth-and-Death Process)** es un caso especial de una Cadena de Markov en Tiempo Continuo (CTMC) en el cual las variables de estado representan la población o cantidad de entidades en un sistema $N(t) \in \{0, 1, 2, \dots\}$, y cuyas transiciones de estado están restringidas exclusivamente a **saltos unitarios adyacentes**:

*   **Nacimiento (Birth):** Incrementa el estado del sistema en una unidad ($n \to n+1$). Ocurre con una tasa de probabilidad instantánea $\lambda_n \ge 0$ cuando el sistema está en el estado $n$.
*   **Muerte (Death):** Decrementa el estado del sistema en una unidad ($n \to n-1$). Ocurre con una tasa de probabilidad instantánea $\mu_n \ge 0$ cuando el sistema está en el estado $n$ (con $\mu_0 = 0$).

Los tiempos entre nacimientos y entre muertes se distribuyen de forma independiente según variables exponenciales con parámetros $\lambda_n$ y $\mu_n$ respectivamente.

### 7.2. Tasa de Transición y Matriz Infinitesimal
En un intervalo infinitesimal $\Delta t$, las probabilidades de transición entre estados vecinos están dadas por:

$$P_{n, n+1}(\Delta t) = \lambda_n \Delta t + o(\Delta t)$$

$$P_{n, n-1}(\Delta t) = \mu_n \Delta t + o(\Delta t)$$

$$P_{n, n}(\Delta t) = 1 - (\lambda_n + \mu_n)\Delta t + o(\Delta t)$$

$$P_{n, m}(\Delta t) = o(\Delta t), \quad \text{para } |n - m| \ge 2$$

Estas tasas permiten estructurar la **Matriz de Tasas de Transición Infinitesimal (Matriz Generatora $\mathbf{Q}$)**:

$$\mathbf{Q} = \begin{bmatrix} -\lambda_0 & \lambda_0 & 0 & 0 & \dots \\ \mu_1 & -(\lambda_1 + \mu_1) & \lambda_1 & 0 & \dots \\ 0 & \mu_2 & -(\lambda_2 + \mu_2) & \lambda_2 & \dots \\ \vdots & \vdots & \vdots & \vdots & \ddots \end{bmatrix}$$

Donde los elementos diagonales satisfacen $q_{nn} = -\sum_{j \neq n} q_{nj} = -(\lambda_n + \mu_n)$.

### 7.3. Principio de Conservación de Flujo: Ecuaciones de Balance Global
Sea $P_n(t) = P(N(t) = n)$ la probabilidad de que el sistema se encuentre en el estado $n$ en el instante $t$. La evolución temporal del estado del sistema está descrita por las **Ecuaciones Diferenciales de Kolmogorov**:

$$\frac{dP_0(t)}{dt} = -\lambda_0 P_0(t) + \mu_1 P_1(t)$$

$$\frac{dP_n(t)}{dt} = -(\lambda_n + \mu_n)P_n(t) + \lambda_{n-1}P_{n-1}(t) + \mu_{n+1}P_{n+1}(t), \quad \forall n \ge 1$$

#### Estado Estacionario (Régimen Permanente)
Cuando el sistema alcanza el equilibrio o régimen estacionario a largo plazo ($t \to \infty$), las probabilidades de estado se vuelven independientes del tiempo y se estabilizan en valores constantes $P_n(t) \to P_n$, lo que implica que sus derivadas temporales se anulan:

$$\lim_{t \to \infty} \frac{dP_n(t)}{dt} = 0$$

Al sustituir las derivadas por cero, se obtienen las **Ecuaciones de Balance Global de Probabilidades**, las cuales traducen el principio físico de conservación de flujo de probabilidad:

$$\text{Tasa de Flujo de Salida del Estado } n = \text{Tasa de Flujo de Entrada al Estado } n$$

*   **Para el estado $0$:**
    $$\lambda_0 P_0 = \mu_1 P_1$$
*   **Para cualquier estado $n \ge 1$:**
    $$(\lambda_n + \mu_n) P_n = \lambda_{n-1} P_{n-1} + \mu_{n+1} P_{n+1}$$

### 7.4. Ecuaciones de Balance Local y Resolución Estacionaria Iterativa
En los procesos de nacimiento y muerte, debido a la estructura unidimensional tridiagonal de las transiciones, el principio de balance de flujo puede simplificarse aislando cortes conceptuales entre estados adyacentes.

Las **Ecuaciones de Balance Local** establecen que el flujo de probabilidad que cruza la frontera entre el estado $(n-1)$ y el estado $n$ hacia la derecha debe igualar exactamente al flujo de probabilidad que cruza esa misma frontera de regreso hacia la izquierda:

$$\lambda_{n-1} P_{n-1} = \mu_n P_n, \quad \forall n \ge 1$$

#### Resolución Iterativa del Sistema
Despejando $P_n$ en función de su estado anterior $P_{n-1}$:

$$P_n = \left( \frac{\lambda_{n-1}}{\mu_n} \right) P_{n-1}$$

Aplicando esta relación de forma recursiva a partir de $P_0$:

$$P_1 = \left( \frac{\lambda_0}{\mu_1} \right) P_0$$

$$P_2 = \left( \frac{\lambda_1}{\mu_2} \right) P_1 = \left( \frac{\lambda_1 \cdot \lambda_0}{\mu_2 \cdot \mu_1} \right) P_0$$

Explicitando la solución para cualquier estado $n \ge 1$:

$$P_n = P_0 \prod_{i=1}^{n} \frac{\lambda_{i-1}}{\mu_i}$$

### 7.5. Distribución de Probabilidades de Estado Estable $P_n$ y Probabilidad de Vacío $P_0$
Para determinar el valor de la **probabilidad de sistema vacío ($P_0$)**, se aplica el **Axioma de Normalización** de la probabilidad, el cual exige que la suma de todas las probabilidades de estado sea igual a la unidad:

$$\sum_{n=0}^{\infty} P_n = 1 \implies P_0 + \sum_{n=1}^{\infty} P_n = 1$$

Sustituyendo la expresión recursiva de $P_n$:

$$P_0 + \sum_{n=1}^{\infty} \left( P_0 \prod_{i=1}^{n} \frac{\lambda_{i-1}}{\mu_i} \right) = 1 \implies P_0 \left( 1 + \sum_{n=1}^{\infty} \prod_{i=1}^{n} \frac{\lambda_{i-1}}{\mu_i} \right) = 1$$

Despejando finalmente la probabilidad de vacío $P_0$:

$$P_0 = \frac{1}{1 + \sum_{n=1}^{\infty} \prod_{i=1}^{n} \frac{\lambda_{i-1}}{\mu_i}}$$

#### Condición Necesaria y Suficiente de Estabilidad Estacionaria
Para que exista una distribución de probabilidades de estado estable estacionaria válida ($P_0 > 0$), la serie infinita del denominador debe ser rigurosamente convergente:

$$\sum_{n=1}^{\infty} \prod_{i=1}^{n} \frac{\lambda_{i-1}}{\mu_i} < \infty$$

Si esta condición no se satisface, el sistema es inestable: la cola crece indefinidamente y no existe régimen permanente.

---

## Segmento 8: Teoría Estructurada de Colas y el Modelo M/M/1

### 8.1. Anatomía Estructural de un Sistema de Espera y Notación Extendida de Kendall
Un sistema de colas o de líneas de espera consta de seis componentes estructurales básicos:

1.  **Patrón de Arribo (Fuente de Entrada):** Caracterizado por la distribución de probabilidad de los tiempos entre llegadas y el tamaño de la población origen (finita o infinita).
2.  **Patrón de Servicio:** Caracterizado por la distribución de probabilidad de los tiempos de atención y la cantidad de servidores disponibles.
3.  **Capacidad del Sistema:** Número máximo total de entidades permitidas simultáneamente en el sistema (en cola + en servicio). Puede ser finita ($K$) o infinita ($\infty$).
4.  **Disciplina de la Cola:** La regla de prioridad bajo la cual se seleccionan las entidades en cola para pasar a servicio (FIFO, LIFO, PRIO, SIRO - *Service in Random Order*).
5.  **Comportamiento de las Entidades:** Actitudes de las entidades frente a la espera:
    *   *Balking:* Entidades que rechazan ingresar al sistema al observar una cola excesivamente larga.
    *   *Reneging:* Entidades que abandonan la cola tras experimentar un tiempo de espera frustrante.
    *   *Jockeying:* Entidades que alternan entre múltiples filas buscando la cola más rápida.

#### Notación Extendida de Kendall
David G. Kendall (1953) propuso una notación estandarizada abreviada para clasificar los sistemas de espera mediante la estructura:

$$A / B / c / K / N / D$$

Donde:
*   **$A$:** Distribución de probabilidad de los tiempos entre arribos.
*   **$B$:** Distribución de probabilidad de los tiempos de servicio.
*   **$c$:** Número de servidores o canales de servicio paralelos ($c \ge 1$).
*   **$K$:** Capacidad máxima total del sistema (cola + servicio). Si se omite, se asume $K = \infty$.
*   **$N$:** Tamaño de la población de la fuente de entrada. Si se omite, se asume $N = \infty$.
*   **$D$:** Disciplina de servicio. Si se omite, se asume FIFO/FCFS.

**Símbolos Canónicos para $A$ y $B$:**
*   **$M$:** *Markoviano* (proceso de Poisson / tiempos exponenciales).
*   **$D$:** *Determinístico* (tiempos constantes).
*   **$E_k$:** *Erlang-$k$* (tiempos distribuidos por etapas).
*   **$G$:** *General* (distribución arbitraria con media y varianza conocidas).

### 8.2. Parámetros Fundamentales: Tasa de Arribos ($\lambda$), Tasa de Servicio ($\mu$) e Intensidad de Tráfico ($\rho$)
Los tres parámetros cuantitativos base que gobiernan el régimen de un sistema de colas son:

*   **Tasa Media de Arribos ($\lambda$):** Cantidad promedio de entidades que ingresan al sistema por unidad de tiempo ($[tiempo]^{-1}$). El tiempo medio entre arribos es $E[A] = 1/\lambda$.
*   **Tasa Media de Servicio por Servidor ($\mu$):** Cantidad promedio de entidades que un servidor individual puede procesar por unidad de tiempo si se mantiene ininterrumpidamente ocupado ($[tiempo]^{-1}$). El tiempo medio de servicio es $E[S] = 1/\mu$.
*   **Factor de Utilización del Sistema e Intensidad de Tráfico ($\rho$):** Proporción promedio de tiempo que los servidores permanecen ocupados, o la fracción de la capacidad de servicio utilizada por la carga de llegada.

Para un sistema de $c$ servidores paralelos:

$$\rho = \frac{\lambda}{c \cdot \mu}$$

#### Condición General de Estabilidad Estocástica
Para garantizar que la cola no crezca indefinidamente en un sistema de capacidad infinita ($K = \infty$), la tasa total de servicio debe superar estrictamente a la tasa de llegada:

$$\rho < 1 \iff \lambda < c \cdot \mu$$

### 8.3. Análisis Exhaustivo del Modelo $M/M/1$: Hipótesis, Derivación Estacionaria y Métrica $P_n = (1-\rho)\rho^n$
El modelo $M/M/1$ representa el sistema de espera más fundamental en la teoría de colas. Sus especificaciones de diseño son:
*   Proceso de entrada de Poisson con tasa constante $\lambda_n = \lambda, \, \forall n \ge 0$.
*   Tiempos de servicio exponenciales con tasa constante $\mu_n = \mu, \, \forall n \ge 1$.
*   Un único servidor ($c = 1$).
*   Capacidad de sistema y población infinitas ($K = \infty, N = \infty$).
*   Disciplina FIFO.

#### Derivación de la Distribución de Probabilidades de Estado $P_n$
El modelo $M/M/1$ es un caso particular del Proceso de Nacimiento y Muerte con tasas homogéneas:

$$\lambda_n = \lambda, \quad \mu_n = \mu, \quad \forall n$$

Sustituyendo estas tasas en la fórmula de balance local estacionario obtenida en el Segmento 7:

$$P_n = P_0 \prod_{i=1}^{n} \frac{\lambda_{i-1}}{\mu_i} = P_0 \prod_{i=1}^{n} \frac{\lambda}{\mu} = P_0 \left( \frac{\lambda}{\mu} \right)^n = P_0 \cdot \rho^n$$

Para calcular $P_0$, aplicamos la condición de normalización:

$$\sum_{n=0}^{\infty} P_n = 1 \implies P_0 \sum_{n=0}^{\infty} \rho^n = 1$$

Puesto que el sistema es estable ($\rho < 1$), la suma corresponde a una **serie geométrica infinita** cuya suma es $\frac{1}{1 - \rho}$:

$$P_0 \left( \frac{1}{1 - \rho} \right) = 1 \implies P_0 = 1 - \rho$$

Donde $P_0$ representa la probabilidad de que el servidor se encuentre ocioso o el sistema esté vacío.

Sustituyendo $P_0$ en la expresión de $P_n$, obtenemos la **Distribución Geométrica de Probabilidades de Estado Estable para $M/M/1$**:

$$P_n = (1 - \rho)\rho^n, \quad n = 0, 1, 2, \dots$$

### 8.4. Derivación Matemática de Indicadores de Rendimiento: $L$, $L_q$, $W$ y $W_q$
Las medidas de respuesta del sistema se calculan a partir de la distribución de estado $P_n$:

#### 1. Número Promedio de Entidades en el Sistema ($L$ o $E[L]$)
Es el valor esperado de la variable aleatoria estado $N$:

$$L = E[N] = \sum_{n=0}^{\infty} n \cdot P_n = \sum_{n=0}^{\infty} n (1 - \rho)\rho^n = (1 - \rho) \rho \sum_{n=1}^{\infty} n \rho^{n-1}$$

Utilizando la propiedad de las series de potencias $\sum_{n=1}^{\infty} n \rho^{n-1} = \frac{d}{d\rho} \left( \sum_{n=0}^{\infty} \rho^n \right) = \frac{d}{d\rho} \left( \frac{1}{1 - \rho} \right) = \frac{1}{(1 - \rho)^2}$:

$$L = (1 - \rho) \rho \left( \frac{1}{(1 - \rho)^2} \right) \implies L = \frac{\rho}{1 - \rho} = \frac{\lambda}{\mu - \lambda}$$

#### 2. Número Promedio de Entidades en la Cola ($L_q$ o $E[L_q]$)
Es el número de clientes esperando en fila, descontando el cliente que está en servicio:

$$L_q = \sum_{n=1}^{\infty} (n - 1) P_n = \sum_{n=1}^{\infty} n P_n - \sum_{n=1}^{\infty} P_n = L - (1 - P_0) = L - \rho$$

Sustituyendo $L = \frac{\rho}{1 - \rho}$:

$$L_q = \frac{\rho}{1 - \rho} - \rho = \frac{\rho - \rho(1 - \rho)}{1 - \rho} \implies L_q = \frac{\rho^2}{1 - \rho} = \frac{\lambda^2}{\mu(\mu - \lambda)}$$

### 8.5. La Ley de Little ($L = \lambda W$) y sus Demostraciones Relacionales
Formulada por John D. C. Little (1961), la **Ley de Little** es el teorema fundamental de la teoría de colas. Establece una relación determinística para cualquier sistema de espera en régimen estacionario, independientemente de las distribuciones de probabilidad de arribos o servicios:

$$L = \lambda W$$

$$L_q = \lambda W_q$$

Donde:
*   $W$: Tiempo promedio de permanencia total de una entidad en el sistema (cola + servicio).
*   $W_q$: Tiempo promedio de espera de una entidad únicamente en la cola.

#### Derivación de los Tiempos de Espera $W$ y $W_q$ para $M/M/1$
Despejando $W$ mediante la Ley de Little:

$$W = \frac{L}{\lambda} = \frac{\frac{\lambda}{\mu - \lambda}}{\lambda} \implies W = \frac{1}{\mu - \lambda}$$

Despejando $W_q$:

$$W_q = \frac{L_q}{\lambda} = \frac{\frac{\lambda^2}{\mu(\mu - \lambda)}}{\lambda} \implies W_q = \frac{\lambda}{\mu(\mu - \lambda)}$$

#### Relación General de Tiempos y Longitudes
Puesto que el tiempo total en el sistema es la suma del tiempo en cola más el tiempo de servicio $W = W_q + E[S]$:

$$W = W_q + \frac{1}{\mu}$$

Multiplicando toda la ecuación por $\lambda$ se deduce inmediatamente la relación de componentes:

$$L = L_q + \rho$$

### 8.6. Extensiones Canónicas de Kendall
Cuando el sistema difiere de las hipótesis $M/M/1$, la teoría ofrece modelos especializados:

#### 1. Modelo Multiservidor $M/M/c$
Posee $c$ servidores en paralelo alimentados por una única cola.
*   Tasas de Servicio del Sistema:
    $$\mu_n = \begin{cases} n\mu, & \text{si } 0 \le n < c \\ c\mu, & \text{si } n \ge c \end{cases}$$
*   Probabilidad de Espera / Fórmula $C$ de Erlang: Describe la probabilidad de que una entidad que llega encuentre todos los servidores ocupados y deba esperar en cola:
    $$P(N \ge c) = P_c(\text{Erlang}) = \frac{\frac{(c\rho)^c}{c!(1-\rho)}}{\sum_{k=0}^{c-1}\frac{(c\rho)^k}{k!} + \frac{(c\rho)^c}{c!(1-\rho)}}$$

#### 2. Modelo $M/M/1/K$ (Capacidad Finita de Búfer $K$)
La cola sólo puede contener $K - 1$ clientes esperando ($K$ total en sistema).
*   No requiere la condición $\rho < 1$ para ser estable, pues la capacidad finita evita el crecimiento infinito.
*   **Probabilidad de Bloqueo / Pérdida ($P_K$):** Probabilidad de que un cliente llegue y encuentre el sistema lleno:
    $$P_K = \frac{(1-\rho)\rho^K}{1 - \rho^{K+1}}$$
*   **Tasa Efectiva de Arribos:** $\lambda_{eff} = \lambda (1 - P_K)$.

#### 3. Modelo $M/G/1$ y Fórmula de Pollaczek-Khintchine (P-K)
Los arribos son de Poisson ($\lambda$), pero los tiempos de servicio siguen una distribución general $G$ con media $E[S] = 1/\mu$ y varianza $\sigma_s^2$.

Debido a que el servicio no es exponencial, la longitud de la cola se analiza mediante una cadena de Markov embebida. La **Fórmula de Pollaczek-Khintchine (P-K)** determina la longitud promedio de la cola en estado estacionario:

$$L_q = \frac{\lambda^2 \sigma_s^2 + \rho^2}{2(1 - \rho)}$$

*   **Impacto de la Variabilidad:** Si el servicio es determinístico $D$ ($\sigma_s^2 = 0$), $L_q = \frac{\rho^2}{2(1-\rho)}$ (se reduce exactamente a la mitad de la cola del modelo $M/M/1$).
*   Demuestra formalmente que la longitud de la cola no depende solo de las medias ($\lambda, \mu$), sino **directamente de la varianza del tiempo de servicio $\sigma_s^2$**.

---

## Segmento 9: Diseño y Análisis de Experimentos de Simulación (DOE) y Metamodelado

### 9.1. La Necesidad del DOE en Entornos Computacionales Estocásticos
Un simulador estocástico validado funciona conceptualmente como un **laboratorio experimental computacional**. Cada ejecución del simulador representa un experimento numérico impulsado por secuencias aleatorias.

El **Diseño de Experimentos (DOE - Design of Experiments)** en simulación es la planificación sistemática de las corridas computacionales con el objetivo de evaluar cómo las variaciones deliberadas en los factores de entrada (parámetros controlables $X$) impactan sobre las variables de respuesta de desempeño ($Y$), maximizando la cantidad de información estadística obtenida al menor costo computacional.

Las particularidades del DOE en simulación frente a la experimentación física son:
1.  **Ausencia de Ruido Físico e Inexistencia de Errores de Medición:** La variabilidad observada en las respuestas es $100\%$ producto del ruido estocástico induced por los generadores de números pseudoaleatorios.
2.  **Repetibilidad Absoluta:** Si se fija la misma semilla aleatoria, el experimento arroja el mismo resultado. Por ende, para realizar **repeticiones genuinas** que permitan estimar la varianza del error estocástico, se debe cambiar deliberadamente la semilla de aleatoriedad en cada corrida.

### 9.2. Estructura Factorial ($q^K$) y el Rol del Ruido Estocástico (Repeticiones)
Para evaluar $K$ factores controlables, cada uno ajustado en $q$ niveles operacionales diferenciados (por ejemplo, nivel Bajo $-$ y nivel Alto $+$ para un diseño de 2 niveles $q=2$):

*   **Tratamiento:** Una combinación específica de niveles de todos los $K$ factores.
*   **Diseño Factorial Completo $q^K$:** Evalúa la totalidad de las combinaciones posibles de tratamientos. Por ejemplo, para $K=3$ factores a 2 niveles, se ejecutan $2^3 = 8$ tratamientos.
*   **Número Total de Ejecuciones ($N$):** Si cada tratamiento se replica $p$ veces utilizando semillas independientes:
    $$N = p \cdot q^K$$

### 9.3. Análisis de Varianza (ANOVA) Aplicado a Salidas de Simulación
El **Análisis de Varianza (ANOVA)** descompone la variabilidad total observada en la variable de respuesta $Y$ en componentes asignables a los factores principales, a sus interacciones y al error estocástico no explicado.

Para un modelo lineal de dos factores $A$ y $B$ con $p$ repeticiones:

$$Y_{ijk} = \mu + \tau_i + \beta_j + (\tau\beta)_{ij} + \epsilon_{ijk}, \quad \begin{cases} i = 1, \dots, a \\ j = 1, \dots, b \\ k = 1, \dots, p \end{cases}$$

Donde:
*   $\mu$: Media global de la respuesta.
*   $\tau_i$: Efecto del nivel $i$ del Factor $A$.
*   $\beta_j$: Efecto del nivel $j$ del Factor $B$.
*   $(\tau\beta)_{ij}$: Efecto de la interacción entre el Factor $A$ y el Factor $B$.
*   $\epsilon_{ijk} \sim N(0, \sigma^2)$: Error aleatorio estocástico i.i.d.

#### Tabla de Descomposición de Suma de Cuadrados
$$\text{SS}_{Total} = \text{SS}_A + \text{SS}_B + \text{SS}_{AB} + \text{SS}_{Error}$$

Se calculan los **Medios Cuadráticos ($MS = SS / df$)** dividiendo cada suma de cuadrados por sus respectivos grados de libertad ($df$).

#### Prueba de Significancia Estadística (Prueba $F$)
Para determinar si el Factor $A$ influye significativamente sobre la respuesta, se evalúa la hipótesis nula $H_0: \tau_i = 0$ mediante el estadístico $F_0$:

$$F_0 = \frac{\text{MS}_A}{\text{MS}_{Error}}$$

Se rechaza $H_0$ (confirmando que el factor es estadísticamente significativo) si $F_0 > F_{\alpha, df_A, df_{Error}}$ o si el $p\text{-valor} < \alpha$.

### 9.4. Construcción de Metamodelos: Superficies de Respuesta y Regresión Lineal/Cuadrática
Un **Metamodelo** es un modelo matemático aproximado (un "modelo del modelo de simulación") que simplifica la relación funcional entre las entradas $X$ y la salida $Y$ generada por el simulador:

$$Y = f_{meta}(X_1, X_2, \dots, X_K) + \epsilon$$

Los metamodelos de **Metodología de Superficie de Respuesta (RSM)** permiten optimizar operativamente el sistema calculando un modelo de regresión cuadrático de segundo orden:

$$Y = \beta_0 + \sum_{i=1}^{K} \beta_i X_i + \sum_{i=1}^{K} \beta_{ii} X_i^2 + \sum_{i<j}^{K} \sum \beta_{ij} X_i X_j + \epsilon$$

Donde:
*   $\beta_0$: Intercepto o constante del modelo.
*   $\beta_i$: Coeficientes lineales asociados a los efectos principales.
*   $\beta_{ii}$: Coeficientes cuadráticos que capturan la curvatura de la respuesta.
*   $\beta_{ij}$: Coeficientes de interacción binaria entre factores.

Los coeficientes del metamodelo se estiman mediante el método de Mínimos Cuadrados Ordinarios (OLS):

$$\vec{\hat{\beta}} = (\mathbf{X}^T \mathbf{X})^{-1} \mathbf{X}^T \vec{Y}$$

Evaluando la calidad de ajuste del metamodelo mediante el Coeficiente de Determinación Ajustado ($R_{adj}^2$).

### 9.5. Optimización de Parámetros Operativos mediante Perfiladores de Predicción y Contorno
Una vez estimado un metamodelo analítico validado $\hat{Y} = f_{meta}(\vec{X})$, el proceso de toma de decisiones sustituye la costosa simulación de eventos discretos por el uso directo del metamodelo para la optimización matemática:

1.  **Perfilador de Predicción (Prediction Profiler):** Evalúa la deseabilidad de la respuesta manteniendo factores fijos y graficando la pendiente de cambio individual de la medida de desempeño ante variaciones continuas de cada factor $X_i$.
2.  **Perfilador de Contornos (Contour Profiler):** Proyecta curvas de nivel bidimensionales de la superficie de respuesta sobre el plano de factores $(X_i, X_j)$, delimitando visualmente la región de operación óptima que satisface las restricciones del sistema.
3.  **Matriz de Deseabilidad de Harrington:** Convierte múltiples respuestas en conflicto (por ejemplo, minimizar tiempo de espera $W$ y minimizar costo de servidores $C$) en una única función de deseabilidad global $D(\vec{X}) \in [0, 1]$, cuya maximización mediante algoritmos de gradiente determina la configuración operativa idónea del sistema real.
