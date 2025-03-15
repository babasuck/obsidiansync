```bash
├───config
│   └───shift_ocr
│       ├───detector
│       ├───loader
│       ├───postprocessor
│       ├───preprocessor
│       ├───recognizer
│       └───visualizer
├───notebooks
├───scripts
│   ├───dataset_prepare
│   │   ├───ddi
│   │   ├───pdfa
│   │   └───sroie
│   └───parsing_scripts
├───shift_ocr
│   ├───detectors
│   ├───loaders
│   ├───postprocessor
│   ├───preprocessor
│   ├───recognizer
│   ├───shift_ocr
│   ├───utils
│   └───visualizers
└───tests
    ├───detector
    └───test_loaders
```

## Detectors

Детектор обнаруживает текст на изображениях, возвращает список детекций.

```python
class Detector(ABC):

    @abstractmethod
    def detect(self, image: np.array) -> List[Detection]:

        """Детектирование текста"""

        raise NotImplementedError
```

Детекция - датакласс 

```python
@dataclass

class Detection:
    absolute_box: List[int]  # Формат (tl_x, tl_y, br_x, br_y)
    score: Optional[float]  # Конфиденс
    relative_box: List[float] = None  # Формат (tl_x, tl_y, br_x, br_y)
    crop: Optional[List[np.array]] = None  # Нарезанные кропы
```

1. `craft.py` +
## Loaders

Служит для загрузки датасета

1. `image_loader.py` `tests\test_loaders\test_image‎_loader.py` +

## Preprocessor

```python
class Preprocessor(ABC):
    @abstractmethod
    def preprocessing(self, image: np.array) -> np.array:
        """Начальная обработка входной картинки"""
       raise NotImplementedError
```


## Postprocessor

```python
class Postprocessor(ABC):
    @abstractmetho
    def postprocessing(
        self, detections: List[Detection], image: np.array) -> List[Detection]:
        """Исправление детектированного текста"""
        raise NotImplementedError
```

## Recognizer 

Служит для распознавания текста из изображения по детекциям

```python
class Recognizer(ABC):
    @abstractmethod
    def recognize(
        self, postprocess_image: List[Detection], image: np.array) -> List[str]:
        """Распознавание текста с детектированных областей"""
        raise NotImplementedError
```

### EasyOCR

Последняя версия EasyOCR несовместима с версией `torch==1.11` понизил версию `easyOCR` на 1

## Utlis

Fix error with yolo detections read

```python
def read_detections(images, txt_paths, box_format='pascal_voc'):
    detections = []
    for image, txt_path in zip(images, txt_paths):
        height, width = image.shape[:2]
        with open(txt_path, 'r', encoding='utf-8') as f:
            lines = [line.strip() for line in f if line.strip()]
        image_detections = []
        for line in lines:
            class_id, coords_str = line.split(" ", 1)
            x_cn, y_cn, w_n, h_n = ast.literal_eval(coords_str)
            if box_format == 'yolo':
                absolute_box = [

                    int((x_cn - w_n / 2) * width),

                    int((y_cn - h_n / 2) * height),

                    int((x_cn + w_n / 2) * width),

                    int((y_cn + h_n / 2) * height),

                ]
            else:
                absolute_box = [x_cn, y_cn, w_n, h_n]

            image_detections.append(
                Detection(
                    absolute_box=absolute_box, score=1
                )  # Можно добавить расчет relative_box
            )
        detections.append(image_detections)
    return detections
```

Зачем в `BoundingBoxVisualizer` и `ImgDetectionVisualize` параметр `type_bbox` если мы преобразуем в единый вид датакласса через `read_detections` 