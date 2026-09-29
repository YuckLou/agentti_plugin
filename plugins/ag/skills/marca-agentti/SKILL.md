---
name: marca-agentti
description: Gerador dos documentos do Agentti em Word e PDF (cabeçalho com logo, rodapé com a origem dos dados, tabelas e gráficos na marca, seção "Sobre os dados"). Use sempre que for gerar um relatório de empresa ou de região do Agentti como arquivo.
user-invocable: false
---

# Documentos Agentti: use o gerador

> **Reserva.** O caminho normal é a ferramenta `gerar_relatorio` do conector, que gera no servidor. Use este
> gerador local só se o conector não tiver essa ferramenta.

O visual é fixo no script `scripts/gerar_relatorio.py` desta skill. **Não escreva código de documento nem de
gráfico**: monte o conteúdo em JSON e rode o script. Ele gera o `.docx` (principal, editável) e o `.pdf` do mesmo
conteúdo, com gráficos, cores, logo e rodapé.

1. Monte o JSON no formato de [references/formato.md](references/formato.md) (exemplo em
   [references/exemplo.json](references/exemplo.json)), só com números das ferramentas do Agentti. Grave em
   `conteudo.json`.
2. Rode:
   ```bash
   python "${CLAUDE_PLUGIN_ROOT}/skills/marca-agentti/scripts/gerar_relatorio.py" conteudo.json --saida <pasta> --previa
   ```
   Se esse caminho não existir, ache o script com
   `find / -name gerar_relatorio.py -path "*marca-agentti*" 2>/dev/null | head -1`.
3. O script responde uma linha JSON:
   - com `docx` e `pdf`: entregue os dois;
   - com `erro` e `detalhes`: corrija o JSON no ponto indicado e rode de novo;
   - com `instalar`: faltam pacotes. No ambiente isolado do Claude, instale e rode de novo. No computador da
     pessoa (Claude Code), **pergunte antes** de instalar.
4. Conferência: no máximo **uma** olhada na `previa` (a 1ª página, em miniatura). Não renderize as outras páginas.

A marca é discreta e sai inteira ao apagar o cabeçalho, o rodapé e a seção "Sobre os dados". Os estilos
nomeados ("Título Agentti", "Texto Agentti", ...) deixam o cliente trocar o visual de uma vez no Word.
