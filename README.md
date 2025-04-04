# laboratorio-de-fatiga-muscular-
## Descripción del Experimento:

El experimento tiene como objetivo registrar y analizar señales electromiográficas (EMG) para estudiar la fatiga muscular. Para ello, se colocan electrodos en la piel sobre el músculo a analizar y se adquiere la señal durante una contracción muscular sostenida. Posteriormente, la señal es procesada aplicando filtrado, ventaneo y análisis espectral con la Transformada de Fourier (FFT) para observar cómo cambia la frecuencia con la fatiga.


## Materiales y Equipos del Laboratorio:

**1.** Computador con acceso a internet.

**2.** Software de análisis de señales en Python.

## Materiales y Equipos del Estudiante: 

- Electrodos de superficie para captura de señales EMG (3 unidades).

- Sistema de adquisición de datos (DAQ o similar).

- Gel conductor.

- Fuente de alimentación.

## Objetivos:

1) Aplicar el filtrado de señales continuas para procesar una señal EMG.

2) Detectar la fatiga muscular mediante el análisis espectral de la señal.

3) Evaluar la disminución de la frecuencia mediana como indicador de fatiga.

4) Implementar pruebas de hipótesis para verificar cambios significativos en la señal.

## Estructura del Experimento:

## Preparación del Sujeto:

1) Colocación de electrodos con gel conductor en el músculo a analizar.

2) Configuración del sistema de adquisición de datos (DAQ y software).

3) Definición de la frecuencia de muestreo adecuada.

 - ## Adquisición de la Señal EMG: 

1) Solicitar al sujeto realizar una contracción muscular sostenida hasta la fatiga.

2) Registrar la señal EMG en tiempo real.

- ## Procesamiento de la Señal:

1) Aplicación de filtros pasa altas y pasa bajas para eliminar ruido.

2) Segmentación de la señal en ventanas de tiempo (ventaneo).

3) Aplicación de la Transformada de Fourier (FFT) para análisis espectral.

- ## Análisis de Fatiga Muscular:

1) Evaluación del cambio en la frecuencia mediana.

2) Aplicación de pruebas de hipótesis para determinar si la fatiga es significativa.

## ¿Qué es un DAQ (Sistema de Adquisición de Datos)?

Un DAQ (Sistema de Adquisición de Datos) es un dispositivo o conjunto de dispositivos que capturan señales del mundo real (como temperatura, voltaje,
fuerza o señales biológicas como EMG) y las convierten en datos digitales que pueden ser procesados por una computadora.

[![imagen-2025-04-02-173138606.png](https://i.postimg.cc/x8gjHyyL/imagen-2025-04-02-173138606.png)](https://postimg.cc/9wRjH9kf)

1) ## Componentes principales de un DAQ

- Electrodos EMG → Capturan señales eléctricas de los músculos.

- Termopares → Miden temperatura.

- Acelerómetros → Miden vibraciones o movimiento.

2) ## Circuitos de acondicionamiento de señal

 Las señales capturadas suelen ser muy débiles o ruidosas, por lo que se deben amplificar y filtrar antes de ser digitalizadas,
 como ejemplo se pueden usar estas tecnicas.

- Amplificadores → Aumentan la intensidad de la señal.

- Filtros pasa-altas / pasa-bajas → Eliminan ruidos no deseados.

3) ## Software de Procesamiento y Análisis

Una vez que la señal llega a la computadora, debe ser procesada. Se pueden usar programas como:

- Python (NumPy, SciPy, Matplotlib)

- MATLAB

- LabVIEW

- Excel (para análisis básico)

## ¿Qué son las funciones de ventana?

Las señales en la vida real son infinitas o muy largas, pero los algoritmos (como la FFT) requieren trabajar con segmentos finitos. Para evitar efectos no deseados, se aplican funciones de ventana, que suavizan los bordes de la señal y mejoran la precisión del análisis.

# Tipos de Ventanas

1. Ventana Rectangular
   
- No aplica suavización, simplemente corta la señal bruscamente.
- Ventajas: Simple y rápida.
- Desventajas: Puede generar fugas espectrales porque introduce discontinuidades en los bordes.
- Fórmula:
  
            w(n) = 1,0 ≤ n ≤ N−1
  
- Cuándo usarla: Si la señal ya tiene transiciones suaves o si no te preocupa la fuga espectral.

2. Ventana de Bartlett (Triangular)
   
- Tiene una forma triangular que reduce un poco la fuga espectral en comparación con la rectangular.
- Ventajas: Menos fuga espectral, pero con menor resolución que la rectangular.
- Desventajas: Aún deja pasar algunos efectos no deseados en el espectro.
- Fórmula:

          w(n)= 1-(2∣n-(N-1)/2∣/N-1
  
- Cuándo usarla: Cuando se busca una opción intermedia entre la rectangular y las más suavizadas.

## Ventana de Hanning

- Suaviza la señal aplicando una curva en forma de coseno.
- Ventajas: Reduce significativamente la fuga espectral.
- Desventajas: Pierde un poco de resolución espectral respecto a la rectangular.
- Fórmula:
  
         w(n)=0.5(1−cos(2πn/N-1))
  
- Cuándo usarla: Para análisis de frecuencia donde es importante reducir la fuga espectral.

## Ventana de Hamming
- Similar a la de Hanning, pero con coeficientes diferentes para mejorar la supresión de las frecuencias laterales.
- Ventajas: Menos fuga espectral que Hanning y buena resolución espectral.
- Desventajas: No es tan eficiente para algunas señales con cambios abruptos.
- Fórmula:
  
         w(n)=0.54−0.46cos( 2πn/N-1)
  
- Cuándo usarla: Para señales donde queremos un equilibrio entre reducción de fuga y resolución espectral.

## Ventana de Blackman

- Tiene una forma de coseno más compleja que da una suavización extrema.
- Ventajas: Reduce mucho la fuga espectral.
- Desventajas: Pierde bastante resolución espectral.
- Fórmula:
  
         w(n)=0.42−0.5cos( 2πn/N-1)+0.08cos(4πn/N-1)
  
- Cuándo usarla: Para señales donde la supresión de ruido y la suavización son más importantes que la resolución.

[![imagen-2025-04-02-173705298.png](https://i.postimg.cc/rFtYDFVw/imagen-2025-04-02-173705298.png)](https://postimg.cc/WhT7KVqB)
 
## Inicio del Laboratorio 

1) # Adquision de la señal

1) Coloca los electrodos de superficie (3 en total):

Electrodo activo 1 (positivo): sobre la parte más prominente del músculo.

Electrodo activo 2 (negativo): unos 2-3 cm más abajo sobre el mismo músculo.

Electrodo de referencia (tierra): en una zona ósea o lejos del músculo, por ejemplo en la muñeca o tobillo.

[![imagen-2025-04-03-201924394.png](https://i.postimg.cc/Fz7YBdKt/imagen-2025-04-03-201924394.png)](https://postimg.cc/dZcQ70dn)

2) Aplica gel conductor, ayuda a mejorar la conductividad entre la piel y los electrodos.

3) Conecta los electrodos al sistema DAQ se s igue el manual del DAQ para asegurarte de conectar correctamente las entradas analógicas.

4) Pedir al sujeto que haga contrancciones de la parte del antebrazo y que sea constante 
  
5) Inicia la grabación en Python usando el DAQ, Guarda los datos en un archivo .csv o matriz para su posterior análisis.

6) Mantén la contracción hasta que el sujeto sienta fatiga muscular.Esto puede tomar entre 30 segundos y 2 minutos.

7) Finaliza la grabación y guarda la señal.

#  Filtrado de la señal

 - **Creación de  el filtro Butterworth:**

signal.butter(...) es una función que diseña matemáticamente el filtro.

fc / (self.fs / 2) → se llama frecuencia normalizada, y se usa para que el filtro se adapte a la frecuencia de muestreo (self.fs).

btype='low' → indica que el filtro es pasa-bajas , donde eliminaremos los  ruidos de alta frecuencia y dejando solo lo que es útil para el análisis muscular.

   ## CODIGO
  
def filtrar_senal(self):
    if self.datos is not None:
        fc = 30  # Frecuencia de corte en Hz
        orden = 6  # Orden del filtro
        b, a = signal.butter(orden, fc / (self.fs / 2), btype='low')  # Diseño del filtro
        self.senal_filtrada = signal.filtfilt(b, a, self.datos)  

        self.ax.clear()
        self.ax.plot(self.datos, color='blue', alpha=0.5, label="Señal original")
        self.ax.plot(self.senal_filtrada, color='green', label="Señal filtrada (30 Hz)")
        self.ax.set_title("Señal Filtrada")
        self.ax.set_xlabel("Tiempo (muestras)")
        self.ax.set_ylabel("Amplitud")
        self.ax.legend()
        self.canvas.draw()


# 3) Aventanamiento de la señal
   
