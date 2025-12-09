# MICRO_CENTRIFUGA
Proyecto Final - Sistemas Embebidos
📌 MICRO-MACRO CENTRIFUGA

AUTORES: 
- Aracely Zubieta
- Ingrid Cruz
- Joseph Iquize

INTRODUCCIÓN
El presente anteproyecto tiene como objetivo el desarrollo de un prototipo funcional de una centrifuga que permita realizar separaciones de sólidos y líquidos es una de las técnicas más utilizadas en los laboratorios clínicos, biomédicos y de investigación, pues permite la separación de componentes de una muestra mediante la aplicación de la fuerza centrífuga. 

🧩 JUSTIFICACIÓN
En los hospitales y laboratorios, donde los recursos humanos y tecnológicos son limitados es necesario buscar alternativas para cumplir sus funciones,el proyecto busca ofrecer una solución práctica y económica al combinar en un solo equipo las funciones de microcentrífuga y macro centrífuga. De esta forma se reduce el costo de adquisición, el espacio requerido y el mantenimiento, facilitando su uso en laboratorios pequeños, hospitales de segundo nivel y entornos educativos, donde los recursos suelen ser limitados. 

🏥 ALCANCE 
El alcance del proyecto comprende el diseño, desarrollo, construcción y validación funcional de un prototipo de centrífuga híbrida capaz de operar como micro y macrocéntrifuga, incluyendo el modelado mecánico de la carcasa, soportes y rotores mediante software CAD; la fabricación de los componentes estructurales mediante impresión 3D; la integración de un sistema de control esclavo para regular la velocidad de rotación

📚 TECNOLOGÍAS UTILIZADAS
Seguridad: Los sensores de temperatura son para controlar el estado de los componentes dado que se trabaaja con componentes como la bateria Lipo 
Sistemas de comunicación:El sistema emplea una arquitectura de comunicación sencilla y eficiente basada en tres canales principales. El sensor BME280 utiliza la interfaz I²C, permitiendo la transmisión de datos ambientales (temperatura y presión) mediante un bus digital de dos líneas que reduce el cableado y facilita la integración con el microcontrolador. La medición de la velocidad real del rotor se realiza mediante un encoder incremental, cuya señal se recibe a través de entradas digitales por pulsos en los canales A y B, lo que permite obtener la frecuencia de giro y detectar variaciones dinámicas en las RPM. Finalmente, se utiliza comunicación serial para monitorear valores, registrar datos o realizar configuraciones durante la etapa de pruebas y validación del prototipo. Esta combinación de protocolos permite un sistema de control estable, de rápida respuesta y fácilmente ampliable.

DIAGRAMA DE FUNCIONAMIENTO
<img width="518" height="349" alt="image" src="https://github.com/user-attachments/assets/4e505761-be3d-4e30-b7c2-da0b6e814951" />

COMPONENTES
-Motor Brushless A2212 (1800 KV o 2200 KV)
-ESC 30A (controlador brushless tipo drone)
-Sensor BME280
-Módulo encoder de velocidad HC-020K
-Batería LiPo 3S (11.1 V)
-Pantalla LCD
-Microcontrolador SP32

ESPECIFICACIONES TÉCNICAS

Control de Velocidad:
- Rango de RPM: 1,000 - 15,000 RPM ajustable.
- Con una capacidad de 1 a 15kg
- Control digital de tiempo, aceleración y desaceleración
  
Adaptabilidad:
- Energía recargable con baterías.
  
Seguridad:
- Protección contra desequilibrio y sobrecarga.
- Sistema de ventilación para evitar sobrecalentamiento.
  
ROLES ASIGNADOS
Aracely Melva: Modularizacion del Proyecto,Revision de piezas no electronicas, revisor de codigo de sensores
Joseph Iquize: Revision de componentes escenciales(MotorBrushless), Evaluacion de costos, Pruebas Fisicas
Ingrid Cruz: Simulaciones de diseño , Revision de tecnologica

AVANCES
- Revision de los parametros que se debe cumplir con el proyecto 
- Evaluacion de tecnologias necesarias
  
2do avance
- Seleccion de Materiales
