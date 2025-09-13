🧠 Sistema de Reconocimiento de Emociones Faciales con FER2013
Este proyecto implementa un modelo de Deep Learning para clasificar emociones faciales en siete categorías (enojo, disgusto, miedo, felicidad, tristeza, sorpresa, neutral) utilizando el dataset FER2013. El modelo se construye en Python con TensorFlow/Keras y está diseñado para ejecutarse en un entorno de Google Colab.
Para lograr un entrenamiento eficiente y un alto rendimiento, se utiliza una técnica de Aprendizaje por Transferencia (Transfer Learning) con la arquitectura MobileNetV2, junto con una estrategia de pesos de clase para manejar el desbalance del dataset.

✨ Características
●	Clasificación de 7 emociones faciales a partir de imágenes estáticas.
●	Modelo Basado en Transfer Learning: Utiliza MobileNetV2 pre-entrenado para un entrenamiento más rápido y preciso.
●	Optimizado para Google Colab: Facilita el acceso a aceleradores de hardware como GPUs.
●	Aumento de Datos: Aplica transformaciones a las imágenes de entrenamiento para mejorar la robustez y reducir el sobreajuste.
●	Manejo de Desbalance de Clases: Implementa class_weight para asegurar que el modelo preste atención a las emociones con menos muestras.
●	Interfaz Interactiva: Permite probar el modelo entrenado con imágenes propias directamente en el notebook.

📋 Requisitos Previos
●	Una cuenta de Google para usar Google Drive y Google Colab.
●	El dataset FER2013, que se puede descargar desde Kaggle: Dataset FER2013.

🛠️ Configuración del Entorno
Sigue estos pasos para preparar tu entorno de trabajo antes de ejecutar el notebook.
1. Organizar los Archivos en Google Drive
El notebook está configurado para leer el dataset desde una ruta específica en tu Google Drive. Debes crear la siguiente estructura de carpetas y colocar tus archivos en ella:
/content/drive/MyDrive/
└── Colab Notebooks/
    └── PROYECTO_FER_2013/
        ├── emotion_recognition.ipynb  <-- Tu notebook de Colab
        └── FER2013/
            ├── test/
            │   ├── angry/
            │   ├── disgust/
            │   ├── fear/
            │   ├── happy/
            │   ├── neutral/
            │   ├── sad/
            │   └── surprise/
            └── train/
                ├── angry/
                ├── disgust/
                ├── fear/
                ├── happy/
                ├── neutral/
                ├── sad/
                └── surprise/

Nota: Si utilizas una ruta diferente, asegúrate de actualizar la variable source_path en la Celda 2 del notebook.
2. Abrir el Notebook en Google Colab
Sube el archivo emotion_recognition.ipynb a la carpeta PROYECTO_FER_2013 en tu Google Drive y ábrelo con Google Colab.

🚀 Cómo Entrenar y Probar el Modelo
El proceso se divide en dos fases principales dentro del notebook.

Fase 1: Entrenamiento del Modelo
1.	Seleccionar un Entorno de Ejecución con GPU:
○	En el menú de Colab, ve a Entorno de ejecución > Cambiar tipo de entorno de ejecución.
○	En el desplegable "Acelerador de hardware", selecciona T4 GPU. Esto es crucial para un entrenamiento rápido.
2.	Ejecutar Todas las Celdas en Orden:
○	La forma más sencilla es ir al menú y seleccionar Entorno de ejecución > Ejecutar todas.
○	El notebook realizará los siguientes pasos de forma secuencial:
1.	Importará todas las librerías necesarias.
2.	Montará tu Google Drive y copiará el dataset al entorno local de Colab para mayor velocidad.
3.	Analizará y visualizará la distribución de los datos.
4.	Configurará los generadores de datos (ImageDataGenerator), aplicando aumento de datos a las imágenes de entrenamiento.
5.	Construirá el modelo MobileNetV2 utilizando Transfer Learning.
6.	Calculará los pesos de clase para manejar el desbalance.
7.	Iniciará el proceso de entrenamiento. Verás el progreso (precisión y pérdida) en la salida de la celda.
3.	Resultado del Entrenamiento:
○	Durante el entrenamiento, el callback ModelCheckpoint guardará automáticamente la mejor versión del modelo en un archivo llamado best_emotion_model.h5.
○	Al finalizar, se mostrarán gráficos con la evolución de la precisión y la pérdida.

Fase 2: Prueba Interactiva con Imágenes Propias
Una vez que el entrenamiento ha concluido, puedes usar la interfaz interactiva para evaluar el rendimiento del modelo en imágenes que no pertenecen al dataset.
1.	Ejecuta la Celda de la Interfaz Interactiva:
○	Navega hasta la última celda del notebook, titulada "Interfaz Interactiva para Probar con Imágenes Propias", y ejecútala.
2.	Sube una Imagen:
○	Aparecerá un botón para "Elegir archivos". Haz clic y selecciona un archivo de imagen (JPG, PNG, etc.) desde tu computadora.
3.	Analiza los Resultados:
○	El modelo procesará la imagen y mostrará:
■	La imagen de entrada con la emoción predicha y el porcentaje de confianza.
■	Un gráfico de barras que detalla la distribución de probabilidad para cada una de las 7 emociones.
4.	Realiza Múltiples Pruebas:
○	El script te preguntará si deseas analizar otra imagen. Puedes repetir el proceso tantas veces como quieras para probar diferentes caras y expresiones.

🏗️ Tecnologías Utilizadas
●	Python 3
●	Google Colab
●	TensorFlow / Keras: Framework principal para la construcción y entrenamiento del modelo.
●	Scikit-learn: Utilizado para calcular los pesos de clase (class_weight).
●	OpenCV: Para el preprocesamiento de las imágenes subidas en la interfaz interactiva.
●	NumPy: Para operaciones numéricas eficientes.
●	Matplotlib: Para la visualización de datos y resultados del entrenamiento.
