# CPU de 8 bits no digital

Vídeo de demosntração: [https://youtu.be/CjeqOnWI43w](https://youtu.be/CjeqOnWI43w?si=StVY-bTJOdMpGsHa)

## Como executar o projeto

Para executar o projeto é necessário instalar software Digital a partir desse link: https://github.com/hneemann/Digital
A instalação do Java Environment (pelo menos JRE 8) é necessário para executar o Digital.

Depois dessas instalações concluidas o usuário deve baixar a pasta ./cpu e abrir o componente cpu.dig no simulador Digital e executar o mesmo para testar as funcionalidades do projeto.

Esse projeto desenvolvido no software Digital tem o objetivo de simular uma CPU de 8 bits contendo:

- ALU (Arithmetic Logic Unit)
- Program counter
- MAR (Memory Address Register)
- W-BUS
- Instruction Register
- Acumuladores
- Ring counter
- Circuit counter

Esse projeto foi contruido com base na arquitetura SAP (Simple as Possible).

**A ROM do MAR da CPU possui apenas uma única estrutura de dados. A variável acessada corresponde à mesma utilizada na sequência de instruções.**

Foi implementado o circuito de Fetch e Execute usando como referencia as seguntes palavras de controle

## Fetch: 
- 00101 1110 XX011 (PC -> MAR) - O conteúdo do Program Counter é colocado no BUS que manda a info pro MAR para que a memória saiba qual instrução buscar.
- 01011 1110 XX011 (PC++) - O Program Counter é incrementado para apontar para a próxima instrução.
- 00010 0110 XX011 (MAR/RAM -> IR) - manda o valor do program conter para o MAR (que vai pegar dois números e salvar no acumulador e mandar o valor da ordem de instrução de imput de comando aqui pro Registrador de Instrução (IR). A palavra de controle permite a leitura da instrução que sai da ROM do MAR que então é copiado e salvo dentro do IR.

## Execute

Cp|Ep|NLm|NCE| |NLi|NEi|NLa|Ea| |Su0|Su1|Su2|Eu|NLb|NLo
- Add
0b0101111000011 (PC -> MAR) - procura uma info na rom do mar
0b0010111000001 (RAM -> B) - guarda a info do rom do mar no b
0b0101111000011 (PC -> MAR) - procura outra info na rom do mar (outra variável para operação de soma)
0b0010110000011 (RAM -> AC) - guarda essa variável no acumulador
0b0011111000110 (ALU -> Out + Disp) - ativa a ALU manda pro out e mostra no display (os três zeros definem a operação soma). o 1 so lado dos 0 ativa a ALU
0b0011101000011 (Clear PC) - limpa o program counter

A operação aritimetica executada no ciclo de execute é de soma.



