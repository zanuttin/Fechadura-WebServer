# Fechadura-WebServer
Sistema desenvolvido com a placa de desenvolvimento ESP-32 para a disciplina de Eletronica para a Computacao do professor Eduardo Simoes.

## O Projeto:

O projeto foi desenvolvido tendo em mente uma ferramenta para uso diario que facilitaria algum aspecto do meu dia. Por conta disso escolhi fazer um web server que posta o HTML por meio de println para o cliente. O projeto teve como base um projeto encontrado na internet que era responsavel por fazer o acionamento de um LED e entao ele foi adaptado para ser usado com um modulo de rele que faz o chaveamento da fonte da fechadura de portao HDL

## A Montagem:
1- Placa desenvolvimento ESP-32\
1- Modulo Rele 1 via\
1- Cabo PP 10 metros\
1- Fonte chinesa de procedencia duvidosa\
Alguns Jumpers\

O circuito funciona de forma bem simples ligando o modulo de rele a ESP-32 em 3 pontos:\
ESP-32 | Modulo Rele\
3V3====| VCC\
GND====| GND\
GPIO4==| IN\

E apos isso o fio positivo da fonte foi ligado ao comum do rele e o negativo direto na ponta preta do cabo PP. A ponta vermelha do cabo PP foi ligado ao conector normalmente fechado do rele e ambas outras extremidades ligadas em seus polos correspondentes na fechadura HDL

## O Codigo:

O codigo contido na ESP eh simples e eh responsavel por se conectar a uma rede Wi-Fi, imprimir seu IP para a maquina conectada por meio de um monitor serial, abrir um servidor Web local e aguardar por requisicoes. Quando chega uma requisicao pelo IP da ESP ela serve uma pagina que possui um botao "Abrir" que quando apertado faz uma requisicao para a placa com endereco final =/26 (era o pino utilizado pelo projeto base para acender um LED) e por meio disso um if eh acionado no loop da placa que realiza o acionamento do rele e o desarme do mesmo depois de 1 segundo.
