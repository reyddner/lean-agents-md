# lean-agents-md

Um arquivo de instruções que faz agentes de IA de programação (Codex, Claude Code e outros) **pararem de gastar tokens à toa**. Coloque no lugar certo e o agente lê sozinho no início de cada conversa.

*English version: [README.md](README.md)*

## Por que os agentes gastam tanto

A cada passo (cada chamada de ferramenta), o agente relê a conversa **inteira** até ali. O gasto cresce com o que se acumula no contexto, não com o que o agente escreve.

Uma sessão real que esgotou os tokens em menos de uma hora:

| | Tokens |
|---|---|
| Lidos (entrada), em ~50 passos | **5,3 milhões** |
| Escritos (saída) | 39 mil |
| Contexto relido por passo, no final | ~90 mil |

O que encheu o contexto: dezenas de páginas renderizadas abertas "para conferir", saídas de comando grandes impressas inteiras e um pipeline novo escrito do zero em vez de mudar parâmetros no que já existia. O mesmo projeto, feito em passos curtos, quase não gastou tokens.

## O que o arquivo pede ao agente

- Abrir só as imagens que importam (3 a 4 por resposta, em resolução baixa); conferir por código quando der.
- Nunca imprimir arquivos grandes inteiros; usar `head`, `grep`, contagens.
- Ler só o código que vai mudar.
- Reaproveitar os scripts existentes em vez de reescrever ou copiar o projeto.
- Em revisões, listar os achados primeiro e corrigir só o que você escolher.
- Passos curtos; avisar antes de tarefas grandes.
- Manter um `HANDOFF.md` para a próxima conversa continuar de onde esta parou.

## Instalação

| Agente | Todos os projetos | Um projeto |
|---|---|---|
| Codex | `~/.codex/AGENTS.md` | `AGENTS.md` na raiz do projeto |
| Claude Code | `~/.claude/CLAUDE.md` | `CLAUDE.md` na raiz do projeto |

Use [AGENTS.pt-BR.md](AGENTS.pt-BR.md) e renomeie para `AGENTS.md` ou `CLAUDE.md` ao instalar. No Windows, `~` é `C:\Users\<você>`.

Se você já tem um desses arquivos, cole as seções nele em vez de substituir.

## Dicas além do arquivo

- **Abra uma conversa nova para cada etapa** (revisar numa, corrigir em outra). O contexto zera, e essa é a maior economia.
- Diga no pedido quando importar: "sem abrir imagens", "use os scripts que já existem".

## Licença

[CC0 1.0](LICENSE): domínio público. Copie, altere e compartilhe à vontade, sem precisar citar.
