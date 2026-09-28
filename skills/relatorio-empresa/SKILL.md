---
name: relatorio-empresa
description: Ficha completa de uma empresa brasileira pelo Agentti (cadastro da Receita, contatos com prova, porte, rede, localização, sugestão de abordagem e riscos). Use quando a pessoa pede para contar sobre uma empresa, preparar uma visita ou ligação, analisar um CNPJ ou lead, ou quer a ficha em Word ou PDF.
argument-hint: "<CNPJ ou nome do lead>"
---

# Relatório de empresa

Pedido recebido pelo comando (pode vir vazio): $ARGUMENTS

## Achar a empresa

1. Com o id do lead ou o CNPJ: `ver_lead`. Passe o CNPJ **só com os 14 dígitos**, sem ponto, barra ou traço.
2. Se `ver_lead` não achar (a empresa não está salva na conta), procure com `buscar_empresas` pelo `nome`
   (e `cidade` + `uf`, se souber). Com o cadastro na mão, pergunte se a pessoa quer salvar num projeto
   (`salvar_no_projeto`, gasta 1 de cota) e qualificar (`qualificar`) para ter os contatos com prova.
   Sem isso, a ficha sai só com o cadastro da Receita, e diga isso.
3. Só com o nome, sem cidade: pergunte a cidade antes de buscar.

## Seções

1. **Resumo** em três linhas: quem é, tamanho, se vale a abordagem e por qual canal.
2. **Cadastro** (Receita): razão social, nome fantasia, CNPJ, atividade, porte, matriz ou filial, abertura,
   tempo ativa, capital social declarado.
3. **Sócios:** só o primeiro nome de pessoa física e a quantidade. Sócio pessoa jurídica pelo nome da empresa.
4. **Contatos com prova:** um por linha, com o selo (**confirmado** ou **provável**) e de onde veio. O que não foi
   achado aparece como "não encontrado". E-mail da Receita marcado "cadastro da Receita (pode ser do contador)".
5. **Porte e rede:** unidades ativas, matriz, o que isso sugere sobre quem decide a compra.
6. **Onde fica:** endereço, bairro, cidade. Distância, se veio de uma busca por raio.
7. **ICP:** score e classificação (hot ≥ 60, warm ≥ 30), com o detalhe que a ficha trouxer.
8. **Sugestão de abordagem:** canal, gancho e pedido, seguindo a skill **abordagem**. Um rascunho curto.
9. **Riscos e lacunas:** o que falta provar, empresa nova, só fixo, e-mail do contador, sem site.
10. **Sobre os dados** (só no arquivo): ver a skill **marca-agentti**.

## Formato

- **Na conversa:** texto com as seções acima, sem a 10.
- **Como arquivo** (quando a pessoa pedir Word, PDF, "arquivo" ou "para imprimir"): Word (.docx) e PDF do mesmo
  conteúdo, seguindo a skill **marca-agentti** e usando as skills de Word e PDF do Claude. Nome do arquivo:
  `Agentti - Ficha - <nome fantasia> - <AAAA-MM-DD>`.

## Regras

- Tudo da ficha sai de `ver_lead` ou `buscar_empresas`. O que não veio de lá não entra, nem como suposição.
- Não pesquise a empresa em outros sites para completar a ficha: o Agentti já faz a busca na web com prova,
  pela qualificação.
- Diga a origem de cada bloco: "cadastro da Receita", "qualificação do Agentti em <data>".
