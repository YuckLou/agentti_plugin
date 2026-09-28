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

Não precisa decorar: pedir em português normal ("quem compra polpa de fruta na Vila Mariana?") já usa o
caminho certo.

## Instalar

### Claude (web e Desktop) e Cowork

1. Personalizar → Plugins → adicionar marketplace pela URL `https://github.com/YuckLou/agentti-plugin`.
2. Instale o plugin **ag**.
3. Conecte o Agentti: em Personalizar → Conectores, entre com a sua conta do Agentti quando o Claude pedir. Se o
   conector não aparecer, adicione um conector personalizado com a URL `https://app.agentti.ia.br/mcp`.

### Claude Code

```
/plugin marketplace add YuckLou/agentti-plugin
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

- **0.1.0**: primeira versão, em teste.
