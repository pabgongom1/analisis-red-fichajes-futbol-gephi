# Análisis de red social del mercado europeo de fichajes

> 🇬🇧 [English version](README.md)

Proyecto de Minería de Medios Sociales — Máster en Ciencia de Datos, Universidad de Granada.

Este proyecto modela el mercado europeo de fichajes de fútbol como una red dirigida y ponderada, y la analiza con técnicas de análisis de redes sociales en **Gephi**: métricas globales, centralidad de actores y detección de comunidades.

## La red

Los nodos son clubes; una arista dirigida y ponderada del club A al B significa que A vendió o cedió jugadores a B, ponderada por el número de jugadores. Los datos cubren los traspasos entre las **siete principales ligas europeas** (LaLiga, Ligue 1, Liga Portugal, Serie A, Premier League, Bundesliga, Eredivisie) durante cinco temporadas (2017/18–2021/22). Los clubes ajenos a estas ligas se agrupan en nodos regionales (p. ej. *free agents*, *UK*, *South America*).

La red tiene **309 nodos y 3.488 aristas**, formando una única componente gigante que engloba todo el grafo.

## Qué se analizó

**1. Estructura global.** La red es muy dispersa (densidad 0,037) pero muestra un claro efecto mundo pequeño: la distancia media es de solo 2,86 con un diámetro de 6, de modo que dos clubes cualesquiera están conectados por menos de tres intermediarios de media. La distribución de grados está muy sesgada a la derecha (tipo ley de potencias), revelando unos pocos hubs dominantes entre muchos clubes de grado bajo.

**2. Centralidad de actores** (cuatro medidas):
- **Grado** — dominado por nodos regionales y de agentes libres; entre clubes individuales, el **AS Mónaco** lidera con el perfil de entrada/salida más equilibrado, actuando como el gran dinamizador del mercado.
- **Intermediación** — dominada por los clubes portugueses (Benfica, Porto, Sporting), lo que confirma su papel de *puentes* que canalizan talento (especialmente sudamericano) hacia las ligas de élite.
- **Cercanía** — varios nodos alcanzan el máximo, evidencia de un mercado fuertemente conectado y sin islas aisladas.
- **Vector propio** — AS Roma, Fiorentina, Genoa, Sevilla y Mónaco encabezan la lista, identificando un círculo cerrado de clubes de alto prestigio que negocian sobre todo entre ellos.

**3. Detección de comunidades.** Se aplicaron **Louvain** y **Leiden** variando la resolución, evaluando la robustez de la modularidad y la coherencia semántica. Ambos métodos coinciden en una gran comunidad puente Portugal–Holanda–Sudamérica. Difieren en Inglaterra y Alemania: Louvain mantiene cada liga como su propia comunidad, mientras que Leiden las fusiona. Se seleccionó la **partición de Louvain con resolución 0.9 (6 comunidades)** como definitiva, por ser la que mejor equilibra calidad estructural e interpretabilidad — cada liga importante se corresponde limpiamente con una comunidad.

## Estructura del repositorio

```
.
├── README.md          # Versión en inglés
├── README.es.md       # Este archivo (español)
├── practica.gephi     # Proyecto de Gephi (red, layout, métricas, particiones)
├── data/
│   ├── nodes.csv      # Lista de nodos (clubes y etiquetas regionales)
│   └── edges.csv      # Lista de aristas (traspasos dirigidos y ponderados)
└── docs/
    └── informe.pdf    # Memoria completa con figuras e interpretación
```

## Herramientas y métodos

[Gephi](https://gephi.org/) — layout Force Atlas 2, centralidad de grado/intermediación/cercanía/vector propio, y los algoritmos de detección de comunidades Louvain y Leiden.

## Autor

Pablo González Gómez — [LinkedIn](https://www.linkedin.com/in/pablo-gonzalez-gomez)
