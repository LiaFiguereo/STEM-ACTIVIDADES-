# Propuesta electrónica B: Raspberry Pi 4 + periféricos USB

## Objetivo

Construir una alternativa de mayor capacidad de cómputo para recibir comandos APRS, tomar evidencia fotográfica y entregarla rápidamente en microSD. Esta versión usa cámara UVC y receptor SDR por USB; el BMI160 se conecta por I2C porque ese sensor no usa USB.

## Componentes recomendados

| Componente | Uso en el sistema | Interfaz |
| --- | --- | --- |
| Raspberry Pi 4 Model B | Procesamiento APRS, cámara, registro y control de misión | USB, I2C, UART y GPIO |
| Arducam UB0235 UVC | Fotografías a color de baja distorsión | USB 2.0 UVC |
| RTL-SDR Blog V4L | Receptor VHF y conversión de RF a muestras digitales | USB 2.0 + SMA |
| Dipolo de 2 m | Recibe la radio de NASA | SMA al RTL-SDR, no USB directo |
| BMI160 | Registra inclinación/vibración de cámara y rover | I2C (0x68 u 0x69) |
| Servo horizontal (pan) | Ejecuta los giros de campo de visión ordenados por APRS | GPIO PWM de la Pi + placa propia |
| Servo vertical (tilt) | Compensa la inclinación de adelante/atrás mediante BMI160 | GPIO PWM de la Pi + placa propia |
| Controlador de motores existente | Ejecuta movimientos y giro de cámara | UART, CAN, PWM o GPIO aislado |
| Extensión FFC microSD | Reubica la microSD para extraerla junto a la cámara | Lector microSD integrado de la Pi |
| Buck DC-DC ajustable no USB | Reduce la batería 6S para el sistema | Entrada a verificar: mínimo 30 V; salida ajustable |
| Placa de distribución de potencia (pendiente) | Distribuye la salida del buck a Pi y servos | 2 headers de 2 pines + terminal blocks |

## Referencias visuales de los componentes

### Raspberry Pi 4 Model B

<img src="./imagenes/raspberry-pi-4-model-b-referencia.png" alt="Raspberry Pi 4 Model B y sus interfaces" width="360" />

Placa alternativa compartida por el equipo. En esta propuesta se usarán dos de sus puertos USB: uno para cámara y otro para RTL-SDR.

### Cámara USB UVC

<img src="./imagenes/arducam-ub0235-referencia.jpg" alt="Cámara USB Arducam UB0235" width="360" />

La cámara propuesta es la **Arducam UB0235**: UVC, 1 MP, lente M12 de 60 grados y baja distorsión. Linux/Raspberry Pi la reconoce sin driver adicional; se captura por V4L2, no por `libcamera`.

La ficha e imagen del módulo exacto están en [Arducam UB0235](https://www.arducam.com/blog/product/arducam-usb-camera-board-for-computer-1mp-720p-1-4-jxh62-low-distortion-uvc-camera-module-usb2-0-webcam-without-microphone-with-3-3ft-1m-cable/). Se debe montar con el cable USB asegurado y la lente sin obstrucciones.

### BMI160: inclinación y vibración

<img src="./imagenes/bmi160-esphome-referencia.jpg" alt="BMI160, imagen de la documentación indicada por el equipo" width="360" />

Es el BMI160 de la documentación compartida por el equipo. Se instalará solidario al soporte de la cámara, con sus ejes documentados antes de programar la compensación; usa I2C en 0x68 u 0x69.

### Servos del soporte pan-tilt

<a href="https://probots.co.in/robotics-hardware/motors/servo-motors/servo-motors.html"><img src="https://probots.co.in/pub/media/catalog/product/cache/751189c34ab403f5e307ff7fa1040f9d/m/i/mini_servo_motor_sg90_for_arduino_rc_planes_9g_9_gram_high_grade.jpg" alt="Servo micro SG90 de referencia" width="360" /></a>

La foto muestra el formato de servo de tres cables. El modelo definitivo se escogerá tras calcular el torque del soporte, cámara y cable; no asumir que un SG90 basta para la carga final. Se usarán dos unidades del mismo modelo: una para pan y otra para tilt.

### Receptor VHF USB y antena de 2 metros

<a href="https://www.rtl-sdr.com/product/rtl-sdr-blog-v4l-lite-r828s-rtl2832u-1ppm-tcxo-sma-software-defined-radio-dongle-only/"><img src="https://www.sdrstore.eu/images/detailed/10/image_2024-02-26_103655049.png" alt="RTL-SDR USB de referencia" width="360" /></a>

El **RTL-SDR Blog V4L** entra por USB y tiene un conector SMA para la antena. No existe una antena USB: la antena siempre es RF/coaxial y el SDR es quien convierte esa señal a USB para la Pi.

<a href="https://thepihut.com/products/rtl-sdr-blog-v4-usb-dongle-with-dipole-antenna-kit"><img src="https://thepihut.com/cdn/shop/files/rtl-sdr-blog-v4-usb-dongle-with-dipole-antenna-kit-sparkfun-wrl-27543-1176095074.jpg?v=1751374632&amp;width=2048" alt="Kit de dipolo VHF con conector SMA" width="360" /></a>

Referencia visual del dipolo de recepción. Para la frecuencia de HERC, ajustar cada elemento a aproximadamente 51 cm y montarlo verticalmente.

### Extensión de microSD para entrega rápida

<img src="./imagenes/extension-microsd-ffc-referencia.png" alt="Extensión FFC de microSD aportada por el equipo" width="360" />

Este adaptador extiende el lector microSD de la Pi a una posición accesible junto a la cámara. La tarjeta contiene fotos, timestamps y logs; se desmonta por software antes de extraerla y entregarla al juez.

### Buck DC-DC no USB para la batería 6S

<img src="./imagenes/buck-dc-dc-no-usb-referencia.png" alt="Buck DC-DC ajustable aportado por el equipo" width="360" />

Se utilizará el buck DC-DC ajustable aportado por el equipo, sin salida USB. La batería 6S es 22.2 V nominales y llega a **25.2 V** recién cargada: antes de conectarlo, confirmar en la ficha o serigrafía del modelo que acepta al menos 30 V continuos. Ajustar la salida de la rama de Raspberry Pi a 5.1 V antes de conectar la placa.

El buck no se conecta directamente a la Raspberry Pi ni a los servos: alimenta la placa de distribución pendiente. Colocar fusible e interruptor antes del buck; un fusible protege también el cable entre la batería y la entrada del módulo.

### Placa de distribución de potencia pendiente

La placa se construirá con esta topología mínima:

```
Salida + / - del buck -> terminal block de entrada -> PCB de distribución
PCB -> header de 2 pines #1
PCB -> header de 2 pines #2
PCB -> terminal block de salida -> terminal block del arnés
```

Los dos headers y el terminal de salida llevarán positivo y GND. El header reservado para la Raspberry Pi se conectará únicamente a 5 V y GND de su GPIO con un arnés polarizado; el otro queda para la carga definida al cerrar el arnés y el terminal block será la conexión removible hacia los servos. Antes de fabricar la placa, medir la corriente de bloqueo de cada servo y el consumo simultáneo de Pi, cámara y SDR. Si el buck no sostiene esa carga sin caída de tensión, separar una rama regulada exclusiva para los servos.

## Plan A de entrega y estación de PC

El **Plan A** es guardar cada JPEG, su timestamp y el log de misión en la microSD del rover. Al finalizar la secuencia, se cierra la escritura, se desmonta la tarjeta de forma segura y los pilotos la llevan al PER para entregar los resultados.

No se instalará un enlace de radio rover -> PC para copiar imágenes durante la prueba. La norma de HERC exige operación de solo recepción: la antena del rover y cualquier SDR conectado a una PC solo pueden recibir los comandos APRS que transmite NASA; no pueden transmitir fotos, telemetría ni reenvíos APRS. APRS a 1200 baudios tampoco es un medio práctico para imágenes.

La PC con microSD queda como **estación de laboratorio**: puede usar un SDR y una antena receptora para grabar y decodificar las transmisiones de prueba de NASA, y puede copiar la evidencia desde la microSD del rover después de su extracción. No debe formar parte de la cadena inalámbrica de entrega en competencia sin una autorización escrita de HERC.

## Interacción de los bloques

```
Antena 2 m -> SMA -> RTL-SDR USB -> Raspberry Pi 4 -> rtl_fm + Dire Wolf -> parser APRS
                                              |                                  |
                                              |                                  +--> controlador del rover
                                              |                                            |
Batería 6S -> fusible + interruptor -> buck DC-DC -> placa de distribución
                                                        |             |
                                                        |             +--> servos por terminal blocks
                                                        +--> Pi por header de 2 pines ----+ acción autorizada
Cámara UVC USB -------------------------------+                                      acción autorizada
BMI160 por I2C -------------------------------+                                            |
GPIO PWM de Pi -> placa propia -> servo pan + servo tilt -------------------------------+
                                              |                                      microSD extendida
                                              +--> JPEG + timestamp + inclinación
                                                                       |
                                                         desmontaje seguro y entrega en PER
```

1. El RTL-SDR recibe la portadora VHF de NASA mediante la antena de 2 m y entrega muestras IQ por USB.
2. `rtl_fm` demodula FM; Dire Wolf o un decodificador equivalente recupera AX.25/APRS y descarta tramas con FCS incorrecto.
3. Un servicio local de misión valida el formato, deduplica y transforma solo comandos aprobados en acciones internas.
4. Para una orden de imagen, la Pi captura JPEG desde la cámara UVC, añade fecha/hora y guarda el archivo en microSD.
5. Para una orden de movimiento, el servicio envía una orden acotada al controlador del rover y registra el resultado.
6. El BMI160 agrega inclinación/vibración a los logs; se puede usar para rechazar una captura si la cámara está en movimiento.
7. La PC puede repetir la recepción APRS en laboratorio, pero no recibe imágenes desde el rover por radio durante la competencia.

## Cabezal de cámara con dos servos

<img src="./imagenes/soporte-pan-tilt-dos-servos-referencia.png" alt="Soporte pan-tilt de dos servos aportado por el equipo" width="360" />

Sí es viable usar dos servos en un soporte **pan-tilt**:

- El servo horizontal realiza pan. Los comandos APRS `B` y `C` modifican su objetivo en incrementos de 30 grados, dentro de topes mecánicos definidos.
- El servo vertical realiza tilt. El BMI160 mide el ángulo de cabeceo; el software compara esa lectura con el ángulo de referencia calibrado al inicio y ordena el servo vertical en sentido contrario para conservar la cámara nivelada de adelante hacia atrás.

La realimentación debe usar un filtro de inclinación, zona muerta y límite de velocidad para evitar que vibraciones del rover causen oscilación del servo. Antes de cada fotografía, el sistema debe esperar a que el error de inclinación quede dentro de su tolerancia durante un intervalo corto y registrar ese error junto al JPEG.

**Límite importante:** con dos ejes se obtiene pan + compensación de pitch. Si el rover se inclina hacia un costado, el horizonte rota por roll y no puede corregirse sin un tercer servo de roll. Para la primera versión, fijar la cámara rígidamente en roll y validar en pruebas que la inclinación lateral del rover no impida reconocer los objetivos.

### Cableado recomendado

```
Pi GND -> GND placa de distribución/servos (tierra común)
GPIO PWM de Pi #1 -> señal servo pan por la placa propia
GPIO PWM de Pi #2 -> señal servo tilt por la placa propia
Salida de servos de la placa -> alimentación de ambos servos
```

No alimentar los servos desde los pines de 5 V de la Raspberry Pi. La placa propia debe llevar sus pistas de potencia y retornos de servo separados de la rama de Pi hasta el punto de entrada, y un capacitor de reserva cerca de las salidas de servo. Los dos GPIO PWM se validarán a 3.3 V con el modelo de servo final antes de fabricar la placa.

## Cámara USB: Arducam UB0235

La UB0235 es una cámara UVC USB 2.0 de 1 MP con sensor JXH62, lente M12 de 60 grados y distorsión menor a 1%. Entrega MJPEG a 1280 x 720, 640 x 480 o 320 x 240; empezar con 1280 x 720 para las fotografías de evidencia y reducir la resolución solo si las pruebas lo exigen.

La cámara consume hasta 200 mA a 5 V. Debe sujetarse firmemente junto al adaptador de microSD, con alivio de tensión en el cable USB.

## BMI160 y adaptador microSD

El BMI160 no es USB: el fabricante de la documentación compartida indica que requiere I2C, con dirección 0x68 o 0x69. Se conecta a 3.3 V, GND, SDA y SCL de la Pi. Su función es medir aceleración y giro para registrar cuándo una imagen fue tomada con inclinación o vibración excesiva; no reemplaza la cámara ni el receptor APRS.

La extensión FFC de microSD permite extraer rápidamente la tarjeta sin abrir el rover. Nunca retirar la tarjeta durante una escritura: el sistema debe terminar el archivo, ejecutar desmontaje seguro y confirmar en pantalla/LED que está lista. Confirmar con HERC si el juez aceptará la microSD como medio de entrega; el handbook exige entregar los resultados en el PER, pero no prescribe el formato de entrega.

## Receptor APRS y seguridad RF

- La Raspberry Pi no es receptora VHF: el RTL-SDR USB recibe RF y entrega muestras a Linux.
- La antena no es USB: el dipolo se conecta por SMA al RTL-SDR. Ajustar ambos elementos a aproximadamente 51 cm para 146 MHz y montarlos en vertical.
- El sistema es solo de recepción. El RTL-SDR y el dipolo elegidos son de recepción; no incorporar un transmisor ni PTT.
- Todo paquete debe superar FCS/CRC y una lista cerrada de comandos antes de afectar el rover.

## Alimentación, interferencia y montaje

- Crear una línea regulada de 5.1 V para la Pi, cámara UVC y RTL-SDR; no compartir el regulador de motores sin filtrado.
- Alimentar la placa de distribución desde la batería 6S mediante el buck no USB. Instalar un fusible en serie **antes** del buck; la batería llega a 25.2 V, por lo que no basta un módulo cuyo máximo de entrada sea 24 V.
- La placa pendiente recibe la salida por un terminal block y distribuye a dos headers de 2 pines y a un terminal block de salida mediante otro terminal block. Etiquetar polaridad y usar conectores que eviten inversión.
- La entrada por GPIO evita el conector USB-C de la Pi y sus protecciones de entrada: verificar dos veces polaridad y tensión antes de conectar el arnés de 2 pines.
- Ajustar y medir la salida de la rama de Pi en 5.1 V tanto sin carga como con carga. Si aparece el icono de bajo voltaje o la tensión cae al mover servos, separar la alimentación de servos en una segunda rama regulada.
- La Pi 4 limita la corriente total de sus USB a aproximadamente 1.1 A. Medir consumo real de cámara y SDR en la prueba de estrés; usar un hub USB con alimentación propia interna si no queda margen.
- Usar un convertidor DC-DC de calidad, fusible, protección de polaridad y capacitores cerca de Pi y RTL-SDR.
- Ubicar antena, coaxial y SDR lejos de ESC, motores y convertidores conmutados. Sujetar cámara, extensión FFC y cables USB con alivio de tensión.

## Ventajas y riesgos

| Ventajas | Riesgos que se deben probar |
| --- | --- |
| Componentes intercambiables por USB | Cámara UVC y SDR comparten presupuesto de corriente USB |
| Dire Wolf/Linux simplifican APRS | Pi requiere apagado limpio y fuente de 5 V robusta |
| MicroSD accesible para entrega rápida | La extensión FFC debe probarse contra errores de lectura/escritura |
| BMI160 registra estabilidad durante la captura | Debe mantenerse separación eléctrica de motores |
| Pan y compensación de pitch en dos ejes | No compensa roll; un tercer eje sería necesario si las pruebas lo requieren |

## Pruebas de aceptación

1. Verificar 100 capturas UVC consecutivas, timestamp y guardado en microSD sin red.
2. Reproducir APRS válido e inválido a través de RTL-SDR; confirmar FCS, deduplicación y lista cerrada.
3. Ejecutar cámara, SDR, BMI160 y motores simultáneamente; medir pérdida de paquetes y consumo USB.
4. Probar 100 ciclos de desmontaje, extracción y lectura de microSD usando la extensión FFC.
5. Inclinar el rover adelante/atrás y verificar que el servo tilt vuelve a la referencia sin oscilar ni golpear topes.
6. Enviar repetidamente comandos `B` y `C`; verificar giros de 30 grados, topes y que pan no desactiva la estabilización de tilt.
7. Ensayar la secuencia completa sin Internet, sin transmisión RF y con el rover listo para competencia.
8. Con la batería 6S a 25.2 V y a su nivel mínimo operativo, ejecutar cámara, SDR, microSD y servos durante 15 minutos; comprobar que el buck y la placa de distribución no se calientan en exceso, que la Pi no indica bajo voltaje y que los conectores no presentan caída apreciable.

## Compra en AliExpress

Al abrir cada búsqueda, seleccionar destino **República Dominicana**, ordenar por pedidos/valoración y activar el filtro **Envío gratis**. Confirmar en el checkout que la variante elegida sí conserva ese envío y coincide con la especificación indicada.

| Material | Cantidad | Enlace de búsqueda |
| --- | ---: | --- |
| Raspberry Pi 4 Model B | 2 | [Buscar Pi 4 Model B](https://www.aliexpress.com/w/wholesale-raspberry-pi-4-model-b.html) |
| Cámara UVC Arducam UB0235 | 2 | [Buscar UB0235](https://www.aliexpress.com/w/wholesale-arducam-ub0235.html) |
| Receptor RTL-SDR Blog V4/V4L con SMA | 2 | [Buscar RTL-SDR V4](https://www.aliexpress.com/w/wholesale-rtl-sdr-blog-v4.html) |
| Kit de antena dipolo VHF con SMA | 2 | [Buscar dipolo RTL-SDR](https://www.aliexpress.com/w/wholesale-rtl-sdr-dipole-antenna.html) |
| Módulo BMI160 GY-BMI160, I2C/SPI | 2 | [Buscar BMI160](https://www.aliexpress.com/w/wholesale-gy-bmi160.html) |
| Módulo VL53L0X ToF auxiliar de corto alcance | 2 | [Buscar VL53L0X](https://www.aliexpress.com/w/wholesale-vl53l0x.html) |
| Servos 9 g, mismo modelo para pan y tilt | 4 | [Buscar servo 9 g](https://www.aliexpress.com/w/wholesale-mg90s-metal-gear-servo.html) |
| Soporte pan-tilt para servos de 9 g | 2 | [Buscar soporte pan-tilt](https://www.aliexpress.com/w/wholesale-sg90-pan-tilt-bracket.html) |
| Extensión FFC para microSD de Raspberry Pi | 2 | [Buscar extensión microSD FFC](https://www.aliexpress.com/w/wholesale-raspberry-pi-microsd-extension-cable.html) |
| MicroSD A1/U3, 64 GB o mayor | 2 | [Buscar microSD A1/U3](https://www.aliexpress.com/w/wholesale-microsd-card-a1-u3-64gb.html) |
| Buck XL4015 o equivalente, 4-38 V de entrada, 5 A | 2 | [Buscar buck XL4015](https://www.aliexpress.com/w/wholesale-xl4015-5a-buck-converter.html) |
| Portafusible en línea y fusibles | 2 | [Buscar portafusible](https://www.aliexpress.com/w/wholesale-inline-blade-fuse-holder.html) |
| Interruptor DC | 2 | [Buscar interruptor DC](https://www.aliexpress.com/w/wholesale-dc-rocker-switch.html) |
| Terminal blocks de 2 pines | 4 | [Buscar terminal blocks 2P](https://www.aliexpress.com/w/wholesale-2-pin-screw-terminal-block.html) |
| Headers macho/hembra de 2 pines | 4 | [Buscar headers 2P](https://www.aliexpress.com/w/wholesale-2-pin-header-2.54mm.html) |
| Cable de silicona 18 AWG para potencia | 2 | [Buscar cable 18 AWG](https://www.aliexpress.com/w/wholesale-18-awg-silicone-wire.html) |
| Cable de silicona 22 AWG para señales | 2 | [Buscar cable 22 AWG](https://www.aliexpress.com/w/wholesale-22-awg-silicone-wire.html) |
| Capacitores electrolíticos de reserva, 1000 uF 10 V o mayor | 2 | [Buscar capacitores](https://www.aliexpress.com/w/wholesale-1000uf-10v-electrolytic-capacitor.html) |

## Fuentes

- [Arducam UB0235: cámara UVC para Raspberry Pi](https://www.arducam.com/blog/product/arducam-usb-camera-board-for-computer-1mp-720p-1-4-jxh62-low-distortion-uvc-camera-module-usb2-0-webcam-without-microphone-with-3-3ft-1m-cable/)
- [RTL-SDR Blog V4L](https://www.rtl-sdr.com/product/rtl-sdr-blog-v4l-lite-r828s-rtl2832u-1ppm-tcxo-sma-software-defined-radio-dongle-only/)
- [RTL-SDR: kit dipolo de recepción](https://www.rtl-sdr.com/using-our-new-dipole-antenna-kit/)
- [BMI160: conexión I2C](https://new.esphome.io/components/sensor/bmi160/)
- [Raspberry Pi 4: alimentación y límites USB](https://www.raspberrypi.com/documentation/hardware/rpi/os.html)
- [Raspberry Pi 4: requisito de alimentación USB-C de 5 V/3 A](https://www.raspberrypi.com/documentation/computers/getting-started.html)
- *2027 Human Exploration Rover Challenge Handbook*, tarea de exploración e información de radio.
