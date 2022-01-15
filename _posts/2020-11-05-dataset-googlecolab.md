---
title: "Використання сторонніх датасетів в Google Colab"
categories:
  - Blog
tags:
  - Post Formats
  - Google colab
  - dataset
---



Часто є потреба в використанні, або перегляді датасету з якогось сайту або Гітхабу. Для цього зовсім не обов'язково завантажувати всі файли до себе на ноутбук або хмару.
Додати датасет до свого проекту дуже просто.
Додаємо сторонній архів (для прикладу - zip з навчальної страниці Autogis на Гітхабі):

    !wget https://github.com/AutoGIS/data/raw/master/L2_data.zip

Розпакувати архів:

    !unzip L2_data.zip

Та переглянути вміст датасету:

    !ls L2_data

![alt text](https://cdn-images-1.medium.com/max/1600/1*QXnDNx2hfC9hGckMYaVGgA.png?raw=true)

Ну і далі вже можемо зробити будь - яку роботу з доступними гіс-даними. Наприклад:

    import os
    # Define path to folder
    input_folder = r"L2_data/NLS/2018/L4/L41/L4132R.shp"
    # Join folder path and filename
    fp = os.path.join(input_folder, "m_L4132R_p.shp")
    # Print out the full file path
    print(fp)

L2_data/NLS/2018/L4/L41/L4132R.shp/m_L4132R_p.shp

    import geopandas as gpd
    # Read file using gpd.read_file()
    data = gpd.read_file(fp)
    type(data)

geopandas.geodataframe.GeoDataFrame

    data.columns.values

array(['TEKSTI', 'RYHMA', 'LUOKKA', 'TASTAR', 'KORTAR', 'KORARV', 'KULKUTAPA', 'KOHDEOSO', 'AINLAHDE', 'SYNTYHETKI', 'KUOLHETKI', 'KARTOGLK', 'ALUEJAKOON', 'VERSUH', 'SUUNTA', 'SIIRT_DX', 'SIIRT_DY', 'KORKEUS', 'ATTR2', 'ATTR3', 'geometry'], dtype=object)

    data = data[['RYHMA', 'LUOKKA',  'geometry']]
    colnames = {'RYHMA':'GROUP', 'LUOKKA':'CLASS'}
    data.rename(columns=colnames, inplace=True)
    data.head()

![alt text](https://cdn-images-1.medium.com/max/1600/1*kegLR1AHCoJGLDJNkO7gOw.png?raw=true)

Виведення готового набору даних на мапі:

    data.plot()

![alt text](https://cdn-images-1.medium.com/max/1600/1*YDtmxmnrkkr37ji9RwD6Qg.png?raw=true)