---
layout: post
title: "Medir a deformação - Parte I"
author: "Gonçalo Henriques"
tags: [documentation,sample]
image:
---

# 1 Introdução

## 1.1 Motivação e objectivo

Na mecânica dos meios contínuos utiliza-se a abordagem fenomenológica para
descrever o comportamento do material, ou seja, é empregue um modelo físico
de comportamento com resposta similar à esperada pelo material real. Esta
abordagem é baseada em ensaios experimentais que, de forma sucinta, consistem em
aplicar forças numa amostra material e medir as deformações por estas
provocadas. Estes ensaios devem permitir definir os parâmetros reológicos do
material e, consequentemente, estabelecer a relação constitutiva que
possibilita a construção de modelos numéricos para o estudo do comportamento do
material.

Em problemas de engenharia são usados modelos computacionais para
prever os comportamentos dos materiais. Nestes modelos surgem diferentes
definições de extensão consoante a ferramenta numérica utilizada, problema em
análise, material em estudo, etc.. Mas quais os motivos para a existência de
tantas definições de extensão?, qual a mais adequada? e para que tipo de
análise? Este artigo tem como objectivo elencar as diferenças e vantagens entre as
várias definições de extensão e o âmbito das suas aplicações.

## 1.2 Conceitos

Para uma leitura adequada são definidos os seguintes conceitos:

**Partículas materiais:** pontos materiais no contínuo.

**Corpo contínuo:** corpo com o interior totalmente preenchido por partículas
 materiais.

**Deformação:** variação da distância entre dois pontos do interior do corpo.

**Extensão:** medida da deformação em relação a um referencial que, por exemplo,
 pode variar consoante o tipo de formulação.

**Configuração inicial:** configuração do corpo no instante $$t_0$$ que se
considera como uma configuração indeformada.

**Configuração corrente:** configuração do corpo no instante $$t$$ que se
considera como uma configuração deformada.

**Formulação Lagrangeana:** medição das grandezas físicas em relação à
 configuração inicial do corpo.

**Formulação Euleriana:** medição das grandezas físicas em relação à
 configuração deformada do corpo.

[//]:**Movimento de corpo rígido:** quando a distância entre todas as partículas
[//]: materiais do interior do corpo se mantém inalterada.

## 1.3 Estrutura do artigo

Esta publicação está dividida em 3 partes:

* Parte I - Deformações e rotações infinitesimais;
* Parte II - Grandes deformações;
* Parte III - Propriedades da extensão logarítmica.

A parte I começa com a Medição da deformação - capítulo 2. Segue o capítulo 3
com o âmbito de aplicação das deformações e rotações infinitesimais e termina
com um exemplo prático para o caso .


## 1.4 Nomenclatura

É utilizada a notação indicial.

$$P$$, $$Q$$ - posições das partículas materiais na configuração do corpo no
instante $$t_0$$.\\
$$P'$$, $$Q'$$ - posições das partículas materiais na configuração do corpo no
instante $$t$$.\\
$$X_i$$ - coordenadas da partícula material no instante $$t_0$$\\
$$x_i$$ - coordenadas da partícula material no instante $$t$$\\
$$E_{ik}$$ - extensão de Green\\
$$e_{ik}$$ - extensão de Almansi\\
$$\varepsilon$$ - extensão de engenharia
# 2 Medição da deformação


Considere uma partícula material no interior da configuração inicial de um corpo
contínuo, correspondente ao instante $$t_0$$. A sua posição inicial $$ P $$ é
definida pelo vector $$ \vec{r}=X_ie_i $$. No instante $$ t $$, a partícula material
passa a ocupar a posição $$ P'$$ definida
pelo vector $$\vec{r'}=x_ie_i$$. O deslocamento da partícula material $$ u$$ é obtido pela
diferença $$ \vec{r'}-\vec{r}$$:

$$\begin{equation}
\begin{split}
& u = \vec{r'}-\vec{r} \\
 \Rightarrow \quad & u_i = (x_i -X_i)e_i \quad .
\end{split}
\end{equation}$$

Seja Q outra partícula material muito próxima da vizinhança de P (distância
infinitesimal). Na configuração inicial do corpo, a distância entre as duas
partículas materiais é dada por:

$$\begin{align}
\overline{PQ} = \mathrm{d} l =& \sqrt{\mathrm{d} X_1^2+\mathrm{d}
X_2^2+\mathrm{d} X_3^2}\\
=& \sqrt{\mathrm{d} X_i^2}
\end{align}$$

Para a configuração deformada do corpo, correspondente ao instante $$ t$$, a
distância entre as duas partículas materiais é calculada de forma análoga:


$$ \begin{align}
\overline{P'Q'} = \mathrm{d} l' &= \sqrt{\mathrm{d} x_1^2+\mathrm{d}
x_2^2+\mathrm{d} x_3^2} \\
&= \sqrt{\mathrm{d} x_i^2}
\end{align}$$

Repare que $$ \mathrm{d} x_i $$ pode ser obtido em função da configuração
inicial do corpo $$ \mathrm{d} x_i = \mathrm{d} X_i + \mathrm{d} u_i$$ e $$
\mathrm{d} u_i = \frac{\partial u_i}{\partial x_k} \mathrm{d} x_k $$.

[//]:No caso de $$ \overline{PQ}=\overline{P'Q'}$$ para qualquer par de partículas
[//]:materiais, o corpo está num movimento de corpo rígido. Caso contrário, o copo
[//]:está deformado.

Para medir a deformação, seguindo o raciocínio de Landau [1], começa-se por analisar a
diferença do quadrado das distâncias infinitesimais das partículas:

$$\begin{align}
\mathrm{d} l'^2 - \mathrm{d} l^2 &= \mathrm{d} x_i^2 - \mathrm{d} X_i^2 \\
 &= (\mathrm{d} X_i + \mathrm{d} u_i)^2 - \mathrm{d} X_i^2 \\
 &= \mathrm{d} X_i^2 + 2 \mathrm{d}X_i \mathrm{d} u_i + \mathrm{d} u_i^2 -
 \mathrm{d} X_i^2 \\
 &=  2 \mathrm{d}X_i \mathrm{d} u_i + \mathrm{d} u_i^2 \\
 &=  2 \left( \frac{\partial u_i}{\partial X_k} \right) \mathrm{d}X_i
 \mathrm{d}X_k \; + \\
 & \quad + \left( \frac{\partial u_i}{\partial X_k} \frac{\partial u_i}{\partial
 X_l} \right) \mathrm{d}X_k \mathrm{d}X_l
\end{align}$$

No primeiro termo da direita troca-se os sufixos e no segundo termo os sufixos
$$ i$$ por $$ l$$:

$$
\begin{equation}
\mathrm{d} l'^2 - \mathrm{d} l^2 = 2 E_{ik} \mathrm{d}X_i \mathrm{d}X_k
\end{equation}
$$

$$ E_{ik}$$ é definido como a extensão de Green:

$$
\begin{align}
E_{ik} &= \frac{1}{2} \left(\frac{\partial u_i}{\partial X_k} + \frac{\partial
u_k}{\partial X_i} + \frac{\partial u_l}{\partial X_k} \frac{\partial
u_l}{\partial X_i} \right) \\
&= \frac{1}{2} (u_{i,k} + u_{k,i} + u_{l,k} u_{l,i})
\end{align}$$

A extensão de Green é dada em função da configuração inicial do corpo, ou seja,
trata-se de uma formulação Lagrangeana. Da mesma forma se pode obter a
extensão de Almansi dada em função da configuração deformada do corpo
(formulação Euleriana):

$$
\begin{equation}
e_{ik} = \frac{1}{2} \left(\frac{\partial u_i}{\partial x_k} + \frac{\partial
u_k}{\partial x_i} + \frac{\partial u_l}{\partial x_k} \frac{\partial
u_l}{\partial x_i} \right)
\end{equation}$$

A formulação Euleriana é a mais utilizada na mecânica nos fluídos. De facto, como
num líquido Newtoniano as tensões são independentes do tempo não há necessidade
de uma configuração inicial. Ao contrário, nos sólidos as tensões dependem da
história de carregamento e, como tal, há necessidade de especificar a configuração
indeformada. Como tal, a formulação Lagrangeana é a mais utilizada na mecânica
dos sólidos.

No caso das deformações e rotações serem infinitesimais, as expressões
anteriores podem ser simplificadas e deixa de haver distinção entre a
configuração inicial e corrente do corpo. Isto permite que o
produto presente nas expressões seja negligenciado e obtém-se a
extensão de engenharia $$\varepsilon_{ik}$$:

$$\begin{equation}
\varepsilon_{ik} = \frac{1}{2} \left(\frac{\partial u_i}{\partial X_k} + \frac{\partial
u_k}{\partial X_i} \right)
\end{equation}$$

As extensões de engenharia são as mais utilizadas por permitirem uma relação
linear com as funções deslocamento. Contudo, estas simplificações têm as suas
limitações.

# 3 Exemplo prático unidimensional

Algumas diferenças entre as definições de extensão podem ser ilustradas através do caso
unidimensional. Seja definido o factor de alongamento $$ \lambda $$ como rácio do
comprimento do elemento linear antes e depois da deformação:

$$
\begin{equation}
\lambda = \frac{l}{l_0}
\end{equation}
$$

As extensões mais usuais: de engenharia $$ \varepsilon_e $$, de Green $$
\varepsilon_G $$, de Almansi $$ \varepsilon_A $$ e logarítmica $$
\varepsilon_{log} $$ podem ser determinadas em função do factor de alongamento:

$$
\begin{equation}
\varepsilon_e = \frac{l-l_0}{l_0} = \lambda -1
\end{equation}
$$

$$
\begin{equation}
\varepsilon_G = \frac{1}{2} \frac{l^2-l_0^2}{l_0^2} = \frac{1}{2} ( \lambda^2 -1 )
\end{equation}
$$

$$
\begin{equation}
\varepsilon_A = \frac{1}{2} \frac{l^2-l_0^2}{l^2} = \frac{1}{2} \left( 1-
\frac{1}{\lambda^2} \right)
\end{equation}
$$


$$
\begin{equation}
\varepsilon_{log} = \ln {\frac{l}{l_0}} = \ln {\lambda}
\end{equation}
$$

Quando o factor de alongamento é 1 a deformação é nula, algo
Na figura seguinte estão representadas as extensões em função de $$ \lambda $$.

{:refdef: style="text-align: center;"}
![get the PDF](/assets/img/fig.jpg)
{: refdef}

Na figura é visível que quando a deformação é muito pequena, ou seja,
quando o factor de alongamento $$ \lambda $$ é próximo da unidade, as várias
definições de extensão são equivalentes.

# 4 Considerações finais da Parte I
