# Datos {#Datos}

Una de las cosas mas importantes que debe hacer todo economista al hacer uso de **R**, es importar las **bases de datos** con las que pretende trabajar y armar su *proyecto*. Los datos vienen desde distintos formatos y poseen varias clasificaciones, recordemos algunos conceptos claves para avanzar

- **Base de datos**: Es una colección especifica de datos.
- Que posee un **formato** ``popular'', es decir, es una tabla de forma de (matrices)
- También es de forma *rectangular*, cuya organización aborda un número de **filas** y **columnas**.
- Una **fila** tiene datos de una o varias *variables* para un mismo **individuo**.
- Una **columna** contiene valores de una *variable* para muchos individuos.

Por otro lado, podemos tener <span style="color:blue"> datos </span> de los siguientes tipos:

- <span style="color:red">Índices</span>: Es la parte de nombres, números de identificación o cuestionario en una base de datos.
- <span style="color:red">Binarios</span>: Variables que tienen sólo dos posibles respuestas. Ej: Si, no; Femenino, masculino, etc. Se codifican con (0 y 1), y se les conoce como variable *dummy*.
- <span style="color:red">De conteo</span>: Números enteros de no negación.
- <span style="color:red">Continuos</span>: Aquellos que admiten decimales.
- <span style="color:red">Nominales</span>: Respuestas no ordenadas y que amplían el espectro de las variables binarias, suelen ser datos categóricos. 
- <span style="color:red">Ordinales</span>: Admiten respuestas nominales pero en esencia *ordenadas* y son codificadas con números.


## Estructuras de datos usualmente utilizadas en econometría

En economía regularmente se trabaja con tres tipos de bases de datos conocidos como **Corte Transversal**, **Series de Tiempo** y **Paneles longitudinales**.

### Datos de corte transversal

Son aquellas *bases* que regularmente tienen información en un solo periodo de tiempo y que varían por individuos, instituciones, países o empresas. Se denotan sus observaciones con el subíndice (i), por ejemplo: $X_{i}$. Donde $X$ hace referencia a cada una de las variables como el nombre, la edad, los ingresos, etc. Y la parte de (i) de los _individuos_. Esto puede ser por ejemplo la variable $Edad_{i}$, donde (i) toma los nombres Matias, Kayson, Garrick, Cordell, etc. y será la edad correspondiente de cada uno de ellos. Mire que si lo escribimos en un vector con datos, esto es:

\begin{equation*}
Edad_{i}= \{ 27, 26, 22, 25, \dots, 33 \}
\end{equation*}

Una tabla mas general, con distintas variables por individuos es este:

```{=html}
<template id="ec52ff08-7b83-463f-b527-01b3d8bebc59"><style>
.tabwid table{
  border-collapse:collapse;
  line-height:1;
  margin-left:auto;
  margin-right:auto;
  border-width: 0;
  display: table;
  margin-top: 1.275em;
  margin-bottom: 1.275em;
  border-spacing: 0;
  border-color: transparent;
}
.tabwid_left table{
  margin-left:0;
}
.tabwid_right table{
  margin-right:0;
}
.tabwid td {
    padding: 0;
}
.tabwid a {
  text-decoration: none;
}
.tabwid thead {
    background-color: transparent;
}
.tabwid tfoot {
    background-color: transparent;
}
.tabwid table tr {
background-color: transparent;
}
</style><div class="tabwid"><style>.cl-5c2526d2{border-collapse:collapse;}.cl-5c19f7f8{font-family:'Arial';font-size:11pt;font-weight:bold;font-style:normal;text-decoration:none;color:rgba(236, 147, 70, 1.00);background-color:transparent;}.cl-5c19f7f9{font-family:'Arial';font-size:11pt;font-weight:normal;font-style:normal;text-decoration:none;color:rgba(164, 206, 229, 1.00);background-color:transparent;}.cl-5c1a4550{margin:0;text-align:left;border-bottom: 0 solid rgba(0, 0, 0, 1.00);border-top: 0 solid rgba(0, 0, 0, 1.00);border-left: 0 solid rgba(0, 0, 0, 1.00);border-right: 0 solid rgba(0, 0, 0, 1.00);padding-bottom:5pt;padding-top:5pt;padding-left:5pt;padding-right:5pt;line-height: 1;background-color:transparent;}.cl-5c1a4551{margin:0;text-align:right;border-bottom: 0 solid rgba(0, 0, 0, 1.00);border-top: 0 solid rgba(0, 0, 0, 1.00);border-left: 0 solid rgba(0, 0, 0, 1.00);border-right: 0 solid rgba(0, 0, 0, 1.00);padding-bottom:5pt;padding-top:5pt;padding-left:5pt;padding-right:5pt;line-height: 1;background-color:transparent;}.cl-5c1a94b0{width:47.4pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-5c1a94b1{width:146.5pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-5c1a94b2{width:91.4pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-5c1a94b3{width:75.6pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-5c1a94b4{width:83.5pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-5c1a94b5{width:52.3pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-5c1a94b6{width:46.8pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-5c1a94b7{width:52.3pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-5c1a94b8{width:83.5pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-5c1a94b9{width:146.5pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-5c1a94ba{width:47.4pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-5c1abba2{width:75.6pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-5c1abba3{width:46.8pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-5c1abba4{width:91.4pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-5c1abba5{width:83.5pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-5c1abba6{width:52.3pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-5c1abba7{width:75.6pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-5c1abba8{width:47.4pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-5c1abba9{width:91.4pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-5c1abbaa{width:46.8pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-5c1abbab{width:146.5pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-5c1abbac{width:83.5pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-5c1ae294{width:146.5pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-5c1ae295{width:75.6pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-5c1ae296{width:47.4pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-5c1ae297{width:91.4pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-5c1ae298{width:46.8pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-5c1ae299{width:52.3pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}</style><table class='cl-5c2526d2'>
```

```{=html}
<thead><tr style="overflow-wrap:break-word;"><td class="cl-5c1abbab"><p class="cl-5c1a4550"><span class="cl-5c19f7f8">Nombre</span></p></td><td class="cl-5c1abba7"><p class="cl-5c1a4551"><span class="cl-5c19f7f8">Grado</span></p></td><td class="cl-5c1abba8"><p class="cl-5c1a4551"><span class="cl-5c19f7f8">Edad</span></p></td><td class="cl-5c1abba5"><p class="cl-5c1a4551"><span class="cl-5c19f7f8">Ingresos</span></p></td><td class="cl-5c1abbaa"><p class="cl-5c1a4551"><span class="cl-5c19f7f8">Peso</span></p></td><td class="cl-5c1abba6"><p class="cl-5c1a4551"><span class="cl-5c19f7f8">Altura</span></p></td><td class="cl-5c1abba9"><p class="cl-5c1a4550"><span class="cl-5c19f7f8">Color_ojos</span></p></td></tr></thead><tbody><tr style="overflow-wrap:break-word;"><td class="cl-5c1a94b1"><p class="cl-5c1a4550"><span class="cl-5c19f7f9">Matias Barrows-Jast</span></p></td><td class="cl-5c1a94b3"><p class="cl-5c1a4551"><span class="cl-5c19f7f9">15/12/2022</span></p></td><td class="cl-5c1a94b0"><p class="cl-5c1a4551"><span class="cl-5c19f7f9"># 27</span></p></td><td class="cl-5c1a94b4"><p class="cl-5c1a4551"><span class="cl-5c19f7f9">$880 588</span></p></td><td class="cl-5c1a94b6"><p class="cl-5c1a4551"><span class="cl-5c19f7f9">56,7</span></p></td><td class="cl-5c1a94b5"><p class="cl-5c1a4551"><span class="cl-5c19f7f9">180,8</span></p></td><td class="cl-5c1a94b2"><p class="cl-5c1a4550"><span class="cl-5c19f7f9">color: Verdes</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-5c1a94b9"><p class="cl-5c1a4550"><span class="cl-5c19f7f9">Kayson Franecki</span></p></td><td class="cl-5c1abba2"><p class="cl-5c1a4551"><span class="cl-5c19f7f9">08/05/2000</span></p></td><td class="cl-5c1a94ba"><p class="cl-5c1a4551"><span class="cl-5c19f7f9"># 26</span></p></td><td class="cl-5c1a94b8"><p class="cl-5c1a4551"><span class="cl-5c19f7f9">No responde</span></p></td><td class="cl-5c1abba3"><p class="cl-5c1a4551"><span class="cl-5c19f7f9">64,6</span></p></td><td class="cl-5c1a94b7"><p class="cl-5c1a4551"><span class="cl-5c19f7f9">176,0</span></p></td><td class="cl-5c1abba4"><p class="cl-5c1a4550"><span class="cl-5c19f7f9">color: Oscuros</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-5c1abbab"><p class="cl-5c1a4550"><span class="cl-5c19f7f9">Garrick Langworth</span></p></td><td class="cl-5c1abba7"><p class="cl-5c1a4551"><span class="cl-5c19f7f9">05/03/2032</span></p></td><td class="cl-5c1abba8"><p class="cl-5c1a4551"><span class="cl-5c19f7f9"># 22</span></p></td><td class="cl-5c1abba5"><p class="cl-5c1a4551"><span class="cl-5c19f7f9">No responde</span></p></td><td class="cl-5c1abbaa"><p class="cl-5c1a4551"><span class="cl-5c19f7f9">90,1</span></p></td><td class="cl-5c1abba6"><p class="cl-5c1a4551"><span class="cl-5c19f7f9">164,4</span></p></td><td class="cl-5c1abba9"><p class="cl-5c1a4550"><span class="cl-5c19f7f9">color: Oscuros</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-5c1ae294"><p class="cl-5c1a4550"><span class="cl-5c19f7f9">Cordell Dickens</span></p></td><td class="cl-5c1ae295"><p class="cl-5c1a4551"><span class="cl-5c19f7f9">21/04/2040</span></p></td><td class="cl-5c1ae296"><p class="cl-5c1a4551"><span class="cl-5c19f7f9"># 25</span></p></td><td class="cl-5c1abbac"><p class="cl-5c1a4551"><span class="cl-5c19f7f9">No responde</span></p></td><td class="cl-5c1ae298"><p class="cl-5c1a4551"><span class="cl-5c19f7f9">75,1</span></p></td><td class="cl-5c1ae299"><p class="cl-5c1a4551"><span class="cl-5c19f7f9">168,0</span></p></td><td class="cl-5c1ae297"><p class="cl-5c1a4550"><span class="cl-5c19f7f9">color: Azules</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-5c1a94b9"><p class="cl-5c1a4550"><span class="cl-5c19f7f9">Destiney Dicki</span></p></td><td class="cl-5c1abba2"><p class="cl-5c1a4551"><span class="cl-5c19f7f9">07/06/2016</span></p></td><td class="cl-5c1a94ba"><p class="cl-5c1a4551"><span class="cl-5c19f7f9"># 28</span></p></td><td class="cl-5c1a94b8"><p class="cl-5c1a4551"><span class="cl-5c19f7f9">$415 902</span></p></td><td class="cl-5c1abba3"><p class="cl-5c1a4551"><span class="cl-5c19f7f9">97,3</span></p></td><td class="cl-5c1a94b7"><p class="cl-5c1a4551"><span class="cl-5c19f7f9">167,7</span></p></td><td class="cl-5c1abba4"><p class="cl-5c1a4550"><span class="cl-5c19f7f9">color: Oscuros</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-5c1a94b1"><p class="cl-5c1a4550"><span class="cl-5c19f7f9">Mrs. Freddie Pouros DDS</span></p></td><td class="cl-5c1a94b3"><p class="cl-5c1a4551"><span class="cl-5c19f7f9">29/09/2017</span></p></td><td class="cl-5c1a94b0"><p class="cl-5c1a4551"><span class="cl-5c19f7f9"># 32</span></p></td><td class="cl-5c1a94b4"><p class="cl-5c1a4551"><span class="cl-5c19f7f9">$784 231</span></p></td><td class="cl-5c1a94b6"><p class="cl-5c1a4551"><span class="cl-5c19f7f9">56,2</span></p></td><td class="cl-5c1a94b5"><p class="cl-5c1a4551"><span class="cl-5c19f7f9">173,9</span></p></td><td class="cl-5c1a94b2"><p class="cl-5c1a4550"><span class="cl-5c19f7f9">color: Azules</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-5c1a94b1"><p class="cl-5c1a4550"><span class="cl-5c19f7f9">Ms. Jada Lesch</span></p></td><td class="cl-5c1a94b3"><p class="cl-5c1a4551"><span class="cl-5c19f7f9">18/09/2028</span></p></td><td class="cl-5c1a94b0"><p class="cl-5c1a4551"><span class="cl-5c19f7f9"># 33</span></p></td><td class="cl-5c1a94b4"><p class="cl-5c1a4551"><span class="cl-5c19f7f9">$942 982</span></p></td><td class="cl-5c1a94b6"><p class="cl-5c1a4551"><span class="cl-5c19f7f9">76,1</span></p></td><td class="cl-5c1a94b5"><p class="cl-5c1a4551"><span class="cl-5c19f7f9">169,6</span></p></td><td class="cl-5c1a94b2"><p class="cl-5c1a4550"><span class="cl-5c19f7f9">color: Azules</span></p></td></tr></tbody></table></div></template>
<div class="flextable-shadow-host" id="c4a4aa33-253a-4a4f-88d1-20ed516d22ed"></div>
<script>
var dest = document.getElementById("c4a4aa33-253a-4a4f-88d1-20ed516d22ed");
var template = document.getElementById("ec52ff08-7b83-463f-b527-01b3d8bebc59");
var caption = template.content.querySelector("caption");
if(caption) {
  caption.style.cssText = "display:block;text-align:center;";
  var newcapt = document.createElement("p");
  newcapt.appendChild(caption)
  dest.parentNode.insertBefore(newcapt, dest.previousSibling);
}
var fantome = dest.attachShadow({mode: 'open'});
var templateContent = template.content;
fantome.appendChild(templateContent);
</script>

```

### Datos de series de tiempo
Por otro lado, existen bases que tienen en común un individuo (i), pero que varian en el tiempo. Los datos de este tipo suelen ser denominados **macroeconómicos** o series "Macro", un ejemplo de esto es el PIB de un país cualquiera desde el año de 2015 al 2021. Las series se denotan con el subíndice (t) que hace referencia al periodo de estudio, es decir, $X_{t}$.

```{=html}
<template id="afb4c03a-6458-44d0-9d45-c2ad938035a6"><style>
.tabwid table{
  border-collapse:collapse;
  line-height:1;
  margin-left:auto;
  margin-right:auto;
  border-width: 0;
  display: table;
  margin-top: 1.275em;
  margin-bottom: 1.275em;
  border-spacing: 0;
  border-color: transparent;
}
.tabwid_left table{
  margin-left:0;
}
.tabwid_right table{
  margin-right:0;
}
.tabwid td {
    padding: 0;
}
.tabwid a {
  text-decoration: none;
}
.tabwid thead {
    background-color: transparent;
}
.tabwid tfoot {
    background-color: transparent;
}
.tabwid table tr {
background-color: transparent;
}
</style><div class="tabwid"><style>.cl-5c46256c{border-collapse:collapse;}.cl-5c3fd928{font-family:'Arial';font-size:11pt;font-weight:bold;font-style:normal;text-decoration:none;color:rgba(236, 147, 70, 1.00);background-color:transparent;}.cl-5c3fd929{font-family:'Arial';font-size:11pt;font-weight:normal;font-style:normal;text-decoration:none;color:rgba(164, 206, 229, 1.00);background-color:transparent;}.cl-5c400060{margin:0;text-align:left;border-bottom: 0 solid rgba(0, 0, 0, 1.00);border-top: 0 solid rgba(0, 0, 0, 1.00);border-left: 0 solid rgba(0, 0, 0, 1.00);border-right: 0 solid rgba(0, 0, 0, 1.00);padding-bottom:5pt;padding-top:5pt;padding-left:5pt;padding-right:5pt;line-height: 1;background-color:transparent;}.cl-5c400061{margin:0;text-align:right;border-bottom: 0 solid rgba(0, 0, 0, 1.00);border-top: 0 solid rgba(0, 0, 0, 1.00);border-left: 0 solid rgba(0, 0, 0, 1.00);border-right: 0 solid rgba(0, 0, 0, 1.00);padding-bottom:5pt;padding-top:5pt;padding-left:5pt;padding-right:5pt;line-height: 1;background-color:transparent;}.cl-5c402716{width:48.1pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-5c402717{width:101.3pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-5c402718{width:45pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-5c402719{width:101.3pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-5c40271a{width:48.1pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-5c40271b{width:45pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}</style><table class='cl-5c46256c'>
```

```{=html}
<thead><tr style="overflow-wrap:break-word;"><td class="cl-5c40271b"><p class="cl-5c400060"><span class="cl-5c3fd928">t</span></p></td><td class="cl-5c402719"><p class="cl-5c400061"><span class="cl-5c3fd928">PIB</span></p></td><td class="cl-5c40271a"><p class="cl-5c400061"><span class="cl-5c3fd928">IPC</span></p></td></tr></thead><tbody><tr style="overflow-wrap:break-word;"><td class="cl-5c402718"><p class="cl-5c400060"><span class="cl-5c3fd929">2015</span></p></td><td class="cl-5c402717"><p class="cl-5c400061"><span class="cl-5c3fd929">110.77 Mill. de $</span></p></td><td class="cl-5c402716"><p class="cl-5c400061"><span class="cl-5c3fd929">77,3</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-5c402718"><p class="cl-5c400060"><span class="cl-5c3fd929">2016</span></p></td><td class="cl-5c402717"><p class="cl-5c400061"><span class="cl-5c3fd929">133.89 Mill. de $</span></p></td><td class="cl-5c402716"><p class="cl-5c400061"><span class="cl-5c3fd929">83,1</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-5c402718"><p class="cl-5c400060"><span class="cl-5c3fd929">2017</span></p></td><td class="cl-5c402717"><p class="cl-5c400061"><span class="cl-5c3fd929">259.11 Mill. de $</span></p></td><td class="cl-5c402716"><p class="cl-5c400061"><span class="cl-5c3fd929">85,5</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-5c402718"><p class="cl-5c400060"><span class="cl-5c3fd929">2018</span></p></td><td class="cl-5c402717"><p class="cl-5c400061"><span class="cl-5c3fd929">154.94 Mill. de $</span></p></td><td class="cl-5c402716"><p class="cl-5c400061"><span class="cl-5c3fd929">102,2</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-5c402718"><p class="cl-5c400060"><span class="cl-5c3fd929">2019</span></p></td><td class="cl-5c402717"><p class="cl-5c400061"><span class="cl-5c3fd929">159.05 Mill. de $</span></p></td><td class="cl-5c402716"><p class="cl-5c400061"><span class="cl-5c3fd929">93,6</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-5c402718"><p class="cl-5c400060"><span class="cl-5c3fd929">2020</span></p></td><td class="cl-5c402717"><p class="cl-5c400061"><span class="cl-5c3fd929">270.05 Mill. de $</span></p></td><td class="cl-5c402716"><p class="cl-5c400061"><span class="cl-5c3fd929">94,0</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-5c402718"><p class="cl-5c400060"><span class="cl-5c3fd929">2021</span></p></td><td class="cl-5c402717"><p class="cl-5c400061"><span class="cl-5c3fd929">182.26 Mill. de $</span></p></td><td class="cl-5c402716"><p class="cl-5c400061"><span class="cl-5c3fd929">91,1</span></p></td></tr></tbody></table></div></template>
<div class="flextable-shadow-host" id="8ee8c542-db9b-4b35-876b-bb03de0a4f70"></div>
<script>
var dest = document.getElementById("8ee8c542-db9b-4b35-876b-bb03de0a4f70");
var template = document.getElementById("afb4c03a-6458-44d0-9d45-c2ad938035a6");
var caption = template.content.querySelector("caption");
if(caption) {
  caption.style.cssText = "display:block;text-align:center;";
  var newcapt = document.createElement("p");
  newcapt.appendChild(caption)
  dest.parentNode.insertBefore(newcapt, dest.previousSibling);
}
var fantome = dest.attachShadow({mode: 'open'});
var templateContent = template.content;
fantome.appendChild(templateContent);
</script>

```


### Panel Longitudinal

Los datos que provienen de un **Panel** son realizados por instituciones o empresas privadas que le hacen *seguimiento* a un individuo (i) en varios periodos de tiempo. Este tipo de datos se denota como $X_{it}$. Note que ahora hay dos subíndices, ya que se mide por tiempo e individuo.

```{=html}
<template id="efa9d221-d82a-4987-a3f5-e5dd775e0c8a"><style>
.tabwid table{
  border-collapse:collapse;
  line-height:1;
  margin-left:auto;
  margin-right:auto;
  border-width: 0;
  display: table;
  margin-top: 1.275em;
  margin-bottom: 1.275em;
  border-spacing: 0;
  border-color: transparent;
}
.tabwid_left table{
  margin-left:0;
}
.tabwid_right table{
  margin-right:0;
}
.tabwid td {
    padding: 0;
}
.tabwid a {
  text-decoration: none;
}
.tabwid thead {
    background-color: transparent;
}
.tabwid tfoot {
    background-color: transparent;
}
.tabwid table tr {
background-color: transparent;
}
</style><div class="tabwid"><style>.cl-5c6d9db8{border-collapse:collapse;}.cl-5c63e926{font-family:'Arial';font-size:11pt;font-weight:bold;font-style:normal;text-decoration:none;color:rgba(236, 147, 70, 1.00);background-color:transparent;}.cl-5c63e927{font-family:'Arial';font-size:11pt;font-weight:normal;font-style:normal;text-decoration:none;color:rgba(164, 206, 229, 1.00);background-color:transparent;}.cl-5c641018{margin:0;text-align:left;border-bottom: 0 solid rgba(0, 0, 0, 1.00);border-top: 0 solid rgba(0, 0, 0, 1.00);border-left: 0 solid rgba(0, 0, 0, 1.00);border-right: 0 solid rgba(0, 0, 0, 1.00);padding-bottom:5pt;padding-top:5pt;padding-left:5pt;padding-right:5pt;line-height: 1;background-color:transparent;}.cl-5c641019{margin:0;text-align:right;border-bottom: 0 solid rgba(0, 0, 0, 1.00);border-top: 0 solid rgba(0, 0, 0, 1.00);border-left: 0 solid rgba(0, 0, 0, 1.00);border-right: 0 solid rgba(0, 0, 0, 1.00);padding-bottom:5pt;padding-top:5pt;padding-left:5pt;padding-right:5pt;line-height: 1;background-color:transparent;}.cl-5c643714{width:48.1pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-5c643715{width:67pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-5c643716{width:101.3pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-5c643717{width:45pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-5c643718{width:48.1pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-5c643719{width:67pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-5c64371a{width:101.3pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-5c64371b{width:45pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}</style><table class='cl-5c6d9db8'>
```

```{=html}
<thead><tr style="overflow-wrap:break-word;"><td class="cl-5c64371b"><p class="cl-5c641018"><span class="cl-5c63e926">t</span></p></td><td class="cl-5c643719"><p class="cl-5c641018"><span class="cl-5c63e926">Paises</span></p></td><td class="cl-5c64371a"><p class="cl-5c641019"><span class="cl-5c63e926">PIB</span></p></td><td class="cl-5c643718"><p class="cl-5c641019"><span class="cl-5c63e926">IPC</span></p></td></tr></thead><tbody><tr style="overflow-wrap:break-word;"><td class="cl-5c643717"><p class="cl-5c641018"><span class="cl-5c63e927">2014</span></p></td><td class="cl-5c643715"><p class="cl-5c641018"><span class="cl-5c63e927">Colombia</span></p></td><td class="cl-5c643716"><p class="cl-5c641019"><span class="cl-5c63e927">234.31 Mill. de $</span></p></td><td class="cl-5c643714"><p class="cl-5c641019"><span class="cl-5c63e927">108,0</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-5c643717"><p class="cl-5c641018"><span class="cl-5c63e927">2015</span></p></td><td class="cl-5c643715"><p class="cl-5c641018"><span class="cl-5c63e927">Colombia</span></p></td><td class="cl-5c643716"><p class="cl-5c641019"><span class="cl-5c63e927">116.51 Mill. de $</span></p></td><td class="cl-5c643714"><p class="cl-5c641019"><span class="cl-5c63e927">103,9</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-5c643717"><p class="cl-5c641018"><span class="cl-5c63e927">2014</span></p></td><td class="cl-5c643715"><p class="cl-5c641018"><span class="cl-5c63e927">Perú</span></p></td><td class="cl-5c643716"><p class="cl-5c641019"><span class="cl-5c63e927">287.73 Mill. de $</span></p></td><td class="cl-5c643714"><p class="cl-5c641019"><span class="cl-5c63e927">108,1</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-5c643717"><p class="cl-5c641018"><span class="cl-5c63e927">2015</span></p></td><td class="cl-5c643715"><p class="cl-5c641018"><span class="cl-5c63e927">Perú</span></p></td><td class="cl-5c643716"><p class="cl-5c641019"><span class="cl-5c63e927">113.82 Mill. de $</span></p></td><td class="cl-5c643714"><p class="cl-5c641019"><span class="cl-5c63e927">91,0</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-5c643717"><p class="cl-5c641018"><span class="cl-5c63e927">2014</span></p></td><td class="cl-5c643715"><p class="cl-5c641018"><span class="cl-5c63e927">Brasil</span></p></td><td class="cl-5c643716"><p class="cl-5c641019"><span class="cl-5c63e927">177.37 Mill. de $</span></p></td><td class="cl-5c643714"><p class="cl-5c641019"><span class="cl-5c63e927">93,3</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-5c643717"><p class="cl-5c641018"><span class="cl-5c63e927">2015</span></p></td><td class="cl-5c643715"><p class="cl-5c641018"><span class="cl-5c63e927">Brasil</span></p></td><td class="cl-5c643716"><p class="cl-5c641019"><span class="cl-5c63e927">110.42 Mill. de $</span></p></td><td class="cl-5c643714"><p class="cl-5c641019"><span class="cl-5c63e927">99,3</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-5c643717"><p class="cl-5c641018"><span class="cl-5c63e927">2014</span></p></td><td class="cl-5c643715"><p class="cl-5c641018"><span class="cl-5c63e927">Chile</span></p></td><td class="cl-5c643716"><p class="cl-5c641019"><span class="cl-5c63e927">136.66 Mill. de $</span></p></td><td class="cl-5c643714"><p class="cl-5c641019"><span class="cl-5c63e927">67,9</span></p></td></tr></tbody></table></div></template>
<div class="flextable-shadow-host" id="3c1b1768-5eb9-4087-9a57-8ecd8e271f90"></div>
<script>
var dest = document.getElementById("3c1b1768-5eb9-4087-9a57-8ecd8e271f90");
var template = document.getElementById("efa9d221-d82a-4987-a3f5-e5dd775e0c8a");
var caption = template.content.querySelector("caption");
if(caption) {
  caption.style.cssText = "display:block;text-align:center;";
  var newcapt = document.createElement("p");
  newcapt.appendChild(caption)
  dest.parentNode.insertBefore(newcapt, dest.previousSibling);
}
var fantome = dest.attachShadow({mode: 'open'});
var templateContent = template.content;
fantome.appendChild(templateContent);
</script>

```

## Importación de datos

Una de las cosas mas requeridas dentro del trabajo de **R** hace referencia a la importación de datos que no son propiamente de el. Aquellos datos o bases regularmente vienen en formatos de xml, csv, dta, asll, etc. Por ende, se hace necesario la implementación de comandos o de la ayuda directa del programa. Los paquetes declarados a continuación permiten realizar esto.


```r
library(foreign)    # Para convertir datos *.dta
library(haven)      # Para importar datos de otros programas
library(readxl)     # Para leer archivos de excel

#Ejemplos utilizabdo readxl:
library("readxl")
datos <- read_csv("miarchivo.csv") # Un primer ejemplo
datos <- read_excel("miarchivo.xlsx") # Un segundo ejemplo


#Ejemplo de una base de datos que esta en excel (debe tener cuidado con la ruta C:)
Pruebadatos <- read_excel("C:/Users/keyne/OneDrive/Escritorio/Pruebadatos.xlsx")
View(Pruebadatos)

#Exportar una base de datos desde R a formato CSV de excel con el comando "write"
write.csv(Pruebadatos, file = "archivodeprueba.csv")
```
Es de recordar que al exportar datos, estos quedan grabados en la carpeta de trabajo que se le ha establecido al programa desde un inicio. A continuación tres pasos para conocer donde se arrojan los archivos exportados y guardados en la ruta. 

<img src="imagenes/C3.png" width="75%" style="display: block; margin: auto;" />

Si tiene en cuenta lo anterior, lo primero es irse a la pestaña de `files`, luego le da `click` a la (tuerca) `more` y decirle ir al directorio de trabajo o `Go To Working Directory`. Si no desea esa carpeta, puede crear una en su computador con **new folder** y de ahí marcar la opción de `Set As Working Directory`. De esta manera podrá guardar todos sus archivos en esa ubicación.

## Datos propios en R

Algunas veces, se pueden vincular los datos propiamente al programa sin necesidad de importarlos. Se puede construir por *vectores*, estos a su vez se convierten o consideran como una lista de elementos que finalmente constituyen una columna de una base de datos o **dataframe**. Para mirar un caso de esto, mire el código a continuación:


```r
# Definimos un vector x para todos los años:
anos<- c(2018,2019,2020,2021,2022,2023)
# Definimos una matriz de y valores:
producto1<-c(10,13,16,19,17,18); producto2<-c(21,32,43,15,19,36); producto3<-c(22,43,42,21,32,21)
# Una forma de unir vectores es con el comando cbind
ventas_mat <- cbind(producto1,producto2,producto3) 
# Nombramos las filas con el vector de años:
rownames(ventas_mat) <- anos 
# La matriz de datos es:
ventas_mat
```

```
##      producto1 producto2 producto3
## 2018        10        21        22
## 2019        13        32        43
## 2020        16        43        42
## 2021        19        15        21
## 2022        17        19        32
## 2023        18        36        21
```

```r
# POr último le decimos que lo tome como data frame
ventas <- as.data.frame(ventas_mat)
```

La parte consecuente a **cbind** es para unir cada una de las columnas que se han venido creando. **R** trabaja con matrices, luego cada columna viene a ser un vector _columna_. Si la forma de unir fuera por filas, la opción a utilizar sería **rbind**.

### Trabajando con Data Frames

Para esta parte, es importante mirar todos los elementos de trabajo con las bases y estructuras de datos. En este, realizaremos algunas de las operaciones con ellas. Una forma de *seleccionar* variables es con la indicación del signo $ (pesos), se hace para seleccionar una variable de la tabla de datos. 


```r
# Acceder a una sola variable:
ventas$producto2
```

```
## [1] 21 32 43 15 19 36
```
El resultado le mostrará solo los valores contenidos en esa variable denominada **producto2**. Podrá incluso trabajar con ella por si sola e incluso empezar a realizar _subconjuntos_ de datos solo con un grupo de ellas, como ocurre a continuación de tres formas distintas para conseguir un mismo objetivo.


```r
# Generar una nueva variable en el data frame
ventas$totalv1 <- ventas$producto1 + ventas$producto2 + ventas$producto3 

# Lo mismo de lo anterior pero usando "with":
ventas$totalv2 <- with(ventas, producto1+producto2+producto3)

# Lo mismo pero usando el comando "attach":
attach(ventas)
```

```
## The following objects are masked _by_ .GlobalEnv:
## 
##     producto1, producto2, producto3
```
Este último (attach), sirve para simplificar aun mas el codigo y ahorrar el uso del signo ($) dentro del código, ademas de brindarle un mensaje tipo "ambiente" que se ha realizado en el programa.

```r
ventas$totalv3 <- producto1+producto2+producto3
detach(ventas)
ventas
```

```
##      producto1 producto2 producto3 totalv1 totalv2 totalv3
## 2018        10        21        22      53      53      53
## 2019        13        32        43      88      88      88
## 2020        16        43        42     101     101     101
## 2021        19        15        21      55      55      55
## 2022        17        19        32      68      68      68
## 2023        18        36        21      75      75      75
```
Note que es importante nuevamente decirle a **R** que debe quitar la opción con el comando (detach), esto libera su uso y puede ser utilizado con otras bases de datos.



