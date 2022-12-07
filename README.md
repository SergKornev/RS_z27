# RS_z27
Используемые библиотеки
```
pandas
recmetrics
numpy
surprise
implicit
tqdm
sklearn
abc
scipy
```
Для тестирования: 
```
from RS-z27 import algoritms

file_item = 'movies.csv'
file_user = 'ratings.csv'

algoritms.recommend_system(file_item, file_user)
```

Параметры ```recommend_system``` :
```
recommend_system(user_data, 
                item_data, 
                user_col='userId', 
                item_col='movieId', 
                rating_col='rating',
                search_word='Matrix', # к какому item искать похожего
                count_recom=10,
                type_of_data='csv', 
                user_id=14) # для какого user делать рекомендации
```

## Реализованные алгоритмы 
### KNN
KNN - алгоритм ближайших соседей. Иcпользуюемая метрика - косинусное расстрояние 
```
knn = NearestNeighbors(metric='cosine', algorithm='brute',
                           n_neighbors=20, n_jobs=-1)
```
### ALS
Заимстрвован из библиотеки ```implicit```
```
 model = implicit.als.AlternatingLeastSquares(
        factors=30, regularization=0.1, iterations=16)
```
Параметры были подобраны путем экспериментов

### SVD
```
reader = Reader(rating_scale=(0, 5))
    data = Dataset.load_from_df(ratings_[[user_col, item_col, rating_col]], reader)
    trainset, testset = train_test_split(data, test_size=0.25)

    algo = SVD()
    algo.fit(trainset)
```
