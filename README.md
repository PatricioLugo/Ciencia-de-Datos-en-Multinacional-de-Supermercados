# Ciencia-de-Datos-en-Multinacional-de-Supermercadp

## Introducción
Abrir una sucursal de una multinacional de supermercado (En este caso utilizamos como ejemplo Walmart), sugiere un gran riesgo de inversión: el poder crear y mantener un supermercado es altamente costoso y el no tener considerados todos los gastos mayores que implica y los aspectos demográficos de la sucursal puede resultar en una gran pérdida de dinero. Así pues, se puede utilizar la ciencia de datos --tanto conocimientos de estadística y probabilidad como de programación-- para poder asegurar que los riesgos son minimizados y a su vez, garantizar el éxito de la sucursa o simplemente dar retroalimentación fundamentada de por qué se debería buscar otra alternativa.
Este proyecto consiste precisamente en eso: crear un análisis completo de la factibilidad de abrir una sucursal de supermercado mediante la proyección y análisis de datos dada una región específica donde se planea abrir la sucursal (en este caso Juriquilla, Querétaro).

## Primer cálculo
### Maximum Likelihood Estimation
Cuando hablamos de Likelihood, nos referimos a la siguiente función de densidad de probabilidad conjunta de datos, donde todos los datos son independientes, están igualmente distribuidos y tienen un cierto número de parámetros:

![image](https://github.com/user-attachments/assets/f45c83e3-8028-41c2-a9c8-6a08f826e036)

En ella lo que buscamos es encontrar el valor de los parámetros que maximice Ln (Likelihood). **Notemos que se usan logaritmos naturales para transformar la función en una sumatoria y que así resulte más sencilla la realización de cálculos**
Así pues, las fórmulas que se encuentran para dichos parámetros se les denomina estimadores de maximum likelihood.

## Aplicación en el análisis de viabilidad de la sucursal
Ahora que estamos contextualizados y hemos establecido brevemente en qué consiste el Maximum Likelihood Estimation, podemos aplicar éste y otros conocimientos de probabilidad y estadística para encontrar una solución a nuestra problemática. Cabe mencionar que todos los cálculos se hicieron utilizando el archivo adjunto "SuperMarketData.csv" con los valores de las ventas convertidos de pesos a dólares.
Nótese que tanto para la distribución de las ventas como del rating se puede observar un tipo de distribución denominada distribución beta, donde la función de densidad está definida de 0 a 1.

### Parámetros alfa y beta
Lo primero que debemos hacer es encontrar los parámetros alfa y beta (propios de una función de densidad beta) que maximice el resultado de nuestra función. Para hacerlo utilizaremos Python.
Iniciamos importando las librerías y los datos necesarios para realizar los cálculos:

![image](https://github.com/user-attachments/assets/f5a4b30c-7927-43e7-b908-9451aaf4ba6b)

Ahora normalizamos los datos:

![image](https://github.com/user-attachments/assets/eea97594-f923-4d8b-9334-5c6dcee1b6e7)

Utilizando la función beta.fit() de scipy podemos fácilmente calcular beta y alfa:

![image](https://github.com/user-attachments/assets/1770eaec-65f7-48e1-944c-f68240de032e)
![image](https://github.com/user-attachments/assets/1f5d5526-e3e2-44d0-9291-3ac9b15358fd)

### Cálculo de la media mu y la desviación estándar
Lo que procede es calcular la media y la desviación estándar de los datos de las ventas, esto lo haremos sabiendo que para calcular ambas, se utilizan las siguientes fórmulas:

![image](https://github.com/user-attachments/assets/b9c42925-612f-4817-98d1-5e672c6ecaaf)

Así pues, implementamos las fórmulas en nuestro programa:
**Cabe aclarar que primero estamos calculando la media, desviación y varianza normalizadas y posteriormente las "desnormalizamos"**

![image](https://github.com/user-attachments/assets/d05617cd-88f3-4dbe-aa82-9bbb48942b39)

### Salarios
Ahora hay que establecer los salarios dadas las fuentes dadas y los parámetros especificados. Así pues, también calcularemos la nómina total:

![image](https://github.com/user-attachments/assets/1aa3d4ac-73e4-4cf0-b52d-e4d6259f34a2)

### Gasto de Luz
Además de pagarle a los empleados del supermercado, es importante considerar también el gasto de la luz, ya que es muy significativo y tendrá un impacto importante en los ingresos del supermercado:

![image](https://github.com/user-attachments/assets/66b8f550-a8b9-4a1c-8c33-0393d3fa57bf)

### Ingreso
De manera muy simple, calcularemos el ingreso deseado sumándole a los gastos el 1,500,000 que se busca obtener de ganancia:

![image](https://github.com/user-attachments/assets/b8573f4c-f9f9-4cbc-8671-811b16bcbaba)

### Implementación del Teorema de Límite Central
Ahora, utilizaremos el Teorema de Límite Central para encontrar en base al ingreso deseado, el tamaño de la población que se necesita alcanzar.
**Es importante notar que obtendremos dos resultados, de los cuáles sólo uno es correcto, puesto que con el otro se indetermina el cálculo intermedio**

![image](https://github.com/user-attachments/assets/7c205d92-90b2-4a80-9529-fd69e9bf76b1)

![image](https://github.com/user-attachments/assets/9bf1dcae-f757-4d94-81e7-419739f6bc2b)

Notemos que el porcentaje de la población que debe alcanzar el supermercado es del 25%.

### Conclusiones en relación a las ventas
De esta manera, hemos podido calcular los gastos que implicará la creación y mantenimiento del supermercado y a su vez la cantidad de personas a las que se tiene que alcanzar para que se obtenga el ingreso deseado.

### Consideraciones del Rating
Además de las ventas, también contamos con información relevante sobre el rating que se le da al supermercado semejante.
Primero, visualizaremos la distribución de los datos graficando con Python:

![image](https://github.com/user-attachments/assets/a1ae9929-5c5e-4ced-a563-63baabc83dde)

![image](https://github.com/user-attachments/assets/cff42aed-abe9-485b-8cd6-4cd1f16f3de6)

Como podemos observar en el gráfico, no parece que haya una tendencia clara hacia ninguna distribución en específico, fuera de que el rating se encuentra entre el 4 y el 10. De esto podemos concluir que no hay ni una predilección especial ni lo contrario por el supermercado en cuestión.
Ahora, para saber cuál es la probabilidad de que en la sucursal que abramos, si los datos que usamos fue en una comunidad semejante a la de Juriquilla, de que en promedio tengan un rating de 8.5 o más usaremos nuevamente el Teorema de Límite central y usaremos un proceso de cálculo de parámetros análogo al que hicimos con las ventas (es decir, que asumiremos una función de densidad beta y encontraremos la media y la varianza de acorde a eso):

![image](https://github.com/user-attachments/assets/e95cc17c-41ad-40f3-b344-d9039ba7b40f)

![image](https://github.com/user-attachments/assets/32307341-6f52-4a98-8d76-302258116a16)

Así pues, podemos concluir que la probabilidad de que el rating sea mayor a 8.5 es aproximadamente del 49%.
En base a este resultado le diría a los del departamento de atención a clientes que el supermercado va bien encaminado según la probabilidad obtenida, ya que es bastante significativa, sin embargo, es claro que puede mejorarse y por lo tanto habría que hacer los ajustes necesarios en el servicio al cliente para mejorar la calificación de la sucursal.

## Mejora de Análisis
A pesar de que hemos logrado hacer un análisis bastante completo, es cierto que puede ser mejorado. Hay datos que podrían ser ajustados para ser más cercanos a la realidad o parámetros que se le agreguen al cálculo de los gastos, como lo pueden ser otros servicios además de la luz o el pago de otros empleados anteriormente no considerados.

### Gasto de Luz
El primer cambio que haremos será cambiar el tiempo que se utiliza la luz a 24 horas. Para hacerlp, tan sólo cambiamos el factor de la fórmula que previamente representaba las 12 horas al día de uso de luz a 24:

![image](https://github.com/user-attachments/assets/1e90f288-7729-465d-9cf3-82abc7b4c1fd)

### Mantenimiento y Reparaciones
Otro cambio que haremos, será añadir al gasto total lo que cuesta el mantenimiento y las reparaciones mensuales del supermercado. De acuerdo a Sheykin (2024), lo mínimo que se gasta mensualmente en esto son 5,000 dólares. Así pues, lo agregaremos en el código y lo convertiremos a pesos:

![image](https://github.com/user-attachments/assets/db6c7e78-5364-4f75-a15f-f96abed94758)

### Residuos
Un último ajuste que haremos, será considerar el gasto que se genera para la gestión de residuos, de acuerdo a Sheykin (2024), esto es mínimamente igual a 2,000 dólares:

### Cambios en los Resultados
Así pues, estos pocos cambios que hicimos tuvieron un gran impacto en los cálculos: el aumento en gastos dada la consideración de más factores resultó en un cambio radical en la cantidad de personas que debe tener como cliente el supermercado para alcanzar el objetivo de ganancias que se busca. Ahora, más del 40% de la población objetivo debe ser alcanzada, es decir, más de 3,000 personas adicionales deben de comprar en el supermercado:

![image](https://github.com/user-attachments/assets/ac749d31-f886-44c3-a4cd-833e5d90bfab)
