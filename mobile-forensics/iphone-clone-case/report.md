\# Análisis Forense de Dispositivo Android Disfrazado como iPhone



> Caso de estudio de Mobile Forensics enfocado en la identificación de un dispositivo Android modificado para aparentar ser un iPhone de última generación.



\---



\# Resumen



Durante una investigación técnica se analizó un dispositivo presentado como un \*\*iPhone 17 Pro Max\*\*.



El objetivo fue determinar:



\- Autenticidad del dispositivo.

\- Sistema operativo real.

\- Hardware subyacente.

\- Evidencia de manipulación.

\- Existencia de artefactos digitales residuales.



La investigación concluyó que el equipo corresponde a un dispositivo Android basado en MediaTek cuya interfaz y firmware fueron modificados para aparentar ser un producto Apple.



\---



\# Vista General del Caso



!\[frontal](Evidencia/frontal.jpeg)



!\[reverso](Evidencia/reverso.jpeg)



\---



\# Objetivos



\- Verificar la autenticidad del dispositivo.

\- Identificar sistema operativo y hardware reales.

\- Detectar indicadores de manipulación.

\- Analizar el almacenamiento disponible.

\- Buscar evidencia residual.

\- Documentar hallazgos técnicos.



\---



\# Alcance



La investigación se realizó utilizando técnicas de adquisición lógica y análisis no invasivo.



No se realizaron:



\- Extracción física de memoria.

\- ISP.

\- JTAG.

\- Chip-Off.

\- Root del dispositivo.

\- Modificación del firmware.



\---



\# Metodología



\## Fase 1 - Inspección Inicial



Se realizó una inspección visual del equipo.



\### Observaciones



\- Apariencia similar a dispositivos Apple.

\- Interfaz basada en iOS.

\- Inconsistencias observadas durante la operación.



\---



\# Fase 2 - Identificación del Sistema Operativo



Se accedió al menú de pruebas Android utilizando:



```text

\*#\*#4636#\*#\*

```



\### Evidencia



!\[android\_testing\_menu](Evidencia/android\_testing\_menu.jpeg)



\### Hallazgo



La presencia del menú de pruebas Android confirma que el dispositivo no ejecuta iOS.



\---



\# Fase 3 - Análisis del Sistema



\## Información General



\### Evidencia



!\[informacion\_general](Evidencia/informacion\_general.jpeg)



\---



\## Device Info HW - General



\### Evidencia



!\[device\_info\_general](Evidencia/device\_info\_general.jpeg)



\### Hallazgos



| Parámetro | Valor |

|------------|------------|

| Sistema Operativo | Android 8.1 |

| Kernel | Linux 3.18.79 |

| Arquitectura | ARMv7 |

| ABI | armeabi-v7a |



\---



\## Device Info HW - SoC



\### Evidencia



!\[device\_info\_soc](Evidencia/device\_info\_soc.jpeg)



\### Hallazgos



\- Arquitectura Cortex-A53

\- GPU Mali-T720

\- Arquitectura de 32 bits



\---



\## Device Info HW - System



\### Evidencia



!\[device\_info\_system](Evidencia/device\_info\_system.jpeg)



\---



\## Device Info HW - Sensores



\### Evidencia



!\[device\_info\_sensors](Evidencia/device\_info\_sensors.jpeg)



\### Sensores Funcionales



\- Acelerómetro

\- Sensor de luz

\- Sensor de proximidad



\### Sensores Declarados pero No Funcionales



\- Magnetómetro

\- Giroscopio

\- Barómetro



\---



\# Fase 4 - Análisis de Hardware



\## CPU Reportada



El dispositivo reportaba:



```text

Apple A18 Pro T

```



\### Resultado



La información fue identificada como falsa.



\### Motivos



\- Android 8.1

\- Arquitectura ARMv7

\- GPU Mali-T720

\- Kernel Linux 3.18

\- Componentes MediaTek



\---



\## PMIC



\### Evidencia



!\[pmic](Evidencia/pmic.jpeg)



\### Hallazgo



```text

PMIC = MT6311

```



Componente asociado a plataformas MediaTek.



\---



\# Fase 5 - Evidencia MediaTek



\## Logs del Sistema



\### Evidencia



!\[kernel](Evidencia/kernel.jpeg)



\### Indicadores Encontrados



```text

mtklog

meta\_tst

mt\_cpufreq

MUSB

MTK charger

```



\### Conclusión



Los registros del sistema muestran evidencia consistente con hardware MediaTek.



\---



\# Fase 6 - Diagnóstico mediante Chrome



\## Chrome Version y GPU



\### Evidencia



!\[chrome\_gpu/Evidencia/chrome\_gpu.jpeg]



\### Hallazgos



```text

Android 8.1.0

A08A

Build/O11019

GPU: Mali-T720

Vendor: ARM

OpenGL ES 3.1

```



Esta evidencia constituye una de las pruebas más sólidas para identificar el hardware real.



\---



\# Fase 7 - Análisis del Almacenamiento



\## Estructura Android



\### Evidencia



!\[android_folders](Evidencia/android_folders.jpeg)



\---



\## Particiones



\### Evidencia



!\[particiones](Evidencia/particiones.jpeg)



\### Particiones Observadas



```text

/data

/system

/vendor

/storage/emulated

```



\---



\## Revisión de Directorios



\### Evidencia



!\[android_data](Evidencia/android_data.jpeg)



!\[whatsapp_folders](Evidencia/whatsapp_folders.jpeg)



\### Resultado



No se localizaron:



\- Fotografías

\- Videos

\- Documentos

\- Conversaciones

\- Respaldos

\- Cuentas configuradas



\---



\# Fase 8 - Intentos de Adquisición Avanzada



\## Android Debug Bridge (ADB)



\### Evidencia



!\[adb_devices](Evidencia/adb_devices.jpeg)



\### Resultado



```text

List of devices attached

```



Sin dispositivos detectados.



\---



\# Correlación de Evidencia



| Evidencia | Resultado |

|------------|------------|

| Android 8.1 | Confirmado |

| ARMv7 | Confirmado |

| Mali-T720 | Confirmado |

| MT6311 | Confirmado |

| Logs MediaTek | Confirmado |

| Kernel Linux | Confirmado |

| Información Apple | Falsificada |



\---



\# Hipótesis del Hardware Real



| Plataforma | Probabilidad |

|------------|------------|

| MediaTek MT6753 | 70% |

| MediaTek MT6737 | 20% |

| Otro MT67xx | 10% |



\---



\# Hallazgos Principales



\## Confirmado



✅ El dispositivo no corresponde a un iPhone.


✅ Ejecuta Android 8.1.


✅ Utiliza hardware MediaTek.


✅ El firmware fue manipulado para mostrar información falsa.


✅ El hardware pertenece a una plataforma Android económica.



\---



\## No Encontrado



❌ Fotografías residuales.


❌ Videos residuales.


❌ Conversaciones.


❌ Cuentas configuradas.


❌ Evidencia atribuible a usuarios previos.


\---



\# Conclusión



El análisis permitió determinar con alto nivel de confianza que el dispositivo investigado corresponde a un teléfono Android basado en MediaTek cuyo firmware fue modificado para aparentar ser un iPhone moderno.



La evidencia recopilada permitió identificar múltiples indicadores de falsificación de hardware y software, aunque no se localizaron artefactos suficientes para atribuir el dispositivo a una identidad específica.



\---



\# Competencias Aplicadas



\- Mobile Forensics

\- Android Analysis

\- Digital Forensics

\- DFIR Fundamentals

\- Artifact Analysis

\- Hardware Identification

\- Log Analysis

\- Technical Documentation

\- Evidence Collection

\- Incident Documentation



\---



\# Herramientas Utilizadas



\- Device Info HW

\- Chrome Diagnostics

\- Android Testing Menu

\- Explorador de Archivos Android

\- Logs del Sistema

\- Android Debug Bridge (ADB)



\---



\# Disclaimer



Toda la información potencialmente identificable fue eliminada o anonimizada antes de la publicación de este caso.



Este repositorio tiene fines exclusivamente educativos, de investigación y desarrollo profesional.

