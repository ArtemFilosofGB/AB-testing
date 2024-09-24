# Выборка из множества
```
import pandas as pd

Загрузите данные в DataFrame (замените 'your_data.csv' на ваш файл)
df = pd.read_csv('your_data.csv')

Разделите данные на группы мужчин и женщин
males = df[df['gender'] == 'male']
females = df[df['gender'] == 'female']

Определите размер меньшей группы
min_size = min(len(males), len(females))

Случайным образом выберите подвыборку из каждой группы
males_sample = males.sample(n=min_size, random_state=1)
females_sample = females.sample(n=min_size, random_state=1)

Объедините подвыборки
balanced_df = pd.concat([males_sample, females_sample])

Теперь можно анализировать сбалансированные данные
marriage_counts = balanced_df['marital_status'].value_counts()
print(marriage_counts)

Если вам нужно посмотреть, как часто мужчины и женщины бывают в браке
marriage_by_gender = balanced_df.groupby('gender')['marital_status'].value_counts()
print(marriage_by_gender)

```