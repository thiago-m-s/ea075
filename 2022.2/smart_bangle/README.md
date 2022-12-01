# `Pulseira Inteligente`
# `Smart Bangle`

## Apresentação

O presente projeto foi originado no contexto das atividades da disciplina de graduação *EA075 - Sistemas Embarcados*, 
oferecida no segundo semestre de 2022, na Unicamp, sob supervisão da Profa. Dra. Paula Dornhofer Paro Costa, do Departamento de Engenharia de Computação e Automação (DCA) da Faculdade de Engenharia Elétrica e de Computação (FEEC).

> 
> |Nome  | RA | Curso|
> |--|--|--|
> | Rafael Cirino | 223730  | Eng. Elétrica|
> | Tarciso Hattum | 224622 | Eng. Elétrica|


## Descrição do Projeto
> Seja em lugares com muitas ou poucas pessoas é necessário que a empresa administradora do local possua controle sobre o acesso de público, monitore a sua permanência durante evento ou interaja com ele proporcionando a melhor experiência possível, criando assim uma lembrança afetiva entre a marca e o cliente.
>  
> Tendo em vista o que foi mencionado acima, o projeto tem como objetivos principais facilitar o controle e permitir uma maior interação com o público em grandes eventos, seja shows, parque de diversões/aquáticos, eventos esportivos etc. Além disso, pode ser utilizada para pequenas aplicações, por exemplo restaurantes, onde o seu uso seria indicado para registro de comanda e aviso de liberação de mesa.
> 
> O projeto em si, é uma pulseira que possui comunicação sem fio, um identificador RFID, led, sistema vibra-call e é prova d' água. Abaixo, como exemplo, estão listados alguns cenários de uso:
> - Show
>   - Proporcionar uma experiência sensorial memorável ao público, onde todos estão com a pulseira e a partir de comandos enviados por uma central para elas, é possível sincronizar o acionamento dos leds, fazendo com que diferentes partes do público pisquem em determinada cor e intensidade, criando um mosaico e um efeito luminoso.
> - Parque aquático e de diversões 
>   - Através do RFID é possível monitorar a entrada do público em brinquedos, bem como fornecer alertas na pulseira a partir de sinais enviados por uma central e proporcionar uma experiência coletiva entre os visitantes.
> - Restaurantes
>   - Em restaurantes, a smart bangle substitui os antigos pagers que avisam quando a mesa está liberada, além disso, ela pode ser utilizada na hora de resgitro da comanda. Atualmente em muitos estabelecimentos garçons utilizam tablet ou celular para registar os pedidos, só quem ainda é necessário que haja uma numeração das mesas, que cria um outro problema, dificuldade na criação de comandas separadas, a smart bangle resolve, pois com cada cliente usando uma pulseira, a partir da identificação RFID, o garçom consegue encostar o tablet ou telefone nela e assim gerar o pedido para a comanda daquele cliente em especifico. 
>


## Descrição Funcional
### Funcionalidades
> - **Comunicação sem fio**: responsável pela comunicação via rádio frequência entre a central e a pulseira com o auxílio de uma antena;
> - **Acionar LED**: atuador é acionado ao receber algum sinal de controle da central. Um exemplo seria num show onde a smart bangle receberia sinais de controle com o objetivo de sincronizar todas as pulseiras com certa cor e certa frequência;
> - **Vibrar**: atuador é acionado ao receber algum sinal de controle da central. Por exemplo, a smart bangle vibra com o intuito de avisar/alertar o usuário de algum evento próximo importante;
> - **RFID**: Fornecer uma identificação única para a pulseira.
> - **Carregamento por indução**: com o auxílio de bobinas, o carregamento por indução é responsável por garantir que o produto esteja com uma bateria adequada para uso e também por carregar simultaneamente diversos aparelhos;
> - **Prova d'agua**: pensado na aplicação de uso em parques aquáticos, a pulseira a prova d'agua garante maior durabilidade e necessita de forte isolamento;
> - **Bateria de longa duração**: uma bateria de longa duração é necessária para durar todo o evento.

### Configurabilidade
> - **Antena:** Sistema de entrada de dados via rádio frequência com banda de 142 a 1050 MHz
> - **Led RGB:** Sistema de saída com três diodos emissores de luz em vermelho, verde e azul.
> - **Atuador vibra-call:** Sistema de saída com nano atuador de vibra call
> - **Tag RFID:** Tag configurado com um id especifico para a smart bangle
> - **Bateria:** Aproximadamente 500 mAh, para durar cerca de 16h.
> - **Microcontrolador:** Com baixo consumo de energia, que permita interrupção, não é necessário grande capacidade de processamento e que permita codificar sinais de rede sem fio.
> - **Bobina para carregamento por indução:** Bobina de carregamento 5V que suporte pelo menos 1000mA de corrente
> - **Circuitos eletrônicos:** 
>	  - Capacitores;
>	  - Resistores;
>	  - Diodos;
>	  - Indutores;
>	  - Receptores;
>	  - Interfaces de entrada e saída;
>	  - Cristal de clock;
>	  - Regulador de tensão;
>	  - Decodificador;
>	  - Circuito de alimentação;
>	  - Icsp;

### Eventos
> | Evento  | Periodicidade | Prioridade |
> |--|--|--|
> |Sem fio | Média | Alta |;
> |Led | Média | Média |;
> |Vibra-call | Baixa | Média |;
> |Carregamento | Baixa | Média |;
> |Economia de energia | Baixa | Alta |;
> |Alerta/Aviso | Média | Alta |;
> |Festa | Média | Alta |
> |LED Estado | Baixa | Baixa |;

### Tratamento de Eventos
> - **Stand by**: No modo espera somente o circuito de comunicação sem fio fica ativo, esperando algum comando externo para atuar.
> - **Sem fio**: Disparado quando há alguma comunicação externa, decodifica o sinal recebido e determina a ação necessária.
> - **LED**: Ativação os leds com determinada frequência e cor.
> - **Atuador vibra-call**: Pulseira irá vibrar por um determinado período.
> - **Carregamento**: Quando algum sistema de indução é conectado, uma interrupção é gerada e a smart bangle entra no estado carregamento.
> - **Economia de energia**: o bloco de processamento verifica se a smart bangle está com bateria baixa (bateria < 10%). Se sim, vai para o modo economia de energia, aciona um LED de estado (bateria baixa: led vermelho, carregando: led azul) e a conexão sem fio é cortada;
> - **Alerta/Aviso**: identifica a mensagem via conexão sem fio e se for necessário, gera um aviso, acionando vibra call e/ou o LED RGB;
> - **Festa**: identifica mensagem via conexão sem fio, entra no modo festa que faz o acionamento do LED com frequências específicas;
> - **LED Estado**: responsável pelo processamento da frequência e a cor de ativação dos LEDs.

## Descrição Estrutural do Sistema
>
> - Primeiramente a smart bangle se encontra no modo "Stand By". Ela verifica se há baixa bateria ou não. Caso sim, ela entra no modo "economia de energia";
>
> - No modo "economia de energia" é desligado o módulo conexão sem fio, é acionado o LED vermelho e volta ao modo "Stand By";
> 
> - Ao ser conectado ao sistema de carregamento por indução, entra no modo carregamento, ativa a conexão sem fio e vai para o "LED Estado";
> 
> - O "LED Estado" define a cor do LED acendido: ao estiver carregando o led azul será aceso e quando estiver com a carga 100% o led verde será aceso;
>
> - Caso a bateria esteja compatível, ela começa a comunicação sem fio;
>
> - O modo "sem fio" recebe a mensagem e decodifica para o acionamento dos comandos;
>
> - O estado "Alerta/Aviso" identifica se será necessário o acionamento do LED e/ou do vibra-call;
>
> - O estado "Festa" vai processar a frequência e a cor de ativação os LEDs;
>


<img src="smart-bangle_ea075.drawio.svg" width=120% height=120%>


## Referências
> - https://pvieito.com/2016/09/xyloband-reverse-engineering
> - https://www.instructables.com/Hacking-a-Xyloband-With-Arduino/
> - https://blog.hqcodeshop.fi/archives/395-Xyloband-Whats-inside-one.html
