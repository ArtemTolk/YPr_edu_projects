## Описание проекта

Необходимо разработать демонстрационную версию поиска изображений по текстовому запросу.<br>
Для демонстрационной версии нужно обучить модель, которая получит векторное представление изображения, векторное представление текста, а на выходе выдаст число от 0 до 1 — покажет, насколько текст и картинка подходят друг другу.<br> Тренировочные данные (изображение + несколько описаний к нему) размечены оценками пользователей и оценками 3-х экспертов.

**В ходе проекта выполнено**
- Загрузка и анализ данных
    - проверка полноты данных (все файлы данных и идентификаторы присутствуют)
    - проверка целостности данных (поиск поврежденных фалов)
    - удаление аномальных значений и пропусков
    - создание целевой переменной (интеграция оценок пользователей и экспертов в индекс соответствия)
- Лемматизация и фильрация текстовых описаний
- Векторизация изображений с использованием предобученой модели
- Векторизация текстов с использованием предобученой модели
- Объединение векторов, формирование итогового датафрейма
- Первичная оценка моделей (кроссвалидация)
- Подбор гиперпараметров
- Тестирование, оценка качества работы моделей

**Результаты**

Изображения и текстовые описания векторизированы с применением предобученных моделей `ResNet50 (Imagenet)` и `bert-base-uncased`.<br>
Признаковое пространство сформировано из объединения векторов и целевой переменной.<br>
По результатам кроссвалидации выбраны лучшие модели - `LGBMRegressor` и `FCNN`.<br>
Тестирование показало, что модели недостаточно обучились на трениеровочных данных (1000 изображений).<br>
Для повышения релевантности поиска необходимо:
- увеличить размер тренировочной выборки
- увеличить вариативность целевой переменной (индекс соответствия) путем увеличения числа экспертов
