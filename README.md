# Ciencia-de-Datos-en-Multinacional-de-Supermercadp

## Introducción
Abrir una sucursal de una multinacional de supermercado (En este caso utilizamos como ejemplo Walmart), sugiere un gran riesgo de inversión: el poder crear y mantener un supermercado es altamente costoso y el no tener considerados todos los gastos mayores que implica y los aspectos demográficos de la sucursal puede resultar en una gran pérdida de dinero. Así pues, se puede utilizar la ciencia de datos --tanto conocimientos de estadística y probabilidad como de programación-- para poder asegurar que los riesgos son minimizados y a su vez, garantizar el éxito de la sucursa o simplemente dar retroalimentación fundamentada de por qué se debería buscar otra alternativa.
Este proyecto consiste precisamente en eso: crear un análisis completo de la factibilidad de abrir una sucursal de supermercado mediante la proyección y análisis de datos dada una región específica donde se planea abrir la sucursal (en este caso Juriquilla, Querétaro).

## Maximum Likelihood Estimation
Cuando hablamos de Likelihood, nos referimos a la siguiente función de densidad de probabilidad conjunta de datos, donde todos los datos son independientes, están igualmente distribuidos y tienen un cierto número de parámetros:

![image](https://github.com/user-attachments/assets/f45c83e3-8028-41c2-a9c8-6a08f826e036)

En ella lo que buscamos es encontrar el valor de los parámetros que maximice Ln (Likelihood). **Notemos que se usan logaritmos naturales para transformar la función en una sumatoria y que así resulte más sencilla la realización de cálculos**
Así pues, las fórmulas que se encuentran para dichos parámetros se les denomina estimadores de maximum likelihood.
