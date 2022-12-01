# `<Varal Inteligente>`
  

# `<Smart Clothesline>`  

## Apresentação


O presente projeto foi originado no contexto das atividades da disciplina de graduação *EA075 - Sistemas Embarcados*, oferecida no segundo semestre de 2022, na Unicamp, sob supervisão da Profa. Dra. Paula Dornhofer Paro Costa, do Departamento de Engenharia de Computação e Automação (DCA) da Faculdade de Engenharia Elétrica e de Computação (FEEC).

|Nome | RA | Curso|
|--|--|--|
| Tony Tian Rui Li | 206373 | Eng. Elétrica|
| Otávio Soares do Espírito Santo Lima | 223031 | Eng. Elétrica|
## Descrição do Projeto
Quem nunca saiu de casa e esqueceu de recolher as roupas do varal? Para resolver esse problema propomos o sensor inteligente de chuva que tem como seu principal objetivo recolher o varal de estender roupa quando houver indícios de chuva, suprindo essa e outras impossibilitadas de retirarem suas roupas de ambientes chuvosos.
## Descrição Funcional
### Funcionalidades
  - Comunicação sem fio via wi-fi para sincronizar informações de sites clima-tempo, para acionar atuadores e para avisar ao proprietário que o sistema foi acionado
- Medição de umidade
### Configurabilidade
  Aplicativo que possibilita escolher o site de referência, configurar o setpoint de mínimo de probabilidade de chuva e umidade do ar.
### Eventos
- Umidade igual ou maior que valor configurado
- Umidade menor que valor configurado
- Indicativo de % de chuva igual ou maior que configurado
- Indicativo de % de chuva menor que configurado
- Presença de água no sensor de chuva
### Tratamento de Eventos
- Quando aumentar o nível de umidade o sensor irá checar se há a probabilidade alta de chuva se sim irá acionar os atuadores para recolher o varal, se não , ele aguardará para a probabilidade de chuva aumentar para acionar os atuadores e comunicar o proprietário
- Quando houver uma probabilidade alta de chuva o sensor irá checar se há a o nível de aumento de umidade se sim irá acionar os atuadores para recolher o varal e comunicar o proprietário, se não , ele aguardará para que o aumento de umidade for significante para acionar os atuadores e se comunicar o proprietário
- Quando o sensor de chuva detectar presença de água, irá acionar os atuadores para recolher o varal e comunicar o proprietário
- Quando diminuir o nível de umidade do sensor e a probabilidade de chuva estiver baixa, irá acionar os atuadores para estender o varal novamente
## Descrição Estrutural do Sistema
![Micro Controlador](https://github.com/OtavioSoares1997/ea075/blob/main/2022.2/Micro%20Controlador.png)
## Especificações
### Especificação Estrutural
O microcontrolador escolhido é o ESP-32, este possui módulo wifi e bluetooth, ele se comunicará com o sensor de chuva (YL-83), ao ser detectado chuva, um atuador será acionado, o atuador escolhido é o motor DC de alto torque (12V, 80W). Para alimentar o circuito é necessário um conversor AC-DC de 220V/110V para 12V/5V e um regulador de saída de 3,3V.
 
### Especificação de Algoritmos 

![Alt](YL-83 (Sensor de Chuva).png)



## Referências
- https://blog.bidu.com.br/sensor-de-chuva/#:~:text=O%20que%20%C3%A9%20Sensor%20de,de%20interven%C3%A7%C3%A3o%20instant%C3%A2nea%20do%20motorista.
- [https://sigmasensors.com.br/sensor-temperatura-umidade#:~:text=Sensor%20de%20Temperatura%20e%20Umidade%20%C3%A9%20um%20equipamento%20que%20pode,(temperatura%20e%20umidade%20foliar)](https://sigmasensors.com.br/sensor-temperatura-umidade#:~:text=Sensor%20de%20Temperatura%20e%20Umidade%20%C3%A9%20um%20equipamento%20que%20pode,(temperatura%20e%20umidade%20foliar)).
