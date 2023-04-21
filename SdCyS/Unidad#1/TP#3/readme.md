# $\textcolor{red}{Trabajo\ Practico\ 3: Objetivos}$

- [ ] Comprender los conceptos de sistema dinámico, lazo abierto y lazo cerrado.
- [ ] Analizar las ventajas y desventajas de los sistemas de control dinámico.
- [ ] Conocer los sistemas de control estáticos y su comparación con los dinámicos.
- [ ] Familiarizarse con los sistemas lineales invariantes en el tiempo y sus propiedades matemáticas.
- [ ] Comprender cómo estas propiedades permiten una mejor comprensión y control de los sistemas. 


# $\textcolor{blue}{Cuestionario:}$






- [ ] (1)  Crear un programa en Python utilizando la biblioteca NumPy para simular y analizar un sistema de control dinámico en lazo abierto.
 Realizar unacomparación con el mismo sistema en lazo cerrado.
- [ ] (2)  Crear un programa en Python utilizando la biblioteca Matplotlib para graficar la respuesta al escalón de un sistema de control
 dinámico en lazo cerrado.Analizar la respuesta en función de los parámetros del sistema.
- [ ] (3)  Utilizar un simulador de circuitos electrónicos para simular un sistema de control estático y analizar su comportamiento.
Comparar este sistema con un sistema de control dinámico de similar funcionalidad.
- [ ] (4)  Crear un programa en Python utilizando la biblioteca SciPy para analizar la respuesta en frecuencia de un sistema lineal invariante en el tiempo. 
Graficar la respuesta en magnitud y fase.
- [ ] (5)  Crear un programa en Python utilizando la biblioteca control para diseñar y analizar un controlador proporcional, integral y derivativo (PID) para 
un sistema lineal invariante en el tiempo.


# $\textcolor{orange}{Desarrollo:}$

- [ ] (1)  Crear un programa en Python utilizando la biblioteca NumPy para simular y analizar un sistema de control dinámico en lazo abierto.
 Realizar unacomparación con el mismo sistema en lazo cerrado.
 
 ##

```python
import numpy as np
import matplotlib.pyplot as plt

# Definir parámetros del sistema
Kp = 0.5   # ganancia del controlador proporcional
Ti = 10    # tiempo integral del controlador
T = 100    # tiempo de simulación
dt = 0.1   # paso de tiempo

# Crear arreglo de tiempo
t = np.arange(0, T, dt)

# Crear arreglo de temperatura del proceso
T_process = np.zeros_like(t)

# Crear arreglo de temperatura deseada (setpoint)
T_setpoint = 50 * np.ones_like(t)

# Simulación del proceso en lazo abierto
for i in range(1, len(t)):
    error = T_setpoint[i] - T_process[i-1]   # calcular el error
    T_process[i] = T_process[i-1] + Kp*error*dt/Ti   # actualizar la temperatura del proceso

# Graficar resultados
plt.plot(t, T_process, label='Temperatura del proceso')
plt.plot(t, T_setpoint, 'r--', label='Temperatura deseada')
plt.xlabel('Tiempo (s)')
plt.ylabel('Temperatura (°C)')
plt.legend()
plt.show()


```
![descarga](https://user-images.githubusercontent.com/46485082/233713417-d4953594-35b0-46c6-bd70-175a4f2453b0.png)

#

- [ ] (2)  Crear un programa en Python utilizando la biblioteca Matplotlib para graficar la respuesta al escalón de un sistema de control
 dinámico en lazo cerrado.Analizar la respuesta en función de los parámetros del sistema.
 
 
 #
 
 - [ ] (3)  Utilizar un simulador de circuitos electrónicos para simular un sistema de control estático y analizar su comportamiento.
Comparar este sistema con un sistema de control dinámico de similar funcionalidad.




#
- [ ] (4)  Crear un programa en Python utilizando la biblioteca SciPy para analizar la respuesta en frecuencia de un sistema lineal invariante en el tiempo. 
Graficar la respuesta en magnitud y fase.

```python
import numpy as np
import matplotlib.pyplot as plt
from scipy import signal

# Definir función de transferencia del sistema
systf = signal.TransferFunction([1], [1, 0.5, 1])

# Calcular respuesta en frecuencia
w, mag, phase = signal.bode(systf)

# Graficar respuesta en magnitud
plt.semilogx(w, mag)
plt.xlabel('Frecuencia (rad/s)')
plt.ylabel('Magnitud (dB)')
plt.title('Respuesta en magnitud')
plt.grid(True)
plt.show()

# Graficar respuesta en fase
plt.semilogx(w, phase)
plt.xlabel('Frecuencia (rad/s)')
plt.ylabel('Fase (grados)')
plt.title('Respuesta en fase')
plt.grid(True)
plt.show()

```![descarga (4a)](https://user-images.githubusercontent.com/46485082/233715058-008859e0-5eab-4808-891f-2c68bf2221ff.png)


![descarga (4b)](https://user-images.githubusercontent.com/46485082/233715092-54d85e05-1bed-4d00-95d4-1ca3f8e171e0.png)


#

- [ ] (5)  Crear un programa en Python utilizando la biblioteca control para diseñar y analizar un controlador proporcional, integral y derivativo (PID) para 
un sistema lineal invariante en el tiempo.


 
