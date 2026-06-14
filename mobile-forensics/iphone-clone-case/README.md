\# Análisis Forense de Dispositivo Android Disfrazado como iPhone



\## Descripción



Este caso tiene la finalidad de documentar una investigación de \*\*Mobile Forensics\*\* realizada sobre un dispositivo comercializado como un supuesto \*\*iPhone 17 Pro Max\*\*.



El objetivo fue determinar la autenticidad del equipo, el sistema operativo real, analizar el hardware subyacente y detectar posibles evidencias de manipulación.



La investigación concluyó que el dispositivo no corresponde a un producto Apple, sino a un teléfono Android basado en hardware MediaTek cuya interfaz y firmware fueron modificados para simular un iPhone moderno.



\---



\## Objetivos



\* Verificar la autenticidad del dispositivo.

\* Identificar el sistema operativo real.

\* Determinar el hardware utilizado.

\* Detectar indicadores de falsificación o manipulación.

\* Buscar artefactos digitales residuales.

\* Documentar los hallazgos obtenidos.



\---



\## Principales Hallazgos



\### Sistema Operativo



\* Android 8.1

\* Kernel Linux 3.18.79

\* Arquitectura ARMv7



\### Hardware Identificado



\* Plataforma MediaTek

\* GPU Mali-T720

\* PMIC MT6311

\* Registros internos compatibles con dispositivos MediaTek



\### Indicadores de Falsificación



El dispositivo reportaba información falsa relacionada con componentes Apple, incluyendo referencias a un supuesto procesador:



```text

Apple A18 Pro

```



La evidencia técnica demostró que dicha información había sido modificada mediante manipulación del firmware.



\### Análisis de Evidencia Residual



Se realizó una revisión del almacenamiento interno en busca de:



\* Fotografías

\* Videos

\* Documentos

\* Conversaciones

\* Cuentas configuradas



No se localizaron artefactos suficientes para asociar el dispositivo a usuarios previos.



\---



\## Metodología



La investigación se realizó mediante técnicas de adquisición lógica y análisis no invasivo:



\* Inspección visual

\* Menú de diagnóstico Android

\* Análisis del sistema operativo

\* Identificación de hardware

\* Revisión de registros del sistema

\* Exploración de particiones y almacenamiento

\* Intentos de adquisición mediante ADB



No se realizaron procedimientos destructivos ni modificaciones al dispositivo.



\---



\## Herramientas Utilizadas



\* Device Info HW

\* Android Testing Menu

\* Chrome Diagnostics

\* Android Debug Bridge (ADB)

\* Explorador de Archivos Android

\* Logs del Sistema



\---



\## Competencias Aplicadas



\* Mobile Forensics

\* Digital Forensics

\* DFIR Fundamentals

\* Android Analysis

\* Análisis de Artefactos

\* Recolección de Evidencia

\* Identificación de Hardware

\* Análisis de Logs

\* Documentación Técnica



\---



\## Resultado



La evidencia recopilada permite concluir con un alto nivel de confianza en que el dispositivo analizado corresponde a un teléfono Android basado en MediaTek, cuya apariencia y configuración fueron modificadas para aparentar ser un iPhone moderno.



Este caso demuestra la aplicación de técnicas forenses para la validación de dispositivos móviles y la identificación de falsificaciones tecnológicas.



