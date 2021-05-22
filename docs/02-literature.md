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
<template id="9461bf23-3980-402d-a549-cfbf473a1e8f"><style>
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
</style><div class="tabwid"><style>.cl-377f4c12{border-collapse:collapse;}.cl-3774ca76{font-family:'Arial';font-size:11pt;font-weight:bold;font-style:normal;text-decoration:none;color:rgba(236, 147, 70, 1.00);background-color:transparent;}.cl-3774ca77{font-family:'Arial';font-size:11pt;font-weight:normal;font-style:normal;text-decoration:none;color:rgba(164, 206, 229, 1.00);background-color:transparent;}.cl-3774ca78{margin:0;text-align:left;border-bottom: 0 solid rgba(0, 0, 0, 1.00);border-top: 0 solid rgba(0, 0, 0, 1.00);border-left: 0 solid rgba(0, 0, 0, 1.00);border-right: 0 solid rgba(0, 0, 0, 1.00);padding-bottom:5pt;padding-top:5pt;padding-left:5pt;padding-right:5pt;line-height: 1;background-color:transparent;}.cl-3774ca79{margin:0;text-align:right;border-bottom: 0 solid rgba(0, 0, 0, 1.00);border-top: 0 solid rgba(0, 0, 0, 1.00);border-left: 0 solid rgba(0, 0, 0, 1.00);border-right: 0 solid rgba(0, 0, 0, 1.00);padding-bottom:5pt;padding-top:5pt;padding-left:5pt;padding-right:5pt;line-height: 1;background-color:transparent;}.cl-377519f4{width:47.4pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-377519f5{width:146.5pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-377519f6{width:91.4pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-377519f7{width:75.6pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-377519f8{width:83.5pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-377519f9{width:52.3pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-377519fa{width:46.8pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-377519fb{width:52.3pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-377519fc{width:83.5pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-377519fd{width:146.5pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-377519fe{width:47.4pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-377540e6{width:75.6pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-377540e7{width:46.8pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-377540e8{width:91.4pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-377540e9{width:83.5pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-377540ea{width:52.3pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-377540eb{width:75.6pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-377540ec{width:47.4pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-377540ed{width:91.4pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-377540ee{width:46.8pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-377540ef{width:146.5pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-377540f0{width:83.5pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-377568e6{width:146.5pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-377568e7{width:75.6pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-377568e8{width:47.4pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-377568e9{width:91.4pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-377568ea{width:46.8pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-377568eb{width:52.3pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}</style><table class='cl-377f4c12'>
```

```{=html}
<thead><tr style="overflow-wrap:break-word;"><td class="cl-377540ef"><p class="cl-3774ca78"><span class="cl-3774ca76">Nombre</span></p></td><td class="cl-377540eb"><p class="cl-3774ca79"><span class="cl-3774ca76">Grado</span></p></td><td class="cl-377540ec"><p class="cl-3774ca79"><span class="cl-3774ca76">Edad</span></p></td><td class="cl-377540e9"><p class="cl-3774ca79"><span class="cl-3774ca76">Ingresos</span></p></td><td class="cl-377540ee"><p class="cl-3774ca79"><span class="cl-3774ca76">Peso</span></p></td><td class="cl-377540ea"><p class="cl-3774ca79"><span class="cl-3774ca76">Altura</span></p></td><td class="cl-377540ed"><p class="cl-3774ca78"><span class="cl-3774ca76">Color_ojos</span></p></td></tr></thead><tbody><tr style="overflow-wrap:break-word;"><td class="cl-377519f5"><p class="cl-3774ca78"><span class="cl-3774ca77">Matias Barrows-Jast</span></p></td><td class="cl-377519f7"><p class="cl-3774ca79"><span class="cl-3774ca77">15/12/2022</span></p></td><td class="cl-377519f4"><p class="cl-3774ca79"><span class="cl-3774ca77"># 27</span></p></td><td class="cl-377519f8"><p class="cl-3774ca79"><span class="cl-3774ca77">$880 588</span></p></td><td class="cl-377519fa"><p class="cl-3774ca79"><span class="cl-3774ca77">56,7</span></p></td><td class="cl-377519f9"><p class="cl-3774ca79"><span class="cl-3774ca77">180,8</span></p></td><td class="cl-377519f6"><p class="cl-3774ca78"><span class="cl-3774ca77">color: Verdes</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-377519fd"><p class="cl-3774ca78"><span class="cl-3774ca77">Kayson Franecki</span></p></td><td class="cl-377540e6"><p class="cl-3774ca79"><span class="cl-3774ca77">08/05/2000</span></p></td><td class="cl-377519fe"><p class="cl-3774ca79"><span class="cl-3774ca77"># 26</span></p></td><td class="cl-377519fc"><p class="cl-3774ca79"><span class="cl-3774ca77">No responde</span></p></td><td class="cl-377540e7"><p class="cl-3774ca79"><span class="cl-3774ca77">64,6</span></p></td><td class="cl-377519fb"><p class="cl-3774ca79"><span class="cl-3774ca77">176,0</span></p></td><td class="cl-377540e8"><p class="cl-3774ca78"><span class="cl-3774ca77">color: Oscuros</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-377540ef"><p class="cl-3774ca78"><span class="cl-3774ca77">Garrick Langworth</span></p></td><td class="cl-377540eb"><p class="cl-3774ca79"><span class="cl-3774ca77">05/03/2032</span></p></td><td class="cl-377540ec"><p class="cl-3774ca79"><span class="cl-3774ca77"># 22</span></p></td><td class="cl-377540e9"><p class="cl-3774ca79"><span class="cl-3774ca77">No responde</span></p></td><td class="cl-377540ee"><p class="cl-3774ca79"><span class="cl-3774ca77">90,1</span></p></td><td class="cl-377540ea"><p class="cl-3774ca79"><span class="cl-3774ca77">164,4</span></p></td><td class="cl-377540ed"><p class="cl-3774ca78"><span class="cl-3774ca77">color: Oscuros</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-377568e6"><p class="cl-3774ca78"><span class="cl-3774ca77">Cordell Dickens</span></p></td><td class="cl-377568e7"><p class="cl-3774ca79"><span class="cl-3774ca77">21/04/2040</span></p></td><td class="cl-377568e8"><p class="cl-3774ca79"><span class="cl-3774ca77"># 25</span></p></td><td class="cl-377540f0"><p class="cl-3774ca79"><span class="cl-3774ca77">No responde</span></p></td><td class="cl-377568ea"><p class="cl-3774ca79"><span class="cl-3774ca77">75,1</span></p></td><td class="cl-377568eb"><p class="cl-3774ca79"><span class="cl-3774ca77">168,0</span></p></td><td class="cl-377568e9"><p class="cl-3774ca78"><span class="cl-3774ca77">color: Azules</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-377519fd"><p class="cl-3774ca78"><span class="cl-3774ca77">Destiney Dicki</span></p></td><td class="cl-377540e6"><p class="cl-3774ca79"><span class="cl-3774ca77">07/06/2016</span></p></td><td class="cl-377519fe"><p class="cl-3774ca79"><span class="cl-3774ca77"># 28</span></p></td><td class="cl-377519fc"><p class="cl-3774ca79"><span class="cl-3774ca77">$415 902</span></p></td><td class="cl-377540e7"><p class="cl-3774ca79"><span class="cl-3774ca77">97,3</span></p></td><td class="cl-377519fb"><p class="cl-3774ca79"><span class="cl-3774ca77">167,7</span></p></td><td class="cl-377540e8"><p class="cl-3774ca78"><span class="cl-3774ca77">color: Oscuros</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-377519f5"><p class="cl-3774ca78"><span class="cl-3774ca77">Mrs. Freddie Pouros DDS</span></p></td><td class="cl-377519f7"><p class="cl-3774ca79"><span class="cl-3774ca77">29/09/2017</span></p></td><td class="cl-377519f4"><p class="cl-3774ca79"><span class="cl-3774ca77"># 32</span></p></td><td class="cl-377519f8"><p class="cl-3774ca79"><span class="cl-3774ca77">$784 231</span></p></td><td class="cl-377519fa"><p class="cl-3774ca79"><span class="cl-3774ca77">56,2</span></p></td><td class="cl-377519f9"><p class="cl-3774ca79"><span class="cl-3774ca77">173,9</span></p></td><td class="cl-377519f6"><p class="cl-3774ca78"><span class="cl-3774ca77">color: Azules</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-377519f5"><p class="cl-3774ca78"><span class="cl-3774ca77">Ms. Jada Lesch</span></p></td><td class="cl-377519f7"><p class="cl-3774ca79"><span class="cl-3774ca77">18/09/2028</span></p></td><td class="cl-377519f4"><p class="cl-3774ca79"><span class="cl-3774ca77"># 33</span></p></td><td class="cl-377519f8"><p class="cl-3774ca79"><span class="cl-3774ca77">$942 982</span></p></td><td class="cl-377519fa"><p class="cl-3774ca79"><span class="cl-3774ca77">76,1</span></p></td><td class="cl-377519f9"><p class="cl-3774ca79"><span class="cl-3774ca77">169,6</span></p></td><td class="cl-377519f6"><p class="cl-3774ca78"><span class="cl-3774ca77">color: Azules</span></p></td></tr></tbody></table></div></template>
<div class="flextable-shadow-host" id="83bfb556-6005-4230-97fa-efff76325a23"></div>
<script>
var dest = document.getElementById("83bfb556-6005-4230-97fa-efff76325a23");
var template = document.getElementById("9461bf23-3980-402d-a549-cfbf473a1e8f");
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
<template id="62067ea4-70e1-4938-b8c0-9c2683872079"><style>
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
</style><div class="tabwid"><style>.cl-37a0dd50{border-collapse:collapse;}.cl-37994252{font-family:'Arial';font-size:11pt;font-weight:bold;font-style:normal;text-decoration:none;color:rgba(236, 147, 70, 1.00);background-color:transparent;}.cl-37994253{font-family:'Arial';font-size:11pt;font-weight:normal;font-style:normal;text-decoration:none;color:rgba(164, 206, 229, 1.00);background-color:transparent;}.cl-37994254{margin:0;text-align:left;border-bottom: 0 solid rgba(0, 0, 0, 1.00);border-top: 0 solid rgba(0, 0, 0, 1.00);border-left: 0 solid rgba(0, 0, 0, 1.00);border-right: 0 solid rgba(0, 0, 0, 1.00);padding-bottom:5pt;padding-top:5pt;padding-left:5pt;padding-right:5pt;line-height: 1;background-color:transparent;}.cl-37994255{margin:0;text-align:right;border-bottom: 0 solid rgba(0, 0, 0, 1.00);border-top: 0 solid rgba(0, 0, 0, 1.00);border-left: 0 solid rgba(0, 0, 0, 1.00);border-right: 0 solid rgba(0, 0, 0, 1.00);padding-bottom:5pt;padding-top:5pt;padding-left:5pt;padding-right:5pt;line-height: 1;background-color:transparent;}.cl-37998f50{width:48.1pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-37998f51{width:101.3pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-37998f52{width:45pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-37998f53{width:101.3pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-37998f54{width:48.1pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-37998f55{width:45pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}</style><table class='cl-37a0dd50'>
```

```{=html}
<thead><tr style="overflow-wrap:break-word;"><td class="cl-37998f55"><p class="cl-37994254"><span class="cl-37994252">t</span></p></td><td class="cl-37998f53"><p class="cl-37994255"><span class="cl-37994252">PIB</span></p></td><td class="cl-37998f54"><p class="cl-37994255"><span class="cl-37994252">IPC</span></p></td></tr></thead><tbody><tr style="overflow-wrap:break-word;"><td class="cl-37998f52"><p class="cl-37994254"><span class="cl-37994253">2015</span></p></td><td class="cl-37998f51"><p class="cl-37994255"><span class="cl-37994253">110.77 Mill. de $</span></p></td><td class="cl-37998f50"><p class="cl-37994255"><span class="cl-37994253">77,3</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-37998f52"><p class="cl-37994254"><span class="cl-37994253">2016</span></p></td><td class="cl-37998f51"><p class="cl-37994255"><span class="cl-37994253">133.89 Mill. de $</span></p></td><td class="cl-37998f50"><p class="cl-37994255"><span class="cl-37994253">83,1</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-37998f52"><p class="cl-37994254"><span class="cl-37994253">2017</span></p></td><td class="cl-37998f51"><p class="cl-37994255"><span class="cl-37994253">259.11 Mill. de $</span></p></td><td class="cl-37998f50"><p class="cl-37994255"><span class="cl-37994253">85,5</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-37998f52"><p class="cl-37994254"><span class="cl-37994253">2018</span></p></td><td class="cl-37998f51"><p class="cl-37994255"><span class="cl-37994253">154.94 Mill. de $</span></p></td><td class="cl-37998f50"><p class="cl-37994255"><span class="cl-37994253">102,2</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-37998f52"><p class="cl-37994254"><span class="cl-37994253">2019</span></p></td><td class="cl-37998f51"><p class="cl-37994255"><span class="cl-37994253">159.05 Mill. de $</span></p></td><td class="cl-37998f50"><p class="cl-37994255"><span class="cl-37994253">93,6</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-37998f52"><p class="cl-37994254"><span class="cl-37994253">2020</span></p></td><td class="cl-37998f51"><p class="cl-37994255"><span class="cl-37994253">270.05 Mill. de $</span></p></td><td class="cl-37998f50"><p class="cl-37994255"><span class="cl-37994253">94,0</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-37998f52"><p class="cl-37994254"><span class="cl-37994253">2021</span></p></td><td class="cl-37998f51"><p class="cl-37994255"><span class="cl-37994253">182.26 Mill. de $</span></p></td><td class="cl-37998f50"><p class="cl-37994255"><span class="cl-37994253">91,1</span></p></td></tr></tbody></table></div></template>
<div class="flextable-shadow-host" id="5af00d48-802e-4a45-b5d0-e3b76492f674"></div>
<script>
var dest = document.getElementById("5af00d48-802e-4a45-b5d0-e3b76492f674");
var template = document.getElementById("62067ea4-70e1-4938-b8c0-9c2683872079");
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
<template id="aea3e870-65b5-4f17-a72e-8197436b2816"><style>
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
</style><div class="tabwid"><style>.cl-37c0d4de{border-collapse:collapse;}.cl-37b93918{font-family:'Arial';font-size:11pt;font-weight:bold;font-style:normal;text-decoration:none;color:rgba(236, 147, 70, 1.00);background-color:transparent;}.cl-37b93919{font-family:'Arial';font-size:11pt;font-weight:normal;font-style:normal;text-decoration:none;color:rgba(164, 206, 229, 1.00);background-color:transparent;}.cl-37b9600a{margin:0;text-align:left;border-bottom: 0 solid rgba(0, 0, 0, 1.00);border-top: 0 solid rgba(0, 0, 0, 1.00);border-left: 0 solid rgba(0, 0, 0, 1.00);border-right: 0 solid rgba(0, 0, 0, 1.00);padding-bottom:5pt;padding-top:5pt;padding-left:5pt;padding-right:5pt;line-height: 1;background-color:transparent;}.cl-37b9600b{margin:0;text-align:right;border-bottom: 0 solid rgba(0, 0, 0, 1.00);border-top: 0 solid rgba(0, 0, 0, 1.00);border-left: 0 solid rgba(0, 0, 0, 1.00);border-right: 0 solid rgba(0, 0, 0, 1.00);padding-bottom:5pt;padding-top:5pt;padding-left:5pt;padding-right:5pt;line-height: 1;background-color:transparent;}.cl-37b98490{width:48.1pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-37b98491{width:67pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-37b98492{width:101.3pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-37b98493{width:45pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-37b98494{width:48.1pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-37b98495{width:67pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-37b98496{width:101.3pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-37b98497{width:45pt;background-clip: padding-box;background-color:rgba(0, 0, 0, 1.00);vertical-align: middle;border-bottom: 1pt solid rgba(164, 206, 229, 1.00);border-top: 1pt solid rgba(164, 206, 229, 1.00);border-left: 1pt solid rgba(164, 206, 229, 1.00);border-right: 1pt solid rgba(164, 206, 229, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}</style><table class='cl-37c0d4de'>
```

```{=html}
<thead><tr style="overflow-wrap:break-word;"><td class="cl-37b98497"><p class="cl-37b9600a"><span class="cl-37b93918">t</span></p></td><td class="cl-37b98495"><p class="cl-37b9600a"><span class="cl-37b93918">Paises</span></p></td><td class="cl-37b98496"><p class="cl-37b9600b"><span class="cl-37b93918">PIB</span></p></td><td class="cl-37b98494"><p class="cl-37b9600b"><span class="cl-37b93918">IPC</span></p></td></tr></thead><tbody><tr style="overflow-wrap:break-word;"><td class="cl-37b98493"><p class="cl-37b9600a"><span class="cl-37b93919">2014</span></p></td><td class="cl-37b98491"><p class="cl-37b9600a"><span class="cl-37b93919">Colombia</span></p></td><td class="cl-37b98492"><p class="cl-37b9600b"><span class="cl-37b93919">234.31 Mill. de $</span></p></td><td class="cl-37b98490"><p class="cl-37b9600b"><span class="cl-37b93919">108,0</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-37b98493"><p class="cl-37b9600a"><span class="cl-37b93919">2015</span></p></td><td class="cl-37b98491"><p class="cl-37b9600a"><span class="cl-37b93919">Colombia</span></p></td><td class="cl-37b98492"><p class="cl-37b9600b"><span class="cl-37b93919">116.51 Mill. de $</span></p></td><td class="cl-37b98490"><p class="cl-37b9600b"><span class="cl-37b93919">103,9</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-37b98493"><p class="cl-37b9600a"><span class="cl-37b93919">2014</span></p></td><td class="cl-37b98491"><p class="cl-37b9600a"><span class="cl-37b93919">Perú</span></p></td><td class="cl-37b98492"><p class="cl-37b9600b"><span class="cl-37b93919">287.73 Mill. de $</span></p></td><td class="cl-37b98490"><p class="cl-37b9600b"><span class="cl-37b93919">108,1</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-37b98493"><p class="cl-37b9600a"><span class="cl-37b93919">2015</span></p></td><td class="cl-37b98491"><p class="cl-37b9600a"><span class="cl-37b93919">Perú</span></p></td><td class="cl-37b98492"><p class="cl-37b9600b"><span class="cl-37b93919">113.82 Mill. de $</span></p></td><td class="cl-37b98490"><p class="cl-37b9600b"><span class="cl-37b93919">91,0</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-37b98493"><p class="cl-37b9600a"><span class="cl-37b93919">2014</span></p></td><td class="cl-37b98491"><p class="cl-37b9600a"><span class="cl-37b93919">Brasil</span></p></td><td class="cl-37b98492"><p class="cl-37b9600b"><span class="cl-37b93919">177.37 Mill. de $</span></p></td><td class="cl-37b98490"><p class="cl-37b9600b"><span class="cl-37b93919">93,3</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-37b98493"><p class="cl-37b9600a"><span class="cl-37b93919">2015</span></p></td><td class="cl-37b98491"><p class="cl-37b9600a"><span class="cl-37b93919">Brasil</span></p></td><td class="cl-37b98492"><p class="cl-37b9600b"><span class="cl-37b93919">110.42 Mill. de $</span></p></td><td class="cl-37b98490"><p class="cl-37b9600b"><span class="cl-37b93919">99,3</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-37b98493"><p class="cl-37b9600a"><span class="cl-37b93919">2014</span></p></td><td class="cl-37b98491"><p class="cl-37b9600a"><span class="cl-37b93919">Chile</span></p></td><td class="cl-37b98492"><p class="cl-37b9600b"><span class="cl-37b93919">136.66 Mill. de $</span></p></td><td class="cl-37b98490"><p class="cl-37b9600b"><span class="cl-37b93919">67,9</span></p></td></tr></tbody></table></div></template>
<div class="flextable-shadow-host" id="8a161ba3-1e3a-48c6-bdd0-4b7810f2c005"></div>
<script>
var dest = document.getElementById("8a161ba3-1e3a-48c6-bdd0-4b7810f2c005");
var template = document.getElementById("aea3e870-65b5-4f17-a72e-8197436b2816");
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

