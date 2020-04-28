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
análise? Este artigo tem como objectivo  as diferenças e vantagens entre as
várias definições de extensão e o âmbito das suas aplicações.

## 1.2 Conceitos

Para uma leitura adequada são definidos os seguintes conceitos:

*Corpo contínuo:* corpo com o interior totalmente preenchido por partículas
 materiais.

*Deformação Lagrangeana:* variação da distância entre dois pontos do interior do corpo.

*Extensão Euleriana:* medida da deformação em relação a um referencial que, por exemplo,
 pode variar consoante o tipo de formulação.

*Formulação Lagrangeana:* medição das grandezas físicas em relação à
 configuração inicial do corpo.

*Formulação Euleriana:* medição das grandezas físicas em relação à
 configuração deformada do corpo.

*Movimento de corpo rígido:* quando após a aplicação de forças ou deslocamentos
 sobre um corpo, a distância entre partículas materiais do interior do corpo se
 mantém inalterada.

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
$$x_i$$ - coordenadas da partícula material no instante $$t$$

# 2 Medição da deformação


Considere uma partícula material no interior da configuração inicial de um corpo
contínuo, correspondente ao instante $$t_0$$. A sua posição inicial $$P$$ é
definida pelo vector $$\vec{r}=X_ie_i$$. No instante $$t$$, a partícula material
passa a ocupar a posição $$P'$$ definida
pelo vector $$\vec{r'}=x_ie_i$$. O deslocamento da partícula material $$u$$ é obtido pela
diferença $$\vec{r'}-\vec{r}$$:

\begin{equation}
\begin{split}
& u = \vec{r'}-\vec{r} \\
 \Rightarrow \quad & u_i = (x_i -X_i)e_i \quad .
\end{split}
\end{equation}

Seja Q outra partícula material muito próxima da vizinhança de P (distância
infinitesimal). Na configuração inicial do corpo, a distância entre as duas
partículas materiais é dada por:

$$\begin{align}
\overline{PQ} = \mathrm{d} l =& \sqrt{\mathrm{d} X_1^2+\mathrm{d}
X_2^2+\mathrm{d} X_3^2}\\
=& \sqrt{\mathrm{d} X_i^2}
\end{align}$$

Para o instante $$t$$, a distância entre as duas partículas materiais é
calculada de forma análoga:


$$\begin{align}
\overline{P'Q'} = \mathrm{d} l' &= \sqrt{\mathrm{d} x_1^2+\mathrm{d}
x_2^2+\mathrm{d} x_3^2} \\
&= \sqrt{\mathrm{d} x_i^2}
\end{align}$$

Repare que $$ \mathrm{d} x_i $$ pode ser obtido em função da configuração
inicial do corpo $$ \mathrm{d} x_i = \mathrm{d} X_i + \mathrm{d} u_i$$ e $$
\mathrm{d} u_i = \frac{\partial u_i}{\partial x_k} \mathrm{d} x_k $$.

No caso de $$\overline{PQ}=\overline{P'Q'}$$, a distância entre as partículas
manteve-se o que significa que houve um movimento de corpo rígido.

Para medir a deformação começa-se por analisar a diferença do quadrado das
distâncias infinitesimais das partículas:


$$\begin{align}
\mathrm{d} l'^2 - \mathrm{d} l^2 &= \mathrm{d} x_i^2 - \mathrm{d} X_i^2 \\
 &= (\mathrm{d} X_i + \mathrm{d} u_i)^2 - \mathrm{d} X_i^2 \\
 &= \mathrm{d} X_i^2 + 2 \mathrm{d}X_i \mathrm{d} u_i + \mathrm{d} u_i^2 -
 \mathrm{d} X_i^2 \\
 &=  2 \mathrm{d}X_i \mathrm{d} u_i + \mathrm{d} u_i^2 \\
 &=  2 ( \frac{\partial u_i}{\partial X_k}) \mathrm{d}X_i \mathrm{d}X_k \\
 & \quad +(\frac{\partial u_i}{\partial X_k} \frac{\partial u_i}{\partial X_l})
 \mathrm{d}X_k \mathrm{d}X_l
\end{align}$$

No primeiro termo da direita troca-se os sufixos e no segundo termo os sufixos $$i$$
po $$l$$:

\begin{equation}
\mathrm{d} l'^2 - \mathrm{d} l^2 = 2 E_{ik} \mathrm{d}X_i \mathrm{d}X_k
\end{equation}

em que $$E_{ik}$$ é definido como a extensão de Green:

$$\begin{align}
E_{ik} &= \frac{1}{2} (\frac{\partial u_i}{\partial X_k} + \frac{\partial
u_k}{\partial X_i} + \frac{\partial u_l}{\partial X_k} \frac{\partial
u_l}{\partial X_i} ) \\
&= \frac{1}{2} (u_{i,k} + u_{k,i} + u_{l,k} u_{l,i})
\end{align}$$

A extensão de Green é dada em função da configuração inicial do corpo, ou seja,
trata-se de uma formulação Langrangeana. De forma análoga pode-se obter a
extensão de Almansi dada em função da configuração deformada do corpo
(formulação Euleriana):

\begin{equation}
e_{ik} = \frac{1}{2} \left(\frac{\partial u_i}{\partial x_k} + \frac{\partial
u_k}{\partial x_k} + \frac{\partial u_l}{\partial x_k} \frac{\partial
u_l}{\partial x_i} \right)
\end{equation}

No caso das deformações infinitesimais, as expressões anteriores podem ser
simplificadas e deixa de haver distinção entre a formulação Langreangena e
Euleriana. Como as deformações são muito pequenas, as suas medições em relação à
configuração inicial e deformada do corpo são equivalentes. Para além disso, o
produto presente nas expressões pode ser negligenciado. Desta forma obtém-se a
extensão de engenharia $$\varepsilon$$:

\begin{equation}
\varepsilon = \frac{1}{2} \left(\frac{\partial u_i}{\partial X_k} + \frac{\partial
u_k}{\partial X_i} \right)
\end{equation}

As extensões de engenharia são as mais utilizadas por permitirem uma relação
linear com as funções deslocamento. Contudo, estas simplificações têm as suas
limitações.

# 3 Âmbito de aplicação das deformações e rotações infinitesimais

### Introdução

Na mecânica dos materiais, apesar da natureza discreta da matéria, é assumido,
sempre que possível, a hipótese da continuidade. No âmbito da deformação, isto
significa que para qualquer configuração de um corpo corresponde uma região $$R$$
no espaço tridimensional totalmente preenchida por partículas materiais.

Considere-se uma partícula material da configuração inicial do corpo que ocupa a
posição do ponto $$P$$ definida pelo vector $$ \textbf{r} = x_i \textbf{e}_i$$.
 Quando  o corpo é deslocado, a partícula material passa a ocupar a posição
$$P'$$ definida pelo vector $$ \textbf{r'} = x'_i \textbf{e}_i$$. O deslocamento
da partícula é obtido pela diferença dos vectores $$ \textbf{r'} - \textbf{r}$$:

$$\begin{align} \textbf{u} &= \textbf{r'} - \textbf{r} \\
                             &= (x'_i - x_i)\textbf{e}_i \tag{1}
\end{align}$$

Se as distâncias entre as posições das partículas do corpo mantiverem-se
incalteradas após a deslocação, houve um movimento de corpo rígido, caso contrário
o corpo deformou-se.

Na secção seguinte começa-se por introduzir o conceito de deformação para o caso
unidimensional.

### Caso unidimensional de deformação

Considere-se uma barra com os graus de liberdade restringidos na extremidade
esquerda.

{:refdef: style="text-align: center;"}
![get the PDF](/assets/img/fig.jpg)
{: refdef}
