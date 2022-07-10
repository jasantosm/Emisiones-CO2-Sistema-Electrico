# **Proyecto: Análisis de Emisiones de Gases Contaminantes (CO2Eq) Sistema Eléctrico Colombiano**

Realizado por: **Julián Andrés Santos Méndez**

email: ingjuliansantos@gmail.com

A continuación se da un resumen del trabajo realizado.

El análisis completo se encuentra en el notebook principal de este repositorio.

## **Objetivos de negocio y situación actual**

Colombia es un país que se enorgullese de que el 69.25% de su energía eléctrica es generada con recursos renovables, los cuales constituyen una matriz energetica no fósil muy variada con diferentes fuentes, tales como la energía hidráulica, la biomasa, la energía eólica y la energía solar, sin embargo, el 98.5% de esa energía es generada con recursos hidráulicos a gran escala. 

Como consecuencia de esa depedencia a los grandes embalses, se tiene un sistema eléctrico que es muy sensible a fenomenos climáticos como el fenomeno del niño.

*Tabla 1. Capacidad efectiva neta del Sistema Interconectado Nacional (SIN) por tipo de recurso natural, Fuente: Informe 2019 XM S.A. E.S.P. [1]*

| Fuente de energía               | 2018 MW   | 2019 MW   | Participación (%) | Variación 2019 vs. 2018 |
|---------------------------------|-----------|-----------|-------------------|-------------------------|
| **Fuentes de energía No Renovable**
| Combustible fósil               | 5,308.14  | 5,369.74  | 30.75%            | 1.16%                   |
| Total No Renovable              | 5,308.14  | 5,369.74  | 30.75%            | 1.16%                   |
| **Fuentes de energía Renovable**    
| Biomasa                         | 139.60    | 139.60    | 0.80%             | 0.00%                   |
| Eólica                          | 18.42     | 18.42     | 0.11%             | 0.00%                   |
| Hidráulica                      | 11,836.57 | 11,916.61 | 68.24%            | 0.68%                   |
| Solar                           | 9.80      | 17.98     | 0.10%             | 83.43%                  |
| **Total Renovable**                 | **12,004.39** | **12,092.60** | **69.25%**           | **0.73%**                   |
| **Total general**                  | **17,312.53** | **17,462.34** | **100.00%**           | **0.87%**                   |

Para contrarrestar esa dependecia a la energía hidráulica, el país inició el proceso de incoporación de mas activos de generacion térmica con combustibles fósiles[2].

Es por esta razón que **el objetivo** principal de este proyecto es hacer un seguimiento de las emisiones de gases contaminantes que ha hecho el sistema eléctrico Colombiano y determinar su relacion con otras variables del sistema, para así tener una base con la cual analizar en el futuro las emisiones de los nuevos activos térmicos.

## **Planeación del proyecto de análisis de datos**

A continuacion se presenta el plan para la ejecución del presente proyecto:

1. **Definición de las fuentes de información.**
  * *Application Programming Interface* tipo REST (API) de XM S.A. E.S.P.
  * *Web scraping* del informe diario de operación (IDO) de XM S.A. E.S.P.
  * Se solicitaron, al *servicio al ciudadano* de XM S.A. E.S.P., los datos de ubicación de las centrales de generacion del Sistema Eléctrico Colombiano.
2. **Integración: Consolidación de los datasets adquiridos en un solo *DataFrame* con todas las *features*.**
3. **Caracterización de los datos**
  * Verificación del tamaño y forma del DataFrame consolidado
  * Verificación de los tipos de dato.
  * Verificación de las unidades de medida de cada *feature*.
4. **Preparación de los datos**
  * Conversión de los *features* a los tipos de dato adecuados.
  * Busqueda de registros vacíos.
  * Reemplazo de registros vacios por datos válidos, con la justificación adecuada.
  * Caracterización de los datos con estadística descriptiva.
  * Visualización de medidas estadísticas.
  * Conversión de las unidades de medida con numeros grandes a unidades con numeros mas pequeños, sin que se salgan del dominio del sistema internacional de unidades.
  * Cálculo de nuevas *features* que ayuden en el proceso de union (join) de los datasets.
  * Selección de los *features* definitivos que se usarán en el análisis.
5. **Análisis de Datos**
  * Determinación de la correlación de los features.
  * Visualización del *Pair Plot* para ver graficamente como cada uno de los features impacta las emisiones de gases contaminantes.
  * Con el apoyo de las visualizaciones contra el tiempo:
    * Buscar de tendencias (trend) en los features respecto al tiempo usando el grafico Feature vs. Tiempo con énfasis en las emisiones de gases contaminantes.
    * Buscar de comportammientos estacionales (seasonality) de las variables respecto al tiempo usando el grafico Feature vs. Tiempo con énfasis en las emisiones de gases contaminantes.
    * Explicar el impacto del clima en las emisiones del SIN.
    * Explicar el impacto del consumo de combustible en el precio bolsa de la eléctricidad.
6. **Visualización de datos**
  * Construcción un mapa coroplético de Colombia indicando los departamentos con mas emsiones de gases contaminantes debidas al Sistema Eléctrico Nacional.