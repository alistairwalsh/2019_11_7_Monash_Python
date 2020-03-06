![](/Users/alistairwalsh/Documents/git\_repos/2019\_11\_7\_Monash\_Python/content/images/pandas.jpeg)

# What is Pandas?

Python Data Analysis Library, called Pandas, is a Python library built for data analysis and manipulation. It’s open-source and supported by Anaconda. It is particularly well suited for structured (tabular) data. For more information, see [pandas-docs](http://pandas.pydata.org/pandas-docs/stable/index.html).

```python
import pandas as pd

airports = pd.read_csv('data/airports.csv')
airport_freq = pd.read_csv('data/airport-frequencies.csv')
runways = pd.read_csv('data/runways.csv')
```

I got this data at [http://ourairports.com/data/]()


### SELECT, WHERE, DISTINCT, LIMIT


|                      SQL                     |                 Pandas                |
|:--------------------------------------------:|:-------------------------------------:|
| select * from airports                       | airports                              |
| select * from airports limit 3               | airports.head(3)                      |
| select id from airports where ident = 'KLAX' | airports[airports.ident == 'KLAX'].id |
| select distinct type from airport            | airports.type.unique()                |


### SELECT with multiple conditions

|                                                  SQL                                                 |                                                       Pandas                                                       |
|:----------------------------------------------------------------------------------------------------:|:------------------------------------------------------------------------------------------------------------------:|
| select * from airports where iso\_region = 'US-CA' and type = 'seaplane\_base'                         | airports[(airports.iso\_region == 'US-CA') & (airports.type == 'seaplane\_base')]                                    |
| select ident, name, municipality from airports where iso\_region = 'US-CA' and type = 'large\_airport' | airports[(airports.iso\_region == 'US-CA') & (airports.type == 'large\_airport')][['ident', 'name', 'municipality']] |


### ORDER BY

|                                     SQL                                    |                                          Pandas                                         |
|:--------------------------------------------------------------------------:|:---------------------------------------------------------------------------------------:|
| select * from airport\_freq where airport\_ident = 'KLAX' order by type      | airport\_freq[airport\_freq.airport\_ident == 'KLAX'].sort\_values('type')                  |
| select * from airport\_freq where airport\_ident = 'KLAX' order by type desc | airport\_freq[airport\_freq.airport\_ident == 'KLAX'].sort\_values('type', ascending=False) |

### IN… NOT IN

|                                  SQL                                 |                           Pandas                           |
|:--------------------------------------------------------------------:|:----------------------------------------------------------:|
| select * from airports where type in ('heliport', 'balloonport')     | airports[airports.type.isin(['heliport', 'balloonport'])]  |
| select * from airports where type not in ('heliport', 'balloonport') | airports[~airports.type.isin(['heliport', 'balloonport'])] |


### GROUP BY, COUNT, ORDER BY

|                                                           SQL                                                           |                                                                     Pandas                                                                    |
|:-----------------------------------------------------------------------------------------------------------------------:|:---------------------------------------------------------------------------------------------------------------------------------------------:|
| select iso\_country, type, count(&ast;) from airports group by iso\_country, type order by iso\_country, type              | airports.groupby(['iso\_country', 'type']).size()                                                                                              |
| select iso\_country, type, count(&ast;) from airports group by iso\_country, type order by iso\_country, count(&ast;) desc | airports.groupby(['iso\_country', 'type']).size().to\_frame('size').reset\_index().sort\_values(['iso\_country', 'size'], ascending=[True, False]) |




|                                                           SQL                                                           |                                                                     Pandas                                                                    |
|:-----------------------------------------------------------------------------------------------------------------------:|:---------------------------------------------------------------------------------------------------------------------------------------------:|
| select iso\_country, type, count(&ast;) from airports group by iso\_country, type order by iso\_country, type              | airports.groupby(['iso\_country', 'type']).size()                                                                                              |
| select iso\_country, type, count(&ast;) from airports group by iso\_country, type order by iso\_country, count(&ast;) desc | airports.groupby(['iso\_country', 'type']).size().to\_frame('size').reset\_index().sort\_values(['iso\_country', 'size'], ascending=[True, False]) |


### HAVING


|                                                                     SQL                                                                     |                                                                   Pandas                                                                   |
|:-------------------------------------------------------------------------------------------------------------------------------------------:|:------------------------------------------------------------------------------------------------------------------------------------------:|
| select type, count(&ast;) from airports where iso\_country = 'US' group by type having count(&ast;) > 1000 order by count(&ast;) desc | airports[airports.iso\_country == 'US'].groupby('type').filter(lambda g: len(g) > 1000).groupby('type').size().sort\_values(ascending=False) |

### Top N records

|                                    SQL                                   |                           Pandas                          |
|:------------------------------------------------------------------------:|:---------------------------------------------------------:|
| select iso\_country from by\_country order by size desc limit 10           | by\_country.nlargest(10, columns='airport\_count')          |
| select iso\_country from by\_country order by size desc limit 10 offset 10 | by\_country.nlargest(20, columns='airport\_count').tail(10) |

### Aggregate functions (MIN, MAX, MEAN)

|                                           SQL                                          |                            Pandas                            |
|:--------------------------------------------------------------------------------------:|:------------------------------------------------------------:|
| select max(length\_ft), min(length\_ft), mean(length\_ft), median(length\_ft) from runways | runways.agg({'length\_ft': ['min', 'max', 'mean', 'median']}) |

### JOIN

|                                                                               SQL                                                                              |                                                                                    Pandas                                                                                    |
|:--------------------------------------------------------------------------------------------------------------------------------------------------------------:|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| select airport\_ident, type, description, frequency\_mhz from airport\_freq join airports on airport\_freq.airport\_ref = airports.id where airports.ident = 'KLAX' | airport\_freq.merge(airports[airports.ident == 'KLAX'][['id']], left\_on='airport\_ref', right\_on='id', how='inner')[['airport\_ident', 'type', 'description', 'frequency\_mhz']] |

### UNION ALL and UNION


|                                                                 SQL                                                                 |                                                                  Pandas                                                                 |
|:-----------------------------------------------------------------------------------------------------------------------------------:|:---------------------------------------------------------------------------------------------------------------------------------------:|
| select name, municipality from airports where ident = 'KLAX' union all select name, municipality from airports where ident = 'KLGB' | pd.concat([airports[airports.ident == 'KLAX'][['name', 'municipality']], airports[airports.ident == 'KLGB'][['name', 'municipality']]]) |

INSERT

UPDATE

DELETE

Immutability


source [jbennetcodes](https://medium.com/jbennetcodes/how-to-rewrite-your-sql-queries-in-pandas-and-more-149d341fc53e)

