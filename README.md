# LABORATORIO 5: VARIABILIDAD DEL LA FRECUENCIA CARDIACA

## Investigación teórica

### (SNA) Sistema Nervioso Autónomo.
El Sistema Nerviso Autónomo dentro de sus varias funciones es el encargado de regular la frecuencia cardíaca y su variabilidad a través de dos ramas:

-**Sistema Simpático**:
Rama encargada del aumento en el ritmo cardíaco y la fuerza de contracción del corazón con el fin de preparar el cuerpo ante situaciones de riesgo, estrés, actividad física, peligro inmediante, etc. La actividad simpática activa las células del nodo Sinoauricular, también llamado marcapasos natural del corazón, esto con el fin de incrementar la frecuencia cardíaca, generando ritmos más rápidos y consistentes.

-**Sistema Parasimpático**:
Rama encarcaga de redicr el ritmo cardíaco y la recuperación de este mismo, esto lo logra a través del control de la frecuencia durante el descanso. El Nervio Vago, asociado al parasimpático, disminuye la actividad del nodo Sinoaricular, logrando así una frecuencia cardíaca mas baja y variada, la cual indica un estado de relajación y recuperación del organismo.
 
### (HRV) Variabilidad de la Frecuencia Cardíaca.
Es la encargada de medir las fluctuaciones en los intervalos entre latidos consecutivos, intervalos R-R, reflejando la capacidad del Sistema Nervioso Autónomo para adaptar la frecuencia cardíaca en función de las necesidades del organismo. Una HRV alta indica una mayot capacidad de flexibilidad y adaptación del sistema cardíaco, mientras que una HRV baja puede señalar limitaciones en la regulación autónoma o condiciones de estrés.

### Frecuencias de Interés en la Variabilidad de la Frecuencia Cardíaca.
Para el análisis de la HRV, se estudian ciertas bandas de frecuencia en los intervalos R-R:

- **Frecuencia Baja (LF: 0.04 - 0.15 Hz)**:  
  Refleja principalmente la actividad del sistema simpático, aunque también incluye elementos del parasimpático. Cambios en esta banda sugieren un cambio en la respuesta de estrés o activación del cuerpo.

- **Frecuencia Alta (HF: 0.15 - 0.4 Hz)**:  
  Se asocia principalmente con la actividad parasimpática y con la respiración. Valores altos de HF indican una buena actividad vagal y control parasimpático. Frecuencias altas son típicas en periodos de relajación o recuperación.

Una relación LF/HF alta sugiere predominancia simpática, mientras que una relación baja indica mayor actividad parasimpática.

A medida que una persona envejece, la HRV tiende a disminuir. Esto ocurre porque el sistema nervioso autónomo (SNA) pierde flexibilidad y capacidad de respuesta, especialmente en su componente parasimpático, que suele reducir su influencia en la frecuencia cardíaca. El valor típico de HRV normal es que la edad de 20 años suele tener una HRV media en el rango de 55-105, mientras que la edad de 60 años tiende a estar entre 25-45.

Los valores de potencia de LF y HF suelen ser más altos en jóvenes porque hay más variabilidad en la frecuencia cardíaca. Esto muestra que el SNA es flexible y responde rápidamente a cambios. En adultos, la potencia espectral de LF y HF disminuye, ya que la frecuencia cardíaca se vuelve más constante, reflejando menos adaptabilidad del SNA.

## Transformada Wavelet y la Wavelet Morlet

La Wavelet Morlet es una onda compuesta por una exponencial compleja multiplicada por una ventana gaussiana, lo que le da la capacidad de detectar eventos localizados en una señal. Se trata de una wavelet compleja y continua, que permite obtener una representación detallada y continua de la señal en diferentes escalas de frecuencia a lo largo del tiempo. Esto es ideal para señales no estacionarias, como el ECG, donde las características pueden variar con el tiempo.

### Características Clave de la Transformada Wavelet Morlet

- **Continuidad**:  
  Al ser una wavelet continua, la Transformada Wavelet Morlet ofrece una representación fluida en el tiempo, lo que facilita el análisis detallado de cada instante de la señal.

- **Resolución en tiempo y frecuencia**:  
  La Morlet wavelet tiene una alta precisión tanto en el dominio del tiempo como en el de la frecuencia, lo cual es ideal para identificar cambios graduales o rápidos en la señal.

- **Forma Gaussiana**:  
  La función de Morlet está modulada por una envolvente gaussiana, lo que permite una transición suave entre las escalas de frecuencia y minimiza el ruido en el análisis de los picos y variaciones de la señal de ECG.

- **Uso en análisis local**:  
  Esta wavelet es particularmente útil para detectar cambios sutiles en cortos períodos de tiempo dentro de la señal de ECG, capturando patrones rápidos y eventos de interés en la frecuencia cardíaca.

  ## Diagrama de Flujo del Plan de Acción para cumplir la práctica.

https://www.mymap.ai/playground?mid=vAOwDxaSZ2FA0&is_share=true

## Adquisición de la Señal.

En la siguiente imagem podremos ver la señal original tomada en un rango de 5 minutos y un fragmento de 10 segundos para lograr distinguir los picos R-R y tener un mejor análisis de la señal.

![Image](https://github.com/user-attachments/assets/8c23111f-4ef4-4376-b923-fefc966d97ed)

Señal original y filtrada de 10 segundos: 

![Image](https://github.com/user-attachments/assets/982ef5c5-2d63-4a64-b319-c64cfbc1eadd)

Para la adquisición de la señal ECG, utilizé un sensor AD8232 conectado a tres electrodos en una configuración específica que se detalla en la siguiente imagén.

![Image](https://github.com/user-attachments/assets/190cfb15-f3cf-4a17-a153-86f4d08eeea9)

Los electrodos fueron colocados sobre la piel limpia de la persona, capturando la actividad eléctrica del corazón y enviando la señal al sensor AD8232. Este se conectó a una STM que, a través de un cable USB-C, transmitió los datos por conexión serial al computador. En el computador, una interfaz desarrollada en Python recibió y mostró la señal en tiempo real, además de guardar los datos adquiridos en un archivo .txt para su posterior procesamiento. Esta configuración permitió una adquisición eficiente y confiable de la señal ECG, manteniendo la calidad y la integridad de los datos para el análisis posterior.

### Parámetros Técnicos
- **Frecuencia de muestreo**: 1000 Hz, lo que significa que se registraron 1000 muestras por segundo. Esto es una frecuencia adecuada para captar detalles rápidos de la señal de ECG, ya que los eventos cardíacos importantes, como los picos QRS, tienen una duración de milisegundos.

- **Tiempo de muestreo**: Con una frecuencia de muestreo de 1000 Hz, el tiempo de muestreo es de 0.001 segundos (1 ms), lo que asegura que se capturen todos los eventos significativos de la señal cardíaca sin distorsión.

- **Niveles de cuantificación**: Es el proceso de asignar un valor discreto a cada muestra, convirtiendo así el valor analógico continuo en un valor digital. Se usaron 50 bytes para la cuantificación, es decir, por cada 0.001 segundos se reciben 50 datos.

- **Media de la señal ECG**: Hace referencia al valor promedio del intervalo R-R (tiempo entre dos picos R consecutivos en el ECG) a lo largo de los 5 minutos de grabación. La media de nuestra señal es de **984.21 ms**, lo que nos indica una frecuencia cardíaca promedio de aproximadamente 61 latidos por minuto (1 latido cada 984.21 ms).

- **Desviación estándar**: Indica la variabilidad en los intervalos R-R. Nuestra desviación estándar es de **329.42 ms**, lo que sugiere que la frecuencia cardíaca varía de un latido a otro, lo cual es normal y esperado en un ECG humano. La HRV se mide precisamente a través de esta variación entre intervalos R-R, y un valor moderado de desviación estándar en este rango sugiere una flexibilidad del sistema cardíaco que puede ser mejorada.

## FILTROS

# Análisis de Señal ECG con Filtro Pasa Banda Butterworth y Detección de Picos R

Este proyecto analiza señales de ECG (electrocardiograma) utilizando un filtro pasa banda Butterworth para mejorar la calidad de la señal y detectar picos R con precisión. La información obtenida permite calcular los intervalos R-R, fundamentales para evaluar la variabilidad de la frecuencia cardíaca (HRV). A continuación, se detallan todos los aspectos técnicos, la justificación de los parámetros y las funcionalidades del código.

---

## Parámetros del Proyecto

- **Frecuencia de Muestreo (fs)**: 1000 Hz
- **Frecuencia de Corte Inferior (lowcut)**: 0.5 Hz
- **Frecuencia de Corte Superior (highcut)**: 100 Hz
- **Orden del Filtro**: 4
- **Filtrado Causal Doble (filtfilt)**: Sí, para eliminar el retardo de fase

---

## Justificación Técnica del Filtro Pasa Banda Butterworth

### 1. Elección del Filtro Butterworth
El filtro **Butterworth** es particularmente adecuado debido a su **respuesta de magnitud plana en la banda de paso**, que minimiza la distorsión en las frecuencias de interés. Esto asegura que las características esenciales del ECG, como los complejos QRS, se mantengan sin alteraciones, lo cual es crucial para la detección de los picos R y el análisis preciso de HRV.

### 2. Frecuencia de Muestreo (fs = 1000 Hz)
La **frecuencia de muestreo de 1000 Hz** permite capturar la señal ECG con suficiente detalle, cumpliendo además con el **Teorema de Nyquist** para evitar aliasing. La alta frecuencia de muestreo garantiza:
   - Una resolución temporal adecuada, crucial para identificar de manera precisa los picos R.
   - Estabilidad en los cálculos de variabilidad de la frecuencia cardíaca (HRV) al proporcionar datos detallados.

### 3. Frecuencias de Corte: 0.5 Hz y 100 Hz
El rango de frecuencias **[0.5 Hz - 100 Hz]** permite aislar el contenido relevante de la señal ECG, eliminando el ruido fuera de esta banda.

- **Frecuencia de Corte Inferior (0.5 Hz)**: 
   - Filtra la **deriva de línea de base** y el ruido de baja frecuencia, como el producido por movimientos respiratorios, que podrían interferir en la detección de los picos R.
   - Preserva las frecuencias fundamentales de la señal ECG sin captar variaciones indeseadas.

- **Frecuencia de Corte Superior (100 Hz)**:
   - Reduce el **ruido electromagnético** de alta frecuencia y otras interferencias externas.
   - Mantiene la **morfología del QRS**, necesaria para la detección precisa de picos R y el análisis de intervalos R-R.

### 4. Orden del Filtro (4)
Un **filtro de orden 4** proporciona un balance óptimo entre **selectividad** (pendiente de 80 dB/decada) y **estabilidad computacional**. Esto asegura una reducción eficaz del ruido sin perder detalles importantes de la señal.

### 5. Filtrado Causal Doble (filtfilt)
Se utiliza la función filtfilt para realizar un filtrado causal doble que:
   - **Elimina el retardo de fase**: Esto asegura que la alineación temporal de los picos R no se vea afectada.
   - **Preserva la morfología de la señal**: Garantiza que la forma de la onda ECG se mantenga clara, lo que es crucial para el análisis de HRV.

---

## Procesamiento de la Señal ECG

El proceso de análisis de la señal ECG se divide en cuatro etapas principales:

1. **Aplicación del Filtro Butterworth**: La señal ECG se filtra utilizando el filtro pasa banda Butterworth configurado para eliminar el ruido de baja y alta frecuencia, preservando las frecuencias relevantes para el ECG.

2. **Detección de Picos R**: Se utilizan algoritmos de detección de picos optimizados para capturar los picos R con precisión, basándose en un umbral ajustado al contenido de la señal filtrada. La detección de picos R es fundamental para calcular los intervalos entre latidos.

3. **Cálculo de Intervalos R-R**: Los intervalos R-R se obtienen a partir de la diferencia de tiempo entre los picos R consecutivos, proporcionando la base para el análisis de HRV.

4. **Cálculo de Parámetros de HRV**: Se calculan métricas básicas como la media y desviación estándar de los intervalos R-R, parámetros relevantes en el análisis de variabilidad de la frecuencia cardíaca.

---

## Visualización

El script genera varios gráficos para facilitar el análisis y evaluación del procesamiento de la señal:

- **Señal ECG Original y Filtrada**: Comparación de la señal ECG sin filtrar y la señal filtrada, permitiendo evaluar la efectividad del filtro.
- **Detección de Picos R**: Visualización de la señal filtrada con los picos R marcados.
- **Intervalos R-R**: Gráfico de los intervalos R-R en el tiempo, útil para el análisis de HRV.

---
# Análisis de la Variabilidad de la Frecuencia Cardíaca (HRV)

El análisis de la variabilidad de la frecuencia cardíaca (HRV) en el dominio del tiempo utilizando datos de electrocardiograma (ECG). El análisis de la HRV es fundamental para evaluar la salud cardiovascular y la respuesta del sistema nervioso autónomo. A continuación, se describen los pasos y técnicas utilizados en este análisis.


## Introducción.

El análisis de la HRV en el dominio del tiempo se enfoca en calcular parámetros que describen la variabilidad de los intervalos R-R (el tiempo entre picos R consecutivos en un ECG). Este análisis es esencial para evaluar la salud cardiovascular.

## Detección de Picos R.

El primer paso en el análisis de HRV es la detección de los picos R en la señal de ECG. Esto se logra mediante:

- **Filtrado de la señal**: Se aplica un filtro (como un filtro Butterworth pasa banda) para eliminar ruidos fuera del rango de interés, típicamente entre 0.5 y 100 Hz.
- 
- **Identificación de picos**: Se utilizan métodos de detección, como `find_peaks` de SciPy, para identificar los picos R con un umbral basado en la media y desviación estándar de la señal filtrada.

## Cálculo de Intervalos R-R

Una vez que se han identificado los picos R, se calculan los intervalos R-R:

- **Intervalos R-R**: Se obtienen restando las posiciones de los picos R adyacentes:

<img src="e1.png" alt="" width="300"/>

- **Conversión a milisegundos**: Los intervalos R-R se expresan en milisegundos (ms) para facilitar la interpretación.

## Cálculo de Parámetros Estadísticos.

Los intervalos R-R se utilizan para calcular varios parámetros estadísticos que describen la HRV:

- **Media de los intervalos R-R**:
<img src="e2.png" alt="" width="300"/>
- **Desviación estándar de los intervalos R-R**:

 <img src="e3.png" alt="" width="400"/>
 
## Interpretación de Resultados.

Los parámetros calculados proporcionan información crítica sobre la salud cardiovascular:

- **Frecuencia Cardíaca**: La media de los intervalos R-R puede ser utilizada para calcular la frecuencia cardíaca (FC) en latidos por minuto (lpm):

<img src="e4.png" alt="" width="300"/>

- **Variabilidad**: Un aumento en la desviación estándar de los intervalos R-R sugiere una mayor capacidad de adaptación del sistema nervioso autónomo.

## Limitaciones y Consideraciones.

- **Calidad de los Datos**: La precisión de los resultados depende de la calidad de la señal de ECG y de la eficacia de la detección de picos.
  
- **Interpretación Contextual**: Los resultados deben ser interpretados dentro del contexto clínico adecuado y revisados por un profesional de la salud.

## Conclusión.

El análisis de la HRV en el dominio del tiempo es una herramienta valiosa para evaluar la salud cardiovascular y la función del sistema nervioso autónomo. Al centrarse en los intervalos R-R y sus propiedades estadísticas, proporciona una visión clara de la variabilidad en la frecuencia cardíaca y su relación con el bienestar general.

### Transformada Wavelet Morlet
La transformada wavelet utilizada fue la wavelet Morlet. Esta wavelet es apropiada para análisis de señales como ECG debido a su capacidad de representar frecuencias de oscilación, permitiendo identificar patrones transitorios y cambios en la frecuencia a lo largo del tiempo. Además, la wavelet de Morlet es adecuada para capturar tanto componentes de baja como de alta frecuencia en una señal compleja como el ECG, donde eventos breves o transitorios pueden contener información significativa (como latidos del corazón, arritmias, etc.).

Para efectos de una mejor visualización del espectrograma, inicialmente se analizará el espectrograma de la señal completa es decir de los 5 minutos y luego de un fragmento de 30 segundos.

### Espectrograma de la Transformada Wavelet Morlet (5 minutos)
![image](https://github.com/user-attachments/assets/14759483-77b8-4220-9fa6-a84cae1a2591)
En el espectrograma de la señal EKG completa (300 segundos), que abarca un rango de frecuencias de 0 a 100 Hz, se observa una serie de líneas verticales que indican actividad periódica en todo el rango temporal.

- **Banda de baja frecuencia (0 a 20 Hz):** Esta banda, que es relevante para observar los componentes fundamentales del ECG como las ondas P, T y el complejo QRS, muestra una periodicidad marcada, lo que corresponde a la actividad regular del corazón. Sin embargo, no parece haber picos claros o variaciones destacadas en la potencia a lo largo del tiempo, lo que indica que no hay cambios abruptos en la actividad cardíaca durante los 5 minutos de registro. Esto es consistente con un ritmo cardíaco estable.

- **Banda de alta frecuencia (20 a 100 Hz):** Las frecuencias más altas están generalmente relacionadas con ruido electromiográfico (EMG) o interferencias ambientales. Aunque no se observan picos muy pronunciados en esta banda, sí se observan algunos patrones más intensos en las frecuencias altas. Sin embargo, en este espectrograma de 5 minutos, la actividad de alta frecuencia parece mantenerse constante y no sugiere ninguna anomalía o evento de alta energía durante el período de análisis.

El espectrograma de 5 minutos refleja un ECG estable sin grandes cambios en la potencia espectral tanto en las frecuencias bajas (asociadas a la actividad cardíaca) como en las altas (posiblemente ruido o actividad menor).

### Espectrograma de la Transformada Wavelet Morlet (30 segundos)
![image](https://github.com/user-attachments/assets/11baae30-b91c-46ea-b9fe-3cdc1b88fb36)
El espectrograma de 30 segundos proporciona una vista más detallada y permite observar eventos con mayor precisión.

- **Banda de baja frecuencia (0 a 20 Hz):** En esta banda, se observan picos claros en color verde y azul claro, lo que indica variaciones en la potencia espectral. Estas variaciones estan relacionadas con los latidos del corazón, más específicamente con las ondas R (pico principal del complejo QRS en el ECG), que suelen tener un alto contenido energético. Los picos periódicos en esta banda reflejan la actividad cíclica del corazón, y los colores más claros (verde/azul claro) indican un aumento de la potencia en esos momentos, lo que corresponde a los latidos del corazón o a eventos específicos del ciclo cardíaco.

- **Banda de alta frecuencia (20 a 100 Hz):** En esta región también hay ciertos picos, aunque menos pronunciados, lo que podría estar asociado con ruido de alta frecuencia o actividad eléctrica relacionada con la contracción muscular del corazón. Las líneas verticales claras en esta banda corresponden a pequeñas interferencias electromiográficas o a fluctuaciones rápidas en la señal.

#### Variaciones de la Frecuencia y Potencia Espectral
A lo largo del tiempo, en la señal se observan fluctuaciones en la potencia espectral, especialmente en la banda baja, lo que indica una actividad cardíaca cíclica. Los picos verdes y azules claros sugieren que hay variaciones en la amplitud del ECG en esos puntos, lo cual representa latidos con mayor energía o variabilidad en la fuerza de los latidos. En cuanto a las frecuencias altas, no se detectan cambios sustanciales a lo largo del tiempo, lo que sugiere que el ruido o las interferencias permanecen relativamente constantes durante el periodo de análisis.

Entonces, frecuencias bajas (0-20 Hz) reflejan la actividad cardíaca, con picos correspondientes a los latidos del corazón (complejos QRS) y variaciones periódicas en la potencia espectral y frecuencias altas (20-100 Hz) están más relacionadas con ruido o actividad de alta frecuencia, pero en este caso, no hay eventos de alta energía que sugieran anomalías significativas.
