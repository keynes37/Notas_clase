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
<template id="849c7c64-f295-4093-91c2-bef912e71bbc"><style>
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
</style><div class="tabwid"><style>.cl-8ccc6e4e{border-collapse:collapse;}.cl-8cbe57c8{font-family:'Arial';font-size:11pt;font-weight:bold;font-style:normal;text-decoration:none;color:rgba(236, 147, 70, 1.00);background-color:transparent;}.cl-8cbe57c9{font-family:'Arial';font-size:11pt;font-weight:normal;font-style:normal;text-decoration:none;color:rgba(164, 206, 229, 1.00);background-color:transparent;}.cl-8cbe7ece{margin:0;text-align:left;border-bottom: 0 solid rgba(0, 0, 0, 1.00);border-top: 0 solid rgba(0, 0, 0, 1.00);border-left: 0 solid rgba(0, 0, 0, 1.00);border-right: 0 solid rgba(0, 0, 0, 1.00);padding-bottom:5pt;padding-top:5pt;padding-left:5pt;padding-right:5pt;line-height: 1;background-color:transparent;}.cl-8cbe7ecf{margin:0;text-align:right;border-bottom: 0 solid rgba(0, 0, 0, 1.00);border-top: 0 solid rgba(0, 0, 0, 1.00);border-left: 0 solid rgba(0, 0, 0, 1.00);border-right: 0 solid rgba(0, 0, 0, 1.00);padding-bottom:5pt;padding-top:5pt;padding-left:5pt;padding-right:5pt;line-height: 1;background-color:transparent;}.cl-8cbeccb2{width:47.4pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-8cbeccb3{width:146.5pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-8cbeccb4{width:91.4pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-8cbeccb5{width:75.6pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-8cbeccb6{width:83.5pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-8cbeccb7{width:52.3pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-8cbeccb8{width:46.8pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-8cbeccb9{width:52.3pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-8cbeccba{width:83.5pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-8cbeccbb{width:146.5pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-8cbeccbc{width:47.4pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-8cbef3a4{width:75.6pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-8cbef3a5{width:46.8pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-8cbef3a6{width:91.4pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-8cbef3a7{width:83.5pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-8cbef3a8{width:52.3pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-8cbef3a9{width:75.6pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-8cbef3aa{width:47.4pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-8cbef3ab{width:91.4pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-8cbef3ac{width:46.8pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-8cbef3ad{width:146.5pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-8cbef3ae{width:83.5pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-8cbf1a96{width:146.5pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-8cbf1a97{width:75.6pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-8cbf1a98{width:47.4pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-8cbf1a99{width:91.4pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-8cbf1a9a{width:46.8pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-8cbf1a9b{width:52.3pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}</style><table class='cl-8ccc6e4e'>
```

```{=html}
<thead><tr style="overflow-wrap:break-word;"><td class="cl-8cbef3ad"><p class="cl-8cbe7ece"><span class="cl-8cbe57c8">Nombre</span></p></td><td class="cl-8cbef3a9"><p class="cl-8cbe7ecf"><span class="cl-8cbe57c8">Grado</span></p></td><td class="cl-8cbef3aa"><p class="cl-8cbe7ecf"><span class="cl-8cbe57c8">Edad</span></p></td><td class="cl-8cbef3a7"><p class="cl-8cbe7ecf"><span class="cl-8cbe57c8">Ingresos</span></p></td><td class="cl-8cbef3ac"><p class="cl-8cbe7ecf"><span class="cl-8cbe57c8">Peso</span></p></td><td class="cl-8cbef3a8"><p class="cl-8cbe7ecf"><span class="cl-8cbe57c8">Altura</span></p></td><td class="cl-8cbef3ab"><p class="cl-8cbe7ece"><span class="cl-8cbe57c8">Color_ojos</span></p></td></tr></thead><tbody><tr style="overflow-wrap:break-word;"><td class="cl-8cbeccb3"><p class="cl-8cbe7ece"><span class="cl-8cbe57c9">Matias Barrows-Jast</span></p></td><td class="cl-8cbeccb5"><p class="cl-8cbe7ecf"><span class="cl-8cbe57c9">15/12/2022</span></p></td><td class="cl-8cbeccb2"><p class="cl-8cbe7ecf"><span class="cl-8cbe57c9"># 27</span></p></td><td class="cl-8cbeccb6"><p class="cl-8cbe7ecf"><span class="cl-8cbe57c9">$880 588</span></p></td><td class="cl-8cbeccb8"><p class="cl-8cbe7ecf"><span class="cl-8cbe57c9">56,7</span></p></td><td class="cl-8cbeccb7"><p class="cl-8cbe7ecf"><span class="cl-8cbe57c9">180,8</span></p></td><td class="cl-8cbeccb4"><p class="cl-8cbe7ece"><span class="cl-8cbe57c9">color: Verdes</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-8cbeccbb"><p class="cl-8cbe7ece"><span class="cl-8cbe57c9">Kayson Franecki</span></p></td><td class="cl-8cbef3a4"><p class="cl-8cbe7ecf"><span class="cl-8cbe57c9">08/05/2000</span></p></td><td class="cl-8cbeccbc"><p class="cl-8cbe7ecf"><span class="cl-8cbe57c9"># 26</span></p></td><td class="cl-8cbeccba"><p class="cl-8cbe7ecf"><span class="cl-8cbe57c9">No responde</span></p></td><td class="cl-8cbef3a5"><p class="cl-8cbe7ecf"><span class="cl-8cbe57c9">64,6</span></p></td><td class="cl-8cbeccb9"><p class="cl-8cbe7ecf"><span class="cl-8cbe57c9">176,0</span></p></td><td class="cl-8cbef3a6"><p class="cl-8cbe7ece"><span class="cl-8cbe57c9">color: Oscuros</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-8cbef3ad"><p class="cl-8cbe7ece"><span class="cl-8cbe57c9">Garrick Langworth</span></p></td><td class="cl-8cbef3a9"><p class="cl-8cbe7ecf"><span class="cl-8cbe57c9">05/03/2032</span></p></td><td class="cl-8cbef3aa"><p class="cl-8cbe7ecf"><span class="cl-8cbe57c9"># 22</span></p></td><td class="cl-8cbef3a7"><p class="cl-8cbe7ecf"><span class="cl-8cbe57c9">No responde</span></p></td><td class="cl-8cbef3ac"><p class="cl-8cbe7ecf"><span class="cl-8cbe57c9">90,1</span></p></td><td class="cl-8cbef3a8"><p class="cl-8cbe7ecf"><span class="cl-8cbe57c9">164,4</span></p></td><td class="cl-8cbef3ab"><p class="cl-8cbe7ece"><span class="cl-8cbe57c9">color: Oscuros</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-8cbf1a96"><p class="cl-8cbe7ece"><span class="cl-8cbe57c9">Cordell Dickens</span></p></td><td class="cl-8cbf1a97"><p class="cl-8cbe7ecf"><span class="cl-8cbe57c9">21/04/2040</span></p></td><td class="cl-8cbf1a98"><p class="cl-8cbe7ecf"><span class="cl-8cbe57c9"># 25</span></p></td><td class="cl-8cbef3ae"><p class="cl-8cbe7ecf"><span class="cl-8cbe57c9">No responde</span></p></td><td class="cl-8cbf1a9a"><p class="cl-8cbe7ecf"><span class="cl-8cbe57c9">75,1</span></p></td><td class="cl-8cbf1a9b"><p class="cl-8cbe7ecf"><span class="cl-8cbe57c9">168,0</span></p></td><td class="cl-8cbf1a99"><p class="cl-8cbe7ece"><span class="cl-8cbe57c9">color: Azules</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-8cbeccbb"><p class="cl-8cbe7ece"><span class="cl-8cbe57c9">Destiney Dicki</span></p></td><td class="cl-8cbef3a4"><p class="cl-8cbe7ecf"><span class="cl-8cbe57c9">07/06/2016</span></p></td><td class="cl-8cbeccbc"><p class="cl-8cbe7ecf"><span class="cl-8cbe57c9"># 28</span></p></td><td class="cl-8cbeccba"><p class="cl-8cbe7ecf"><span class="cl-8cbe57c9">$415 902</span></p></td><td class="cl-8cbef3a5"><p class="cl-8cbe7ecf"><span class="cl-8cbe57c9">97,3</span></p></td><td class="cl-8cbeccb9"><p class="cl-8cbe7ecf"><span class="cl-8cbe57c9">167,7</span></p></td><td class="cl-8cbef3a6"><p class="cl-8cbe7ece"><span class="cl-8cbe57c9">color: Oscuros</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-8cbeccb3"><p class="cl-8cbe7ece"><span class="cl-8cbe57c9">Mrs. Freddie Pouros DDS</span></p></td><td class="cl-8cbeccb5"><p class="cl-8cbe7ecf"><span class="cl-8cbe57c9">29/09/2017</span></p></td><td class="cl-8cbeccb2"><p class="cl-8cbe7ecf"><span class="cl-8cbe57c9"># 32</span></p></td><td class="cl-8cbeccb6"><p class="cl-8cbe7ecf"><span class="cl-8cbe57c9">$784 231</span></p></td><td class="cl-8cbeccb8"><p class="cl-8cbe7ecf"><span class="cl-8cbe57c9">56,2</span></p></td><td class="cl-8cbeccb7"><p class="cl-8cbe7ecf"><span class="cl-8cbe57c9">173,9</span></p></td><td class="cl-8cbeccb4"><p class="cl-8cbe7ece"><span class="cl-8cbe57c9">color: Azules</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-8cbeccb3"><p class="cl-8cbe7ece"><span class="cl-8cbe57c9">Ms. Jada Lesch</span></p></td><td class="cl-8cbeccb5"><p class="cl-8cbe7ecf"><span class="cl-8cbe57c9">18/09/2028</span></p></td><td class="cl-8cbeccb2"><p class="cl-8cbe7ecf"><span class="cl-8cbe57c9"># 33</span></p></td><td class="cl-8cbeccb6"><p class="cl-8cbe7ecf"><span class="cl-8cbe57c9">$942 982</span></p></td><td class="cl-8cbeccb8"><p class="cl-8cbe7ecf"><span class="cl-8cbe57c9">76,1</span></p></td><td class="cl-8cbeccb7"><p class="cl-8cbe7ecf"><span class="cl-8cbe57c9">169,6</span></p></td><td class="cl-8cbeccb4"><p class="cl-8cbe7ece"><span class="cl-8cbe57c9">color: Azules</span></p></td></tr></tbody></table></div></template>
<div class="flextable-shadow-host" id="cbd2cd73-fd23-4fdb-9b18-bdb909acf17d"></div>
<script>
var dest = document.getElementById("cbd2cd73-fd23-4fdb-9b18-bdb909acf17d");
var template = document.getElementById("849c7c64-f295-4093-91c2-bef912e71bbc");
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
<template id="be150ee8-40f1-4465-bfc5-581476f555ef"><style>
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
</style><div class="tabwid"><style>.cl-8cf0f2be{border-collapse:collapse;}.cl-8ce92fd4{font-family:'Arial';font-size:11pt;font-weight:bold;font-style:normal;text-decoration:none;color:rgba(236, 147, 70, 1.00);background-color:transparent;}.cl-8ce92fd5{font-family:'Arial';font-size:11pt;font-weight:normal;font-style:normal;text-decoration:none;color:rgba(164, 206, 229, 1.00);background-color:transparent;}.cl-8ce92fd6{margin:0;text-align:left;border-bottom: 0 solid rgba(0, 0, 0, 1.00);border-top: 0 solid rgba(0, 0, 0, 1.00);border-left: 0 solid rgba(0, 0, 0, 1.00);border-right: 0 solid rgba(0, 0, 0, 1.00);padding-bottom:5pt;padding-top:5pt;padding-left:5pt;padding-right:5pt;line-height: 1;background-color:transparent;}.cl-8ce92fd7{margin:0;text-align:right;border-bottom: 0 solid rgba(0, 0, 0, 1.00);border-top: 0 solid rgba(0, 0, 0, 1.00);border-left: 0 solid rgba(0, 0, 0, 1.00);border-right: 0 solid rgba(0, 0, 0, 1.00);padding-bottom:5pt;padding-top:5pt;padding-left:5pt;padding-right:5pt;line-height: 1;background-color:transparent;}.cl-8ce97db8{width:48.1pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-8ce97db9{width:101.3pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-8ce97dba{width:45pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-8ce97dbb{width:101.3pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-8ce97dbc{width:48.1pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-8ce97dbd{width:45pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}</style><table class='cl-8cf0f2be'>
```

```{=html}
<thead><tr style="overflow-wrap:break-word;"><td class="cl-8ce97dbd"><p class="cl-8ce92fd6"><span class="cl-8ce92fd4">t</span></p></td><td class="cl-8ce97dbb"><p class="cl-8ce92fd7"><span class="cl-8ce92fd4">PIB</span></p></td><td class="cl-8ce97dbc"><p class="cl-8ce92fd7"><span class="cl-8ce92fd4">IPC</span></p></td></tr></thead><tbody><tr style="overflow-wrap:break-word;"><td class="cl-8ce97dba"><p class="cl-8ce92fd6"><span class="cl-8ce92fd5">2015</span></p></td><td class="cl-8ce97db9"><p class="cl-8ce92fd7"><span class="cl-8ce92fd5">110.77 Mill. de $</span></p></td><td class="cl-8ce97db8"><p class="cl-8ce92fd7"><span class="cl-8ce92fd5">77,3</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-8ce97dba"><p class="cl-8ce92fd6"><span class="cl-8ce92fd5">2016</span></p></td><td class="cl-8ce97db9"><p class="cl-8ce92fd7"><span class="cl-8ce92fd5">133.89 Mill. de $</span></p></td><td class="cl-8ce97db8"><p class="cl-8ce92fd7"><span class="cl-8ce92fd5">83,1</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-8ce97dba"><p class="cl-8ce92fd6"><span class="cl-8ce92fd5">2017</span></p></td><td class="cl-8ce97db9"><p class="cl-8ce92fd7"><span class="cl-8ce92fd5">259.11 Mill. de $</span></p></td><td class="cl-8ce97db8"><p class="cl-8ce92fd7"><span class="cl-8ce92fd5">85,5</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-8ce97dba"><p class="cl-8ce92fd6"><span class="cl-8ce92fd5">2018</span></p></td><td class="cl-8ce97db9"><p class="cl-8ce92fd7"><span class="cl-8ce92fd5">154.94 Mill. de $</span></p></td><td class="cl-8ce97db8"><p class="cl-8ce92fd7"><span class="cl-8ce92fd5">102,2</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-8ce97dba"><p class="cl-8ce92fd6"><span class="cl-8ce92fd5">2019</span></p></td><td class="cl-8ce97db9"><p class="cl-8ce92fd7"><span class="cl-8ce92fd5">159.05 Mill. de $</span></p></td><td class="cl-8ce97db8"><p class="cl-8ce92fd7"><span class="cl-8ce92fd5">93,6</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-8ce97dba"><p class="cl-8ce92fd6"><span class="cl-8ce92fd5">2020</span></p></td><td class="cl-8ce97db9"><p class="cl-8ce92fd7"><span class="cl-8ce92fd5">270.05 Mill. de $</span></p></td><td class="cl-8ce97db8"><p class="cl-8ce92fd7"><span class="cl-8ce92fd5">94,0</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-8ce97dba"><p class="cl-8ce92fd6"><span class="cl-8ce92fd5">2021</span></p></td><td class="cl-8ce97db9"><p class="cl-8ce92fd7"><span class="cl-8ce92fd5">182.26 Mill. de $</span></p></td><td class="cl-8ce97db8"><p class="cl-8ce92fd7"><span class="cl-8ce92fd5">91,1</span></p></td></tr></tbody></table></div></template>
<div class="flextable-shadow-host" id="093cf637-2f64-414d-8b62-02cce484dc32"></div>
<script>
var dest = document.getElementById("093cf637-2f64-414d-8b62-02cce484dc32");
var template = document.getElementById("be150ee8-40f1-4465-bfc5-581476f555ef");
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
<template id="fe78e46a-1664-4fae-8157-0c20a6c9aab4"><style>
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
</style><div class="tabwid"><style>.cl-8d15017c{border-collapse:collapse;}.cl-8d0d1958{font-family:'Arial';font-size:11pt;font-weight:bold;font-style:normal;text-decoration:none;color:rgba(236, 147, 70, 1.00);background-color:transparent;}.cl-8d0d1959{font-family:'Arial';font-size:11pt;font-weight:normal;font-style:normal;text-decoration:none;color:rgba(164, 206, 229, 1.00);background-color:transparent;}.cl-8d0d195a{margin:0;text-align:left;border-bottom: 0 solid rgba(0, 0, 0, 1.00);border-top: 0 solid rgba(0, 0, 0, 1.00);border-left: 0 solid rgba(0, 0, 0, 1.00);border-right: 0 solid rgba(0, 0, 0, 1.00);padding-bottom:5pt;padding-top:5pt;padding-left:5pt;padding-right:5pt;line-height: 1;background-color:transparent;}.cl-8d0d195b{margin:0;text-align:right;border-bottom: 0 solid rgba(0, 0, 0, 1.00);border-top: 0 solid rgba(0, 0, 0, 1.00);border-left: 0 solid rgba(0, 0, 0, 1.00);border-right: 0 solid rgba(0, 0, 0, 1.00);padding-bottom:5pt;padding-top:5pt;padding-left:5pt;padding-right:5pt;line-height: 1;background-color:transparent;}.cl-8d0d3ea6{width:48.1pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-8d0d3ea7{width:67pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-8d0d3ea8{width:101.3pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-8d0d3ea9{width:45pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-8d0d3eaa{width:48.1pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-8d0d3eab{width:67pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-8d0d3eac{width:101.3pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-8d0d3ead{width:45pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}</style><table class='cl-8d15017c'>
```

```{=html}
<thead><tr style="overflow-wrap:break-word;"><td class="cl-8d0d3ead"><p class="cl-8d0d195a"><span class="cl-8d0d1958">t</span></p></td><td class="cl-8d0d3eab"><p class="cl-8d0d195a"><span class="cl-8d0d1958">Paises</span></p></td><td class="cl-8d0d3eac"><p class="cl-8d0d195b"><span class="cl-8d0d1958">PIB</span></p></td><td class="cl-8d0d3eaa"><p class="cl-8d0d195b"><span class="cl-8d0d1958">IPC</span></p></td></tr></thead><tbody><tr style="overflow-wrap:break-word;"><td class="cl-8d0d3ea9"><p class="cl-8d0d195a"><span class="cl-8d0d1959">2014</span></p></td><td class="cl-8d0d3ea7"><p class="cl-8d0d195a"><span class="cl-8d0d1959">Colombia</span></p></td><td class="cl-8d0d3ea8"><p class="cl-8d0d195b"><span class="cl-8d0d1959">234.31 Mill. de $</span></p></td><td class="cl-8d0d3ea6"><p class="cl-8d0d195b"><span class="cl-8d0d1959">108,0</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-8d0d3ea9"><p class="cl-8d0d195a"><span class="cl-8d0d1959">2015</span></p></td><td class="cl-8d0d3ea7"><p class="cl-8d0d195a"><span class="cl-8d0d1959">Colombia</span></p></td><td class="cl-8d0d3ea8"><p class="cl-8d0d195b"><span class="cl-8d0d1959">116.51 Mill. de $</span></p></td><td class="cl-8d0d3ea6"><p class="cl-8d0d195b"><span class="cl-8d0d1959">103,9</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-8d0d3ea9"><p class="cl-8d0d195a"><span class="cl-8d0d1959">2014</span></p></td><td class="cl-8d0d3ea7"><p class="cl-8d0d195a"><span class="cl-8d0d1959">Perú</span></p></td><td class="cl-8d0d3ea8"><p class="cl-8d0d195b"><span class="cl-8d0d1959">287.73 Mill. de $</span></p></td><td class="cl-8d0d3ea6"><p class="cl-8d0d195b"><span class="cl-8d0d1959">108,1</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-8d0d3ea9"><p class="cl-8d0d195a"><span class="cl-8d0d1959">2015</span></p></td><td class="cl-8d0d3ea7"><p class="cl-8d0d195a"><span class="cl-8d0d1959">Perú</span></p></td><td class="cl-8d0d3ea8"><p class="cl-8d0d195b"><span class="cl-8d0d1959">113.82 Mill. de $</span></p></td><td class="cl-8d0d3ea6"><p class="cl-8d0d195b"><span class="cl-8d0d1959">91,0</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-8d0d3ea9"><p class="cl-8d0d195a"><span class="cl-8d0d1959">2014</span></p></td><td class="cl-8d0d3ea7"><p class="cl-8d0d195a"><span class="cl-8d0d1959">Brasil</span></p></td><td class="cl-8d0d3ea8"><p class="cl-8d0d195b"><span class="cl-8d0d1959">177.37 Mill. de $</span></p></td><td class="cl-8d0d3ea6"><p class="cl-8d0d195b"><span class="cl-8d0d1959">93,3</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-8d0d3ea9"><p class="cl-8d0d195a"><span class="cl-8d0d1959">2015</span></p></td><td class="cl-8d0d3ea7"><p class="cl-8d0d195a"><span class="cl-8d0d1959">Brasil</span></p></td><td class="cl-8d0d3ea8"><p class="cl-8d0d195b"><span class="cl-8d0d1959">110.42 Mill. de $</span></p></td><td class="cl-8d0d3ea6"><p class="cl-8d0d195b"><span class="cl-8d0d1959">99,3</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-8d0d3ea9"><p class="cl-8d0d195a"><span class="cl-8d0d1959">2014</span></p></td><td class="cl-8d0d3ea7"><p class="cl-8d0d195a"><span class="cl-8d0d1959">Chile</span></p></td><td class="cl-8d0d3ea8"><p class="cl-8d0d195b"><span class="cl-8d0d1959">136.66 Mill. de $</span></p></td><td class="cl-8d0d3ea6"><p class="cl-8d0d195b"><span class="cl-8d0d1959">67,9</span></p></td></tr></tbody></table></div></template>
<div class="flextable-shadow-host" id="a392756d-1903-4e9b-8a66-0b16dedda5bc"></div>
<script>
var dest = document.getElementById("a392756d-1903-4e9b-8a66-0b16dedda5bc");
var template = document.getElementById("fe78e46a-1664-4fae-8157-0c20a6c9aab4");
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



