# Хакатон Пермского краеведческого музея


## Описание

Задача - поиск картинок по текстам описаний, обучающая выборка 2098, тестовая - 900 пар.

## Решение

Общая идея модели - превратить изображения и тексты в численное представление (вектор), с помощью модели научиться превращать представление текста в представление картинки и потом находить самую похожую на него.

**Инструменты**

- tensorflow (Keras)
- предобученная модель BERT (русскоязычная версия от DeepPavlov) в transformers
- предобученная модель EfficientNetB0
- библиотека Annoy для построения индекса представлений картинок, чтобы потом быстро искать


**Плюсы**

- можно масштабировать, если картинок очень много (тысячи, миллионы картинок, сам поиск будет занимать максимум пару секунд)
- решение не привязано к метрике задачи, не использует никакие утечки данных

**Проблемы**

- если такое использовать для поиска по картинкам для обычных людей, то это не будет работать, так как обучение происходит на основе музейных описаний, которые написаны специализированным профессиональным языком и в особой форме. Если, например, как люди ищут что-то в гугле, то можно заметить явную разницу
- очень мало данных строго в рамках задачи, качество будет намного лучше, если обучать модель на больших данных Госкаталога

**Техническая информация по репозиторию**

- требуемые библиотеки в файле requirements.txt
- файл обучения модели training.ipynb
- файл с демонстрацией demo.ipynb
- требуемая файловая структура для работы

```
/train_dataset_train
	/train
		1.png
		...
	train.csv
/test_dataset_test
	/test
		1.png
		...
	test.csv
training.ipynb
demo.ipynb
test.ann
train.ann
model.keras
requirements.txt
```

