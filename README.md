# 💡 MICRO MACRO CENTRÍFUGA - ESP32
**Proyecto Final - Sistemas Embebidos**

Este repositorio contiene el desarrollo de un **sistema embebido** para una Micromacrocentrífuga, capaz de controlar un motor de alta velocidad mediante un **ESC**, medir las **RPM reales con un encoder**, registrar **temperatura interna** mediante un **BME280**, y permitir al usuario manipular la velocidad mediante un potenciómetro.

El sistema está diseñado bajo una arquitectura modular y escalable, preparada para migrar a **FreeRTOS**, y optimizada para aplicaciones biomédicas de giro y separación de muestras.

[📎 CARPETA DE DISEÑO 3D](https://github.com/IngridCruz25/MICRO_CENTRIFUGA/tree/92060eb0a3998ebec707785761aa640f046ac42a/DISE%C3%91O)

## 🧩 JUSTIFICACIÓN

En hospitales y laboratorios con recursos limitados, la adquisición de múltiples equipos puede ser costosa e impráctica. Por ello, esta centrífuga híbrida busca:

✔ Ofrecer una alternativa accesible para centros educativos y hospitales de segundo nivel.

✔  Reducir costos de adquisición y mantenimiento.

✔ Ahorrar espacio.

## 🏥 ALCANCE DEL PROYECTO

El proyecto comprende:

- Diseño mecánico CAD (carcasa, soportes, rotor).

- Simulaciones estructurales (SolidWorks / Fusion 360).

- Fabricación en impresión 3D.

- Montaje de un sistema de control embebido basado en ESP32 + ESC + Encoder.

- Validación de RPM, estabilidad, vibración y temperatura.

## 🧪 TECNOLOGÍAS UTILIZADAS
**1. Sensores y Seguridad**

BME280: monitoreo de temperatura, humedad y presión interna.

Control de batería LiPo: protección contra descarga peligrosa.

**2. Sistema de Comunicación**

- I²C → BME280

- Serial UART → Monitoreo de pruebas

- Entradas digitales → Encoder incremental

## ⚙ DIAGRAMA DE FUNCIONAMIENTO
![🖼 DIAGRAMA FUNCIONAL](https://github.com/IngridCruz25/MICRO_CENTRIFUGA/blob/92060eb0a3998ebec707785761aa640f046ac42a/IMG/3%20DIAGRAMA%20FUNCIONAL.jpeg)

## 🔌 COMPONENTES ELECTRÓNICOS

A continuación se presenta una tabla técnica de los componentes principales:
| COMPONENTE | MODELO | FUNCIÓN | GPIO | DESCRIPCIÓN |
| - | - | - | - | - |
| ESC (motor) | Brushless	A2212 | Generar rotación de alta velocidad	Alta estabilidad, eficiencia, usado en drones | 4 |	Control PWM 1000–2000 us |
| Potenciómetro	| Genérico | Regular la intensidad | 34 | Entrada ADC 12 bits |
| Encoder | HC-020K | Alta precisión en pulsos | 27 | Pulso por interrupción |
| PANTALLA LCD | 16X2 I2C | Interfaz usuario	Permite mostrar RPM y estado | SDA - 21 / SCL - 22 | Comunicación BME280 |
 | BATERÍA | LIPO | Alta descarga, estable para motores brushless | Alimentsción | 3S (11.1V) |
 | ESP 32 | WROOM I2C | Control principal	WiFi, Bluetooth, multitarea con FreeRTOS | SDA - 21 / SCL - 22 | Comunicación BME280 |
 | BME280 | Sensor ambiente| Muy preciso, bajo consumo
 |  | Comunicación BME280 | 

![COMPONENTES](https://github.com/IngridCruz25/MICRO_CENTRIFUGA/blob/92060eb0a3998ebec707785761aa640f046ac42a/IMG/2%20COMPONENTES%20ELECTR%C3%93NICOS.jpeg)


## 🔍 DESCRIPCIÓN GENERAL DEL FUNCIONAMIENTO

**1. Control de velocidad por potenciómetro (0–100%)**
→ Genera una señal PWM de 1000–2000 µs hacia el ESC.

**2. Medición precisa de RPM mediante interrupciones**
→ Encoder HC-020K con 40 pulsos por vuelta.

**3. Lectura de temperatura interna del rotor**
→ Sensor BME280 vía I2C.

**4. Cálculo de RPM cada 500 ms**
→ Algoritmo basado en conteo de pulsos en ventana fija.

**5. Monitoreo en tiempo real por puerto serial**
→ ADC, PWM, RPM, temperatura, estados.

## 🎯 FUNCIONAMIENTO DE MÁQUINA DE ESTADOS 

🔸 **INIT – Inicialización**

Configura los periféricos ESC, ADC del potenciómetro, interrupción del encoder, bus I2C y detección del BME280.
- El sistema no avanza hasta establecer condiciones mínimas de seguridad.

🔸 **INPUT READ – Lectura del Potenciómetro**

El microcontrolador convierte la entrada analógica (0–4095) y la transforma proporcionalmente a un pulso PWM entre 1000–2000 µs.

🔸 **MOTOR DRIVE – Control del Motor**

El PWM calculado se envía al ESC, gestionando la aceleración del motor brushless dentro de límites seguros (estabilidad y suavidad en respuesta).

🔸 **RPM MONITOR – Medición de Velocidad**

Cada 500 ms se calcula la velocidad del rotor usando los pulsos del encoder y la fórmula estándar de RPM.

🔸 **ENVIRONMENT READ – Monitoreo Ambiental**

Si el BME280 fue detectado, se registra la temperatura interna del sistema.
Si falla, se continúa sin esta medición pero sin afectar el funcionamiento del motor.

🔸 **LOGGING – Reporte por Serial**

Cada 500 ms se envía un paquete con:

- ADC (entrada del usuario)

- PWM enviado al ESC

- RPM medidas

- Temperatura (si disponible)

## ✨ CARACTERÍSTICAS PRINCIPALES
✔ Control del motor mediante ESC: PWM 50 Hz, rango seguro 1000–2000 microsegundos y aceleración suave.

✔ Medición de RPM con encoder: ISR optimizada, eliminación de ruido y precisión alta incluso a velocidades elevadas.

✔ Sensado ambiental; I2C nativo, lectura de temperatura para evitar sobrecalentamiento y lista para expansión (humedad y presión).

✔ Interfaz simple y robusta: Potenciómetro para control manual, lecturas cada 500 ms y serial para monitoreo y pruebas.

## 📐 ARQUITECTURA DEL SOFTWARE

**Tareas FreeRTOS implementadas**

| TAREA | FUNCIÓN |
 | - | - |
 | Control PWM | Ajusta microsegundos enviados al ESC |
 | ISR del encoder | Captura pulsos del rotor |
 | Cálculo de RPM | Convierte pulsos → RPM reales |
 | Lectura de BME280 | Obtiene temperatura interna |
| Interfaz Serial |	Muestra datos en tiempo real |

**Módulos incluidos**

| MÓDULO |  |
 | - | - |
 | ESC | Control directo del motor con señal PWM |
 | BME280 | Lectura de temperatura del rotor |
 | encoder | Interrupción + conteo de pulsos |
 | rpm_control | Conversión matemática a RPM |
| adc_input | Conversión del potenciómetro |
| serial_monitor | Mostrar ADC, PWM, RPM, T° |

## 🧱 BLOQUES DEL PROYECTO

A continuación se detalla la estructura conceptual del proyecto en bloques de desarrollo, cada uno con su propósito, actividades y criterios de finalización.

### BLOQUE 🅐 — Infraestructura del Firmware

| CARACTERISTICA | DESCRIPCIÓN | 
| - | - |
| Propósito | Establecer el control base del motor, la lectura de sensores y la interfaz mínima de prueba |
| Actividades | Inicialización de UART a 115200 |
| | Configuración de potenciómetro (ADC 12 bits) |
| | Inicialización de ESC |
| | Configuración de I2C para BME280 |
| | Configuración de interrupción del encoder |

**Criterios de finalización:**

- El ESC responde correctamente

- El ADC proporciona valores estables

- El encoder ya genera pulsos válidos

### BLOQUE 🅑 — Hardware básico y control manual

| CARACTERÍSTICA | DESCRIPCIÓN |
| - | - |
| Propósito | Permitir operar la centrífuga manualmente como un equipo real |
| Actividades | Mapeo lineal potenciómetro → PWM |
|  | Escritura al ESC |
|  | Verificación de temperatura básica |

**Criterios de finalización:** 

El motor responde a los cambios del potenciómetro

No hay saltos bruscos de velocidad

La temperatura se lee correctamente

### BLOQUE 🅒 — Medición real de RPM

| CARACTERÍSTICA | DESCRIPCIÓN | 
| - | - |
| Propósito | Lograr medición confiable incluso a alta velocidad |
| Actividades | Implementar ISR limpia |
| | Calcular RPM con ventana temporal |
| | Validar que RESOLUTION = 40 pulsos/vuelta |
| | Mostrar RPM por serial |

**Criterios de finalización:**

- Error de medición < 5% en velocidad estable

- RPM estables durante toda la prueba

### BLOQUE 🅓 — Máquina de Estados (FSM) 
![MÁQUINA DE ESTADOS](https://github.com/IngridCruz25/MICRO_CENTRIFUGA/blob/92060eb0a3998ebec707785761aa640f046ac42a/IMG/5%20FMS.jpeg)

### BLOQUE 🅔 — Validación y pulido final

**Pruebas realizadas**

Prueba	Resultado
Lectura de potenciómetro	✔ estable
Variación de PWM	✔ 1000–2000 μs
Encoder en alta velocidad	✔ pulsos sin pérdida
BME280 temperatura	✔ ok
Test de estabilidad térmica	✔ sin sobrecalentamiento

**Ajustes finales:**

- Minimización de jitter en PWM

- Ajuste fino en cálculo de RPM

- Debounce por software si se agregan botones

## 📐 ESPECIFICACIONES TÉCNICAS DEL PROTOTIPO
🌀 **Control de Velocidad**

Rango de RPM: 1.000 – 15.000 RPM ajustable.

Control digital de aceleración y frenado.

🧱 **Capacidad**

Capacidad del rotor: 1 a 15 kg (dependiendo del tipo de porta–tubos).

Sistema híbrido para microtubos (1.5–2 mL) y tubos grandes.

🛡 **Seguridad**

Protección contra desbalance.

Sensor ambiental para evitar sobrecalentamiento.

![DIAGRAMA DEL MOTOR](https://github.com/IngridCruz25/MICRO_CENTRIFUGA/blob/92060eb0a3998ebec707785761aa640f046ac42a/IMG/4%20DIAGRAMA%20DEL%20MOTOR.jpeg)

## 👤 ROLES ASIGNADOS

- Aracely Melva	Modularización, revisión mecánica, revisión de sensores
- Joseph Iquize	Motores, pruebas físicas, costos
- Ingrid Cruz	Simulaciones, repositorio, FreeRTOS, revisión tecnológica, diapositivas

## DOCUMENTACIÓN

[Recopilación de Documentación](https://github.com/IngridCruz25/MICRO_CENTRIFUGA/tree/92060eb0a3998ebec707785761aa640f046ac42a/DOCS)

## 👥 AUTORES

Proyecto desarrollado por los estudiantes: 
- [@Ingrid Jazmín Cruz Soruco](https://github.com/IngridCruz25)

- [@Aracely Melva Zubieta Morales](https://github.com/AracelyZubieta)

- [@Joseph Santiago Iquize Condori](https://github.com/josephiquize-674)
