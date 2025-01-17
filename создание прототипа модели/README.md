# Создание прототипа модели "Исследование технологического процесса очистки золота"

Цель: подготовить прототип модели машинного обучения для компании, которая разрабатывает решения для эффективной работы промышленных предприятий. Спецификации модели: Модель должна предсказать коэффициент восстановления золота из золотосодержащей руды с использованием данных с параметрами добычи и очистки. Модель поможет оптимизировать производство, чтобы не запускать предприятие с убыточными характеристиками.

Задачи: 
Подготовить данные 1.1 Проверить, что эффективность обогащения рассчитана правильно. Вычислить её на обучающей выборке для признака rougher.output.recovery. Найти MAE между расчётами и значением признака. 1.2. Проанализировать признаки, недоступные в тестовой выборке. 1.3. Провести предобработку данных.
Проанализировать данные 2.1. Посмотреть, как меняется концентрация металлов (Au, Ag, Pb) на различных этапах очистки. 2.2. Сравнить распределения размеров гранул сырья на обучающей и тестовой выборках. 2.3. Исследовать суммарную концентрацию всех веществ на разных стадиях: в сырье, в черновом и финальном концентратах.
Построить модель 3.1. Написать функцию для вычисления итоговой sMAPE. 3.2. Обучить разные модели и оценить их качество кросс-валидацией. Выбрать лучшую модель и проверить её на тестовой выборке.

Навыки и инструменты: Python, Pandas, Matplotlib, Scikit-learn, NumPy, машинное обучение, исследовательский анализ,  кросс-валидация, регрессия и модели: LinearRegression, DecisionTreeRegressor, RandomForestRegressor, кастомные метрики: MAE, SMAPE 

Выводы: 

Эффективность обогащения рассчитана правильно, она была сравнена с вычислениями ее на обучающей выборке для признака rougher.output.recovery. Абсолютная средняя ошибка по тренировочной выборке = 1.0748911125799084e-14

Изучены концетрации основных веществ на разных этапах очистки и представлены в виде графиков Размер гранул тестовой и обучающей выборки на начальном этапе представлен в виде графика. Создана таблица суммарной концентрации веществ на разных этапах.

У золота и свинца концентрация после каждого этапа увеличивается, у серебра после второго этапа увеличивается, а в результате очисток падает ниже первоначального показателя. Видимо, часть металла теряется в процессе реакций с веществами, которые используют для очистки

Создана функция для подсчета sMAPE для целевого признака train_target_rougher и итоговой sMAPE. Проанализированы показатели R2, MAE:

Mean R2 from CV of LinearRegression = -0.17458109168892058 Mean MAE from CV of LinearRegression = 6.82938596512015 Mean MAE from CV of LinearRegression = 10.825620606932198

Mean R2 from CV of DecisionTreeRegressor = -1.960313484276531 Mean MAE from CV of DecisionTreeRegressor = 9.229946514719604 Mean MAE from CV of DecisionTreeRegressor = 15.969075449486985

Mean R2 from CV of RandomForestRegressor = 0.051079076171925863 Mean MAE from CV of RandomForestRegressor = 7.009355682626632 Mean MAE from CV of RandomForestRegressor = 9.663341590725057

Масштабирование данных на результат LinearRegression не повлияло, значит, и для других моделей можно им пренебречь.

Данные кросс-валидации также были проверены на анализе, какая из моделей даст лучший результат по sMAPE с учетом перебора гиперпараметров, где это возможно

Таким образом, лучшая модель из всех трех LinearRegression(), ее sMAPE составил 6.622023914131742, а sMAPE на final 9.745442057962514

А на тестовой выборке у LinearRegression() показатели такие: sMAPE на тестовой выборке 8.063902395250446 sMAPEfinal на тестовой выборке 8.99855954969781

Вторая по показателю RandomForestRegressor ее sMAPE составил , а sMAPE на final 9.360555450246625, что лучше, чем у лидера

Однако показатели на тестовой выборке у RandomForestRegressor хуже, чем у лидера: sMAPE на тестовой выборке 8.94876150849763 sMAPEfinal на тестовой выборке 9.418584108553386
