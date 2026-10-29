# EstudaAí

Tutor de estudos com IA para universitários. Projeto da atividade A3 de Inteligência Artificial (UCs HUB 2026.2).

## Problema
Alunos chegam às provas sem saber se entenderam a matéria: reler slides não testa o aprendizado e a monitoria é escassa.

## O que o app faz
1. O aluno cola o conteúdo de uma aula (texto, resumo ou slides).
2. **Explicar:** a IA explica o conteúdo de forma simples, com exemplos do dia a dia.
3. **Gerar quiz:** a IA cria 5 questões de múltipla escolha baseadas somente no conteúdo colado.
4. **Corrigir:** o app calcula a nota, mostra acertos e erros, explica cada erro e lista o que revisar.
5. **Novo quiz:** gera questões diferentes sobre o mesmo conteúdo.

## Arquitetura
- Página web em um único arquivo (`index.html`): HTML, CSS e JavaScript puro, sem servidor.
- Modelo de linguagem: Llama 3.3 70B, acessado pela API do [Groq](https://console.groq.com) (compatível com o formato da OpenAI), com modelos reserva caso o principal fique indisponível.
- Técnica de IA: Processamento de Linguagem Natural com LLM via engenharia de prompts. O quiz é pedido em modo JSON e validado no navegador (4 alternativas, índice da correta de 0 a 3), com uma nova tentativa automática se o formato vier errado.
- A nota é calculada no próprio navegador, sem IA; só as questões erradas vão para a IA gerar o "O que revisar".

## Como rodar
1. Crie uma chave gratuita em https://console.groq.com/keys.
2. Abra `index.html` num editor de texto e troque `COLE_SUA_CHAVE_AQUI` pela chave.
3. Abra `index.html` no navegador.

> Não faça commit da sua chave. Ela é pessoal e o GitHub/Groq a cancelam se ela for publicada.

## Ética e privacidade
- Aviso fixo de que a IA pode errar e de que o aluno deve conferir com o material da disciplina.
- Os prompts instruem a IA a usar apenas o conteúdo fornecido, para reduzir respostas inventadas.
- Nenhum dado do aluno é salvo. O conteúdo colado é enviado à API do Groq apenas para gerar a resposta.
