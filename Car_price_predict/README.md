## Описание проекта

Сервис по продаже автомобилей разрабатывает приложение для привлечения новых клиентов. Одной из функций приложения должна стать возможность быстрой оценки рыночной стоимости автомобиля.<br>
В распоряжении имеются исторические данные: технические характеристики, комплектации и цены автомобилей. Необходимо построить модель для определения стоимости. 

Заказчику важны следующие критерии:
- качество предсказания (для оценки качества моделей применяем метрику `RMSE`, `threshold = 2500`);
- скорость предсказания;
- время обучения.

**В рамках проекта выполнено**
- Предобработка данных
    * Очистка данных, удаление аномальных значений и ошибок, трансформация признаков (например, `год выпуска` --> `возраст`)
    * Генерация новых признков (например, `почтовый индекс` --> `название региона`)
    * Восстановление пропусков в данных с применением собственой функции<br>Функция возвращает наиболее частое или медианное значение пропущенной величины<br>Расчет производится по группировкам восстанавливаемой переменой по нескольким "опорным" признакам.<br>Например, восстановление пропусков для признака `gearbox` основывается на выборе наиболее часто встречающегося значения для данного признака при группировке по полям `model` и `brand`
    * Оптимизация типов данных
    * OHE кодирование категориальных признаков
- Замер метрик моделей на кроссвалидации
- Подбор гиперпараметров моделей
- Оценка важности признаков по данным моделей на тренировочной выборке
- Анализ моделей по критериям, указанным заказчиком
- По результатам тестирования выбрана наиболее подходящая модель

**Результаты**

Лучшие результаты показали модели бустинга (`LGBM` и `CatBoost`). Значение заданной условием метрики `RMSE` у обеих моделей близкое (1596 и 1606 соотв.), время обучения и прогноза моделей значительно отличается:<br>
- `обучение` 6.3 и 447 соотв.
- `прогноз` 3.052 и 0.847 соотв.

С учетом планируемого применения модели, наиболее критичным является время прогноза т.е. "отклика" модели на запрос пользователя, поэтому рекомендацией заказчику может быть выбор модели с лучшим временем прогноза при сопоставимой точности.
