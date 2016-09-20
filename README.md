# Notas de classe Neural Nets Prof. GeoffHinton

Algumas notas de classes sobre a matéria, observações e também algumas dúvidas.

## Aula 2c: treinamento do vetor de pesos **w**

Nessa aula é apresentado um diagrama, conforme abaixo:

<img src="https://github.com/hitoshinagano/Notas-de-classe-Neural-Nets-Geoff-Hinton/blob/master/figuras/Figura_aula_2c.png" width="350">

Complementando a explicação do Prof. Hinton fiz a seguinte figura, na qual desenho um plano perpendicular ao vetor vermelho (linha grossa em vermelho)

<img src="https://github.com/hitoshinagano/Notas-de-classe-Neural-Nets-Geoff-Hinton/blob/master/figuras/plano_e_seus_dois_lados.png" width="500">

Esse plano separa o espaço em dois lados:

1. conjunto dos pontos cujo produto interno **w**.**x** é positivo (lado A)
2. outro conjunto dos pontos cujo produto interno **w**.**x** é negativo (lado B)

Se ponto **x** tivesse sido classificado corretamente, o vetor **w** não precisaria ser atualizado. 
Por exemplo, se **x** fosse da classe 0 e o produto interno sendo negativo, então nada precisaria ser feito e **w** não seria alterado. 

Ao contrário, no exemplo do Prof. Hinton (quando **w** é o 'bad weight vector' e **x** é da classe 1), **x** está classificado incorretamente. Pelas regras de atualização do perceptron, será efetuado **w**<-**w**+**x**. 
A atualização de **w**<-**w**+**x** gera um novo plano (em verde), sendo que o lado C corresponde a uma classificação dos pontos positivos, enquanto que o lado D aos pontos negativos. 

<img src="https://github.com/hitoshinagano/Notas-de-classe-Neural-Nets-Geoff-Hinton/blob/master/figuras/apos_soma_w_com_x.png" width="500">

Veja que a atualização de **w**<-**w**+**x** faz com que **w** se "aproxime" do sentido de **x**. (**w** é "puxado" no sentido de **x**). Essa aproximação faz aumentar as chances do produto interno se tornar positivo. De fato, se dois vetores tem um ângulo maior que 90 graus, somar **x** ao vetor **w**, fará o ângulo diminuir. 

Então assim é a dinâmica do perceptron: um loop varre as observações, e a cada observação **x**, o vetor **w** ora é puxado no sentido de **x**, ou empurrado para longe de **x** (\*), sendo que atualizações ocorrem somente quando erros de classificação são encontrados.

(\*) caso onde o erro de classificação ocorre ao contrário do exemplo descrito acima, ou seja quando o ponto **x** é classe 0, mas é classificado como 1

## Interpretação geométrica do bias

Considere um ponto de classe negativa $x_{neg} = (-0.81, 0.84)$ e um outro de classe positiva $x_{pos} = (0.87, 0.62)$
