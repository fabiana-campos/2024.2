# Implementação de tarefas

## Informações gerais

- Capítulo: [Implementação de tarefas](https://wiki.inf.ufpr.br/maziero/lib/exe/fetch.php?media=socm:socm-05.pdf)
- Disciplina: *sistemas operacionais*
- Livro: [Sistemas Operacionais: Conceitos e Mecanismos](https://wiki.inf.ufpr.br/maziero/doku.php?id=socm:start)

## Aluno

- nome: Fabiana Campos
- matrícula: 20231014040033

## Respostas dos exercícios

### 1. Explique o que é, para que serve e o que contém um TCB - Task Control Block.
um TCB é uma estrutura de dados que o núcleo do sistema operacional usa para representar e gerenciar cada tarefa. Nessa estrutura de dados são armazenadas as informações relativas ao seu contexto e os demais dados necessários à sua gerência, permitindo que o sistema controle e retome a execução da tarefa conforme necessário. O TCB inclui informações essenciais, como o identificador da tarefa, seu estado atual (nova, pronta, executando, etc.), informações de contexto do processador (como valores dos registradores), além de listas com áreas de memória e recursos utilizados, como arquivos abertos e conexões de rede. Ele também armazena informações de gerência e contabilização, como prioridade, usuário proprietário, data de início e volume de dados processados. 

### 4. O que são threads e para que servem? 
Uma thread é definida como sendo um fluxo de execução independente. Um processo pode conter uma ou mais threads, cada uma executando seu próprio código e compartilhando recursos com as demais threads localizadas no mesmo processo. Cada thread é caracterizada por um código em execução e um pequeno contexto local, o chamado Thread Local Storage (TLS), composto pelos registradores do processador e uma área de pilha em memória, para que a thread possa armazenar variáveis locais e efetuar chamadas de funções. Threads são também utilizadas para implementar fluxos de execução dentro do núcleo do SO, neste caso recebendo o nome de threads de núcleo. Além disso as threads de núcleo também incluem atividades internas do núcleo, como rotinas de drivers de dispositivos ou tarefas de gerência.

### 5. Quais as principais vantagens e desvantagens de threads em relação a processos?
Threads possui um custo de crição mais baixo em comparação a processos, também possui uma troca de contexto mais rápida e consomem menos memória. Além disso threads podem compartilhar dados facilmente através de variáveis globais e dinâmicas. Porém possui desvantagem de robustez ( um erro pode afetar todas as threads) e segurança (todas as threads
herdam as permissões do processo onde executam).


### 6. Forneça dois exemplos de problemas cuja implementação multi-thread não tem desempenho melhor que a respectiva implementação sequencial.
1- Um cenário onde a tarefa principal envolve operações de entrada/saída (I/O), como leitura e gravação em arquivos ou comunicação com redes, a implementação multi-thread não possui melhor desempenho porque enquanto uma thread aguarda a conclusão de uma operação de I/O, outras threads podem ficar inativas ou em espera.

2- Em um cenário onde várias threads precisam acessar um recurso compartilhado, como um banco de dados ou uma estrutura de dados, a implementação multi-thread pode sofrer de contenção significativa. O custo de gerenciamento para sincronizar o acesso a esse recurso pode ser tão alto que uma implementação sequencial se mostra mais vantajosa.

### 7 
- (a) Tem a implementação mais simples, leve e eficiente. -  many-to-one (N:1)
- (b) Multiplexa os threads de usuário em um pool de threads de núcleo. - many-to-many (N)
- (c) Pode impor uma carga muito pesada ao núcleo. - many-to-one (N:1)
- (d) Não permite explorar a presença de várias CPUs pelo mesmo processo. - many-to-one (N:1)
- (e) Permite uma maior concorrência sem impor muita carga ao núcleo. - many-to-many (N)
- (f) Geralmente implementado por bibliotecas. - many-to-one (N:1)
- (g) É o modelo implementado no Windows NT e seus sucessores. - one-to-one (1:1)
- (h) Se um thread bloquear, todos os demais têm de esperar por ele. - many-to-one (N:1)
- (i) Cada thread no nível do usuário tem sua correspondente dentro do núcleo. - one-to-one (1:1)
- (j) É o modelo com implementação mais complexa. - many-to-many (N)
