# Trabajo Práctico Integrador - Visión por Computadora II

Este repositorio contiene el desarrollo del Trabajo Práctico Integrador para el curso de Visión por Computadora II, perteneciente a la Especialización en Inteligencia Artificial (CEIA) de la Facultad de Ingeniería de la Universidad de Buenos Aires (FIUBA). El objetivo principal de este trabajo es analizar y desarrollar distintos modelos de visión por computadora para detectar diversas afecciones dentales en radiografías panorámicas, tales como dientes impactados, endodoncia, caries, entre otras patologías.

Integrantes:
- Marco Joel Isidro (marcojoelisidro@gmail.com)
- Diego Sarina (sarinadiego@gmail.com)

Estructura del Repositorio:

```
├── notebooks/                    # Notebooks con los experimentos y análisis
│   ├── EDA.ipynb                 # Análisis exploratorio de datos
│   ├── YOLOv8_training.ipynb      # Entrenamiento de YOLOv8
│   ├── RetinaNet_training.ipynb   # Entrenamiento de RetinaNet
│   ├── FasterRCNN_training.ipynb  # Entrenamiento de Faster R-CNN
├── results/                      # Gráficas y métricas obtenidas de los experimentos
│   ├── yolo_results/             # Resultados del entrenamiento YOLOv8
│   ├── retina_results/           # Resultados del entrenamiento RetinaNet
│   ├── faster_rcnn_results/      # Resultados del entrenamiento Faster R-CNN
├── slides/                       # Diapositivas de la presentación final
│   └── Presentacion_TP.pptx      
├── src/                          # Código fuente del proyecto
│   ├── augmentation.py           # Implementaciones de data augmentation
│   ├── train.py                  # Script de entrenamiento común
│   └── utils/                    # Utilidades para la gestión del dataset y métricas
├── poetry.env              # Lista de dependencias del proyecto
└── README.md                     # Este archivo
```

# Descripción del Proyecto

El objetivo de este proyecto es resolver una tarea de detección de objetos utilizando varios modelos de visión por computadora. El dataset seleccionado para este trabajo contiene imágenes de [descripción del dataset, e.g., radiografías dentales anotadas con distintas patologías] y busca identificar [problemas como caries, dientes impactados, lesiones, etc.].

## Dataset

- **Nombre del dataset**: [Especificar el nombre o fuente]
- **Descripción**: Este dataset contiene imágenes de [descripción del dataset], anotadas con etiquetas de objetos para resolver una tarea de detección de objetos.
- **Formato**: COCO / Pascal VOC / etc.

## Tareas de Visión por Computadora

- **Detección de objetos**: Se abordará el problema de detección de [clases de objetos a detectar, e.g., enfermedades dentales] en imágenes.

## Análisis Exploratorio de Datos (EDA)

Se realizó un análisis exploratorio para entender la distribución del dataset, las clases a predecir, y la calidad de las anotaciones. Este análisis está documentado en el notebook `EDA.ipynb`.

### Visualización de datos

- **Distribución de clases**
- **Tamaño y resolución de las imágenes**
- **Ejemplos de imágenes anotadas**

## Modelos Utilizados

Entrenamos al menos 4 modelos diferentes para abordar el problema de detección de objetos:

- **YOLOv8**: Un modelo de detección de objetos eficiente y rápido.
- **RetinaNet**: Un modelo diseñado para manejar la detección de objetos con un fuerte enfoque en objetos pequeños y medianos.
- **Faster R-CNN**: Un modelo más robusto que ofrece alta precisión en la detección de objetos.
- **[Otro modelo]**: Por ejemplo, EfficientDet o SSD para comparar desempeño.

Cada modelo fue entrenado con distintos hiperparámetros y configuraciones que se detallan en los notebooks correspondientes.

## Transfer Learning

Se decidió utilizar Transfer Learning en algunos modelos para aprovechar pesos preentrenados en grandes datasets (e.g., COCO). Esto permitió obtener mejores resultados iniciales y acelerar el entrenamiento.

- **Modelos con Transfer Learning**: YOLOv8, RetinaNet, Faster R-CNN.
- **Modelos sin Transfer Learning**: [Especificar si aplica].

## Data Augmentation

El uso de Data Augmentation fue considerado debido a la posible limitación en la cantidad de imágenes etiquetadas.

- **Data Augmentation utilizado**: Rotaciones, escalado, recortes aleatorios y flip horizontal.
- **Justificación**: Aumentar la diversidad de los datos para mejorar la generalización de los modelos.

## Entrenamientos Realizados

Se realizaron múltiples entrenamientos, probando diferentes configuraciones de hiperparámetros. Los resultados de estos entrenamientos se pueden encontrar en los notebooks:

- `YOLOv8_training.ipynb`
- `RetinaNet_training.ipynb`
- `FasterRCNN_training.ipynb`
- `OtroModelo_training.ipynb`

### Hiperparámetros utilizados

| Modelo          | Epochs | Batch Size | Learning Rate | Otros Hiperparámetros     |
|-----------------|--------|------------|---------------|---------------------------|
| YOLOv8          | 50     | 16         | 0.001         | Augmentation X             |
| RetinaNet       | 40     | 8          | 0.0001        | Scheduler Y                |
| Faster R-CNN    | 60     | 4          | 0.005         | Backbone ResNet50          |
| [Otro Modelo]   | X      | X          | X             | X                         |

## Resultados

Los resultados de los experimentos incluyen métricas como:

- **Mean Average Precision (mAP)** para detección de objetos.
- **Precision**, **Recall** para cada clase.
- Comparación gráfica de las curvas de aprendizaje y las métricas obtenidas por cada modelo.

Las gráficas y comparaciones están disponibles en el directorio `results/`.

### Comparación de Modelos

| Modelo          | mAP (%) | Precisión (%) | Recall (%) | Tiempo de Entrenamiento |
|-----------------|---------|---------------|------------|-------------------------|
| YOLOv8          | XX.XX   | XX.XX         | XX.XX      | XX horas                |
| RetinaNet       | XX.XX   | XX.XX         | XX.XX      | XX horas                |
| Faster R-CNN    | XX.XX   | XX.XX         | XX.XX      | XX horas                |
| [Otro Modelo]   | XX.XX   | XX.XX         | XX.XX      | XX horas                |

## Conclusiones

- **YOLOv8** se destacó por su rapidez y precisión en comparación con otros modelos.
- **RetinaNet** mostró mejor rendimiento para la detección de objetos más pequeños.
- **Faster R-CNN** ofreció una mayor precisión general, aunque a costa de tiempos de entrenamiento más largos.
- [Añadir conclusiones adicionales relacionadas con la generalización, el uso de Data Augmentation y Transfer Learning].

## Requisitos

Para reproducir los experimentos, instala las dependencias del proyecto:

```bash
pip install -r requirements.txt
```


### Uso
Para entrenar un modelo, utiliza el script de entrenamiento con los parámetros deseados:

```bash
python src/train.py --model yolo --epochs 50 --batch_size 16
```

### Diapositivas de la Presentación
Las diapositivas para la presentación final están disponibles en slides/Presentacion_TP.pptx.