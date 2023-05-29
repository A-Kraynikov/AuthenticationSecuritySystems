# Сбор и аналитическая обработка информации о сетевом трафике

## Цель работы

1. Развить практические навыки использования современного стека
инструментов сбора и аналитической обработки информации о сетвом трафике

2. Освоить базовые подходы блокировки нежелательного сетевого трафика

3. Закрепить знания о современных сетевых протоколах прикладного уровня

## Ход выполнения практической работы

1. C помощью Wireshark был собран сетевой трафик объёмом 3,77 МБ  

![screen_2_01](https://github.com/A-Kraynikov/AuthenticationSecuritySystems/assets/90748885/594e0138-735e-4eec-8819-0763eb2da9b8)  

2.C помощью утилиты Zeek была выделена метаинформация сетевого трафика  

3.Загрузим и соединим файлы, содержащие списки источников нежелательного трафика:  

    mkdir hosts
    cd hosts
    wget -q https://github.com/StevenBlack/hosts/raw/master/data/add.2o7Net/hosts
    wget -q https://raw.githubusercontent.com/StevenBlack/hosts/master/data/KADhosts/hosts
    wget -q https://raw.githubusercontent.com/StevenBlack/hosts/master/data/yoyo.org/hosts
    wget -q https://raw.githubusercontent.com/StevenBlack/hosts/master/data/tiuxo/hosts
    wget -q https://raw.githubusercontent.com/StevenBlack/hosts/master/data/URLHaus/hosts
    sort hosts* | grep "^[^#;]" | uniq > final_hosts
    mv final_hosts ../Fhosts.data
    cd ..
    rm -rf hosts

4.Установим библиотеку Zeek Analysis Toolkit для преобразоваия метаинформации сетевого трафика в формате log-файлов в датафрейм Pandas:  

    pip -q install zat

5.После установки библиотеки преобразуем файл dns.log в датафрейм Pandas:  

    import warnings
    warnings.filterwarnings("ignore", category=RuntimeWarning)
    import numpy as np
    import pandas as pd
    from zat.log_to_dataframe import LogToDataFrame
    df = LogToDataFrame()
    z_df = df.create_dataframe('dns.log')
    domains = z_df['query']
    domains.name = 'CNAME'

6.Затем преобразуем файл со списком источников нежелательного трафика:  

    df = pd.read_csv('Fhosts.data', sep="\s+", names=['redirect_to','CNAME'])
    bd_domains = df['CNAME']

7.Объединим два полученных датафрейма и получим процент нежелательного трафика:  

    merged = pd.merge(domains, bd_domains, on='CNAME', how='left', indicator='exists')
    merged['exists'] = np.where(merged.exists == 'both', True,False)
    count = merged['exists'].value_counts()[1]
    percentile = round(merged['exists'].value_counts(normalize=True)[1]*100, 2)
    print("DNS имен из списков трафика: {}.".format(count), "Процент нежелательного трафика: {}%.".format(percentile), sep='\n')



## Оценка результата  

В результате лабораторной работы мы смогли определить нежелательный трафик.  

## Вывод  

В ходе лабораторной работы мы научились анализировать сетевой трафик.  
