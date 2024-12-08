## Предобработка данных
#### Заполнение пропусков
- df.fillna() - метод, заполняющий пропуски конкретным значением:
```
df = pd.DataFrame({ 'A': [1, 2, np.nan, 4], 
					'B': [np.nan, 5, 6, 7], 
					'C': [8, 9, 10, np.nan] })
# Заполняем пропуски в столбце 'A' средним значением 
df['A'] = df['A'].fillna(df['A'].mean()) 
# Заполняем пропуски в столбце 'B' значением 0 
df['B'] = df['B'].fillna(0) 
# Заполняем пропуски в столбце 'C' значением, равным 100 df['C'] = df['C'].fillna(100)
```
- [SimpleImputer](https://scikit-learn.org/1.5/modules/generated/sklearn.impute.SimpleImputer.html) - класс, с помощью которого мы можем удобно заполнить пропуски в данных:
	```
	import numpy as np 
	import pandas as pd 
	from sklearn.impute import SimpleImputer 
	# Создаем пример DataFrame с пропущенными значениями 
	df = pd.DataFrame({ 'A': [1, 2, np.nan, 4], 
						'B': [np.nan, 5, 6, 7], 
						'C': [8, 9, 10, np.nan] }) 
	# Создаем объект SimpleImputer 
	# Здесь мы используем стратегию 'mean' для заполнения средним значением
	imputer = SimpleImputer(strategy='mean') # Применяем imputer к данным
	df_imputed = pd.DataFrame(imputer.fit_transform(df), columns=df.columns)
	```
	