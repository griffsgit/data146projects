## Answers to exercises

1. There are twelve unique values, which means there are twelve unique years. These years are: 1952, 1957, 1962, 1967, 1972, 1977, 1982, 1987, 1992, 1997, 2002, 2007

> uniqueyears = data.year.unique()

> print(uniqueyears)

2. The largest population was 1,318,683,096. This occured in China in 2007
> new_object_with_max_pop = data['pop'].max()

> print(new_object_with_max_pop)

> new_object_with_idxmax_pop = data['pop'].idxmax()

> print(data.loc[new_object_with_idxmax_pop])

3. The country in Europe with the lowest population in 1957 was Iceland, at 165,110. In 2007 the population was 301,931.

> cont = 'Europe'

> idxCont = data['continent']==cont

> temp = data[idxCont]

> year = 1957

> idxYear = temp['year']==year

> data_final = temp[idxYear]

> idx_min = data_final['pop'].idxmin()

>print(data_final.loc[idx_min])

> year = 2007

> idxYear = temp['year']==year

> data_final = temp[idxYear]

> place = data_final['country'] =='Iceland'


> print(data_final[place])
