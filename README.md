# Notas de classe Neural Nets Prof. GeoffHinton

Algumas notas de classes sobre a matéria, observações e também algumas dúvidas

## Aula 2c

Nessa aula é apresentado um diagrama, conforme abaixo:

<img src="https://github.com/hitoshinagano/Notas-de-classe-Neural-Nets-Geoff-Hinton/blob/master/figuras/Figura_aula_2c.png" width="350">

O plano perpendicular ao vetor vermelho separa o espaço em dois lados:

1. uma parte dos pontos cujo produto interno *w*.x é positivo (lado A)
2. outra parte com pontos cujo produto interno *w*.x é negativo (lado B)

Se ponto x estiver classificado corretamente, o vetor *w* não precisa ser atualizado. Por exemplo, x é da classe 0 e o produto interno é negativo, então nada precisa ser feito. 

Ao contrário, se x estiver classificado incorretamente (por exemplo, x é classe 1), pelas regras de atualização do perceptron, *w*<-*w*+x. 
A atualização de *w*<-*w*+x gera um novo plano (em verde), sendo que o lado C corresponde a uma classificação dos pontos positivos, enquanto que o lado D aos pontos negativos. 

A atualização de *w*<-*w*+x faz com que *w* se "aproxime" de x. (*w* é "puxado" no sentido de x). Essa aproximação faz com que as chances do produto interno se tornar positivo aumentem. Veja, se dois vetores tem um ângulo maior que 90graus, somar x ao vetor *w*, fará o ângulo diminuir. 

Assim a dinâmica do perceptron faz com que o vetor *w* seja puxado no sentido de x, ou empurrado para longe de x (nesse caso quando o erro de classificação ocorre ao contrário do exemplo descrito acima, ou seja quando o ponto x é classe 0, mas é classificado como 1).
