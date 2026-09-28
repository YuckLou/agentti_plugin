---
name: marca-agentti
description: Padrão visual dos documentos do Agentti (Word e PDF) - cores, fontes, cabeçalho com logo, rodapé com a origem dos dados, estilos nomeados e a seção "Sobre os dados". Use sempre que for gerar um relatório de empresa ou de região do Agentti como arquivo.
user-invocable: false
---

# Padrão dos documentos Agentti

A marca é **discreta**: logo pequeno no cabeçalho, origem dos dados no rodapé e uma seção final curta. Nada de
marca-d'água, capa de propaganda ou logo no meio do texto. O cliente tem de conseguir tirar a marca inteira
apagando o cabeçalho, o rodapé e a última seção.

## Arquivos

- **Word (.docx)** é o arquivo principal: abre no Word, no Google Docs e no LibreOffice.
- **PDF** sai do mesmo conteúdo, para enviar. Os dois têm de dizer a mesma coisa.

## Cores (tema claro)

| Uso | Cor |
| :--- | :--- |
| destaque: títulos, barras dos gráficos | laranja `#D84315` |
| cabeçalho de tabela (fundo), linhas de tabela | grafite `#263238` |
| texto | `#0F172A` |
| texto secundário, legendas, rodapé | `#475569` |
| fundo de destaque (caixas, linhas alternadas) | `#F1F5F9` |
| realce raro (um número-chave) | creme `#FFE082` |

Gráfico com mais de uma série: laranja, grafite e `#94A3B8`, nessa ordem.

## Fontes

Títulos em **Chakra Petch**, texto em **Inter**. No arquivo, declare a fonte com substituto comum (Arial), para
abrir igual numa máquina sem as fontes. Tamanhos: título 20, seção 14, texto 10,5, tabela 9, rodapé 8.

## Estilos nomeados (Word)

Crie e use estilos, nunca formatação solta, para que trocar uma cor mude o documento inteiro:
- `Título Agentti`, `Seção Agentti`, `Texto Agentti`, `Legenda Agentti`;
- `Tabela Agentti`: cabeçalho grafite com texto branco, linhas finas, linhas alternadas em `#F1F5F9`.

## Cabeçalho e rodapé

- **Cabeçalho:** o logo `assets/logo.png` desta skill, alinhado à esquerda, com no máximo **2,5 cm de largura**,
  e o título curto do documento à direita, em texto secundário.
- **Rodapé:** "Dados: base oficial da Receita Federal · análise Agentti · agentti.ia.br", a data de geração e o
  número da página.

## Seção final "Sobre os dados"

Use este texto, trocando o que está entre < >:

> **Sobre os dados.** Os números vêm da contagem completa dos estabelecimentos ativos na base oficial da Receita
> Federal, consultada pelo Agentti em <data>. A faixa A/B/C é uma pré-qualificação feita só com o cadastro
> (porte, tempo ativa, canal de contato e nome fantasia) e não indica se a empresa compra o produto. Contatos
> marcados como "confirmado" foram achados numa página que traz o endereço ou o telefone da Receita; "provável"
> indica sinais sem essa prova. Capital social é o declarado na abertura e não representa faturamento.
> Mais em agentti.ia.br.

No relatório de empresa sem qualificação, tire a frase dos contatos. No relatório de região sem contatos, também.

## Ferramentas para gerar o arquivo

Use o que já existe no ambiente (as skills de Word e PDF do Claude e as bibliotecas instaladas). No computador
da pessoa (Claude Code), **pergunte antes** de instalar pacote ou baixar fonte; se ela não quiser, use o que
houver e declare as fontes da marca com o substituto Arial. No ambiente isolado do Claude (web, Desktop, Cowork),
instalar o que faltar é normal.

## Gráficos

Imagem PNG com a tabela de números ao lado ou abaixo. Fundo branco, sem borda, sem 3D, rótulos em texto
secundário, eixo sem grade pesada.
