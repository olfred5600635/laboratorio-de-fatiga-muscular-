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

## Test de hipotesis o stevens 

El test de hipótesis es una herramienta fundamental en la estadística inferencial, utilizada para determinar si existen diferencias significativas entre dos grupos de datos o condiciones. Este procedimiento se basa en formular dos hipótesis: la hipótesis nula (H₀), que asume que no hay diferencia entre los grupos comparados, y la hipótesis alternativa (H₁), que plantea que sí existe una diferencia estadísticamente significativa. La decisión sobre cuál hipótesis aceptar se toma mediante el cálculo de un valor p, el cual representa la probabilidad de obtener los resultados observados, o más extremos, bajo el supuesto de que la hipótesis nula es cierta. Si este valor p es menor que un umbral predeterminado (comúnmente 0.05), se rechaza la hipótesis nula en favor de la alternativa, concluyendo que existe una diferencia significativa entre los grupos.

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

## INTERFAZ

[![imagen-2025-04-04-203445753.png](https://i.postimg.cc/7hwgNrcj/imagen-2025-04-04-203445753.png)](https://postimg.cc/34f4KV3Z)

**Captura:**  corresponde a adquirir y analizar en tiempo real los datos de la señal EMG mediante un sistema de adquisición de datos (DAQ). Cuando se pulsa el botón "Capturar desde DAQ", el código se conecta al dispositivo (usando, por ejemplo, la librería nidaqmx de National Instruments) y obtiene un bloque de datos en tiempo real.

**Cargar señal:** Al presionar este botón, se lee un archivo CSV  y se extrae la señal

**Filtrar señal:** Se aplica un filtro pasa-bajas Butterworth de orden 6 con una frecuencia de corte de 30 Hz. Esto suaviza la señal y elimina el ruido de alta frecuencia. La interfaz muestra ambas señales: la original (en azul con mayor transparencia) y la filtrada (en verde). Esta comparación permite ver claramente cómo el filtro reduce las fluctuaciones indeseadas.

**Ventana Hanning:** La interfaz aplica una ventana de Hanning a la señal filtrada y genera tambien una ventana hanning a cada pulso de la señal dandonos la media de cada pulso que nos da esa ventana y cada dato que se uso para la media de cada pulso  . Esta operación consiste en multiplicar la señal filtrada por una función ventana que atenúa sus extremos. El resultado se grafica en naranja y se superpone a la señal filtrada, permitiendo apreciar el efecto del aventanamiento, que es fundamental para reducir el fenómeno de fugas espectrales en el análisis de frecuencia.

**Ver las 800 muestras:** Al pulsar este boton nos mostrar las primeras 800 muestras donde se pueden ver los primeros pulsos que dio el sujeto.

**Ver las ultimas  800 muestras:** Al pulsar este boton mostrar las ultimos impuslos que dio el sujeto antes de llegar a la fatiga mostrandonos como cambia los pulsos  

**Espectro FFT:** Al pulsar este botón, se calcula la Transformada Rápida de Fourier (FFT) de la señal filtrada. Se muestra el espectro de frecuencia en una nueva ventana usando una escala logarítmica en el eje y. Esto ayuda a identificar las componentes de frecuencia dominantes, lo cual es esencial para el análisis espectral.

**Test de  hipotesis:** Al pulsar este boton nos dara el teste de stevens o de hipotesis para la los dos ultimos pico tomados mostrandonos tambien la grafica de que datos se tomaron.


#  Filtrado de la señal

 - **Creación de  el filtro Butterworth:**

signal.butter(...) es una función que diseña matemáticamente el filtro.

fc / (self.fs / 2) → se llama frecuencia normalizada, y se usa para que el filtro se adapte a la frecuencia de muestreo (self.fs).

btype='low' → indica que el filtro es pasa-bajas , donde eliminaremos los  ruidos de alta frecuencia y dejando solo lo que es útil para el análisis muscular.

   ## CODIGO
 ## flitrado de la señal
 
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
        
Donde se arroja la siguiente imagen:

![](https://github.com/olfred5600635/laboratorio-de-fatiga-muscular-/blob/main/Se%C3%B1alFil.png)

## Los 800 datos desde 2000



    def ver_800_desde_1(self):
      if self.datos is not None and len(self.datos) > 800:
        self.ax.clear()
        self.ax.plot(self.datos[2000:2800], color='blue', label="800 muestras desde la 2000")
        self.ax.set_title("Vista de 800 muestras desde la muestra 2000")
        self.ax.set_xlabel("Tiempo (muestras)")
        self.ax.set_ylabel("Amplitud")
        self.ax.legend()
        self.ax.grid(True)
        self.canvas.draw()

Este fragmento de código permite visualizar una parte específica de la señal, exactamente 800 datos, empezando desde la posición número 200.
Lo que hace es cortar la señal desde ese punto y mostrarla en la gráfica, para poder observar cómo se comporta esa sección de la señal.

Esot nos ayuda a observar y analisar como los puslsos como se ven en un punto donde hay mas fuerza  y como se observan cuando tienen mas fuerza el sujeto de prueba. 

[![imagen-2025-04-04-180649204.png](https://i.postimg.cc/3r9VGf5k/imagen-2025-04-04-180649204.png)](https://postimg.cc/pyhsbZdv)

## Los 800 datos finales


    def ver_800_ultimas_muestras(self):
      if self.datos is not None:
        self.ax.clear()
        self.ax.plot(self.datos[-800:], color='blue', label="Últimas 800 muestras")
        self.ax.set_title("Vista de 800 últimas muestras")
        self.ax.set_xlabel("Tiempo (muestras)")
        self.ax.set_ylabel("Amplitud")
        self.ax.legend()
        self.ax.grid(True)
        self.canvas.draw()
        
Este código toma las últimas 800 muestras de toda la señal que se cargó y las muestra en la gráfica.

Sirve para observar el comportamiento de la señal al final del archivo, lo cual es muy útil para observar el cambio de fuerza y como se muetra la fatiga en los ultimos datos .


[![imagen-2025-04-04-180911017.png](https://i.postimg.cc/FRpWjz6M/imagen-2025-04-04-180911017.png)](https://postimg.cc/1ngrSmsB)


 ## Aventanamiento de la señal
   
    def analizar_ventanas_hanning(self):
    if self.datos is not None:
        # Este bloque de código analiza la señal y busca los picos más altos (los valores que sobresalen),
        # que son zonas de interés porque ahí están los pulsos que se buscan.
        picos, _ = signal.find_peaks(self.datos, height=np.mean(self.datos))

        resultados = []  # Aquí se guardarán los resultados para mostrarlos en la tabla

        self.ax.clear()
        self.ax.plot(self.datos, color='blue', alpha=0.5, label="Señal Original")

        for pico in picos:
            # Luego, alrededor de cada pico, el programa toma una pequeña parte de la señal
            # (25 datos antes y 25 datos después del pico, es decir, 50 datos en total)
            inicio = max(0, pico - 25)
            fin = inicio + 50

            if fin > len(self.datos):
                continue  # Si nos pasamos del final de la señal, saltamos este pico

            segmento = self.datos[inicio:fin]

            # y le aplica algo llamado una ventana de Hanning
            ventana = signal.windows.hann(50)
            ventana_aplicada = segmento * ventana

            # Luego, el programa calcula la media (el promedio) de esa señal suavizada,
            # lo que permite saber cuán fuerte es ese pico de forma más confiable.
            media = np.mean(ventana_aplicada)
            desviacion = np.std(ventana_aplicada)

            resultados.append((pico, media, desviacion, len(segmento)))

            self.ax.plot(range(inicio, fin), ventana_aplicada, label=f"Ventana en {pico}")

        self.ax.set_title("Picos y Ventanas Hanning")
        self.ax.set_xlabel("Tiempo (muestras)")
        self.ax.set_ylabel("Amplitud")
        self.ax.scatter(picos, self.datos[picos], color='red', label="Picos")
        self.ax.legend()
        self.canvas.draw()

        # Finalmente, todos esos valores (posición del pico, media, desviación y cantidad de datos usados)
        # se muestran en una tabla para poder analizarlos.
        self.mostrar_tabla_hanning(resultados)



Este bloque de código analiza la señal y busca los picos más altos (los valores que sobresalen), que son zonas de interés porque ahí los pulsos que se buscan .

Luego, alrededor de cada pico, el programa toma una pequeña parte de la señal (25 datos antes y 25 datos después del pico, es decir, 50 datos en total) y le aplica algo llamado una ventana de Hanning.

Después, el programa calcula la media (el promedio) y la desviación estándar de esa señal suavizada. Esto permite saber cuán fuerte y consistente es ese pico de una forma más confiable y menos afectada por ruido.

Finalmente, todos esos valores (posición del pico, media, desviación, y cantidad de datos usados) se guardan y se muestran en una tabla para poder analizarlos fácilmente desde la interfaz.


[![imagen-2025-04-04-191032183.png](https://i.postimg.cc/g2PgB1hc/imagen-2025-04-04-191032183.png)](https://postimg.cc/fJB7V251)


[![imagen-2025-04-04-181205571.png](https://i.postimg.cc/k4Ts2Z69/imagen-2025-04-04-181205571.png)](https://postimg.cc/qhCyY1xZ)


 ![](https://github.com/olfred5600635/laboratorio-de-fatiga-muscular-/blob/main/Hanning.png)


## Analisis Espectral 

def espectro_fft(self):
    if self.senal_filtrada is not None:
        N = len(self.senal_filtrada)
        fft_senal = np.fft.fft(self.senal_filtrada)
        fft_senal = np.abs(fft_senal[:N // 2])  # Solo la mitad positiva
        f = np.fft.fftfreq(N, d=1/self.fs)[:N // 2]

        plt.figure("Espectro de Frecuencia (FFT)")
        plt.semilogy(f, fft_senal, color='purple')
        plt.title("Espectro de Frecuencia de la Señal Filtrada")
        plt.xlabel("Frecuencia (Hz)")
        plt.ylabel("Magnitud (escala log)")
        plt.grid(True)
        plt.show()
        
Este fragmento de código realiza el análisis espectral de la señal filtrada utilizando la Transformada Rápida de Fourier (FFT). Primero, se calcula la FFT de la señal filtrada y se obtiene la magnitud del espectro. Luego, se calcula el vector de frecuencias correspondiente y se grafica el espectro en escala logarítmica (usando plt.semilogy) para resaltar las diferencias en magnitud de las componentes de frecuencia. Esto nos permite identificar las frecuencias dominantes en la señal de manera clara y detallada.

Lo cual nos arroja lo siguiente :

![](https://github.com/olfred5600635/laboratorio-de-fatiga-muscular-/blob/main/Espectral.png)

## test de hipotesis 
    def test_hipotesis_hanning(self):
    resultados = self.resultados_hanning
    if len(resultados) < 2:
        messagebox.showinfo("Test de Hipótesis", "Se necesitan al menos dos ventanas para realizar el test.")
        return

    primer_pico = resultados[0][0]
    ultimo_pico = resultados[-1][0]

    inicio_1 = max(0, primer_pico - 25)
    fin_1 = inicio_1 + 50
    inicio_2 = max(0, ultimo_pico - 25)
    fin_2 = inicio_2 + 50

    if fin_1 > len(self.datos) or fin_2 > len(self.datos):
        messagebox.showwarning("Test de Hipótesis", "Una de las ventanas excede los límites de la señal.")
        return

    ventana = signal.windows.hann(50)
    segmento_1 = self.datos[inicio_1:fin_1] * ventana
    segmento_2 = self.datos[inicio_2:fin_2] * ventana

    t_stat, p_value = ttest_ind(segmento_1, segmento_2)

    if p_value < 0.05:
        resultado_hipotesis = "**Hipótesis Alternativa ACEPTADA** (p < 0.05)\nLos datos presentan diferencias significativas."
    else:
        resultado_hipotesis = "**Hipótesis Nula ACEPTADA** (p ≥ 0.05)\nNo hay diferencias significativas entre los datos."

    mensaje = (
        f"Test de Hipótesis entre primer y último pico:\n\n"
        f"Primer pico (índice): {primer_pico}\n"
        f"Último pico (índice): {ultimo_pico}\n\n"
        f"t: {t_stat:.4f}\n"
        f"p: {p_value:.6f}\n\n"
        f"{resultado_hipotesis}"
    )

    messagebox.showinfo("Resultado del Test de Hipótesis", mensaje)

    try:
        with open("resultado_test_hipotesis.txt", "w", encoding="utf-8") as f:
            f.write(mensaje)
        print("Resultado guardado en: resultado_test_hipotesis.txt")
    except Exception as e:
        print("Error al guardar el archivo:", e)

    self.ax.clear()
    self.ax.plot(self.datos, color='lightgray', label="Señal original")
    self.ax.plot(range(inicio_1, fin_1), segmento_1, color='orange', label=f"Ventana 1 (pico {primer_pico})")
    self.ax.plot(range(inicio_2, fin_2), segmento_2, color='magenta', label=f"Ventana 2 (pico {ultimo_pico})")

    self.ax.set_title("Comparación de Ventanas para Test de Hipótesis")
    self.ax.set_xlabel("Tiempo (muestras)")
    self.ax.set_ylabel("Amplitud")
    self.ax.legend()
    self.ax.grid(True)
    self.canvas.draw()

Este fragmento de código realiza una comparación estadística entre dos partes de la señal de EMG (una al principio y otra al final) para ver si hay una diferencia significativa entre ellas.
Primero, el programa detecta los picos más importantes en la señal. Luego, toma dos fragmentos cortos de la señal: uno alrededor del primer pico y otro alrededor del último pico. Cada fragmento contiene 50 datos, centrados en el pico detectado.
Después, el programa aplica una ventana Hanning, que es una forma suave de enfocar esos datos para evitar distorsiones. Esto ayuda a que el análisis sea más preciso.
Con estos dos fragmentos listos, se hace una prueba estadística llamada "test t". Esta prueba sirve para comparar si las dos partes de la señal tienen valores muy distintos o no con la formula:

       t= (μ1-μ2)/√((s1^2/n1)+(s2^2/n2))
donde:
μ= al promedio de los pulso 
s= la desviacion estandar 
n= el numero de dato 
Todo estos datos son proporcionado por la tabla del boton de (ventana hanning)

-  Si el resultado indica que sí hay diferencias significativas, se muestra un mensaje diciendo que la hipótesis alternativa es aceptada. Esto quiere decir que probablemente el sujeto de prueba aplicó más fuerza (o menos) en un momento comparado con otro.

-  Si no hay diferencias, se acepta la hipótesis nula, lo que significa que la señal fue parecida en ambos momentos.

Finalmente, el resultado se muestra en una ventana y también se guarda en un archivo de texto.

[![imagen-2025-04-04-220727276.png](https://i.postimg.cc/0jhZdBYS/imagen-2025-04-04-220727276.png)](https://postimg.cc/MfbyztrZ)


## Resultados y Analisis

# 1)
- Como se peude observar en las graficas de los datos de 800 datos desde 2000 y los 800 datos fianles , se nota una gran diferencias en los pulsos,
  siendo notorio dos cuestiones. La primera cuestionos el numero de picos que se ve en la de 800 datos desde 2000 en el pulso se ven mas picos siendo un total de 8 picos contados pero
  los 800 datos del final se pueden registrar 5 picos siendo un pulso menor y notando una fatiga y la segunda cuestion que nos deja ver la diferencias es el tamaño tan irregulas de los picos en el pulso como se observor en la grafica de los
  800 datos desde los 2000 se ven que los picos se mentienen de una forma mas regular que en los 800 datos finales, esto dejandos analisar que cuando se llego a la fatiga del sujeto de pruebas se pudo observar que en algunas occaciones el sujeto intentara recuperar la fuerza pero igualmenete
  se notaba en ese lapso de tiempo la fatiga del musculo llengando a mostrar esas irregularidad de los picos.

# 2)
- Para analizar esta señal, se aplicó una ventana de Hanning , que "limpia" los datos eliminando ruido y resaltando patrones clave.

-  El gráfico 1 compara la señal original (línea azul) con versiones filtradas usando ventanas de Hanning en diferentes momentos (líneas de colores). Los puntos rojos marcan los picos máximos de fuerza en cada ventana. Al inicio, estos picos son altos (cerca de 3), pero conforme avanza el tiempo (hacia la derecha del eje), disminuyen progresivamente hasta valores cercanos a 1.5 – 2. Esto reflejacómo el músculo pierde capacidad para generar esfuerzo máximo debido a la fatiga. Además, hacia el final de la señal, los picos se vuelven irregulares: algunos suben brevemente (intentos de recuperar fuerza) pero caen rápidamente, indicando que el agotamiento persiste, como se habia dicho en el analisi anterior .

-  El segundo gráfico muestra como la señal original (azul) con la versión filtrada por Hanning (naranja) se contrastan una a la otra mostrando que  La línea naranja es más suave, eliminando fluctuaciones pequeñas y mostrando una tendencia clara: la fuerza disminuye de manera sostenida. Esto confirma que la ventana de Hanning ayuda a identificar cambios graduales en la actividad muscular, incluso en presencia de ruido.

- en conclucion de este analisis se peude decir que En este caso, la Hanning fue elegida porque priorizaba precisión en el tiempo (para detectar picos de fuerza y fatiga) sin sacrificar demasiado la claridad en el dominio frecuencial. La Hamming, aunque útil en aplicaciones donde las fugas son críticas , no era necesaria aquí, ya que el foco estaba en analizar cambios dinámicos en la actividad muscular.

# 3)
-  Los resultados obtenidos muestran que el primer pico identificado en la señal ocurrió en el índice 1, mientras que el último pico detectado se encuentra en el índice 34,661. A través de la prueba t de Student se obtuvo un valor de t = 0.2154 dandonos un  valor bajo de t indicando  que las diferencias entre ambas ventanas de señal no son grandes. y un p-valor = 0.829925. Dado que este último es mayor a 0.05,  aceptando  la hipótesis nula, lo que indica que no hay diferencias significativas entre la actividad muscular en los dos momentos analizados.
Estos resultados sugieren que, en este experimento, la fatiga no generó un cambio estadísticamente significativo en la señal EMG. Esto puede deberse a varios factores, como una insuficiente intensidad en el esfuerzo realizado, una duración inadecuada del experimento, o la necesidad de un análisis más detallado en otras secciones de la señal.

# 4)
-  En este experimento se analizó cómo cambia la señal muscular a medida que se presenta la fatiga. A través de las gráficas iniciales se notó una reducción en el número y tamaño de los picos, lo que indica una pérdida de fuerza con el tiempo. La señal se volvió más irregular, lo que sugiere que el músculo trataba de mantener el esfuerzo pero ya mostraba signos de agotamiento.
Al aplicar una ventana de Hanning para suavizar la señal, se hizo más evidente la caída progresiva en los picos de fuerza, ayudando a identificar mejor los momentos de fatiga. Además, la comparación entre la señal original y la filtrada confirmó una tendencia descendente en la actividad muscular.
Sin embargo, el análisis estadístico con la prueba t de Student no mostró una diferencia significativa entre el inicio y el final del esfuerzo. Esto sugiere que, aunque visualmente se observa un cambio, desde el punto de vista estadístico no fue suficiente para confirmar una diferencia clara.

