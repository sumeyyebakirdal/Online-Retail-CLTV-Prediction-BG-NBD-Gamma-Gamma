{
 "cells": [
  {
   "cell_type": "code",
   "execution_count": 1,
   "id": "91b600bf",
   "metadata": {
    "_cell_guid": "b1076dfc-b9ad-4769-8c92-a6c4dae69d19",
    "_uuid": "8f2839f25d086af736a60e9eeb907d3b93b6e0e5",
    "execution": {
     "iopub.execute_input": "2026-02-25T13:18:10.225547Z",
     "iopub.status.busy": "2026-02-25T13:18:10.224972Z",
     "iopub.status.idle": "2026-02-25T13:18:10.988478Z",
     "shell.execute_reply": "2026-02-25T13:18:10.987645Z"
    },
    "papermill": {
     "duration": 0.76881,
     "end_time": "2026-02-25T13:18:10.989970",
     "exception": false,
     "start_time": "2026-02-25T13:18:10.221160",
     "status": "completed"
    },
    "tags": []
   },
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "/kaggle/input/datasets/lakshmi25npathi/online-retail-dataset/online_retail_II.xlsx\n"
     ]
    }
   ],
   "source": [
    "# This Python 3 environment comes with many helpful analytics libraries installed\n",
    "# It is defined by the kaggle/python Docker image: https://github.com/kaggle/docker-python\n",
    "# For example, here's several helpful packages to load\n",
    "\n",
    "import numpy as np # linear algebra\n",
    "import pandas as pd # data processing, CSV file I/O (e.g. pd.read_csv)\n",
    "\n",
    "# Input data files are available in the read-only \"../input/\" directory\n",
    "# For example, running this (by clicking run or pressing Shift+Enter) will list all files under the input directory\n",
    "\n",
    "import os\n",
    "for dirname, _, filenames in os.walk('/kaggle/input'):\n",
    "    for filename in filenames:\n",
    "        print(os.path.join(dirname, filename))\n",
    "\n",
    "# You can write up to 20GB to the current directory (/kaggle/working/) that gets preserved as output when you create a version using \"Save & Run All\" \n",
    "# You can also write temporary files to /kaggle/temp/, but they won't be saved outside of the current session"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 2,
   "id": "16cc345c",
   "metadata": {
    "execution": {
     "iopub.execute_input": "2026-02-25T13:18:10.993716Z",
     "iopub.status.busy": "2026-02-25T13:18:10.993349Z",
     "iopub.status.idle": "2026-02-25T13:18:55.697054Z",
     "shell.execute_reply": "2026-02-25T13:18:55.696222Z"
    },
    "papermill": {
     "duration": 44.708739,
     "end_time": "2026-02-25T13:18:55.699969",
     "exception": false,
     "start_time": "2026-02-25T13:18:10.991230",
     "status": "completed"
    },
    "tags": []
   },
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "Collecting lifetimes\r\n",
      "  Downloading Lifetimes-0.11.3-py3-none-any.whl.metadata (4.8 kB)\r\n",
      "Requirement already satisfied: numpy>=1.10.0 in /usr/local/lib/python3.12/dist-packages (from lifetimes) (2.0.2)\r\n",
      "Requirement already satisfied: scipy>=1.0.0 in /usr/local/lib/python3.12/dist-packages (from lifetimes) (1.16.3)\r\n",
      "Requirement already satisfied: pandas>=0.24.0 in /usr/local/lib/python3.12/dist-packages (from lifetimes) (2.3.3)\r\n",
      "Requirement already satisfied: autograd>=1.2.0 in /usr/local/lib/python3.12/dist-packages (from lifetimes) (1.8.0)\r\n",
      "Requirement already satisfied: dill>=0.2.6 in /usr/local/lib/python3.12/dist-packages (from lifetimes) (0.3.8)\r\n",
      "Requirement already satisfied: python-dateutil>=2.8.2 in /usr/local/lib/python3.12/dist-packages (from pandas>=0.24.0->lifetimes) (2.9.0.post0)\r\n",
      "Requirement already satisfied: pytz>=2020.1 in /usr/local/lib/python3.12/dist-packages (from pandas>=0.24.0->lifetimes) (2025.2)\r\n",
      "Requirement already satisfied: tzdata>=2022.7 in /usr/local/lib/python3.12/dist-packages (from pandas>=0.24.0->lifetimes) (2025.3)\r\n",
      "Requirement already satisfied: six>=1.5 in /usr/local/lib/python3.12/dist-packages (from python-dateutil>=2.8.2->pandas>=0.24.0->lifetimes) (1.17.0)\r\n",
      "Downloading Lifetimes-0.11.3-py3-none-any.whl (584 kB)\r\n",
      "\u001b[2K   \u001b[90m━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━\u001b[0m \u001b[32m584.2/584.2 kB\u001b[0m \u001b[31m10.8 MB/s\u001b[0m eta \u001b[36m0:00:00\u001b[0m\r\n",
      "\u001b[?25hInstalling collected packages: lifetimes\r\n",
      "Successfully installed lifetimes-0.11.3\r\n",
      "--- UK Customers: Top 10 by 6-Month CLTV ---\n",
      "             recency       T  frequency  monetary  cltv_6_month  cltv_1_month  cltv_12_month segment\n",
      "Customer ID                                                                                         \n",
      "18102.0000   52.2857 52.5714         60 3582.7037    85596.3189    14875.4326    163487.0583       A\n",
      "14096.0000   13.8571 14.5714         17 3159.4912    55654.1274     9856.4348    104907.4989       A\n",
      "17450.0000   51.2857 52.5714         46 2627.0337    48485.8846     8426.5013     92603.9163       A\n",
      "17511.0000   52.8571 53.4286         31 2921.8200    36794.3729     6393.8510     70280.7843       A\n",
      "16684.0000   50.4286 51.2857         28 2118.9150    25068.9600     4358.5975     47863.6232       A\n",
      "13694.0000   52.7143 53.4286         50 1267.2430    25057.6376     4353.9241     47866.1460       A\n",
      "14088.0000   44.5714 46.1429         13 3860.1431    25012.9687     4355.9805     47694.5283       A\n",
      "15311.0000   53.2857 53.4286         91  667.5945    23590.6036     4098.7226     45066.4153       A\n",
      "13089.0000   52.2857 52.8571         97  605.2472    22929.3014     3984.3208     43798.6504       A\n",
      "15061.0000   52.5714 53.2857         48 1108.1121    21118.7578     3669.6615     40340.6517       A\n"
     ]
    }
   ],
   "source": [
    "# 1. Kütüphane Kurulumu (Kaggle ortamında lifetimes yüklü gelmez)\n",
    "!pip install lifetimes\n",
    "\n",
    "import pandas as pd\n",
    "import datetime as dt\n",
    "from lifetimes import BetaGeoFitter\n",
    "from lifetimes import GammaGammaFitter\n",
    "\n",
    "# Çıktı ayarları\n",
    "pd.set_option('display.max_columns', None)\n",
    "pd.set_option('display.width', 500)\n",
    "pd.set_option('display.float_format', lambda x: '%.4f' % x)\n",
    "\n",
    "###############################################################\n",
    "# GÖREV 1: Veri Hazırlama (Data Preparation)\n",
    "###############################################################\n",
    "\n",
    "# Belirttiğin tam dosya yolu\n",
    "file_path = \"/kaggle/input/datasets/lakshmi25npathi/online-retail-dataset/online_retail_II.xlsx\"\n",
    "\n",
    "# Excel dosyasını oku (Kaggle'da Excel okumak biraz vakit alabilir, lütfen bekleyiniz)\n",
    "df_ = pd.read_excel(file_path, sheet_name=\"Year 2010-2011\")\n",
    "df = df_.copy()\n",
    "\n",
    "def outlier_thresholds(dataframe, variable):\n",
    "    quartile1 = dataframe[variable].quantile(0.01)\n",
    "    quartile3 = dataframe[variable].quantile(0.99)\n",
    "    interquantile_range = quartile3 - quartile1\n",
    "    up_limit = quartile3 + 1.5 * interquantile_range\n",
    "    low_limit = quartile1 - 1.5 * interquantile_range\n",
    "    return low_limit, up_limit\n",
    "\n",
    "def replace_with_thresholds(dataframe, variable):\n",
    "    low_limit, up_limit = outlier_thresholds(dataframe, variable)\n",
    "    dataframe.loc[(dataframe[variable] < low_limit), variable] = round(low_limit, 0)\n",
    "    dataframe.loc[(dataframe[variable] > up_limit), variable] = round(up_limit, 0)\n",
    "\n",
    "# Veri Ön İşleme adımları\n",
    "df.dropna(inplace=True)\n",
    "df = df[~df[\"Invoice\"].astype(str).str.contains(\"C\", na=False)]\n",
    "df = df[df[\"Quantity\"] > 0]\n",
    "df = df[df[\"Price\"] > 0]\n",
    "\n",
    "# PDF Talimatı: Sadece United Kingdom (UK) müşterileri\n",
    "df = df[df[\"Country\"] == \"United Kingdom\"]\n",
    "\n",
    "replace_with_thresholds(df, \"Quantity\")\n",
    "replace_with_thresholds(df, \"Price\")\n",
    "\n",
    "df[\"TotalPrice\"] = df[\"Quantity\"] * df[\"Price\"]\n",
    "df[\"InvoiceDate\"] = pd.to_datetime(df[\"InvoiceDate\"])\n",
    "today_date = dt.datetime(2011, 12, 11)\n",
    "\n",
    "###############################################################\n",
    "# GÖREV 2: CLTV Veri Yapısının Oluşturulması (RFM)\n",
    "###############################################################\n",
    "\n",
    "cltv_df = df.groupby('Customer ID').agg({\n",
    "    'InvoiceDate': [lambda date: (date.max() - date.min()).days,\n",
    "                    lambda date: (today_date - date.min()).days],\n",
    "    'Invoice': lambda num: num.nunique(),\n",
    "    'TotalPrice': lambda total_price: total_price.sum()\n",
    "})\n",
    "\n",
    "cltv_df.columns = cltv_df.columns.droplevel(0)\n",
    "cltv_df.columns = ['recency', 'T', 'frequency', 'monetary']\n",
    "\n",
    "# Monetary: Satın alma başına ortalama kazanç\n",
    "cltv_df[\"monetary\"] = cltv_df[\"monetary\"] / cltv_df[\"frequency\"]\n",
    "\n",
    "# Haftalık birime çevirme\n",
    "cltv_df[\"recency\"] = cltv_df[\"recency\"] / 7\n",
    "cltv_df[\"T\"] = cltv_df[\"T\"] / 7\n",
    "\n",
    "# BG-NBD modeli için en az 2 alışveriş yapmış olanlar seçilir\n",
    "cltv_df = cltv_df[(cltv_df['frequency'] > 1)]\n",
    "\n",
    "###############################################################\n",
    "# GÖREV 3: Modelleme ve CLTV Tahmini\n",
    "###############################################################\n",
    "\n",
    "# BG/NBD Model Kurulumu\n",
    "bgf = BetaGeoFitter(penalizer_coef=0.001)\n",
    "bgf.fit(cltv_df['frequency'], cltv_df['recency'], cltv_df['T'])\n",
    "\n",
    "# Gamma-Gamma Model Kurulumu\n",
    "ggf = GammaGammaFitter(penalizer_coef=0.01)\n",
    "ggf.fit(cltv_df['frequency'], cltv_df['monetary'])\n",
    "\n",
    "# PDF Görev 1: 6 Aylık CLTV\n",
    "cltv_df[\"cltv_6_month\"] = ggf.customer_lifetime_value(bgf, cltv_df['frequency'], cltv_df['recency'], cltv_df['T'], cltv_df['monetary'], time=6, freq=\"W\", discount_rate=0.01)\n",
    "\n",
    "# PDF Görev 2: 1 Ay ve 12 Aylık CLTV\n",
    "cltv_df[\"cltv_1_month\"] = ggf.customer_lifetime_value(bgf, cltv_df['frequency'], cltv_df['recency'], cltv_df['T'], cltv_df['monetary'], time=1, freq=\"W\", discount_rate=0.01)\n",
    "cltv_df[\"cltv_12_month\"] = ggf.customer_lifetime_value(bgf, cltv_df['frequency'], cltv_df['recency'], cltv_df['T'], cltv_df['monetary'], time=12, freq=\"W\", discount_rate=0.01)\n",
    "\n",
    "# Segmentasyon (6 aylık değere göre)\n",
    "cltv_df[\"segment\"] = pd.qcut(cltv_df[\"cltv_6_month\"], 4, labels=[\"D\", \"C\", \"B\", \"A\"])\n",
    "\n",
    "# Sonuçları Gözlemleme\n",
    "print(\"--- UK Customers: Top 10 by 6-Month CLTV ---\")\n",
    "print(cltv_df.sort_values(\"cltv_6_month\", ascending=False).head(10))"
   ]
  }
 ],
 "metadata": {
  "kaggle": {
   "accelerator": "nvidiaTeslaT4",
   "dataSources": [
    {
     "databundleVersionId": 826251,
     "datasetId": 421200,
     "sourceId": 804181,
     "sourceType": "datasetVersion"
    }
   ],
   "dockerImageVersionId": 31287,
   "isGpuEnabled": true,
   "isInternetEnabled": true,
   "language": "python",
   "sourceType": "notebook"
  },
  "kernelspec": {
   "display_name": "Python 3",
   "language": "python",
   "name": "python3"
  },
  "language_info": {
   "codemirror_mode": {
    "name": "ipython",
    "version": 3
   },
   "file_extension": ".py",
   "mimetype": "text/x-python",
   "name": "python",
   "nbconvert_exporter": "python",
   "pygments_lexer": "ipython3",
   "version": "3.12.12"
  },
  "papermill": {
   "default_parameters": {},
   "duration": 48.445113,
   "end_time": "2026-02-25T13:18:56.118953",
   "environment_variables": {},
   "exception": null,
   "input_path": "__notebook__.ipynb",
   "output_path": "__notebook__.ipynb",
   "parameters": {},
   "start_time": "2026-02-25T13:18:07.673840",
   "version": "2.6.0"
  }
 },
 "nbformat": 4,
 "nbformat_minor": 5
}
