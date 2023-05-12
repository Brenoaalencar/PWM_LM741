# PWM_LM741
Gerador analógico de PWM com amplificador operacional LM741, por Breno Alencar, Lorran Caetano e Nívea Abreu

O projeto tem a finalidade de descrever a montagem e o funcionamento de 
um controlador PWM (Pulse Width Modulation) analógico.
A montagem será dividida em três circuitos: oscilador, integrador e comparador. A união desses 
três circuitos é capaz de controlar o tempo de duração de um pulso, ou seja, a 
largura de um pulso.

### Componentes utilizados
* 3 amplificadores operacionais TL081 na simulação e LM741 na protoboard
* 2 baterias de 9V
* 2 capacitores de 100nF
* 1 transistor 2N3904 na simulação e BC547B na protoboard
* 1 LED
* 4 resistores de 10 kΩ
* 1 (3 na protoboard) resistores de 100 kΩ
* 1 resistor de 330 Ω
* 2 potenciômetros de 50 kΩ

### Esquema elétrico do circuito oscilador
Abaixo, segue a montagem do circuito oscilador:

<div align="center">
<img src ="https://github.com/Brenoaalencar/Estacao_Meteorologica/assets/72100554/da38e531-4145-4e4d-9bb2-08ad5584529b" width="400px"/>
</div>

R3 e R10 são divisores da tensão Vosc que, de acordo com as entradas Vcc e Vce do 
amplificador operacional, podem ser +9V ou –9V. Portanto a entrada não inversora do 
amplificador assume valores de +4,5V ou –4,5V. Optamos por altas resistências, para que 
pouca corrente atravesse os resistores, ou seja, apenas a informação da tensão é propagada 
por eles.
Na porção superior do oscilador temos um resistor variável que afetará o tempo de carga e 
descarga do capacitor e, assim, regulando a tensão na entrada não inversora. Tomando como –4,5V a tensão sobre o capacitor e 30 kohms a resistência do potenciômetro teremos um período de 6,59 ms e uma frequência de 151,74 Hz.

Um oscilador gera uma onda quadrada de frequência fixa. Em nosso projeto físico, 
adicionamos um potenciômetro para variar a frequência.

<div align="center">
<img src ="https://github.com/Brenoaalencar/PWM_LM741/assets/72100554/6e6b05cc-7cc4-42fc-bd0b-7c4cae26e19d" width="400px"/>
</div>

### Esquema elétrico do circuito integrador
Abaixo, segue a montagem do circuito integrador:

<div align="center">
<img src ="https://github.com/Brenoaalencar/PWM_LM741/assets/72100554/2fb9c666-48a7-46df-b23d-3909bea8e559" width="200px"/>
</div>

O circuito acima foi elaborado com base nas seguintes considerações:
Utilizando a onda quadrada gerada no primeiro circuito na entrada inversora do segundo 
amplificador operacional, e tendo como referência uma tensão de 0V na entrada não inversora, 
produziremos uma onda triangular ao adicionarmos um capacitor à entrada inversora e à saída 
do amplificador. O resistor R12 em paralelo com o capacitor é utilizado para completar o filtro passa baixas e 
atenuar frequências maiores que as de corte.

<div align="center">
<img src ="https://github.com/Brenoaalencar/PWM_LM741/assets/72100554/b0131381-9c6f-4e78-99d6-669484abe7bf" width="400px"/>
</div>

### Esquema elétrico do circuito comparador
Abaixo, segue a montagem do circuito comparador:

<div align="center">
<img src ="https://github.com/Brenoaalencar/PWM_LM741/assets/72100554/d11aecba-2403-41a7-877c-fe892410b796" width="200px"/>
</div>

O comparador recebe o sinal triangular do integrador na entrada não inversora e o compara 
com uma tensão de referência: a da entrada não inversora, que pode ser regulada com um 
potenciômetro e um resistor fixo, que funcionam como divisores de tensão variando entre 6V 
e 0V. A tensão de saída do último amplificador +/-9V tem a largura do seu pulso variada por 
essa mudança de tensão. 
Por fim, o sinal modulado que sai do comparador chega ao transistor e o satura com a corrente 
que chega à base, fechando o circuito e acionando o LED. Utilizaremos um resistor de 330 
ohms em nossa protoboard, pois a corrente que sai do amplificador operacional é de 18,38 mA 
e a queda de tensão do LED é de aproximadamente 2,6V. 


### Montagem e resultados
Finalizada a montagem, obteve-se os gráficos de saída do circuito

<div align="center">
<img src ="https://github.com/Brenoaalencar/PWM_LM741/assets/72100554/a2d544b2-20e8-4069-98b3-e097efeb5e6e" width="400px"/>
</div>

Sinal do PWM para maior intensidade do LED. Duty Cycle próximo de 100%.

<div align="center">
<img src ="https://github.com/Brenoaalencar/PWM_LM741/assets/72100554/9971904b-487a-485b-91fe-4619d0add263" width="400px"/>
</div>

Sinal do PWM para menor intensidade do LED. Duty Cycle próximo de 0%








