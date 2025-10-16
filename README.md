<img src="https://github.com/hernancontigiani/ceia_memorias_especializacion/raw/master/Figures/logoFIUBA.jpg" width="500" align="center">

# CEIA - Procesamiento de Lenguaje Natural I

## Descripción
Este repositorio contiene las soluciones a los desafíos de la asignatura **Procesamiento de Lenguaje Natural I**, correspondiente a la Carrera de Especialización en Inteligencia Artificial de la Universidad de Buenos Aires (UBA). El objetivo de la materia es abordar problemas relacionados con el procesamiento y análisis de texto mediante técnicas de inteligencia artificial y aprendizaje automático.

En este repositorio se incluyen los cuatro desafíos propuestos en la asignatura, cada uno enfocado en diferentes aspectos fundamentales del procesamiento de lenguaje natural.

## Autor
- **Agustín López Fredes**

## Estructura del Repositorio

### Desafío 1: Vectorización y Clasificación de Texto
- **Archivo**: [`Desafio_1.ipynb`](Desafio_1/Desafio_1.ipynb)
- **Enfoque**: Vectorización de documentos, similaridad de coseno y clasificadores básicos
- **Técnicas**: TF-IDF, Naive Bayes (MultinomialNB y ComplementNB), clasificación por prototipos
- **Dataset**: 20 Newsgroups
- **Principales Conclusiones**:
  - La optimización de hiperparámetros mejoró significativamente el F1-score de 58% a 70.5%
  - ComplementNB superó a MultinomialNB para datos desbalanceados
  - La clasificación por prototipos (zero-shot) obtuvo menor performance (50.5% F1-score)
  - TF-IDF con bigramas y filtrado de términos raros mejoró la calidad de las representaciones

### Desafío 2: Embeddings Personalizados con Word2Vec
- **Archivo**: [`Desafio_2.ipynb`](Desafio_2/Desafio_2.ipynb)
- **Enfoque**: Entrenamiento de embeddings mediante Skipgram y CBOW
- **Técnicas**: Word2Vec, t-SNE para visualización, análisis de similitud semántica
- **Dataset**: Novelas de "A Song of Ice and Fire" de George R.R. Martin
- **Principales Conclusiones**:
  - **Skipgram** captura mejor relaciones específicas y términos raros (ideal para análisis narrativo detallado)
  - **CBOW** generaliza mejor y refleja temas recurrentes (visión global de temas)
  - Ambos modelos reflejaron correctamente relaciones familiares y características distintivas de personajes
  - El preprocesamiento es fundamental: eliminación de stopwords, normalización y filtrado de artefactos

### Desafío 3: Modelos de Lenguaje con RNNs
- **Archivo**: [`Desafio_3.ipynb`](Desafio_3/Desafio_3.ipynb)
- **Enfoque**: Generación de secuencias con redes neuronales recurrentes, utilizando tokenización por caracteres
- **Técnicas**: RNN, LSTM, GRU, Perplexity, estrategias de generación Greedy, Beam Search determinístico, Beam Search con sampleo estocástico
- **Dataset**: "A Game of Thrones" (primer libro de la saga)
- **Principales Conclusiones**:
  - **GRU** obtuvo mejor performance que RNN simple y LSTM para generación de texto
  - **Adam** converge más rápido pero genera overfitting; RMSProp es más estable
  - **Beam Search** (determinístico y estocástico T=1) supera significativamente a Greedy Search
  - La temperatura en muestreo estocástico afecta dramáticamente la calidad: T<1 → repetitivo, T>1 → aleatorio
  - La complejidad del modelo (2 capas) no mejoró significativamente la performance

### Desafío 4: Traducción Secuencia a Secuencia
- **Archivo**: [`Desafio_4.ipynb`](Desafio_4/Desafio_4.ipynb)
- **Enfoque**: Modelos de traducción español-inglés con arquitecturas encoder-decoder
- **Técnicas**: LSTM bidireccional, mecanismos de atención, embeddings pre-entrenados (GloVe)
- **Dataset**: spa-eng (Spanish-English translation pairs)
- **Principales Conclusiones**:
  - **Aumentar el contexto** (tamaño de secuencias) fue clave para mejorar la traducción
  - **LSTM bidireccional** mejoró marginalmente la captura de contexto
  - **Mecanismos de atención** mejoraron la calidad de traducción pero con overfitting significativo
  - Los embeddings pre-entrenados (GloVe) fueron más efectivos que embeddings entrenables
  - La métrica de Accuracy no fue adecuada; se recomienda BLEU para evaluación de traducción

## Conclusiones Generales del Curso

### Aspectos Técnicos Fundamentales
1. **Preprocesamiento**: Es crucial para la calidad de los modelos de NLP. La limpieza de datos, normalización y filtrado de artefactos impactan directamente en el rendimiento.

2. **Selección de Arquitecturas**: 
   - Para clasificación de texto: ComplementNB con optimización de hiperparámetros
   - Para embeddings semánticos: Skipgram para detalles específicos, CBOW para temas generales
   - Para generación de texto: GRU con Beam Search
   - Para traducción: Encoder-Decoder con atención y contexto amplio

3. **Optimización y Regularización**:
   - La optimización de hiperparámetros puede mejorar significativamente el rendimiento
   - El dropout y early stopping son esenciales para evitar overfitting
   - RMSProp demostró ser más estable que Adam para tareas de generación de texto

### Metodologías de Evaluación
- **F1-score macro** para clasificación multiclase desbalanceada
- **Perplexity** para evaluación de modelos de lenguaje
- **Análisis cualitativo** complementa las métricas cuantitativas

### Desafíos y Limitaciones Identificadas
1. **Overfitting**: Especialmente crítico en modelos complejos con datasets pequeños
2. **Métricas inadecuadas**: La elección de métricas impacta la evaluación del modelo (por ejemplo utilizar BLEU para traducción)
3. **Balance entre complejidad y datos**: Modelos más complejos requieren más datos de entrenamiento
4. **Generalización**: Los modelos tienden a memorizar patrones de entrenamiento

### Recomendaciones para Futuros Trabajos
1. **Datos**: Priorizar la calidad y cantidad de datos sobre la complejidad del modelo
2. **Validación**: Implementar validación cruzada y conjuntos de prueba robustos
3. **Métricas**: Seleccionar métricas específicas para cada tarea de NLP
4. **Iteración**: Comenzar con modelos simples y aumentar complejidad gradualmente
5. **Análisis**: Combinar evaluación cuantitativa con análisis cualitativo de resultados

## Tecnologías Utilizadas
- **Python 3.x**
- **TensorFlow/Keras** para redes neuronales
- **scikit-learn** para clasificadores tradicionales
- **Gensim** para Word2Vec
- **NLTK** para preprocesamiento de texto
- **Optuna** para optimización de hiperparámetros
- **Plotly** para visualizaciones interactivas