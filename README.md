# project1
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
dropout= pd.read_csv("dropout-ratio-2012-2015.csv",delimiter=',', quotechar='"')
dropout
State_UT	year	Primary_Boys	Primary_Girls	Primary_Total	Upper Primary_Boys	Upper Primary_Girls	Upper Primary_Total	Secondary _Boys	Secondary _Girls	Secondary _Total	HrSecondary_Boys	HrSecondary_Girls	HrSecondary_Total
0	A & N Islands	2012-13	0.83	0.51	0.68	Uppe_r_Primary	1.09	1.23	5.57	5.55	5.56	17.66	10.15	14.14
1	A & N Islands	2013-14	1.35	1.06	1.21	NR	1.54	0.51	8.36	5.98	7.2	18.94	12.2	15.87
2	A & N Islands	2014-15	0.47	0.55	0.51	1.44	1.95	1.69	11.47	8.16	9.87	21.05	12.21	16.93
3	Andhra Pradesh	2012-13	3.3	3.05	3.18	3.21	3.51	3.36	12.21	13.25	12.72	2.66	NR	0.35
4	Andhra Pradesh	2013-14	4.31	4.39	4.35	3.46	4.12	3.78	11.95	13.37	12.65	12.65	10.85	11.79
...	...	...	...	...	...	...	...	...	...	...	...	...	...	...
105	West Bengal	2013-14	3.44	2.37	2.91	5.63	3.1	4.31	16.73	19.77	18.34	8.03	7.76	7.9
106	West Bengal	2014-15	2.13	0.79	1.47	5.84	2.88	4.3	16.33	19.06	17.8	8.18	8.04	8.11
107	All India	2012-13	4.68	4.66	4.67	2.3	4.01	3.13	14.54	14.54	14.54	NR	NR	NR
108	All India	2013-14	4.53	4.14	4.34	3.09	4.49	3.77	17.93	17.79	17.86	1.48	1.61	1.54
109	All India	2014-15	4.36	3.88	4.13	3.49	4.6	4.03	17.21	16.88	17.06	0.25	NR	NR
110 rows × 14 columns

dropout.head()
State_UT	year	Primary_Boys	Primary_Girls	Primary_Total	Upper Primary_Boys	Upper Primary_Girls	Upper Primary_Total	Secondary _Boys	Secondary _Girls	Secondary _Total	HrSecondary_Boys	HrSecondary_Girls	HrSecondary_Total
0	A & N Islands	2012-13	0.83	0.51	0.68	Uppe_r_Primary	1.09	1.23	5.57	5.55	5.56	17.66	10.15	14.14
1	A & N Islands	2013-14	1.35	1.06	1.21	NR	1.54	0.51	8.36	5.98	7.2	18.94	12.2	15.87
2	A & N Islands	2014-15	0.47	0.55	0.51	1.44	1.95	1.69	11.47	8.16	9.87	21.05	12.21	16.93
3	Andhra Pradesh	2012-13	3.3	3.05	3.18	3.21	3.51	3.36	12.21	13.25	12.72	2.66	NR	0.35
4	Andhra Pradesh	2013-14	4.31	4.39	4.35	3.46	4.12	3.78	11.95	13.37	12.65	12.65	10.85	11.79
dropout.isna()
State_UT	year	Primary_Boys	Primary_Girls	Primary_Total	Upper Primary_Boys	Upper Primary_Girls	Upper Primary_Total	Secondary _Boys	Secondary _Girls	Secondary _Total	HrSecondary_Boys	HrSecondary_Girls	HrSecondary_Total
0	False	False	False	False	False	False	False	False	False	False	False	False	False	False
1	False	False	False	False	False	False	False	False	False	False	False	False	False	False
2	False	False	False	False	False	False	False	False	False	False	False	False	False	False
3	False	False	False	False	False	False	False	False	False	False	False	False	False	False
4	False	False	False	False	False	False	False	False	False	False	False	False	False	False
...	...	...	...	...	...	...	...	...	...	...	...	...	...	...
105	False	False	False	False	False	False	False	False	False	False	False	False	False	False
106	False	False	False	False	False	False	False	False	False	False	False	False	False	False
107	False	False	False	False	False	False	False	False	False	False	False	False	False	False
108	False	False	False	False	False	False	False	False	False	False	False	False	False	False
109	False	False	False	False	False	False	False	False	False	False	False	False	False	False
110 rows × 14 columns

dropout.columns
Index(['State_UT', 'year', 'Primary_Boys', 'Primary_Girls', 'Primary_Total',
       'Upper Primary_Boys', 'Upper Primary_Girls', 'Upper Primary_Total',
       'Secondary _Boys', 'Secondary _Girls', 'Secondary _Total',
       'HrSecondary_Boys', 'HrSecondary_Girls', 'HrSecondary_Total'],
      dtype='object')
dropout.isna().any()
State_UT               False
year                   False
Primary_Boys           False
Primary_Girls          False
Primary_Total          False
Upper Primary_Boys     False
Upper Primary_Girls    False
Upper Primary_Total    False
Secondary _Boys        False
Secondary _Girls       False
Secondary _Total       False
HrSecondary_Boys       False
HrSecondary_Girls      False
HrSecondary_Total      False
dtype: bool
data_wb=dropout[dropout['State_UT']=='West Bengal']
print(data_wb.head())
        State_UT     year Primary_Boys Primary_Girls Primary_Total  \
104  West Bengal  2012-13         6.88          5.71           6.3   
105  West Bengal  2013-14         3.44          2.37          2.91   
106  West Bengal  2014-15         2.13          0.79          1.47   

    Upper Primary_Boys Upper Primary_Girls Upper Primary_Total  \
104               6.29                4.16                5.18   
105               5.63                 3.1                4.31   
106               5.84                2.88                 4.3   

    Secondary _Boys Secondary _Girls Secondary _Total HrSecondary_Boys  \
104           14.95            19.41             17.3             7.81   
105           16.73            19.77            18.34             8.03   
106           16.33            19.06             17.8             8.18   

    HrSecondary_Girls HrSecondary_Total  
104              8.49              8.13  
105              7.76               7.9  
106              8.04              8.11  
dropout.groupby('State_UT').groups
{'A & N Islands': [0, 1, 2], 'All India': [107, 108, 109], 'Andhra Pradesh': [3, 4, 5], 'Arunachal  Pradesh': [6], 'Arunachal Pradesh': [7, 8], 'Assam': [9, 10, 11], 'Bihar': [12, 13, 14], 'Chandigarh': [15, 16, 17], 'Chhattisgarh': [18, 19, 20], 'Dadra & Nagar Haveli': [21, 22, 23], 'Daman & Diu': [24, 25, 26], 'Delhi': [27, 28, 29], 'Goa': [30, 31, 32], 'Gujarat': [33, 34, 35], 'Haryana': [36, 37, 38], 'Himachal Pradesh': [39, 40, 41], 'Jammu & Kashmir': [42, 43, 44], 'Jharkhand': [45, 46, 47], 'Karnataka': [48, 49, 50], 'Kerala': [51, 52, 53], 'Lakshadweep': [54, 55, 56], 'Madhya  Pradesh': [57], 'Madhya Pradesh': [58, 59], 'Maharashtra': [60, 61, 62], 'Manipur': [63, 64, 65], 'Meghalaya': [66, 67, 68], 'Mizoram': [69, 70, 71], 'Nagaland': [72, 73, 74], 'Odisha': [75, 76, 77], 'Puducherry': [78, 79, 80], 'Punjab': [81, 82, 83], 'Rajasthan': [84, 85, 86], 'Sikkim': [87, 88, 89], 'Tamil  Nadu': [90], 'Tamil Nadu': [91, 92], 'Telangana': [93, 94], 'Tripura': [95, 96, 97], 'Uttar Pradesh': [98, 99, 100], 'Uttarakhand': [101, 102, 103], 'West Bengal': [104, 105, 106]}
dropout['Primary_Boys'].values
array(['0.83', '1.35', '0.47', '3.3', '4.31', '6.57', '11.54', '15.84',
       '11.51', '7.02', '8.19', '16.07', 'NR', '2.38', '0.35', 'NR', 'NR',
       'NR', '4.24', '1.45', '3.08', 'NR', '1.05', '1.6', 'NR', '1.06',
       '1.8', 'NR', 'NR', 'NR', 'NR', '0.08', '0.63', '0.21', '0.5',
       '0.82', '1.48', '0.22', '5.54', '0.51', '0.57', '0.46', '6.8',
       '5.53', '6.98', '7.36', '6.89', '5.91', '3.4', '2.42', '2.03',
       'NR', 'NR', 'NR', '2.3', '0', 'NR', '5.75', '9.91', '6.48', '0.88',
       '0.51', '1.26', '10.24', '17.27', '9.5', '11.32', '11.3', '10.35',
       '24.27', '12.57', '10.17', '7.11', '19.09', '6.18', '3.63', '2.83',
       '2.91', '0.25', '0.76', '0.36', '1.99', '1.35', '2.89', '7.2',
       '7.76', '5.02', '4.78', '5.55', '3.75', '4.02', '0.53', 'NR',
       '6.04', '2.21', '2.31', '3.63', '1.37', '10.53', '7.91', '9.08',
       '1.14', '3.28', '4.37', '6.88', '3.44', '2.13', '4.68', '4.53',
       '4.36'], dtype=object)
dropout=dropout.replace('NR', 0)
dropout['Primary_Boys']=dropout['Primary_Boys'].apply(lambda x: float(x))
primary_boys=dropout['Primary_Boys'].values.astype(np.float32)
dropout['Primary_Girls']=dropout['Primary_Girls'].values.astype(np.float32)
dropout['Upper Primary_Boys'].values
array([0.        , 0.        , 1.44000006, 3.21000004, 3.46000004,
       5.09000015, 4.44000006, 5.86000013, 5.30999994, 7.88999987,
       7.5999999 , 8.74900026, 0.        , 2.76999998, 4.13999987,
       0.        , 0.72000003, 0.01      , 6.09000015, 4.09000015,
       6.46999979, 2.58999991, 3.30999994, 3.70000005, 0.        ,
       3.42000008, 3.1400001 , 0.        , 3.13000011, 0.94999999,
       0.        , 0.        , 0.        , 2.75      , 3.51999998,
       4.6500001 , 0.18000001, 1.97000003, 5.5       , 0.51999998,
       0.60000002, 0.5       , 5.51000023, 3.8599999 , 4.98000002,
       4.98999977, 7.19000006, 8.74900026, 4.96000004, 2.30999994,
       3.46000004, 0.        , 0.        , 0.        , 0.97000003,
       1.15999997, 2.36999989, 6.78999996, 8.74900026, 7.78000021,
       0.88999999, 0.        , 0.88999999, 5.48000002, 7.48000002,
       3.6099999 , 8.43000031, 6.34000015, 6.76999998, 8.74900026,
       6.61000013, 5.46000004, 8.74900026, 8.74900026, 7.86999989,
       4.0999999 , 3.1099999 , 4.11000013, 0.33000001, 0.37      ,
       0.44      , 2.57999992, 2.51999998, 2.95000005, 2.8599999 ,
       4.48999977, 2.53999996, 2.5999999 , 6.3499999 , 2.06999993,
       0.38      , 4.38000011, 0.        , 4.63000011, 2.43000007,
       3.0999999 , 3.21000004, 2.36999989, 0.        , 0.        ,
       0.77999997, 0.        , 1.77999997, 0.79000002, 6.28999996,
       5.63000011, 5.84000015, 2.29999995, 3.08999991, 3.49000001])
dropout=dropout.replace('Uppe_r_Primary',0)
dropout['Upper Primary_Boys']=dropout['Upper Primary_Boys'].values.astype(np.float32)
dropout['Upper Primary_Girls']=dropout['Upper Primary_Girls'].values.astype(np.float32)
dropout['Secondary _Boys']=dropout['Secondary _Boys'].values.astype(np.float32)
dropout['Secondary _Girls']=dropout['Secondary _Girls'].values.astype(np.float32)

dropout['HrSecondary_Boys']=dropout['HrSecondary_Boys'].values.astype(np.float32)
dropout['HrSecondary_Girls']=dropout['HrSecondary_Girls'].values.astype(np.float32)
dropout.describe()
Primary_Boys	Primary_Girls	Upper Primary_Boys	Upper Primary_Girls	Secondary _Boys	Secondary _Girls	HrSecondary_Boys	HrSecondary_Girls
count	110.000000	110.000000	110.000000	110.000000	110.000000	110.000000	110.000000	110.000000
mean	4.293455	4.010818	3.359854	3.966073	16.853643	15.993138	6.691627	4.662882
std	4.674719	4.553512	2.689052	2.827656	7.112603	7.850483	6.483881	4.398286
min	0.000000	0.000000	0.000000	0.000000	6.199500	4.630000	0.000000	0.000000
25%	0.540000	0.590000	0.782500	1.580000	11.312500	9.385000	0.057500	0.000000
50%	2.900000	2.440000	3.120000	3.535000	16.105000	14.985000	5.680000	3.880000
75%	6.742500	5.870000	5.422500	5.835000	23.012500	21.682500	11.765000	8.470000
max	24.270000	23.930000	8.749001	9.928000	29.894001	30.582500	19.176500	13.064500
dropout.info()
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 110 entries, 0 to 109
Data columns (total 14 columns):
 #   Column               Non-Null Count  Dtype  
---  ------               --------------  -----  
 0   State_UT             110 non-null    object 
 1   year                 110 non-null    object 
 2   Primary_Boys         110 non-null    float64
 3   Primary_Girls        110 non-null    float32
 4   Primary_Total        110 non-null    object 
 5   Upper Primary_Boys   110 non-null    float32
 6   Upper Primary_Girls  110 non-null    float32
 7   Upper Primary_Total  110 non-null    object 
 8   Secondary _Boys      110 non-null    float32
 9   Secondary _Girls     110 non-null    float32
 10  Secondary _Total     110 non-null    object 
 11  HrSecondary_Boys     110 non-null    float32
 12  HrSecondary_Girls    110 non-null    float32
 13  HrSecondary_Total    110 non-null    object 
dtypes: float32(7), float64(1), object(6)
memory usage: 9.1+ KB
