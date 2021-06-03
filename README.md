# Advertisement
Поиск объявлений, содержащих контактные данные

Данные: название и текст объявления, категория, цена, местоположение, время размещения. Задача - определить, содержатся ли в объявлении контактные данные человека (номер телефона, ссылки на соцсети и др.) (Классификация). Целевой столбец - "is_bad".

Присутствует дисбаланс классов, поэтому для оценки качества используем roc auc. Также имеются пропуски в столбце "price", которые были удалены. Были извлечены дополнительные признаки: количество цифр в тексте объявления, день недели размещения, наличие символов "+" или "@" и другие.

Сам текст объявления был лемматизирован (слова приведены к нормальной форме, удалены стоп-слова). Далее слова были приведены к векторной форме, используя TfidfVectorizer.

В качестве модели использован xgboost + RandomizedSearchCV.

В результате работы алгоритма XGBoost со стандартными параметрами на тестовой выборке получился результат roc_auc = 0,8958.

Отбор признаков и подбор гиперпараметров позволил улучшить этот результат до 0,9241.

Самыми весомыми признаками оказались категория и подкатегория объявления, а также такие ключевые слова, как "тело", "звонить", "телефон" и "вопрос", что видно из графика важности признаков.

Модель получилась не переобучена.
