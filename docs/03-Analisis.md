# Un primer análisis de datos {#Analisis}
La **importancia** del análisis de datos es requerida para tomar decisiones y conocer muy bien lo que cada una de las variables nos esta indicando, es por esto que recurrimos a la **estadística** y hacemos uso de las distintas medidas de tendencia central ampliamente conocidas como _media_, _desviación estándar_ (varianza), _asimetría_ y _curtosis_.

## Métricas  

\BeginKnitrBlock{definition}\iffalse{-91-80-114-111-109-101-100-105-111-32-111-32-109-101-100-105-97-32-97-114-105-116-109-233-116-105-99-97-93-}\fi{}<div class="definition"><span class="definition" id="def:media"><strong>(\#def:media)  \iffalse (Promedio o media aritmética) \fi{} </strong></span>Es una característica central de un grupo de datos u observaciones, se denomina muchas veces como la esperanza matematica (valor esperado) y esta compuesto por la sumatoria de todos los elementos dividos por el total de ellos.
$$\bar{X}= \frac{\sum \limits_{i=1}^{n} x_{i}}{n}$$
</div>\EndKnitrBlock{definition}
_Donde (n) es el tamaño de la muestra y (x) la variable de interés con sus observaciones (i) hasta (n)._

En **R** solo es cargar los datos con los que se pretende trabajar y empezar aplicar cada una de las formulas (funciones) y con esto tener las metricas que se requieren para un primer análisis


```r
library(readxl) # Paquete para leer archivos de excel de Microsoft 
#Se carga la base con la que se va a trabajar
Pruebadatos <- read_excel("C:/Users/keyne/Downloads/Pruebadatos.xlsx")

# Promedio de una variable: El signo $ solo selecciona una de las variables de la base

mean(Pruebadatos$Salarios) #En este caso Salarios
```

```
## [1] 222381.4
```

Lo que nos indica que los salarios de los individuos de la base en promedio son de unos $222.381. 

\BeginKnitrBlock{definition}\iffalse{-91-86-97-114-105-97-110-122-97-93-}\fi{}<div class="definition"><span class="definition" id="def:des"><strong>(\#def:des)  \iffalse (Varianza) \fi{} </strong></span>Regularmente se expresa como $(\sigma^2)$ y nos dice que tan dispersa esta una serie de observaciones con respecto a la media o promedio aritmético. Es una resta al cuadrado dividido por el tamaño muestral.  

$$Var (X)=\frac{\sum \limits_{i=1}^{n} (x_{i} - \bar{x})^{2}}{n}$$
</div>\EndKnitrBlock{definition}
_Donde (n) es el tamaño muestral, (x) la variable y (\bar{x}) su respectiva media o promedio aritmético, _

Dentro del programa solo hay que escribir

```r
var(Pruebadatos$Salarios)
```

```
## [1] 7878422680
```

Brindando como resultado 7878422680. Con el propósito de realizar una mejor _lectura_ de la varianza, podemos extraer su raíz cuadrada, o directamente en **R** colocar el comando de la _desviación estandar_ que es (sd)


```r
sd(Pruebadatos$Salarios)
```

```
## [1] 88760.48
```

Y con este valor de 88760.48, podemos decir que tan dispersos esta cada uno de los salarios de la muestra con respecto a la media o promedio.

\BeginKnitrBlock{definition}\iffalse{-91-65-115-105-109-101-116-114-237-97-93-}\fi{}<div class="definition"><span class="definition" id="def:asi"><strong>(\#def:asi)  \iffalse (Asimetría) \fi{} </strong></span>Es denominada el tercer momento de una distribución. Tiene los elementos del promedio y la varianza y sirve para medir que tan concentrados estan los datos de una distribución. Suele clasificarse como asimetría **positiva** y **negativa**.  

$$Asímetría=\frac{\mu^{3}}{\sigma^{3}}$$
</div>\EndKnitrBlock{definition}
_El término de $\mu$ es el mismo del promedio muestral solo que elevado al cubo_.

Primero que todo, hay que instalar el paquete **moments** del CRAN^[Es el acrónimo de Comprehensive R Archive Network y es desde donde se pueden descargar los paquetes para trabajar en el programa de R.] y esto se hace así


```r
install.packages("moments")
```

Luego de instalado, ya se puede hacer uso de los momentos de asímetria y curtosis respectivamente para calcular las métricas de la variable de interés



```r
library(moments) 
#Asimetría
skewness(Pruebadatos$Salarios)
```

```
## [1] 0.9690956
```

Para este caso podemos afirmar con el valor de 0.97 existe una asimetría **positiva**, lo que indica que hay cierta variación de los salarios hacia la izquierda de la distribución de los salarios, pero que hay una gran participación de salarios menores a la media.


\BeginKnitrBlock{definition}\iffalse{-91-67-117-114-116-111-115-105-115-93-}\fi{}<div class="definition"><span class="definition" id="def:skw"><strong>(\#def:skw)  \iffalse (Curtosis) \fi{} </strong></span>Es denominada como el cuarto momento de una distribución. Nos indica que forma tiene la varianza de la variable. Podemos decir que si esta $K=3$, es **mesocurtica** y su varianza es estable y su forma gráfica es similar a la de una distribución normal o Gaussiana. Si por el contrario, su valor es $K<3$ podemos identificarla como **platicurtica** y su varianza es alta. Por último si $K>3$ tendremos una distribución de forma **leptocurtica** y la indicación es una varianza pequeña.  

$$\frac{\sum \limits_{i=1}^{n} (x_{i} - \bar{x})^{4}}{n\sigma^{2}}-3$$
</div>\EndKnitrBlock{definition}

_El término de $x_{i}$ son cada una de las observaciones, (n) el número total de observaciones, $\bar{x}$  el mismo del promedio muestral_.



```r
#Curtosis
kurtosis(Pruebadatos$Salarios)
```

```
## [1] 3.268191
```

La forma de la Curtosis puede indicarnos que tan "volátiles" son nuestros datos, para este caso arrojó un resultado de 3.26, que nos define a los _salarios_ que siguen una distribución de forma mesocurtica y que posee una varianza estable, _lo que quiere decir que entre los salarios de los individuos no existe demasiada diferencia_.

## Los resúmenes de métricas
Existen un grupo de paquetes que permiten de igual forma realizar **resumenes** de estas métricas por grupo de variables y tener el mismo resultado que lo anterior. En esta parte lo haremos con el paquete **skimr**

Este se instala de tal manera que:


```r
install.packages("skimr")
```

Luego de instalado el paquete, ya se puede hacer uso desde la biblioteca del programa **R** y nos dará como resultado una tabla bastante amplia de acuerdo a la composición que tenga dicha base.


```r
library(skimr)

skim(Pruebadatos)
```


Table: (\#tab:unnamed-chunk-8)Data summary

|                         |            |
|:------------------------|:-----------|
|Name                     |Pruebadatos |
|Number of rows           |11          |
|Number of columns        |4           |
|_______________________  |            |
|Column type frequency:   |            |
|numeric                  |4           |
|________________________ |            |
|Group variables          |None        |


**Variable type: numeric**

|skim_variable | n_missing| complete_rate|      mean|       sd|     p0|      p25|    p50|      p75|   p100|hist                                     |
|:-------------|---------:|-------------:|---------:|--------:|------:|--------:|------:|--------:|------:|:----------------------------------------|
|Salarios      |         0|             1| 222381.36| 88760.48| 115000| 178097.5| 197000| 259500.0| 420000|▅▇▂▂▂ |
|Edad          |         0|             1|     28.27|     7.55|     18|     21.5|     25|     35.5|     38|▇▃▁▂▇ |
|Experiencia   |         0|             1|      6.27|     4.82|      0|      1.5|      6|     10.5|     13|▇▂▂▃▆ |
|CI            |         0|             1|     96.09|     8.78|     85|     91.5|     93|     98.0|    114|▂▇▁▁▂ |

Encontramos para este ejemplo, los resultados del número de filas (n) y columnas^[Incluso si se encuentran completas o existen datos perdidos o valores en blanco.], la clasificación que poseen cada una de las variables y las estadísticas de tendencia central incluyendo los percentiles que van desde el primero, hasta la mediana o (p50) y así hasta los valores mayores p100 de cada una de ellas. De igual forma aparece un minigráfico de histograma que en la sección [de gráficas](#Graficos) ampliaremos su explicación y uso.

\BeginKnitrBlock{example}\iffalse{-91-65-110-225-108-105-115-105-115-32-100-105-114-101-99-116-111-93-}\fi{}<div class="example"><span class="example" id="exm:exam11"><strong>(\#exm:exam11)  \iffalse (Análisis directo) \fi{} </strong></span>Del conjunto de variables de la base de datos, encontramos las variables de salarios, edad, experiencia y el resultado obtenido en su prueba de coeficiente intelectual (CI). Dentro de las carácteristicas a reconocer, se encuentra que la edad promedio de los individuos es de 28 años, quien mas edad tiene su dato es de 38 años y quien menos tiene, apenas 18. De la prueba de CI, quien mas resultado obtuvo sacó 114 y el promedio para las 11 observaciones es de 96.1, nada mal para ese grupo como tal</div>\EndKnitrBlock{example}

## Datos cualitativos

Es común tambien intentar medir algunas variables cuya naturaleza son condiciones **cualitativas**



