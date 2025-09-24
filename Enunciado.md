# Prova Presencial — Java Básico (Console)
## Aplicativo TODO List

**Cenário:** Você deve implementar, em Java **básico** e **console**, uma lista de tarefas (TODO list) simples para uso local durante a sessão da prova, sem persistência em disco. O foco é domínio de estruturas básicas, controle de fluxo e interação via terminal.

---

## Objetivos de aprendizagem
- Usar classes simples para modelar dados.
- Manipular coleções em memória (ArrayList).
- Ler entradas do usuário com `Scanner` e validar entradas.
- Implementar um menu interativo com laço (`while`) e `switch`/`if`.
- Aplicar boas mensagens de feedback ao usuário.

---

## Requisitos mínimos (obrigatórios)
1. **Modelo de dados**
   - Criar a classe `Tarefa` **com campos (não usar getters/setters)**:
     - `public int id;`
     - `public String titulo;`
     - `public boolean concluida;`
   - **Construtor opcional** (pode usar apenas campos públicos para simplificar).
   - Métodos utilitários opcionais: `marcarConcluida()` e `desmarcarConcluida()`.
2. **Aplicação console**
   - Usar `ArrayList<Tarefa>` para armazenar as tarefas em memória.
   - **Menu em loop** com as operações:
     1. Adicionar tarefa
     2. Listar tarefas
     3. Marcar tarefa como concluída
     4. Desmarcar tarefa
     5. Remover tarefa
     6. Sair
   - **IDs** devem ser gerados incrementalmente (ex.: `int proximoId = 1;` e incrementar a cada nova tarefa).
   - **Listagem** deve mostrar status `[X]`/`[ ]`, `id` e `titulo`.
   - **Validações** mínimas:
     - Não aceitar título vazio ou apenas espaços.
     - Ao operar por `id`, avisar se o `id` não existir.
   - **Restrições:**
     - Console puro (`System.out/Scanner`), **sem** bibliotecas externas.
     - **Sem** persistência (não salvar em arquivo ou banco).
     - Sem uso de frameworks; **Java básico**.
3. **Interação com o usuário**
   - Exibir mensagens claras (sucesso/erro) após cada operação.
   - Proteger o programa contra entradas inválidas (ex.: `id` não numérico).

---

## Exemplo de interface (somente para visualização)
```
===== TODO LIST =====
1) Adicionar tarefa
2) Listar tarefas
3) Marcar tarefa como concluída
4) Desmarcar tarefa
5) Remover tarefa
6) Sair
Escolha uma opção: 2

[ ] 1 - Comprar pão
[X] 2 - Estudar Java
```
> Observação: O exemplo é **ilustrativo**. A implementação e a formatação podem variar, desde que atendam os requisitos.

---

## Entregáveis
- Arquivos **`.java`**:
  - `Tarefa.java`
  - `Main.java` (ou outro nome de classe com `public static void main(String[] args)`)
- O código deve **compilar** e **executar** via terminal.

---

## Critérios de avaliação (rubrica)
| Critério | Descrição | Pontos            |
|---|---|-------------------|
| Modelo de dados | Classe `Tarefa` com campos corretos. | 2,0               |
| Estrutura de métodos | Implementação dos 8 métodos obrigatórios em `Main.java` conforme especificado. | 3,0               |
| Menu e fluxo | Laço principal, leitura com `Scanner`, tratamento de opção inválida. | 2,0               |
| Operações CRUD | Adicionar, listar, marcar/desmarcar, remover funcionando corretamente. | 2,0               |
| Validações básicas | Título não vazio, `id` inexistente, feedback claro ao usuário. | 1,0               |
| Validações avançadas | Tratamento robusto de erros, confirmações, mensagens detalhadas. | 2,0 (Bônus)       |
| Organização e clareza | Nomes de variáveis, mensagens e estrutura do código. | 1,0 (Bônus)       |
| **Total** |  | **10,0** + 03,0 de Bônus |

---

## Desafios (bônus até +2,0)
- **(+)** Editar título de uma tarefa pelo `id` (validando título).
- **(+)** Listar tarefas com filtros: somente concluídas / somente pendentes.
- **(+)** Ordenar listagem (ex.: pendentes primeiro).
- **(+)** Confirmar remoção (pedir `S/N`).

> Bônus só contam se os requisitos mínimos estiverem corretos.

---

## Estrutura de métodos obrigatória em Main.java
**IMPORTANTE:** Você deve implementar os seguintes métodos na classe `Main`:

### Métodos obrigatórios:
1. **`public static void main(String[] args)`**
   - Ponto de entrada da aplicação
   - Inicializar variáveis globais (`ArrayList<Tarefa>`, `Scanner`, `proximoId`)
   - Implementar o loop principal do menu

2. **`public static void exibirMenu()`**
   - Exibir as opções do menu numeradas de 1 a 6

3. **`public static void adicionarTarefa()`**
   - Ler título do usuário
   - Validar entrada (não vazio, não apenas espaços)
   - Criar nova tarefa com ID incremental
   - Adicionar à lista
   - Exibir mensagem de sucesso

4. **`public static void listarTarefas()`**
   - Percorrer a lista de tarefas
   - Exibir cada tarefa no formato: `[X]/[ ] id - titulo`
   - Tratar caso de lista vazia

5. **`public static void marcarTarefaConcluida()`**
   - Ler ID do usuário
   - Buscar tarefa na lista pelo ID
   - Marcar como concluída (`concluida = true`)
   - Exibir mensagem de sucesso/erro

6. **`public static void desmarcarTarefa()`**
   - Ler ID do usuário
   - Buscar tarefa na lista pelo ID
   - Desmarcar (`concluida = false`)
   - Exibir mensagem de sucesso/erro

7. **`public static void removerTarefa()`**
   - Ler ID do usuário
   - Buscar e remover tarefa da lista pelo ID
   - Exibir mensagem de sucesso/erro

8. **`public static Tarefa buscarTarefaPorId(int id)`**
   - Percorrer a lista procurando pela tarefa com o ID especificado
   - Retornar a tarefa encontrada ou `null` se não encontrar

### Variáveis globais necessárias:
```java
private static ArrayList<Tarefa> tarefas = new ArrayList<>();
private static Scanner scanner = new Scanner(System.in);
private static int proximoId = 1;
```

## Roteiro sugerido (passo a passo)
1. Criar `Tarefa.java` com os **campos** obrigatórios.
2. Em `Main.java`, declarar as **variáveis globais** e os **métodos** listados acima.
3. Implementar o método **`main()`** com o menu dentro de um `while (true)` e `switch`.
4. Implementar **`adicionarTarefa()`**:
   - Usar `scanner.nextLine()` para ler título
   - Validar com `trim()` e verificar se não está vazio
   - Criar `Tarefa` com `proximoId++` e adicionar na lista
5. Implementar **`listarTarefas()`**:
   - Verificar se lista está vazia primeiro
   - Usar loop `for` para percorrer e exibir todas as tarefas
6. Implementar **`buscarTarefaPorId()`**:
   - Usar loop `for` ou `enhanced for` para percorrer a lista
   - Comparar `tarefa.id == id` e retornar a tarefa encontrada
7. Implementar **`marcarTarefaConcluida()`** e **`desmarcarTarefa()`**:
   - Usar `buscarTarefaPorId()` para localizar a tarefa
   - Alterar o campo `concluida` e exibir mensagem apropriada
8. Implementar **`removerTarefa()`**:
   - Usar `buscarTarefaPorId()` para localizar
   - Usar `lista.remove(tarefa)` para remover e exibir mensagem
---

## Dicas e erros comuns
- **`Scanner` e `nextLine()`**: quando misturar `nextInt()` e `nextLine()`, consuma a quebra de linha pendente com um `nextLine()` extra.
- **Busca por `id`**: percorra a lista e compare `t.id == desejado`.
- **Mensagem após operação**: sempre informe o resultado ao usuário.
- **Formatação**: um método utilitário que monta a string de exibição ajuda a manter padrão.

---

## Como compilar e executar (terminal)
```bash
javac Tarefa.java Main.java
java Main
```

> Garanta que os arquivos `.java` estejam na **mesma pasta** (sem `package`) para simplificar a prova.

---

### Checklist rápido antes de entregar
- [ ] Compila sem erros (`javac`).
- [ ] Menu e todas as opções funcionam.
- [ ] Mensagens claras e validações aplicadas.
- [ ] Código organizado e legível.

Boa prova! :)
