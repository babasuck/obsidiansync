## Dataset

`torch.utils.data.Dataset`

Примитив для хранения самих данных и ассоциированных с ними меток.
Датасеты должны наследоваться от абстрактного класса `Dataset`
Для этого нужно реализовать 3 метода:
1. `__init__`
2. `__len__`
3. `__getitem__`

### `__init__` функция

Конструктор датасета, здесь обычно указывается:
* директория до данных
* директория до меток
* трансформации

```python
def __init__(self, annotations_file, files_dir, transform=None):
	self.data_dir = files_dir
	self.labels = pd.read_csv(annotations_file)
	self.tranform = transform
```


### `__len__` функция

Должна возвращать длину датасета для оператора `len()`:

```python
return len(self.labels)
```

### `__getitem__` функция

Возвращает элемент датасета и его метку по заданному индексу `idx`, чтобы была поддержка оператора `[]`

```python
def __getitem__(self, idx):
	img_path = os.path.join(self.data_dir, self.labels.iloc[idx, 0])
	image = read_image(img_path)
	label = self.labels.iloc[idx, 1]
	if self.transform:
		image = self.transform(image)
	return image, label
```

## Встроенные датасеты (torchvision)

### MNIST

```python
from torchvision.datasets import MNIST
from trochvision.transforms import ToTensor

mnist = MNIST("data", train=True, download=True, transform=ToTensor())
```

## Dataloader

Обертка над `Dataset`, которая используется непосредственно в процессе обучения, позволяет перемешивать данные, упаковывать их в минибатчи, использовать `multiprocessing` для заполнения минибатчей. Возвращает непосредственно минибатч.

```python
from torch.utils.data import DataLoader

dataloader = DataLoader(dataset, shuffle=True, batch_size=64)
```


