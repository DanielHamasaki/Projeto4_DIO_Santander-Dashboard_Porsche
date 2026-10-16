# 🏎️ Dashboard de Vendas da Porsche

Projeto desenvolvido com base no desafio **“Criando um Dashboard da Porsche com Agentes de IA”**, do curso **Santander — Excel com IA e Claude**, na plataforma DIO.

O objetivo é organizar e visualizar dados comerciais da divisão norte-americana da Porsche, apoiando a análise de performance de vendas através de um dashboard interativo focado em modelos, regiões e tendências temporais.

## 🔗 Acesso ao Projeto

**Dashboard Publicada:** https://danielhamasaki.github.io/Projeto4_DIO_Santander-Dashboard_Porsche/

## 💡 Perguntas de Negócio e KPIs Escolhidos

A estruturação deste dashboard foi guiada por perguntas de negócio focadas em unir volume de vendas, tendências e impacto financeiro:

1. **Quais os principais modelos de carro vendidos por cidade?**
   * *Por quê:* Permite entender preferências regionais, otimizar a distribuição de estoque de concessionárias específicas e direcionar campanhas de marketing locais.
2. **Qual o ano de modelo de carro mais saiu em um período?**
   * *Por quê:* Ajuda a analisar o ciclo de vida dos produtos, o giro de estoque de modelos anteriores (ex: 2022 vs 2024) e a adoção de novas frotas pelos clientes.
3. **Quais modelos geram maior faturamento e qual o preço médio de venda por modelo?**
   * *Por quê:* Volume não significa necessariamente lucro. Estas KPIs financeiras foram adicionadas para identificar quais veículos trazem maior retorno financeiro para a divisão (ex: o 911 Turbo S e o 911 GT3 RS) e entender o poder de compra e ticket médio dos clientes.
4. **Insights de carros populares (Best Sellers) por região:**
   * *Por quê:* Destaca rapidamente os "campeões de vendas" nos 3 maiores mercados, fornecendo uma visão executiva imediata sem precisar analisar gráficos complexos.
5. **Evolução Temporal: Ano de Modelo por Período**
   * *Por quê:* Através de um gráfico de linhas evolutivo, este KPI permite visualizar as flutuações das vendas de cada ano-modelo ao longo dos meses, revelando sazonalidades, declínio de modelos mais antigos e o pico de adoção de lançamentos.

## 🤖 Evolução do Prompt e IA

O projeto foi construído iterativamente. 

**Prompt Inicial:**
> *"Utilizando o recurso de canvas, renderize uma dashboard em html ao lado. Filtros: Modelo da porsche, Model Year, City, Pay method. Perguntas de negócios e kpis: Quais os principais modelos de carro vendido por cidade, Qual o ano de modelo de carro mais saiu em um período, Quero insight de carros populares de vendas com base nos dados em cada cidade. Sobre ui/ux, se baseie no site oficial da porsche brasil: porsche.com/brazil/pt. Tenha um ar elegante e refinado."*

**Evolução até a versão final:**
1. **Identidade Visual:** O prompt inicial focou na UI/UX da Porsche. O resultado foi um Dark Theme com tons de preto, cinza e vermelho. Chegamos a testar um layout claro estilo *Power BI*, mas optamos por retornar ao visual "Premium Porsche" com gradientes vermelhos.
2. **Imagens:** Foram feitos refinamentos no prompt para utilizar URLs exatas de imagens oficiais da Porsche (`.avif`), exigindo ajustes de CSS (`object-cover`) para enquadramento perfeito nos cards de insights.
3. **Gráficos:** Mudamos o gráfico de "Modelos por cidade" para barras horizontais para melhor legibilidade. Substituímos temporariamente o gráfico evolutivo por "Vendas por Estado" e, em seguida, unimos os dois.
4. **Novas KPIs:** Em prompts subsequentes, solicitamos a inclusão dos gráficos de "Faturamento por Modelo" e "Preço Médio", padronizando a cor deles para vermelho para manter a harmonia visual.

**Ferramentas de IA Utilizadas:**
Neste projeto, utilizamos **os dois modelos em conjunto**: 
- Um **Agente com Skill de Análise de Dados (Python Interpreter)** para ler ativamente o arquivo `porsche_database_apenas_tratado.xlsx`, extrair a lista exata de cidades, estados, modelos e métodos de pagamento.
- Uma interface de **edição visual (estilo Canvas/Artifacts)** acoplada a um LLM avançado para gerar e iterar o código HTML/JS/Tailwind lado a lado em tempo real.

## 📊 A Origem dos Dados: Foco em Excel (.xlsx)

Como o curso base possui um forte foco em **Excel**, todo o ponto de partida deste projeto e as análises geradas derivam de uma planilha de dados real. 

A base utilizada foi o arquivo `porsche_database_tratado.xlsx`. A lógica de funcionamento da interface em HTML/JS foi totalmente moldada para refletir e consumir a estrutura de linhas e colunas oriunda dessa planilha (simulando a leitura no front-end para fins de demonstração web).

## 🧹 Tratamento da Base de Dados

Antes de alimentar a inteligência artificial para a criação do dashboard, o arquivo Excel passou por higienização e tratamento:
- **Sanitização de Colunas:** Padronização de nomes de colunas (ex: `SaleDateSanitized`, `PorscheModelSanitized`, `SalesPriceSanitized`).
- **Tratamento Geográfico:** Identificou-se que não havia cidades brasileiras na base real, apenas dados dos EUA. A IA precisou mapear as cidades (ex: Boston, Seattle) para seus respectivos estados (MA, WA) para viabilizar a visão estadual.
- **Limpeza de Valores:** Tratamento de datas inválidas, remoção de duplicatas de nomenclaturas de modelos e garantia de que os valores de preços e quilometragem fossem numéricos válidos.

## 📂 Estrutura da Interface

O projeto consiste em um arquivo HTML contendo:

- **Sidebar de Filtros** — Menu lateral para segmentação interativa dos dados por Modelo, Ano, Cidade e Método de Pagamento.
- **Visão Executiva (Hero Banner)** — Cabeçalho de impacto visual com imagem de fundo e KPIs de Total Entregue e Faturamento (USD).
- **Highlights de Vendas** — Cards dinâmicos que exibem as três cidades com maior volume de vendas e seus respectivos modelos "Best Sellers".
- **Área de Gráficos** — Seção principal com cinco painéis analíticos utilizando Chart.js.

## 🧰 Recursos e Tecnologias

O dashboard web foi construído sem dependências locais complexas, utilizando recursos modernos consumidos via CDN:

- **HTML5 e CSS3**
- **Tailwind CSS** (Tema escuro customizado: `#d5001c`, `#121212`, etc.)
- **Chart.js** (Gráficos interativos)
- **JavaScript (Vanilla)** (Manipulação do DOM e filtros reativos)
- **Google Fonts** (Inter)

---
**Observação:** Projeto educacional para prática de análise e visualização de dados com IA. Os resultados refletem os dados do dataset disponibilizado no curso.