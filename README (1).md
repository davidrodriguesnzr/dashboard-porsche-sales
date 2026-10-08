# Porsche Sales Intelligence — Dashboard Interativo | DIO

Dashboard comercial construído em **HTML, CSS e JavaScript nativos**, em um único arquivo `index.html`, a partir de **100 registros sanitizados** fornecidos no desafio **Criando Agentes de Tratamento de Dados** (DIO). Funciona localmente, sem instalação, servidor ou dependências externas, e pode ser publicado no GitHub Pages.

## Perguntas de negócio

1. **Quais modelos da Porsche geram mais receita?** Ranking com barras horizontais, por receita somada.
2. **Quais cidades concentram mais receita?** Ranking das cinco cidades com maior faturamento.
3. **Quais meios de pagamento são mais utilizados?** Gráfico circular com participações por quantidade de vendas.

**Análise complementar:** como a receita se distribui ao longo dos meses com datas válidas? Série temporal por mês da venda.

## Indicadores

- 100 vendas registradas;
- Receita total de **US$ 12.827.800,50** (soma do preço de venda sanitizado);
- 41 registros com status `Delivered`;
- 24 registros com data sanitizada inválida (`INVALID`).

O período de vendas não deve ser inferido a partir do ano do modelo do veículo. Os indicadores são recalculados conforme os filtros.

## Como executar

1. Baixe o arquivo `index.html`.
2. Abra-o no navegador (Chrome, Edge ou Firefox). Não há instalações ou servidor.
3. Altere os filtros de **modelo, estado, ano do modelo, pagamento e status de entrega**.
4. Consulte os indicadores e gráficos atualizados e use **Exportar CSV filtrado** para obter o recorte.
5. Clique em **Limpar filtros** para retornar à base completa.

## Tratamento dos dados

A planilha original da DIO contém pares de colunas: informações cruas e versões sanitizadas. Foram usadas as versões sanitizadas: `SaleDateSanitized`, `PorscheModelSanitized`, `ModelYearSanitized`, `SalesPriceSanitized`, `VehicleMileageSanitized`, `PayMethodSanitized`, `CitySanitized`, `StateSanitized` e `DeliveryStatusSanitized`, além do identificador `sale_id`.

- Os campos `SalesPriceSanitized`, `ModelYearSanitized` e `VehicleMileageSanitized` foram convertidos para tipos numéricos.
- O campo `SaleDateSanitized` foi validado como data ISO `AAAA-MM-DD`.
- **24 datas inválidas permaneceram ausentes**, sem adivinhação ou substituição arbitrária. Os respectivos registros continuam nos KPIs e gráficos não temporais.
- Informações pessoais de clientes e vendedores foram **excluídas** do conjunto embutido por não serem necessárias às perguntas de negócio.
- O conjunto tratado está embutido no `index.html`, que independe de consultas a servidores ou APIs.

O arquivo opcional `base_sanitizada_porsche.json` oferece os mesmos campos tratados para fins de auditoria e reprodução.

## Processo de criação / prompt

Ferramenta utilizada: **ChatGPT para análise e geração de código HTML/JavaScript**, não Canvas nem agente com skill específica. O arquivo foi implementado como HTML único.

### Prompt orientador

> Usando apenas as 100 vendas sanitizadas da planilha Porsche, crie uma dashboard responsiva em HTML único, sem dependências, que responda: (1) quais modelos geram mais receita, (2) quais cidades concentram mais faturamento e (3) quais formas de pagamento são preferidas. Inclua KPIs, filtros por modelo, estado, ano, pagamento e status, evolução mensal, exportação de CSV e visual escuro inspirado em dashboards automotivos. Não invente datas e evite incluir informações pessoais desnecessárias.

### Refinamentos incorporados

- Uso exclusivo das colunas sanitizadas com coerção de tipos;
- Tratamento explícito de datas inválidas, sem falsa correção;
- Indicadores reativos a todos os filtros e estado vazio;
- Exclusão de nomes de clientes/vendedores da publicação;
- Dashboard independente de bibliotecas externas e capaz de funcionar diretamente no GitHub Pages.

## Estrutura

```text
porsche-sales-dashboard/
├── index.html
├── README.md
└── base_sanitizada_porsche.json
```

## Como publicar no GitHub Pages

1. Crie um **repositório público** (sugestão: `dashboard-porsche-sales`) na sua conta GitHub.
2. Faça upload de `index.html`, `README.md` e, opcionalmente, `base_sanitizada_porsche.json` na raiz do repositório, e confirme o commit.
3. Abra **Settings → Pages → Build and deployment**.
4. Em **Source**, selecione **Deploy from a branch**; em **Branch**, escolha `main` e `/ (root)` e clique **Save**.
5. Aguarde a publicação e abra o endereço apresentado no GitHub Pages.
6. Teste os filtros e registre capturas de tela da visão inicial e de um filtro aplicado.

**URL a verificar após a publicação:** `https://davidrodriguesnzr.github.io/dashboard-porsche-sales/`.

**Link a entregar na DIO:** repositório público (não somente a URL do Pages): `https://github.com/davidrodriguesnzr/dashboard-porsche-sales`.

> Os endereços acima são esperados **após criação e publicação**, não confirmação de que o site já esteja disponível.

## Observações

Projeto educacional. Não é produto oficial, afiliado ou endossado pela Porsche. Os valores da planilha são interpretados em USD, conforme notações nos preços brutos. A análise é descritiva, não contábil.
