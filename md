import pandas as pd
import random

# Создаем DataFrame с одним столбцом 'whoAmI'
lst = ['robot'] * 10 + ['human'] * 10
random.shuffle(lst)
data = pd.DataFrame({'whoAmI': lst})

# Получаем уникальные значения из столбца 'whoAmI'
categories = data['whoAmI'].unique()

# Создаем новые столбцы в DataFrame для каждой уникальной категории
for category in categories:
    data[category] = (data['whoAmI'] == category).astype(int)

# Удаляем исходный столбец 'whoAmI'
data.drop('whoAmI', axis=1, inplace=True)

# Выводим преобразованный DataFrame
print(data.head())
