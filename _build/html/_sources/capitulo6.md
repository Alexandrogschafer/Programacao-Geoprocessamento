---
jupytext:
  formats: md:myst
  text_representation:
    extension: .md
    format_name: myst
    format_version: 0.13
    jupytext_version: 1.11.5
kernelspec:
  display_name: Python 3
  language: python
  name: python3
---

# 6. VISUALIZAÇÃO DE DADOS GEOESPACIAIS NO PYTHON

[Abrir no Google Colab](https://colab.research.google.com/github/Alexandrogschafer/Programacao-Geoprocessamento/blob/main/notebooks/capitulo6.ipynb)

O geoprocessamento, como área que se dedica à coleta, processamento e análise de dados geoespaciais, é intrinsecamente ligado à visualização de informações. A representação gráfica desses dados não apenas facilita a compreensão de padrões e tendências espaciais, mas também serve como uma ponte entre informações complexas e a tomada de decisões informadas. Mapas, gráficos e outras representações visuais transformam conjuntos de dados brutos em insights tangíveis, permitindo que especialistas e tomadores de decisão visualizem fenômenos terrestres de maneira mais intuitiva.

Em uma época em que a quantidade de dados geoespaciais cresce exponencialmente, a capacidade de sintetizar e apresentar esses dados de forma clara e concisa é crucial. A visualização adequada permite que os usuários identifiquem rapidamente áreas de interesse, anomalias ou padrões, otimizando processos de análise e acelerando a resposta a questões geográficas críticas. Esta síntese visual também facilita a comunicação entre diferentes públicos, desde especialistas técnicos até o público em geral, democratizando o acesso à informação geoespacial.

A visualização de dados no geoprocessamento não se limita à simples representação gráfica. Ela também desempenha um papel vital na validação e qualidade dos dados. Através da representação visual, erros, inconsistências ou lacunas nos dados podem ser rapidamente identificados e corrigidos. Assim, a visualização atua como uma ferramenta de controle de qualidade, garantindo que as análises e decisões tomadas com base nesses dados sejam confiáveis e precisas.

Existem diversas ferramentas dedicadas à visualização de dados espaciais. Entre as mais populares estão o QGIS e o ArcGIS. No entanto, linguagens de programação, como Python e R, também oferecem bibliotecas que permitem criar visualizações espaciais complexas e personalizadas. Algumas das principais bibliotecas e ferramentas que possibilitam a visualização de dados espaciais em Python são a Geopandas, a Matplotlib (e Pyplot), a Folium e a Rasterio. Nesta seção, exploraremos algumas dessas ferramentas e bibliotecas. 


## 6.1 Introdução a Matplotlib

A Matplotlib é uma das principais bibliotecas de visualização de dados em Python, criada por John D. Hunter em 2003. Desde sua concepção, cresceu significativamente como um projeto de código aberto, auxiliado por uma grande comunidade de colaboradores. 

A biblioteca destaca-se pela sua capacidade de gerar uma ampla variedade de gráficos, como de linha, barras, dispersão, histogramas, entre outros, e se integra com as principais estruturas de dados do Python, como listas e arrays, especialmente com a biblioteca Numpy.

Um diferencial do Matplotlib é seu alto grau de personalização. O usuário pode ajustar quase todos os aspectos de uma visualização, desde cores e estilos até a posição das legendas e dos eixos. É possível implementar a biblioteca em diferentes interfaces gráficas, servidores web e Notebooks Jupyter, conferindo grande versatilidade na criação e exportação de gráficos.

Além de suas capacidades intrínsecas, a extensibilidade da Matplotlib é evidente no surgimento de bibliotecas derivadas que oferecem funcionalidades adicionais, como o Seaborn para visualizações estatísticas e o Basemap para mapeamento geográfico. Sua adoção generalizada em diversos campos, como pesquisa acadêmica, ciência de dados e engenharia, reforça seu papel como uma ferramenta importante para análise e comunicação de dados.

### 6.1.1 Principais abordagens para a criação de gráficos na Matplotlib

A criação de gráficos na Matplotlib pode ser abordada de duas maneiras principais: a abordagem funcional e a abordagem orientada a objetos. Ambas permitem a criação de visualizações de alta qualidade, mas são usadas em contextos diferentes e têm diferenças em termos de flexibilidade e controle sobre os elementos do gráfico.

A abordagem Funcional é a mais simples, sendo frequentemente usada para gráficos rápidos e diretos. A interface pyplot da Matplotlib oferece uma série de funções que atuam sobre uma configuração padrão em andamento. Por exemplo, quando você chama plt.plot(...), você está modificando o gráfico atual. As funções nesta abordagem se assemelham a comandos, e a sequência em que são chamadas importa, pois alteram o estado atual do gráfico. Embora seja conveniente para gráficos simples, pode tornar-se menos intuitiva para visualizações mais complexas com múltiplos subgráficos.

A abordagem orientada a objetos (OO) na Matplotlib refere-se a uma maneira de criar e manipular gráficos usando explicitamente objetos e métodos associados a esses objetos, em vez de depender de uma interface funcional mais direta. Esta abordagem oferece um controle mais explícito e maior flexibilidade sobre a figura e os eixos do gráfico. Ao invés de depender do estado global, você trabalha diretamente com objetos específicos, como a figura e os eixos, permitindo um controle mais preciso sobre todos os aspectos da visualização. É especialmente útil para visualizações mais complexas, como aquelas com múltiplos subgráficos ou eixos. Ela é frequentemente combinada com a interface pyplot para obter a flexibilidade da programação orientada a objeto com a simplicidade das funções do pyplot.

Em resumo, enquanto a abordagem funcional é ótima para criar rapidamente visualizações simples, a abordagem orientada a objetos oferece a flexibilidade necessária para criar visualizações mais complexas e personalizadas. A escolha entre as abordagens depende do contexto e da complexidade da visualização desejada. Em nosso curso, vamos optar por trabalhar com a abordagem funcional sempre que possível.


## 6.1.2 Primeiros passos na Matplotlib

*Gráficos básicos*

Para começar, focaremos na elaboração de gráficos fundamentais, abordando os tipos linha, coluna e dispersão.
Exemplo 1:

```{code-cell} python
import matplotlib.pyplot as plt
x = [0, 1, 2, 3, 4]
y = [0, 1, 4, 9, 16]
plt.plot(x, y)
plt.show()
```

Vamos detalhar o código:

``` import matplotlib.pyplot as plt ```

Aqui, importamos o módulo pyplot da biblioteca matplotlib e atribuimos a ele o alias "plt". 

```
x = [0, 1, 2, 3, 4]
y = [0, 1, 4, 9, 16]
```

Duas listas são criadas. A lista x representará os valores no eixo horizontal (eixo x), enquanto a lista y representará os valores no eixo vertical (eixo y). 


``` plt.plot(x, y) ```

O método plot do pyplot é usado para plotar as listas x e y como um gráfico de linhas. Por padrão, a Matplotlib traçará uma linha contínua azul ligando os pontos definidos pelas listas x e y. Este comando exibe o gráfico criado:

``` plt.show() ```
<br><br>

Exemplo 2:

```{code-cell} python
etiqueta = ['A', 'B', 'C']
valor = [3, 7, 2]
plt.bar(etiqueta, valor)
plt.show()
```

Vamos detalhar o código:

``` etiqueta = ['A', 'B', 'C'] ```

Nesta linha, você está definindo uma lista chamada “etiqueta” que contém três strings: 'A', 'B' e 'C'. Essas serão as etiquetas (ou rótulos) das barras no gráfico.

``` valor = [3, 7, 2] ```

Aqui, você está definindo uma lista chamada “valor” que contém três números: 3, 7 e 2. Esses números representarão as alturas das barras correspondentes às etiquetas 'A', 'B' e 'C'.

```plt.bar(etiqueta, valor) ```

Esta é a chamada principal para a criação do gráfico de barras. A função bar() do plt (pyplot) é usada para criar gráficos de barra. Ela espera, pelo menos, dois argumentos: os rótulos das barras e os valores das barras. Neste caso, as barras serão rotuladas como 'A', 'B' e 'C', e terão alturas de 3, 7 e 2 unidades, respectivamente.

``` plt.show() ```

Por fim, esta linha exibe o gráfico. Ela é responsável por renderizar o gráfico e mostrá-lo ao usuário:
<br><br>

Exemplo 3:

```{code-cell} python
x = [1, 2, 3, 4, 5]
y = [5, 4, 3, 2, 1]
plt.scatter(x, y)
plt.show()
```

Vamos detalhar o código:

``` x = [1, 2, 3, 4, 5] ```

Aqui, estamos definindo uma lista chamada x que contém cinco números. Esta lista representará as coordenadas x dos pontos que você deseja plotar no gráfico de dispersão.

``` y = [5, 4, 3, 2, 1] ```

Nesta linha, estamos definindo uma segunda lista chamada y que também contém cinco números. Essa lista representará as coordenadas y correspondentes dos pontos a serem plotados no gráfico.

``` plt.scatter(x, y) ```

Esta é a linha principal do código, onde a função scatter() do plt (módulo pyplot da Matplotlib) é chamada para criar um gráfico de dispersão. Ela espera, pelo menos, dois argumentos: as coordenadas x e y dos pontos. Neste caso, estamos instruindo a Matplotlib a criar pontos nas coordenadas (1,5), (2,4), (3,3), (4,2) e (5,1). Por fim:

``` plt.show() ```



### 6.1.3 Personalizando Gráficos com Matplotlib

A efetividade de uma visualização não reside apenas em representar dados, mas também na forma como essa representação é feita. Uma boa personalização pode destacar informações importantes, enquanto uma escolha de design inadequada pode obscurecer ou até mesmo distorcer os dados. A Matplotlib fornece uma grande quantidade de ferramentas para personalizar gráficos, garantindo que eles sejam informativos e esteticamente agradáveis.
<br><br>

*Cores, marcadores e linhas*

A aparência visual de um gráfico pode ser definida principalmente por suas cores, os marcadores utilizados e os estilos de linha.
<br><br>

*Cores*

Em Matplotlib, a cor de qualquer elemento do gráfico pode ser alterada. As cores podem ser especificadas de várias maneiras, incluindo nomes comuns ('red', 'blue', 'green'), códigos hexadecimais ('#FF5733'), entre outros.  
Exemplo:

```{code-cell} python
x = [0, 1, 2, 3, 4]
y = [0, 1, 4, 9, 16]
plt.plot(x, y, color='red')  # linha vermelha
plt.show()
```


*Marcadores*

Em gráficos de dispersão ou pontos específicos de uma linha, os marcadores indicam a localização exata de um ponto. Existem diferentes estilos de marcadores disponíveis, como 'o' para círculos, 's' para quadrados, '^' para triângulos, entre outros.  
Exemplo:

```{code-cell} python
x = [1, 2, 3, 4, 5]
y = [5, 4, 3, 2, 1]
plt.scatter(x, y, marker='^') # pontos triangulares
plt.show
```


*Linhas*

Os estilos de linha podem variar, e Matplotlib oferece opções como linhas contínuas ('-'), tracejadas ('--'), pontos e traços ('-.'), entre outros.  
Exemplo:

```{code-cell} python
x = [0, 1, 2, 3, 4]
y = [0, 1, 4, 9, 16]
plt.plot(x, y, color='red', linestyle='--')
# linha tracejada  
plt.show()
```


Para simplificar, a Matplotlib permite combinar o estilo de linha, marcador e cor em uma única string. Por exemplo, 'go-' significa marcadores verdes circulares com uma linha contínua.

```{code-cell} python
plt.plot(x, y, 'ro-')  
# linha contínua vermelha com marcadores circulares
plt.show()
```


Além disso, a largura da linha e o tamanho do marcador podem ser ajustados usando os argumentos linewidth e markersize, respectivamente.

```{code-cell} python
plt.plot(x, y, 'go-', linewidth=2, markersize=10)
plt.show()
```

Ao ajustar esses elementos básicos, já é possível criar gráficos mais informativos e visualmente atraentes. 
<br><br>

*Rótulos, títulos e legendas*

Os rótulos, títulos e legendas são componentes essenciais em visualizações de dados, pois proporcionam contexto e significado, facilitando a interpretação dos gráficos. Vejamos um exemplo:


- Rótulos: são usados para dar nome aos eixos (x e y) de um gráfico.

- Títulos: uma descrição breve e concisa que indica o propósito ou o conteúdo do gráfico.

- Legendas: usadas para identificar as diferentes séries ou categorias em um gráfico, especialmente útil quando várias linhas, pontos ou barras são desenhadas no mesmo espaço.

A partir dos elementos apresentados até aqui, podemos sugerir uma estrutura básica para criar um gráfico na Matplotlib:

```{code-cell} python
plt.plot(x, y, label='linha 1')
plt.xlabel('Eixo X')
plt.ylabel('Eixo Y')
plt.title('Gráfico de linhas')
plt.legend()
plt.show()
```

Vamos detalhar cada componente:

``` plt.plot(x, y, label='Legenda') ``` é a função principal para plotar gráficos de linhas. Ela toma os valores do eixo x e y como entrada e os plota. O argumento label é usado para associar uma legenda a essa linha específica, o que será útil quando chamarmos plt.legend() mais tarde. Podemos ter diversos outros argumentos, como os responsáveis pela definição de cores, marcadores, tipo e espessura de linhas, entre outros;

``` plt.xlabel('Eixo X') ``` e ``` plt.ylabel('Eixo Y') ``` são usadas para adicionar rótulos aos eixos x e y, respectivamente;

``` plt.title('Título do Gráfico') ``` é usada para adicionar um título ao gráfico;

``` plt.legend() ``` é usada para mostrar as legendas associadas a cada série no gráfico. A legenda é baseada nos labels fornecidos nas chamadas anteriores, como em plt.plot();

``` plt.show() ``` é usado para exibir o gráfico. Sem chamar essa função, o gráfico pode não ser exibido (dependendo do ambiente em que você está trabalhando).

Esta estrutura básica é suficiente para criar gráficos simples. No entanto, a Matplotlib é uma biblioteca muito versátil e possui muitas outras funcionalidades que permitem personalizar e aprimorar seus gráficos, dependendo da necessidade. 
<br><br>


*Adicionando texto ao gráfico*

Além dos componentes mencionados acima, a Matplotlib permite que você adicione texto em qualquer parte do gráfico.
Use plt.text(x, y, "Texto") para adicionar um texto na posição (x, y) do gráfico.

Exemplo:

```{code-cell} python
x = [1, 2, 3, 4, 5]
y = [5, 4, 3, 2, 1]
plt.plot(x, y, label='linha 1', color='green', linestyle='--')
plt.xlabel('Eixo X')
plt.ylabel('Eixo Y')
plt.title('Gráfico de linhas')
plt.text(1, 1.5, 'Texto de exemplo')
plt.legend()
plt.show()
```

Nosso exemplo consiste em um gráfico de linhas, em que utilizamos a estrutura básica sugerida anteriormente para a criação de gráficos na Matplotlib. Adicionamos plt.text(x, y, ‘texto’) para inserir o texto “Texto de exemplo” na posição x=1 e y=1.5.


Vamos agora plotar um gráfico com duas linha:

```{code-cell} python
# Dados de exemplo
x = [0, 1, 2, 3, 4]
y1 = [0, 1, 4, 9, 16]
y2 = [0, 2, 3, 7, 11]  

# Plotando as linhas
plt.plot(x, y1, label='Linha 1', color='blue')
plt.plot(x, y2, label='Linha 2', color='green') 

# Personalizando o gráfico
plt.xlabel('Eixo X')
plt.ylabel('Eixo Y')
plt.title('Gráfico de linhas')
plt.legend()

# Mostrando o gráfico
plt.show()
```


### 6.1.4 Subplots na Matplotlib

Subplots são uma maneira de criar múltiplos gráficos em uma única figura. Eles são úteis quando você quer comparar diferentes conjuntos de dados lado a lado ou quando quer visualizar diferentes aspectos de um mesmo conjunto de dados. Com a combinação de subplots e as diversas funções de plotagem disponíveis, você pode criar uma ampla variedade de visualizações para analisar e apresentar seus dados.

A função plt.subplots() é a maneira mais comum de criar subplots. Ela retorna uma figura e os eixos dos subplots.

```{code-cell} python
fig, ax = plt.subplots()
```

Neste caso, fig é a figura completa, enquanto ax é um único conjunto de eixos. Você pode plotar diretamente neste conjunto de eixos usando métodos como ax.plot().
<br><br>


*Especificando o número de subplots*

Você pode especificar o número de subplots passando dois argumentos para plt.subplots(): o número de linhas e o número de colunas.

```{code-cell} python
fig, axs = plt.subplots(2, 3)  
# Cria uma grade de 2x3 subplots
```

Aqui, axs é uma matriz 2x3 contendo os eixos dos subplots. Você pode acessar um subplot específico usando a indexação, como ``` axs[0, 1] ``` para o subplot na primeira linha e segunda coluna.
<br><br>


*Ajustando o Espaçamento*

Quando você cria múltiplos subplots, pode ser necessário ajustar o espaçamento entre eles para evitar sobreposição de rótulos ou de títulos. Você pode fazer isso usando plt.tight_layout() ou ajustando manualmente com fig.subplots_adjust().

``` plt.tight_layout() ```

ou

``` fig.subplots_adjust(left=None, bottom=None, right=None, top=None, wspace=None, hspace=None) ```

Em que:

- left, right, top, bottom controlam o espaçamento em relação à figura;

- wspace e hspace controlam o espaçamento entre subplots.

Para visualizar o resultado:

```{code-cell} python
fig, axs = plt.subplots(2, 3)  
plt.tight_layout()
plt.show()
```
<br><br>


*Plotando nos Subplots*


Uma vez que você tenha seus subplots definidos, você pode plotar neles usando os métodos de plotagem do objeto de eixos.

```{code-cell} python
fig, axs = plt.subplots(2, 1)
axs[0].plot([0, 1, 2], [0, 1, 0], label='Subplot 1')
axs[1].plot([0, 1, 2], [0, -1, 0], label='Subplot 2')
```


*Títulos e Rótulos*


Você pode adicionar títulos e rótulos a cada subplot individualmente:

```{code-cell} python
axs[0].set_title('Título do Subplot 1')
axs[0].set_xlabel('Eixo X do Subplot 1')
axs[0].set_ylabel('Eixo Y do Subplot 1')
```


*Compartilhando Eixos*


Se você estiver comparando dados em diferentes subplots e quiser que eles compartilhem o mesmo eixo X ou Y, você pode usar o argumento sharex ou sharey:

```{code-cell} python
fig, axs = plt.subplots(2, 1, sharex=True)
```

Neste caso, ambos subplots compartilharão o mesmo eixo X.


Exemplo: Criando múltiplos gráficos em uma única figura.


a) Usando plt.subplots():

O método plt.subplots() retorna uma figura e uma matriz de objetos "axes" (eixos), que são as áreas individuais de plotagem.

Etapa 1: Importação de biblioteca e criação da figura e dos subplots:

```{code-cell} python
# Criar a figura e os subplots
fig, ax = plt.subplots(nrows=2, ncols=2, figsize=(10, 10))
```

Nesse código, plt.subplots() retorna uma figura (fig) e os eixos (ax) dos subplots; nrows=2, ncols=2 define uma matriz 2x2, resultando em 4 subplots; figsize=(10, 10) define o tamanho da figura. Neste caso, a figura terá 10x10 polegadas.


Etapa 2: Plotando os gráficos em cada subplot.

Cada subplot é referenciado usando a indexação ``` ax[row, col] ```. Por exemplo, ``` ax[0, 0] ``` refere-se ao subplot superior esquerdo, enquanto ``` ax[1, 1] ``` é o subplot inferior direito. 


```{code-cell} python
# Primeiro subplot (superior esquerdo)
ax[0, 0].plot([0, 1, 2], [0, 1, 4])
ax[0, 0].set_title('Gráfico de Linha')

# Segundo subplot (superior direito)
ax[0, 1].scatter([0, 1, 2], [0, 1, 3])
ax[0, 1].set_title('Gráfico de Dispersão')

# Terceiro subplot (inferior esquerdo)
ax[1, 0].bar(['A', 'B', 'C'], [3, 7, 2])
ax[1, 0].set_title('Gráfico de Barras')

# Quarto subplot (inferior direito)
ax[1, 1].hist([0, 1, 2, 2, 3, 3, 3, 4, 4, 5])
ax[1, 1].set_title('Histograma')
```

Os seguintes métodos são usados para criar os gráficos: .plot() cria o gráfico de linha; .scatter() cria o gráfico de dispersão; .bar() cria o gráfico de barras; .hist() cria o histograma; set_title é usado para definir o título de cada subplot.


Etapa 3: Ajustando e visualizando a figura.

```{code-cell} python
plt.tight_layout()
```

O método tight_layout() ajusta o espaçamento entre os subplots para que não se sobreponham.


### 6.1.5 Gráficos com dados reais

Para exemplificar a criação de gráficos com dados reais, vamos criar um gráfico para visualizar a precipitação mensal (em mm) registrada na estação meteorológica do INMET, código A827, instalada no município de Bagé-RS nos anos de 2021, 2022 e 2023. Os dados estão armazenados em um arquivo CSV. 

O código completo para ler o arquivo e criar o gráfico é:

```{code-cell} python
import pandas as pd

df_precipitacao = pd.read_csv('~/geopythonbook/files/f20/precipitacao_A827.csv')
df_precipitacao.head()
```

```{code-cell} python
ax = df_precipitacao.plot(kind='bar', figsize=(10, 6), width=0.8, 
    color=['steelblue', 'mediumseagreen', 'silver'])
ax.set_xlabel('Mês')
ax.set_ylabel('Precipitação mensal (mm)')
ax.set_title('Precipitação: Estação INMET A827(Bagé)')
ax.set_xticklabels(df_precipitacao['Mês'], rotation=45)
ax.legend()
plt.tight_layout()
plt.show()
```


Vamos analisar o código por partes:

```
import pandas as pd
df_precipitacao = pd.read_csv('~/geopythonbook/files/f20/precipitacao_A827.csv')
df_precipitacao.head()
```
 
Aqui realizamos a leitura do arquivo CSV denominado precipitacao_A827.CSV. Os dados do arquivo são armazenados no DataFrame chamado df_precipitacao. Em seguida, as primeiras cinco linhas do DataFrame são impressas usando o método head().
<br><br>

```
ax = df_precipitacao.plot(kind='bar', figsize=(10, 6), width=0.8, color=['steelblue', 'mediumseagreen', 'silver']) 
```

Nesse código, df_precipitacao.plot(...) utiliza a função plot() do DataFrame df_precipitacao para criar um gráfico; kind='bar' especifica que o tipo de gráfico desejado é um gráfico de barras; figsize=(10, 6) define o tamanho da figura como 10 unidades de largura por 6 unidades de altura; width=0.8 define a largura das barras como 80% da largura padrão entre os ticks do eixo x; ``` color=['steelblue', 'mediumseagreen', 'silver'] ``` define as cores das barras. 
<br><br>

``` ax.set_xlabel('Mês') ```
 
Define o rótulo do eixo x como "Mês".
<br><br>

``` ax.set_ylabel('Precipitação mensal (mm)') ```

Define o rótulo do eixo y como "Precipitação mensal (mm)".
<br><br>

``` ax.set_title('Precipitação: Estação INMET A827(Bagé)') ```

Estabelece o título do gráfico.
<br><br>

``` ax.set_xticklabels(df_precipitacao['Mês'], rotation=45) ```


Define os rótulos do eixo x com os valores da coluna 'Mês' do DataFrame df_precipitacao e roda esses rótulos em 45 graus para melhor visualização.
<br><br>

``` ax.legend() ```


Exibe a legenda do gráfico, que, por padrão, usará os nomes das colunas do DataFrame como rótulos.
<br><br>

``` plt.tight_layout() ```

Ajusta automaticamente o layout da figura para garantir que tudo seja exibido corretamente.
<br><br>

``` plt.show() ```

Exibe a figura. Se você estiver usando um Jupyter Notebook ou um ambiente IPython, a figura será exibida diretamente abaixo da célula que contém o código. Em outros ambientes, isso pode abrir uma janela com a figura.


### 6.1.6 Exportando Gráficos

Quando você cria um gráfico, seja para análise de dados, apresentações ou publicações, muitas vezes é necessário exportá-lo para um formato de arquivo específico. A exportação de gráficos envolve várias considerações, incluindo o formato de arquivo, resolução e qualidade. A escolha certa depende do uso pretendido do gráfico e das especificações do meio em que será apresentado.


*Formatos*

Existem vários formatos de arquivo para os quais você pode exportar um gráfico, e a escolha do formato depende do uso pretendido. Alguns dos formatos mais comuns incluem:

- PNG (Portable Network Graphics): É um formato de imagem matricial, o que significa que ele armazena o gráfico como uma coleção de pixels. É amplamente usado devido à sua compressão sem perdas e suporte a transparência;

- JPEG (Joint Photographic Experts Group): Também é um formato de imagem matricial, mas usa compressão com perdas, o que pode reduzir a qualidade da imagem. É mais adequado para fotografias do que para gráficos;

- SVG (Scalable Vector Graphics): É um formato de imagem vetorial, o que possibilita que o gráfico seja redimensionado sem perder qualidade;

- PDF (Portable Document Format): É um formato de arquivo versátil que pode conter gráficos vetoriais e matriciais. É amplamente usado para publicações e impressão.
<br><br>


*Resolução*

A resolução refere-se ao número de pixels por polegada (PPI) ou pontos por polegada (DPI) em uma imagem. Uma resolução mais alta resulta em uma imagem mais nítida, mas também em um tamanho de arquivo maior. A resolução ideal depende de onde o gráfico será usado:

- Tela (web, apresentações): Geralmente, uma resolução de 72 PPI é suficiente;

- Impressão: Para obter uma imagem nítida, é recomendável uma resolução de pelo menos 300 DPI.


*Qualidade*

A qualidade refere-se à quantidade de detalhes e clareza em uma imagem. Em formatos de compressão com perdas, como JPEG, você pode escolher um nível de qualidade ao exportar. Uma qualidade mais alta resultará em uma imagem mais nítida, mas também em um tamanho de arquivo maior. Por outro lado, uma qualidade mais baixa reduzirá o tamanho do arquivo, mas também a nitidez da imagem. Ao exportar gráficos, é importante equilibrar a qualidade e o tamanho do arquivo, considerando o propósito pretendido do gráfico. 


*Exportando o gráfico de precipitação da estação A827*

Para exportar o último gráfico criado com os dados de precipitação da estação climatológica A827 no contexto da Matplotlib, utilizamos o método savefig(). Vamos criar um arquivo em formato PNG, com resolução de 300dpi.

```{code-cell} python
plt.savefig('files_out/precipitacao_2021-2023_A827.png', format='png', dpi=300)
```

É importante ressaltar que o método savefig() deve ser posicionado antes do método .show para que o gráfico seja exportado corretamente. O código atualizado com esta linha é:

```{code-cell} python

ax = df_precipitacao.plot(kind='bar', figsize=(10, 6), width=0.8, 
    color=['steelblue', 'mediumseagreen', 'silver'])
ax.set_xlabel('Mês')
ax.set_ylabel('Precipitação mensal (mm)')
ax.set_title('Precipitação: Estação INMET A827(Bagé)')
ax.set_xticklabels(df_precipitacao['Mês'], rotation=45)
ax.legend()
plt.tight_layout()
plt.savefig('files_out/precipitacao_2021-2023_A827.png', format='png', dpi=300)
plt.show()
```

Depois de executar este código, você encontrará o gráfico exportado como um arquivo PNG com a resolução especificada, no diretório atual de trabalho.



## 6.2 Função de plotagem integrada da GeoPandas.

Como vimos no capítulo anterior, a Geopandas é uma extensão da Pandas, uma das bibliotecas mais populares para análise de dados em Python. Ele facilita o trabalho com dados geoespaciais, incorporando estruturas para manipulação de geometrias.

Com a Geopandas, é possível realizar a plotagem básica de dados geográficos com facilidade. Um simples comando plot() aplicado a um GeoDataFrame ou GeoSeries gera uma representação visual dos dados. Por exemplo:

```{code-cell} python
import geopandas as gpd
gdf_uf = gpd.read_file('~/geopythonbook/files/f4/BR_UF.shp')
gdf_uf.plot()
```


A seguir, exploraremos as opções de personalização do método plot. A visualização padrão é prática, mas muitas vezes precisamos modificar cores, legendas e outros detalhes para melhorar a apresentação dos dados. Entender essas opções nos ajudará a produzir gráficos mais claros e adequados ao nosso propósito.


a) Definição da cor de preenchimento

O blue é a cor padrão quando plotamos utilizando o .plot(). Para aplicar outra cor a todas as geometrias do GeoDataFrame, você pode usar o argumento color.

```{code-cell} python
gdf_uf.plot(color = 'green')
```


*Atribuindo cores diferentes de acordo com os atributos*

Para colorir geometrias com base nos valores de uma coluna (atributo) específica, você pode utilizar os argumentos column e cmap (mapa de cores). Vamos criar uma visualização do gdf_uf, atribuindo cores a cada geometria com base nos valores da coluna NM_REGIAO e usando o esquema de cores Pastel2.

```{code-cell} python
gdf_uf.plot(column = 'NM_REGIAO', cmap = 'Pastel2')
```


O cmap, abreviação de Colormap, refere-se a uma escala de cores ou um mapa de cores na Matplotlib e em outras bibliotecas de visualização. A Matplotlib oferece uma variedade de colormaps pré-definidos que podem ser usados conforme o tipo de dado e a preferência visual. Alguns exemplos de colormaps na Matplotlib incluem:

- Sequenciais: São adequados para dados que vão de valores baixos a altos. Exemplos: Blues, Greens, OrRd.

- Divergentes: São adequados para dados que têm um valor médio significativo e variações nos dois extremos (baixo e alto). Exemplos: RdBu (Vermelho-Azul), coolwarm.

- Cíclicos: São adequados para dados que têm valores repetidos em ciclos. Exemplo: twilight.

- Qualitativos: São usados para representar informações categóricas. Exemplo: tab10. Para mais detalhes, consulte (https://matplotlib.org/stable/users/explain/colors/colormaps.html).
<br><br>

*Personalizando as linhas de borda* 

Usando edgecolor e linewidth, você pode personalizar a cor e a largura das linhas de borda das geometrias. Exemplo:

```{code-cell} python
gdf_uf.plot(color='green', edgecolor='black', linewidth=0.8)
```
<br><br>

*Configuração de legenda e barra de cores*

Ao usar o argumento legend=True, você pode adicionar uma legenda ou barra de cores para representar os valores dos dados.

```{code-cell} python
gdf_uf.plot(column = 'NM_REGIAO', cmap = 'Pastel2', legend=True)
```


Estes são apenas alguns exemplos básicos de como você pode personalizar a plotagem de seus dados geográficos na Geopandas. Como a Geopandas se integra perfeitamente a Matplotlib, as possibilidades são amplas e permitem muita personalização. Estudaremos a integração da Geopandas com a Matplotlib a seguir.



## 6.3 Integração da Geopandas com Matplotlib

Quando você usa o método .plot() da Geopandas, ele já está usando a matplotlib implicitamente. No entanto, para uma integração mais profunda e personalizada, você pode usar a matplotlib explicitamente. Essa integração é bastante direta e traz várias vantagens, dentre elas:

- Personalização Avançada: A matplotlib oferece uma ampla gama de opções de personalização, permitindo que você ajuste quase todos os aspectos do seu gráfico;

- Combinação de Gráficos: Você pode combinar seu mapa com outros tipos de gráficos, como gráficos de barras, linhas ou scatter plots, em uma única figura;

- Subplots: Como discutido anteriormente, a matplotlib permite criar subplots. Isso é útil se você quiser mostrar vários mapas lado a lado para comparação;

- Controle de Legenda: A matplotlib oferece opções avançadas para personalizar a legenda do seu gráfico, incluindo posição, tamanho, cor e muito mais;

- Integração com Outras Bibliotecas: Ao usar a matplotlib como base, você pode facilmente integrar seu mapa com outras bibliotecas de visualização que também usam a matplotlib, como seaborn;

- Exportação Flexível: A matplotlib oferece várias opções para exportar seu gráfico, permitindo que você escolha formatos, resoluções e outros parâmetros de exportação;

- Interatividade: Embora a matplotlib seja principalmente uma biblioteca de plotagem estática, ele tem algumas funcionalidades interativas, especialmente quando usado em ambientes como o Jupyter Notebook.

Em resumo, integrar a Geopandas com a Matplotlib oferece uma maior flexibilidade e controle sobre a visualização dos seus dados geoespaciais. Vamos explorar algumas opções de personalização a seguir.
<br><br>

*Configuração das etiquetas dos eixos*

O método .plot() da Geopandas retorna um objeto de eixos (ax) da matplotlib, e você pode usar esse objeto para ajustar as propriedades dos eixos, incluindo o tamanho do texto das etiquetas dos eixos. 

As etiquetas dos eixos na Matplotlib são altamente configuráveis. O método ax.tick_params() pode ser usado para ajustar várias propriedades das etiquetas dos eixos e dos marcadores (ticks) ao mesmo tempo. 

Vamos reduzir o tamanho do texto referente aos valores das coordenadas geográficas em nosso GeoDataFrame gdf_uf:

```{code-cell} python
# Plotando o GeoDataFrame
ax = gdf_uf.plot()

# Ajustando o tamanho do texto das etiquetas dos eixos:
# Ajuste o tamanho desejado para '7'
ax.tick_params(axis='both', which='major', labelsize=7)  
plt.show()
```


No método ax.tick_params(), o argumento labelsize define o tamanho do texto. Você pode ajustar esse valor conforme necessário. which=’major’ indica que a configuração será realizada com o eixo principal da plotagem.


Além de ax.tick_params(), existem outros métodos e propriedades para ajustar as etiquetas dos eixos e os ticks. A documentação oficial da matplotlib é uma excelente fonte para verificar as opções disponíveis e obter exemplos detalhados. Você pode encontrar mais informações sobre ax.tick_params() e outras funcionalidades relacionadas na documentação da matplotlib, em: (https://matplotlib.org/stable/api/axis_api.html).
<br><br>


*Mais exemplos de integração entre Geopandas e Matplotlib*

Exemplo 1: Plotando um único GeoDataFrame

```{code-cell} python
fig, ax = plt.subplots(figsize=(10, 10))

# Usando o método .plot() do GeoDataFrame e passando o eixo criado
gdf_uf.plot(ax=ax, color='darkseagreen', edgecolor='black')

# Personalizando com Matplotlib
ax.set_title('Brasil')
ax.set_xlabel('Longitude')
ax.set_ylabel('Latitude')

# Mostrando o gráfico
plt.show()
```

Resumidamente, este código carrega um conjunto de dados geoespaciais do Brasil a partir de um arquivo shapefile, cria uma figura e eixos usando matplotlib, plota os dados geoespaciais no gráfico, personaliza o gráfico e, em seguida, exibe o gráfico resultante. 
Vamos analisar o código passo a passo.

``` fig, ax = plt.subplots(figsize=(10, 10)) ```

Uma figura e eixos são criados usando a função subplots da matplotlib. A figura terá um tamanho de 10x10 polegadas.

``` gdf_uf.plot(ax=ax, color='darkseagreen', edgecolor='black') ```

O método .plot() do GeoDataFrame (gdf_uf) é usado para visualizar os dados geoespaciais. O argumento ax=ax indica que o plot deve ser feito nos eixos previamente criados. O argumento color='darkseagreen' define a cor de preenchimento das unidades federativas, enquanto edgecolor='black' define a cor das bordas.

```
ax.set_title('Brasil')
ax.set_xlabel('Longitude')
ax.set_ylabel('Latitude')
```

Aqui, o gráfico é personalizado usando funções da matplotlib. O título do gráfico é definido como "Brasil", e os rótulos dos eixos x e y são definidos como "Longitude" e "Latitude", respectivamente.
<br><br>


Exemplo 2: Plotando uma geometria e o conteúdo de uma coluna

Vamos plotar a mesma figura anterior, mas inserindo na visualização a sigla referente a cada estado. Para tanto, vamos utilizar a função annotate da matplotlib. A ideia é iterar sobre cada geometria (neste caso, cada estado) no GeoDataFrame e adicionar uma anotação (o nome do estado) à sua posição central.

```{code-cell} python
# Criando uma figura e eixos com Matplotlib
fig, ax = plt.subplots(figsize=(10, 10))

# Usando o método .plot() do GeoDataFrame e passando o eixo criado
gdf_uf.plot(ax=ax, color='darkseagreen', edgecolor='black')

# Adicionando os nomes dos estados
for x, y, label in zip(gdf_uf.geometry.centroid.x, 
    gdf_uf.geometry.centroid.y, gdf_uf['SIGLA_UF']):
    ax.annotate(label, xy=(x, y), xytext=(0,-2), 
        textcoords='offset points', fontsize=9)

# Personalizando com Matplotlib
ax.set_title('Brasil')
ax.set_xlabel('Longitude')
ax.set_ylabel('Latitude')

# Mostrando o gráfico
plt.show()
```


Neste código, a parte chave é o loop for que itera sobre as coordenadas centrais de cada geometria (usando gdf_uf.geometry.centroid.x e gdf_uf.geometry.centroid.y) e os nomes dos estados ``` (usando gdf_uf['NM_UF']). ``` Para cada estado, a função annotate adiciona o nome do estado à sua posição central no gráfico. O argumento xytext=(0,-2) e textcoords="offset points" são usados para garantir que o texto não seja colocado exatamente no centro da geometria, mas ligeiramente deslocado para evitar sobreposições com as bordas das geometrias.
<br><br>


Exemplo 3: Plotando camadas de geometrias sobrepostas

Vamos criar uma plotagem das rodovias do estado de Sergipe sobrepostas a geometria desse estado.

```{code-cell} python

gdf_sergipe = gpd.read_file('~/geopythonbook/files/f21/sergipe_UF.shp')
gdf_rodovias = gpd.read_file('~/geopythonbook/files/f21/sergipe_rodo.shp')

# Criar uma figura e eixos com Matplotlib
fig, ax = plt.subplots(figsize=(10, 10))

# Plotar a geometria do estado do Sergipe como fundo
gdf_sergipe.plot(ax=ax, color='lightgray', edgecolor='black', linewidth=0.5)

# Plotar as rodovias sobrepostas ao estado
gdf_rodovias.plot(ax=ax, color='red', linewidth=1)

# Personalizar com Matplotlib: inserir um título
ax.set_title('Rodovias de Sergipe')

# Plotar o gráfico
plt.show()
```


Neste exemplo, a geometria do estado do Sergipe é plotada primeiro com uma cor de fundo lightgray e borda black. As rodovias são então plotadas por cima com uma cor red e uma largura de linha de 1.0. 


É possível criar uma visualização sem os eixos de coordenadas, o que é útil em muitas situações. A chamada ax.axis('off') pode ser usada para isso:

```{code-cell} python
fig, ax = plt.subplots(figsize=(10, 10))

gdf_sergipe.plot(ax=ax, color='lightgray', edgecolor='black', linewidth=0.5)

gdf_rodovias.plot(ax=ax, color='red', linewidth=1)

ax.set_title('Rodovias de Sergipe')

# Removendo os eixos para uma visualização mais limpa
ax.axis('off')

plt.show()
```
<br><br>


Exemplo 4: Classificando um tema por categorias

O GeoDataFrame gdf_rodovias tem uma coluna chamada jurisdição que especifica a jurisdição de cada segmento de rodovia (Federal, Estadual, Municipal ou desconhecida). Vamos gerar uma plotagem das rodovias de Sergipe, categorizadas de acordo com a sua jurisdição. Para tanto, vamos utilizar o argumento column no método plot e adicionar uma legenda.

```{code-cell} python
# Criar uma figura e eixos com Matplotlib
fig, ax = plt.subplots(figsize=(8,8))

# Plotar a geometria do estado do Sergipe como fundo
gdf_sergipe.plot(ax=ax, color='lightgray', edgecolor='black', 
    linewidth=0.5)

# Plotar as rodovias classificadas por jurisdição
gdf_rodovias.plot(ax=ax, column='jurisdicao', legend=True, cmap='Reds', 
    linewidth=1.5)

# Inserir o título
ax.set_title('Rodovias de Sergipe por Jurisdição', fontweight='bold')

# Remover os eixos para uma visualização mais limpa
ax.axis('off')

# Ajustar a posição da legenda
leg = ax.get_legend()
leg.set_bbox_to_anchor((0.9, 0.3))

# Ajustar o layout automaticamente
plt.tight_layout()

# Mostrar o gráfico
plt.show()
```

Neste código: leg.set_bbox_to_anchor((0.9, 0.3)) ajusta a posição da legenda para que ela não sobreponha o gráfico. 
<br><br>


Exemplo 6: Mapa coroplético 

Vamos criar uma visualização da distribuição espacial da população por município para o estado de Santa Catarina (dados referentes ao ano de 2021). Para simplificar, usaremos aqui o termo ‘mapa coroplético’, mesmo que alguns dos elementos que constituem um mapa por definição (como a escala gráfica ou numérica) não estejam presentes nessa visualização.

Inicialmente, vamos importar as bibliotecas, ler o arquivo shapefile e plotar as primeiras linhas do GeoDataFrame.

```{code-cell} python
gdf_sc = gpd.read_file('~/geopythonbook/files/f22/censo_mun_sc.shp')
gdf_sc.head()
```

```{code-cell} python
gdf_sc.plot()
```

Para criar o mapa coroplético, vamos utilizar o seguinte código:

```{code-cell} python
# Definir o tamanho da figura
fig, ax = plt.subplots(figsize=(10, 10))

# Criar o mapa
gdf_sc.plot(column='pop_2021', ax=ax, cmap='OrRd')

# Criar a barra de cores (colorbar) manualmente
cbar = plt.colorbar(ax.collections[0], ax=ax, shrink=0.5)
cbar.set_label('População por Município', size=10)
cbar.ax.tick_params(labelsize=9)

# Ajustar o tamanho do texto dos eixos de coordenadas
ax.tick_params(axis='both', which='major', labelsize=6) 

# Adicionar título e exibindo o mapa
ax.set_title('Distribuição da População por Município')
plt.show()
```

Vamos detalhar o código:

``` fig, ax = plt.subplots(figsize=(10, 10)) ```

Esta linha cria uma figura (fig) e um conjunto de eixos (ax) com um tamanho especificado de 10x10 polegadas.
<br><br>

``` gdf_sc.plot(column='pop_2021', ax=ax, cmap='OrRd') ```

Aqui, estamos usando o método plot do GeoDataFrame gdf_sc para criar um mapa coroplético. Estamos atribuindo cores aos municípios com base nos valores da coluna pop_2021, usando o cmap 'OrRd'. O argumento ax=ax especifica que queremos plotar os dados no conjunto de eixos que criamos anteriormente.
<br><br>

``` cbar = plt.colorbar(ax.collections[0], ax=ax, shrink=0.5) ```

Esta linha adiciona uma barra de cores (colorbar) ao gráfico. A barra de cores fornece uma referência visual para mapear cores individuais para valores de dados. O argumento shrink=0.5 especifica que a barra de cores deve ser reduzida para metade do tamanho do eixo.
<br><br>

``` cbar.set_label('População por Município', size=10) ```

Aqui, estamos definindo um rótulo para a barra de cores com o texto "População por Município" e especificando que o tamanho da fonte do rótulo deve ser 10.
<br><br>

``` cbar.ax.tick_params(labelsize=9) ```

O código acima ajusta os parâmetros dos ticks (marcadores) da barra de cores. Estamos definindo o tamanho da fonte dos rótulos dos marcadores para 9.


Na figura acima, a vasta diferença nos valores populacionais entre os municípios tornou a visualização desbalanceada e pouco informativa. Isso porque municípios com populações muito altas contrastavam fortemente com aqueles de população menor, obscurecendo nuances e padrões regionais. Para proporcionar uma interpretação mais clara dos dados, vamos ajustar a representação para uma escala logarítmica. Esse ajuste pode equilibrar visualmente as variações populacionais, tornando o mapa mais compreensível e revelando detalhes anteriormente ofuscados pela discrepância nos valores absolutos. Para criar essa visualização, utilizamos o código:

```{code-cell} python
import numpy as np
import matplotlib.colors as mcolors
import matplotlib.cm as cm

# Definir o tamanho da figura
fig, ax = plt.subplots(figsize=(10, 10))

# Criar uma coluna logarítmica
gdf_sc = gdf_sc.copy()
gdf_sc['pop_2021_log'] = np.log(gdf_sc['pop_2021'])

# Definir o colormap
cmap = 'OrRd'
norm = mcolors.Normalize(vmin=gdf_sc['pop_2021'].min(), 
    vmax=gdf_sc['pop_2021'].max())

# Plotar o mapa coroplético com escala logarítmica
gdf_sc.plot(column='pop_2021_log', ax=ax, cmap=cmap, legend=False)

# Criar uma legenda personalizada
cbar = plt.cm.ScalarMappable(norm=norm, cmap=cmap)

# Ajustar as dimensões da legenda
cbar_ax = fig.add_axes([0.95, 0.25, 0.02, 0.5])
cb = fig.colorbar(cbar, cax=cbar_ax, orientation='vertical')

# Ajustar o tamanho do título da legenda
cb.set_label('População', size=10)  

# Ajustar o tamanho dos ticks da legenda
cb.ax.tick_params(labelsize=9)      

# Ajustar o tamanho do texto dos eixos de coordenadas
ax.tick_params(axis='both', which='major', labelsize=6) 

# Adicionar título e exibir o mapa
ax.set_title('Distribuição da População por Município - SC')
plt.show()
```

Vamos analisar as diferenças com relação ao código anterior:

```
import numpy as np
import matplotlib.colors as mcolors
import matplotlib.cm as cm
```

Aqui, além da Matplotlib importamos o numpy, e os módulos matplotlib.colors e matplotlib.cm, que são usados para trabalhar com mapas de cores.
<br><br>

```
gdf_sc = gdf_sc.copy()
gdf_sc['pop_2021_log'] = np.log(gdf_sc['pop_2021']) 
```

Cria uma cópia do GeoDataFrame gdf_sc para evitar alterações no original. Em seguida, adiciona uma nova coluna pop_2021_log que contém o logaritmo natural dos valores da coluna pop_2021.
<br><br>

```
cmap = 'OrRd'
norm = mcolors.Normalize(vmin=gdf_sc['pop_2021'].min(), vmax=gdf_sc['pop_2021'].max())
```

Define o mapa de cores como 'OrRd' e cria um objeto de normalização que mapeia os valores da coluna pop_2021 para o intervalo ``` [0, 1] ```.
<br><br>

``` gdf_sc.plot(column='pop_2021_log', ax=ax, cmap=cmap, legend=False) ```

Plota o mapa coroplético usando a coluna pop_2021_log e o mapa de cores definido anteriormente. A legenda não é mostrada porque legend=False.
<br><br>

```
cbar = plt.cm.ScalarMappable(norm=norm, cmap=cmap)
cbar_ax = fig.add_axes([0.95, 0.25, 0.02, 0.5])
cb = fig.colorbar(cbar, cax=cbar_ax, orientation='vertical
```

Cria uma legenda personalizada para o mapa; plt.cm.ScalarMappable é usado para mapear os valores da coluna pop_2021 para cores no mapa de cores; fig.add_axes adiciona um novo conjunto de eixos à figura para a legenda, e fig.colorbar adiciona a legenda à figura.

Ao utilizar a escala logarítmica, foi possível representar de forma mais eficaz a distribuição populacional, realçando tanto áreas densamente quanto escassamente povoadas.
<br><br>

Exemplo 7: Múltiplos plots em uma visualização

A visualização simultânea de múltiplos conjuntos de dados geoespaciais pode proporcionar uma compreensão abrangente das características e relações territoriais de uma área. No exemplo a seguir, exploraremos o uso de subplots para visualizar, lado a lado: os estados, os biomas e as regiões hidrográficas do Brasil. Para facilitar o entendimento, inicialmente vamos apresentar o código sem a configuração de estilos de cores, dos textos e de legendas. 

```{code-cell} python
# Leitura dos arquivos
gdf_uf = gpd.read_file('~/geopythonbook/files/f4/BR_UF.shp')
gdf_bio = gpd.read_file('~/geopythonbook/files/f23/biomas.shp')
gdf_hid = gpd.read_file('~/geopythonbook/files/f23/regioes_hidro.shp')

# Criando uma figura com três subplots (um ao lado do outro)
fig, axs = plt.subplots(1, 3, figsize=(15, 5))

# Plotando gdf_uf no primeiro subplot
gdf_uf.plot(ax=axs[0])
axs[0].set_title('Estados')

# Plotando gdf_bio no segundo subplot
gdf_bio.plot(ax=axs[1])
axs[1].set_title('Biomas')

# Plotando gdf_hid no terceiro subplot
gdf_hid.plot(ax=axs[2])
axs[2].set_title('Regiões Hidrográficas')

# Ajustando a apresentação
for ax in axs:
    ax.axis('off')

plt.tight_layout()
plt.show()
```


No código acima:

``` fig, axs = plt.subplots(1, 3, figsize=(15, 5)) ```

Aqui, usamos o método plt.subplots() para criar uma figura (fig) e três subplots (axs). O argumento “1, 3” indica que queremos 1 linha e 3 colunas de subplots, ou seja, três áreas de plotagem lado a lado. O argumento figsize=(15, 5) define o tamanho total da figura como 15x5 polegadas.
<br><br>

```
gdf_uf.plot(ax=axs[0])
axs[0].set_title('Estados')

gdf_bio.plot(ax=axs[1])
axs[1].set_title('Biomas')

gdf_hid.plot(ax=axs[2])
axs[2].set_title('Regiões Hidrográficas')
```

Neste código, estamos plotando o gdf_uf (que representa os estados) no primeiro subplot (área de plotagem ``` axs[0] ```). Em seguida, definimos um título para esse subplot. Da mesma forma, estamos plotando o gdf_bio (que representa os biomas) no segundo subplot (área de plotagem ``` axs[1] ```) e definindo um título para ele. Por fim, estamos plotando o gdf_hid (que representa as regiões hidrográficas) no terceiro subplot (área de plotagem ``` axs[2] ```) e definindo um título para ele.
<br><br>

```
for ax in axs:
    ax.axis('off')

plt.tight_layout()
plt.show()
```

Aqui, estamos percorrendo cada subplot (área de plotagem) e desativando os eixos usando ax.axis('off'), o que remove os rótulos e os marcadores dos eixos, tornando a visualização mais limpa. plt.tight_layout() ajusta automaticamente o tamanho e a posição dos subplots para que eles se ajustem bem na figura; plt.show() exibe a figura criada.
<br><br>



Agora vamos alterar o código, adicionando as configurações de texto, legendas e categorias:

```{code-cell} python

gdf_uf = gpd.read_file('~/geopythonbook/files/f4/BR_UF.shp')
gdf_bio = gpd.read_file('~/geopythonbook/files/f23/biomas.shp')
gdf_hid = gpd.read_file('~/geopythonbook/files/f23/regioes_hidro.shp')

# Criando uma figura e três eixos
fig, axs = plt.subplots(nrows=1, ncols=3, figsize=(15, 5))

# Argumentos para a legenda
legend_args = {
    'loc': 'lower left',
    'fontsize': 'small'  # Reduzindo o tamanho da fonte da legenda
}

# Plotando o mapa dos estados brasileiros no primeiro eixo
gdf_uf.plot(column='SIGLA_UF', ax=axs[0], cmap='Pastel2', edgecolor='black')
axs[0].set_title('Estados Brasileiros')

# Plotando o mapa dos biomas do Brasil no segundo eixo
gdf_bio.plot(column='NOME', ax=axs[1], cmap = 'Greens', edgecolor='black', 
    legend=True, legend_kwds=legend_args)
axs[1].set_title('Biomas do Brasil')

# Plotando o mapa das regiões hidrográficas do Brasil no terceiro eixo
gdf_hid.plot(column='RHI_NM', ax=axs[2], cmap='Blues', edgecolor='black', 
    legend=True, legend_kwds=legend_args)
axs[2].set_title('Regiões Hidrográficas do Brasil')

# Removendo os eixos x e y para uma visualização mais limpa
for ax in axs:
    ax.axis('off')

# Ajustando o layout com um espaçamento reduzido
plt.tight_layout(pad=0.1)
plt.show()
```


Vamos analisar o código:

``` fig, axs = plt.subplots(nrows=1, ncols=3, figsize=(15, 5)) ```

Aqui, usamos o método plt.subplots() para criar uma figura (fig) e três eixos (axs), da mesma maneira que no código anterior.
<br><br>

```
legend_args = {
    'loc': 'lower left',
    'fontsize': 'small'  # Reduzindo o tamanho da fonte da legenda
}
```

Neste trecho, definimos um dicionário legend_args que contém argumentos para personalizar a legenda dos plots. A legenda é posicionada no canto inferior esquerdo ('loc': 'lower left') e tem tamanho de fonte pequeno ('fontsize': 'small').
<br><br>

```
gdf_uf.plot(column='SIGLA_UF', ax=axs[0], cmap='Pastel2', edgecolor='black')
axs[0].set_title('Estados Brasileiros')
```

Aqui, plotamos o gdf_uf no primeiro eixo (```axs[0]```) e atribuímos cores aos estados com base na coluna 'SIGLA_UF' usando o mapa de cores Pastel2. As bordas dos estados são definidas como pretas (edgecolor='black'). Em seguida, definimos um título para esse eixo.
<br><br>

```
gdf_bio.plot(column='NOME', ax=axs[1], cmap = 'Greens', edgecolor='black', 
    legend=True, legend_kwds=legend_args)
axs[1].set_title('Biomas do Brasil')
```

Neste trecho, estamos plotando o gdf_bio no segundo eixo (``` axs[1] ```) e atribuindo cores aos biomas com base na coluna 'NOME', usando o mapa de cores Greens. As bordas dos biomas são definidas como pretas (edgecolor='black'). A legenda é ativada (legend=True) e personalizada usando os argumentos definidos anteriormente (legend_kwds=legend_args). Em seguida, definimos um título para esse eixo.
<br><br>

     
```
gdf_hid.plot(column='RHI_NM', ax=axs[2], cmap='Blues', edgecolor='black', 
    legend=True, legend_kwds=legend_args)
axs[2].set_title('Regiões Hidrográficas do Brasil')
```

Aqui, plotamos o gdf_hid no terceiro eixo (```axs[2] ```) e atribuímos cores as regiões hidrográficas com base na coluna 'RHI_NM' usando o mapa de cores 'Blues'. As bordas das regiões são definidas como pretas (edgecolor='black'). A legenda é ativada (legend=True) e personalizada usando os argumentos definidos anteriormente (legend_kwds=legend_args). Em seguida, definimos um título para esse eixo.

O restante do código permanece inalterado com relação ao primeiro código apresentado. 


## 6.4 Adicionando Mapas Base à Plotagem com Contextily

Ao visualizar dados geoespaciais, muitas vezes é útil ter um mapa base para fornecer contexto geográfico. A biblioteca Contextily permite adicionar facilmente mapas base, provenientes de fontes populares como OpenStreetMap e Stamen às suas visualizações.

A biblioteca foi projetada para integrar-se perfeitamente com outras bibliotecas geoespaciais, como Geopandas e Matplotlib. Ela é capaz de reprojetar os dados automaticamente para o sistema de coordenadas Web Mercator (EPSG:3857), comumente usado por provedores de tiles de mapas base. Além disso, ao recuperar tiles de mapas base, otimiza o desempenho armazenando-os localmente em cache.
<br><br>


*Provedores de mapas base na Contextily*

A biblioteca Contextily fornece acesso a vários provedores de tiles de mapas base. Os provedores incluídos no Contextily estão organizados sob o módulo ctx.providers. Cada provedor tem um ou mais estilos de mapa disponíveis. No quadro 15 apresenta-se alguns dos principais provedores e estilos disponíveis com acesso gratuito. 


Quadro 15: Provedores de tiles e estilos na Contextily.

| Provedor     | Estilo                           |
|--------------|----------------------------------|
| OpenStreetMap| ctx.providers.OpenStreetMap.Mapnik|
| Stamen       | ctx.providers.Stamen.Toner       |
|              | ctx.providers.Stamen.TonerLite   |
|              | ctx.providers.Stamen.Terrain     |
|              | ctx.providers.Stamen.Watercolor  |
| CartoDB      | ctx.providers.CartoDB.Positron   |
|              | ctx.providers.CartoDB.DarkMatter |
| Esri         | ctx.providers.Esri.WorldStreetMap|
|              | ctx.providers.Esri.DeLorme       |
|              | ctx.providers.Esri.WorldTopoMap  |
|              | ctx.providers.Esri.WorldImagery  |

<br><br>

Abaixo apresentamos alguns exemplos de estilos de mapas base:

| OpenStreetMap.Mapnik | Stamen.Watercolor |
|----------------------|-------------------|
| ![Figura 23](images/fig23.png)           | ![Figura 24](images/fig24.png)         |


| Esri.DeLorme | NASAGIBS.ASTER_GDEM_Greyscale_Shaded_Relief |
|--------------|---------------------------------------------|
| ![Figura 25](images/fig25.png)     | ![Figura 26](images/fig26.png)                                    |

<br><br>

Vale lembrar que a disponibilidade dos tiles pode variar dependendo dos termos de serviço dos provedores e da capacidade de suportar tráfego. Além disso, a lista de provedores e estilos pode mudar com o tempo, conforme novos estilos são adicionados ou antigos são removidos. Você pode verificar diretamente a lista completa de provedores e estilos disponíveis no ambiente Python explorando o módulo ctx.providers.
<br><br>

Exemplo: Criar uma visualização do município de Florianópolis com o basemap WorldImagery, do provedor ESRI.

Inicialmente, precisamos instalar a biblioteca Contextily:

```{code-cell} python
# !pip install contextily
```

O comando !pip install é utilizado para instalar pacotes Python utilizando o gerenciador de pacotes pip. O prefixo “!“ é específico para ambientes como o Jupyter Notebook e indica que o comando deve ser executado no sistema operacional, e não no kernel Python. 
Em seguida, importamos as bibliotecas necessárias, lemos o arquivo shapefile e geramos um plot para ver se o arquivo foi lido corretamente.

```{code-cell} python
import contextily as ctx

# Carregar o GeoDataFrame
gdf = gpd.read_file('~/geopythonbook/files/f24/floripa.shp')
gdf.plot()
```

Agora vamos plotar o GeoDataFrame utilizando a Contextily:

```{code-cell} python
# Plotar o GeoDataFrame
ax = gdf.to_crs(epsg=3857).plot(figsize=(15, 15), facecolor='none', 
    alpha=0.9, edgecolor='r')

# Adicionar o mapa base
ctx.add_basemap(ax, source=ctx.providers.Esri.WorldImagery, zoom=12)

plt.show()
```

Vamos detalhar o código:

``` ax = gdf.to_crs(epsg=3857).plot(figsize=(15, 15), facecolor='none', alpha=0.9, edgecolor='r') ```

Aqui, reprojetamos o GeoDataFrame gdf para o sistema de coordenadas Web Mercator (EPSG:3857), que é comum para mapas base. Em seguida, plotamos com as seguintes características: 
<br><br>

``` figsize=(15, 15) ```: Define o tamanho da figura;

``` facecolor='none' ``` : Define a cor de preenchimento das geometrias como ‘sem cor’;

```  alpha=0.9 ``` : Define a transparência das geometrias (0 é totalmente transparente, 1 é totalmente opaco);

```  edgecolor='r' ``` : Define a cor das bordas das geometrias como vermelho.
<br><br>

```
ctx.add_basemap(ax, source=ctx.providers.Esri.WorldImagery, zoom=12)
plt.show()
```

A biblioteca Contextily é usada para adicionar um mapa base à visualização. Neste caso, o mapa base escolhido é o WorldImagery da Esri. A função add_basemap adiciona esse mapa ao fundo da plotagem de gdf, com um nível de zoom definido como 12. Por fim, plt.show() é utilizado para exibir o gráfico.



## 6.5 Visualização interativa com folium

A Folium é uma biblioteca que tem como base a biblioteca JavaScript Leaflet.js (https://leafletjs.com/). Sua integração com as bibliotecas Pandas e Geopandas permite transformar DataFrames e GeoDataFrames em visualizações de mapa interativas. 

A Folium suporta uma ampla variedade de tiles de mapa, como Mapbox e OpenStreetMap, para que os usuários possam personalizar a aparência de seus mapas base. É possível configurar cores, ícones e estilos para a visualização de dados. Com relação a ícones, a Folium utiliza predominantemente os ícones do FontAwesome 4.7 e os estilos de cores são predefinidos dentro da própria biblioteca. A lista completa de ícones disponíveis pode ser consultada no seguinte link: (https://fontawesome.com/v4.7/icons/).

A Folium possui um conjunto predefinido de cores para os ícones. No entanto, ao contrário dos ícones, a lista de cores não está bem documentada em um único lugar, no site oficial ou na documentação da Folium. Algumas das cores disponíveis são: 'red', 'blue', 'green', 'purple', 'orange', 'darkred', 'lightred', 'beige'- 'darkblue', 'darkgreen', 'cadetblue', 'darkpurple', 'white', 'pink', 'lightblue', 'lightgreen', 'gray', 'black', 'lightgray'.

Existem vários plugins que ampliam as funcionalidades da Folium e possibilitam a criação de visualizações de mapas mais interativas e ricas em recursos, como o HeatMap, MarkerCluster, Fullscreen. Além disso, como a biblioteca é baseada no Leaflet.js, muitos plugins do Leaflet podem ser facilmente adaptados ou integrados a ele.



### 6.5.1 Aplicando a Folium com dados reais

Vamos demonstrar algumas das funcionalidades da Folium a partir de exemplos com dados reais.


Exemplo 1: Criar uma visualização interativa das localizações das hidrelétricas e PCHs do estado de São Paulo.


```{code-cell} python

# Importar as bibliotecas, ler o arquivo shapefile e criar o GeoDataFrame
import folium
gdf_hsp = gpd.read_file('~/geopythonbook/files/f25/hidreletricas_sp.shp')


#nCalcular a latitude e longitude médias das geometrias no GeoDataFrame

latitude_central = gdf_hsp.geometry.y.mean()
longitude_central = gdf_hsp.geometry.x.mean()


# Imprimir as coordenadas centrais

print(latitude_central, longitude_central)


# Inicializar um mapa centrado nas coordenadas médias com um nível de zoom inicial de 7

mapa_hid = folium.Map(location=[latitude_central, longitude_central], 
    zoom_start=7)
# Também é possível inserir manualmente as coordenadas centrais do mapa
# mapa_hid = folium.Map(location=[-22.6444, -48.0996], zoom_start=7)

# Adicionar um marcador ao mapa para cada hidrelétrica no GeoDataFrame
for idx, row in gdf_hsp.iterrows():
    folium.Marker(location=[row['geometry'].y, row['geometry'].x],
                  popup=row['potenciaou']  
                 ).add_to(mapa_hid)

# Exibir o mapa 
mapa_hid
```


Nessa visualização, além de termos a localização dos pontos referentes às hidrelétricas e PCHs, podemos visualizar a capacidade instalada clicando no ícone desejado.


Vamos analisar o código por partes:

```
latitude_central = gdf_hsp.geometry.y.mean()
longitude_central = gdf_hsp.geometry.x.mean()
print(latitude_central, longitude_central)
#Saída: (-22.6444, -48.0966)
```

Esse código calcula a latitude e longitude médias de todas as geometrias no GeoDataFrame. Isso é usado para definir o ponto central do mapa que será criado posteriormente.
<br><br>

```
mapa_hid = folium.Map(location=[latitude_central, longitude_central], zoom_start=7)
Um mapa é inicializado usando a biblioteca Folium, centrado nas coordenadas médias calculadas anteriormente e com um nível de zoom inicial de 7.

for idx, row in gdf_hsp.iterrows():
    folium.Marker(location=[row['geometry'].y, row['geometry'].x],
                  popup=row['potenciaou']  
                 ).add_to(mapa_hid)
```

Para cada hidrelétrica no GeoDataFrame gdf_hsp, um marcador é adicionado ao mapa. A localização de cada marcador é definida pela latitude (``` row['geometry'].y ```) e longitude (``` row['geometry'].x ```) da hidrelétrica. Um pop-up também é adicionado a cada marcador, que exibirá a potência da hidrelétrica quando o marcador for clicado. Para salvar a visualização interativa em um arquivo HTML:

``` mapa_hid.save('mapa_hidreletricas_SP.html') ```
<br><br>


Vamos agora gerar uma nova visualização, alterando o mapa base e o símbolo dos marcadores:


```{code-cell} python
# Inicializando um mapa folium centrado na latitude e longitude médias

# usar o serviço de imagens do ArcGIS como tiles de fundo
mapa_hid = folium.Map(
    location=[latitude_central, longitude_central],  # Ponto central do mapa
    zoom_start=7,  # Nível de zoom inicial
    control_scale=True,  # Adiciona um controle de escala ao mapa
    attr='ESRI World Imagery',  # Atribuição do mapa
    tiles=
    'http://services.arcgisonline.com/ArcGIS/rest/services/World_Imagery/MapServer/tile/{z}/{y}/{x}'  # URL do servidor de tiles
)

# Iterar sobre cada linha do GeoDataFrame 'gdf_hsp' para adicionar marcadores ao mapa
for idx, row in gdf_hsp.iterrows():
    folium.Marker(
        location=[row['geometry'].y, row['geometry'].x],  # Coordenadas do marcador
        popup=row['potenciaou'],  # Informação da potência que será mostrada no pop-up
        icon=folium.Icon(color='blue', icon='flash')  # Ícone azul com símbolo de 'flash'
    ).add_to(mapa_hid)  # Adiciona o marcador ao mapa

# Exibir o mapa
mapa_hid
```


É possível ainda alterar o dimensionamento da área gráfica da figura:

```{code-cell} python
folium.Map(location=[latitude_central, longitude_central], zoom_start=7, width=600, height=400, control_scale=True)
```

Nesse Código, width=600 e height=400 definem as dimensões do mapa em pixels. Neste caso, o mapa terá uma largura de 600 pixels e uma altura de 400 pixels.


Exemplo 2: Criar a visualização interativa de uma geometria do tipo ‘linha’: a BR-116.

```{code-cell} python

# Ler o arquivo shapefile e armazenar no GeoDataFrame
gdf = gpd.read_file('~/geopythonbook/files/f18/br116.shp')

# Calcular o ponto central da união das geometrias no GeoDataFrame
center = gdf.geometry.unary_union.centroid

# Obter a latitude e longitude desse ponto central
latitude_central = center.y
longitude_central = center.x

# Converter o GeoDataFrame para formato JSON 
gdf.crs = 'EPSG:4326'
gdf.to_json()
gdf_json = gdf.to_json()

# Criar um objeto de feature GeoJson a partir do gdf convertido em JSON
gdf_ftrs = folium.features.GeoJson(gdf_json)

# Inicializar o mapa folium centrado na latitude e longitude calculadas 
# Nível de zoom inicial de 4
mapabr = folium.Map(location=[latitude_central, longitude_central], 
    zoom_start=4)

# Adicionar o GeoJson (que representa a BR-116) ao mapa
mapabr.add_child(gdf_ftrs)

# Exibir o mapa 
mapabr
```


Exemplo 3: Criar uma visualização com os municípios do estado do Amapá (dados do tipo ‘polígono’), introduzindo algumas possibilidades de configuração adicional.

```{code-cell} python
# Ler o arquivo shapefile e armazenar no GeoDataFrame
amapa = gpd.read_file('~/geopythonbook/files/f26/censo_mun_AP.shp')

# Calcular o ponto central (centroid) da união de todas as geometrias no GeoDataFrame
center = amapa.geometry.unary_union.centroid

# Obter a latitude e longitude desse ponto central
latitude_central = center.y
longitude_central = center.x

# Converter o GeoDataFrame para formato JSON (útil para visualização em algumas bibliotecas)
amapa.crs = 'EPSG:4326'
amapa.to_json()
amapa_json = amapa.to_json()
# Criar um objeto de feature GeoJson a partir do GeoDataFrame convertido em JSON
amapa_ftrs = folium.features.GeoJson(amapa_json)

# Inicializar um mapa folium centrado na latitude e longitude calculadas com um nível de zoom inicial de 7
# Utilizar o serviço de imagens do mundo do ArcGIS como tiles de fundo
mapa_AP = folium.Map(location=[latitude_central, longitude_central], zoom_start=7,
        control_scale=True, attr='ESRI World Imagery',
        tiles=
        'http://services.arcgisonline.com/ArcGIS/rest/services/World_Imagery/MapServer/tile/{z}/{y}/{x}')

# Adicionar o GeoJson (que representa os municípios do Amapá) ao mapa
mapa_AP.add_child(amapa_ftrs)

# Exibir o mapa
mapa_AP
```


Vamos alterar o código anterior, especificando a cor e a espessura da linha de borda e a cor de preenchimento dos municípios:

```{code-cell} python
# Criar uma função para estilizar as geometrias referentes aos municípios.
# A função especifica a cor da borda, a espessura da borda e a cor de preenchimento.
def estilo_mun(ftr):
    return({'color':'red', 'weight':1, 'fillColor':'purple'})

# Converter o GeoDataFrame 'amapa' para formato JSON.

amapa_json = amapa.to_json()

# Criar o objeto de feature GeoJson a partir do GeoDataFrame convertido em JSON. E:
# - Definir o nome da layer como 'municipio'.
# - Adicionar um tooltip que mostra informações dos municípios ao passar o mouse sobre eles.
# - Aplicar a função de estilo estilo_mun a cada município.
amapa_ftrs = folium.features.GeoJson(amapa_json, 
    name='municipio', 
    tooltip=folium.features.GeoJsonTooltip(['municipio', 'pop_2010', 'pop_2021', 'dif_pop']), 
    style_function=estilo_mun)

# Adicionar o GeoJson ao mapa previamente criado.
mapa_AP.add_child(amapa_ftrs)

# Exibir o mapa.
mapa_AP
```


A partir das alterações realizadas no código, é possível visualizar as geometrias referentes aos municípios do estado do Amapá com outra configuração. Além disso, podemos verificar os dados sobre a população em 2010 e 2021 e a sua alteração (em porcentagem).


É possível criar estilos de visualização diferentes, com base na seleção de propriedades ou atributos. Nesse exemplo, vamos criar uma função que verifica o nome do município e, se for 'Macapá', aplica estilo específico. Caso contrário, aplica um estilo padrão para os outros municípios.

```{code-cell} python
def estilo_mun(ftr):
    # Verificar se o município é 'Macapá'
    if ftr['properties']['municipio']=='Macapá':
        # Estilo para o município 'Macapá'  
        return {'color':'red', 'weight':4, 'fillColor':'green'} 
    else:
        #Estilo padrão para os outros municípios
        return {'color':'black', 'weight':2, 'fillColor':'purple'} 


amapa_json = amapa.to_json()

amapa_ftrs = folium.features.GeoJson(amapa_json, 
    name='municipio', 
    tooltip=folium.features.GeoJsonTooltip(['municipio', 'pop_2010', 
        'pop_2021', 'dif_pop']), 
    style_function=estilo_mun)

mapa_AP.add_child(amapa_ftrs)
mapa_AP
```


No próximo exemplo, vamos aplicar um estilo com cor de preenchimento aleatória a cada município do Amapá, enquanto a cor de borda e a espessura serão as mesmas para todos:


```{code-cell} python
# Importar o módulo random, que permite fazer escolhas aleatórias
import random

# Definir uma função para estilizar as geometrias (municípios) no mapa.
# A cor de preenchimento de cada município é determinada aleatoriamente 
# a partir de uma lista de cores.
def estilo_mun(ftr):
    # Definir uma lista de cores que podem ser escolhidas.
    cores = ['grey', 'orange', 'yellow', 'violet', 'blue', 'green', 'indigo']
    
    # Retornar o estilo para o município. A cor de preenchimento é selecionada 
    # aleatoriamente. A cor de contorno é definida como preta e a espessura do 
    # contorno como 2.
    return {'color': 'black', 'weight': 2, 'fillColor': random.choice(cores)}

amapa_json = amapa.to_json()
amapa_ftrs = folium.features.GeoJson(
    amapa_json, 
    name='municipio', 
    tooltip=folium.features.GeoJsonTooltip(['municipio', 'pop_2010', 'pop_2021', 
        'dif_pop']), 
    style_function=estilo_mun
)

mapa_AP.add_child(amapa_ftrs)
mapa_AP
```


Por fim, vamos gerar um mapa interativo que mostra os municípios do estado do Amapá e as estações fluviométricas da Agência Nacional de Águas (ANA), com estilizações e tooltips específicos:

```{code-cell} python
# Carregar o shapefile que contém informações sobre as estações 
# fluviométricas da ANA
ANA = gpd.read_file('~/geopythonbook/files/f27/ANA_estacoes.shp')

# Definir uma função para estilizar as geometrias dos municípios.
def estilo_mun(ftr):
    # Retornar o estilo que será aplicado aos municípios.
    return({'color':'red', 'weight':1, 'fillColor':'purple'})

amapa_json = amapa.to_json()
amapa_ftrs = folium.features.GeoJson(
    amapa_json, 
    name='municipio', 
    tooltip=folium.features.GeoJsonTooltip(['municipio', 
        'pop_2010', 'pop_2021', 'dif_pop']), 
    style_function=estilo_mun)

ANA.crs = 'EPSG:4326' 

ANA_json = ANA.to_json()

# Criar uma camada GeoJson para as estações fluviométricas da ANA.
# Tooltips são adicionadas para mostrar informações adicionais sobre 
# uma estação.
ANA_ftrs = folium.features.GeoJson(
    ANA_json, 
    name='Estações fluviométricas ANA',
    tooltip=folium.features.GeoJsonTooltip(['Codigo', 'Rios', 
        'Operador']))

# Inicializar um mapa interativo da Folium. # Definir a localização 
# central e o zoom. O mapa também usará tiles de imagens da ESRI.
mapa_AP = folium.Map(
    location=[latitude_central, longitude_central], 
    zoom_start=7,
    control_scale=True, 
    attr='ESRI World Imagery', 
    tiles=
    'http://services.arcgisonline.com/ArcGIS/rest/services/World_Imagery/MapServer/tile/{z}/{y}/{x}')

# Adicionando a camada de municípios ao mapa.
mapa_AP.add_child(amapa_ftrs)

# Adicionando a camada de estações fluviométricas da ANA ao mapa.
mapa_AP.add_child(ANA_ftrs)

# Exibindo o mapa.
mapa_AP
```


Nesta visualização interativa, podemos verificar tanto dados referentes à população dos municípios quanto dados das estações da ANA.










