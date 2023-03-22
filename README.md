# python-data-assignment

#το query με mysql
select * from finance_liquor_sales
where date between '2016-01-01' and '2019-12-31';

#o κώδικας python
import pandas as pd
import numpy as np
data=pd.read_csv('finance_liquor_sales.csv')
grp_data=data.groupby(['zip_code','store_name'])
perc_sales=grp_data['sale_dollars'].sum()/data['sale_dollars'].sum()
most_popular=grp_data['item_description'].max()[perc_sales.idxmax()]
print(most_popular,perc_sales)
import matplotlib.pyplot as plt
x=data['zip_code']
y=data['bottles_sold']
plt.scatter(x,y)
plt.xlabel('Zip Code')
plt.ylabel('Bottles Sold')
plt.title('Bottles Sold')
plt.show()
