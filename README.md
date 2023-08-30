# <p align = "center">🔍 Simulações numéricas 3D em GPUs de hipertermia com nanopartículas por um modelo de bioaquecimento não linear </p>

<p align="center">
   <img src="https://i.imgur.com/XaCV8aK.gif" width="600" height="450" object-fit="cover"/>
</p>

***

##  :clipboard: Descrição 

Segundo a Organização Mundial de Saúde (OMS) em conjunto com a Organização Pan-Americana da Saúde (OPAS) o câncer é a segunda principal causa de morte no mundo e foi responsável por 9,6 milhões de mortes em 2018. A nível global, uma em cada seis mortes está relacionada à doença. Existem mais de 100 tipos de câncer, sendo os mais comuns os de pulmão, mama, colorretal, próstata, câncer de pele não-melanoma e estômago. Uma alternativa aos tratamentos convencionais que tem sido desenvolvida é realizada por meio de hipertermia onde o calor é empregado para superaquecer o tecido até uma determinada temperatura que leva à necrose das células, evitando a necessidade de um processo cirúrgico invasivo. Neste âmbito, esta pesquisa almeja utilizar métodos estocásticos para analisar e quantificar as incertezas relacionadas aos parâmetros de modelos matemáticos que descrevem um tratamento baseado em hipertermia. Através do uso desta ferramenta, pesquisadores poderão realizar o planejamento por meio de simulações in silico do procedimento, considerando as incertezas presentes nos parâmetros. Isto é, a análise das incertezas pode fornecer informações importantes para o planejamento de tratamentos por hipertermia. Além disso, este estudo pretende demonstrar que a análise de incertezas pode ser uma ferramenta importante para a medicina in silico, principalmente diminuindo a necessidade de ensaios clínicos com animais e também de estudos em humanos...

***

## :computer:	 Tecnologias e Conceitos 

- Método das Diferenças Finitas (MDF)
- Phyton
- C++
- Modelagem 3D
- Numpy
- Modelo Matemático de Pennes
- EDP Parabólica resolvida com Euler Implícito
- EDP Elíptica resolvida pelo método iterativo simples
- Heatmap

*** 

## :brain: Modelo Matemático de Pennes

<p align="center">
   <img src="https://i.imgur.com/zi5kPMY.png" width="900" height="500" object-fit="cover"/>
</p>

Figura 1: modelo matemático de Pennes com legenda descritiva das variáveis

***

## :pinching_hand: Modelo Matemático simplificado de Pennes

<p align="center">
   <img src="https://i.imgur.com/x9Fwgr7.png" width="900" height="450" object-fit="cover"/>
</p>

Figura 2: modelo matemático de Pennes simplificado com legenda descritiva das variáveis

***

## :books: Trabalhos 

1. [Simplificação do modelo matemático de Pennes em Phyton](https://github.com/lucasmartinso/IC/blob/main/pt1_Simula%C3%A7%C3%B5es_num%C3%A9ricas_3D_em_GPUs_de_hipertermia_com_nanopart%C3%ADculas_por_um_modelo_de_bioaquecimento_n%C3%A3o_linear.ipynb)
2. [Modelo matemático de Pennes em Phyton](https://github.com/lucasmartinso/IC/blob/main/Modelo_matem%C3%A1tico_Pennes.ipynb)
3. [Simplificação do modelo matemático de Pennes em C++](https://github.com/lucasmartinso/IC/blob/main/Compiling_Cpp_Colab.ipynb)
4. [Modelo matemático de Pennes em C++](https://github.com/lucasmartinso/IC/blob/main/C%2B%2B_Pennes.ipynb)

*** 

## :one: Simplificação do modelo matemático de Pennes em Phyton

Considera o modelo matemático de Pennes simplificado apresentado -figura(2)- em que é retratado uma situação inicial de tratamento sem a entrada de calor no sistema, ou seja, fluxo nulo. Nesse sentido, consideramos MDF para resolução desse problema, a partir de um método matématico iterativo para resolução da EDP elíptica retratada. Além desse, também consideramos trechos de modelagem do método de Cranck-Nicolson, porém a implementação quase como toda é modelada a partir do método iterativo simples.    
Para resolução, utilizamos dois métodos, Jacobi e Gauss-Seidal, em que para efeito de comparação em média obtemos uma resolução 3x mais ráṕida para Gauss-Seidal, isso se deve ao fato de Seidal considerar passos de solução anterioes ao longo da solução, o que faz com que o processo de convergência ganhe bastante agilidade, computacionalmente falando, menos iterações chegando ao mesmo resultado.
Assim sobre o problema modelado, esse retrata 4 tecidos humanos, derme, gordura, músculo e região tumoral e o comportamento dessas regiões mediante a temperatura, na qual considerou-se uma temperatura inicial de 37 Celsius, que está na faixa de temperatura média corporal humana. Logo, pode-se retirar como conclusão em que apesar das regiões apresentarem temperatura muito semelhantes, a região tumoral apresenta uma leve diferença de temperatura, um pouco maior, em que quanto mais afastada a região em análise do espaço tumoral, mais próximo da temperatura corporal essa será, ou seja, menor temperatura vai ter, apesar dessa relação não ser uniforme, mas é uma tendência que pode ser observada na análise da imagem abaixo  

<p align="center">
   <img src="https://i.imgur.com/P3DLqD6.png" width="400" height="500" object-fit="cover"/>
</p>

Pela implementação em Phyton temos um custo computacional mais elevado, devido a processos pouco otimizados da própria de linguagem de alto nível, fazendo com que o processo de compilação fique mais demorado e extenso para se chegar no resultado, um adendo importante a se fazer é que ao se aumentar o número de iterações máximas ou diminuir o erro relativo para a convergência temos que o processo pode-se tornar até inviável por conta do tempo necessário de compilação, isso se tratando de uma modelagem 2D, para resoluação da mesma em 3D o tempo aumentaria muito consideravelmente e provavelmente se tornaria pouco acessível em Phyton, fazendo a necessidade da implementação em linguagens de mais baixo nível como c/c++ 

*** 

## :two: Modelo matemático de Pennes em Phyton



***

## :three: Simplificação do modelo matemático de Pennes em C++

Nessa tratativa, temos o mesmo problema de (1), só que agora implementado em c++. Essa troca de linguagem fez com que o processo de compilação ganhasse muita eficiência, já que por se tratar de uma linguagem de mais baixo nivel proporciona processos de otimazação bem mais eficientes, tanto no quesito de tempo quanto em memória, reduzindo drasticamente o tempo de compilação, permitindo com que chegassemos em resultados mais precisos, visto que pode-se aumentar o número máximo de iterações e/ou diminuir o erro de convergência. Importante ressaltar que essa implementação teve uma tratativa mesmo que mais básica orientada a objetos, que em certos casos pode reduzir um pouco da eficiência da aplicação, porém ao mesmo tempo ganhasse mais semântica, facilita a manutenção e leitura do código. 

***

## :four: Modelo matemático de Pennes em C++

Temos o mesmo problema de (2), só que novamente implementado em c++, fazendo com que ganhassemos muita eficência no processo de compilação, segue o mesmo princípio adotado no item anterior, impactando em otimização de memória e tempo

***

## :stars: Contribuições 

Professor coordenador do projeto: [Ruy Freitas Reis](https://github.com/ruyfreis)   
Aluno orientado: [Lucas Martins Oliveira](https://github.com/lucasmartinso/)   
Instituição: UFJF 
