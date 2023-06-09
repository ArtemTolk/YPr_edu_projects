## Описание проекта

Чтобы оптимизировать производственные расходы, металлургический комбинат решил построить модель, которая будет предсказывать температуру расплава в ковше, учитывая завершенные к этому моменту времени стадии технологического процесса. В качестве критерия оценки качества модели по заданию необходимо использовать метрику `MAE`. Значение метрики должно быть не более `6.3`. Необходимо рассмотреть следующие классы моделей:
- решающее дерево,
- бустинги,
- нейронные сети.

**В рамках проекта выполнено**
- первичное исследование таблиц БД
- расчет показателей по всему массиву данных с использованием SQL запросов (4 аналитические задачи)
- выгрузка данных из БД
- исследовательский анализ данных
- создание признаков (Feature engineering)
- подбор гиперпараметров моделей
- тестирование моделей
- анализ важности признаков

**Результаты**

Сформировано признаковое пространство.<br>
В соответствии с условиями задачи рассмотрены модели:
- RandomForestRegressor
- CatBoostregressor
- FC нейронная сеть

Лучшей моделью по метрике **`MAE`** с значением `5.398` стал `CatBoostRegressor`.<br>
Проведен анализ важности признаков, выявлены приоритетные и важные признаки. Для признака **полная переданная энергия** `total_energy` проведен анализ взаимосвязи с целевой переменной.<br>Сформулированы рекомендации заказчику по улучшению сбора исходных данных.
