# Parser de Arquivos XML do MS Project

Este repositório contém um script Python para extrair dados de arquivos XML exportados do Microsoft Project. O script lê o arquivo XML, converte os dados para um formato estruturado (DataFrame Pandas) e aplica transformações úteis, como a conversão de durações para dias úteis.
## Instalação

Para instalar as bibliotecas necessárias, execute o seguinte comando no seu terminal:

```bash
pip install xml.etree.ElementTree pandas
```


## Passos do Script

### Lendo o XML

O script carrega e analisa o arquivo XML exportado do MS Project usando a biblioteca `xml.etree.ElementTree`. Ele utiliza namespaces específicos para garantir que as tags sejam identificadas corretamente.

### Extraindo Colunas

O script itera pelas tarefas e atributos do arquivo XML e coleta as colunas presentes no arquivo, incluindo atributos estendidos. As colunas extraídas são armazenadas em um conjunto para evitar duplicações e organizadas hierarquicamente.

### Criando DataFrame

As informações XML extraídas são convertidas em um DataFrame Pandas, fornecendo uma estrutura de dados tabular. A exibição do DataFrame é configurada para mostrar todas as colunas e linhas, facilitando a visualização dos dados.

### Traduzindo Colunas

Um dicionário de tradução é usado para renomear as colunas do DataFrame de inglês para português, tornando os dados mais fáceis de ler.

### Convertendo Duração

O script inclui uma função para converter durações no formato "PTxHyMzS" (usado no MS Project) para dias úteis, assumindo uma jornada de trabalho de 8 horas. As colunas de duração e trabalho (por exemplo, "Duração", "Trabalho", "Trabalho Extra") são convertidas para dias úteis.

### Exibição e Análise

O script exibe as primeiras linhas do DataFrame com os dados extraídos e transformados. O usuário pode aprofundar-se nos dados e realizar análises adicionais usando ferramentas Pandas.

## Como Usar

1. Substitua o caminho do arquivo XML na variável `xml_file` pelo caminho do seu arquivo XML exportado do MS Project.
2. Execute o script e os dados serão carregados, extraídos e convertidos.
3. Explore as variáveis `df` e `df_dias` para analisar os dados extraídos e convertidos.


## Exemplo de Uso (Ilustrativo):

```python
# ... (Importar as bibliotecas e funções necessárias)

# Substitua pelo caminho do seu arquivo XML
xml_file = "seu_projeto.xml"

# ... (Código para ler, analisar e transformar os dados XML)

# Exibir as primeiras 5 linhas do DataFrame
print(df.head())

# Exibir as primeiras 5 linhas do DataFrame com durações convertidas
print(df_dias.head())
```

## Desenvolvimento Futuro

* Implementar tratamento de erros para arquivos XML inválidos ou dados ausentes.
* Adicionar lógica de conversão de duração mais sofisticada (por exemplo, considerando diferentes horários de trabalho).
* Criar visualizações interativas usando Plotly para explorar os dados.

