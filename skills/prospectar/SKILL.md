---
name: prospectar
description: Prospecção B2B no Brasil com o Agentti, sobre a base oficial da Receita Federal. Use quando a pessoa quer achar clientes, saber quais empresas compram o que ela vende, montar uma lista de leads numa cidade, bairro ou raio, ou pede algo como "quem compra X em Y" ou "monte uma lista de empresas".
argument-hint: "<o que você vende> em <cidade, bairro ou CEP>"
---

# Prospectar com o Agentti

Pedido recebido pelo comando (pode vir vazio): $ARGUMENTS

As ferramentas são as do conector **Agentti** (`buscar_atividade`, `estatisticas_empresas`, `buscar_empresas`,
`listar_projetos`, `criar_projeto`, `definir_oferta`, `salvar_no_projeto`, `qualificar`, `acompanhar_fila`,
`listar_leads`, `ver_lead`). Se elas não aparecerem, diga à pessoa para conectar o Agentti (README do plugin) e pare.

## Passo a passo

1. **Entenda a oferta.** O que a pessoa vende, onde atende e quem costuma comprar. Se faltar o local, pergunte
   só isso. Não faça questionário.
2. **Proponha os ramos compradores.** Pense em todos os ramos que compram o produto, não só no que a pessoa citou.
   Use [references/ramos-compradores.md](references/ramos-compradores.md) como ponto de partida. Mostre a lista em
   dois grupos, **núcleo** (compram com certeza) e **vale testar**, e peça confirmação.
3. **Ache os códigos.** `buscar_atividade` para cada ramo. Mostre os códigos escolhidos com o nome oficial.
   Até 15 códigos por busca. Se um ramo não achar, tente o termo formal da Receita.
4. **Raio-X antes de listar.** Chame `estatisticas_empresas` com os ramos e o local. Leia o resultado como manda a
   skill **mercado**: tamanho, porte, faixa, canal, distância. Proponha dois ou três recortes com a contagem de cada
   um e deixe a pessoa escolher. Nunca pule este passo: é grátis e evita salvar gente errada.
5. **Liste.** `buscar_empresas` com o recorte escolhido. Mostre uma tabela curta: nome, bairro, distância, porte,
   faixa e o motivo principal. No máximo 25 linhas na conversa; o resto fica para as próximas páginas.
6. **Salve.** Confirme quais salvar. Use um projeto existente (`listar_projetos`) ou crie um (`criar_projeto`)
   **com a oferta preenchida** (`produto`, `publico_alvo`, `proposta_de_valor`, `chamada`): as mensagens usam
   isso. Depois `salvar_no_projeto` com os CNPJs.
7. **Qualifique.** `qualificar` busca site, Instagram, WhatsApp, telefone e e-mail na web, com prova. Explique
   antes: roda na extensão Agentti do Chrome da pessoa, uns 20 a 30 segundos por empresa. Mostre a prévia que a
   ferramenta devolve (buscas, tempo estimado, cota restante). Se `extensao_conectada` vier falso, avise que a fila
   só começa quando ela entrar na extensão.
8. **Acompanhe e entregue.** `acompanhar_fila`; quando terminar, `listar_leads` com `categoria: "qualificados"`.
   Ofereça o próximo passo: rascunhos de abordagem (skill **abordagem**) ou a ficha de uma empresa
   (skill **relatorio-empresa**).

## Local

- Bairro, endereço ou CEP: `perto_de` + `raio_km`. O raio padrão é 3 km; em bairro denso, 1 a 2 km bastam.
  A busca atravessa bairros e municípios vizinhos.
- Cidade inteira: `cidade` + `uf`. Em cidade pequena, prefira a cidade ao raio.
- Mais de um local: uma chamada por local.

## Regras

- **Dado só vem das ferramentas.** Não invente empresa, contagem, contato nem código.
- **A faixa A/B/C não diz se a empresa compra.** Ela mede o cadastro (porte, tempo ativa, canal, nome fantasia).
  Se a empresa compra ou não é julgamento seu sobre o ramo, e a qualificação traz as provas de contato.
- **Cota.** Salvar gasta 1 de descoberta por empresa; qualificar gasta 1 por empresa buscada. Sempre confirme
  antes. Acima de 50, diga o número e peça um "sim" explícito.
- **Nada é enviado.** O Agentti não manda mensagem para ninguém.
- **Sócio pessoa física** aparece só pelo primeiro nome, e só quando ajuda a cumprimentar.
- Escreva em português do Brasil, direto, sem jargão de sistema. Chame a pré-qualificação de "faixa" e explique
  na primeira vez.
