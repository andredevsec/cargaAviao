# Algoritmo Genético para Otimização de Carga em Avião

## Estrutura Principal

### Pacotes e Importações

O código está organizado em pacotes e importa várias classes do Java para manipulação de arquivos, listas e geração de números aleatórios.

### Classes

- **AlgoritmoGenetico**: A classe principal que implementa o algoritmo genético.
- **Carga**: Representa uma carga individual com suas propriedades (descrição, massa, dimensões).
- **Main**: Define constantes para as restrições do avião e os parâmetros do algoritmo, além de conter o método `main`.

## AlgoritmoGenetico

### Atributos

- `cargas`: Lista de objetos `Carga` representando as cargas disponíveis.
- `tamanhoCromossomo`: Número de cargas.
- `populacao`: Lista de cromossomos, onde cada cromossomo é uma lista de inteiros representando a seleção (1) ou não seleção (0) de uma carga.
- `roletaVirtual`: Lista usada para o método de seleção por roleta.

### Métodos

#### `executar(String nomeArquivo)`

- Carrega o arquivo de dados de cargas.
- Cria a população inicial.
- Executa o loop de gerações, aplicando operadores genéticos (seleção, cruzamento, mutação) e renovando a população.
- Exibe a melhor solução encontrada.

#### `carregarArquivo(String nomeArquivo)`

- Lê o arquivo CSV contendo os dados das cargas e cria objetos `Carga`.

#### `criarCarga(String[] dadosCarga)`

- Cria um objeto `Carga` a partir de um array de strings.

#### `adicionarCarga(Carga novaCarga)`

- Adiciona uma carga à lista de cargas e incrementa o tamanho do cromossomo.

#### `criarPopulacao()`

- Inicializa a população com cromossomos gerados aleatoriamente.

#### `criarCromossomo()`

- Cria um cromossomo (lista de inteiros) aleatoriamente, com 0s e 1s.

#### `mostrarPopulacao()`

- Exibe a população atual e a avaliação de cada cromossomo.

#### `fitness(List<Integer> cromossomo)`

- Avalia a "aptidão" de um cromossomo baseado na soma do volume das cargas selecionadas, respeitando as restrições de massa e dimensões.

#### `operadoresGeneticos()`

- Aplica os operadores de cruzamento e mutação para gerar novos cromossomos e os adiciona à população.

#### `gerarRoleta()`

- Cria uma roleta virtual para seleção de pais baseada na aptidão dos cromossomos.

#### `cruzamento()`

- Realiza o cruzamento entre dois pais para gerar dois filhos.

#### `roleta()`

- Seleciona um cromossomo da população usando a roleta virtual.

#### `mutacao(List<Integer> filho)`

- Aplica a mutação em um cromossomo com uma probabilidade definida.

#### `renovarPopulacao()`

- Remove os piores cromossomos da população, mantendo o tamanho constante.

#### `obterPior()`

- Retorna o índice do pior cromossomo na população.

#### `mostrarCargaAviao(List<Integer> resultado)`

- Exibe as cargas selecionadas no melhor cromossomo.

#### `obterMelhor()`

- Retorna o índice do melhor cromossomo na população.

## Carga

### Atributos e Métodos

- Representa as propriedades de uma carga (descrição, massa, largura, altura, profundidade).
- Método `calcularVolume()` calcula o volume da carga.
- Método `toString()` para exibir as propriedades da carga.

## Main

### Constantes

Define as restrições do problema, como capacidade de carga, dimensões máximas, tamanho da população, probabilidade de mutação, quantidade de cruzamentos e número de gerações.

### Método `main`

- Verifica a validade das constantes.
- Instancia e executa o algoritmo genético.

### Método `volumeMaximo()`

- Calcula o volume máximo permitido baseado nas dimensões máximas.

## Fluxo do Algoritmo

1. Carrega os dados das cargas do arquivo.
2. Inicializa a população de cromossomos.
3. Para cada geração, realiza as seguintes etapas:
   - Avalia a aptidão de cada cromossomo.
   - Seleciona cromossomos para cruzamento e gera novos filhos.
   - Aplica mutação aos filhos.
   - Adiciona os filhos à população.
   - Remove os piores cromossomos para manter o tamanho da população constante.
4. Exibe a melhor solução encontrada ao final das gerações.

Este algoritmo genético tenta maximizar o volume de carga transportada no avião, respeitando as restrições de massa e dimensões de cada carga individual.
