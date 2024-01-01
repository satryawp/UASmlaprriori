# Laporan Proyek Machine Learning

### Nama : Satrya wirangga permana putra

### Nim : 211351138

### Kelas : Pagi B

## Domain Proyek
Grocery Store atau toko kelontong adalah toko ritel jasa makanan yang terutama menjual berbagai macam produk makanan, yang mungkin segar atau dikemas. Namun, dalam penggunaan sehari-hari di AS, "toko kelontong" adalah sinonim untuk supermarket, dan tidak digunakan untuk merujuk pada jenis toko lain yang menjual bahan makanan. Di Inggris, toko-toko yang menjual makanan dibedakan menjadi grocers atau grocery shops (walaupun dalam penggunaan sehari-hari, orang biasanya menggunakan istilah "supermarket" atau "corner store"[4] atau "toko serba ada").

## Business Understanding

Dikarenakan pelanggan kadangkala mengalami kesulitan dalam menemukan barang yang ingin dibeli, kami bermaksud untuk memproyeksikan frekuensi pembelian suatu barang dengan mengetahui riwayat pembelian sebelumnya. Hal ini bertujuan agar kami dapat menempatkan barang kedua secara strategis, berdekatan dengan barang pertama, untuk meningkatkan kenyamanan dan kemudahan bagi pelanggan.

### Problem Statements

Menjelaskan pernyataan masalah latar belakang:

- Pembeli mengalami kesulitan dalam menemukan barang yang ingin dibeli.
- Toko tidak dapat memberikan bantuan yang memadai bagi pelanggan dalam pencarian barang.
- Untuk meningkatkan kenyamanan pelanggan, kami berkomitmen untuk mengoptimalkan pengalaman berbelanja dengan menyediakan petunjuk yang jelas dan memindahkan barang-barang terkait secara strategis, sehingga pembeli dapat dengan mudah menemukan dan memilih produk yang mereka butuhkan

### Goals Dengan Solution Statements

Menjelaskan tujuan dari pernyataan masalah:

-  Melakukan penelitian menggunakan algoritma Apriori untuk meramalkan produk selanjutnya yang kemungkinan akan dibeli oleh pelanggan.
-   Mendapatkan wawasan mengenai produk-produk yang sering dibeli secara bersamaan oleh pelanggan.

## Import Dataset
\[Groceries dataset for Market Basket Analysis(MBA)\]\[<https://www.kaggle.com/datasets/rashikrahmanpritom/groceries-dataset-for-market-basket-analysismba/data>)

Pertama-tama, saya mengunggah file kaggle.json untuk memperoleh akses ke platform Kaggle.

``` python
from google.colab import files
files.upload()
```
Berikutnya, saya membuat direktori dan mengatur izin pada skrip ini

``` python
!mkdir -p ~/.kaggle
!cp kaggle.json ~/.kaggle/
!chmod 600 ~/.kaggle/kaggle.json
!ls ~/.kaggle
```
Lalu mendownload dataset tersebut

``` python
!kaggle datasets download -d rashikrahmanpritom/groceries-dataset-for-market-basket-analysismba
```
lalu saya melakukan unziping data

```python
!mkdir groceries-dataset-for-market-basket-analysismba
!unzip groceries-dataset-for-market-basket-analysismba.zip -d groceries-dataset-for-market-basket-analysismba
!ls groceries-dataset-for-market-basket-analysismba
```
## Import Library

lalu saya import library yang akan digunakan

``` python
import numpy as np
import pandas as pd
from mlxtend.preprocessing import TransactionEncoder
from mlxtend.frequent_patterns import apriori, association_rules
import matplotlib.pyplot as plt
import seaborn as sns
import plotly.graph_objects as go
import plotly.express as px
import plotly.figure_factory as ff
```
## Data Discovery

kemudian saya melakukan pembacaan data 

![image](