import os
from PyPDF2 import PdfFileMerger

source_dir = os.getcwd()
merger = PdfFileMerger()

for item in os.listdir(source_dir):
    if item.endswith("pdf"):
        merger.append(item)
merger.write("./Total.pdf")
merger.close()

------------------------
import pandas as pd

T1 = pd.read_excel('C:\\Users\\Andern Hu\\Desktop\\Pandas\\Practice.xlsx', 'Sheet1')

T2 = pd.read_excel('C:\\Users\\Andern Hu\\Desktop\\Pandas\\Practice2.xlsx', 'Sheet2')

Orders = pd.merge(left = T1, right = T2, left_on = ['Customer','Date'], right_on = ['Customer','Date2'], how = 'right')

Orders[['Customer', 'Date2','Q','Test']]

------------------------
