# Algoritmo Genético em Python

Este repositório contém uma implementação de um algoritmo genético em Python, desenvolvido para resolver problemas de otimização combinatória.

## Visão Geral

O projeto consiste em dois arquivos principais:
- **final-genetic-algorithm.py**: Implementação completa do algoritmo genético
- **step-by-step.ipynb**: Notebook Jupyter com explicação passo a passo da implementação

O algoritmo foi desenvolvido para resolver um problema específico de otimização: maximizar o valor dos produtos transportados em um caminhão com espaço limitado.

## Problema de Exemplo

O algoritmo resolve um problema de transporte onde:
- Temos um caminhão com capacidade limitada (3m³)
- Precisamos escolher quais produtos transportar
- Cada produto possui um volume (em m³) e um valor (em R$)
- Precisamos maximizar o valor total transportado sem exceder a capacidade

## Estrutura do Algoritmo

O algoritmo genético implementado inclui:

1. **Classe Produto**: Representa um produto com nome, espaço (volume) e valor.
2. **Classe Individuo**: Representa uma solução candidata (cromossomo).
   - Possui métodos para avaliação (fitness), crossover e mutação.
3. **Classe AlgoritimoGenetico**: Implementa a lógica principal do algoritmo.
   - Gerencia a população de soluções
   - Implementa seleção de pais, crossover, mutação
   - Executa o algoritmo por múltiplas gerações

## Como Usar

### Executando o Algoritmo Completo

```python
# Importar o algoritmo
from final-genetic-algorithm import Produto, Individuo, AlgoritimoGenetico

# Criar lista de produtos
lista_produtos = []
lista_produtos.append(Produto('Produto A', 0.5, 1000.0))
lista_produtos.append(Produto('Produto B', 0.3, 800.0))
# ... adicionar mais produtos

# Preparar dados
espacos = [produto.espaco for produto in lista_produtos]
valores = [produto.valor for produto in lista_produtos]

# Configurar parâmetros
tamanho_populacao = 20
limite_espaco = 3  # m³
taxa_mutacao = 0.01
numero_geracoes = 100

# Executar algoritmo
ag = AlgoritimoGenetico(tamanho_populacao)
resultado = ag.resolver(taxa_mutacao, numero_geracoes, espacos, valores, limite_espaco)

# Exibir resultados
for i in range(len(lista_produtos)):
    if resultado[i] == '1':
        print(f'Nome: {lista_produtos[i].nome} R$ {lista_produtos[i].valor}')
```

### Parâmetros Importantes

- **tamanho_populacao**: Define quantos indivíduos terão na população
- **taxa_mutacao**: Probabilidade de ocorrer mutação em um gene
- **numero_geracoes**: Quantidade de gerações a serem executadas
- **limite_espaco**: Capacidade máxima disponível

## Aprendizado Passo a Passo

O notebook `step-by-step.ipynb` contém uma implementação detalhada e comentada do algoritmo, explicando cada etapa:

1. Definição do problema
2. Implementação das classes
3. Desenvolvimento do algoritmo genético
4. Visualização dos resultados

É recomendado explorar o notebook para entender melhor os conceitos e a implementação.

## Adaptando para Outros Problemas

O algoritmo pode ser adaptado para outros problemas de otimização combinatória:

1. Altere a classe `Produto` para representar os elementos do seu problema
2. Modifique a função de avaliação (`avaliacao`) para calcular o fitness específico
3. Ajuste os parâmetros (tamanho da população, taxa de mutação, etc.)
4. Execute o algoritmo conforme suas necessidades

## Conceitos de Algoritmos Genéticos

- **Cromossomo**: Representação binária de uma solução
- **População**: Conjunto de soluções candidatas
- **Seleção**: Processo de escolha dos melhores indivíduos
- **Crossover**: Recombinação de material genético entre indivíduos
- **Mutação**: Alteração aleatória nos genes
- **Fitness**: Avaliação da qualidade de uma solução