# Actividades STEM comunitarias: RDX en ruta

## Propósito

Organizar visitas prácticas a escuelas, iglesias, clubes juveniles, bibliotecas y centros comunitarios para que niños y jóvenes construyan, prueben y expliquen un sistema sencillo con ESP32. La meta recomendada es completar **10 actividades presenciales** y alcanzar al menos **300 participantes**, documentando el impacto real de cada encuentro.

Esto apoya la opción de participación comunitaria STEM de HERC y el premio **"Paga el favor"**, que reconoce eventos educativos prácticos de alto impacto; una charla o demostración pasiva no basta.

Este archivo es el plan operativo interno. Para la propuesta HERC se extraerá de aquí un plan de una página; para la revisión operativa se usará la evidencia acumulada de cada visita.

## Formato de visita: "Misión RDX"

Duración: 90 minutos. Público objetivo: hasta 40 participantes, organizados en equipos de dos o tres. Esto equivale a 14 equipos de tres, o a 20 equipos si todos trabajan por parejas.

| Tiempo | Actividad | Resultado del participante |
| --- | --- | --- |
| 0-10 min | Presentación del rover, HERC y el reto del día | Entiende qué problema resuelve un rover |
| 10-25 min | Estación 1: LED, pulsador y buzzer con ESP32 | Programa una señal de "rover listo" y una alerta sonora corta |
| 25-40 min | Estación 2: reto de reflejos | Usa pulsadores, LEDs y buzzer para completar una secuencia o responder una pregunta de misión |
| 40-55 min | Estación 3: medición cercana con VL53L0X | Compara una distancia medida con una regla |
| 55-70 min | Estación 4: servo y soporte pan-tilt | Orienta una cámara/sensor hacia un objetivo |
| 70-85 min | Mini misión | Integra una acción y explica la decisión del grupo |
| 85-90 min | Cierre, encuesta corta y foto autorizada | Entrega evidencia y siguiente paso para seguir aprendiendo |

El VL53L0X se usa aquí como ejemplo de medición a corta distancia; no se presenta como el telémetro oficial del rover para la tarea de HERC.

## Kits portátiles para atender varios equipos

Preparar 20 kits iguales para que funcionen sin depender del equipamiento del lugar. Así, los 40 participantes pueden trabajar por parejas sin compartir el montaje con otro equipo; si se organizan de tres, quedan kits disponibles para estaciones y reemplazo.

- ESP32 DevKit, cable USB y *power bank* por kit.
- Protoboard, LEDs con resistencias, dos pulsadores, buzzer pasivo de 3.3 V y cables Dupont.
- Cuatro LCD I2C para rotación por estaciones.
- Cuatro sensores VL53L0X y cuatro conjuntos de servo/soporte pan-tilt para las estaciones compartidas.
- Código de ejemplo precargado y una hoja de misión por equipo. Los retos sugeridos son semáforo/alerta del rover, juego de reflejos y clave sonora de una misión.

La lista de compra electrónica está en la sección **Compra en AliExpress** de [propuesta-sistema-raspberry-pi-4.md](./propuesta-sistema-raspberry-pi-4.md).

## Compra en AliExpress: kits para Actividades STEM

Las cantidades siguientes cubren 20 kits de participantes y repuestos para continuar una visita si se pierde o falla una pieza pequeña. Elegir un único modelo de ESP32 y comprar los cables de datos que correspondan a su conector; no mezclar placas micro-USB y USB-C sin separar claramente los cables.

| Material | Cantidad | Uso | Enlace de búsqueda |
| --- | ---: | --- | --- |
| ESP32 DevKit con pines ya soldados | 24 | 20 kits y 4 repuestos | [Buscar ESP32 DevKit](https://www.aliexpress.com/w/wholesale-esp32-devkit.html) |
| Cable USB **de datos**, según el conector de la placa | 28 | Programación y alimentación; comprobar que no sea solo de carga | [Buscar cable USB de datos](https://www.aliexpress.com/w/wholesale-usb-data-cable.html) |
| Protoboard mini o de 400 puntos | 24 | Una por kit y repuestos | [Buscar protoboard](https://www.aliexpress.com/w/wholesale-400-point-breadboard.html) |
| LEDs de 5 mm surtidos | 300 | Semáforo, alertas y repuestos | [Buscar LEDs de 5 mm](https://www.aliexpress.com/w/wholesale-5mm-led-assorted.html) |
| Resistencias de 220-330 ohmios, 1/4 W | 300 | Limitación de corriente para LEDs | [Buscar resistencias 220 ohm](https://www.aliexpress.com/w/wholesale-220-ohm-resistor.html) |
| Kit surtido de resistencias de 1/4 W | 1 | Valores de apoyo para retos y reparaciones | [Buscar kit de resistencias](https://www.aliexpress.com/w/wholesale-1-4w-resistor-kit.html) |
| Pulsadores táctiles de 6 x 6 mm | 150 | Dos por kit y repuestos | [Buscar pulsadores táctiles](https://www.aliexpress.com/w/wholesale-6x6mm-tactile-push-button.html) |
| Buzzers pasivos de 3.3 V | 30 | Retos de sonido y alarmas cortas | [Buscar buzzer pasivo](https://www.aliexpress.com/w/wholesale-3.3v-passive-buzzer.html) |
| Jumpers macho-macho, 20 cm | 6 juegos de 120 | Cableado principal de protoboard | [Buscar jumpers macho-macho](https://www.aliexpress.com/w/wholesale-dupont-male-to-male-20cm.html) |
| Jumpers macho-hembra, 20 cm | 3 juegos de 120 | LCD, sensores y módulos con conector hembra | [Buscar jumpers macho-hembra](https://www.aliexpress.com/w/wholesale-dupont-male-to-female-20cm.html) |
| Jumpers hembra-hembra, 20 cm | 3 juegos de 120 | Adaptación entre módulos y pruebas | [Buscar jumpers hembra-hembra](https://www.aliexpress.com/w/wholesale-dupont-female-to-female-20cm.html) |
| LCD I2C 16 x 2 con pines soldados | 8 | Seis estaciones y dos repuestos | [Buscar LCD I2C 1602](https://www.aliexpress.com/w/wholesale-i2c-1602-lcd.html) |
| VL53L0X con pines soldados | 8 | Seis estaciones y dos repuestos | [Buscar VL53L0X](https://www.aliexpress.com/w/wholesale-vl53l0x.html) |
| Servo de 9 g | 8 | Estación pan-tilt y repuestos | [Buscar servo 9 g](https://www.aliexpress.com/w/wholesale-mg90s-metal-gear-servo.html) |
| Soporte pan-tilt compatible con servo de 9 g | 5 | Cuatro estaciones y repuesto | [Buscar soporte pan-tilt](https://www.aliexpress.com/w/wholesale-sg90-pan-tilt-bracket.html) |
| *Power bank* de 5 V/2 A o superior | 22 | Alimentación portátil de los kits | [Buscar power bank 5V 2A](https://www.aliexpress.com/w/wholesale-5v-2a-power-bank.html) |
| Fuente USB-C para protoboard, 3.3/5 V, con protección de corto | 24 | Alimenta los rieles de práctica; una por kit y repuestos | [Buscar fuente USB-C protegida para protoboard](https://www.aliexpress.com/w/wholesale-usb-c-breadboard-power-supply-short-circuit-protection.html) |
| Regleta con protección y extensión | 2 de cada una | Carga segura de laptops y kits | [Buscar regleta con protección](https://www.aliexpress.com/w/wholesale-surge-protector-power-strip.html) |
| Estuche rígido o bolsas con cierre, numerados | 24 | Un kit completo por compartimento | [Buscar estuche para electrónica](https://www.aliexpress.com/w/wholesale-electronics-project-case.html) |
| Bridas, cinta aislante y etiquetas | 1 paquete de cada uno | Orden, identificación y reparación ligera | [Buscar consumibles electrónicos](https://www.aliexpress.com/w/wholesale-electronics-cable-management-kit.html) |

Para la **Aula móvil RDX**, llevar 14 laptops reacondicionadas de 11-12 pulgadas para formar hasta 14 equipos de tres. Si el centro solicita trabajo estrictamente por parejas, completar el lote con seis laptops más, para un total de 20. Incluir cargadores, fundas acolchadas y un maletín. Es preferible obtener esos equipos localmente con prueba de batería y garantía, antes que importarlos por AliExpress; los componentes pequeños de la tabla sí son adecuados para compra en lote.

### Fuente USB-C protegida para la protoboard

Usar una **fuente USB-C que se inserta directamente en los rieles de la protoboard**, configurada a `3.3 V`, con protección de sobrecorriente/cortocircuito y recuperación automática o reiniciable. La referencia funcional es **BrodBoost-C**: se alimenta por USB-C, entrega 3.3 o 5 V en los rieles y declara protección de cortocircuito. [Especificaciones de BrodBoost-C](https://www.crowdsupply.com/axiometa/brodboost-c)

Conexión del kit: **power bank USB-C → fuente protegida → rieles `VCC`/`GND` de la protoboard**. El ESP32 se conecta al mismo riel con `3V3` y `GND`, o se alimenta por USB cuando se programa, pero **nunca por ambos métodos a la vez**. Si un niño une `VCC` y `GND`, la fuente corta su salida; se quita el puente y la fuente se recupera o se reinicia con su interruptor. La protección no se consume como un fusible de vidrio.

No comprar un MB102 genérico solo porque diga “protección”: algunos reguladores sobreviven el corto por límite térmico, pero siguen proporcionando corriente y se calientan mucho. El módulo elegido debe indicar explícitamente corte por corto y su prueba debe confirmar que la salida cae a 0 V durante la falla.

Esta fuente protege la alimentación, no los GPIO frente a tensión externa. Los LEDs siempre llevan resistencia y los GPIO se usan como señales, nunca como alimentación. Los servos se alimentan aparte y no pasan por la protoboard.

Antes de comprar las 24 unidades, el equipo técnico prueba tres muestras: alimenta un ESP32, puentea brevemente `VCC` y `GND` en la protoboard y confirma con multímetro que la salida cae a 0 V, no se calienta y se recupera al retirar el puente. Esta prueba la realiza un facilitador, nunca participantes.

## Dos modalidades según la infraestructura del centro

La persona de enlace confirma antes de reservar: cantidad de laptops utilizables, acceso a tomacorrientes, permiso para conectar ESP32 por USB e instalar/controlar software, tamaño y edad del grupo, y autorización de fotografías. Con esa información se elige una modalidad, sin cancelar una visita porque el centro no tenga laboratorio.

### Propuesta A: Aula móvil RDX

Para escuelas, iglesias, bibliotecas o grupos que no disponen de computadoras. RDX transporta un aula compacta con **14 laptops reacondicionadas de 11 a 12 pulgadas**, protegidas en fundas numeradas dentro de un maletín acolchado. Cada laptop atiende a un equipo de hasta tres participantes, de modo que 40 niños trabajan en 14 equipos. Para una jornada organizada por parejas se añaden seis laptops y se llega a 20 equipos.

| Elemento | Criterio práctico | Uso en la visita |
| --- | --- | --- |
| 14 laptops ligeras, ampliables a 20 | 11-12", máximo aproximado 1.3 kg, al menos 4 GB RAM, 64 GB de almacenamiento y cargador identificado | Una por equipo de tres; 20 para trabajo simultáneo por parejas |
| Imagen offline preparada | Arduino IDE, controlador USB del DevKit, soporte ESP32, ejemplos y guía PDF ya instalados | No depender del internet del lugar |
| Maletín y fundas | Compartimentos, inventario numerado y cargadores separados | Transporte cómodo y recuperación rápida del equipo |
| Regletas y extensiones | Con protección y capacidad suficiente para los cargadores | Mantener la jornada sin improvisar conexiones |
| Memoria USB de recuperación | Copia de instaladores, ejemplos y presentaciones | Resolver un equipo sin descargar archivos durante el taller |

Esta modalidad prioriza laptops robustas y reparables, no equipos nuevos de alto costo. Antes de cada salida se cargan, se prueba un ESP32 por laptop y se abre el mismo ejemplo de LED/buzzer. Al terminar, el técnico borra archivos personales que pudieran quedar, carga el inventario y vuelve a guardar cada equipo en su compartimento.

### Propuesta B: Laboratorio anfitrión

Para centros que ya cuentan con laptops, laboratorio de informática o materiales tecnológicos. RDX lleva los **20 kits de electrónica**, dos laptops de facilitación y una memoria USB con el material; el anfitrión aporta las computadoras de los 14 a 20 equipos. Esto permite dedicar más tiempo al reto y atender grupos mayores.

| Antes de la visita | Durante la actividad | Plan de respaldo |
| --- | --- | --- |
| Verificar puertos USB, permisos de instalación y una laptop por equipo o pareja | Cada equipo programa su ESP32, arma el circuito LED-pulsador-buzzer y documenta el resultado | Si no se permite instalar software o falla la red, usar los sketches ya cargados y completar el reto modificando conexiones, secuencias y explicación del diseño |

El código, los controladores y la guía se entregan también en memoria USB para que el docente pueda repetir la actividad. Nunca se asume que el laboratorio tiene internet: los ejemplos y las instrucciones deben funcionar localmente.

## Retos lúdicos de bajo costo

Los tres componentes se usan para que la actividad sea una construcción real y no una demostración:

- **Semáforo del rover:** tres LEDs indican listo, precaución y alto; un pulsador cambia el estado.
- **Alerta de obstáculo:** el VL53L0X activa LED rojo y un beep breve si detecta un objeto cercano.
- **Reto de reflejos:** el buzzer avisa el inicio; gana el equipo que pulse después de encenderse el LED correcto, sin pulsar antes.
- **Código de misión:** el LCD muestra una instrucción y el grupo reproduce un patrón de luz/sonido con pulsadores.

Usar resistencias limitadoras con cada LED y buzzer de baja tensión. El volumen se mantiene bajo y no se emplean sirenas, láseres ni piezas calientes en actividades con menores.

## Itinerarios propuestos

| Ruta | Tipo de institución | Actividad principal | Resultado que se registra |
| --- | --- | --- | --- |
| Escuelas públicas | Primaria alta, secundaria y politécnicos | Misión RDX de 90 minutos | Participantes, equipos construidos y encuesta |
| Iglesias y grupos juveniles | Pastoral juvenil, scouts o clubes de adolescentes | "Rover por una tarde" con LED, LCD y servo | Asistencia, mini misiones completadas y facilitadores |
| Centros tecnológicos comunitarios y bibliotecas | Espacios con computadores o programación | Taller extendido de 2 horas | Proyecto guardado y código QR para continuar |
| Centros con club de robótica | Equipos con experiencia previa | Reto de mejora: sensor, cámara o autonomía | Prototipo, presentación y posible mentoría |
| Jornada anfitriona en ITLA | Grupos invitados de varias instituciones | Tour de rover + feria de estaciones | Visita, demostración y conexión con carreras técnicas |

### Contactos iniciales en Santo Domingo

Estos son candidatos, no alianzas confirmadas. El responsable de enlace debe contactar primero a la dirección/coord. de cada institución y registrar la respuesta.

- Centros públicos de las Regionales 10 y 15 que ya recibieron equipos de robótica de MINERD: priorizar visitas donde el taller complemente un club existente. [Referencia MINERD](https://www.minerd.gob.do/comunicaciones/noticias/minerd-entrega-equipos-de-robotica-a-31-centros-educativos-beneficiando-mas-de-15-mil-estudiantes-de-las-regionales-10-y-15-de-santo-domingo)
- Centros Tecnológicos Comunitarios: proponer una jornada abierta o un ciclo de talleres en un CTC con disponibilidad. [CTC](https://ctc.edu.do/)
- Centros y escuelas con programas de robótica: usar el taller como intercambio técnico y demostración del rover, no como repetición de una clase ya existente. [Ejemplo: Club de Robótica New Horizons](https://newhorizons.edu.do/club-de-robotica/)
- ITLA como sede anfitriona para grupos escolares invitados y para reclutar facilitadores. [ITLA](https://itla.edu.do/)
- Iglesias, bibliotecas y organizaciones barriales: iniciar por los contactos directos del equipo; priorizar grupos juveniles de 20 a 40 personas y un salón con mesas y tomacorrientes.

## Roles de RDX por visita

| Rol | Responsabilidad |
| --- | --- |
| Enlace comunitario | Coordina fecha, permisos, grupo de edad y salón |
| Líder de estación | Explica una estación y verifica que todos participen |
| Técnico de kits | Carga, prueba y recupera ESP32, cables y sensores |
| Seguridad | Supervisa cables, baterías, herramientas y orden del área |
| Documentación | Registra asistencia, resultados, consentimiento y evidencia |
| Comunicación | Prepara una publicación autorizada y etiqueta a la institución |

Cada visita debe tener al menos cuatro facilitadores: un líder general, dos líderes de estación y una persona de documentación/seguridad.

## Evidencia para HERC y presencia pública

Por cada actividad guardar una carpeta con:

1. Nombre de la institución, persona de contacto, fecha y modalidad presencial/virtual.
2. Conteo de participantes por grupo: preescolar-4.º, 5.º-8.º, 9.º-12.º, universitarios y adultos no educadores.
3. Objetivo del taller, estaciones realizadas y resultado de la mini misión.
4. Lista de asistencia y una encuesta de salida de tres preguntas: "¿qué construiste?", "¿qué aprendiste?" y "¿te interesa seguir en STEM?".
5. Fotografías, video corto o cita de participante/docente **solo con autorización** de la institución y de los responsables cuando corresponda.
6. Enlace o captura de la publicación de RDX, evitando publicar rostros de menores sin permiso.

Una demostración del rover abre la conversación, pero el indicador clave es cuántas personas construyeron, midieron, programaron o explicaron algo por sí mismas.

## Cronograma repetible

| Semana | Acción |
| --- | --- |
| 1 | Seleccionar institución, confirmar responsable y revisar requisitos de seguridad/foto |
| 2 | Probar 20 kits, cargar firmware y asignar roles |
| 3 | Realizar visita y completar la hoja de evidencia el mismo día |
| 4 | Publicar material autorizado, enviar agradecimiento y agendar seguimiento |

Repetir el ciclo con una institución nueva o una segunda sesión más avanzada para los grupos que continúen.

## Mensaje inicial de contacto

> Somos RDX, equipo del ITLA que participa en NASA Human Exploration Rover Challenge. Queremos ofrecer sin costo una actividad práctica de 90 minutos para que sus estudiantes trabajen en equipos con ESP32, luces, pantallas y sensores, conectando la experiencia con robótica espacial. Llevamos los kits y facilitadores; solicitamos un salón con mesas, tomacorrientes y un grupo de 20 a 40 participantes. ¿Podemos coordinar una fecha?

## Seguridad y límites

- No usar herramientas de corte, soldadura ni baterías 6S durante talleres infantiles.
- Usar únicamente alimentación USB de 5 V para los kits de participantes, mediante la fuente protegida de cada protoboard; configurar los rieles a 3.3 V y no exponer 5 V directamente.
- El rover completo se muestra con una zona delimitada y sin acceso a partes móviles o antenas.
- Tener autorización previa para fotos/video y respetar la política del centro anfitrión.
- No prometer certificados, donaciones o entregas de equipos sin que el equipo haya aprobado el presupuesto y la logística.

## Fuentes

- [HERC 2027 Handbook](https://www.nasa.gov/humans-in-space/human-exploration-rover-challenge/)
- [MINERD: robótica educativa en Santo Domingo](https://www.minerd.gob.do/comunicaciones/noticias/minerd-entrega-equipos-de-robotica-a-31-centros-educativos-beneficiando-mas-de-15-mil-estudiantes-de-las-regionales-10-y-15-de-santo-domingo)
- [INTEC STEM](https://stem.intec.edu.do/)
- [Centros Tecnológicos Comunitarios](https://ctc.edu.do/)
