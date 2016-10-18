# Notas de classe Neural Nets Prof. Geoff Hinton

Algumas notas de classes sobre a matéria, observações e também algumas dúvidas,<br>
e sempre em construção...

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

Ao contrário, no exemplo do Prof. Hinton (quando **w** é o 'bad weight vector' e **x** é da classe positiva), **x** está classificado incorretamente. Pelas regras de atualização do perceptron, será efetuado **w**<-**w**+**x**. 
A atualização de **w**<-**w**+**x** gera um novo plano (em verde), sendo que o lado C corresponde a uma classificação dos pontos positivos, enquanto que o lado D aos pontos negativos. 

<img src="https://github.com/hitoshinagano/Notas-de-classe-Neural-Nets-Geoff-Hinton/blob/master/figuras/apos_soma_w_com_x.png" width="500">

Veja que a atualização de **w**<-**w**+**x** faz com que **w** se "aproxime" do sentido de **x**. (**w** é "puxado" no sentido de **x**). Essa aproximação faz aumentar as chances do produto interno se tornar positivo. De fato, se dois vetores tem um ângulo maior que 90 graus, somar **x** ao vetor **w**, fará o ângulo diminuir. 

Então assim é a dinâmica do perceptron: um loop varre as observações, e a cada observação **x**, o vetor **w** ora é puxado no sentido de **x**, ou empurrado para longe de **x** (\*), sendo que atualizações ocorrem somente quando erros de classificação são encontrados.

(\*) caso onde o erro de classificação ocorre ao contrário do exemplo descrito acima, ou seja quando o ponto **x** é classe negativa, mas é classificado como positiva.



## Aula 2b: Uma interpretação geométrica do bias

<img src="https://github.com/hitoshinagano/Notas-de-classe-Neural-Nets-Geoff-Hinton/blob/master/figuras/bias.png" width="500">

Uma interpretação geométrica mais direta da figura acima seria algo assim:

* pontos classificados como positivos: w_1 * x_1 + w_2 * x_2 + b >= 0
* pontos classificados como negativos: w_1 * x_1 + w_2 * x_2 + b < 0

Uma outra seria...

Considere um ponto de classe negativa **n** = (-0.81, 0.84) e um outro de classe positiva **p** = (0.87, 0.62).<br>
(Esses pontos correspondem as primeiras linhas da matriz `neg_examples_nobias` e `pos_example_nobias` do 
arquivo `dataset1_ancient_octave.mat` do Assigment1 do curso. E o vetor de pesos **w** é o `w_init`)

<img src="https://github.com/hitoshinagano/Notas-de-classe-Neural-Nets-Geoff-Hinton/blob/master/figuras/bias2D.jpg" width="500">

Esses dois pontos encontram-se no plano 2D conforme a figura acima, mas vamos adicionar uma 3a dimensão que terá sempre valor 1. 
Assim, esses dois pontos serão **n** = (-0.81, 0.84, 1) e **p** = (0.87, 0.62, 1). Note que esses dois pontos estão no plano z=1.

Agora, seja o vetor **w** = (-0.62, 0.76, 0.77) referente aos pesos. O ultimo elemento de **w** corresponde ao bias. Esse vetor define um plano que passa pela origem e tem a seguinte equação: -0.62x + 0.76y + 0.77z = 0. Conforme visto anteriormente, esse plano separa o espaço em dois lados:

1. um lado cujos pontos **x** estão do "mesmo lado" que o vetor, assim o produto interno **w**.**x** será positivo
2. outro lado cujos pontos **x** encontra-se no "lado oposto" ao vetor, assim o produto interno **w**.**x** será negativo

Note que nesse exemplo, o ponto **n** está classificado incorretamente, enquanto **p** está corretamente classificado.

Agora sobre a interpretação geometrica do bias. A interseção desses dois planos: 

* -0.62x + 0.76y + 0.77z = 0  
* z = 1

será uma reta definida pela equação -0.62x + 0.76y + 0.77 = 0, ou aproximadamente

* y = 0.82x - 1

Se olharmos no plano 2D, essa reta será justamente a que divide os pontos classificados como positivos (acima da reta)
dos pontos classificados como negativos (abaixo da reta).

<a href="http://www.youtube.com/watch?feature=player_embedded&v=7p0CgaLevWE" 
target="_blank"><img src="http://img.youtube.com/vi/7p0CgaLevWE/0.jpg" 
alt="IMAGE ALT TEXT HERE" width="240" height="180" border="10" /></a>

Se **w** tivesse sua 3a dimensão sempre igual a zero, todas as interseções sempre passariam por (x,y) = (0,0). O fato da 3a dimensão de **w** ser diferente de zero (imagine o plano ortogonal a **w** inclinando para um dos lados), faz com que a reta de interseção possa não conter (0,0), aumentando as possibilidades de encontrar uma solução linearmente separável.  


## Aula 2e: What perceptrons can't do


<img src="https://github.com/hitoshinagano/Notas-de-classe-Neural-Nets-Geoff-Hinton/blob/master/figuras/Aula%202e.png" width="500">


## Aula 3a: Learning weights of a linear neuron

[//]: # (1:30 It is not true for perceptron learning. "...the outputs as whole can get further away from the target outputs, even though the weights are getting closer to a good set of weights...",... não entendi.)

* 8:58 Uma explicação mais detalhada do *batch* learning versus *online* learning pode ser encontrada no material do Prof. Andrew Ng.

* 11:01 Gostei desse exemplo. Features correlacionadas dificultam a convergencia da solução: "*It can be very slow if two input dimensions are highly correlated. If you almost always have the same number of portions of ketchup and chips, it is hard to decide how to divide the price between ketchup and chips.*

* 11:15 Tambem desse exemplo. semelhanças entre online learning e perceptron: "*In perceptron learning, we increment or decrement the weight vector by the input vector. But we only change the weights when we make an error*"  

## Aula 3b: 

O professor faz duas colocações: 

* No gradient descend, as variações caminham ortogonalmente as curvas de nível
* No online learning, as variações caminham ortogonalmente as retas 'constraint' para cada peso

<img src="https://github.com/hitoshinagano/Notas-de-classe-Neural-Nets-Geoff-Hinton/blob/master/figuras/Aula%203c%20grad%20descent%20e%20online%20learning.png" width="500">

Para a primeira, pensei em rabiscar algumas equações, mas vi que o assunto está super bem explicado em:

<a href="https://www.youtube.com/watch?v=Fpbdt376rGQ" 
target="_blank"><img src="http://img.youtube.com/vi/Fpbdt376rGQ/0.jpg" 
alt="IMAGE ALT TEXT HERE" width="240" height="180" border="10" /></a>

... e daí, somente checar que (utilizando a mesma notação do vídeo):
* interseção entre o plano **P** tangente a superficie **S** no ponto *(x_0, y_0, z_0)* e o plano *z = k*, ...
* ... será a reta tangente à curva de nível. 
* E a projeção do gradiente (vetor normal ao plano tangente a **S**) sobre o plano *z = k* ... 
* ... será perpendicular à curva de nível.

Quanto ao 'zig-zag', segue um video que preparei. Explica as diferenças entre o batch e online gradient descent com um exemplo em duas dimensões. 

<a href="https://www.youtube.com/watch?v=xpfND2MNw-0" 
target="_blank"><img src="https://img.youtube.com/vi/xpfND2MNw-0/0.jpg" 
alt="IMAGE ALT TEXT HERE" width="240" height="180" border="10" /></a>

## Aula 3c: 

<img src="https://github.com/hitoshinagano/Notas-de-classe-Neural-Nets-Geoff-Hinton/blob/master/figuras/Aula%203c.png" width="500">

## Aula 3d: 

<img src="https://github.com/hitoshinagano/Notas-de-classe-Neural-Nets-Geoff-Hinton/blob/master/figuras/Aula%203d%20new.png" width="800">


... So we can clearly do that for as many layers as we like. And after we've done that for all these layers, we can compute how the error changes as you change the weights on the connections. That's the backpropagation algorithm. It's an algorithm for taking one training case, and computing, efficiently, for every weight in the network, how the error will change as, on that particular training case, as you change the weight.
