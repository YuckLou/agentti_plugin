# Agentti para o Claude

Plugin que ensina o Claude a trabalhar com o **Agentti Lead Generator**: prospecção B2B sobre a base oficial da
Receita Federal (todo o Brasil), leitura de mercado, rascunhos de abordagem e relatórios em Word e PDF.

O conector do Agentti entrega os dados. Este plugin entrega o método: que ramos compram o seu produto, como ler
o mercado antes de listar, como escrever uma mensagem que não parece spam e como montar um relatório que o seu
cliente consegue editar.

## O que você precisa

- Uma conta no Agentti: [agentti.ia.br](https://agentti.ia.br).
- Claude Pro, Max, Team ou Enterprise (o plano gratuito não tem plugins; nele, o conector sozinho funciona).
- Para qualificar leads (achar site, Instagram, WhatsApp e e-mail com prova): a extensão Agentti no Chrome.

## Comandos

| Comando | O que faz |
| :--- | :--- |
| `/ag:prospectar <o que você vende> em <local>` | do ramo à lista qualificada, passo a passo |
| `/ag:mercado <ramos> em <local>` | quantas empresas existem, de que porte, onde, e os melhores recortes |
| `/ag:abordagem <lead, CNPJ ou projeto>` | rascunhos por canal e a sequência de follow-up |
| `/ag:relatorio-empresa <CNPJ ou lead>` | ficha completa, na conversa ou em Word e PDF |
| `/ag:relatorio-regiao <ramos> em <local>` | relatório de mercado em Word e PDF |
| `/ag:exportar <projeto> [csv, json ou xlsx]` | leads do projeto com link de download (15 min) |
| `/ag:descobrir <o que buscar> em <local>` | lugares no Google Maps que a Receita não mostra ou mostra sem contato |
| `/ag:pesquisa-profunda <lead ou CNPJ>` | quem é a empresa, o que vende, se está ativa, com a fonte de cada fato |

Não precisa decorar: pedir em português normal ("quem compra polpa de fruta na Vila Mariana?") já usa o
caminho certo.

## Instalar

### Claude (web e Desktop) e Cowork

1. Personalizar → Plugins → adicionar marketplace pela URL `https://github.com/YuckLou/agentti_plugin`.
2. Instale o plugin **ag**.
3. Conecte o Agentti: em Personalizar → Conectores, entre com a sua conta do Agentti quando o Claude pedir. Se o
   conector não aparecer, adicione um conector personalizado com a URL `https://app.agentti.ia.br/mcp`.

### Claude Code

```
/plugin marketplace add YuckLou/agentti_plugin
/plugin install ag@agentti
```

Depois, `/mcp` para entrar com a sua conta do Agentti. Se você já tinha adicionado o conector do Agentti à mão,
desligue um dos dois em `/mcp` para as ferramentas não aparecerem em dobro.

## Privacidade e boas práticas

- O Agentti **não envia mensagens**. Tudo o que o Claude escreve é rascunho para você revisar.
- Salvar e qualificar leads consomem a cota do seu plano Agentti; o Claude confirma antes.
- Contato comercial entre empresas, uma mensagem por vez, sempre com saída educada. Nada de disparo em massa.
- Este repositório não guarda dado de cliente nem token. Os exemplos usam empresas fictícias.

## Versões

- **0.6.0**: menos ferramentas no conector (24 → 19), com a mesma precisão: `listar` (projetos, buscas, relatórios, imagens e geometrias) e `projeto` (cria o projeto ou grava a oferta). Textos das ferramentas mais curtos, para gastar menos tokens a cada pedido. As skills já usam os nomes novos; atualize o plugin junto com o conector.
- **0.5.4**: relatório e mensagem pela IA também mostram a prévia da cota e esperam o seu "sim" (tabela de cotas de 10/10/2026: relatórios e textos da IA têm cota própria).
- **0.5.3**: mapa no relatório: `gerar_imagem_mapa` desenha as empresas do recorte (pontos pela faixa ou calor) com o painel do Agentti aberto no navegador, e o `gerar_relatorio` põe o mapa numa seção "No mapa". O mapa que você está vendo também vai para o relatório (botão "Enviar ao assistente" na prancha do mapa).
- **0.5.0**: o agente sabe como o motor trabalha (Chrome do Agentti, ritmo humano, provas) e usa o que a empresa diz de si (bio, último post, avaliações do Maps, site), sempre com a fonte. Skills novas **descobrir** (Google Maps pelo Chrome) e **pesquisa-profunda**. Relatórios e campanhas seguem o que você pedir (foco, canal, tom, quantidade).
- **0.4.2**: tudo que gasta cota (salvar, qualificar) mostra antes quantas empresas e quanto de cota, e só acontece depois do seu "sim", mesmo que o pedido já diga "salve". Relatórios ficam na página **Relatórios** do painel. "Cidade e região" sem raio chutado: ferramenta `regiao` (a cidade e as que fazem divisa, ou a região metropolitana). Contexto do mercado com o IBGE: população, estabelecimentos por 10 mil habitantes e PIB per capita por município, com o ano de cada dado.
- **0.4.1**: planilha e CSV numa chamada só, com o arquivo pelo link (o Claude não remonta o arquivo na conversa); relatórios já feitos voltam com link novo (`listar_relatorios`) e aparecem no painel em Projetos → Relatórios.
- **0.4.0**: relatórios em Word e PDF gerados no servidor do Agentti (não precisa de Python no computador; os números saem da base, a análise é do Claude); lista com uma linha por empresa e sem repetir entre páginas; "salve todas" pela busca salva, com a cota mostrada antes; exportação só do que veio de uma busca.
- **0.3.0**: projeto primeiro; a busca fica gravada no projeto e aparece como aba na Consulta CNPJ do painel (sem gastar cota); empresas só são salvas quando você escolhe; a exportação sai completa.
- **0.2.0**: relatórios por um gerador fixo (Word e PDF iguais em qualquer lugar, com gráficos e a marca), sem o Claude escrever código a cada vez; menos tokens nas buscas.
- **0.1.4**: comando `/ag:exportar`; a abordagem lê a oferta gravada no projeto; ficha de empresa por CNPJ com faixa e rede.
- **0.1.3**: relatórios com o mínimo da marca (Word e PDF, gráficos, cores, logo) mesmo quando o pedido é só "um PDF".
- **0.1.2**: plugin movido para `plugins/ag` (o Claude Desktop não lia o plugin na raiz do marketplace).
- **0.1.1**: ajustes do primeiro teste (mensagem não inventa fatos da oferta; CNPJ só com dígitos; perguntar antes de instalar pacote).
- **0.1.0**: primeira versão, em teste.
