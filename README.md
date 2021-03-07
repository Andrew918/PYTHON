import os
from PyPDF2 import PdfFileMerger

source_dir = os.getcwd()
merger = PdfFileMerger()

for item in os.listdir(source_dir):
    if item.endswith("pdf"):
        merger.append(item)
merger.write("./Total.pdf")
merger.close()

-------------------------------------------------------------------------------------------------------------------------
import pandas as pd

T1 = pd.read_excel('C:\\Users\\Andern Hu\\Desktop\\Pandas\\Practice.xlsx', 'Sheet1')

T2 = pd.read_excel('C:\\Users\\Andern Hu\\Desktop\\Pandas\\Practice2.xlsx', 'Sheet2')

Orders = pd.merge(left = T1, right = T2, left_on = ['Customer','Date'], right_on = ['Customer','Date2'], how = 'right')

Orders[['Customer', 'Date2','Q','Test']]

-------------------------------------------------------------------------------------------------------------------------
import pandas as pd

file = pd.ExcelFile('C:\\Users\\yhu\\OneDrive - OneWorkplace\\Documents\\BB Triggers Weekly\
\\ECOMM_ANALYTICS_DASHBOARD_RESPONSE_REPORT_20210301.xls')

#file = pd.ExcelFile('C:\\Users\\yhu\\OneDrive - OneWorkplace\\Documents\\ECOMM 20210101.xlsx')

JAN = pd.read_excel(file, 'EAD RESP TOUCH DET - JAN', skiprows = 1)

#df = pd.concat([JAN,FEB,MAR,APR,MAY,JUN,JUL,AUG,SEP,OCT,NOV,DEC])

df = pd.concat([JAN,FEB,MAR])

df['EVENT_DT_CAT'] = df['EVENT_DT_CAT'].str.replace('_','/')

#df[['EVENT_DT_CAT', 'CAMPAIGN_SEGMENT']]

#df.to_csv('C:\\Users\\yhu\\OneDrive - OneWorkplace\\Documents\\\\BB Triggers Weekly\\ALL_20210301.csv', index = False)

---------------------------------------------------------------------------------------------------------------------------

import pandas as pd

df = pd.read_csv('C:\\Users\\yhu\\OneDrive - OneWorkplace\\Documents\\BB Triggers Weekly\\ALL_20210301.csv')

df = df[df['CAMPAIGN_SEGMENT'].str.contains('cart',case = False)]

R_Products = df[df['CAMPAIGN_SEGMENT'].str.contains('mob|tv|bundle|wls|wireless',case = False)].index

df.drop(R_Products, inplace = True)

R_Dates = df[df['EVENT_DT_CAT'] > '2021/02/27'].index

df.drop(R_Dates, inplace = True)

#df.to_csv('C:\\Users\\yhu\\OneDrive - OneWorkplace\\Documents\\\\BB Triggers Weekly\\BBWEEKLY_20210301.csv', index = False)

----------------------------------------------------------------------------------------------------------------------------

total = df.groupby([date]).['ipbbsales','dtvsales','atttvsales'].sum().reset_index()


