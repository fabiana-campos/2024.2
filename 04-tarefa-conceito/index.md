# Conceito de tarefas

## Informações gerais

- Capítulo: [Conceito de tarefas](https://wiki.inf.ufpr.br/maziero/lib/exe/fetch.php?media=socm:socm-04.pdf)
- Disciplina: *sistemas operacionais*
- Livro: [Sistemas Operacionais: Conceitos e Mecanismos](https://wiki.inf.ufpr.br/maziero/doku.php?id=socm:start)

## Aluno

- nome: Fabiana Campos
- matrícula: 20231014040033

## Respostas dos exercícios

### 1. O que significa time sharing e qual a sua importância em um sistema operacional?
time sharing significa compartilhamento de tempo, ele é usado para otimizar a utilização do processador em sistemas operacionais, permitindo que múltiplas tarefas compartilhem o processador de maneira eficiente. Em um sistema de time-sharing, cada tarefa recebe um tempo específico de uso do processador, chamado de fatia de tempo ou quantum. Esse mecanismo é essencial para manter a responsividade e a interatividade dos sistemas, especialmente para aplicações interativas, como terminais de comando, onde é importante que o usuário não precise esperar muito para que sua ação seja processada.
   
### 2. Como e com base em que critérios é escolhida a duração de um quantum de processamento? 
Ela é definida com base em um equilíbrio entre responsividade e eficiência do sistema, considerando o tipo de aplicações, a necessidade de rápida resposta para tarefas interativas, e o impacto das trocas de contexto. Os critérios utilizados são: Tipo de Aplicações, responsividade do sistema, overhead de trocas de contexto, carga de trabalho e prioridades e capacidade de hardware.

### 3. Considerando o diagrama de estados dos processos apresentado na figura a seguir, complete o diagrama com a transição de estado que está faltando (t6) e apresente o significado de cada um dos estados e transições.

![image](https://github.com/user-attachments/assets/e9fc5cfb-26be-475e-825d-e03a8401a099)


### 4. Indique se cada uma das transições de estado de tarefas a seguir definidas é possível ou não. Se a transição for possível, dê um exemplo de situação na qual ela ocorre (N: Nova, P: pronta, E: executando, S: suspensa, T: terminada).
• E → P - Possível (a tarefa retorna a fila de tarefas prontas)
• E → S - Possível (a tarefa precisa esperar uma operação de entrada/saída, ficando suspensa até que o recurso esteja disponível)
• S → E  Impossível
• P → N  Impossível
• S → T   Impossível
• E → T   Possível  (a tarefa conclui sua execução, indo para o estado terminado)
• N → S   Impossível
• P → S   Possível (o sistema precisa liberar espaço na memória ou suspender tarefas prontas para dar prioridade a outras tarefas)

### 5. Relacione as afirmações abaixo aos respectivos estados no ciclo de vida das tarefas (N: Nova, P: Pronta, E: Executando, S: Suspensa, T: Terminada):
[ N ] O código da tarefa está sendo carregado.
[ P ] A tarefas são ordenadas por prioridades.
[ S ] A tarefa sai deste estado ao solicitar uma operação de entrada/saída.
[ T ] Os recursos usados pela tarefa são devolvidos ao sistema.
[ P ] A tarefa vai a este estado ao terminar seu quantum.
[ P ] A tarefa só precisa do processador para poder executar.
[ S ] O acesso a um semáforo em uso pode levar a tarefa a este estado.
[ E ] A tarefa pode criar novas tarefas.
[ E ] Há uma tarefa neste estado para cada processador do sistema.
[ S ] A tarefa aguarda a ocorrência de um evento externo.
