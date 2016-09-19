# Notas de classe Neural Nets Prof. GeoffHinton

Algumas notas de classes sobre a matéria, observações e também algumas dúvidas.

## Aula 2c

Nessa aula é apresentado um diagrama, conforme abaixo:

<img src="https://github.com/hitoshinagano/Notas-de-classe-Neural-Nets-Geoff-Hinton/blob/master/figuras/Figura_aula_2c.png" width="350">

Complementando a explicação do Prof. Hinton fiz a seguinte figura, na qual desenho um plano.

<img src="https://github.com/hitoshinagano/Notas-de-classe-Neural-Nets-Geoff-Hinton/blob/master/figuras/plano_e_seus_dois_lados.png" width="500">

Um plano perpendicular ao vetor vermelho (linha grossa em vermelho), que separa o espaço em dois lados:

1. conjunto dos pontos cujo produto interno **w**.**x** é positivo (lado A)
2. outro conjunto dos pontos cujo produto interno **w**.**x** é negativo (lado B)

Se ponto **x** estivesse classificado corretamente, o vetor **w** não precisaria ser atualizado. 
Por exemplo, se **x** fosse da classe 0 e o produto interno sendo negativo, então nada precisaria ser feito e **w** não precisaria ser alterado. 

Ao contrário, no exemplo do Prof. Hinto, **x** é da classe 1, e está classificado incorretamente. Pelas regras de atualização do perceptron, será efetuado **w**<-**w**+**x**. 
A atualização de **w**<-**w**+**x** gera um novo plano (em verde), sendo que o lado C corresponde a uma classificação dos pontos positivos, enquanto que o lado D aos pontos negativos. 

<img src="https://github.com/hitoshinagano/Notas-de-classe-Neural-Nets-Geoff-Hinton/blob/master/figuras/apos_soma_w_com_x.png" width="500">

A atualização de **w**<-**w**+**x** faz com que **w** se "aproxime" de x. (**w** é "puxado" no sentido de **x**). Essa aproximação faz com que as chances do produto interno se tornar positivo aumentem. Veja, se dois vetores tem um ângulo maior que 90graus, somar **x** ao vetor **w**, fará o ângulo diminuir. 

Assim a dinâmica do perceptron faz com que o vetor **w** seja puxado no sentido de **x**, ou empurrado para longe de **x** (nesse caso quando o erro de classificação ocorre ao contrário do exemplo descrito acima, ou seja quando o ponto **x** é classe 0, mas é classificado como 1).
