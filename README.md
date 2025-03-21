﻿# Analise-dos-Top-50-Livros-mais-vendidos-Amazon
 
# Importando a biblioteca pandas e lendo o arquivo csv

import pandas as pd 
df  = pd.read_csv('bestsellers.csv')
print(df.head())
print(df.shape)
print(df.columns)
print(df.describe())

# para tirar linhas duplicadas use 'df.drop_duplicates()'

df.drop_duplicates(inplace=True)

# agora vamos renomear as colunas com o código 'df.rename()'

df.rename(columns={'Name': 'Title', 'Year': 'Puclication Year', 'User Rating': 'Rating'}, inplace=True)

# para mudar o tipo de dado de uma coluna use 'df.astype()']

df["Price"] = df["Price"].astype(float)

# para mudar o tipo de dado de uma coluna use 'df.astype()'

author_counts = df["Author"].value_counts()
print(author_counts)

# para agrupar os dados por genero e calcular a média de avaliação use 'uf.groupby()'

media_para_cada_genero = df.groupby("Genre")["Rating"].mean()
print(media_para_cada_genero)

# para salvar os dados em um arquivo use 'to_csv()'
author_counts.head(10).to_csv('top_authors.csv')
media_para_cada_genero.to_csv('media_por_genero.csv')
