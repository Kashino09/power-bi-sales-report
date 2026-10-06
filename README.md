# 📊 Desafio Power BI — Relatório Financeiro com Foco na Experiência do Usuário

## 📑 Índice
- Contexto
- Objetivos
- Fontes
- Estrutura do Relatório
- Decisões de Experiência do Usuário
- Paleta de Cores
- Colunas Criadas
- Principais Resultados
- Arquivos
- Autor

# Contexto:
- Este projeto é a entrega do desafio "Atualizando Relatório Financeiro com Foco na Experiência do Usuário", da trilha de Analista de Dados da [DIO](https://www.dio.me/). A partir de um template de 3 páginas e da tabela `financials` (base Financial Sample), o relatório foi reconstruído com atenção à navegação, à hierarquia visual, ao contraste e à segmentação das informações.

# Objetivos:
- Aplicar princípios de experiência do usuário (UX) em um relatório de Power BI;
- Criar navegação clara entre as páginas, com botões, menu e retorno à Home;
- Organizar a leitura com hierarquia visual, agrupamento por contexto e cores com função definida;
- Alternar visões do mesmo dado (por exemplo, semestres e meses) sem poluir a página;
- Detalhar as vendas por semestre, trimestre, produto e distribuição de unidades vendidas.

# Fontes:
- Tabela `financials` (Financial Sample), fornecida no desafio, com vendas entre 01/09/2013 e 01/12/2014;
- Template de 3 páginas fornecido pela DIO (Home, Relatório e Página 1);
- Conteúdo de referência: módulos do curso de Power BI Analyst da DIO.

# Estrutura do Relatório

**Página 1 — Home**
- Capa "Report Financeiro" com o botão **Explorar análise**, que leva ao relatório.

**Página 2 — Relatório de Vendas**
- Segmentador de data (01/09/2013 a 01/12/2014);
- Cartões: Total de Vendas, Unidades Vendidas, Descontos Totais, Total de Lucro e Custo de Mercadoria (COGS);
- Área: vendas por mês;
- Vendas por Segmento, com botões para alternar entre barras e pizza (rosca);
- Vendas por Produto (barras);
- Vendas por País, com botões para alternar entre treemap e mapa;
- Menu de navegação.

**Página 3 — Detalhes de Vendas**
- Vendas por Semestre (colunas empilhadas por ano), com botões para alternar entre **Semestres** e **Meses**;
- Matriz de Trimestre por Ano, com totais;
- Histograma de Unidades Vendidas (faixas de unidades por venda);
- Vendidos por Produto (barras);
- Botão Home e menu de navegação.

# Decisões de Experiência do Usuário
- **Navegação:** botão de entrada na capa, menu em todas as páginas e atalho para a Home, para o usuário nunca ficar sem saída;
- **Hierarquia:** o título e os indicadores principais ficam no topo, em um cartão claro que contrasta com o fundo; os detalhes vêm abaixo;
- **Segmentação:** visuais relacionados agrupados em painéis, com títulos curtos e consistentes;
- **Alternância de visões:** botões com indicadores (bookmarks) trocam um visual por outro no mesmo espaço, em vez de multiplicar gráficos na página;
- **Contraste:** textos e gráficos claros sobre o fundo roxo-escuro, evitando tons escuros sobre fundo escuro;
- **Cor com função:** uma cor para os dados, outra para o destaque e outra só para ações (veja abaixo);
- **Rótulos de dados** nos gráficos, para o usuário ler o valor sem passar o mouse.

# Paleta de Cores

| Função | Cor | Uso |
|---|---|---|
| Dado padrão | `#EBDDF7` (lilás claro) | barras e séries comuns |
| Destaque | `#FFC857` (âmbar) | maior valor, comparação entre anos, picos |
| Degradê | `#F3E2FF` → `#FFC857` | treemap, histograma e produtos por valor |
| Ação | `#B8527A` (rosa) | botões, ícone Home e estado selecionado |
| Texto | `#FFFFFF` / `#2A1050` | texto sobre fundo escuro / sobre cores claras |

# Colunas Criadas
Na tabela `financials`, uma coluna calculada para o semestre, já que a hierarquia de datas do Power BI traz Ano, Trimestre, Mês e Dia, mas não o semestre:

```DAX
Semestre = IF(MONTH(financials[Date]) <= 6, "1º Semestre", "2º Semestre")
```

Também foi criado o grupo de compartimentos (bins) sobre `Units Sold`, usado no eixo do histograma.

# Principais Resultados
- Total de vendas no período: **118,73 Mi**, com lucro de **16,89 Mi** e COGS de **101,83 Mi**;
- **Paseo** é o produto mais vendido (33 Mi) e **Government** o segmento de maior receita (53 Mi);
- Os **Estados Unidos** lideram as vendas por país (25,03 Mi), seguidos de Canadá (24,89 Mi) e França (24,35 Mi);
- O **2º semestre** concentra a maior parte das vendas, e o **4º trimestre** é o mais forte (51,69 Mi somando os dois anos);
- Os dados começam em setembro de 2013, então 2013 aparece só no 2º semestre.

# Arquivos

| Arquivo | Descrição |
|---|---|
| `Sales_Report_-_UX.pbix` | Projeto completo do Power BI Desktop, com as 3 páginas |
| `Sales_Report_-_UX.pdf` | Exportação em PDF das 3 páginas do relatório |
| `Sales_Report_-_UX.pptx` | Apresentação com as 3 páginas do relatório (um slide por página) |

# Autor
- Kelwin Paschoal
