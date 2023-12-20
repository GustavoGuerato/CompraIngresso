# Sistema de Venda de Ingressos

## Visão Geral
Este script em Python simula um sistema simples de venda de ingressos usando threads e locks para gerenciar o inventário de ingressos de forma concorrente.

## Estrutura do Código
### Classe Ingressos
- `__init__(self, estoque)`: Inicializa a classe Ingressos com um inventário de ingressos dado (`estoque`) e um lock (`self.lock`) para garantir a segurança entre threads.
- `comprar(self, quantidade)`: Representa a operação de compra de ingressos. Adquire o lock, verifica se há ingressos suficientes em estoque, simula um atraso de um segundo (representando um processo de compra), atualiza o inventário de ingressos e libera o lock.

### Script Principal
- **Inicialização:**
    - Cria uma instância da classe Ingressos com um inventário inicial de 135 ingressos.
    - Inicializa um array (`threads`) para armazenar objetos de thread.

- **Criação de Threads:**
    - Cria várias threads, cada uma representando uma possível compra de ingressos. A função `target` para cada thread é definida como o método `comprar` da classe Ingressos, e o argumento passado é a quantidade de ingressos a serem comprados.

- **Execução de Threads:**
    - Inicia cada thread para executar a operação de compra de ingressos de forma concorrente.

- **Monitoramento de Threads:**
    - Utiliza um loop while para verificar se alguma thread ainda está ativa. Se pelo menos uma thread estiver ativa, o loop continua. Isso garante que o script principal não saia antes que todas as threads concluam a execução.

- **Verificação Final do Inventário:**
    - Imprime o inventário de ingressos restantes após todas as threads terem sido concluídas.

## Segurança entre Threads
O script utiliza um lock (`self.lock`) dentro da classe `Ingressos` para garantir que a seção crítica (compra de ingressos e atualização do inventário) seja executada atomicamente. Isso evita condições de corrida e assegura a integridade do inventário de ingressos.

## Saída
O script exibe os detalhes da compra de ingressos para cada thread e o inventário final de ingressos restantes após a conclusão de todas as threads.

**Observação:**
Este script é uma simulação simplificada e pode não ser adequado para um cenário do mundo real. Em um ambiente de produção, uma solução mais robusta e escalável seria necessária, possivelmente envolvendo um banco de dados para armazenamento persistente e mecanismos avançados de controle de concorrência.
