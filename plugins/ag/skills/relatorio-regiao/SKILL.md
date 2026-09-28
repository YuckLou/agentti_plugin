---
name: relatorio-regiao
description: Relatório de mercado B2B por região em Word e PDF, com os números do Agentti (contagem completa da base da Receita Federal) - tamanho, porte, faixas, tempo ativa, canais, bairros, distância e recomendações, com gráficos e a marca Agentti. Use quando a pessoa pede um PDF, relatório, estudo ou análise de mercado de um ramo numa cidade, bairro ou raio. Para relatório de mercado com dados do Agentti, use esta skill antes da skill genérica de PDF ou Word.
argument-hint: "<ramos> em <cidade, bairro ou CEP>"
---

# Relatório de região

Pedido recebido pelo comando (pode vir vazio): $ARGUMENTS

## Coletar os números

1. Ramos → `buscar_atividade`. Confirme a lista de ramos com a pessoa antes de seguir.
2. Local → `perto_de` + `raio_km` ou `cidade` + `uf`.
3. `estatisticas_empresas` com ramos e local: é a base de todo o relatório.
4. Se ajudar a decisão, até três chamadas a mais:
   - por ramo, quando um ramo domina o total;
   - por bairro ou raio menor, para comparar partes da região;
   - com o recorte recomendado (ex.: `porte: "EPP"`, `faixa_minima: "A"`), para dar a contagem exata.
5. Opcional, se a pessoa quiser nomes: `buscar_empresas` com o recorte recomendado, `por_pagina: 10`. Entram só
   nome, bairro, porte e faixa. Sem contatos no relatório de região.

Leia os números como manda a skill **mercado** ([como ler](../mercado/references/como-ler.md)).

## Seções

1. **Resumo** (meia página): o tamanho do mercado, onde está, o perfil dominante e a recomendação em uma frase.
2. **Método:** ramos e códigos CNAE usados, local e raio, data da consulta, "contagem completa dos
   estabelecimentos ativos na base da Receita Federal".
3. **Tamanho:** total, empresas distintas, densidade por km² (se houver raio).
4. **Porte:** tabela e gráfico de barras. Explique o peso do MEI.
5. **Pré-qualificação:** faixas A/B/C e o cruzamento porte × faixa. Diga o que a faixa mede e o que não mede.
6. **Maturidade:** tempo ativa.
7. **Canais de contato:** celular, só fixo, sem telefone, e-mail na Receita (com a ressalva do contador).
8. **Onde estão:** bairros ou municípios (os 10 maiores) e a distância, com gráfico.
9. **Recomendações:** dois ou três recortes, cada um com contagem, motivo e próximo passo (lista, qualificação,
   visita).
10. **Sobre os dados:** texto fixo da skill **marca-agentti**.

## Gráficos

- Barras horizontais, cor de destaque da marca, rótulo com o número e o percentual.
- Cada gráfico com a **tabela de números ao lado ou logo abaixo**, para o cliente refazer no programa dele.
- Gere como imagem (PNG, 150 dpi ou mais) a partir dos números da estatística. Nunca desenhe número que não veio
  da ferramenta.

## Arquivo

Word (.docx) como arquivo principal e PDF do mesmo conteúdo, seguindo a skill **marca-agentti** (se ela não
carregar pelo nome, leia `../marca-agentti/SKILL.md`) e usando as skills de Word e PDF do Claude. Nome:
`Agentti - Mercado - <ramos resumidos> - <local> - <AAAA-MM-DD>`.

Antes de entregar, confira o mínimo, mesmo que a pessoa tenha pedido só "um PDF":
- [ ] **Word e PDF**, os dois;
- [ ] **gráficos** de porte, faixa e bairros (ou distância), cada um com a tabela de números;
- [ ] cores da marca: laranja `#D84315` nos títulos e barras, grafite `#263238` no cabeçalho das tabelas;
- [ ] logo `../marca-agentti/assets/logo.png` no cabeçalho (até 2,5 cm) e a origem dos dados no rodapé;
- [ ] seção final "Sobre os dados".

Depois de gerar, diga em três linhas o que o relatório conclui e entregue os dois arquivos.

## Regras

- Número só da ferramenta, exato no relatório. Percentuais com uma casa.
- Não transforme contagem em demanda nem capital em faturamento.
- Não invente o mês da base: "base da Receita Federal, atualizada mensalmente".
