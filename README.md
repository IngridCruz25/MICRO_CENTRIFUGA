####   📌 Proyecto Final - Sistemas Embebidos
##### AUTORES:

- Aracely Melva Zubieta Morales
- Ingrid Jazmín Cruz Soruco
- Joseph Santiago Iquize

#### 📚 INTRODUCCIÓN <p>
El presente anteproyecto tiene como objetivo el desarrollo de un prototipo funcional de una centrifuga que permita realizar separaciones de sólidos y líquidos es una de las técnicas más utilizadas en los laboratorios clínicos, biomédicos y de investigación, pues permite la separación de componentes de una muestra mediante la aplicación de la fuerza centrífuga.
</p>

#### 🧩 JUSTIFICACIÓN <p>
En los hospitales y laboratorios, donde los recursos humanos y tecnológicos son limitados es necesario buscar alternativas para cumplir sus funciones,el proyecto busca ofrecer una solución práctica y económica al combinar en un solo equipo las funciones de microcentrífuga y macro centrífuga. De esta forma se reduce el costo de adquisición, el espacio requerido y el mantenimiento, facilitando su uso en laboratorios pequeños, hospitales de segundo nivel y entornos educativos, donde los recursos suelen ser limitados.
</p>

#### 🏥 ALCANCE <p>
El alcance del proyecto comprende el diseño, desarrollo, construcción y validación funcional de un prototipo de centrífuga híbrida capaz de operar como micro y macrocéntrifuga, incluyendo el modelado mecánico de la carcasa, soportes y rotores mediante software CAD; la fabricación de los componentes estructurales mediante impresión 3D; la integración de un sistema de control esclavo para regular la velocidad de rotación
</p>

#### 📚 TECNOLOGÍAS UTILIZADAS <p>
**1. Seguridad:** Los sensores de temperatura son para controlar el estado de los componentes dado que se trabaaja con componentes como la batería. 

**2. Sistemas de comunicación:** El sistema emplea una arquitectura de comunicación sencilla y eficiente basada en tres canales principales. 
- El sensor BME280 utiliza la interfaz I²C, permitiendo la transmisión de datos ambientales (temperatura y presión) mediante un bus digital de dos líneas que reduce el cableado y facilita la integración con el microcontrolador. 
- La medición de la velocidad real del rotor se realiza mediante un encoder incremental, cuya señal se recibe a través de entradas digitales por pulsos en los canales A y B, lo que permite obtener la frecuencia de giro y detectar variaciones dinámicas en las RPM. 
Finalmente, se utiliza comunicación serial para monitorear valores, registrar datos o realizar configuraciones durante la etapa de pruebas y validación del prototipo. Esta combinación de protocolos permite un sistema de control estable, de rápida respuesta y fácilmente ampliable.
</p>

#### DIAGRAMA DE FUNCIONAMIENTO <p>

</p>

#### 🧩 COMPONENTES ELECTRÓNICOS<p>
- Motor Brushless A2212 (1800 KV o 2200 KV) 
- ESC 30A (controlador brushless tipo drone)  
- Módulo encoder de velocidad HC-020K 
- Microcontrolador SP32
- Batería LiPo 3S (11.1 V) 
- Sensor BME280
- Pantalla LCD 
</p>

### 🏥 ESPECIFICACIONES TÉCNICAS<p>
**Control de Velocidad:**
- Rango de RPM: 1,000 - 15,000 RPM ajustable.
- Con una capacidad de 1 a 15kg
- Control digital de tiempo, aceleración y desaceleración

**Adaptabilidad:**
- Energía recargable con baterías.

**Seguridad:**
- Protección contra desequilibrio y sobrecarga.
- Sistema de ventilación para evitar sobrecalentamiento.
</p>

#### ROLES ASIGNADOS <p>
*Aracely Melva: *Modularización del Proyecto, Revisión de piezas no electrónicas y Revisión del código de sensores.

*Joseph Iquize:* Revisión de componentes esenciales (MotorBrushless), Evaluación de costos y Pruebas Físicas.

*Ingrid Cruz:* Simulaciones de diseño, Repositorio, Asignación de tareas FreeRTOS, Revisión tecnológica y Diapositivas.
</p>

#### 📚 MATERIALES<p>
Seleccionados en la primera fase
<p>

### AVANCES<p>
- Revision de los parametros que se debe cumplir con el proyecto
- Evaluacion de tecnologias necesarias
<p>
