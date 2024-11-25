---
title: "OPTIMIZACIÓN EN LA LÍNEA DE ENSAMBLAJE"
author: "Susana Aguirre, Marlon Atehortúa, Annie Sequeda"
lang: es
theme: Sketchy
format: html
editor: visual
---

::: {style="text-align: justify;"}
```{r include = FALSE}
knitr:: opts_chunk$set(echo = FALSE, message = FALSE, warning = FALSE)
```

## INTRODUCCIÓN

Uno de los trabajos de la ingeniería industrial es el estudio y análisis de las líneas de producción, con el objetivo de mejorar los procesos, reduciendo demoras, actividades innecesarias y gastos. De esta manera, se fomenta la idea del mejoramiento continuo, lo que trae consigo efectos positivos, aumentando las ganancias y, a su vez, la creación de un mejor clima organizacional.

En la línea de producción hay un constante movimiento de operarios y producto, de esta misma manera en el ensamblaje hay factores clave que causan efectos que disminuyen la productividad como lo puede ser el ruido, el tipo de instrucciones y el orden de las piezas que se ensamblan aumentando el tiempo para completar las tareas.

Para el desarrollo de este proyecto se realizó un experimento simulando un escenario de ensamblaje, en el cual un operario se enfrenta a los factores previamente mencionados de forma combinada.Permitiendo realizar el análisis que se presentará a continuación.

## OBJETIVOS

Determinar el efecto individual y combinado de las variables tipo de instrucción, organización de piezas y nivel de ruido sobre el tiempo de ensamblaje:

-   Cuantificar la influencia de cada factor por separado.

-   Evaluar la combinación de estos factores en un solo ensamblaje.

-   Identificar los factores más críticos para optimizar el proceso de ensamblaje.

Evaluar la eficiencia de las instrucciones visuales en comparación con las instrucciones textuales y la ausencia de instrucciones en la reducción del tiempo de ensamblaje:

-   Determinar cuál tipo de instrucción (visual, textual o ninguna) es más eficiente para guiar al ensamblador.

-   Minimizar el tiempo de ensamblaje mediante el uso de instrucciones adecuadas.

Cuantificar el efecto del ruido ambiental en la ejecución de tareas de ensamblaje y su relación con el tiempo final del producto ensamblado:

-   Explorar cómo el ruido ambiental influye en la concentración de la persona que está ensamblando.

-   Analizar cómo el ruido afecta directamente el tiempo final del producto ensamblado.

-   Evaluar cómo el ruido genera errores y afecta la precisión del ensamblaje.

## OPTIMIZACIÓN EN LA LÍNEA DE ENSAMBLAJE

### DESCRIPCIÓN DEL EXPERIMENTO

![](https://github.com/PrettySusi/Experimento-DEAR/blob/main/P.jpeg?raw=true){fig-align="center" width="583"}

Para realizar este experimento se hizo reserva del laboratorio lúdico úbicado en el bloque 21, pues este disponía de los materiales y el lugar necesarios para desarrollar el estudio experimental correctamente.

El orden de actividades realizadas se estructuró de la siguiente manera:

#### Diseño

1.  *Diseño de la figura:* Se estableció la estructura del objeto que se armaría en cada replica del experimento.

![Figura 1: diseño del carrito.](https://github.com/PrettySusi/Experimento-DEAR/blob/main/carrito.jpeg?raw=true%7D){fig-align="center" width="1442"}

2.  *Diseño de Instrucciones:* Se crearon las instrucciones en cada uno de los formatos elegidos.

-   IMAGENES

![Figura 2: Instrucción en imagenes.](https://github.com/PrettySusi/Experimento-DEAR/blob/main/1.png?raw=true)

-   TEXTO

1.  Tomar una base de ruedas y ensamblar un rueda en cada lado de dicha ficha.

2.  Realizar el mismo proceso del paso 1.

3.  Tomar ficha circular morada y ajustar encima de una base de ruedas.

4.  Realizar el mismo procedimiento del paso 2 con la ficha del paso 2.

5.  Ajustar cada par de ruedas en la parte inferior de la base azul una en cada extremo de dicha base.

6.  Ensamblar en la base el par de rectángulos rosados en cada extremo ajustandolo solo con la mitad del rectángulo rosado, dejando la otra mitad fuera de la base.

7.  Encajar las fichas verdes en el centro de la base en dirección del movimiento de las ruedas, en cada extremo.

8.  Ensamblar las 4 fichas semi triangulares rosadas sobre una de las bases rosada.

9.  Ajustar detrás de las fichas rozadas un bloque verde en la dirección contraria a la dirección de las ruedas.

10. Ensamblar las ventanas en cada lado de las bases de las fichas. verdes paralelas justo detrás de la ficha verde colocada en el paso 9.

11. ajustar sobre las ventanas un bloque morado para formar el techo.

12. Ensamblar detrás de los ventanas las fichas semi triangulares blancas, formando un trapecio.

13. Acomodar la base naranja con luces en la parte central trasera del carro.

-   VIDEO [click para ver](https://drive.google.com/file/d/1OJEs8ufnAkLEJSwgmhONAw84kIzVmvnQ/view?usp=sharing)

3.  *Deifinición de los tipos de orden:* Se estableció el orden como ubicarían las fichas previas al ensamblado.

![Figura 3, 4, 5: Fichas ordenadas por tipo, pre ensambladas y desordenadas.](https://github.com/PrettySusi/Experimento-DEAR/blob/main/1%20(1).png?raw=true)

4.  *Definición factores de ruido:* Se estableció el tipo de ruido que se haría dependiendo de la combinación requerida.

-   silencio
-   Ruido moderado: música en volúmen bajo.
-   Ruido Alto: música sofocante.

#### Premuestreo

Antes de llevar a cabo oficialmente el experimento se realizo un premuestreo, verificando que tan factible sería la realización de el experimento con los tiempos obtenidos, para este se eligieron aleatoriamente 9 combinaciones distintas y se realizo el ensamblado de acuerdo a estas. Los tiempos obtenidos también fueron útiles para establecer parámetros que se utilizados para un análisis posterior en R.

| ORDEN                | INSTRUCCIONES | RUIDO    | TIEMPO    |
|----------------------|---------------|----------|-----------|
| Organizadas por tipo | Imagen        | Silencio | 125, 40 s |
| Organizadas por tipo | Imagen        | Moderado | 142,20 s  |
| Organizadas por tipo | texto         | Alto     | 124,80 s  |
| Orgaizadas por tipo  | Video         | Moderado | 75,60 s   |
| Pre ensambladas      | Imagen        | Moderado | 81,60 s   |
| Pre ensambladas      | Texto         | Silencio | 90 s      |
| Pre ensambladas      | Video         | Moderado | 55 s      |
| Mezcladas            | Imagen        | Silencio | 120,60 s  |
| Mezcladas            | Video         | Silencio | 91,20 s   |

#### Experimento

El experimento realizado pertenece a la familia de diseños factoriales 3^3^, pues son 3 factores y cada uno consiste de 3 niveles. El total de tratamientos fueron 27, ya que estos son todas las posibles combinaciones que pueden realizarse entre los niveles de cada factor. Además teniendo en cuenta que se harían 3 tomas de tiempos para cada tratamiento, se obtuvo un total de 81 observaciones. Para aleatorizar las tomas de tiempos, asegurando la validez de los datos, se le solicito a ChatGPT desordenar los numeros del 1 al 81, estos los ubicamos en el [*excel*](https://docs.google.com/spreadsheets/d/1oHcHNWfVKn4JwPl3pzKDuPww45uU82AS/edit?usp=sharing&ouid=110809190313665873677&rtpof=true&sd=true) y se tomaron los tiempos de acuerdo al orden establecido, en la cual la unidad experimental que es el proceso de ensamblaje variaba por los factores.

![Figura 6: Diagrama del proceso.](https://github.com/PrettySusi/Experimento-DEAR/blob/main/Diagrama%20del%20proceso.jpeg?raw=true)

## ANÁLISIS EXPLORATORIO DE LOS DATOS

```{r include = FALSE}
url<-'https://raw.githubusercontent.com/PrettySusi/Experimento-DEAR/refs/heads/main/TIEMPOScsv.csv'
tiempos<- read.csv(url , sep = ";" , dec = ",", quote = "")

attach(tiempos)
```

```{r include = FALSE}
#LIBRERIAS
require(gplots)
require(graphics)
require(car)
require(nortest)
require(tseries)
require(lmtest)
require(rstatix)
require(ggplot2)
require(agricolae)
require(pwr)

```

```{r include = FALSE}
t<- as.numeric(tiempo)
ins<- as.factor(instrucciones)
ord<- as.factor(orden)
ru<- as.factor(ruido)
```

### BOXPLOTS COMPARATIVOS

```{r}
par(mfrow=c(1,3))
boxplot(tiempo ~ instrucciones, xlab="instrucciones", ylab="Tiempo", col= "ivory")
boxplot(tiempo ~ orden, xlab="Orden", ylab="Tiempo", col="ivory2")
boxplot(tiempo ~ ruido, xlab="Ruido", ylab="Tiempo", col= "ivory3")
```

##### Instrucciones

-   Imagen: Podemos observar que esta tiene un rango considerable entre el tiempo mínimo y el máximo, teniendo una diferencia aproximada de 72 segundos.

-   Texto: Para esta tenemos una muestra más compacta, ya que su tiempo máximo es aproximado de 92 segundos y el mínimo de 70 segundos, teniendo una diferencia de 22 segundos.

-   Video: Nivel que tiene la mayor diferencia entre el mínimo y máximo, ya que va desde los 18 segundos y alcanza los 101 segundos, teniendo una diferencia de 83 segundos, lo cual es significativo.

Analizando estos tres niveles podemos determinar que no hay una diferencia significativa entre ellos, lo cual no determinaria nuestra variable de respuesta.

##### Orden

-   Mezcladas: Observamos que tiene un rango moderado entre su mínimo y su máximo, donde son 70 segundos y 101 segundos respectivamente, teniendo una diferencia de 31 segundos.

-   Organizadas: Se tiene una diferencia normal entre su cuantil 1 y cuantil 3, obteniendo en el cuantil 1 60 segundos y el cuantil 3 de 95 segundos, con una diferencia de 35 segundos.

-   Preensambladas: Este nivel es el boxplot más compacto, donde tiene menores diferencias entre el mínimo y el máximo, logrando 18 segundos y 35 segundos respectivamente, teniendo una diferencia de 17 segundos. Además, se observa que hay outliers por encima del cuantil 3, indicando que algunas muestras aumentaron considerablemente el tiempo de ensamblaje.

Los niveles de mezclado y organizados tienen cierta similitud, indicando que no pueden describir el tiempo de ensamblaje. Sin embargo, el preensamblado muestra todo lo contrario, ya que disminuye considerablemente el tiempo de ensamblaje, lo que podría ser un factor influyente en la variable de respuesta.

##### Ruido

-   Alto: Tiene un rango amplio, indicando que hay gran dispersión de los datos, donde va desde los 10 segundos hasta los 90 segundos, teniendo una diferencia de 80 segundos.

-   Moderado: El mayor rango lo tiene este nivel, lo que indica una amplia dispersión de los datos, teniendo gran similitud con el nivel de ruido alto.

-   Silencio: Es el más compacto de los tres, pero aun así tiene tiempos similares a los dos niveles anteriores. Sin embargo, tiene outliers que están por debajo del cuantil 1, indicando que hay datos que tuvieron un mejor rendimiento.

Este factor, aunque tiene gran rango entre sus niveles, tiene similitudes que no podrían brindar información sobre el tiempo en el ensamblaje, exceptuando los outliers, en comparación con los otros factores.

### GRÁFICO DE MEDIAS

```{r}
par(mfrow=c(1,3))
plotmeans(tiempo~instrucciones, data=tiempos, xlab="Instrucciones", ylab="Tiempo")
plotmeans(tiempo ~ orden, data= tiempos, xlab="Orden", ylab="Tiempo")
plotmeans(tiempo ~ ruido, data= tiempos, xlab="Ruido", ylab="Tiempo")
```

*INSTRUCCIONES:* El nivel texto tiene el mayor tiempo promedio, aproximadamente 67 segundos, mientras que imagen y video tienen tiempos similares con 60 y 62 segundos, respectivamente. Las tres medias están tan cerca que es difícil tener una diferencia significativa. Además, la dispersión es alta en todos los niveles, mostrando que el ensamblaje tiene alta variabilidad en los tiempos.

*ORDEN:* Hay un patrón descendente. Mezclado tiene el mayor tiempo promedio, aproximadamente 81 segundos, seguido del nivel organizado con 75 segundos y finalmente preensamblado con 30 segundos. Mezclado y organizado tienen menor dispersión, y preensamblado tiene una dispersión muy reducida, lo que sugiere mayor consistencia en este nivel.

*RUIDO:* Los niveles alto y silencio tienen los tiempos promedio más altos, con 63 segundos y 66 segundos respectivamente, mientras que moderado es el nivel más bajo con 59 segundos. La dispersión en todos los niveles es similar, con barras de error largas que indican variabilidad considerable.

### GRÁFICO DE EFECTOS PRINCIPALES

```{r}
formula <- t ~ ins + ord + ru
plot.design(formula, col= "blue", xlab="Efectos", ylab="Promedio tiempo")

```

Entre los factores, el que presenta una mayor significancia es el orden, dado que tiene una mayor diferencia entre sus niveles. Las instrucciones y ruidos tienen menor variabilidad, lo que indicaría menor claridad para determinar si influyen en el tiempo de ensamblado.

### GRÁFICOS DE INTERACCIONES

```{r}
par(mfrow=c(2,3))

interaction.plot(ins, ord, t,
                 xlab="Instrucciones", ylab="Promedio de tiempo")

interaction.plot(ord, ins, t,
                 xlab="Orden", ylab="Promedio de tiempo")

interaction.plot(ru, ins, t,
                 xlab="Ruido", ylab="Promedio de tiempo")

interaction.plot(ins, ru, t,
                 xlab="Instrucciones", ylab="Promedio de tiempo")

interaction.plot(ord, ru, t,
                 xlab="Orden", ylab="Promedio de tiempo")

interaction.plot(ru, ord, t,
                 xlab="Ruido", ylab="Promedio de tiempo")

```

Realizando este análisis por pares puede notarse que hay presencia evidente de interacción en algunas gráficas, especialmente en las cuales el factor de ruido esta involucrado. Las demás gráficas dan a parecer que no hay interacción muy significativa debido a su comportamiento aislado o familiar entre las líneas, sin embargo es necesario realizar las pruebas estadísticas necesarias para validar estos supuestos.

## ANÁLISIS ESTADÍSTICO

Para validar los supuestos y seguir desarrollando este estudio, tiene sentido realizar pruebas estadísticas cuantitativas que aseguren la confiabilidad del experimento. A continuación, encontrará una serie de pruebas, las cuales tendrán su respectivo análisis, y se podrá concluir respecto al ejercicio planteado.

### MODELOS DE EFECTOS Y DE REGRESIÓN

El modelo de efectos en este caso permite descomponer y analizar cómo los factores y sus interacciones afectan el tiempo, en el caso del experimento. Esta compuesto de la siguiente manera:

*Y* ~𝑖𝑗𝑢𝑘~= *𝜇* + *𝜏* ~𝑖~ + *𝛽* ~𝑗~ + *𝛼* ~𝑢~ + *𝜏 𝛼 𝛽* ~𝑖𝑗𝑢~ + *𝜀* ~𝑖𝑗𝑢𝑘~, 𝑖 = 3, 𝑗 = 3 , 𝑢 = 3, 𝑘 = 3.

Donde la media global *𝜇* es:

```{r}
mean(t)
```

*𝜏* ~𝑖~, *𝛽* ~𝑗~, *𝛼* ~𝑢~ son las medias de los niveles de cada factor:

-   Instrucciones:

```{r}
tapply(t, ins, mean)

```

-   Orden:

```{r}
tapply(t, ord, mean)
```

-   Ruido:

```{r}
tapply(t, ru, mean)
```

*𝜏 𝛼 𝛽* ~𝑖𝑗𝑢~ corresponde a las interacciones entre los niveles de cada factor:

```{r}
tapply(t, ins:ord:ru, mean)
```

Y *𝜀* ~𝑖𝑗𝑢𝑘~ es un componente de error aleatorio para las 81 observaciones.

El modelo de regresión permitirá observar como afectan los factores instrucciones, orden de las piezas y ruido en el tiempo total de ensamblado. Este tiene en cuenta todas sus posibles interacciones:

Y = *𝛽* 0 + *𝛽* ~1~ X1 + *𝛽* ~2~ X2 + *𝛽*~3~ X3 + *𝛽* ~12~ X1X2 + *𝛽*~13~ X1X3 + *𝛽*~23~ X2X3 + *𝛽*~123~ X1X2X3 + *𝜀*

En R se observa de la siguiente manera:

```{r,echo = TRUE}
mre<- lm(t~ ins*ord*ru, data= tiempos)

```

El `summary(mre)` del modelo permite obtener una cantidad de datos iniciales que dan indicios de la efectividad de este para realizar predicciones. El R cuadrado y R cuadrado ajustado indican que la variabilidad del tiempo esta explicada por los factores a los que se enfrenta el operario en el momento de ensamble, este predice en un 96,08% el efecto de estos. Adicionalmente cada tipo de interacción entre los niveles afectará este. Las predicciones que se lleven a cabo pueden ser relevantes y el error estándar resulta pequeño, lo que le da más validez al modelo, el cual también resulta significativo.

```{r}
summary(mre)
```

### ANOVA

El análisis de varianza indica que las diferencias en las condiciones de ensamblado son significativas para cada uno de los factores, puntualmente puede observarse que el que más influye en el tiempo de ensamblado de forma individual es el orden en el que se organizan las piezas en la mesa. Conjuntamente, el tipo de instrucciones y el ruido reflejan un nivel alto de significancia.

```{r}
modelo <-  aov(t ~ ins*ord*ru, data=tiempos)
summary(modelo)

model1e <- model.tables(modelo,type='effects')
model1t <- model.tables(modelo,type='means')

ygorro <- fitted(modelo)

```

El nivel de significancia para el objetivo del estudio que es la influencia de los 3 factores propuestos también resulta efectivo y permite que se proceda con los demás estudios.

### VALIDACIÓN DEL MODELO

#### Normalidad

```{r, include= FALSE}
residuales <- rstandard(modelo)

```

```{r}
par(mfrow=c(1,3))
qqPlot(residuales, xlab="Cuantiles teoricos", ylab="Cuantiles muestrales", main="Gráfico cuantil-cuantil")
hist(residuales, xlab="Residuales", ylab="Frecuencia", main="Histograma", col= 'ivory3')
boxplot(residuales, xlab="Residuales",  main="Gráfico de cajas", col= 'ivory')
```

Visualmente los 3 gráficos nos muestran que el modelo está en condiciones ideales con respecto a la normalidad, todos los cuantiles están sobre las bandas dd confianza, el histograma y el boxplot no reflejan con exactitud normalidad pero pueden observarse indicios de esta. Desde la parte exploratoria no se rechaza la hipótesis de normalidad, y para válidar estos supuestos se realizarán las pruebas estadísticas necesarias.

```{r}
shapiro.test(residuales)
ad.test(residuales)
jarque.bera.test(residuales)
```

Se realizaron tres pruebas para observar si los residuales siguen normalidad:

-   La shapiro-Wilk nos da un valor-p de 0.47.

-   La Anderson-Darling tiene valor-p de 0.433.

-   La jarque-Bera tiene un valor de 0.38.

Todos los valores resultan por encima del nivel de significancia, indicando que no se rechaza la hipotesis nula, osea que el modelo sigue una distribucion normal.

#### Homocedasticidad

```{r}
valores_ajustados<-fitted(modelo)

plot(valores_ajustados, residuales, xlab="Valores ajustados", ylab="Residuales")
abline(h=0, col = "gray60")

```

Al no observarse un patrón entre los puntos que hay en la gráfica, puede haber presencia de homocedasticidad y para válidar está hipótesis se realizan pruebas numéricas:

```{r}
bptest(modelo)
leveneTest(modelo)
gqtest(modelo)
```

De la prueba de Breushch-Pagan se obtiene un valor con el que se rehazaría la hipótesis de que el modelo siguen varianza constante a diferencia de la gráfica, por lo que se realizaron 2 pruebas más para obtener una respuesta con más certeza. La Levene's y Goldfeld-Quandt resultan con valores de 0.97 y 0.93 respectivamente, ambas mayores al nivel de significncia, concluyendo que el modelo cumple com homocedasticidad.

#### Independencia

```{r}
dwtest(modelo,alternative="two.sided")
```

Por ultimo se realiza la prueba de Durbin-Watson para comprobar si los datos son indepedientes, donde efectivamente si son ya que el valor-p da un valor de 0.45, por tanto se acepta la hipotesis nula, los datos son indepenedientes entre sí.

De este análisis estadístico puede inferirse en su totalidad la factibilidad del experimento realizado. Permitiendo que a partir de este se hagan supuestos y se tomen desiciónes para optimizar el tiempo en la línea de ensamblaje, como lo es determinar que condiciones son más efectivas para que el operario sea más productivo. Esto puede determinarse mediante una comparativa entre los tratamientos, esta dará respuesta al interrogante ¿A partir de que condiciones es mmenor el tiempo de ensamblado?

### COMPARACIONES

#### Método LSD

Las siguientes pruebas evaluan el rendimiento de los niveles en cada factor:

```{r}
LSD.test(modelo, "ins", console=TRUE, group=FALSE)
```

Para el factor tipo de instrucciones puede observarse un mejor rendimiento en terminos de tiempo cuando las instrucciones son por imagenes. Por otro lado las que ralentizan del proceso son las intrucciones en formato textual, porlo que serían la última opción a implementar en el proceso de ensamblado.

```{r}
LSD.test(modelo, "ord", console=TRUE, group=FALSE)
```

El nivel que tiene mejor rendimiento en cuestión de orden de las fichas es cuando estas se encuentran previamente ensambladas, esto puede ser debido a que omite pasos que se realizan cuando el vehículo se arma desde cero. Por otro lado, como era de esperarse, la manera menos efectiva de respartir las fichas sobre la mesa es de forma mezclada. Estos resultados reflejan la importancia del orden de las cosas en la línea de ensamblaje.

```{r}
LSD.test(modelo, "ru", console=TRUE, group=FALSE)
```

Está comprobado que trabajar con música de fondo como en el experimento realizado, trae beneficios para mejorar la concentración, aumentar la productividad, reducir el etrés y mejorar el estado de ánimo. Estos supuestos pueden afirmarse para este experimento, ya que el ruido moderado obtuvo un mejor rendimiento. Mientras el silencio fue el que menor rendimiento tuvo, se considera que esto también depende de la persona, ya que cuando hay un ruído alto puede sentirse presionado, y en algunos casos puede aumentar la velocidad de ensamblado. Este factor varía mucho, pues también depende de la persona que realiza la operación y su forma de trabajar.

#### Método de Tukey (gráfico)

```{r}

par(mfrow=c(1,3))
plot(TukeyHSD(modelo, "ins"))
plot(TukeyHSD(modelo, "ord"))
plot(TukeyHSD(modelo, "ru"))

```

Aunque gráficamente es confuso, también puede concluirse lo anteriormente mencionado. Y en resumen, el operario registra un mejor tiempo cuando sigue las imagenes instructivas, las piezas están pre ensambladas y hay un ruido moderado.

Tener una alta potencia estadística aumenta la probabilidad de que lo previamente mencionado a lo largo de todo el trabajo sea verídico y aplicable, reduciendo la probabilidad de cometer un error tipo 2. Además es más probable que los efectos observados sean aplicables en la realidad y le den un significado al experimento.

```{r, include = FALSE}
HSD.test(modelo, "ins", group= FALSE, console= TRUE)
```

```{r, include=FALSE}
HSD.test(modelo, "ord", group= FALSE, console= TRUE)
```

```{r, include = FALSE}
HSD.test(modelo, "ru", group= FALSE, console= TRUE)
```

Para hallar esta potencia inicialmente se necesitan los siguientes parámetros, a los cuales les corresponde un valor en base al experimento:

-   n: hace referencia al número de réplicas, el cual es 3.

-   a: es el número de tratamientos, el cual le corresponde un valor de 27.

-   𝜎: Es la desviavión estandár, este dato se halló en el premuestreo, en el cual obtuvo un valor de 0.5970343.

-   D: La distancia mínima entre las medias. Estas se hallaron mediante la prueba de Tukey, se obtuvo la menor para cada factor y luego se promediaron. A esta le corresponde un valor de 3.098.

-   𝛼: Niel de significancia de 0.05.

Estos servirán para hallar el valor de Φ^2^ , el cual tiene un valor de:

```{r, include=FALSE}
Φ <- (3*(3.098)^2)/(2*27*(0.5970343)^2)
```

```{r}
Φ
```

De esta manera podrá realizarse la prueba necesaria para determinar la potencia con el número de réplicas utilizadas en el experimento:

```{r}
pwr.anova.test(f= sqrt(Φ), k = 27, n =3, sig.level = 0.05)
```

La potencia con un número de 3 réplicas en los 27 tratamientos resulta ser casi 1, esto significa que esta cantidad es suficiente para cumplir con los estandares que requiere el experimento para considerarse efectivo.

Al hallar el número de replicas que se debieron haber realizado para el experimento y obtener una potencia de 0.90 resulta ser innecesario, ya que previamente se obtuvo una mejor, al hacer este proceso el código arroja un error. Esto puede ser debido a la gran cantidad de tratamientos, pues entre más sean, en algunos casos las réplicas suelen ser más pocas.

## CONCLUSIONES

En el factor ruido, las condiciones de silencio y ruido moderado muestran tiempos similares y menores en comparación con el ruido alto. Aunque el ruido moderado tiene un ligero beneficio en promedio frente al silencio, esto podría estar relacionado con niveles de activación mental que optimizan la concentración del operario. El ruido alto, en cambio, afecta negativamente el desempeño, incrementando tanto el tiempo de ensamblaje como la posibilidad de errores. El silencio y el ruido moderado presentan condiciones óptimas para el ensamblaje, mientras que el ruido alto es el mayor obstáculo, provocando tiempos de ensamblaje más largos y una mayor dispersión en los datos.

Las instrucciones por imagenes resultan ser las más efectivas, mientras las instrucciones textuales presentan un mayor tiempo de ensamblaje, probablemente debido a la necesidad de decodificación adicional por parte del operario. El preensamblado reduce de manera significativa el tiempo total, seguido por el nivel organizadas por tipo, las piezas completamente desordenadas tienen el peor desempeño, aumentando tanto el tiempo como la dificultad de la tarea.

El análisis de interacciones sugiere que los efectos combinados de los factores pueden variar, con el ruido interactuando significativamente con los otros factores. Por ejemplo, el ruido alto amplifica los efectos negativos de las instrucciones textuales y de las piezas desordenadas. Este estudio confirma que el tiempo de ensamblaje puede optimizarse mediante ajustes en las condiciones de trabajo. Implementar instrucciones visuales, preensamblar piezas y controlar el ruido ambiental a niveles moderados son medidas recomendadas para mejorar la productividad en una línea de ensamblaje.


# Referencias

[@gplots] [@graphics] [@car] [@nortest] [@tseries] [@lmtest] [@rstatix] [@ggplot2] [@agricolae] [@pwr]
:::

