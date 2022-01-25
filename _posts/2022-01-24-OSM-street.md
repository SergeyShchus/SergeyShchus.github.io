---
title: "Впорядкованість вулиць міста з ОСМ"
categories:
  - Notebooks
tags:
  - OSM
  - street
  - town
  - python
  - google colab
  - notebook
---

![compass](https://miro.medium.com/max/1040/1*U6fK1aol_4nVQJ3eVJJtYQ.jpeg?raw=true)

Уявіть собі компас. У кожного компаса є стрілка, яка завжди вказує на північ. За допомогою компаса ми завжди можемо дізнатись розташування сторін світу та пройти по азімуту від точки до точки.
А тепер уявимо, що замість стрілки на компас ми покладемо вулицю. Наприклад, ту, на якій знаходимось зараз, або вулицю на якій народились. Куди в такому випадку покаже “стрілка”? У якому напрямку прокладена ця вулиця?


![compass](https://miro.medium.com/max/4800/1*pC2xFQsUFg0Hniu3GRRSVQ.png?raw=true)

Кожне місто планується, відштовхуючісь від місцини, на якій знаходиться, історичних подій, наявності промисловості тощо. Надихаючись дослідженням Geoff Boeing та його [статтєю](https://appliednetsci.springeropen.com/articles/10.1007/s41109-019-0189-1) можна дослідити “розу доріг” різних міст та побачити особливості планування кожного з них. Для цього можна використати загальнодоступні дані Open Street Map.


![compass](https://miro.medium.com/max/1400/1*k8Z0F4FVGXaswkEZOJLdQw.jpeg?raw=true)

На прикладі двох міст наочно видно, що може бути досить продумане планування, а може бути і хаотичне.
Отже, хто має сітку, а хто немає? Кожне міст представлено полярною гістограмою, що показує, як орієнтовані його вулиці. Напрямок кожного стовпця є азимутом вулиці по компасу (у цьому осередку гістограми), довжина представляє відносну частоту вулиць із цими азимутами.
Скористуємось для аналізу пакетом для роботи з Open Street Map у Python — OSMNX.

    !pip install osmnx

--

Інсталюємо пакет та імпортуємо необхідне до Google Colab Notebook


    import matplotlib.pyplot as plt
    import numpy as np
    import osmnx as ox
    import geopandas as gpd
    %matplotlib inline
    ox.__version__
    %matplotlib inline
    weight_by_length = False
    ox.__version__
    # turn response caching off
    ox.config(use_cache=False)
    # turn it back on and turn on/off logging to your console
    ox.config(use_cache=True, log_console=False)

--

Знаходимо місцини, які хочемо переглянути та візуалізуємо для аналізу


    # download/model a street network for some city then visualize it
    G = ox.graph_from_place("Yaremche, Ukraine", network_type="drive")
    fig, ax = ox.plot_graph(G)
--

Робимо перелік усіх місць для компанування на одній дошці


    # verify OSMnx geocodes each query to what you expect (i.e., a [multi]polygon geometry)
    gdf = ox.geocode_to_gdf(list(places.values()))
    gdf
--

Та формуємо звіт, який зберігаємо у каталозі на Google drive


    # create figure and axes
    n = len(places)
    ncols = int(np.ceil(np.sqrt(n)))
    nrows = int(np.ceil(n / ncols))
    figsize = (ncols * 5, nrows * 5)
    fig, axes = plt.subplots(nrows, ncols, figsize=figsize, subplot_kw={"projection": "polar"})
    # plot each city's polar histogram
    for ax, place in zip(axes.flat, sorted(places.keys())):
    print(ox.utils.ts(), place)
    # get undirected graphs with edge bearing attributes
    G = ox.graph_from_place(place, network_type="drive")
    Gu = ox.add_edge_bearings(ox.get_undirected(G))
    fig, ax = ox.bearing.plot_orientation(Gu, ax=ax, title=place, area=True)
    # add figure title and save image
    suptitle_font = {
    "family": "DejaVu Sans",
    "fontsize": 60,
    "fontweight": "normal",
    "y": 1,
    }
    fig.suptitle("Орієнтація вуличної мережі міста", **suptitle_font)
    fig.tight_layout()
    fig.subplots_adjust(hspace=0.35)
    fig.savefig("/content/image/street-orientations_05.png", facecolor="w", dpi=100, bbox_inches="tight")
    plt.close()
--


![compass](https://miro.medium.com/max/2000/1*-8yzFRuE3rGRC8v1ldi8qQ.png?raw=true)


На зображенні можна побачити різницю у плануванні міст. Частина має чітке зонування кварталів за виключенням незначних провулків та вуличок, найбільші ж міста, навпаки, мають хаотичне планування з напрямком вулиць на усі сторони світу.


![compass](https://miro.medium.com/max/1400/1*P_L4p1IzsBTJoFIOQ0supw.png?raw=true)



![compass](https://miro.medium.com/max/1400/1*gxv08hpGatQ5Y84oji7oCg.png?raw=true)
