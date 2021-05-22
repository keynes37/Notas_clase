# Datos

Una de las cosas mas importantes que debe hacer todo economista al hacer uso de **R**, es importar las **bases de datos** con las que pretende trabajar y armar su *proyecto*. Los datos vienen desde distintos formatos y poseen varias clasificaciones, recordemos unos conceptos claves para avanzar

- **Base de datos**: Es una colección especifica de datos.
- Que posee un **formato** ``popular'', es decir, es una tabla (matrices)
- También es de forma *rectangular* cuya organización aborda **filas** y **columnas**.
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

Son aquellas *bases* que regularmente tienen información en un solo periodo de tiempo y que varían por individuos, instituciones, países o empresas. Se denotan sus observaciones con el subíndice (i), por ejemplo: $X_{i}$. Donde $X$ hace referencia a cada una de las variables como el nombre, la edad, los ingresos, etc.  

```{=html}
<template id="4c8b2fa2-7912-4451-b2a3-4b72d4fb5491"><style>
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
</style><div class="tabwid"><style>.cl-121bf3c0{border-collapse:collapse;}.cl-1210d724{font-family:'Arial';font-size:11pt;font-weight:bold;font-style:normal;text-decoration:none;color:rgba(236, 147, 70, 1.00);background-color:transparent;}.cl-1210d725{font-family:'Arial';font-size:11pt;font-weight:normal;font-style:normal;text-decoration:none;color:rgba(164, 206, 229, 1.00);background-color:transparent;}.cl-1210d726{margin:0;text-align:left;border-bottom: 0 solid rgba(0, 0, 0, 1.00);border-top: 0 solid rgba(0, 0, 0, 1.00);border-left: 0 solid rgba(0, 0, 0, 1.00);border-right: 0 solid rgba(0, 0, 0, 1.00);padding-bottom:5pt;padding-top:5pt;padding-left:5pt;padding-right:5pt;line-height: 1;background-color:transparent;}.cl-1210d727{margin:0;text-align:right;border-bottom: 0 solid rgba(0, 0, 0, 1.00);border-top: 0 solid rgba(0, 0, 0, 1.00);border-left: 0 solid rgba(0, 0, 0, 1.00);border-right: 0 solid rgba(0, 0, 0, 1.00);padding-bottom:5pt;padding-top:5pt;padding-left:5pt;padding-right:5pt;line-height: 1;background-color:transparent;}.cl-1211258a{width:47.4pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-1211258b{width:146.5pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-1211258c{width:91.4pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-1211258d{width:75.6pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-1211258e{width:83.5pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-1211258f{width:52.3pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-12112590{width:46.8pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-12112591{width:52.3pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-12112592{width:83.5pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-12112593{width:146.5pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-12112594{width:47.4pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-12114c04{width:75.6pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-12114c05{width:46.8pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-12114c06{width:91.4pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-12114c07{width:83.5pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-12114c08{width:52.3pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-12114c09{width:75.6pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-12114c0a{width:47.4pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-12114c0b{width:91.4pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-12114c0c{width:46.8pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-12114c0d{width:146.5pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-12114c0e{width:83.5pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-12117378{width:146.5pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-12117379{width:75.6pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-1211737a{width:47.4pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-1211737b{width:91.4pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-1211737c{width:46.8pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-1211737d{width:52.3pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}</style><table class='cl-121bf3c0'>
```

```{=html}
<thead><tr style="overflow-wrap:break-word;"><td class="cl-12114c0d"><p class="cl-1210d726"><span class="cl-1210d724">Nombre</span></p></td><td class="cl-12114c09"><p class="cl-1210d727"><span class="cl-1210d724">Grado</span></p></td><td class="cl-12114c0a"><p class="cl-1210d727"><span class="cl-1210d724">Edad</span></p></td><td class="cl-12114c07"><p class="cl-1210d727"><span class="cl-1210d724">Ingresos</span></p></td><td class="cl-12114c0c"><p class="cl-1210d727"><span class="cl-1210d724">Peso</span></p></td><td class="cl-12114c08"><p class="cl-1210d727"><span class="cl-1210d724">Altura</span></p></td><td class="cl-12114c0b"><p class="cl-1210d726"><span class="cl-1210d724">Color_ojos</span></p></td></tr></thead><tbody><tr style="overflow-wrap:break-word;"><td class="cl-1211258b"><p class="cl-1210d726"><span class="cl-1210d725">Matias Barrows-Jast</span></p></td><td class="cl-1211258d"><p class="cl-1210d727"><span class="cl-1210d725">15/12/2022</span></p></td><td class="cl-1211258a"><p class="cl-1210d727"><span class="cl-1210d725"># 27</span></p></td><td class="cl-1211258e"><p class="cl-1210d727"><span class="cl-1210d725">$880 588</span></p></td><td class="cl-12112590"><p class="cl-1210d727"><span class="cl-1210d725">56,7</span></p></td><td class="cl-1211258f"><p class="cl-1210d727"><span class="cl-1210d725">180,8</span></p></td><td class="cl-1211258c"><p class="cl-1210d726"><span class="cl-1210d725">color: Verdes</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-12112593"><p class="cl-1210d726"><span class="cl-1210d725">Kayson Franecki</span></p></td><td class="cl-12114c04"><p class="cl-1210d727"><span class="cl-1210d725">08/05/2000</span></p></td><td class="cl-12112594"><p class="cl-1210d727"><span class="cl-1210d725"># 26</span></p></td><td class="cl-12112592"><p class="cl-1210d727"><span class="cl-1210d725">No responde</span></p></td><td class="cl-12114c05"><p class="cl-1210d727"><span class="cl-1210d725">64,6</span></p></td><td class="cl-12112591"><p class="cl-1210d727"><span class="cl-1210d725">176,0</span></p></td><td class="cl-12114c06"><p class="cl-1210d726"><span class="cl-1210d725">color: Oscuros</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-12114c0d"><p class="cl-1210d726"><span class="cl-1210d725">Garrick Langworth</span></p></td><td class="cl-12114c09"><p class="cl-1210d727"><span class="cl-1210d725">05/03/2032</span></p></td><td class="cl-12114c0a"><p class="cl-1210d727"><span class="cl-1210d725"># 22</span></p></td><td class="cl-12114c07"><p class="cl-1210d727"><span class="cl-1210d725">No responde</span></p></td><td class="cl-12114c0c"><p class="cl-1210d727"><span class="cl-1210d725">90,1</span></p></td><td class="cl-12114c08"><p class="cl-1210d727"><span class="cl-1210d725">164,4</span></p></td><td class="cl-12114c0b"><p class="cl-1210d726"><span class="cl-1210d725">color: Oscuros</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-12117378"><p class="cl-1210d726"><span class="cl-1210d725">Cordell Dickens</span></p></td><td class="cl-12117379"><p class="cl-1210d727"><span class="cl-1210d725">21/04/2040</span></p></td><td class="cl-1211737a"><p class="cl-1210d727"><span class="cl-1210d725"># 25</span></p></td><td class="cl-12114c0e"><p class="cl-1210d727"><span class="cl-1210d725">No responde</span></p></td><td class="cl-1211737c"><p class="cl-1210d727"><span class="cl-1210d725">75,1</span></p></td><td class="cl-1211737d"><p class="cl-1210d727"><span class="cl-1210d725">168,0</span></p></td><td class="cl-1211737b"><p class="cl-1210d726"><span class="cl-1210d725">color: Azules</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-12112593"><p class="cl-1210d726"><span class="cl-1210d725">Destiney Dicki</span></p></td><td class="cl-12114c04"><p class="cl-1210d727"><span class="cl-1210d725">07/06/2016</span></p></td><td class="cl-12112594"><p class="cl-1210d727"><span class="cl-1210d725"># 28</span></p></td><td class="cl-12112592"><p class="cl-1210d727"><span class="cl-1210d725">$415 902</span></p></td><td class="cl-12114c05"><p class="cl-1210d727"><span class="cl-1210d725">97,3</span></p></td><td class="cl-12112591"><p class="cl-1210d727"><span class="cl-1210d725">167,7</span></p></td><td class="cl-12114c06"><p class="cl-1210d726"><span class="cl-1210d725">color: Oscuros</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-1211258b"><p class="cl-1210d726"><span class="cl-1210d725">Mrs. Freddie Pouros DDS</span></p></td><td class="cl-1211258d"><p class="cl-1210d727"><span class="cl-1210d725">29/09/2017</span></p></td><td class="cl-1211258a"><p class="cl-1210d727"><span class="cl-1210d725"># 32</span></p></td><td class="cl-1211258e"><p class="cl-1210d727"><span class="cl-1210d725">$784 231</span></p></td><td class="cl-12112590"><p class="cl-1210d727"><span class="cl-1210d725">56,2</span></p></td><td class="cl-1211258f"><p class="cl-1210d727"><span class="cl-1210d725">173,9</span></p></td><td class="cl-1211258c"><p class="cl-1210d726"><span class="cl-1210d725">color: Azules</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-1211258b"><p class="cl-1210d726"><span class="cl-1210d725">Ms. Jada Lesch</span></p></td><td class="cl-1211258d"><p class="cl-1210d727"><span class="cl-1210d725">18/09/2028</span></p></td><td class="cl-1211258a"><p class="cl-1210d727"><span class="cl-1210d725"># 33</span></p></td><td class="cl-1211258e"><p class="cl-1210d727"><span class="cl-1210d725">$942 982</span></p></td><td class="cl-12112590"><p class="cl-1210d727"><span class="cl-1210d725">76,1</span></p></td><td class="cl-1211258f"><p class="cl-1210d727"><span class="cl-1210d725">169,6</span></p></td><td class="cl-1211258c"><p class="cl-1210d726"><span class="cl-1210d725">color: Azules</span></p></td></tr></tbody></table></div></template>
<div class="flextable-shadow-host" id="b7851d56-a900-46c4-b91b-6ae0d65a6b43"></div>
<script>
var dest = document.getElementById("b7851d56-a900-46c4-b91b-6ae0d65a6b43");
var template = document.getElementById("4c8b2fa2-7912-4451-b2a3-4b72d4fb5491");
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
<template id="506ce3b4-acba-479d-9674-dba33a6edac4"><style>
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
</style><div class="tabwid"><style>.cl-123918ec{border-collapse:collapse;}.cl-1231a3e6{font-family:'Arial';font-size:11pt;font-weight:bold;font-style:normal;text-decoration:none;color:rgba(236, 147, 70, 1.00);background-color:transparent;}.cl-1231a3e7{font-family:'Arial';font-size:11pt;font-weight:normal;font-style:normal;text-decoration:none;color:rgba(164, 206, 229, 1.00);background-color:transparent;}.cl-1231cad8{margin:0;text-align:left;border-bottom: 0 solid rgba(0, 0, 0, 1.00);border-top: 0 solid rgba(0, 0, 0, 1.00);border-left: 0 solid rgba(0, 0, 0, 1.00);border-right: 0 solid rgba(0, 0, 0, 1.00);padding-bottom:5pt;padding-top:5pt;padding-left:5pt;padding-right:5pt;line-height: 1;background-color:transparent;}.cl-1231cad9{margin:0;text-align:right;border-bottom: 0 solid rgba(0, 0, 0, 1.00);border-top: 0 solid rgba(0, 0, 0, 1.00);border-left: 0 solid rgba(0, 0, 0, 1.00);border-right: 0 solid rgba(0, 0, 0, 1.00);padding-bottom:5pt;padding-top:5pt;padding-left:5pt;padding-right:5pt;line-height: 1;background-color:transparent;}.cl-1231f1ca{width:48.1pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-1231f1cb{width:101.3pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-1231f1cc{width:45pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-1231f1cd{width:101.3pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-1231f1ce{width:48.1pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-1231f1cf{width:45pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}</style><table class='cl-123918ec'>
```

```{=html}
<thead><tr style="overflow-wrap:break-word;"><td class="cl-1231f1cf"><p class="cl-1231cad8"><span class="cl-1231a3e6">t</span></p></td><td class="cl-1231f1cd"><p class="cl-1231cad9"><span class="cl-1231a3e6">PIB</span></p></td><td class="cl-1231f1ce"><p class="cl-1231cad9"><span class="cl-1231a3e6">IPC</span></p></td></tr></thead><tbody><tr style="overflow-wrap:break-word;"><td class="cl-1231f1cc"><p class="cl-1231cad8"><span class="cl-1231a3e7">2015</span></p></td><td class="cl-1231f1cb"><p class="cl-1231cad9"><span class="cl-1231a3e7">110.77 Mill. de $</span></p></td><td class="cl-1231f1ca"><p class="cl-1231cad9"><span class="cl-1231a3e7">77,3</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-1231f1cc"><p class="cl-1231cad8"><span class="cl-1231a3e7">2016</span></p></td><td class="cl-1231f1cb"><p class="cl-1231cad9"><span class="cl-1231a3e7">133.89 Mill. de $</span></p></td><td class="cl-1231f1ca"><p class="cl-1231cad9"><span class="cl-1231a3e7">83,1</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-1231f1cc"><p class="cl-1231cad8"><span class="cl-1231a3e7">2017</span></p></td><td class="cl-1231f1cb"><p class="cl-1231cad9"><span class="cl-1231a3e7">259.11 Mill. de $</span></p></td><td class="cl-1231f1ca"><p class="cl-1231cad9"><span class="cl-1231a3e7">85,5</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-1231f1cc"><p class="cl-1231cad8"><span class="cl-1231a3e7">2018</span></p></td><td class="cl-1231f1cb"><p class="cl-1231cad9"><span class="cl-1231a3e7">154.94 Mill. de $</span></p></td><td class="cl-1231f1ca"><p class="cl-1231cad9"><span class="cl-1231a3e7">102,2</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-1231f1cc"><p class="cl-1231cad8"><span class="cl-1231a3e7">2019</span></p></td><td class="cl-1231f1cb"><p class="cl-1231cad9"><span class="cl-1231a3e7">159.05 Mill. de $</span></p></td><td class="cl-1231f1ca"><p class="cl-1231cad9"><span class="cl-1231a3e7">93,6</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-1231f1cc"><p class="cl-1231cad8"><span class="cl-1231a3e7">2020</span></p></td><td class="cl-1231f1cb"><p class="cl-1231cad9"><span class="cl-1231a3e7">270.05 Mill. de $</span></p></td><td class="cl-1231f1ca"><p class="cl-1231cad9"><span class="cl-1231a3e7">94,0</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-1231f1cc"><p class="cl-1231cad8"><span class="cl-1231a3e7">2021</span></p></td><td class="cl-1231f1cb"><p class="cl-1231cad9"><span class="cl-1231a3e7">182.26 Mill. de $</span></p></td><td class="cl-1231f1ca"><p class="cl-1231cad9"><span class="cl-1231a3e7">91,1</span></p></td></tr></tbody></table></div></template>
<div class="flextable-shadow-host" id="fc6fba5d-cad2-46e7-8b29-15a2cf1d79c1"></div>
<script>
var dest = document.getElementById("fc6fba5d-cad2-46e7-8b29-15a2cf1d79c1");
var template = document.getElementById("506ce3b4-acba-479d-9674-dba33a6edac4");
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
<template id="e3b57950-bb3f-492b-9afc-2441e27a2e8f"><style>
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
</style><div class="tabwid"><style>.cl-125713a6{border-collapse:collapse;}.cl-124f29d4{font-family:'Arial';font-size:11pt;font-weight:bold;font-style:normal;text-decoration:none;color:rgba(236, 147, 70, 1.00);background-color:transparent;}.cl-124f29d5{font-family:'Arial';font-size:11pt;font-weight:normal;font-style:normal;text-decoration:none;color:rgba(164, 206, 229, 1.00);background-color:transparent;}.cl-124f50c6{margin:0;text-align:left;border-bottom: 0 solid rgba(0, 0, 0, 1.00);border-top: 0 solid rgba(0, 0, 0, 1.00);border-left: 0 solid rgba(0, 0, 0, 1.00);border-right: 0 solid rgba(0, 0, 0, 1.00);padding-bottom:5pt;padding-top:5pt;padding-left:5pt;padding-right:5pt;line-height: 1;background-color:transparent;}.cl-124f50c7{margin:0;text-align:right;border-bottom: 0 solid rgba(0, 0, 0, 1.00);border-top: 0 solid rgba(0, 0, 0, 1.00);border-left: 0 solid rgba(0, 0, 0, 1.00);border-right: 0 solid rgba(0, 0, 0, 1.00);padding-bottom:5pt;padding-top:5pt;padding-left:5pt;padding-right:5pt;line-height: 1;background-color:transparent;}.cl-124f77b8{width:48.1pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-124f77b9{width:67pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-124f77ba{width:101.3pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-124f77bb{width:45pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-124f77bc{width:48.1pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-124f77bd{width:67pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-124f77be{width:101.3pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-124f77bf{width:45pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}</style><table class='cl-125713a6'>
```

```{=html}
<thead><tr style="overflow-wrap:break-word;"><td class="cl-124f77bf"><p class="cl-124f50c6"><span class="cl-124f29d4">t</span></p></td><td class="cl-124f77bd"><p class="cl-124f50c6"><span class="cl-124f29d4">Paises</span></p></td><td class="cl-124f77be"><p class="cl-124f50c7"><span class="cl-124f29d4">PIB</span></p></td><td class="cl-124f77bc"><p class="cl-124f50c7"><span class="cl-124f29d4">IPC</span></p></td></tr></thead><tbody><tr style="overflow-wrap:break-word;"><td class="cl-124f77bb"><p class="cl-124f50c6"><span class="cl-124f29d5">2014</span></p></td><td class="cl-124f77b9"><p class="cl-124f50c6"><span class="cl-124f29d5">Colombia</span></p></td><td class="cl-124f77ba"><p class="cl-124f50c7"><span class="cl-124f29d5">234.31 Mill. de $</span></p></td><td class="cl-124f77b8"><p class="cl-124f50c7"><span class="cl-124f29d5">108,0</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-124f77bb"><p class="cl-124f50c6"><span class="cl-124f29d5">2015</span></p></td><td class="cl-124f77b9"><p class="cl-124f50c6"><span class="cl-124f29d5">Colombia</span></p></td><td class="cl-124f77ba"><p class="cl-124f50c7"><span class="cl-124f29d5">116.51 Mill. de $</span></p></td><td class="cl-124f77b8"><p class="cl-124f50c7"><span class="cl-124f29d5">103,9</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-124f77bb"><p class="cl-124f50c6"><span class="cl-124f29d5">2014</span></p></td><td class="cl-124f77b9"><p class="cl-124f50c6"><span class="cl-124f29d5">Perú</span></p></td><td class="cl-124f77ba"><p class="cl-124f50c7"><span class="cl-124f29d5">287.73 Mill. de $</span></p></td><td class="cl-124f77b8"><p class="cl-124f50c7"><span class="cl-124f29d5">108,1</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-124f77bb"><p class="cl-124f50c6"><span class="cl-124f29d5">2015</span></p></td><td class="cl-124f77b9"><p class="cl-124f50c6"><span class="cl-124f29d5">Perú</span></p></td><td class="cl-124f77ba"><p class="cl-124f50c7"><span class="cl-124f29d5">113.82 Mill. de $</span></p></td><td class="cl-124f77b8"><p class="cl-124f50c7"><span class="cl-124f29d5">91,0</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-124f77bb"><p class="cl-124f50c6"><span class="cl-124f29d5">2014</span></p></td><td class="cl-124f77b9"><p class="cl-124f50c6"><span class="cl-124f29d5">Brasil</span></p></td><td class="cl-124f77ba"><p class="cl-124f50c7"><span class="cl-124f29d5">177.37 Mill. de $</span></p></td><td class="cl-124f77b8"><p class="cl-124f50c7"><span class="cl-124f29d5">93,3</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-124f77bb"><p class="cl-124f50c6"><span class="cl-124f29d5">2015</span></p></td><td class="cl-124f77b9"><p class="cl-124f50c6"><span class="cl-124f29d5">Brasil</span></p></td><td class="cl-124f77ba"><p class="cl-124f50c7"><span class="cl-124f29d5">110.42 Mill. de $</span></p></td><td class="cl-124f77b8"><p class="cl-124f50c7"><span class="cl-124f29d5">99,3</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-124f77bb"><p class="cl-124f50c6"><span class="cl-124f29d5">2014</span></p></td><td class="cl-124f77b9"><p class="cl-124f50c6"><span class="cl-124f29d5">Chile</span></p></td><td class="cl-124f77ba"><p class="cl-124f50c7"><span class="cl-124f29d5">136.66 Mill. de $</span></p></td><td class="cl-124f77b8"><p class="cl-124f50c7"><span class="cl-124f29d5">67,9</span></p></td></tr></tbody></table></div></template>
<div class="flextable-shadow-host" id="554624ef-7cfa-45fa-ae67-57955e07b1ef"></div>
<script>
var dest = document.getElementById("554624ef-7cfa-45fa-ae67-57955e07b1ef");
var template = document.getElementById("e3b57950-bb3f-492b-9afc-2441e27a2e8f");
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

Ahora esto, pero mirando el git adicional

