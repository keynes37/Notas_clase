# Primer análisis de datos
La **importancia** del análisis de datos es requerida para tomar decisiones y conocer muy bien lo que cada una de las variables nos esta indicando, es por esto que recurrimos a la **estadística** y hacemos uso de las distintas medidas de tendencia central ampliamente conocidas como media, desviación estándar, asimetría y curtosis.

\begin{align*}
    \bar{X}=& \frac{\sum \limits_{i=1}^{n} x_{i}}{n}\\
    Var(X)=& \frac{\sum \limits_{i=1}^{n} (x_{i} - \bar{x})^{2}}{n} \\
    Asimetría (Fisher)=& \frac{\mu^{3}}{\sigma^{3}} \\
    Curtosis= & \frac{\sum \limits_{i=1}^{n} (x_{i} - \bar{x})^{4}}{n\sigma^{2}}-3 
\end{align*}
_Donde (n) es el tamaño de la muestra, (x) las observaciones,$(\sigma)$ la desviación estándar, $\mu$ la media de la distribución. Con una base de datos podemos entonces tener_