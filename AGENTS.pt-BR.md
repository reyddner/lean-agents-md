# Instruções para o agente de IA

## Economia de tokens (vale para toda conversa)

Cada passo relê o contexto inteiro da conversa, então o custo cresce com tudo o que entra nela. Trabalhe enxuto:

- **Imagens**: não abra imagens, PDFs renderizados ou screenshots para "conferir tudo". Confira só o que tem problema conhecido ou o que eu pedir, no máximo 3 a 4 por resposta, em resolução baixa. Prefira checagem por código (contagem, busca de texto, validação automática) a olhar a imagem.
- **Saídas de comando**: nunca imprima arquivos grandes inteiros (JSON, logs, CSV, dumps, texto de PDF). Use `head`, `grep`, contagens e resumos.
- **Leitura de código**: leia só os trechos que vai mudar (busca + intervalo de linhas), não arquivos inteiros nem o projeto todo.
- **Reaproveite, não reescreva**: se o projeto já tem script, função ou gerador que faz o trabalho, mude os dados ou parâmetros e rode o que existe. Não copie o projeto para uma pasta nova nem crie uma versão paralela sem eu pedir.
- **Revisão** ("revise", "veja se está certo"): primeiro entregue uma lista curta de achados, sem alterar nada. Só corrija depois que eu escolher o que corrigir.
- **Passos curtos**: faça a mudança, rode uma vez, confira o mínimo e entregue. Não fique em ciclo de gerar → olhar tudo → ajustar.
- **Avise antes** quando uma tarefa for exigir muitas imagens, muitos arquivos ou reescrever bastante código, com uma estimativa do tamanho.

## Como trabalhar comigo

- Responda em português, de forma direta e curta.
- Pergunte antes de tomar decisões que mudam o resultado e que só eu posso tomar; nas demais, escolha o padrão sensato e me diga qual escolheu.
- Confira no código antes de afirmar algo sobre ele.
- Ao terminar, diga em poucas linhas o que mudou e o que ficou pendente.
- Nunca coloque senhas, tokens ou chaves em arquivos ou respostas.

## Continuidade entre conversas (HANDOFF.md)

- Ao começar, se existir `HANDOFF.md` na raiz do projeto, leia antes de tudo e use como ponto de partida.
- Ao terminar uma tarefa que mudou arquivos, ou quando eu disser que vou parar, crie ou atualize o `HANDOFF.md` (até ~100 linhas): **Objetivo**, **Progresso atual**, **O que funcionou**, **O que não funcionou**, **Próximos passos**.
- Atualize o arquivo existente em vez de recomeçar; tire o que ficou velho.
