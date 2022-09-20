# ML-2022-DIMP
Trabalho Aprendizado de Máquina

Esse repositório apresenta ferramentas uteis para o compreendimento de dados a respeito de *flakes* de oxido de grafeno. Grafeno é uma estrutura composta apenas por carbono, é uma monocamada de grafite. Seu oxido, portanto, é essa mesma estrutura, porém com defeitos de oxigênio e hidrogênio.

Utilizamos as seguintes bibliotecas para a **obtenção e análise de dados**
```python
import pandas as pd
import lmfit 
import matplotlib.pyplot as plt
import seaborn as sns
import numpy as np
```

Aqui estão algumas estruturas para exemplificar:
![image](https://github.com/Karl-Marcos/ML-2022-DIMP/blob/main/imagens/neutral_12141.png)
![image](https://github.com/Karl-Marcos/ML-2022-DIMP/blob/main/imagens/neutral_6221.png)

Essas imagens foram plotadas a partir dos dados gerados por Amanda S. Bernard, que tivemos acesso em [https://data.csiro.au/collection/csiro:41659v1](url).  E foram interpretados no programa de estruturas 3D de molécula VESTA (***V**isualisation for **E**lectronic **S**tructural **A**nalysis*).

Os dados que usamos são de flakes de óxido de grafeno relaxadas, o que significa que a estrutura 3D vai depender da quantidade e posição das impurezas de oxigênio. Observamos melhor essa reorganização da estrutura na segunda imagem.

Decidimos estudar, como targets numéricos, os valores de energia de Fermi, e de energia total por átomo. Podemos ver no histograma abaixo que a energia de Fermi está distribuída nos exemplos de forma que se assemelha a uma distrubuição de Poisson:
![image](https://github.com/Karl-Marcos/ML-2022-DIMP/blob/main/imagens/histograma_fermi.png)

Com os dados em mãos, precisávamos selecionar quais eram mais uteis para nossos *targets* numéricos, que são a energia de fermi¹ e energia por átomo. Para isso calculamos quão relacionados estavam cada uma das *features* dos dados (tínhamos aproximadamente 800 delas) com as informações que queríamos (nosso *target*). Relacionamos eles usando o coeficiente de correlação de Pearson.

Conseguimos juntar essa informação na tabela abaixo, nela podemos observar que as fatures que mais se relacionam com a energia de fermi estão próximos de 1 ou –1 (caso exista uma relação de proporção inversa).

Atributos para calcular a energia de Fermi:
![image](https://github.com/Karl-Marcos/ML-2022-DIMP/blob/main/imagens/atributos_energia_fermi.png)

A energia total por átomo está dispersa de forma aparentemente menos organizada, com intervalos de alta ocorrência alternando com intervalos que aparecem pouco nos dados:
![image](https://github.com/Karl-Marcos/ML-2022-DIMP/blob/main/imagens/histograma_energia.png)

Também calculamos a correção das *features* para a energia por átomo

Atributos para calcular a energia por átomo:
![image](https://github.com/Karl-Marcos/ML-2022-DIMP/blob/main/imagens/atributos_energia_por_atomo.png)

Para o **Aprendizado supervisionado** uitlizamos as seguintes bibliotecas: 
```python
import pandas as pd
import matplotlib.pyplot as plt
plt.style.use('seaborn-bright')
import numpy as np
import lmfit
import sklearn #somente algumas funções 
```
Vamos calcular métricas de Machine Learnig, testaremos modelos:
- `Baseline`; 
- `K-NN`;
- `Linear Normalizado`;
- `Linear Não-Normalizado`;
- `Árvore de decisão`;
- `Floresta aleatória`

Antes de testar os modelos e decidir qual o melhor para o nosso dataset, separamos os dados em dois grupos diferentes: `teste` e `treino`. Os dados de teste são usados somente na hora de testar os modelos, para não haver possibilidade do algoritimo ter decorado os dados e devolvido somente um valor que já era conhecido. Para melhorarmos os nossos modelos, nós também modificamos os hiperparâmetros para podermos ter melhores resultados das relações. Por fim, o melhor modelo foi o de `Árvore aleatória`, tanto para Energia de Fermi quanto para Energia por átomo. 
