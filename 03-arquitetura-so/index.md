# Arquiteturas de Sistemas Operacionais

## Informações gerais

- Capítulo: [Arquitetura de SO](https://wiki.inf.ufpr.br/maziero/lib/exe/fetch.php?media=socm:socm-03.pdf)
- Disciplina: *sistemas operacionais*
- Livro: [Sistemas Operacionais: Conceitos e Mecanismos](https://wiki.inf.ufpr.br/maziero/doku.php?id=socm:start)

## Aluno

- nome: Fabiana Campos Serra dos Santos
- matrícula: 20231014040033

## Respostas dos exercícios


### 1. Monte uma tabela com os benefícios e deficiências mais relevantes das principais arquiteturas de sistemas operacionais.

| Arquitetura       | Benefícios Principais                                                                 | Deficiências Principais                                                               |
|-------------------|----------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------|
| **Monolítica**    | - Alto desempenho devido ao acesso direto aos recursos do sistema.                      | - Falhas em um componente podem comprometer todo o sistema.                            |
|                   | - Sistema mais rápido e compacto.                                                      | - Complexidade na manutenção devido às interdependências entre os componentes.       |
|                   | - Menor sobrecarga na comunicação entre os componentes.                                | - Dificuldade em evoluir e manter o código, pois mudanças podem impactar outros módulos. |
| **Micronúcleo**   | - Maior modularidade e flexibilidade.                                                   | - Desempenho inferior devido ao custo elevado das trocas de mensagens e cópias de dados. |
|                   | - Melhor robustez, com falhas isoladas sem afetar o sistema como um todo.               | - Necessita de múltiplas trocas de mensagens para realizar operações simples.         |
|                   | - Facilidade em adicionar e remover serviços.                                          | - Desempenho não competitivo em sistemas de uso geral.                               |
| **Em Camadas**    | - Modularização clara, com camadas definindo responsabilidades.                         | - Empilhamento de camadas pode prejudicar o desempenho.                               |
|                   | - Facilidade de manutenção e evolução do sistema devido à separação das camadas.        | - Dificuldade em dividir funcionalidades entre camadas, pois muitas são interdependentes. |
|                   | - Estruturação que facilita o entendimento e a extensão do sistema.                     | - Impacto no desempenho devido à comunicação entre camadas.                          |
| **Híbrido**       | - Combina os benefícios de sistemas monolíticos e micronúcleos.                         | - Complexidade na implementação devido à combinação de características de diferentes arquiteturas. |
|                   | - Melhor desempenho em comparação aos micronúcleos.                                     | - Potencial para ser mais pesado do que um micronúcleo puro.                         |
|                   | - Flexibilidade e robustez, com alguns componentes no núcleo e outros fora dele.        | - Pode sofrer de ineficiências por misturar as vantagens dos dois tipos de núcleos.   |
| **Máquinas Virtuais** | - Execução de múltiplos sistemas operacionais isolados sobre o mesmo hardware.           | - Overhead devido à sobrecarga de virtualização, afetando o desempenho.                |
|                   | - Facilidade em testar e isolar sistemas diferentes.                                    | - A virtualização pode consumir mais recursos, como memória e CPU.                    |
| **Contêineres**   | - Isolamento de processos com uso eficiente de recursos.                                | - Dependência do kernel para gerenciamento de contêineres.                           |
|                   | - Menor sobrecarga comparado às máquinas virtuais, com compartilhamento de núcleo.     | - Pode ser difícil garantir total isolamento entre contêineres.                       |
|                   | - Ideal para implantação de aplicativos em nuvem devido à leveza.                       | - Menos flexível que as máquinas virtuais em termos de suporte a múltiplos SOs.       |
| **Exonúcleo**     | - Desempenho elevado, com redução de abstrações e sobrecarga do núcleo.                | - Exige que as aplicações implementem suas próprias abstrações, o que pode ser complexo. |
|                   | - Permite que o hardware seja acessado de forma mais eficiente.                        | - Pode ser mais difícil de programar e manter, pois as abstrações precisam ser feitas pela aplicação. |
| **Uninúcleo**     | - Desempenho muito alto devido à compilação do núcleo e da aplicação em um único binário. | - Não é flexível para rodar múltiplas aplicações, pois o sistema é dedicado a uma única aplicação. |
|                   | - Sistema mais leve e rápido, ideal para ambientes de nuvem ou servidores dedicados.    | - Difícil de manter e evoluir em sistemas que precisam de múltiplas aplicações ou serviços. |




### 2. O Linux possui um núcleo similar com o da figura 3.1, mas também possui “tarefas de núcleo” que executam como os gerentes da figura 3.2. Seu núcleo é monolítico ou micronúcleo? Por quê?
Embora o Linux tenha um design modular e possa ter "tarefas de núcleo" semelhantes às de sistemas com micronúcleos, ele é monolítico, pois a grande maioria dos serviços essenciais ainda reside no núcleo e há uma comunicação direta e rápida entre esses componentes. A modularidade no Linux não altera sua natureza como um núcleo monolítico, onde o código de gerenciamento de recursos e drivers está diretamente integrado e não isolado em espaços separados.

### 3. Sobre as afirmações a seguir, relativas às diversas arquiteturas de sistemas operacionais, indique quais são incorretas, justificando sua resposta:
(a) Uma máquina virtual de sistema é construída para suportar uma aplicação escrita em uma linguagem de programação específica, como Java. 
Incorreta. Esta definição descreve uma máquina virtual de aplicação. Uma máquina virtual de sistema é projetada para executar um sistema operacional completo (ou vários sistemas operacionais), não apenas uma aplicação.

(b) Um hipervisor convidado executa sobre um sistema operacional hospedeiro.
Correta.

(c) Em um sistema operacional micronúcleo, os diversos componentes do sistema são construídos como módulos interconectados executando dentro do núcleo.
Incorreta. No micronúcleo, os componentes estão fora do núcleo, não dentro.

(d) Núcleos monolíticos são muito utilizados devido à sua robustez e facilidade de manutenção.
Incorreta. Núcleos monolíticos têm alto desempenho, mas não são fáceis de manter nem são robustos.


(e) Em um sistema operacional micronúcleo, as chamadas de sistema são implementadas através de trocas de mensagens.
Correta.
