# Escalonamento de tarefas

## Informações gerais

- Capítulo: [Escalonamento de tarefas](https://wiki.inf.ufpr.br/maziero/lib/exe/fetch.php?media=socm:socm-06.pdf)
- Disciplina: *sistemas operacionais*
- Livro: [Sistemas Operacionais: Conceitos e Mecanismos](https://wiki.inf.ufpr.br/maziero/doku.php?id=socm:start)

## Aluno

- nome: Fabiana Campos Serra dos Santos
- matrícula: 20231014040033

## Respostas dos exercícios

### 01 Explique o que é escalonamento round-robin, dando um exemplo.
O escalonamento Round-Robin (RR) é um método de escalonamento preemptivo que atribui o processador a cada tarefa por um período de tempo fixo chamado quantum. Após esse tempo, se a tarefa não terminou, ela é colocada de volta na fila de prontas e o processador passa para a próxima tarefa. Isso continua em um ciclo, garantindo que todas as tarefas recebam tempo de processador de forma justa. Um exemplo é um sistema com três tarefas  T1, T2 E T3, cada uma com um tempo de quantum de 2 segundos. A sequência de execução poderia ser T1 > T2 > T3 > T1, e assim por diante até que todas completem a execução.

### 02 Considere um sistema de tempo compartilhado com valor de quantum tq e duração da troca de contexto ttc. Considere tarefas de entrada/saída que usam em média p% de seu quantum de tempo cada vez que recebem o processador. Defina a eficiência E do sistema como uma função dos parâmetros tq, ttc e p.

A eficiência E de um sistema de tempo compartilhado mede o tempo efetivo de uso do processador para o processamento de tarefas em comparação com o tempo total, incluindo trocas de contexto. A eficiência pode ser representada como:

\[E = \frac{tq \cdot (p / 100)}{tq + ttc}\]

onde: tq  é o quantum de tempo, ttc  é o tempo de troca de contexto, p% é a porcentagem do quantum utilizada efetivamente pela tarefa.


### 3. Explique o que é, para que serve e como funciona a técnica de aging.

A técnica de aging (envelhecimento) é usada para evitar a inanição (ou starvation) de tarefas de baixa prioridade. O aging aumenta gradualmente a prioridade de uma tarefa à medida que ela espera na fila de prontas. Quando uma tarefa espera por muito tempo, sua prioridade aumenta até que ela tenha a chance de ser executada. Esse mecanismo garante que todas as tarefas eventualmente recebam tempo de processador, melhorando a justiça no escalonamento.

### 04 No algoritmo de envelhecimento definido na Seção 6.4.6, o que seria necessário modificar para suportar uma escala de prioridades negativa?

O fator de envelhecimento deve diminuir o valor da prioridade dinâmica em vez de aumentá-lo. Assim, ao longo do tempo, uma tarefa que espera aumentaria sua prioridade com valores mais baixos até ser executada.

