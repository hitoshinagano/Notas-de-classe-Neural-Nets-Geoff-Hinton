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
Por exemplo, se **x** fosse da classe negativa e o produto interno sendo negativo, então nada precisaria ser feito e **w** não seria alterado. 

Ao contrário, no exemplo do Prof. Hinton (quando **w** é o 'bad weight vector' e **x** é da classe 1), **x** está classificado incorretamente. Pelas regras de atualização do perceptron, será efetuado **w**<-**w**+**x**. 
A atualização de **w**<-**w**+**x** gera um novo plano (em verde), sendo que o lado C corresponde a uma classificação dos pontos positivos, enquanto que o lado D aos pontos negativos. 

<img src="https://github.com/hitoshinagano/Notas-de-classe-Neural-Nets-Geoff-Hinton/blob/master/figuras/apos_soma_w_com_x.png" width="500">

Veja que a atualização de **w**<-**w**+**x** faz com que **w** se "aproxime" do sentido de **x**. (**w** é "puxado" no sentido de **x**). Essa aproximação faz aumentar as chances do produto interno se tornar positivo. De fato, se dois vetores tem um ângulo maior que 90 graus, somar **x** ao vetor **w**, fará o ângulo diminuir. 

Então assim é a dinâmica do perceptron: um loop varre as observações, e a cada observação **x**, o vetor **w** ora é puxado no sentido de **x**, ou empurrado para longe de **x** (\*), sendo que atualizações ocorrem somente quando erros de classificação são encontrados.

(\*) caso onde o erro de classificação ocorre ao contrário do exemplo descrito acima, ou seja quando o ponto **x** é classe negativa, mas é classificado como positiva.

## Aula 2b: Interpretação geométrica do bias

<img src="https://github.com/hitoshinagano/Notas-de-classe-Neural-Nets-Geoff-Hinton/blob/master/figuras/bias.png" width="500">

Considere um ponto de classe negativa **n** = (-0.81, 0.84) e um outro de classe positiva **p** = (0.87, 0.62)

<img src="https://github.com/hitoshinagano/Notas-de-classe-Neural-Nets-Geoff-Hinton/blob/master/figuras/bias2D.jpg" width="500">

Esses dois pontos encontram-se no plano 2D conforme a figura abaixo, mas vamos adicionar uma 3a dimensão que terá valor 1. 
Assim, esses dois pontos serão **n** = (-0.81, 0.84, 1) e **p** = (0.87, 0.62, 1). Note que esses dois pontos estão no plano z=1.

Agora, seja o vetor **w** = (-0.62, 0.76, 0.77) referente aos pesos, sendo que o ultimo elemento corresponde ao bias. Esse vetor define um plano que passa pela origem e tem a seguinte equação: -0.62x + 0.76y + 0.77z = 0. Conforme visto anteriormente, esse plano separa o espaço em dois lados:

1. um lado cujos pontos **x** estão do mesmo lado que o vetor, assim o produto interno **w**.**x** será positivo
2. outro lado cujos pontos **x** encontra-se no lado oposto ao vetor, assim o produto interno **w**.**x** será negativo

O ponto **n** está classificado incorretamente, enquanto **p** está corretamente classificado - para este valor de **w**.

Agora sobre a interpretação geometrica do bias. A interseção do plano definido por 

* -0.62x + 0.76y + 0.77z = 0  
* z = 1

será uma reta definida pela equação -0.62x + 0.76y + 0.77 = 0, ou aproximadamente

* y = 0.82x - 1


