# ML-2022-DIMP
Trabalho Aprendizado de Máquina
Esse repositório apresenta ferramentas uteis para o compreendimento de dados a respeito de *flakes* de oxido de grafeno. Grafeno é uma estrutura composta apenas por carbono, é uma monocamada de grafite. Seu oxido, portanto, é essa mesma estrutura, porém com defeitos de oxigênio e hidrogênio.

Aqui estão algumas estruturas para exemplificar:
![image](https://github.com/Karl-Marcos/ML-2022-DIMP/blob/main/imagens/neutral_12141.png)
![image](https://github.com/Karl-Marcos/ML-2022-DIMP/blob/main/imagens/neutral_6221.png)

Essas imagens foram plotadas a partir dos dados gerados por Amanda S. Bernard, que tivemos acesso em https://data.csiro.au/collection/csiro:41659v1.  E foram interpretados no programa de estruturas 3D de molécula VESTA (***V**isualisation for **E**lectronic **S**tructural **A**nalysis*).
Os dados que usamos são de flocos de oxido de grafeno relaxadas, o que significa que a estrutura 3D vai depender da quantidade e posição das impurezas de oxigênio. Observamos melhor essa reorganização da estrutura na segunda imagem.

Histograma da energia de Fermi:
![image](https://github.com/Karl-Marcos/ML-2022-DIMP/blob/main/imagens/histograma_fermi.png)

Com os dados em mãos, precisávamos selecionar quais eram mais uteis para nossos *targets* numéricos, que são a energia de fermi¹ e energia por átomo. Para isso calculamos quão relacionados estavam cada uma das *features* dos dados (tínhamos aproximadamente 800 delas) com as informações que queríamos (nosso *target*). Relacionamos eles usando o coeficiente de correlação de Pearson.
Conseguimos juntar essa informação na tabela abaixo, nela podemos observar que as fatures que mais se relacionam com a energia de fermi estão próximos de 1 ou –1 (caso exista uma relação de proporção inversa).

Atributos para calcular a energia de Fermi:
![image](https://github.com/Karl-Marcos/ML-2022-DIMP/blob/main/imagens/atributos_energia_fermi.png)

Histograma energia total por atomo:
![image](https://github.com/Karl-Marcos/ML-2022-DIMP/blob/main/imagens/histograma_energia.png)

Também calculamos a correção das *features* para a energia por átomo
Atributos para calcular a energia por átomo:
![image](https://github.com/Karl-Marcos/ML-2022-DIMP/blob/main/imagens/atributos_energia_por_atomo.png)

