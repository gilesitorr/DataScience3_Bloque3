{
  "nbformat": 4,
  "nbformat_minor": 0,
  "metadata": {
    "colab": {
      "name": "Proyecto.ipynb",
      "provenance": [],
      "include_colab_link": true
    },
    "kernelspec": {
      "name": "python3",
      "display_name": "Python 3"
    },
    "language_info": {
      "name": "python"
    }
  },
  "cells": [
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "view-in-github",
        "colab_type": "text"
      },
      "source": [
        "<a href=\"https://colab.research.google.com/github/gilesitorr/DataScience3_Bloque3/blob/main/Postwork_1/Readme.md\" target=\"_parent\"><img src=\"https://colab.research.google.com/assets/colab-badge.svg\" alt=\"Open In Colab\"/></a>"
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "uQZABV7FBD4L"
      },
      "source": [
        "# **BEDU: Data Science 3 (Santander Universidades)**\n",
        "# *Procesamiento de Datos con Python Santander 2021*"
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "RKMAVWaAChjG"
      },
      "source": [
        "\n",
        "## Los __Terremotos__ (NOMBRE TENTATIVO DEL PROYECTO xd)\n"
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "Lol6l1uQCddX"
      },
      "source": [
        "## Postwork 01: Identificación del Problema"
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "DNUMKCLhDohT"
      },
      "source": [
        "###Identificación del problema\n",
        "El tema de los __terremotos__ se puede estudiar desde diversas perspectivas. Es posible determinar las zonas del planeta con más sismos así como predecir la cantidad de sismos anuales en cada región. También se puede predecir la cantidad de sismos que habrá en próximos años. Esto puede ser de utilidad para elaborar planes de evacuación especializados en las zonas con mayor frecuencia de sismos así como de mayor magnitud. Sin embargo, según el Sistema Sismológico Nacional (de México) (s.f.), en la actualidad no hay una manera conocida en la actualidad  para predecir cuándo habrá un sismo, mucho menos su magnitud.\n",
        "\n",
        "_Fuentes:_\n",
        "- Sistema Sismológico Nacional. (s.f.) Preguntas frecuentes. Recuperado el 28 de julio del 2021 de http://www.ssn.unam.mx/divulgacion/preguntas/."
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "nDk5PzLple95"
      },
      "source": [
        "###Planteamiento del Problema\n",
        "Se busca estimar las regiones de riesgo sismológico (en base a la magnitud de los terremotos y su frecuencia). Esto es consecuencia de que no hay métodos actuales para predecir cuándo ocurrirá un sismo."
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "YqlftGfilmXL"
      },
      "source": [
        "### Justificación\n",
        "Las instituciones de protección civil no pueden verse limitadas por la imposibilidad actual para predecir terremotos, entonces la manera de realizar planes de prevención es identificar patrones estadísticos en base a las observaciones pasadas de terremotos."
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "wT_gunwRlqVF"
      },
      "source": [
        "### Marco teórico\n",
        "De acuerdo a Wikipedia (s.f.), un terremoto (o sismo) es un fenómeno donde la corteza terrestre se sacude de manera brusca y pasajera al liberar energía en forma de ondas sísmicas. Estas ondas generalmente ocurren por la actividad de las fallas geológicas así como por el movimiento de las placas tectónicas, al igual que por procesos volcánicos o impactos de asteroides. El punto de origen de un terremoto se conoce como foco o hipocentro, mientras que el punto de la superficie que se encuentra sobre el hipocentro se conoce como epicentro.\n",
        "\n",
        "Según el Sistema Sismológico Nacional (s.f.), se tienen diversas escalas para medir el tamaño o el impacto de  un temblor. La magnitud de un temblor está relacionada con la energía liberada en forma de  ondas sísmicas que se propagan a través del interior de la Tierra. Esta energía -que, a su vez, sirve para determinar la magnitud- se calcula a partir de algunas características de las ondas así como la distancia entre el epicentro y la estación de medición (los aparatos usados para esas mediciones se conocen como sismógrafos). La escala de magnitud se obtiene a partir de los registros obtenidos por sismógrafos.\n",
        "\n",
        "_Fuentes_:\n",
        "- Wikipedia. (s.f.). Terremoto. Recuperado el 28 de julio del 2021 de https://es.wikipedia.org/wiki/Terremoto#:~:text=Un%20terremoto%E2%80%8B%20(del%20latín,terrestre%20producida%20por%20la%20liberación.\n",
        "- Sistema Sismológico Nacional. (s.f.) Preguntas frecuentes. Recuperado el 28 de julio del 2021 de http://www.ssn.unam.mx/divulgacion/preguntas/."
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "6U16paqiZ7jL"
      },
      "source": [
        "###Soluciones anteriores\n",
        "Para dar contexto al proyecto actual, se discuten brevemente algunos proyectos que sirven como referencia.\n",
        "\n",
        "Como se ve en el blog de Aaron Lee (2020), una de las maneras más comunes de graficar los sismos en un mapa es colocando un punto sobre la ubicación del epicentro. De la misma manera, si se desea detallar, se puede jugar con el tamaño y el color de los puntos para indicar su magnitud. Esta perspectiva sugiere fuertemente las zonas donde hay más sismos detectados incluso si se presentan pocos puntos. Sin embargo, cuando se tienen muchos puntos en un mismo mapa, se pierde la noción visual de la frecuencia de los sismos.\n",
        "\n",
        "Al priorizar la noción de frecuencia, es necesario restar detalle a otros rasgos, como la magnitud del sismo. Esto puede sortearse dependiendo del interés de la investigación. Es decir, puede determinarse el rango de escalas a estudiar y, una vez seleccionados los registros de la base de datos que cumplen con ese criterio, se puede realizar un heatmap para presentar la información. El Government of Canada (s.f.) en su página oficial presenta unas gráficas que pueden servir de ejemplo (aunque presentan información que se relaciona con la frecuencia de los sismos pero también incorpora otras características al estudio).\n",
        "\n",
        "La intención con el heatmap de las frecuencias en función de la ubicación es que, dada una serie de tiempo de la cantidad de sismos con la que se hagan predicciones, puede servir para predecir la cantidad de sismos en cada región para un año futuro. Esta puede ser una manera de darle la vuelta a la limitación de no poder predecir cuándo ocurrirá un sismo. Para un análisis similar pero con más detalles que lo propuesto, puede consultarse el trabajo de Kagan, Y. (2009).\n",
        "\n",
        "_Fuentes_:\n",
        "- Lee, A. (2020). Plotting USGS Earthquake Data with Folium. Recuperado el 29 de julio del 2021 de https://levelup.gitconnected.com/plotting-usgs-earthquake-data-with-folium-8f11ddc21950.\n",
        "- Government of Canada. (s.f.). Simplified seismic hazard map for Canada, the provinces and territories. Recuperado el 29 de julio del 2021 de https://seismescanada.rncan.gc.ca/hazard-alea/simphaz-en.php.\n",
        "- Kagan, Y. (2009). Testing long-term earthquake forecasts: Likelihood methods and error diagrams. Geophysical Journal International. 177. Recuperado el 30 de julio del 2021 de https://watermark.silverchair.com/177-2-532.pdf. "
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "An7_1KigFNfd"
      },
      "source": [
        "##Postwork 02: Planteamiento de Preguntas"
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "Q4NuYKCOFd4y"
      },
      "source": [
        "### El problema\n",
        "Se busca estimar las regiones de riesgo sismológico (en base a la magnitud de los terremotos y su frecuencia). Esto es consecuencia de que no hay métodos actuales para predecir cuándo ocurrirá un sismo, pero las instituciones de protección civil no pueden verse limitadas por eso, entonces la manera de realizar planes de prevención es identificar patrones estadísticos en base a las observaciones pasadas de terremotos.\n",
        "\n",
        "El primer objetivo que se identifica es determinar las zonas con más sismos anuales (que, a priori, parece una buena unidad temporal para el análisis) así como las zonas con sismos más “fuertes”. El segundo objetivo es predecir la cantidad de sismos extrapolando la información histórica de los sismos.\n",
        "\n",
        "\n"
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "67OIRXKKa7Gg"
      },
      "source": [
        "###Planteamiento de preguntas\n",
        "En base a los objetivos que se plantearon y a la investigación, se pueden determinar algunas preguntas guía.\n",
        "\n",
        "_Preguntas generales_:\n",
        "1. ¿Cuántos sismos hay anualmente?\n",
        "2. ¿Cuáles son las regiones donde hay sismos más frecuentemente?\n",
        "3. ¿Cuáles son las regiones con más sismos “fuertes” (en términos de magnitud)?\n",
        "\n",
        "_Preguntas de profundización del tema_:\n",
        "1. ¿Cuántos sismos habrá en los próximos años?\n",
        "2. ¿Hay una relación entre la magnitud o la profundidad de los sismos y su región?\n",
        "\n",
        "_Pregunta específica_:\n",
        "1. ¿Cuántos sismos habrá en México en el 2022?\n"
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "ZKe7DMTrQ-zZ"
      },
      "source": [
        "##Postwork 03: Colección de Datos"
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "9dw8ZUGfRJE6"
      },
      "source": [
        "Con el objetivo de abordar la problemática, se buscó un dataset pertinente. De __Kaggle__ se obtuvo el dataset titulado [___Significant Earthquakes, 1965-2016___](https://www.kaggle.com/usgs/earthquake-database), proporcionado por el Servicio Geológico de los Estados Unidos. \n",
        "\n",
        "El dataset contiene 21 columnas, entre las cuales se encuentran la fecha, hora, localización y magnitud de sismos reportados a nivel mundial con magnitudes mayores a 5.5 desde 1965 hasta 2016.\n"
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "Q7aGEu3YUTx3"
      },
      "source": [
        "## Postwork 04: Análisis Exploratorio de nuestro Dataset\n",
        "\n"
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "N51O0Vy-dwzj"
      },
      "source": [
        "A continuación se presentan algunas preguntas y su respectiva respuesta (para quien no desee adentrarse demasiado en el código, pero todas las respuestas se justifican abajo):\n",
        "\n",
        "1. __¿El conjunto de datos que tengo realmente me sirve para responder algunas de las preguntas que me planteé?__ Sí, pues cuenta con una columna de fecha, otras con longitudes y latitudes (para poder tener idea de la localización geográfica) así como una columna de magnitudes.\n",
        "\n",
        "2. __¿Qué tamaño tiene mi conjunto de datos? ¿Serán datos suficientes?__ El dataset completo tiene una dimensión de 23,412 registros y 21 columnas. Considerando que las columnas que son de interés están completas, se puede ver que son datos suficientes.\n",
        "\n",
        "3. __¿Qué columnas tengo y qué información tengo en cada una de esas columnas?__ Las columnas relevantes son _Date_ (fecha del evento), _Latitude_ (latitud), _Longitud_ (longitud), _Type_ (si el temblor detectado es un terremoto o fue causado por algún otro tipo de evento), _Magnitude_ (magnitud del sismo), _Magnitude Type_ (qué sistema para determinar la magnitud se usó) y _Depth_(la profundidad del hipocentro).\n",
        "\n",
        "4. __Los nombres que tienen mis columnas, ¿son el nombre más apropiado?__ Sí, entre los nombres y los datos, es sencillo comprender la base de datos.\n",
        "\n",
        "5. __¿Qué tipos de datos tengo en cada columna? ¿Parecen ser el tipo correcto de datos? ¿O es un tipo de datos \"incorrecto\"?__ _Date_ tiene formato de string, entonces será oportuno cambiar el formato a fecha. _Latitude_, _Longitud_, _Magnitude_ y _Depth_ tienen formato de float, que es apropiado. Tanto _Type_ como _Magnitude Type_ tienen formato de string, que tiene sentido, sin embargo, _Type_ puede usarse para un filtro para sólo analizar terremotos.\n",
        "\n",
        "6. __Si selecciono algunas filas al azar y las observo, ¿estoy obteniendo los datos que debería? ¿O hay datos que parecen estar \"sucios\" o \"incorrectos\"?__ Hay muchos NaNs, pero no en las columnas que son interesantes. Las columnas irrelevantes se quitarán para el análisis posterior."
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "d91AQ3KTo6Ag"
      },
      "source": [
        "Primero se lee el dataframe, en este caso, se lee desde GitHub, pues se cargó previamente al repositorio. (Para ver cómo usarlo sin descargarlo, puede consultar el __Postwork 6__)."
      ]
    },
    {
      "cell_type": "code",
      "metadata": {
        "id": "UrnB_cV_V4-c"
      },
      "source": [
        "import pandas as pd"
      ],
      "execution_count": 16,
      "outputs": []
    },
    {
      "cell_type": "code",
      "metadata": {
        "id": "95Bt2OhS0UsG"
      },
      "source": [
        "#Se toma el dataset desde el repositorio de github (desde el raw)\n",
        "url = \"https://raw.githubusercontent.com/gilesitorr/DataScience3_Bloque3/main/Postwork_3/database.csv\"\n",
        "df = pd.read_csv(url)"
      ],
      "execution_count": 17,
      "outputs": []
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "XwNZYVU7piyi"
      },
      "source": [
        "Puede notarse que el dataset cuenta con una columna de fechas, de magnitudes así como de latitud y longitud. Por lo tanto, es útil para responder las preguntas que se plantearon."
      ]
    },
    {
      "cell_type": "code",
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 470
        },
        "id": "BVfQPuXZ3CNS",
        "outputId": "afab9139-d815-40b3-8dc9-8e6a0ac5e454"
      },
      "source": [
        "df"
      ],
      "execution_count": 18,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "text/html": [
              "<div>\n",
              "<style scoped>\n",
              "    .dataframe tbody tr th:only-of-type {\n",
              "        vertical-align: middle;\n",
              "    }\n",
              "\n",
              "    .dataframe tbody tr th {\n",
              "        vertical-align: top;\n",
              "    }\n",
              "\n",
              "    .dataframe thead th {\n",
              "        text-align: right;\n",
              "    }\n",
              "</style>\n",
              "<table border=\"1\" class=\"dataframe\">\n",
              "  <thead>\n",
              "    <tr style=\"text-align: right;\">\n",
              "      <th></th>\n",
              "      <th>Date</th>\n",
              "      <th>Time</th>\n",
              "      <th>Latitude</th>\n",
              "      <th>Longitude</th>\n",
              "      <th>Type</th>\n",
              "      <th>Depth</th>\n",
              "      <th>Depth Error</th>\n",
              "      <th>Depth Seismic Stations</th>\n",
              "      <th>Magnitude</th>\n",
              "      <th>Magnitude Type</th>\n",
              "      <th>Magnitude Error</th>\n",
              "      <th>Magnitude Seismic Stations</th>\n",
              "      <th>Azimuthal Gap</th>\n",
              "      <th>Horizontal Distance</th>\n",
              "      <th>Horizontal Error</th>\n",
              "      <th>Root Mean Square</th>\n",
              "      <th>ID</th>\n",
              "      <th>Source</th>\n",
              "      <th>Location Source</th>\n",
              "      <th>Magnitude Source</th>\n",
              "      <th>Status</th>\n",
              "    </tr>\n",
              "  </thead>\n",
              "  <tbody>\n",
              "    <tr>\n",
              "      <th>0</th>\n",
              "      <td>01/02/1965</td>\n",
              "      <td>13:44:18</td>\n",
              "      <td>19.2460</td>\n",
              "      <td>145.6160</td>\n",
              "      <td>Earthquake</td>\n",
              "      <td>131.60</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>6.0</td>\n",
              "      <td>MW</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>ISCGEM860706</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>Automatic</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>1</th>\n",
              "      <td>01/04/1965</td>\n",
              "      <td>11:29:49</td>\n",
              "      <td>1.8630</td>\n",
              "      <td>127.3520</td>\n",
              "      <td>Earthquake</td>\n",
              "      <td>80.00</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>5.8</td>\n",
              "      <td>MW</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>ISCGEM860737</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>Automatic</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>2</th>\n",
              "      <td>01/05/1965</td>\n",
              "      <td>18:05:58</td>\n",
              "      <td>-20.5790</td>\n",
              "      <td>-173.9720</td>\n",
              "      <td>Earthquake</td>\n",
              "      <td>20.00</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>6.2</td>\n",
              "      <td>MW</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>ISCGEM860762</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>Automatic</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>3</th>\n",
              "      <td>01/08/1965</td>\n",
              "      <td>18:49:43</td>\n",
              "      <td>-59.0760</td>\n",
              "      <td>-23.5570</td>\n",
              "      <td>Earthquake</td>\n",
              "      <td>15.00</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>5.8</td>\n",
              "      <td>MW</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>ISCGEM860856</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>Automatic</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>4</th>\n",
              "      <td>01/09/1965</td>\n",
              "      <td>13:32:50</td>\n",
              "      <td>11.9380</td>\n",
              "      <td>126.4270</td>\n",
              "      <td>Earthquake</td>\n",
              "      <td>15.00</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>5.8</td>\n",
              "      <td>MW</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>ISCGEM860890</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>Automatic</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>...</th>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>23407</th>\n",
              "      <td>12/28/2016</td>\n",
              "      <td>08:22:12</td>\n",
              "      <td>38.3917</td>\n",
              "      <td>-118.8941</td>\n",
              "      <td>Earthquake</td>\n",
              "      <td>12.30</td>\n",
              "      <td>1.2</td>\n",
              "      <td>40.0</td>\n",
              "      <td>5.6</td>\n",
              "      <td>ML</td>\n",
              "      <td>0.320</td>\n",
              "      <td>18.0</td>\n",
              "      <td>42.47</td>\n",
              "      <td>0.120</td>\n",
              "      <td>NaN</td>\n",
              "      <td>0.1898</td>\n",
              "      <td>NN00570710</td>\n",
              "      <td>NN</td>\n",
              "      <td>NN</td>\n",
              "      <td>NN</td>\n",
              "      <td>Reviewed</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>23408</th>\n",
              "      <td>12/28/2016</td>\n",
              "      <td>09:13:47</td>\n",
              "      <td>38.3777</td>\n",
              "      <td>-118.8957</td>\n",
              "      <td>Earthquake</td>\n",
              "      <td>8.80</td>\n",
              "      <td>2.0</td>\n",
              "      <td>33.0</td>\n",
              "      <td>5.5</td>\n",
              "      <td>ML</td>\n",
              "      <td>0.260</td>\n",
              "      <td>18.0</td>\n",
              "      <td>48.58</td>\n",
              "      <td>0.129</td>\n",
              "      <td>NaN</td>\n",
              "      <td>0.2187</td>\n",
              "      <td>NN00570744</td>\n",
              "      <td>NN</td>\n",
              "      <td>NN</td>\n",
              "      <td>NN</td>\n",
              "      <td>Reviewed</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>23409</th>\n",
              "      <td>12/28/2016</td>\n",
              "      <td>12:38:51</td>\n",
              "      <td>36.9179</td>\n",
              "      <td>140.4262</td>\n",
              "      <td>Earthquake</td>\n",
              "      <td>10.00</td>\n",
              "      <td>1.8</td>\n",
              "      <td>NaN</td>\n",
              "      <td>5.9</td>\n",
              "      <td>MWW</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>91.00</td>\n",
              "      <td>0.992</td>\n",
              "      <td>4.8</td>\n",
              "      <td>1.5200</td>\n",
              "      <td>US10007NAF</td>\n",
              "      <td>US</td>\n",
              "      <td>US</td>\n",
              "      <td>US</td>\n",
              "      <td>Reviewed</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>23410</th>\n",
              "      <td>12/29/2016</td>\n",
              "      <td>22:30:19</td>\n",
              "      <td>-9.0283</td>\n",
              "      <td>118.6639</td>\n",
              "      <td>Earthquake</td>\n",
              "      <td>79.00</td>\n",
              "      <td>1.8</td>\n",
              "      <td>NaN</td>\n",
              "      <td>6.3</td>\n",
              "      <td>MWW</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>26.00</td>\n",
              "      <td>3.553</td>\n",
              "      <td>6.0</td>\n",
              "      <td>1.4300</td>\n",
              "      <td>US10007NL0</td>\n",
              "      <td>US</td>\n",
              "      <td>US</td>\n",
              "      <td>US</td>\n",
              "      <td>Reviewed</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>23411</th>\n",
              "      <td>12/30/2016</td>\n",
              "      <td>20:08:28</td>\n",
              "      <td>37.3973</td>\n",
              "      <td>141.4103</td>\n",
              "      <td>Earthquake</td>\n",
              "      <td>11.94</td>\n",
              "      <td>2.2</td>\n",
              "      <td>NaN</td>\n",
              "      <td>5.5</td>\n",
              "      <td>MB</td>\n",
              "      <td>0.029</td>\n",
              "      <td>428.0</td>\n",
              "      <td>97.00</td>\n",
              "      <td>0.681</td>\n",
              "      <td>4.5</td>\n",
              "      <td>0.9100</td>\n",
              "      <td>US10007NTD</td>\n",
              "      <td>US</td>\n",
              "      <td>US</td>\n",
              "      <td>US</td>\n",
              "      <td>Reviewed</td>\n",
              "    </tr>\n",
              "  </tbody>\n",
              "</table>\n",
              "<p>23412 rows × 21 columns</p>\n",
              "</div>"
            ],
            "text/plain": [
              "             Date      Time  ...  Magnitude Source     Status\n",
              "0      01/02/1965  13:44:18  ...            ISCGEM  Automatic\n",
              "1      01/04/1965  11:29:49  ...            ISCGEM  Automatic\n",
              "2      01/05/1965  18:05:58  ...            ISCGEM  Automatic\n",
              "3      01/08/1965  18:49:43  ...            ISCGEM  Automatic\n",
              "4      01/09/1965  13:32:50  ...            ISCGEM  Automatic\n",
              "...           ...       ...  ...               ...        ...\n",
              "23407  12/28/2016  08:22:12  ...                NN   Reviewed\n",
              "23408  12/28/2016  09:13:47  ...                NN   Reviewed\n",
              "23409  12/28/2016  12:38:51  ...                US   Reviewed\n",
              "23410  12/29/2016  22:30:19  ...                US   Reviewed\n",
              "23411  12/30/2016  20:08:28  ...                US   Reviewed\n",
              "\n",
              "[23412 rows x 21 columns]"
            ]
          },
          "metadata": {
            "tags": []
          },
          "execution_count": 18
        }
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "cEg4JVQ9pL_T"
      },
      "source": [
        "El tamaño del dataset"
      ]
    },
    {
      "cell_type": "code",
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "M-PHrQME3hqE",
        "outputId": "061ceba6-9064-4b59-96d9-e48c44f99643"
      },
      "source": [
        " df.shape"
      ],
      "execution_count": 19,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "text/plain": [
              "(23412, 21)"
            ]
          },
          "metadata": {
            "tags": []
          },
          "execution_count": 19
        }
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "9c12SB57qa72"
      },
      "source": [
        "Para saber más"
      ]
    },
    {
      "cell_type": "code",
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 257
        },
        "id": "Yeu1bb9-451C",
        "outputId": "f590b0c7-7a83-4837-f12d-9e3061e58618"
      },
      "source": [
        "df.head(5)"
      ],
      "execution_count": 20,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "text/html": [
              "<div>\n",
              "<style scoped>\n",
              "    .dataframe tbody tr th:only-of-type {\n",
              "        vertical-align: middle;\n",
              "    }\n",
              "\n",
              "    .dataframe tbody tr th {\n",
              "        vertical-align: top;\n",
              "    }\n",
              "\n",
              "    .dataframe thead th {\n",
              "        text-align: right;\n",
              "    }\n",
              "</style>\n",
              "<table border=\"1\" class=\"dataframe\">\n",
              "  <thead>\n",
              "    <tr style=\"text-align: right;\">\n",
              "      <th></th>\n",
              "      <th>Date</th>\n",
              "      <th>Time</th>\n",
              "      <th>Latitude</th>\n",
              "      <th>Longitude</th>\n",
              "      <th>Type</th>\n",
              "      <th>Depth</th>\n",
              "      <th>Depth Error</th>\n",
              "      <th>Depth Seismic Stations</th>\n",
              "      <th>Magnitude</th>\n",
              "      <th>Magnitude Type</th>\n",
              "      <th>Magnitude Error</th>\n",
              "      <th>Magnitude Seismic Stations</th>\n",
              "      <th>Azimuthal Gap</th>\n",
              "      <th>Horizontal Distance</th>\n",
              "      <th>Horizontal Error</th>\n",
              "      <th>Root Mean Square</th>\n",
              "      <th>ID</th>\n",
              "      <th>Source</th>\n",
              "      <th>Location Source</th>\n",
              "      <th>Magnitude Source</th>\n",
              "      <th>Status</th>\n",
              "    </tr>\n",
              "  </thead>\n",
              "  <tbody>\n",
              "    <tr>\n",
              "      <th>0</th>\n",
              "      <td>01/02/1965</td>\n",
              "      <td>13:44:18</td>\n",
              "      <td>19.246</td>\n",
              "      <td>145.616</td>\n",
              "      <td>Earthquake</td>\n",
              "      <td>131.6</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>6.0</td>\n",
              "      <td>MW</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>ISCGEM860706</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>Automatic</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>1</th>\n",
              "      <td>01/04/1965</td>\n",
              "      <td>11:29:49</td>\n",
              "      <td>1.863</td>\n",
              "      <td>127.352</td>\n",
              "      <td>Earthquake</td>\n",
              "      <td>80.0</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>5.8</td>\n",
              "      <td>MW</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>ISCGEM860737</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>Automatic</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>2</th>\n",
              "      <td>01/05/1965</td>\n",
              "      <td>18:05:58</td>\n",
              "      <td>-20.579</td>\n",
              "      <td>-173.972</td>\n",
              "      <td>Earthquake</td>\n",
              "      <td>20.0</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>6.2</td>\n",
              "      <td>MW</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>ISCGEM860762</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>Automatic</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>3</th>\n",
              "      <td>01/08/1965</td>\n",
              "      <td>18:49:43</td>\n",
              "      <td>-59.076</td>\n",
              "      <td>-23.557</td>\n",
              "      <td>Earthquake</td>\n",
              "      <td>15.0</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>5.8</td>\n",
              "      <td>MW</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>ISCGEM860856</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>Automatic</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>4</th>\n",
              "      <td>01/09/1965</td>\n",
              "      <td>13:32:50</td>\n",
              "      <td>11.938</td>\n",
              "      <td>126.427</td>\n",
              "      <td>Earthquake</td>\n",
              "      <td>15.0</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>5.8</td>\n",
              "      <td>MW</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>ISCGEM860890</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>Automatic</td>\n",
              "    </tr>\n",
              "  </tbody>\n",
              "</table>\n",
              "</div>"
            ],
            "text/plain": [
              "         Date      Time  Latitude  ...  Location Source Magnitude Source     Status\n",
              "0  01/02/1965  13:44:18    19.246  ...           ISCGEM           ISCGEM  Automatic\n",
              "1  01/04/1965  11:29:49     1.863  ...           ISCGEM           ISCGEM  Automatic\n",
              "2  01/05/1965  18:05:58   -20.579  ...           ISCGEM           ISCGEM  Automatic\n",
              "3  01/08/1965  18:49:43   -59.076  ...           ISCGEM           ISCGEM  Automatic\n",
              "4  01/09/1965  13:32:50    11.938  ...           ISCGEM           ISCGEM  Automatic\n",
              "\n",
              "[5 rows x 21 columns]"
            ]
          },
          "metadata": {
            "tags": []
          },
          "execution_count": 20
        }
      ]
    },
    {
      "cell_type": "code",
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 257
        },
        "id": "pq7RGrTF5Asb",
        "outputId": "5477e772-8b1d-4364-e27e-f2ab5ed5685f"
      },
      "source": [
        "df.tail(5)"
      ],
      "execution_count": 21,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "text/html": [
              "<div>\n",
              "<style scoped>\n",
              "    .dataframe tbody tr th:only-of-type {\n",
              "        vertical-align: middle;\n",
              "    }\n",
              "\n",
              "    .dataframe tbody tr th {\n",
              "        vertical-align: top;\n",
              "    }\n",
              "\n",
              "    .dataframe thead th {\n",
              "        text-align: right;\n",
              "    }\n",
              "</style>\n",
              "<table border=\"1\" class=\"dataframe\">\n",
              "  <thead>\n",
              "    <tr style=\"text-align: right;\">\n",
              "      <th></th>\n",
              "      <th>Date</th>\n",
              "      <th>Time</th>\n",
              "      <th>Latitude</th>\n",
              "      <th>Longitude</th>\n",
              "      <th>Type</th>\n",
              "      <th>Depth</th>\n",
              "      <th>Depth Error</th>\n",
              "      <th>Depth Seismic Stations</th>\n",
              "      <th>Magnitude</th>\n",
              "      <th>Magnitude Type</th>\n",
              "      <th>Magnitude Error</th>\n",
              "      <th>Magnitude Seismic Stations</th>\n",
              "      <th>Azimuthal Gap</th>\n",
              "      <th>Horizontal Distance</th>\n",
              "      <th>Horizontal Error</th>\n",
              "      <th>Root Mean Square</th>\n",
              "      <th>ID</th>\n",
              "      <th>Source</th>\n",
              "      <th>Location Source</th>\n",
              "      <th>Magnitude Source</th>\n",
              "      <th>Status</th>\n",
              "    </tr>\n",
              "  </thead>\n",
              "  <tbody>\n",
              "    <tr>\n",
              "      <th>23407</th>\n",
              "      <td>12/28/2016</td>\n",
              "      <td>08:22:12</td>\n",
              "      <td>38.3917</td>\n",
              "      <td>-118.8941</td>\n",
              "      <td>Earthquake</td>\n",
              "      <td>12.30</td>\n",
              "      <td>1.2</td>\n",
              "      <td>40.0</td>\n",
              "      <td>5.6</td>\n",
              "      <td>ML</td>\n",
              "      <td>0.320</td>\n",
              "      <td>18.0</td>\n",
              "      <td>42.47</td>\n",
              "      <td>0.120</td>\n",
              "      <td>NaN</td>\n",
              "      <td>0.1898</td>\n",
              "      <td>NN00570710</td>\n",
              "      <td>NN</td>\n",
              "      <td>NN</td>\n",
              "      <td>NN</td>\n",
              "      <td>Reviewed</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>23408</th>\n",
              "      <td>12/28/2016</td>\n",
              "      <td>09:13:47</td>\n",
              "      <td>38.3777</td>\n",
              "      <td>-118.8957</td>\n",
              "      <td>Earthquake</td>\n",
              "      <td>8.80</td>\n",
              "      <td>2.0</td>\n",
              "      <td>33.0</td>\n",
              "      <td>5.5</td>\n",
              "      <td>ML</td>\n",
              "      <td>0.260</td>\n",
              "      <td>18.0</td>\n",
              "      <td>48.58</td>\n",
              "      <td>0.129</td>\n",
              "      <td>NaN</td>\n",
              "      <td>0.2187</td>\n",
              "      <td>NN00570744</td>\n",
              "      <td>NN</td>\n",
              "      <td>NN</td>\n",
              "      <td>NN</td>\n",
              "      <td>Reviewed</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>23409</th>\n",
              "      <td>12/28/2016</td>\n",
              "      <td>12:38:51</td>\n",
              "      <td>36.9179</td>\n",
              "      <td>140.4262</td>\n",
              "      <td>Earthquake</td>\n",
              "      <td>10.00</td>\n",
              "      <td>1.8</td>\n",
              "      <td>NaN</td>\n",
              "      <td>5.9</td>\n",
              "      <td>MWW</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>91.00</td>\n",
              "      <td>0.992</td>\n",
              "      <td>4.8</td>\n",
              "      <td>1.5200</td>\n",
              "      <td>US10007NAF</td>\n",
              "      <td>US</td>\n",
              "      <td>US</td>\n",
              "      <td>US</td>\n",
              "      <td>Reviewed</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>23410</th>\n",
              "      <td>12/29/2016</td>\n",
              "      <td>22:30:19</td>\n",
              "      <td>-9.0283</td>\n",
              "      <td>118.6639</td>\n",
              "      <td>Earthquake</td>\n",
              "      <td>79.00</td>\n",
              "      <td>1.8</td>\n",
              "      <td>NaN</td>\n",
              "      <td>6.3</td>\n",
              "      <td>MWW</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>26.00</td>\n",
              "      <td>3.553</td>\n",
              "      <td>6.0</td>\n",
              "      <td>1.4300</td>\n",
              "      <td>US10007NL0</td>\n",
              "      <td>US</td>\n",
              "      <td>US</td>\n",
              "      <td>US</td>\n",
              "      <td>Reviewed</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>23411</th>\n",
              "      <td>12/30/2016</td>\n",
              "      <td>20:08:28</td>\n",
              "      <td>37.3973</td>\n",
              "      <td>141.4103</td>\n",
              "      <td>Earthquake</td>\n",
              "      <td>11.94</td>\n",
              "      <td>2.2</td>\n",
              "      <td>NaN</td>\n",
              "      <td>5.5</td>\n",
              "      <td>MB</td>\n",
              "      <td>0.029</td>\n",
              "      <td>428.0</td>\n",
              "      <td>97.00</td>\n",
              "      <td>0.681</td>\n",
              "      <td>4.5</td>\n",
              "      <td>0.9100</td>\n",
              "      <td>US10007NTD</td>\n",
              "      <td>US</td>\n",
              "      <td>US</td>\n",
              "      <td>US</td>\n",
              "      <td>Reviewed</td>\n",
              "    </tr>\n",
              "  </tbody>\n",
              "</table>\n",
              "</div>"
            ],
            "text/plain": [
              "             Date      Time  ...  Magnitude Source    Status\n",
              "23407  12/28/2016  08:22:12  ...                NN  Reviewed\n",
              "23408  12/28/2016  09:13:47  ...                NN  Reviewed\n",
              "23409  12/28/2016  12:38:51  ...                US  Reviewed\n",
              "23410  12/29/2016  22:30:19  ...                US  Reviewed\n",
              "23411  12/30/2016  20:08:28  ...                US  Reviewed\n",
              "\n",
              "[5 rows x 21 columns]"
            ]
          },
          "metadata": {
            "tags": []
          },
          "execution_count": 21
        }
      ]
    },
    {
      "cell_type": "code",
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "9ETNu5T35Y9i",
        "outputId": "b8fe3f46-ddb9-47ad-dd8c-1b105409c31b"
      },
      "source": [
        "df.dtypes"
      ],
      "execution_count": 22,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "text/plain": [
              "Date                           object\n",
              "Time                           object\n",
              "Latitude                      float64\n",
              "Longitude                     float64\n",
              "Type                           object\n",
              "Depth                         float64\n",
              "Depth Error                   float64\n",
              "Depth Seismic Stations        float64\n",
              "Magnitude                     float64\n",
              "Magnitude Type                 object\n",
              "Magnitude Error               float64\n",
              "Magnitude Seismic Stations    float64\n",
              "Azimuthal Gap                 float64\n",
              "Horizontal Distance           float64\n",
              "Horizontal Error              float64\n",
              "Root Mean Square              float64\n",
              "ID                             object\n",
              "Source                         object\n",
              "Location Source                object\n",
              "Magnitude Source               object\n",
              "Status                         object\n",
              "dtype: object"
            ]
          },
          "metadata": {
            "tags": []
          },
          "execution_count": 22
        }
      ]
    },
    {
      "cell_type": "code",
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "-WGFTlWp5dxT",
        "outputId": "d93be0b7-6e73-45e5-a1f4-117110ad06af"
      },
      "source": [
        "df.info()"
      ],
      "execution_count": 23,
      "outputs": [
        {
          "output_type": "stream",
          "text": [
            "<class 'pandas.core.frame.DataFrame'>\n",
            "RangeIndex: 23412 entries, 0 to 23411\n",
            "Data columns (total 21 columns):\n",
            " #   Column                      Non-Null Count  Dtype  \n",
            "---  ------                      --------------  -----  \n",
            " 0   Date                        23412 non-null  object \n",
            " 1   Time                        23412 non-null  object \n",
            " 2   Latitude                    23412 non-null  float64\n",
            " 3   Longitude                   23412 non-null  float64\n",
            " 4   Type                        23412 non-null  object \n",
            " 5   Depth                       23412 non-null  float64\n",
            " 6   Depth Error                 4461 non-null   float64\n",
            " 7   Depth Seismic Stations      7097 non-null   float64\n",
            " 8   Magnitude                   23412 non-null  float64\n",
            " 9   Magnitude Type              23409 non-null  object \n",
            " 10  Magnitude Error             327 non-null    float64\n",
            " 11  Magnitude Seismic Stations  2564 non-null   float64\n",
            " 12  Azimuthal Gap               7299 non-null   float64\n",
            " 13  Horizontal Distance         1604 non-null   float64\n",
            " 14  Horizontal Error            1156 non-null   float64\n",
            " 15  Root Mean Square            17352 non-null  float64\n",
            " 16  ID                          23412 non-null  object \n",
            " 17  Source                      23412 non-null  object \n",
            " 18  Location Source             23412 non-null  object \n",
            " 19  Magnitude Source            23412 non-null  object \n",
            " 20  Status                      23412 non-null  object \n",
            "dtypes: float64(12), object(9)\n",
            "memory usage: 3.8+ MB\n"
          ],
          "name": "stdout"
        }
      ]
    },
    {
      "cell_type": "code",
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "7UXzeROy5ptU",
        "outputId": "d68a35e1-9dfa-4dd7-8f74-39aec3e04ece"
      },
      "source": [
        "df.columns"
      ],
      "execution_count": 24,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "text/plain": [
              "Index(['Date', 'Time', 'Latitude', 'Longitude', 'Type', 'Depth', 'Depth Error',\n",
              "       'Depth Seismic Stations', 'Magnitude', 'Magnitude Type',\n",
              "       'Magnitude Error', 'Magnitude Seismic Stations', 'Azimuthal Gap',\n",
              "       'Horizontal Distance', 'Horizontal Error', 'Root Mean Square', 'ID',\n",
              "       'Source', 'Location Source', 'Magnitude Source', 'Status'],\n",
              "      dtype='object')"
            ]
          },
          "metadata": {
            "tags": []
          },
          "execution_count": 24
        }
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "SQuNwXpi59Ue"
      },
      "source": [
        "## Postwork 05: Limpieza de datos y agregaciones"
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "W-F4dsCPr-IA"
      },
      "source": [
        "\n",
        "\n",
        "1.   Limpiar nuestro dataset de NaNs.\n",
        "2.   Reindexar, si es necesario.\n",
        "3.   Renombrar columnas si es necesario.\n",
        "4.   Experimentar la aplicación de agregaciones para explorar nuestro dataset.\n",
        "\n"
      ]
    },
    {
      "cell_type": "code",
      "metadata": {
        "id": "pWd_Dm2msjz7"
      },
      "source": [
        "import numpy as np"
      ],
      "execution_count": 25,
      "outputs": []
    },
    {
      "cell_type": "code",
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 470
        },
        "id": "-C1OgBYUtpM_",
        "outputId": "c0193d0f-e7bb-47e5-912e-b4de9f42003d"
      },
      "source": [
        "df.isna()"
      ],
      "execution_count": 26,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "text/html": [
              "<div>\n",
              "<style scoped>\n",
              "    .dataframe tbody tr th:only-of-type {\n",
              "        vertical-align: middle;\n",
              "    }\n",
              "\n",
              "    .dataframe tbody tr th {\n",
              "        vertical-align: top;\n",
              "    }\n",
              "\n",
              "    .dataframe thead th {\n",
              "        text-align: right;\n",
              "    }\n",
              "</style>\n",
              "<table border=\"1\" class=\"dataframe\">\n",
              "  <thead>\n",
              "    <tr style=\"text-align: right;\">\n",
              "      <th></th>\n",
              "      <th>Date</th>\n",
              "      <th>Time</th>\n",
              "      <th>Latitude</th>\n",
              "      <th>Longitude</th>\n",
              "      <th>Type</th>\n",
              "      <th>Depth</th>\n",
              "      <th>Depth Error</th>\n",
              "      <th>Depth Seismic Stations</th>\n",
              "      <th>Magnitude</th>\n",
              "      <th>Magnitude Type</th>\n",
              "      <th>Magnitude Error</th>\n",
              "      <th>Magnitude Seismic Stations</th>\n",
              "      <th>Azimuthal Gap</th>\n",
              "      <th>Horizontal Distance</th>\n",
              "      <th>Horizontal Error</th>\n",
              "      <th>Root Mean Square</th>\n",
              "      <th>ID</th>\n",
              "      <th>Source</th>\n",
              "      <th>Location Source</th>\n",
              "      <th>Magnitude Source</th>\n",
              "      <th>Status</th>\n",
              "    </tr>\n",
              "  </thead>\n",
              "  <tbody>\n",
              "    <tr>\n",
              "      <th>0</th>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>True</td>\n",
              "      <td>True</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>True</td>\n",
              "      <td>True</td>\n",
              "      <td>True</td>\n",
              "      <td>True</td>\n",
              "      <td>True</td>\n",
              "      <td>True</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>1</th>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>True</td>\n",
              "      <td>True</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>True</td>\n",
              "      <td>True</td>\n",
              "      <td>True</td>\n",
              "      <td>True</td>\n",
              "      <td>True</td>\n",
              "      <td>True</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>2</th>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>True</td>\n",
              "      <td>True</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>True</td>\n",
              "      <td>True</td>\n",
              "      <td>True</td>\n",
              "      <td>True</td>\n",
              "      <td>True</td>\n",
              "      <td>True</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>3</th>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>True</td>\n",
              "      <td>True</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>True</td>\n",
              "      <td>True</td>\n",
              "      <td>True</td>\n",
              "      <td>True</td>\n",
              "      <td>True</td>\n",
              "      <td>True</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>4</th>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>True</td>\n",
              "      <td>True</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>True</td>\n",
              "      <td>True</td>\n",
              "      <td>True</td>\n",
              "      <td>True</td>\n",
              "      <td>True</td>\n",
              "      <td>True</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>...</th>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>23407</th>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>True</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>23408</th>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>True</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>23409</th>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>True</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>True</td>\n",
              "      <td>True</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>23410</th>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>True</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>True</td>\n",
              "      <td>True</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>23411</th>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>True</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "      <td>False</td>\n",
              "    </tr>\n",
              "  </tbody>\n",
              "</table>\n",
              "<p>23412 rows × 21 columns</p>\n",
              "</div>"
            ],
            "text/plain": [
              "        Date   Time  Latitude  ...  Location Source  Magnitude Source  Status\n",
              "0      False  False     False  ...            False             False   False\n",
              "1      False  False     False  ...            False             False   False\n",
              "2      False  False     False  ...            False             False   False\n",
              "3      False  False     False  ...            False             False   False\n",
              "4      False  False     False  ...            False             False   False\n",
              "...      ...    ...       ...  ...              ...               ...     ...\n",
              "23407  False  False     False  ...            False             False   False\n",
              "23408  False  False     False  ...            False             False   False\n",
              "23409  False  False     False  ...            False             False   False\n",
              "23410  False  False     False  ...            False             False   False\n",
              "23411  False  False     False  ...            False             False   False\n",
              "\n",
              "[23412 rows x 21 columns]"
            ]
          },
          "metadata": {
            "tags": []
          },
          "execution_count": 26
        }
      ]
    },
    {
      "cell_type": "code",
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "Q14_vtXCtxpH",
        "outputId": "b59ca709-3607-4d11-f60a-938ead1e7baf"
      },
      "source": [
        "#Se cuentan los NaNs en cada columna\n",
        "df.isna().sum(axis=0)"
      ],
      "execution_count": 29,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "text/plain": [
              "Date                              0\n",
              "Time                              0\n",
              "Latitude                          0\n",
              "Longitude                         0\n",
              "Type                              0\n",
              "Depth                             0\n",
              "Depth Error                   18951\n",
              "Depth Seismic Stations        16315\n",
              "Magnitude                         0\n",
              "Magnitude Type                    3\n",
              "Magnitude Error               23085\n",
              "Magnitude Seismic Stations    20848\n",
              "Azimuthal Gap                 16113\n",
              "Horizontal Distance           21808\n",
              "Horizontal Error              22256\n",
              "Root Mean Square               6060\n",
              "ID                                0\n",
              "Source                            0\n",
              "Location Source                   0\n",
              "Magnitude Source                  0\n",
              "Status                            0\n",
              "dtype: int64"
            ]
          },
          "metadata": {
            "tags": []
          },
          "execution_count": 29
        }
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "qAyAI8DOuo7z"
      },
      "source": [
        "Borraremos las columnas \"Depth Error\", \"Depth Seismic Stations\", \"Magnitude Error\", \"Magnitude Seismic Stations\", \"Azimuthal Gap\", \"Horizontal Distance\", \"Horizontal Error\" ,\"Root Mean Square\" debido a la cantidad de NaNs encontrados en ellas.     "
      ]
    },
    {
      "cell_type": "code",
      "metadata": {
        "id": "Qr8bHDLDxKoY",
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 433
        },
        "outputId": "e4184d2a-4551-4fb4-95e9-3a648db0cd35"
      },
      "source": [
        "columns_to_delete = [\"Depth Error\", \"Depth Seismic Stations\", \"Magnitude Error\", \"Magnitude Seismic Stations\", \"Azimuthal Gap\", \"Horizontal Distance\", \"Horizontal Error\" ,\"Root Mean Square\"]\n",
        "df_dropped = df.drop(columns=columns_to_delete)\n",
        "df_dropped"
      ],
      "execution_count": 36,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "text/html": [
              "<div>\n",
              "<style scoped>\n",
              "    .dataframe tbody tr th:only-of-type {\n",
              "        vertical-align: middle;\n",
              "    }\n",
              "\n",
              "    .dataframe tbody tr th {\n",
              "        vertical-align: top;\n",
              "    }\n",
              "\n",
              "    .dataframe thead th {\n",
              "        text-align: right;\n",
              "    }\n",
              "</style>\n",
              "<table border=\"1\" class=\"dataframe\">\n",
              "  <thead>\n",
              "    <tr style=\"text-align: right;\">\n",
              "      <th></th>\n",
              "      <th>Date</th>\n",
              "      <th>Time</th>\n",
              "      <th>Latitude</th>\n",
              "      <th>Longitude</th>\n",
              "      <th>Type</th>\n",
              "      <th>Depth</th>\n",
              "      <th>Magnitude</th>\n",
              "      <th>Magnitude Type</th>\n",
              "      <th>ID</th>\n",
              "      <th>Source</th>\n",
              "      <th>Location Source</th>\n",
              "      <th>Magnitude Source</th>\n",
              "      <th>Status</th>\n",
              "    </tr>\n",
              "  </thead>\n",
              "  <tbody>\n",
              "    <tr>\n",
              "      <th>0</th>\n",
              "      <td>01/02/1965</td>\n",
              "      <td>13:44:18</td>\n",
              "      <td>19.2460</td>\n",
              "      <td>145.6160</td>\n",
              "      <td>Earthquake</td>\n",
              "      <td>131.60</td>\n",
              "      <td>6.0</td>\n",
              "      <td>MW</td>\n",
              "      <td>ISCGEM860706</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>Automatic</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>1</th>\n",
              "      <td>01/04/1965</td>\n",
              "      <td>11:29:49</td>\n",
              "      <td>1.8630</td>\n",
              "      <td>127.3520</td>\n",
              "      <td>Earthquake</td>\n",
              "      <td>80.00</td>\n",
              "      <td>5.8</td>\n",
              "      <td>MW</td>\n",
              "      <td>ISCGEM860737</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>Automatic</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>2</th>\n",
              "      <td>01/05/1965</td>\n",
              "      <td>18:05:58</td>\n",
              "      <td>-20.5790</td>\n",
              "      <td>-173.9720</td>\n",
              "      <td>Earthquake</td>\n",
              "      <td>20.00</td>\n",
              "      <td>6.2</td>\n",
              "      <td>MW</td>\n",
              "      <td>ISCGEM860762</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>Automatic</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>3</th>\n",
              "      <td>01/08/1965</td>\n",
              "      <td>18:49:43</td>\n",
              "      <td>-59.0760</td>\n",
              "      <td>-23.5570</td>\n",
              "      <td>Earthquake</td>\n",
              "      <td>15.00</td>\n",
              "      <td>5.8</td>\n",
              "      <td>MW</td>\n",
              "      <td>ISCGEM860856</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>Automatic</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>4</th>\n",
              "      <td>01/09/1965</td>\n",
              "      <td>13:32:50</td>\n",
              "      <td>11.9380</td>\n",
              "      <td>126.4270</td>\n",
              "      <td>Earthquake</td>\n",
              "      <td>15.00</td>\n",
              "      <td>5.8</td>\n",
              "      <td>MW</td>\n",
              "      <td>ISCGEM860890</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>Automatic</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>...</th>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>23407</th>\n",
              "      <td>12/28/2016</td>\n",
              "      <td>08:22:12</td>\n",
              "      <td>38.3917</td>\n",
              "      <td>-118.8941</td>\n",
              "      <td>Earthquake</td>\n",
              "      <td>12.30</td>\n",
              "      <td>5.6</td>\n",
              "      <td>ML</td>\n",
              "      <td>NN00570710</td>\n",
              "      <td>NN</td>\n",
              "      <td>NN</td>\n",
              "      <td>NN</td>\n",
              "      <td>Reviewed</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>23408</th>\n",
              "      <td>12/28/2016</td>\n",
              "      <td>09:13:47</td>\n",
              "      <td>38.3777</td>\n",
              "      <td>-118.8957</td>\n",
              "      <td>Earthquake</td>\n",
              "      <td>8.80</td>\n",
              "      <td>5.5</td>\n",
              "      <td>ML</td>\n",
              "      <td>NN00570744</td>\n",
              "      <td>NN</td>\n",
              "      <td>NN</td>\n",
              "      <td>NN</td>\n",
              "      <td>Reviewed</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>23409</th>\n",
              "      <td>12/28/2016</td>\n",
              "      <td>12:38:51</td>\n",
              "      <td>36.9179</td>\n",
              "      <td>140.4262</td>\n",
              "      <td>Earthquake</td>\n",
              "      <td>10.00</td>\n",
              "      <td>5.9</td>\n",
              "      <td>MWW</td>\n",
              "      <td>US10007NAF</td>\n",
              "      <td>US</td>\n",
              "      <td>US</td>\n",
              "      <td>US</td>\n",
              "      <td>Reviewed</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>23410</th>\n",
              "      <td>12/29/2016</td>\n",
              "      <td>22:30:19</td>\n",
              "      <td>-9.0283</td>\n",
              "      <td>118.6639</td>\n",
              "      <td>Earthquake</td>\n",
              "      <td>79.00</td>\n",
              "      <td>6.3</td>\n",
              "      <td>MWW</td>\n",
              "      <td>US10007NL0</td>\n",
              "      <td>US</td>\n",
              "      <td>US</td>\n",
              "      <td>US</td>\n",
              "      <td>Reviewed</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>23411</th>\n",
              "      <td>12/30/2016</td>\n",
              "      <td>20:08:28</td>\n",
              "      <td>37.3973</td>\n",
              "      <td>141.4103</td>\n",
              "      <td>Earthquake</td>\n",
              "      <td>11.94</td>\n",
              "      <td>5.5</td>\n",
              "      <td>MB</td>\n",
              "      <td>US10007NTD</td>\n",
              "      <td>US</td>\n",
              "      <td>US</td>\n",
              "      <td>US</td>\n",
              "      <td>Reviewed</td>\n",
              "    </tr>\n",
              "  </tbody>\n",
              "</table>\n",
              "<p>23412 rows × 13 columns</p>\n",
              "</div>"
            ],
            "text/plain": [
              "             Date      Time  ...  Magnitude Source     Status\n",
              "0      01/02/1965  13:44:18  ...            ISCGEM  Automatic\n",
              "1      01/04/1965  11:29:49  ...            ISCGEM  Automatic\n",
              "2      01/05/1965  18:05:58  ...            ISCGEM  Automatic\n",
              "3      01/08/1965  18:49:43  ...            ISCGEM  Automatic\n",
              "4      01/09/1965  13:32:50  ...            ISCGEM  Automatic\n",
              "...           ...       ...  ...               ...        ...\n",
              "23407  12/28/2016  08:22:12  ...                NN   Reviewed\n",
              "23408  12/28/2016  09:13:47  ...                NN   Reviewed\n",
              "23409  12/28/2016  12:38:51  ...                US   Reviewed\n",
              "23410  12/29/2016  22:30:19  ...                US   Reviewed\n",
              "23411  12/30/2016  20:08:28  ...                US   Reviewed\n",
              "\n",
              "[23412 rows x 13 columns]"
            ]
          },
          "metadata": {
            "tags": []
          },
          "execution_count": 36
        }
      ]
    },
    {
      "cell_type": "code",
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "LIgdhI-Jz2XP",
        "outputId": "ff62ea6b-9140-4fd7-c476-ee3acd320359"
      },
      "source": [
        "df_dropped.info()"
      ],
      "execution_count": 37,
      "outputs": [
        {
          "output_type": "stream",
          "text": [
            "<class 'pandas.core.frame.DataFrame'>\n",
            "RangeIndex: 23412 entries, 0 to 23411\n",
            "Data columns (total 13 columns):\n",
            " #   Column            Non-Null Count  Dtype  \n",
            "---  ------            --------------  -----  \n",
            " 0   Date              23412 non-null  object \n",
            " 1   Time              23412 non-null  object \n",
            " 2   Latitude          23412 non-null  float64\n",
            " 3   Longitude         23412 non-null  float64\n",
            " 4   Type              23412 non-null  object \n",
            " 5   Depth             23412 non-null  float64\n",
            " 6   Magnitude         23412 non-null  float64\n",
            " 7   Magnitude Type    23409 non-null  object \n",
            " 8   ID                23412 non-null  object \n",
            " 9   Source            23412 non-null  object \n",
            " 10  Location Source   23412 non-null  object \n",
            " 11  Magnitude Source  23412 non-null  object \n",
            " 12  Status            23412 non-null  object \n",
            "dtypes: float64(4), object(9)\n",
            "memory usage: 2.3+ MB\n"
          ],
          "name": "stdout"
        }
      ]
    },
    {
      "cell_type": "code",
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "dU0HN46i08I3",
        "outputId": "6f8735d4-626c-445c-d993-ef00fefe2712"
      },
      "source": [
        "df_dropped.isna().sum(axis=0)"
      ],
      "execution_count": 38,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "text/plain": [
              "Date                0\n",
              "Time                0\n",
              "Latitude            0\n",
              "Longitude           0\n",
              "Type                0\n",
              "Depth               0\n",
              "Magnitude           0\n",
              "Magnitude Type      3\n",
              "ID                  0\n",
              "Source              0\n",
              "Location Source     0\n",
              "Magnitude Source    0\n",
              "Status              0\n",
              "dtype: int64"
            ]
          },
          "metadata": {
            "tags": []
          },
          "execution_count": 38
        }
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "9yTaMM5F41XB"
      },
      "source": [
        "Como en la columna \"Magnitude Type\" hay tres valores NaN's, se eliminarán esas tres filas."
      ]
    },
    {
      "cell_type": "code",
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 433
        },
        "id": "Cu13n4yxZwlv",
        "outputId": "13e1a091-e636-41e8-d549-3585d62ba44d"
      },
      "source": [
        "df_no_nan = df_dropped.dropna(axis=0)\n",
        "df_no_nan"
      ],
      "execution_count": 39,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "text/html": [
              "<div>\n",
              "<style scoped>\n",
              "    .dataframe tbody tr th:only-of-type {\n",
              "        vertical-align: middle;\n",
              "    }\n",
              "\n",
              "    .dataframe tbody tr th {\n",
              "        vertical-align: top;\n",
              "    }\n",
              "\n",
              "    .dataframe thead th {\n",
              "        text-align: right;\n",
              "    }\n",
              "</style>\n",
              "<table border=\"1\" class=\"dataframe\">\n",
              "  <thead>\n",
              "    <tr style=\"text-align: right;\">\n",
              "      <th></th>\n",
              "      <th>Date</th>\n",
              "      <th>Time</th>\n",
              "      <th>Latitude</th>\n",
              "      <th>Longitude</th>\n",
              "      <th>Type</th>\n",
              "      <th>Depth</th>\n",
              "      <th>Magnitude</th>\n",
              "      <th>Magnitude Type</th>\n",
              "      <th>ID</th>\n",
              "      <th>Source</th>\n",
              "      <th>Location Source</th>\n",
              "      <th>Magnitude Source</th>\n",
              "      <th>Status</th>\n",
              "    </tr>\n",
              "  </thead>\n",
              "  <tbody>\n",
              "    <tr>\n",
              "      <th>0</th>\n",
              "      <td>01/02/1965</td>\n",
              "      <td>13:44:18</td>\n",
              "      <td>19.2460</td>\n",
              "      <td>145.6160</td>\n",
              "      <td>Earthquake</td>\n",
              "      <td>131.60</td>\n",
              "      <td>6.0</td>\n",
              "      <td>MW</td>\n",
              "      <td>ISCGEM860706</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>Automatic</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>1</th>\n",
              "      <td>01/04/1965</td>\n",
              "      <td>11:29:49</td>\n",
              "      <td>1.8630</td>\n",
              "      <td>127.3520</td>\n",
              "      <td>Earthquake</td>\n",
              "      <td>80.00</td>\n",
              "      <td>5.8</td>\n",
              "      <td>MW</td>\n",
              "      <td>ISCGEM860737</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>Automatic</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>2</th>\n",
              "      <td>01/05/1965</td>\n",
              "      <td>18:05:58</td>\n",
              "      <td>-20.5790</td>\n",
              "      <td>-173.9720</td>\n",
              "      <td>Earthquake</td>\n",
              "      <td>20.00</td>\n",
              "      <td>6.2</td>\n",
              "      <td>MW</td>\n",
              "      <td>ISCGEM860762</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>Automatic</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>3</th>\n",
              "      <td>01/08/1965</td>\n",
              "      <td>18:49:43</td>\n",
              "      <td>-59.0760</td>\n",
              "      <td>-23.5570</td>\n",
              "      <td>Earthquake</td>\n",
              "      <td>15.00</td>\n",
              "      <td>5.8</td>\n",
              "      <td>MW</td>\n",
              "      <td>ISCGEM860856</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>Automatic</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>4</th>\n",
              "      <td>01/09/1965</td>\n",
              "      <td>13:32:50</td>\n",
              "      <td>11.9380</td>\n",
              "      <td>126.4270</td>\n",
              "      <td>Earthquake</td>\n",
              "      <td>15.00</td>\n",
              "      <td>5.8</td>\n",
              "      <td>MW</td>\n",
              "      <td>ISCGEM860890</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>Automatic</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>...</th>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>23407</th>\n",
              "      <td>12/28/2016</td>\n",
              "      <td>08:22:12</td>\n",
              "      <td>38.3917</td>\n",
              "      <td>-118.8941</td>\n",
              "      <td>Earthquake</td>\n",
              "      <td>12.30</td>\n",
              "      <td>5.6</td>\n",
              "      <td>ML</td>\n",
              "      <td>NN00570710</td>\n",
              "      <td>NN</td>\n",
              "      <td>NN</td>\n",
              "      <td>NN</td>\n",
              "      <td>Reviewed</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>23408</th>\n",
              "      <td>12/28/2016</td>\n",
              "      <td>09:13:47</td>\n",
              "      <td>38.3777</td>\n",
              "      <td>-118.8957</td>\n",
              "      <td>Earthquake</td>\n",
              "      <td>8.80</td>\n",
              "      <td>5.5</td>\n",
              "      <td>ML</td>\n",
              "      <td>NN00570744</td>\n",
              "      <td>NN</td>\n",
              "      <td>NN</td>\n",
              "      <td>NN</td>\n",
              "      <td>Reviewed</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>23409</th>\n",
              "      <td>12/28/2016</td>\n",
              "      <td>12:38:51</td>\n",
              "      <td>36.9179</td>\n",
              "      <td>140.4262</td>\n",
              "      <td>Earthquake</td>\n",
              "      <td>10.00</td>\n",
              "      <td>5.9</td>\n",
              "      <td>MWW</td>\n",
              "      <td>US10007NAF</td>\n",
              "      <td>US</td>\n",
              "      <td>US</td>\n",
              "      <td>US</td>\n",
              "      <td>Reviewed</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>23410</th>\n",
              "      <td>12/29/2016</td>\n",
              "      <td>22:30:19</td>\n",
              "      <td>-9.0283</td>\n",
              "      <td>118.6639</td>\n",
              "      <td>Earthquake</td>\n",
              "      <td>79.00</td>\n",
              "      <td>6.3</td>\n",
              "      <td>MWW</td>\n",
              "      <td>US10007NL0</td>\n",
              "      <td>US</td>\n",
              "      <td>US</td>\n",
              "      <td>US</td>\n",
              "      <td>Reviewed</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>23411</th>\n",
              "      <td>12/30/2016</td>\n",
              "      <td>20:08:28</td>\n",
              "      <td>37.3973</td>\n",
              "      <td>141.4103</td>\n",
              "      <td>Earthquake</td>\n",
              "      <td>11.94</td>\n",
              "      <td>5.5</td>\n",
              "      <td>MB</td>\n",
              "      <td>US10007NTD</td>\n",
              "      <td>US</td>\n",
              "      <td>US</td>\n",
              "      <td>US</td>\n",
              "      <td>Reviewed</td>\n",
              "    </tr>\n",
              "  </tbody>\n",
              "</table>\n",
              "<p>23409 rows × 13 columns</p>\n",
              "</div>"
            ],
            "text/plain": [
              "             Date      Time  ...  Magnitude Source     Status\n",
              "0      01/02/1965  13:44:18  ...            ISCGEM  Automatic\n",
              "1      01/04/1965  11:29:49  ...            ISCGEM  Automatic\n",
              "2      01/05/1965  18:05:58  ...            ISCGEM  Automatic\n",
              "3      01/08/1965  18:49:43  ...            ISCGEM  Automatic\n",
              "4      01/09/1965  13:32:50  ...            ISCGEM  Automatic\n",
              "...           ...       ...  ...               ...        ...\n",
              "23407  12/28/2016  08:22:12  ...                NN   Reviewed\n",
              "23408  12/28/2016  09:13:47  ...                NN   Reviewed\n",
              "23409  12/28/2016  12:38:51  ...                US   Reviewed\n",
              "23410  12/29/2016  22:30:19  ...                US   Reviewed\n",
              "23411  12/30/2016  20:08:28  ...                US   Reviewed\n",
              "\n",
              "[23409 rows x 13 columns]"
            ]
          },
          "metadata": {
            "tags": []
          },
          "execution_count": 39
        }
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "JKGd7_vhZ1bJ"
      },
      "source": [
        "Se comprueba que no exista ningún NaN en el DataFrame.\n",
        "\n"
      ]
    },
    {
      "cell_type": "code",
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "wrYVn2n3awj_",
        "outputId": "a4cb9394-212a-4f01-cca1-93a4116fac50"
      },
      "source": [
        "df_no_nan.isna().sum(axis=0)"
      ],
      "execution_count": 42,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "text/plain": [
              "Date                0\n",
              "Time                0\n",
              "Latitude            0\n",
              "Longitude           0\n",
              "Type                0\n",
              "Depth               0\n",
              "Magnitude           0\n",
              "Magnitude Type      0\n",
              "ID                  0\n",
              "Source              0\n",
              "Location Source     0\n",
              "Magnitude Source    0\n",
              "Status              0\n",
              "dtype: int64"
            ]
          },
          "metadata": {
            "tags": []
          },
          "execution_count": 42
        }
      ]
    },
    {
      "cell_type": "code",
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 433
        },
        "id": "AijdP03sbHp3",
        "outputId": "b3525df0-e9cf-46b8-89f7-b9b4e7aebcab"
      },
      "source": [
        "df_no_nan"
      ],
      "execution_count": 44,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "text/html": [
              "<div>\n",
              "<style scoped>\n",
              "    .dataframe tbody tr th:only-of-type {\n",
              "        vertical-align: middle;\n",
              "    }\n",
              "\n",
              "    .dataframe tbody tr th {\n",
              "        vertical-align: top;\n",
              "    }\n",
              "\n",
              "    .dataframe thead th {\n",
              "        text-align: right;\n",
              "    }\n",
              "</style>\n",
              "<table border=\"1\" class=\"dataframe\">\n",
              "  <thead>\n",
              "    <tr style=\"text-align: right;\">\n",
              "      <th></th>\n",
              "      <th>Date</th>\n",
              "      <th>Time</th>\n",
              "      <th>Latitude</th>\n",
              "      <th>Longitude</th>\n",
              "      <th>Type</th>\n",
              "      <th>Depth</th>\n",
              "      <th>Magnitude</th>\n",
              "      <th>Magnitude Type</th>\n",
              "      <th>ID</th>\n",
              "      <th>Source</th>\n",
              "      <th>Location Source</th>\n",
              "      <th>Magnitude Source</th>\n",
              "      <th>Status</th>\n",
              "    </tr>\n",
              "  </thead>\n",
              "  <tbody>\n",
              "    <tr>\n",
              "      <th>0</th>\n",
              "      <td>01/02/1965</td>\n",
              "      <td>13:44:18</td>\n",
              "      <td>19.2460</td>\n",
              "      <td>145.6160</td>\n",
              "      <td>Earthquake</td>\n",
              "      <td>131.60</td>\n",
              "      <td>6.0</td>\n",
              "      <td>MW</td>\n",
              "      <td>ISCGEM860706</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>Automatic</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>1</th>\n",
              "      <td>01/04/1965</td>\n",
              "      <td>11:29:49</td>\n",
              "      <td>1.8630</td>\n",
              "      <td>127.3520</td>\n",
              "      <td>Earthquake</td>\n",
              "      <td>80.00</td>\n",
              "      <td>5.8</td>\n",
              "      <td>MW</td>\n",
              "      <td>ISCGEM860737</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>Automatic</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>2</th>\n",
              "      <td>01/05/1965</td>\n",
              "      <td>18:05:58</td>\n",
              "      <td>-20.5790</td>\n",
              "      <td>-173.9720</td>\n",
              "      <td>Earthquake</td>\n",
              "      <td>20.00</td>\n",
              "      <td>6.2</td>\n",
              "      <td>MW</td>\n",
              "      <td>ISCGEM860762</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>Automatic</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>3</th>\n",
              "      <td>01/08/1965</td>\n",
              "      <td>18:49:43</td>\n",
              "      <td>-59.0760</td>\n",
              "      <td>-23.5570</td>\n",
              "      <td>Earthquake</td>\n",
              "      <td>15.00</td>\n",
              "      <td>5.8</td>\n",
              "      <td>MW</td>\n",
              "      <td>ISCGEM860856</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>Automatic</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>4</th>\n",
              "      <td>01/09/1965</td>\n",
              "      <td>13:32:50</td>\n",
              "      <td>11.9380</td>\n",
              "      <td>126.4270</td>\n",
              "      <td>Earthquake</td>\n",
              "      <td>15.00</td>\n",
              "      <td>5.8</td>\n",
              "      <td>MW</td>\n",
              "      <td>ISCGEM860890</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>Automatic</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>...</th>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>23407</th>\n",
              "      <td>12/28/2016</td>\n",
              "      <td>08:22:12</td>\n",
              "      <td>38.3917</td>\n",
              "      <td>-118.8941</td>\n",
              "      <td>Earthquake</td>\n",
              "      <td>12.30</td>\n",
              "      <td>5.6</td>\n",
              "      <td>ML</td>\n",
              "      <td>NN00570710</td>\n",
              "      <td>NN</td>\n",
              "      <td>NN</td>\n",
              "      <td>NN</td>\n",
              "      <td>Reviewed</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>23408</th>\n",
              "      <td>12/28/2016</td>\n",
              "      <td>09:13:47</td>\n",
              "      <td>38.3777</td>\n",
              "      <td>-118.8957</td>\n",
              "      <td>Earthquake</td>\n",
              "      <td>8.80</td>\n",
              "      <td>5.5</td>\n",
              "      <td>ML</td>\n",
              "      <td>NN00570744</td>\n",
              "      <td>NN</td>\n",
              "      <td>NN</td>\n",
              "      <td>NN</td>\n",
              "      <td>Reviewed</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>23409</th>\n",
              "      <td>12/28/2016</td>\n",
              "      <td>12:38:51</td>\n",
              "      <td>36.9179</td>\n",
              "      <td>140.4262</td>\n",
              "      <td>Earthquake</td>\n",
              "      <td>10.00</td>\n",
              "      <td>5.9</td>\n",
              "      <td>MWW</td>\n",
              "      <td>US10007NAF</td>\n",
              "      <td>US</td>\n",
              "      <td>US</td>\n",
              "      <td>US</td>\n",
              "      <td>Reviewed</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>23410</th>\n",
              "      <td>12/29/2016</td>\n",
              "      <td>22:30:19</td>\n",
              "      <td>-9.0283</td>\n",
              "      <td>118.6639</td>\n",
              "      <td>Earthquake</td>\n",
              "      <td>79.00</td>\n",
              "      <td>6.3</td>\n",
              "      <td>MWW</td>\n",
              "      <td>US10007NL0</td>\n",
              "      <td>US</td>\n",
              "      <td>US</td>\n",
              "      <td>US</td>\n",
              "      <td>Reviewed</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>23411</th>\n",
              "      <td>12/30/2016</td>\n",
              "      <td>20:08:28</td>\n",
              "      <td>37.3973</td>\n",
              "      <td>141.4103</td>\n",
              "      <td>Earthquake</td>\n",
              "      <td>11.94</td>\n",
              "      <td>5.5</td>\n",
              "      <td>MB</td>\n",
              "      <td>US10007NTD</td>\n",
              "      <td>US</td>\n",
              "      <td>US</td>\n",
              "      <td>US</td>\n",
              "      <td>Reviewed</td>\n",
              "    </tr>\n",
              "  </tbody>\n",
              "</table>\n",
              "<p>23409 rows × 13 columns</p>\n",
              "</div>"
            ],
            "text/plain": [
              "             Date      Time  ...  Magnitude Source     Status\n",
              "0      01/02/1965  13:44:18  ...            ISCGEM  Automatic\n",
              "1      01/04/1965  11:29:49  ...            ISCGEM  Automatic\n",
              "2      01/05/1965  18:05:58  ...            ISCGEM  Automatic\n",
              "3      01/08/1965  18:49:43  ...            ISCGEM  Automatic\n",
              "4      01/09/1965  13:32:50  ...            ISCGEM  Automatic\n",
              "...           ...       ...  ...               ...        ...\n",
              "23407  12/28/2016  08:22:12  ...                NN   Reviewed\n",
              "23408  12/28/2016  09:13:47  ...                NN   Reviewed\n",
              "23409  12/28/2016  12:38:51  ...                US   Reviewed\n",
              "23410  12/29/2016  22:30:19  ...                US   Reviewed\n",
              "23411  12/30/2016  20:08:28  ...                US   Reviewed\n",
              "\n",
              "[23409 rows x 13 columns]"
            ]
          },
          "metadata": {
            "tags": []
          },
          "execution_count": 44
        }
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "-6mL85f7yhWV"
      },
      "source": [
        "Se reindexa el DataFrame para terminar la limpieza"
      ]
    },
    {
      "cell_type": "code",
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 433
        },
        "id": "xG278-RDyi1N",
        "outputId": "bee0c059-0867-428f-b822-d4c53f137677"
      },
      "source": [
        "#Como se hará un reindexado, la columna \"index\" es inútil, por lo que se le hará drop\n",
        "#para que no se cree una columna con los índices antiguos\n",
        "df_clean = df_no_nan.reset_index(drop=True)\n",
        "df_clean"
      ],
      "execution_count": 88,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "text/html": [
              "<div>\n",
              "<style scoped>\n",
              "    .dataframe tbody tr th:only-of-type {\n",
              "        vertical-align: middle;\n",
              "    }\n",
              "\n",
              "    .dataframe tbody tr th {\n",
              "        vertical-align: top;\n",
              "    }\n",
              "\n",
              "    .dataframe thead th {\n",
              "        text-align: right;\n",
              "    }\n",
              "</style>\n",
              "<table border=\"1\" class=\"dataframe\">\n",
              "  <thead>\n",
              "    <tr style=\"text-align: right;\">\n",
              "      <th></th>\n",
              "      <th>Date</th>\n",
              "      <th>Time</th>\n",
              "      <th>Latitude</th>\n",
              "      <th>Longitude</th>\n",
              "      <th>Type</th>\n",
              "      <th>Depth</th>\n",
              "      <th>Magnitude</th>\n",
              "      <th>Magnitude Type</th>\n",
              "      <th>ID</th>\n",
              "      <th>Source</th>\n",
              "      <th>Location Source</th>\n",
              "      <th>Magnitude Source</th>\n",
              "      <th>Status</th>\n",
              "    </tr>\n",
              "  </thead>\n",
              "  <tbody>\n",
              "    <tr>\n",
              "      <th>0</th>\n",
              "      <td>01/02/1965</td>\n",
              "      <td>13:44:18</td>\n",
              "      <td>19.2460</td>\n",
              "      <td>145.6160</td>\n",
              "      <td>Earthquake</td>\n",
              "      <td>131.60</td>\n",
              "      <td>6.0</td>\n",
              "      <td>MW</td>\n",
              "      <td>ISCGEM860706</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>Automatic</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>1</th>\n",
              "      <td>01/04/1965</td>\n",
              "      <td>11:29:49</td>\n",
              "      <td>1.8630</td>\n",
              "      <td>127.3520</td>\n",
              "      <td>Earthquake</td>\n",
              "      <td>80.00</td>\n",
              "      <td>5.8</td>\n",
              "      <td>MW</td>\n",
              "      <td>ISCGEM860737</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>Automatic</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>2</th>\n",
              "      <td>01/05/1965</td>\n",
              "      <td>18:05:58</td>\n",
              "      <td>-20.5790</td>\n",
              "      <td>-173.9720</td>\n",
              "      <td>Earthquake</td>\n",
              "      <td>20.00</td>\n",
              "      <td>6.2</td>\n",
              "      <td>MW</td>\n",
              "      <td>ISCGEM860762</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>Automatic</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>3</th>\n",
              "      <td>01/08/1965</td>\n",
              "      <td>18:49:43</td>\n",
              "      <td>-59.0760</td>\n",
              "      <td>-23.5570</td>\n",
              "      <td>Earthquake</td>\n",
              "      <td>15.00</td>\n",
              "      <td>5.8</td>\n",
              "      <td>MW</td>\n",
              "      <td>ISCGEM860856</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>Automatic</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>4</th>\n",
              "      <td>01/09/1965</td>\n",
              "      <td>13:32:50</td>\n",
              "      <td>11.9380</td>\n",
              "      <td>126.4270</td>\n",
              "      <td>Earthquake</td>\n",
              "      <td>15.00</td>\n",
              "      <td>5.8</td>\n",
              "      <td>MW</td>\n",
              "      <td>ISCGEM860890</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>Automatic</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>...</th>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>23404</th>\n",
              "      <td>12/28/2016</td>\n",
              "      <td>08:22:12</td>\n",
              "      <td>38.3917</td>\n",
              "      <td>-118.8941</td>\n",
              "      <td>Earthquake</td>\n",
              "      <td>12.30</td>\n",
              "      <td>5.6</td>\n",
              "      <td>ML</td>\n",
              "      <td>NN00570710</td>\n",
              "      <td>NN</td>\n",
              "      <td>NN</td>\n",
              "      <td>NN</td>\n",
              "      <td>Reviewed</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>23405</th>\n",
              "      <td>12/28/2016</td>\n",
              "      <td>09:13:47</td>\n",
              "      <td>38.3777</td>\n",
              "      <td>-118.8957</td>\n",
              "      <td>Earthquake</td>\n",
              "      <td>8.80</td>\n",
              "      <td>5.5</td>\n",
              "      <td>ML</td>\n",
              "      <td>NN00570744</td>\n",
              "      <td>NN</td>\n",
              "      <td>NN</td>\n",
              "      <td>NN</td>\n",
              "      <td>Reviewed</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>23406</th>\n",
              "      <td>12/28/2016</td>\n",
              "      <td>12:38:51</td>\n",
              "      <td>36.9179</td>\n",
              "      <td>140.4262</td>\n",
              "      <td>Earthquake</td>\n",
              "      <td>10.00</td>\n",
              "      <td>5.9</td>\n",
              "      <td>MWW</td>\n",
              "      <td>US10007NAF</td>\n",
              "      <td>US</td>\n",
              "      <td>US</td>\n",
              "      <td>US</td>\n",
              "      <td>Reviewed</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>23407</th>\n",
              "      <td>12/29/2016</td>\n",
              "      <td>22:30:19</td>\n",
              "      <td>-9.0283</td>\n",
              "      <td>118.6639</td>\n",
              "      <td>Earthquake</td>\n",
              "      <td>79.00</td>\n",
              "      <td>6.3</td>\n",
              "      <td>MWW</td>\n",
              "      <td>US10007NL0</td>\n",
              "      <td>US</td>\n",
              "      <td>US</td>\n",
              "      <td>US</td>\n",
              "      <td>Reviewed</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>23408</th>\n",
              "      <td>12/30/2016</td>\n",
              "      <td>20:08:28</td>\n",
              "      <td>37.3973</td>\n",
              "      <td>141.4103</td>\n",
              "      <td>Earthquake</td>\n",
              "      <td>11.94</td>\n",
              "      <td>5.5</td>\n",
              "      <td>MB</td>\n",
              "      <td>US10007NTD</td>\n",
              "      <td>US</td>\n",
              "      <td>US</td>\n",
              "      <td>US</td>\n",
              "      <td>Reviewed</td>\n",
              "    </tr>\n",
              "  </tbody>\n",
              "</table>\n",
              "<p>23409 rows × 13 columns</p>\n",
              "</div>"
            ],
            "text/plain": [
              "             Date      Time  ...  Magnitude Source     Status\n",
              "0      01/02/1965  13:44:18  ...            ISCGEM  Automatic\n",
              "1      01/04/1965  11:29:49  ...            ISCGEM  Automatic\n",
              "2      01/05/1965  18:05:58  ...            ISCGEM  Automatic\n",
              "3      01/08/1965  18:49:43  ...            ISCGEM  Automatic\n",
              "4      01/09/1965  13:32:50  ...            ISCGEM  Automatic\n",
              "...           ...       ...  ...               ...        ...\n",
              "23404  12/28/2016  08:22:12  ...                NN   Reviewed\n",
              "23405  12/28/2016  09:13:47  ...                NN   Reviewed\n",
              "23406  12/28/2016  12:38:51  ...                US   Reviewed\n",
              "23407  12/29/2016  22:30:19  ...                US   Reviewed\n",
              "23408  12/30/2016  20:08:28  ...                US   Reviewed\n",
              "\n",
              "[23409 rows x 13 columns]"
            ]
          },
          "metadata": {
            "tags": []
          },
          "execution_count": 88
        }
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "sTBdreumzWHC"
      },
      "source": [
        "Para tener una idea burda de la región geográfica que aparece más en el dataset, se calcula el promedio y la desviación estándar de la longitud y de la latitud"
      ]
    },
    {
      "cell_type": "code",
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "K0va7hSN0UAF",
        "outputId": "8eb5ac6e-598f-40ab-af20-dd90c2a581a0"
      },
      "source": [
        "#Latitud\n",
        "print(f\"La distribución de latitud es\\n{df_clean['Latitude'].mean():.2f} +/- {df_clean['Latitude'].std():.2f}\")"
      ],
      "execution_count": 89,
      "outputs": [
        {
          "output_type": "stream",
          "text": [
            "La distribución de latitud es\n",
            "1.67 +/- 30.11\n"
          ],
          "name": "stdout"
        }
      ]
    },
    {
      "cell_type": "code",
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "RP8fz6nl0WD6",
        "outputId": "12fa1c57-1e16-4f55-8e63-a92634029208"
      },
      "source": [
        "#Longitud\n",
        "print(f\"La distribución de longitud es\\n{df_clean['Longitude'].mean():.2f} +/- {df_clean['Longitude'].std():.2f}\")"
      ],
      "execution_count": 90,
      "outputs": [
        {
          "output_type": "stream",
          "text": [
            "La distribución de longitud es\n",
            "39.66 +/- 125.51\n"
          ],
          "name": "stdout"
        }
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "DqelKibQ1zOc"
      },
      "source": [
        "Para poner en perspectiva la distribución anterior, se debe conocer el intervalo de valores de ambas columnas"
      ]
    },
    {
      "cell_type": "code",
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "bZo7LD3t2AGb",
        "outputId": "487b1d03-0725-4f32-cabe-8c39474aab59"
      },
      "source": [
        "#Latitud\n",
        "print(f\"La latitud toma valores entre\\n{df_clean['Latitude'].min():.2f} y {df_clean['Latitude'].max():.2f}\")"
      ],
      "execution_count": 91,
      "outputs": [
        {
          "output_type": "stream",
          "text": [
            "La latitud toma valores entre\n",
            "-77.08 y 86.00\n"
          ],
          "name": "stdout"
        }
      ]
    },
    {
      "cell_type": "code",
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "xbWqFH8E2CDp",
        "outputId": "871847ff-4169-43c2-cef2-c262561e9f85"
      },
      "source": [
        "#Longitud\n",
        "print(f\"La longitud toma valores entre\\n{df_clean['Longitude'].min():.2f} y {df_clean['Longitude'].std():.2f}\")"
      ],
      "execution_count": 92,
      "outputs": [
        {
          "output_type": "stream",
          "text": [
            "La longitud toma valores entre\n",
            "-180.00 y 125.51\n"
          ],
          "name": "stdout"
        }
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "zIIc4_5a4IMT"
      },
      "source": [
        "Concluimos que la distribución en la latitud no es tan dispersa, pero la distribución sobre la longitud sí."
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "G9C5SXGv4UAv"
      },
      "source": [
        "Para tener una perspectiva condensada de lo anterior, se usa la agregación _describe_\n",
        "\n",
        "Se confirma lo que se  mencionó sobre la distribución ya no sólo con el promedio y la desviación estándar, sino también con los cuartiles"
      ]
    },
    {
      "cell_type": "code",
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 294
        },
        "id": "xqc0cD7P4ThG",
        "outputId": "8c3b4d94-4c63-422e-db75-8fbafcaad127"
      },
      "source": [
        "df_clean.describe()"
      ],
      "execution_count": 94,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "text/html": [
              "<div>\n",
              "<style scoped>\n",
              "    .dataframe tbody tr th:only-of-type {\n",
              "        vertical-align: middle;\n",
              "    }\n",
              "\n",
              "    .dataframe tbody tr th {\n",
              "        vertical-align: top;\n",
              "    }\n",
              "\n",
              "    .dataframe thead th {\n",
              "        text-align: right;\n",
              "    }\n",
              "</style>\n",
              "<table border=\"1\" class=\"dataframe\">\n",
              "  <thead>\n",
              "    <tr style=\"text-align: right;\">\n",
              "      <th></th>\n",
              "      <th>Latitude</th>\n",
              "      <th>Longitude</th>\n",
              "      <th>Depth</th>\n",
              "      <th>Magnitude</th>\n",
              "    </tr>\n",
              "  </thead>\n",
              "  <tbody>\n",
              "    <tr>\n",
              "      <th>count</th>\n",
              "      <td>23409.000000</td>\n",
              "      <td>23409.000000</td>\n",
              "      <td>23409.000000</td>\n",
              "      <td>23409.000000</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>mean</th>\n",
              "      <td>1.674322</td>\n",
              "      <td>39.660642</td>\n",
              "      <td>70.775695</td>\n",
              "      <td>5.882553</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>std</th>\n",
              "      <td>30.112233</td>\n",
              "      <td>125.506701</td>\n",
              "      <td>122.657829</td>\n",
              "      <td>0.423087</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>min</th>\n",
              "      <td>-77.080000</td>\n",
              "      <td>-179.997000</td>\n",
              "      <td>-1.100000</td>\n",
              "      <td>5.500000</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>25%</th>\n",
              "      <td>-18.656000</td>\n",
              "      <td>-76.311300</td>\n",
              "      <td>14.540000</td>\n",
              "      <td>5.600000</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>50%</th>\n",
              "      <td>-3.570000</td>\n",
              "      <td>103.993000</td>\n",
              "      <td>33.000000</td>\n",
              "      <td>5.700000</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>75%</th>\n",
              "      <td>26.158000</td>\n",
              "      <td>145.027000</td>\n",
              "      <td>54.000000</td>\n",
              "      <td>6.000000</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>max</th>\n",
              "      <td>86.005000</td>\n",
              "      <td>179.998000</td>\n",
              "      <td>700.000000</td>\n",
              "      <td>9.100000</td>\n",
              "    </tr>\n",
              "  </tbody>\n",
              "</table>\n",
              "</div>"
            ],
            "text/plain": [
              "           Latitude     Longitude         Depth     Magnitude\n",
              "count  23409.000000  23409.000000  23409.000000  23409.000000\n",
              "mean       1.674322     39.660642     70.775695      5.882553\n",
              "std       30.112233    125.506701    122.657829      0.423087\n",
              "min      -77.080000   -179.997000     -1.100000      5.500000\n",
              "25%      -18.656000    -76.311300     14.540000      5.600000\n",
              "50%       -3.570000    103.993000     33.000000      5.700000\n",
              "75%       26.158000    145.027000     54.000000      6.000000\n",
              "max       86.005000    179.998000    700.000000      9.100000"
            ]
          },
          "metadata": {
            "tags": []
          },
          "execution_count": 94
        }
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "2qOefPqQ42S5"
      },
      "source": [
        "Por último, puede contarse la cantidad de registros que son terremotos"
      ]
    },
    {
      "cell_type": "code",
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "GOYTy9ba41su",
        "outputId": "af1492b0-8f89-46a3-f1ed-51135b2f62d2"
      },
      "source": [
        "df_clean [ df_clean[\"Type\"]==\"Earthquake\" ] [\"Type\"].count()\n",
        "#La primera parte entre corchetes es el pipe para tomar sólo los terremotos\n",
        "#La segunda es para tomar una de las columnas (en este caso la del type), del df \"pipeado\""
      ],
      "execution_count": 95,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "text/plain": [
              "23229"
            ]
          },
          "metadata": {
            "tags": []
          },
          "execution_count": 95
        }
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "QH5QYouQ5o0f"
      },
      "source": [
        "De los 23409 registros, 23,229 son terremotos, por lo que la base de datos es útil."
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "6lchslCtdmYo"
      },
      "source": [
        "##(Opcional) Postwork 6: Automatización y APIs"
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "bso5ZkJ4fTyY"
      },
      "source": [
        "Hay que descargar el paquete para trabajar con Kaggle desde Colab"
      ]
    },
    {
      "cell_type": "code",
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "nGVp2lxreGcL",
        "outputId": "42c316e1-e9ec-4663-d1f6-44c60e2e8ef7"
      },
      "source": [
        "!pip install kaggle"
      ],
      "execution_count": 1,
      "outputs": [
        {
          "output_type": "stream",
          "text": [
            "Requirement already satisfied: kaggle in /usr/local/lib/python3.7/dist-packages (1.5.12)\n",
            "Requirement already satisfied: python-slugify in /usr/local/lib/python3.7/dist-packages (from kaggle) (5.0.2)\n",
            "Requirement already satisfied: six>=1.10 in /usr/local/lib/python3.7/dist-packages (from kaggle) (1.15.0)\n",
            "Requirement already satisfied: tqdm in /usr/local/lib/python3.7/dist-packages (from kaggle) (4.41.1)\n",
            "Requirement already satisfied: certifi in /usr/local/lib/python3.7/dist-packages (from kaggle) (2021.5.30)\n",
            "Requirement already satisfied: requests in /usr/local/lib/python3.7/dist-packages (from kaggle) (2.23.0)\n",
            "Requirement already satisfied: python-dateutil in /usr/local/lib/python3.7/dist-packages (from kaggle) (2.8.1)\n",
            "Requirement already satisfied: urllib3 in /usr/local/lib/python3.7/dist-packages (from kaggle) (1.24.3)\n",
            "Requirement already satisfied: text-unidecode>=1.3 in /usr/local/lib/python3.7/dist-packages (from python-slugify->kaggle) (1.3)\n",
            "Requirement already satisfied: chardet<4,>=3.0.2 in /usr/local/lib/python3.7/dist-packages (from requests->kaggle) (3.0.4)\n",
            "Requirement already satisfied: idna<3,>=2.5 in /usr/local/lib/python3.7/dist-packages (from requests->kaggle) (2.10)\n"
          ],
          "name": "stdout"
        }
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "4QSXdLIbfcjU"
      },
      "source": [
        "Se tiene que subir el API key que se obtiene en el perfil de Kaggle (para eso hay que registrarse). [Aquí hay una guía completa donde se cubre eso](https://www.kaggle.com/docs/api). [Aquí hay un foro donde se discute más información](https://www.kaggle.com/general/74235)."
      ]
    },
    {
      "cell_type": "code",
      "metadata": {
        "colab": {
          "resources": {
            "http://localhost:8080/nbextensions/google.colab/files.js": {
              "data": "Ly8gQ29weXJpZ2h0IDIwMTcgR29vZ2xlIExMQwovLwovLyBMaWNlbnNlZCB1bmRlciB0aGUgQXBhY2hlIExpY2Vuc2UsIFZlcnNpb24gMi4wICh0aGUgIkxpY2Vuc2UiKTsKLy8geW91IG1heSBub3QgdXNlIHRoaXMgZmlsZSBleGNlcHQgaW4gY29tcGxpYW5jZSB3aXRoIHRoZSBMaWNlbnNlLgovLyBZb3UgbWF5IG9idGFpbiBhIGNvcHkgb2YgdGhlIExpY2Vuc2UgYXQKLy8KLy8gICAgICBodHRwOi8vd3d3LmFwYWNoZS5vcmcvbGljZW5zZXMvTElDRU5TRS0yLjAKLy8KLy8gVW5sZXNzIHJlcXVpcmVkIGJ5IGFwcGxpY2FibGUgbGF3IG9yIGFncmVlZCB0byBpbiB3cml0aW5nLCBzb2Z0d2FyZQovLyBkaXN0cmlidXRlZCB1bmRlciB0aGUgTGljZW5zZSBpcyBkaXN0cmlidXRlZCBvbiBhbiAiQVMgSVMiIEJBU0lTLAovLyBXSVRIT1VUIFdBUlJBTlRJRVMgT1IgQ09ORElUSU9OUyBPRiBBTlkgS0lORCwgZWl0aGVyIGV4cHJlc3Mgb3IgaW1wbGllZC4KLy8gU2VlIHRoZSBMaWNlbnNlIGZvciB0aGUgc3BlY2lmaWMgbGFuZ3VhZ2UgZ292ZXJuaW5nIHBlcm1pc3Npb25zIGFuZAovLyBsaW1pdGF0aW9ucyB1bmRlciB0aGUgTGljZW5zZS4KCi8qKgogKiBAZmlsZW92ZXJ2aWV3IEhlbHBlcnMgZm9yIGdvb2dsZS5jb2xhYiBQeXRob24gbW9kdWxlLgogKi8KKGZ1bmN0aW9uKHNjb3BlKSB7CmZ1bmN0aW9uIHNwYW4odGV4dCwgc3R5bGVBdHRyaWJ1dGVzID0ge30pIHsKICBjb25zdCBlbGVtZW50ID0gZG9jdW1lbnQuY3JlYXRlRWxlbWVudCgnc3BhbicpOwogIGVsZW1lbnQudGV4dENvbnRlbnQgPSB0ZXh0OwogIGZvciAoY29uc3Qga2V5IG9mIE9iamVjdC5rZXlzKHN0eWxlQXR0cmlidXRlcykpIHsKICAgIGVsZW1lbnQuc3R5bGVba2V5XSA9IHN0eWxlQXR0cmlidXRlc1trZXldOwogIH0KICByZXR1cm4gZWxlbWVudDsKfQoKLy8gTWF4IG51bWJlciBvZiBieXRlcyB3aGljaCB3aWxsIGJlIHVwbG9hZGVkIGF0IGEgdGltZS4KY29uc3QgTUFYX1BBWUxPQURfU0laRSA9IDEwMCAqIDEwMjQ7CgpmdW5jdGlvbiBfdXBsb2FkRmlsZXMoaW5wdXRJZCwgb3V0cHV0SWQpIHsKICBjb25zdCBzdGVwcyA9IHVwbG9hZEZpbGVzU3RlcChpbnB1dElkLCBvdXRwdXRJZCk7CiAgY29uc3Qgb3V0cHV0RWxlbWVudCA9IGRvY3VtZW50LmdldEVsZW1lbnRCeUlkKG91dHB1dElkKTsKICAvLyBDYWNoZSBzdGVwcyBvbiB0aGUgb3V0cHV0RWxlbWVudCB0byBtYWtlIGl0IGF2YWlsYWJsZSBmb3IgdGhlIG5leHQgY2FsbAogIC8vIHRvIHVwbG9hZEZpbGVzQ29udGludWUgZnJvbSBQeXRob24uCiAgb3V0cHV0RWxlbWVudC5zdGVwcyA9IHN0ZXBzOwoKICByZXR1cm4gX3VwbG9hZEZpbGVzQ29udGludWUob3V0cHV0SWQpOwp9CgovLyBUaGlzIGlzIHJvdWdobHkgYW4gYXN5bmMgZ2VuZXJhdG9yIChub3Qgc3VwcG9ydGVkIGluIHRoZSBicm93c2VyIHlldCksCi8vIHdoZXJlIHRoZXJlIGFyZSBtdWx0aXBsZSBhc3luY2hyb25vdXMgc3RlcHMgYW5kIHRoZSBQeXRob24gc2lkZSBpcyBnb2luZwovLyB0byBwb2xsIGZvciBjb21wbGV0aW9uIG9mIGVhY2ggc3RlcC4KLy8gVGhpcyB1c2VzIGEgUHJvbWlzZSB0byBibG9jayB0aGUgcHl0aG9uIHNpZGUgb24gY29tcGxldGlvbiBvZiBlYWNoIHN0ZXAsCi8vIHRoZW4gcGFzc2VzIHRoZSByZXN1bHQgb2YgdGhlIHByZXZpb3VzIHN0ZXAgYXMgdGhlIGlucHV0IHRvIHRoZSBuZXh0IHN0ZXAuCmZ1bmN0aW9uIF91cGxvYWRGaWxlc0NvbnRpbnVlKG91dHB1dElkKSB7CiAgY29uc3Qgb3V0cHV0RWxlbWVudCA9IGRvY3VtZW50LmdldEVsZW1lbnRCeUlkKG91dHB1dElkKTsKICBjb25zdCBzdGVwcyA9IG91dHB1dEVsZW1lbnQuc3RlcHM7CgogIGNvbnN0IG5leHQgPSBzdGVwcy5uZXh0KG91dHB1dEVsZW1lbnQubGFzdFByb21pc2VWYWx1ZSk7CiAgcmV0dXJuIFByb21pc2UucmVzb2x2ZShuZXh0LnZhbHVlLnByb21pc2UpLnRoZW4oKHZhbHVlKSA9PiB7CiAgICAvLyBDYWNoZSB0aGUgbGFzdCBwcm9taXNlIHZhbHVlIHRvIG1ha2UgaXQgYXZhaWxhYmxlIHRvIHRoZSBuZXh0CiAgICAvLyBzdGVwIG9mIHRoZSBnZW5lcmF0b3IuCiAgICBvdXRwdXRFbGVtZW50Lmxhc3RQcm9taXNlVmFsdWUgPSB2YWx1ZTsKICAgIHJldHVybiBuZXh0LnZhbHVlLnJlc3BvbnNlOwogIH0pOwp9CgovKioKICogR2VuZXJhdG9yIGZ1bmN0aW9uIHdoaWNoIGlzIGNhbGxlZCBiZXR3ZWVuIGVhY2ggYXN5bmMgc3RlcCBvZiB0aGUgdXBsb2FkCiAqIHByb2Nlc3MuCiAqIEBwYXJhbSB7c3RyaW5nfSBpbnB1dElkIEVsZW1lbnQgSUQgb2YgdGhlIGlucHV0IGZpbGUgcGlja2VyIGVsZW1lbnQuCiAqIEBwYXJhbSB7c3RyaW5nfSBvdXRwdXRJZCBFbGVtZW50IElEIG9mIHRoZSBvdXRwdXQgZGlzcGxheS4KICogQHJldHVybiB7IUl0ZXJhYmxlPCFPYmplY3Q+fSBJdGVyYWJsZSBvZiBuZXh0IHN0ZXBzLgogKi8KZnVuY3Rpb24qIHVwbG9hZEZpbGVzU3RlcChpbnB1dElkLCBvdXRwdXRJZCkgewogIGNvbnN0IGlucHV0RWxlbWVudCA9IGRvY3VtZW50LmdldEVsZW1lbnRCeUlkKGlucHV0SWQpOwogIGlucHV0RWxlbWVudC5kaXNhYmxlZCA9IGZhbHNlOwoKICBjb25zdCBvdXRwdXRFbGVtZW50ID0gZG9jdW1lbnQuZ2V0RWxlbWVudEJ5SWQob3V0cHV0SWQpOwogIG91dHB1dEVsZW1lbnQuaW5uZXJIVE1MID0gJyc7CgogIGNvbnN0IHBpY2tlZFByb21pc2UgPSBuZXcgUHJvbWlzZSgocmVzb2x2ZSkgPT4gewogICAgaW5wdXRFbGVtZW50LmFkZEV2ZW50TGlzdGVuZXIoJ2NoYW5nZScsIChlKSA9PiB7CiAgICAgIHJlc29sdmUoZS50YXJnZXQuZmlsZXMpOwogICAgfSk7CiAgfSk7CgogIGNvbnN0IGNhbmNlbCA9IGRvY3VtZW50LmNyZWF0ZUVsZW1lbnQoJ2J1dHRvbicpOwogIGlucHV0RWxlbWVudC5wYXJlbnRFbGVtZW50LmFwcGVuZENoaWxkKGNhbmNlbCk7CiAgY2FuY2VsLnRleHRDb250ZW50ID0gJ0NhbmNlbCB1cGxvYWQnOwogIGNvbnN0IGNhbmNlbFByb21pc2UgPSBuZXcgUHJvbWlzZSgocmVzb2x2ZSkgPT4gewogICAgY2FuY2VsLm9uY2xpY2sgPSAoKSA9PiB7CiAgICAgIHJlc29sdmUobnVsbCk7CiAgICB9OwogIH0pOwoKICAvLyBXYWl0IGZvciB0aGUgdXNlciB0byBwaWNrIHRoZSBmaWxlcy4KICBjb25zdCBmaWxlcyA9IHlpZWxkIHsKICAgIHByb21pc2U6IFByb21pc2UucmFjZShbcGlja2VkUHJvbWlzZSwgY2FuY2VsUHJvbWlzZV0pLAogICAgcmVzcG9uc2U6IHsKICAgICAgYWN0aW9uOiAnc3RhcnRpbmcnLAogICAgfQogIH07CgogIGNhbmNlbC5yZW1vdmUoKTsKCiAgLy8gRGlzYWJsZSB0aGUgaW5wdXQgZWxlbWVudCBzaW5jZSBmdXJ0aGVyIHBpY2tzIGFyZSBub3QgYWxsb3dlZC4KICBpbnB1dEVsZW1lbnQuZGlzYWJsZWQgPSB0cnVlOwoKICBpZiAoIWZpbGVzKSB7CiAgICByZXR1cm4gewogICAgICByZXNwb25zZTogewogICAgICAgIGFjdGlvbjogJ2NvbXBsZXRlJywKICAgICAgfQogICAgfTsKICB9CgogIGZvciAoY29uc3QgZmlsZSBvZiBmaWxlcykgewogICAgY29uc3QgbGkgPSBkb2N1bWVudC5jcmVhdGVFbGVtZW50KCdsaScpOwogICAgbGkuYXBwZW5kKHNwYW4oZmlsZS5uYW1lLCB7Zm9udFdlaWdodDogJ2JvbGQnfSkpOwogICAgbGkuYXBwZW5kKHNwYW4oCiAgICAgICAgYCgke2ZpbGUudHlwZSB8fCAnbi9hJ30pIC0gJHtmaWxlLnNpemV9IGJ5dGVzLCBgICsKICAgICAgICBgbGFzdCBtb2RpZmllZDogJHsKICAgICAgICAgICAgZmlsZS5sYXN0TW9kaWZpZWREYXRlID8gZmlsZS5sYXN0TW9kaWZpZWREYXRlLnRvTG9jYWxlRGF0ZVN0cmluZygpIDoKICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgJ24vYSd9IC0gYCkpOwogICAgY29uc3QgcGVyY2VudCA9IHNwYW4oJzAlIGRvbmUnKTsKICAgIGxpLmFwcGVuZENoaWxkKHBlcmNlbnQpOwoKICAgIG91dHB1dEVsZW1lbnQuYXBwZW5kQ2hpbGQobGkpOwoKICAgIGNvbnN0IGZpbGVEYXRhUHJvbWlzZSA9IG5ldyBQcm9taXNlKChyZXNvbHZlKSA9PiB7CiAgICAgIGNvbnN0IHJlYWRlciA9IG5ldyBGaWxlUmVhZGVyKCk7CiAgICAgIHJlYWRlci5vbmxvYWQgPSAoZSkgPT4gewogICAgICAgIHJlc29sdmUoZS50YXJnZXQucmVzdWx0KTsKICAgICAgfTsKICAgICAgcmVhZGVyLnJlYWRBc0FycmF5QnVmZmVyKGZpbGUpOwogICAgfSk7CiAgICAvLyBXYWl0IGZvciB0aGUgZGF0YSB0byBiZSByZWFkeS4KICAgIGxldCBmaWxlRGF0YSA9IHlpZWxkIHsKICAgICAgcHJvbWlzZTogZmlsZURhdGFQcm9taXNlLAogICAgICByZXNwb25zZTogewogICAgICAgIGFjdGlvbjogJ2NvbnRpbnVlJywKICAgICAgfQogICAgfTsKCiAgICAvLyBVc2UgYSBjaHVua2VkIHNlbmRpbmcgdG8gYXZvaWQgbWVzc2FnZSBzaXplIGxpbWl0cy4gU2VlIGIvNjIxMTU2NjAuCiAgICBsZXQgcG9zaXRpb24gPSAwOwogICAgZG8gewogICAgICBjb25zdCBsZW5ndGggPSBNYXRoLm1pbihmaWxlRGF0YS5ieXRlTGVuZ3RoIC0gcG9zaXRpb24sIE1BWF9QQVlMT0FEX1NJWkUpOwogICAgICBjb25zdCBjaHVuayA9IG5ldyBVaW50OEFycmF5KGZpbGVEYXRhLCBwb3NpdGlvbiwgbGVuZ3RoKTsKICAgICAgcG9zaXRpb24gKz0gbGVuZ3RoOwoKICAgICAgY29uc3QgYmFzZTY0ID0gYnRvYShTdHJpbmcuZnJvbUNoYXJDb2RlLmFwcGx5KG51bGwsIGNodW5rKSk7CiAgICAgIHlpZWxkIHsKICAgICAgICByZXNwb25zZTogewogICAgICAgICAgYWN0aW9uOiAnYXBwZW5kJywKICAgICAgICAgIGZpbGU6IGZpbGUubmFtZSwKICAgICAgICAgIGRhdGE6IGJhc2U2NCwKICAgICAgICB9LAogICAgICB9OwoKICAgICAgbGV0IHBlcmNlbnREb25lID0gZmlsZURhdGEuYnl0ZUxlbmd0aCA9PT0gMCA/CiAgICAgICAgICAxMDAgOgogICAgICAgICAgTWF0aC5yb3VuZCgocG9zaXRpb24gLyBmaWxlRGF0YS5ieXRlTGVuZ3RoKSAqIDEwMCk7CiAgICAgIHBlcmNlbnQudGV4dENvbnRlbnQgPSBgJHtwZXJjZW50RG9uZX0lIGRvbmVgOwoKICAgIH0gd2hpbGUgKHBvc2l0aW9uIDwgZmlsZURhdGEuYnl0ZUxlbmd0aCk7CiAgfQoKICAvLyBBbGwgZG9uZS4KICB5aWVsZCB7CiAgICByZXNwb25zZTogewogICAgICBhY3Rpb246ICdjb21wbGV0ZScsCiAgICB9CiAgfTsKfQoKc2NvcGUuZ29vZ2xlID0gc2NvcGUuZ29vZ2xlIHx8IHt9OwpzY29wZS5nb29nbGUuY29sYWIgPSBzY29wZS5nb29nbGUuY29sYWIgfHwge307CnNjb3BlLmdvb2dsZS5jb2xhYi5fZmlsZXMgPSB7CiAgX3VwbG9hZEZpbGVzLAogIF91cGxvYWRGaWxlc0NvbnRpbnVlLAp9Owp9KShzZWxmKTsK",
              "ok": true,
              "headers": [
                [
                  "content-type",
                  "application/javascript"
                ]
              ],
              "status": 200,
              "status_text": ""
            }
          },
          "base_uri": "https://localhost:8080/",
          "height": 91
        },
        "id": "VfPddO5je7Ni",
        "outputId": "d78dbc2b-e630-4a1f-fa61-6fcef0dde11e"
      },
      "source": [
        "from google.colab import files\n",
        "\n",
        "uploaded = files.upload()\n",
        "\n",
        "for fn in uploaded.keys():\n",
        "  print('User uploaded file \"{name}\" with length {length} bytes'.format(\n",
        "      name=fn, length=len(uploaded[fn])))\n",
        "  \n",
        "# Then move kaggle.json into the folder where the API expects to find it.\n",
        "!mkdir -p ~/.kaggle/ && mv kaggle.json ~/.kaggle/ && chmod 600 ~/.kaggle/kaggle.json"
      ],
      "execution_count": 2,
      "outputs": [
        {
          "output_type": "display_data",
          "data": {
            "text/html": [
              "\n",
              "     <input type=\"file\" id=\"files-33dc6701-78f2-4371-9351-a063fece5502\" name=\"files[]\" multiple disabled\n",
              "        style=\"border:none\" />\n",
              "     <output id=\"result-33dc6701-78f2-4371-9351-a063fece5502\">\n",
              "      Upload widget is only available when the cell has been executed in the\n",
              "      current browser session. Please rerun this cell to enable.\n",
              "      </output>\n",
              "      <script src=\"/nbextensions/google.colab/files.js\"></script> "
            ],
            "text/plain": [
              "<IPython.core.display.HTML object>"
            ]
          },
          "metadata": {
            "tags": []
          }
        },
        {
          "output_type": "stream",
          "text": [
            "Saving kaggle.json to kaggle.json\n",
            "User uploaded file \"kaggle.json\" with length 66 bytes\n"
          ],
          "name": "stdout"
        }
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "YxCi8apmgb0l"
      },
      "source": [
        "Una vez que colocamos el key en la celda anterior, ya se puede explorar el API, en nuestro caso, desde el _servicio_ de Datasets (aunque también puede usarse el de Competitions). Primero se consulta la lista de datasets y luego se escoge un dataset (en este caso cargaremos el de terremotos)."
      ]
    },
    {
      "cell_type": "code",
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "gl-jF-Cbe98A",
        "outputId": "9e6d6934-e955-4fb7-9314-68828ee7ab54"
      },
      "source": [
        "!kaggle datasets list"
      ],
      "execution_count": 3,
      "outputs": [
        {
          "output_type": "stream",
          "text": [
            "Warning: Looks like you're using an outdated API Version, please consider updating (server 1.5.12 / client 1.5.4)\n",
            "ref                                                         title                                              size  lastUpdated          downloadCount  \n",
            "----------------------------------------------------------  ------------------------------------------------  -----  -------------------  -------------  \n",
            "gpreda/reddit-vaccine-myths                                 Reddit Vaccine Myths                              234KB  2021-08-07 09:10:20          10344  \n",
            "crowww/a-large-scale-fish-dataset                           A Large Scale Fish Dataset                          3GB  2021-04-28 17:03:01           6326  \n",
            "imsparsh/musicnet-dataset                                   MusicNet Dataset                                   22GB  2021-02-18 14:12:19           2371  \n",
            "dhruvildave/wikibooks-dataset                               Wikibooks Dataset                                   2GB  2021-07-03 18:37:20           2589  \n",
            "promptcloud/careerbuilder-job-listing-2020                  Careerbuilder Job Listing 2020                     42MB  2021-03-05 06:59:52           1534  \n",
            "fatiimaezzahra/famous-iconic-women                          Famous Iconic Women                               838MB  2021-02-28 14:56:00           1077  \n",
            "alsgroup/end-als                                            End ALS Kaggle Challenge                           12GB  2021-04-08 12:16:37            825  \n",
            "mathurinache/twitter-edge-nodes                             Twitter Edge Nodes                                342MB  2021-03-08 06:43:04            726  \n",
            "nickuzmenkov/nih-chest-xrays-tfrecords                      NIH Chest X-rays TFRecords                         11GB  2021-03-09 04:49:23            880  \n",
            "simiotic/github-code-snippets                               GitHub Code Snippets                                7GB  2021-03-03 11:34:39            263  \n",
            "coloradokb/dandelionimages                                  DandelionImages                                     4GB  2021-02-19 20:03:47            708  \n",
            "imsparsh/accentdb-core-extended                             AccentDB - Core & Extended                          6GB  2021-02-17 14:22:54            127  \n",
            "stuartjames/lights                                          LightS: Light Specularity Dataset                  18GB  2021-02-18 14:32:26            107  \n",
            "mathurinache/the-lj-speech-dataset                          The LJ Speech Dataset                               3GB  2021-02-15 09:19:54            267  \n",
            "landrykezebou/lvzhdr-tone-mapping-benchmark-dataset-tmonet  LVZ-HDR Tone Mapping Benchmark Dataset (TMO-Net)   24GB  2021-03-01 05:03:40            164  \n",
            "nickuzmenkov/ranzcr-clip-kfold-tfrecords                    RANZCR CLiP KFold TFRecords                         2GB  2021-02-21 13:29:51            115  \n",
            "datasnaek/youtube-new                                       Trending YouTube Video Statistics                 201MB  2019-06-03 00:56:47         146134  \n",
            "zynicide/wine-reviews                                       Wine Reviews                                       51MB  2017-11-27 17:08:04         141487  \n",
            "residentmario/ramen-ratings                                 Ramen Ratings                                      40KB  2018-01-11 16:04:39          25549  \n",
            "datasnaek/chess                                             Chess Game Dataset (Lichess)                        3MB  2017-09-04 03:09:09          20513  \n"
          ],
          "name": "stdout"
        }
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "tscJCzlJiQ0j"
      },
      "source": [
        "El api code se consigue en la [página del dataset](https://www.kaggle.com/usgs/earthquake-database), en los tres puntos del menú de navegación (el menú que tiene las opciones de _Data_|_Tasks_|_Code_| etc.) hay una opción que dice _Copy API command_. Al dar click ahí se obtiene el siguiente comando:"
      ]
    },
    {
      "cell_type": "code",
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "f1YWnoU1fO6M",
        "outputId": "a47df153-995d-4500-bde1-5f7ac6ac6a18"
      },
      "source": [
        "!kaggle datasets download -d usgs/earthquake-database"
      ],
      "execution_count": 4,
      "outputs": [
        {
          "output_type": "stream",
          "text": [
            "Downloading earthquake-database.zip to /content\n",
            "\r  0% 0.00/590k [00:00<?, ?B/s]\n",
            "\r100% 590k/590k [00:00<00:00, 39.3MB/s]\n"
          ],
          "name": "stdout"
        }
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "0UueBEo1jiMh"
      },
      "source": [
        "Ahora se crea una carpeta para guardar la información del archivo que se descargó en la celda anterior. Ahí se descomprimirá el archivo."
      ]
    },
    {
      "cell_type": "code",
      "metadata": {
        "id": "45joW3oSjMN9"
      },
      "source": [
        "!mkdir postwork_6"
      ],
      "execution_count": 5,
      "outputs": []
    },
    {
      "cell_type": "code",
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "IZDh6WddjUKp",
        "outputId": "9038f3d0-a263-47e0-d33e-e4a41b8ef05b"
      },
      "source": [
        "!unzip earthquake-database.zip -d postwork_6"
      ],
      "execution_count": 6,
      "outputs": [
        {
          "output_type": "stream",
          "text": [
            "Archive:  earthquake-database.zip\n",
            "  inflating: postwork_6/database.csv  \n"
          ],
          "name": "stdout"
        }
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "vN2Wo3ZMjx5T"
      },
      "source": [
        "Por último, se puede leer el csv del archivo y replicar lo que se hizo hasta ahora en los otros Postworks"
      ]
    },
    {
      "cell_type": "code",
      "metadata": {
        "id": "ZglwhWtaj6Ze"
      },
      "source": [
        "import pandas as pd\n",
        "df_postwork_6 = pd.read_csv(\"/content/postwork_6/database.csv\")"
      ],
      "execution_count": 8,
      "outputs": []
    },
    {
      "cell_type": "code",
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 257
        },
        "id": "wGlJmwCgkgnI",
        "outputId": "2d9cbc24-b391-4aff-8b6d-93092462abe8"
      },
      "source": [
        "df_postwork_6.head()"
      ],
      "execution_count": 10,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "text/html": [
              "<div>\n",
              "<style scoped>\n",
              "    .dataframe tbody tr th:only-of-type {\n",
              "        vertical-align: middle;\n",
              "    }\n",
              "\n",
              "    .dataframe tbody tr th {\n",
              "        vertical-align: top;\n",
              "    }\n",
              "\n",
              "    .dataframe thead th {\n",
              "        text-align: right;\n",
              "    }\n",
              "</style>\n",
              "<table border=\"1\" class=\"dataframe\">\n",
              "  <thead>\n",
              "    <tr style=\"text-align: right;\">\n",
              "      <th></th>\n",
              "      <th>Date</th>\n",
              "      <th>Time</th>\n",
              "      <th>Latitude</th>\n",
              "      <th>Longitude</th>\n",
              "      <th>Type</th>\n",
              "      <th>Depth</th>\n",
              "      <th>Depth Error</th>\n",
              "      <th>Depth Seismic Stations</th>\n",
              "      <th>Magnitude</th>\n",
              "      <th>Magnitude Type</th>\n",
              "      <th>Magnitude Error</th>\n",
              "      <th>Magnitude Seismic Stations</th>\n",
              "      <th>Azimuthal Gap</th>\n",
              "      <th>Horizontal Distance</th>\n",
              "      <th>Horizontal Error</th>\n",
              "      <th>Root Mean Square</th>\n",
              "      <th>ID</th>\n",
              "      <th>Source</th>\n",
              "      <th>Location Source</th>\n",
              "      <th>Magnitude Source</th>\n",
              "      <th>Status</th>\n",
              "    </tr>\n",
              "  </thead>\n",
              "  <tbody>\n",
              "    <tr>\n",
              "      <th>0</th>\n",
              "      <td>01/02/1965</td>\n",
              "      <td>13:44:18</td>\n",
              "      <td>19.246</td>\n",
              "      <td>145.616</td>\n",
              "      <td>Earthquake</td>\n",
              "      <td>131.6</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>6.0</td>\n",
              "      <td>MW</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>ISCGEM860706</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>Automatic</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>1</th>\n",
              "      <td>01/04/1965</td>\n",
              "      <td>11:29:49</td>\n",
              "      <td>1.863</td>\n",
              "      <td>127.352</td>\n",
              "      <td>Earthquake</td>\n",
              "      <td>80.0</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>5.8</td>\n",
              "      <td>MW</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>ISCGEM860737</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>Automatic</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>2</th>\n",
              "      <td>01/05/1965</td>\n",
              "      <td>18:05:58</td>\n",
              "      <td>-20.579</td>\n",
              "      <td>-173.972</td>\n",
              "      <td>Earthquake</td>\n",
              "      <td>20.0</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>6.2</td>\n",
              "      <td>MW</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>ISCGEM860762</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>Automatic</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>3</th>\n",
              "      <td>01/08/1965</td>\n",
              "      <td>18:49:43</td>\n",
              "      <td>-59.076</td>\n",
              "      <td>-23.557</td>\n",
              "      <td>Earthquake</td>\n",
              "      <td>15.0</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>5.8</td>\n",
              "      <td>MW</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>ISCGEM860856</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>Automatic</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>4</th>\n",
              "      <td>01/09/1965</td>\n",
              "      <td>13:32:50</td>\n",
              "      <td>11.938</td>\n",
              "      <td>126.427</td>\n",
              "      <td>Earthquake</td>\n",
              "      <td>15.0</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>5.8</td>\n",
              "      <td>MW</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>NaN</td>\n",
              "      <td>ISCGEM860890</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>ISCGEM</td>\n",
              "      <td>Automatic</td>\n",
              "    </tr>\n",
              "  </tbody>\n",
              "</table>\n",
              "</div>"
            ],
            "text/plain": [
              "         Date      Time  Latitude  ...  Location Source Magnitude Source     Status\n",
              "0  01/02/1965  13:44:18    19.246  ...           ISCGEM           ISCGEM  Automatic\n",
              "1  01/04/1965  11:29:49     1.863  ...           ISCGEM           ISCGEM  Automatic\n",
              "2  01/05/1965  18:05:58   -20.579  ...           ISCGEM           ISCGEM  Automatic\n",
              "3  01/08/1965  18:49:43   -59.076  ...           ISCGEM           ISCGEM  Automatic\n",
              "4  01/09/1965  13:32:50    11.938  ...           ISCGEM           ISCGEM  Automatic\n",
              "\n",
              "[5 rows x 21 columns]"
            ]
          },
          "metadata": {
            "tags": []
          },
          "execution_count": 10
        }
      ]
    },
    {
      "cell_type": "code",
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "tOGwqff4kAQk",
        "outputId": "37c6a51a-d974-4786-c853-856ac3df399b"
      },
      "source": [
        "df_postwork_6.info()"
      ],
      "execution_count": 9,
      "outputs": [
        {
          "output_type": "stream",
          "text": [
            "<class 'pandas.core.frame.DataFrame'>\n",
            "RangeIndex: 23412 entries, 0 to 23411\n",
            "Data columns (total 21 columns):\n",
            " #   Column                      Non-Null Count  Dtype  \n",
            "---  ------                      --------------  -----  \n",
            " 0   Date                        23412 non-null  object \n",
            " 1   Time                        23412 non-null  object \n",
            " 2   Latitude                    23412 non-null  float64\n",
            " 3   Longitude                   23412 non-null  float64\n",
            " 4   Type                        23412 non-null  object \n",
            " 5   Depth                       23412 non-null  float64\n",
            " 6   Depth Error                 4461 non-null   float64\n",
            " 7   Depth Seismic Stations      7097 non-null   float64\n",
            " 8   Magnitude                   23412 non-null  float64\n",
            " 9   Magnitude Type              23409 non-null  object \n",
            " 10  Magnitude Error             327 non-null    float64\n",
            " 11  Magnitude Seismic Stations  2564 non-null   float64\n",
            " 12  Azimuthal Gap               7299 non-null   float64\n",
            " 13  Horizontal Distance         1604 non-null   float64\n",
            " 14  Horizontal Error            1156 non-null   float64\n",
            " 15  Root Mean Square            17352 non-null  float64\n",
            " 16  ID                          23412 non-null  object \n",
            " 17  Source                      23412 non-null  object \n",
            " 18  Location Source             23412 non-null  object \n",
            " 19  Magnitude Source            23412 non-null  object \n",
            " 20  Status                      23412 non-null  object \n",
            "dtypes: float64(12), object(9)\n",
            "memory usage: 3.8+ MB\n"
          ],
          "name": "stdout"
        }
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "d_3SP-yZeHYD"
      },
      "source": [
        "##Postwork 7: Transformación, filtración y ordenamiento de datos"
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "6_Je5zIvKkDo"
      },
      "source": [
        "- Utilizar transformaciones de datos para limpiar y preparar un dataset para análisis.\n",
        "- Realizar filtraciones para obtener conjuntos de datos.\n",
        "- Reordenar datos para ver el conjunto desde diferentes perspectivas."
      ]
    },
    {
      "cell_type": "code",
      "metadata": {
        "id": "cAGbxQ7peRZz"
      },
      "source": [
        ""
      ],
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "KM60Oz3UeIMd"
      },
      "source": [
        "##Postwork 8: Preparándose para las siguientes fases"
      ]
    },
    {
      "cell_type": "code",
      "metadata": {
        "id": "QkQlJT9eeZPF"
      },
      "source": [
        ""
      ],
      "execution_count": null,
      "outputs": []
    }
  ]
}