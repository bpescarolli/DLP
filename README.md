# Sumário
  Instalando o Vivado

  Placa Basys3 Digilent

  Criando o primeiro projeto

  Simulando o projeto criado

  Implementando o projeto

  Gravando o projeto na Placa

  Exemplos de Projetos


# 🐱‍🏍Instalando o Vivado 2018.2

1° Antes de tudo você precisará ter uma conta no site da Xilinx através do endereço:
https://login.xilinx.com/app/xilinxinc_f5awsprod_1/exknv8ms950lm0Ldh0x7/sso/saml

![](/images/login_create_account_xilinx.jpg)

2° Após ter criado a conta e seguido todos os passos o qual o site manda ... acesse a sua conta.

![](/images/login_xilinx.jpg)

3° Após ter logado você deverá ir para em "Products" > "Hardware Development Tools" > "Vivado ML"

![](/images/xilins_products.jpg)

![](/images/xilins_products_hardware.jpg)

![](/images/xilins_products_hardware_Vivado.jpg)

4° Ao Acessar a pagina do Vivado você deverá ir em "Editions" > "Standart Edition Free" > "Download from Download Center"

![](/images/vivado_editions.jpg)

![](/images/vivado_editions_free.jpg)

![](/images/vivado_editions_free_download_center.jpg)

5° Na pagina do download center ir me "Vivado Archive" > "2018" > "2018.2"

![](/images/vivado_editions_free_download_center_Archives.jpg)

![](/images/vivado_editions_free_download_center_Archives_Select_Version.jpg)

6° Selecione para baixar o arquivo "Web-Pack"
![](/images/vivado_editions_free_download_center_Archives_Select_Version_WebPack.jpg)

7° Preenchas as informações e clique em download.
![](/images/forms.jpg)

8° Abra o executavel como administrador irá aparecer um aviso de baixar a ultima versão mais recente .. cliquem em Continue e "Next"

![](/images/open_file.jpg)

![](/images/continue.jpg)

![](/images/steup_1.jpg)

9° Irá pedir que você loge na conta da Xilins a mesma que você usou para baixar o executavel, preenche seu login e sua senha, selecione me "Download and Install Now" e por fim "Next"

![](/images/steup_1.jpg)

![](/images/steup_2.jpg)

10° Aguarde a instalação termina e reinicie o computador.

# 👋Criando o primeiro projeto

Em breve ...

# Exemplos de Projetos

## Somadores

### Efetuando Soma em binário
![](/images/soma.png)

A operação da imagem acima trata-se de uma operação soma de 29(11101) + 13(01101) em binário, tendo o mesmo raciocínio da soma que fazemos para decimal, 1+ 1 em binário teremos 10 (2 em decimal) , o qual o primeiro algarismo menos significativo(LSB) permanece o e mais significativo(LSB) “sobe” o qual chamamos de bit de transporte ou de Carry, marcados em vermelho e segue efetuando a soma para as demais posições.

![](/images/soma1.jpg)![](/images/soma2.jpg)

### Meio Somador (Half-Adder)

Possui a capacidade de adicionar dois dígitos binários únicos e fornece uma saída, ou seja temos dois bits de entrada (A e B) e dois de saída (Soma ou S e Carry_Out ou C).

![](/images/somador_meio.jpg)

![](/images/meio_somador.png)

Este tipo de circuito ele possui uma desvantagem, o qual é de apesar de mostrar e sinalizar o Carry(Vout) ele não leva isso para a próxima operação de soma ... como mostra as imagens abaixo:

![](/images/soma3.jpg)
![](/images/soma4.jpg)

### Somador completo (full-adder)

Diferente do meio somador(Half-adder), o somador completo (full-adder) propriamente dito , leva em consideração o bit de transporte (Carry) da operação anterior , pois ele possui uma entrada o qual armazena este valor da operação anterior ao efetuar uma nova o qual chamamos de Carry_In , ou seja temos 3 bits de entrada A, B e o Carry_In, e na saída temos S de soma e o C de Carry_out.

![](/images/somador_completo.jpg)
![](/images/somador_completo_table.jpg.png)


## Display de 7 segmentos

A placa Basys3 possui um display de 7 segmentos do tipo anodo comum energizado com 3.3V(nível lógico 1) por meio de um transistor(atuando como chave eletrônica) TBJ PNP acionados pelos pinos (W4, V4, U4, U2).

![](/images/7seg.jpg)

Sua lógica é inversa, ou seja para acionar os segmentos precisarei colocar 0V (jogar para nivel lógico 0) os pinos (W7, W6, U8, V8, U5, V5, U7 e V7).

Sendo assim representado da seguinte maneira:

![](/images/7seg2.jpg)

![](/images/7seg3.jpg)

## Contadores
Contadores são um arranjo sequencial de flip-flops o qual existem dois tipos síncronos e assíncronos ambos regidos por um sinal de clock.

Os contadores síncronos são quando os flip-flop são acionados de forma paralela no mesmo pulso de clock seja na borda de subida ou descida. Já o assíncronos o qual é o tipo
que iremos aplicar neste laboratório é quando o sinal de clock é colocado apenas na entrada do primeiro flip-flop e os outros são ligados em cascata.

![](/images/contador.png)

O que mais comumente usado é o contador assincrono por conta da sua simplicidade de implementação, porém temos ficarmos atento devido a atraso de propagação(insitreco no CI o qual é mencionado no datasheet) entre as comutações de um flip-flop o outro, o qual pode tornar o projeto impreciso e inviável devido ao acumulo de atrasos caso se utilizar muitos flip-flops.

No caso do circuitos sincrono não temos problemas de tempo de propagação(tempo é reduzido) pois todos os flip-flops estão ligados em paralelo, porém sua implementação requer uma atenção a mais na analise.

## Sistemas digitais sequenciais

Um sistema digital sequencial é basicamente composto por um circuito combinacional e por elementos de memória como mostra a imagem abaixo.

![](/images/combinacional.png)

As entradas e a saídas estão conectadas somente no circuito combinacional. Já os elementos de memoria(registradores compostos por flip-flop´s) são circuitos capazes de  armazenar informação codificada em binário, algumas saídas do circuito combinacional são entradas para os elementos de memoria constituem , uma parte das entrada do circuito combinacional o qual acabam recebendo o nome de variável de estado atual, com isso acaba formando um laço de realimentação pois a saída de um bloco e a entrada do outro e vice-versa.

A informações armazenada nos elementos de memoria determina o estado atual do circuito sequencial. O circuito sequencial com base nesta informação determina o valores da sua saída o qual torna estes os valores do próximo estado que é armazenado novamente pelo elementos de memoria e o ciclo volta a se repetir de forma sucessiva.

Estes circuitos é divido em dois tipos de acordo com o comportamento de seu sinal em função do tempo: síncronos e assíncronos.


