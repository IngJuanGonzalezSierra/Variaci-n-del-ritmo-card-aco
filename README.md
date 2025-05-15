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
