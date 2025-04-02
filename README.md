# laboratorio-de-fatiga-muscular-
## Descripción del Experimento:

El experimento tiene como objetivo registrar y analizar señales electromiográficas (EMG) para estudiar la fatiga muscular. Para ello, se colocan electrodos en la piel sobre el músculo a analizar y se adquiere la señal durante una contracción muscular sostenida. Posteriormente, la señal es procesada aplicando filtrado, ventaneo y análisis espectral con la Transformada de Fourier (FFT) para observar cómo cambia la frecuencia con la fatiga.


## Materiales y Equipos del Laboratorio:

Computador con acceso a internet.

Software de análisis de señales en Python.

## Materiales y Equipos del Estudiante: 

Electrodos de superficie para captura de señales EMG (3 unidades).

Sistema de adquisición de datos (DAQ o similar).

Gel conductor.

Fuente de alimentación.

## Objetivos:

1) Aplicar el filtrado de señales continuas para procesar una señal EMG.

2) Detectar la fatiga muscular mediante el análisis espectral de la señal.

3) Evaluar la disminución de la frecuencia mediana como indicador de fatiga.

4) Implementar pruebas de hipótesis para verificar cambios significativos en la señal.

## Estructura del Experimento:

1) ## Preparación del Sujeto:

1)Colocación de electrodos con gel conductor en el músculo a analizar.

2)Configuración del sistema de adquisición de datos (DAQ y software).

3)Definición de la frecuencia de muestreo adecuada.

2) ## Adquisición de la Señal EMG:

1)Solicitar al sujeto realizar una contracción muscular sostenida hasta la fatiga.

2)Registrar la señal EMG en tiempo real.

3) ## Procesamiento de la Señal:

1)Aplicación de filtros pasa altas y pasa bajas para eliminar ruido.

2)Segmentación de la señal en ventanas de tiempo (ventaneo).

3)Aplicación de la Transformada de Fourier (FFT) para análisis espectral.

4) ## Análisis de Fatiga Muscular:

1)Evaluación del cambio en la frecuencia mediana.

2)Aplicación de pruebas de hipótesis para determinar si la fatiga es significativa.

## ¿Qué es un DAQ (Sistema de Adquisición de Datos)?

Un DAQ (Sistema de Adquisición de Datos) es un dispositivo o conjunto de dispositivos que capturan señales del mundo real (como temperatura, voltaje,
fuerza o señales biológicas como EMG) y las convierten en datos digitales que pueden ser procesados por una computadora.

[![imagen-2025-04-02-173138606.png](https://i.postimg.cc/x8gjHyyL/imagen-2025-04-02-173138606.png)](https://postimg.cc/9wRjH9kf)

1) ## Componentes principales de un DAQ

-Electrodos EMG → Capturan señales eléctricas de los músculos.

-Termopares → Miden temperatura.

-Acelerómetros → Miden vibraciones o movimiento.

2) ## Circuitos de acondicionamiento de señal

 Las señales capturadas suelen ser muy débiles o ruidosas,
 por lo que se deben amplificar y filtrar antes de ser digitalizadas,
 como ejemplo se pueden usar estas tecnicas.

-Amplificadores → Aumentan la intensidad de la señal.

-Filtros pasa-altas / pasa-bajas → Eliminan ruidos no deseados.

3) ## Software de Procesamiento y Análisis

Una vez que la señal llega a la computadora, debe ser procesada. Se pueden usar programas como:

-Python (NumPy, SciPy, Matplotlib)

-MATLAB

-LabVIEW

-Excel (para análisis básico)

## ¿Qué son las funciones de ventana?

Las señales en la vida real son infinitas o muy largas, pero los algoritmos (como la FFT) requieren trabajar con segmentos finitos. Para evitar efectos no deseados, se aplican funciones de ventana, que suavizan los bordes de la señal y mejoran la precisión del análisis.

# Tipos de Ventanas

1. Ventana Rectangular
   
- No aplica suavización, simplemente corta la señal bruscamente.
- Ventajas: Simple y rápida.
- Desventajas: Puede generar fugas espectrales porque introduce discontinuidades en los bordes.
- Fórmula:
  
            w(n) = 1,0 ≤ n ≤ N−1
  
-Cuándo usarla: Si la señal ya tiene transiciones suaves o si no te preocupa la fuga espectral.

2. Ventana de Bartlett (Triangular)
- Tiene una forma triangular que reduce un poco la fuga espectral en comparación con la rectangular.
- Ventajas: Menos fuga espectral, pero con menor resolución que la rectangular.
- Desventajas: Aún deja pasar algunos efectos no deseados en el espectro.
-Fórmula:

          w(n)= 1-(2∣n-(N-1)/2∣/N-1
  
-Cuándo usarla: Cuando se busca una opción intermedia entre la rectangular y las más suavizadas.

3. Ventana de Hanning
- Suaviza la señal aplicando una curva en forma de coseno.
- Ventajas: Reduce significativamente la fuga espectral.
-Desventajas: Pierde un poco de resolución espectral respecto a la rectangular.
- Fórmula:
  
         w(n)=0.5(1−cos(2πn/N-1))
  
-Cuándo usarla: Para análisis de frecuencia donde es importante reducir la fuga espectral.

4. Ventana de Hamming
- Similar a la de Hanning, pero con coeficientes diferentes para mejorar la supresión de las frecuencias laterales.
- Ventajas: Menos fuga espectral que Hanning y buena resolución espectral.
- Desventajas: No es tan eficiente para algunas señales con cambios abruptos.
- Fórmula:
  
         w(n)=0.54−0.46cos( 2πn/N-1)
  
-Cuándo usarla: Para señales donde queremos un equilibrio entre reducción de fuga y resolución espectral.

5. Ventana de Blackman
- Tiene una forma de coseno más compleja que da una suavización extrema.
- Ventajas: Reduce mucho la fuga espectral.
- Desventajas: Pierde bastante resolución espectral.
- Fórmula:
  
         w(n)=0.42−0.5cos( N−12πn)+0.08cos( N−14πn )
  
-Cuándo usarla: Para señales donde la supresión de ruido y la suavización son más importantes que la resolución.

[![imagen-2025-04-02-173252301.png](https://i.postimg.cc/MKFqSGsZ/imagen-2025-04-02-173252301.png)](https://postimg.cc/fJm67Mn1)
