## Проект "Автоматическая разметка автомобильных номеров на изображениях с помощью модели YOLO World"

### Цель проекта

Цель проекта -  сократить время, затрачиваемое на выполнение рутинной работы по разметке изображений.

### Задачи проекта

Для достижения цели необходимо решить следующие задачи:

1. Найти в открытых источниках датасет фотографий авто с российскими автомобильными номерами.

2. Изучить механизмы и принципы работы моделей, позволяющих выделить объект на изображении по текстовому описанию (Grounding Dino, YOLO-World).

3. Изучить техники формирования промптов к zero-shot object detection моделям.

4. Проанализировать потребление видеопамяти у различных конфигураций моделей для расчёта оптимального батча изображений.

5. Разработать пайплайн автоматической разметки изображений (промпт с текстовым описанием целевого объекта, предобработка размера изображения, выставление порога уверенности для распознавания, формирование детекций на каждом изображении в батче, сохранение размеченных изображений, формирование датасета с метаданными по детекциям для каждого изображения, экспорт датасета в формат YOLO).

6. Оценить качество разметки на случайной подвыборке.

7. Сформировать методику валидации датасета через инструмент CVAT.

8. Обучить модель YOLO11 на сформированном датасете, оценить результаты.

9. Изучить способы и методы формирования real-time инференса модели YOLO11 (для вывода в продакшен).

### Результаты

1. Сформирован пайплайн zero-shot разметки изображений с помощью модели YOLO-World для решения задачи object detection (детекция автомобильных номеров).

2. Оценено качество разметки: из 600 изображений модель не смогла корректно разметить 78 изображений (с выставленным порогом распознавания в 0.45), ошибка модели составила 13%. С порогом распознавания в 0.6 - модель не разметила 51 изображение, ошибка модели составила 8%. Работа разметчика значительно сокращена.

3. Произведены необходимые корректировки разметки в инструменте CVAT с последующим обновлением текстовых метаданных (координаты целевых объектов на изображениях).

4. Выполнено обучение модели YOLO11 на датасете, размеченным моделью YOLO-World, а также выполнено обучение модели на исходном датасете (размеченным руками).

5. Выполнено тестирование инференса real-time детекции модели YOLO11 с помощью библиотеки OpenCV.

### Дальнейшее развитие проекта

1. Изучение и применение механизмов трекинга объектов в real-time инференсе модели YOLO11.

2. Изучение и решение проблемы низкого FPS при использовании трекинг-алгоритмов (BotSort, ByteTrack) в real-time инференсе модели YOLO11.

3. Сравнение скоростей инференса real-time детекций в OpenCV и Supervision.

4. Изучение модели YOLOE, проведение экспериментов с авторазметкой, сравнение производительности с YOLO-World.