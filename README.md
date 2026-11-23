# 🔍 Investigación y Desarrollo sobre Algoritmos de Clustering


Deben investigar cómo funcionan los algoritmos de clustering, sus principales tipos,
ventajas, desventajas y aplicaciones en el mundo real.

## Parte 1: Algoritmos No Supervisados de Clustering.

Cada estudiante debe investigar y responder las siguientes preguntas de forma detallada:
1. *¿Qué es el aprendizaje no supervisado y qué es un algoritmo de clustering? ¿En qué se
diferencia del aprendizaje supervisado y cuál es su propósito?*

    > **Aprendizaje no supervisado** es un tipo de Machine Learning en el que entrenamos un modelo utilizando datos sin etiquetas ni respuestas previamente definidas. Le damos muchos datos al algoritmo y le pedimos que encuentre patrones, relaciones o estructuras por sí mismo.
    
    Un **algoritmo de clustering** es una técnica de aprendizaje no supervisado que consiste en agrupar datos que tienen características similares para encontrar patrones en ellos.
    
    Esa falta de etiqueta o respuesta definida es el la diferencia con el aprendizaje supervisado (qui si tiene). Sirve a encontrar patrones de clasificacion donde no habia previamente.

2. *Explique la diferencia conceptual entre el clustering basado en centroides (particional) y el clustering jerárquico, mencionando un algoritmo representativo de cada enfoque.*

    > La diferencia conceptual principal está en cómo se forman los grupos y cómo se organiza el resultado.

    El **clustering basado en centroides** divide directamente el conjunto de datos en un número determinado de grupos (clusters).
    El algoritmo busca agrupar los datos de manera que los elementos de un mismo grupo sean lo más similares posible.
    
    Algoritmo representativo: **K-Means**.

        1. Elegimos el número de grupos (K).

        2. El algoritmo calcula un centro para cada grupo (centroide).
        
        3. Asigna cada dato al centroide más cercano.
        
        4. Recalcula los centroides y repite el proceso hasta estabilizar los grupos.

    En el **Clustering jerárquico** los grupos se construyen progresivamente, creando una estructura de agrupaciones en diferentes niveles.
    
    En lugar de obtener directamente K grupos, el algoritmo construye una jerarquía que podemos representar mediante un árbol llamado dendrograma.
    
    Existen dos enfoques:

        - Aglomerativo (bottom-up): empieza con cada dato como un grupo individual y va fusionando los grupos más similares.

        - Divisivo (top-down): empieza con todos los datos en un único grupo y los va dividiendo progresivamente.

3. *¿En qué consiste el clustering basado en densidad (como DBSCAN) y cómo difiere su
enfoque del clustering basado en centroides y del jerárquico?*

    > El **clustering basado en densidad** es un método de aprendizaje no supervisado que agrupa datos según la concentración de puntos que existen en una zona determinada.
    
    Su principal diferencia respecto a K-Means y al clustering jerárquico es que no busca centros ni construye necesariamente una jerarquía: busca regiones donde los datos están densamente concentrados y las separa de las zonas con pocos puntos.

4. *¿Por qué es importante elegir correctamente el número de clusters o los hiperparámetros
de un algoritmo de clustering? Explica al menos dos métodos para evaluar la calidad de un
agrupamiento (por ejemplo, el método del codo y el coeficiente de silueta).*

    > Elegir correctamente el número de clusters o los hiperparámetros determina cómo se agrupan los datos y, por tanto, la calidad y utilidad de los resultados obtenidos.
    Si elegimos valores inadecuados, podemos obtener agrupamientos que no representan correctamente la estructura real de los datos.
    El objetivo es encontrar un equilibrio: grupos suficientemente diferenciados entre sí y suficientemente similares internamente.

    **Método del codo (Elbow Method)**

    Encontrar un valor adecuado de K analizando cómo disminuye la variación interna de los grupos cuando aumentamos el número de clusters. Se llama asi porque buscamos un punto parecido al codo de un brazo: antes de ese punto, aumentar K mejora considerablemente el agrupamiento; después, la mejora es mucho menor.

    **Coeficiente de silueta(Silhouette Score)**

    Evalúa cómo de bien está asignado cada punto a su propio cluster comparándolo con los clusters vecinos.
    Tiene en cuenta dos aspectos:

        - Cohesión: qué tan cerca está un punto de los demás elementos de su propio cluster.

        - Separación: qué tan lejos está de los puntos del cluster más cercano al que no pertenece.

        Valor cercano a +1 : Los puntos están bien agrupados y claramente separados de otros clusters.

        Valor cercano a 0 : Los clusters se solapan o los puntos están cerca de la frontera entre dos grupos.

        Valor cercano a -1 : Algunos puntos probablemente están asignados al cluster equivocado.

5. *Explica brevemente los siguientes algoritmos:*

● K-Means

● Clustering Jerárquico (Aglomerativo)

● DBSCAN

● Gaussian Mixture Models (GMM)

*Para cada uno, incluye una breve descripción del mecanismo, ventajas, desventajas y
casos de uso comunes.*

### 1. K-Means

**Mecanismo**

K-Means es un algoritmo de clustering basado en centroides que divide un conjunto de datos en un número determinado de grupos (K).

**Funcionamiento**

    - Elegir el número de clusters (K).

    - Inicializar K centroides.

    - Asignar cada punto al centroide más cercano.

    - Recalcular los centroides según los puntos asignados.

    - Repetir el proceso hasta que los grupos se estabilicen.

**Objetivo**

Minimizar la distancia entre los puntos y el centroide de su propio cluster (WCSS).

**Ventajas**

Es sencillo de implementar y relativamente rápido.

Funciona bien con conjuntos de datos grandes.

Permite identificar grupos de manera eficiente.

**Desventajas**

Es necesario definir previamente el número de clusters (K).

Es sensible a la inicialización de los centroides y a los valores atípicos (outliers).

Funciona mejor con grupos compactos y aproximadamente esféricos.

Puede ofrecer resultados poco adecuados cuando los grupos tienen formas o densidades muy diferentes.

**Casos de uso comunes**

Segmentación de clientes según sus hábitos de compra.

Agrupación de productos según sus características.

Compresión y cuantización de imágenes.

Identificación de patrones de comportamiento.

---

### 2. Clustering Jerárquico (Aglomerativo)

**Mecanismo**

El clustering jerárquico aglomerativo es un algoritmo de aprendizaje no supervisado que construye grupos progresivamente, empezando con cada dato como un cluster individual.

**Funcionamiento**

- Inicializar un cluster para cada punto.
- Calcular las distancias entre los clusters.
- Fusionar los dos clusters más cercanos.
- Repetir el proceso hasta que todos los puntos formen un único cluster o se alcance el criterio de parada.

El resultado se representa mediante un árbol llamado dendrograma, que permite visualizar cómo se relacionan y fusionan los grupos a diferentes niveles.

La distancia entre clusters depende del método de enlace (*linkage*), como Single, Complete, Average o Ward.

**Objetivo**

Construir una estructura jerárquica de agrupaciones que permita identificar relaciones y similitudes entre los datos a diferentes niveles.

**Ventajas**

- No requiere definir previamente el número de clusters.
- Permite visualizar las relaciones jerárquicas entre los datos.
- Ofrece diferentes criterios de agrupamiento mediante los métodos de enlace.
- Puede identificar estructuras de agrupación a diferentes niveles.

**Desventajas**

- Puede ser costoso computacionalmente con grandes conjuntos de datos.
- Las fusiones realizadas no suelen poder deshacerse.
- Los resultados pueden variar según el método de enlace y la métrica de distancia elegidos.
- Puede ser sensible al ruido y a los valores atípicos.

**Casos de uso comunes**

- Agrupación de documentos según su contenido.
- Clasificación de especies según características similares.
- Análisis de relaciones entre productos o clientes.
- Estudios de similitud genética.

---

### 3. DBSCAN (Density-Based Spatial Clustering of Applications with Noise)

**Mecanismo**

DBSCAN es un algoritmo de clustering basado en densidad que identifica grupos de datos según la concentración de puntos en determinadas regiones.

**Funcionamiento**

Utiliza dos parámetros principales:

- **Epsilon (ε):** define el radio de proximidad para considerar dos puntos vecinos.
- **MinPts:** establece el número mínimo de puntos necesarios dentro de ese radio para considerar que una región tiene suficiente densidad.

El algoritmo identifica tres tipos de puntos:

- **Core Point:** tiene suficientes puntos vecinos dentro de su radio.
- **Border Point:** no tiene suficientes vecinos para ser un punto núcleo, pero pertenece a la región de uno.
- **Noise Point:** no pertenece a ningún grupo y se considera ruido u outlier.

A partir de los puntos núcleo, el algoritmo va expandiendo los clusters incorporando los puntos conectados por densidad.

**Objetivo**

Identificar grupos de datos basándose en regiones de alta densidad y detectar automáticamente los puntos aislados o considerados ruido.

**Ventajas**

- No requiere definir previamente el número de clusters.
- Puede detectar grupos de formas irregulares.
- Identifica automáticamente puntos aislados y valores atípicos.
- No depende de centroides para formar los grupos.

**Desventajas**

- Es sensible a la elección de los parámetros Epsilon y MinPts.
- Puede tener dificultades cuando los datos presentan clusters con densidades muy diferentes.
- La elección de la distancia adecuada puede ser complicada en conjuntos de datos con muchas dimensiones.
- Los resultados pueden variar considerablemente según los parámetros utilizados.

**Casos de uso comunes**

- Detección de zonas geográficas con alta concentración de actividad.
- Identificación de transacciones o comportamientos anómalos.
- Análisis de datos espaciales y geográficos.
- Detección de patrones en datos de sensores.

---

### 4. Gaussian Mixture Models (GMM)

**Mecanismo**

Gaussian Mixture Models (GMM) es un modelo probabilístico que representa los datos como una combinación de varias distribuciones gaussianas (distribuciones normales).

Cada distribución representa un posible cluster y se caracteriza por su media, covarianza y peso dentro del modelo.

**Funcionamiento**

El algoritmo utiliza habitualmente el método **Expectation-Maximization (EM)** para estimar los parámetros de las distribuciones.

- Inicializar los parámetros de las distribuciones gaussianas.
- **Expectation (E):** calcular la probabilidad de que cada punto pertenezca a cada cluster.
- **Maximization (M):** actualizar los parámetros de las distribuciones según esas probabilidades.
- Repetir ambos pasos hasta que el modelo converja.

A diferencia de K-Means, GMM utiliza una asignación probabilística o *soft clustering*: cada punto puede pertenecer a varios clusters con diferentes probabilidades.

**Objetivo**

Modelar la distribución de los datos mediante una combinación de distribuciones gaussianas y calcular la probabilidad de pertenencia de cada punto a los diferentes clusters.

**Ventajas**

- Permite asignar probabilidades de pertenencia a cada cluster.
- Puede identificar grupos con formas elípticas y diferentes orientaciones.
- Es más flexible que K-Means para representar distribuciones de datos solapadas.
- Proporciona información sobre la incertidumbre de las asignaciones.

**Desventajas**

- Es necesario definir previamente el número de componentes gaussianos.
- Puede ser sensible a la inicialización de los parámetros.
- El proceso de entrenamiento puede ser más costoso computacionalmente que K-Means.
- Supone que los datos pueden representarse mediante una mezcla de distribuciones gaussianas, por lo que no es adecuado para cualquier estructura de datos.
- Puede converger a soluciones locales que no sean óptimas.

**Casos de uso comunes**

- Segmentación de clientes según patrones de comportamiento.
- Reconocimiento de patrones y procesamiento de imágenes.
- Detección de anomalías.
- Modelización de distribuciones de datos.
- Agrupación de datos con clusters solapados.

---




