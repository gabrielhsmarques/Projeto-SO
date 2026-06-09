# Projeto xv6 - Tema 10: Syscall getmem() e Escalonador MLQ
**Disciplina:** GBC045 - Sistemas Operacionais  
**Universidade:** Universidade Federal de Uberlândia (UFU)  
**Curso:** Bacharelado em Ciência da Computação  

---

## Integrantes do Grupo
* Davi Santos Oliveira - 12411BCC088
* Gabriel Henrique Silva Marques - 12411BCC057
* Gustavo Pereira Mendes - 12221BCC007
* Pedro Lucas Oliveira Borges - 12311BSI261
* Tiarlisson Silva Gontijo - 12111BSI270

---

## Descrição do Projeto (Tema 10)
Este projeto consiste na modificação do kernel do sistema operacional **xv6** para a implementação de duas funcionalidades principais:

1.  **System Call `getmem()`**: Uma chamada de sistema que permite a um processo consultar o tamanho atual da memória alocada para ele (em bytes).
2.  **Escalonador Multi-Level Queue (MLQ)**: Implementação de um algoritmo de escalonamento que utiliza múltiplas filas de prioridade, visando otimizar a distribuição de tempo de CPU entre processos interativos e processos de cálculo intenso.

---

## Descrição das Etapas 

### ETAPA 1: Fundamentação
Nesta etapa inicial, o grupo realizou o levantamento teórico e o planejamento técnico da solução. Os seguintes materiais foram produzidos:
*   **Slides de Apresentação:** Detalhando a lógica da syscall e do algoritmo de escalonamento.
*   **Vídeo Explicativo:** Apresentação técnica com a participação de todos os membros, abordando a motivação, o funcionamento do MLQ e a estratégia de implementação no xv6.
*   **Proposta de Implementação:** Planejamento dos arquivos do kernel que sofrerão modificações.

### ETAPA 2: Plano de Implementação

### 1. Chamada de Sistema `getmem()`
Para implementar a `getmem()`, utilizaremos o campo `sz` da `struct proc`. Os arquivos modificados serão:
*   `kernel/syscall.h` e `kernel/syscall.c`: Registro da nova syscall.
*   `kernel/sysproc.c`: Implementação da lógica que acessa `myproc()->sz`.
*   `user/user.h` e `user/usys.pl`: Definição da interface para o espaço de usuário.

### 2. Escalonador Multi-Level Queue (MLQ)
A estratégia para o escalonador consiste em:
*   Adicionar um campo `priority` na estrutura do processo em `kernel/proc.h`.
*   Modificar a função `scheduler()` em `kernel/proc.c` para que ela percorra a tabela de processos buscando primeiro aqueles com maior prioridade (Fila 0) antes de atender a Fila 1.
*   Implementar uma lógica simples de feedback ou definição inicial de prioridade para observar o comportamento das filas.

