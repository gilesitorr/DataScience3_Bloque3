# Postwork 01: Identificación del Problema
## Identificación del problema
El tema de los __terremotos__ se puede estudiar desde diversas perspectivas. Es posible determinar las zonas del planeta con más sismos así como predecir la cantidad de sismos anuales en cada región. También se puede predecir la cantidad de sismos que habrá en próximos años. Esto puede ser de utilidad para elaborar planes de evacuación especializados en las zonas con mayor frecuencia de sismos así como de mayor magnitud. Sin embargo, según el Sistema Sismológico Nacional (de México) (s.f.), en la actualidad no hay una manera conocida en la actualidad  para predecir cuándo habrá un sismo, mucho menos su magnitud.,

_Fuentes:_
- Sistema Sismológico Nacional. (s.f.) Preguntas frecuentes. Recuperado el 28 de julio del 2021 de http://www.ssn.unam.mx/divulgacion/preguntas/.

## Planteamiento del Problema
Se busca estimar las regiones de riesgo sismológico (en base a la magnitud de los terremotos y su frecuencia). Esto es consecuencia de que no hay métodos actuales para predecir cuándo ocurrirá un sismo.

## Justificación
Las instituciones de protección civil no pueden verse limitadas por la imposibilidad actual para predecir terremotos, entonces la manera de realizar planes de prevención es identificar patrones estadísticos en base a las observaciones pasadas de terremotos.

## Marco teórico
De acuerdo a Wikipedia (s.f.), un terremoto (o sismo) es un fenómeno donde la corteza terrestre se sacude de manera brusca y pasajera al liberar energía en forma de ondas sísmicas. Estas ondas generalmente ocurren por la actividad de las fallas geológicas así como por el movimiento de las placas tectónicas, al igual que por procesos volcánicos o impactos de asteroides. El punto de origen de un terremoto se conoce como foco o hipocentro, mientras que el punto de la superficie que se encuentra sobre el hipocentro se conoce como epicentro.

Según el Sistema Sismológico Nacional (s.f.), se tienen diversas escalas para medir el tamaño o el impacto de  un temblor. La magnitud de un temblor está relacionada con la energía liberada en forma de  ondas sísmicas que se propagan a través del interior de la Tierra. Esta energía -que, a su vez, sirve para determinar la magnitud- se calcula a partir de algunas características de las ondas así como la distancia entre el epicentro y la estación de medición (los aparatos usados para esas mediciones se conocen como sismógrafos). La escala de magnitud se obtiene a partir de los registros obtenidos por sismógrafos.

_Fuentes_:
- Wikipedia. (s.f.). Terremoto. Recuperado el 28 de julio del 2021 de https://es.wikipedia.org/wiki/Terremoto#:~:text=Un%20terremoto%E2%80%8B%20(del%20latín,terrestre%20producida%20por%20la%20liberación.
- Sistema Sismológico Nacional. (s.f.) Preguntas frecuentes. Recuperado el 28 de julio del 2021 de http://www.ssn.unam.mx/divulgacion/preguntas/.

## Soluciones anteriores
Para dar contexto al proyecto actual, se discuten brevemente algunos proyectos que sirven como referencia.

Como se ve en el blog de Aaron Lee (2020), una de las maneras más comunes de graficar los sismos en un mapa es colocando un punto sobre la ubicación del epicentro. De la misma manera, si se desea detallar, se puede jugar con el tamaño y el color de los puntos para indicar su magnitud. Esta perspectiva sugiere fuertemente las zonas donde hay más sismos detectados incluso si se presentan pocos puntos. Sin embargo, cuando se tienen muchos puntos en un mismo mapa, se pierde la noción visual de la frecuencia de los sismos.

Al priorizar la noción de frecuencia, es necesario restar detalle a otros rasgos, como la magnitud del sismo. Esto puede sortearse dependiendo del interés de la investigación. Es decir, puede determinarse el rango de escalas a estudiar y, una vez seleccionados los registros de la base de datos que cumplen con ese criterio, se puede realizar un heatmap para presentar la información. El Government of Canada (s.f.) en su página oficial presenta unas gráficas que pueden servir de ejemplo (aunque presentan información que se relaciona con la frecuencia de los sismos pero también incorpora otras características al estudio).

La intención con el heatmap de las frecuencias en función de la ubicación es que, dada una serie de tiempo de la cantidad de sismos con la que se hagan predicciones, puede servir para predecir la cantidad de sismos en cada región para un año futuro. Esta puede ser una manera de darle la vuelta a la limitación de no poder predecir cuándo ocurrirá un sismo. Para un análisis similar pero con más detalles que lo propuesto, puede consultarse el trabajo de Kagan, Y. (2009).

_Fuentes_:
- Lee, A. (2020). Plotting USGS Earthquake Data with Folium. Recuperado el 29 de julio del 2021 de https://levelup.gitconnected.com/plotting-usgs-earthquake-data-with-folium-8f11ddc21950.
- Government of Canada. (s.f.). Simplified seismic hazard map for Canada, the provinces and territories. Recuperado el 29 de julio del 2021 de https://seismescanada.rncan.gc.ca/hazard-alea/simphaz-en.php.
- Kagan, Y. (2009). Testing long-term earthquake forecasts: Likelihood methods and error diagrams. Geophysical Journal International. 177. Recuperado el 30 de julio del 2021 de https://watermark.silverchair.com/177-2-532.pdf.
