# VKIntern_0424 Большагин Вячеслав
Результирующие метрики:
Average NDCG@5:  0.5881107326687397;
Average NDCG@50: 0.7476370126497026;
Average MAP@5:   0.24654899015189452;
Average MAP@50:  0.22244712491686655;

Все метрики были вычислены внутри отдельных запросов и усреднены
В целом, получилась достаточно хорошей, так как большинство документов в целом находятся рядом с целевыми позициями. Однако MAP указывает, что модель редко когда угадывает точное местоположение документа. Хотя и сама метрика MAP@k не является в полной мере репрезентативной (как и подобные метрики, учитывающие только совпадение идеального и предсказанного местоположения документа), так в данном датасете очень малое количество уровней рангов - в основном 0 и 1, что делает сложным вычисление MAP и подобных.

# Что было сделано
Анализ данных на:
- пропуски
- повторяющиеся записи
- особенности данных
- корреляцию признаков (с последующей очисткой)

Признаки были отмасштабированы MaxAbsScaler'ом

В качестве модели был выбран CatBoostRanker, параметры для которого были подобраны с помощью кросс-валидации. Была также проверена гипотеза о необходимости удаления коррелирующих признаков. Получившиеся модели были сохранены с помощью модуля pickle. (из-за большого размера моделей не получилось загрузить их в репозиторий)

P.S. В результате одного из тестовых запусков была получена модель со следующими метриками (она была сохранена): 
Average NDCG@5:  0.6739929401048327;
Average NDCG@50: 0.7936437279188054;
Average MAP@5:   0.31785316864185165;
Average MAP@50:  0.2746504691059156;

Однако повторить данные метрики (даже с полным копированием всех параметров модели) не удалось ни разу, поэтому называть их рабочими нет возможности
