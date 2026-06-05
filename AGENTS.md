# AGENTS.md — livekit_estudos

## Contexto do projeto

Este repositório é um projeto de estudos e análise técnica sobre LiveKit aplicado ao contexto da MB Finance.

A empresa atualmente utiliza ElevenLabs para criação e operação de agentes de voz, mas existe uma preocupação interna com:

- custo elevado da plataforma;
- subutilização de parte dos recursos contratados;
- limitações de funcionalidades;
- necessidade de maior controle sobre agentes de Voice AI;
- possibilidade de criar uma infraestrutura própria;
- integração mais profunda com APIs internas, n8n, webhooks, sistemas internos e front-end próprio.

Por isso, este projeto deve ajudar a avaliar se uma migração da ElevenLabs para uma arquitetura baseada em LiveKit é tecnicamente viável, financeiramente interessante e operacionalmente sustentável.

## Contexto profissional

Sou estagiário na MB Finance e estou aprendendo/trabalhando com:

- Agentes de IA
- ElevenLabs
- LiveKit
- Voice AI
- n8n
- APIs REST
- Webhooks
- PostgreSQL/Neon
- Sistemas internos
- Integrações
- Automações empresariais
- Front-end interno
- IA aplicada a processos de negócio

A empresa incentiva o uso de IA para produtividade, aprendizado, desenvolvimento e automação.

## Objetivo do repositório

Este projeto deve me ajudar a:

- Entender o que é LiveKit.
- Entender como LiveKit se compara com ElevenLabs.
- Identificar o que a ElevenLabs entrega pronto.
- Identificar o que o LiveKit entrega e o que precisaria ser construído pela equipe.
- Avaliar vantagens e desvantagens de uma possível migração.
- Entender os componentes necessários para construir agentes próprios de Voice AI.
- Estudar arquitetura com front-end próprio conectado à API interna e à infraestrutura do LiveKit.
- Mapear como n8n, APIs, webhooks e sistemas internos entrariam nessa arquitetura.
- Preparar ideias, riscos, perguntas e propostas para reuniões técnicas da empresa.
- Criar documentação clara para apoiar uma decisão futura.

## Problema de negócio

A MB Finance possui agentes de voz na ElevenLabs, mas o custo atual é considerado elevado em relação ao uso real e às limitações percebidas da plataforma.

A empresa quer entender se, usando LiveKit, seria possível:

- reduzir custos operacionais;
- aumentar controle técnico;
- ampliar possibilidades de customização;
- criar agentes próprios;
- conectar melhor com sistemas internos;
- criar um front-end próprio para operação/configuração;
- integrar a solução com APIs internas, n8n e webhooks;
- depender menos de uma plataforma fechada.

## Hipótese principal

A hipótese a ser investigada é:

"LiveKit pode permitir uma arquitetura própria de Voice AI com mais controle, mais flexibilidade e potencialmente menor custo do que a operação atual baseada exclusivamente em ElevenLabs."

Essa hipótese precisa ser validada tecnicamente, financeiramente e operacionalmente.

## Pontos que precisam ser avaliados

Sempre que estudar ou propor algo, considere:

1. O que a ElevenLabs entrega pronto hoje.
2. O que o LiveKit entrega nativamente.
3. O que precisaríamos construir por conta própria.
4. Quais serviços externos ainda seriam necessários.
5. Quais custos seriam reduzidos.
6. Quais novos custos apareceriam.
7. Qual seria a complexidade técnica.
8. Qual seria a complexidade operacional.
9. Quais riscos existem.
10. Qual seria um MVP viável.
11. Se a migração total faz sentido.
12. Se uma abordagem híbrida faria mais sentido.
13. Se devemos considerar outras ferramentas além do LiveKit.

## Como o Codex deve atuar

Antes de executar uma tarefa:

1. Classifique se a demanda é estudo, comparação, arquitetura, documentação, MVP ou implementação.
2. Escolha poucos agentes relevantes.
3. Use as skills adequadas.
4. Prefira explicações didáticas, pois ainda estou aprendendo.
5. Priorize soluções simples antes de soluções complexas.
6. Explique o raciocínio técnico.
7. Sempre mostre como testar ou validar.
8. Sempre aponte riscos técnicos, operacionais e de custo.
9. Nunca exponha secrets, tokens, chaves de API ou dados sensíveis.
10. Não faça alterações destrutivas sem explicar antes.
11. Não assuma que LiveKit é automaticamente melhor que ElevenLabs.
12. Compare alternativas de forma crítica e pragmática.

## Agentes disponíveis

Os agentes estão em:

```text
.agents/agents/
```

Priorize estes agentes para este projeto:

- Voice AI & LiveKit Migration Architect
- Voice AI Cost & Feasibility Analyst
- API & Webhook Integration Engineer
- n8n Automation Architect
- Internal Voice AI Frontend Architect
- Prompt Engineering & Agent Behavior Specialist
- Documentation & Knowledge Engineer
- Security & Privacy Engineer
- Back-end Architect & API Engineer
- AI, Automation & Tooling Engineer
- MB Finance Automation Mentor

## Skills disponíveis

As skills estão em:

```text
.agents/skills/
```

Priorize estas skills:

- voice-ai-migration-analysis
- livekit-voice-ai
- api-webhook-integration
- n8n-automation
- internal-voice-ai-frontend
- prompt-engineering
- mbfinance-learning-mentor
- elevenlabs-agent-prompt

## Regras para estudos sobre LiveKit

Quando eu pedir explicação sobre LiveKit:

1. Explique primeiro a visão geral.
2. Depois explique onde ele entra numa arquitetura de Voice AI.
3. Depois compare com ElevenLabs.
4. Depois explique o que vem pronto e o que precisa ser construído.
5. Depois relacione com n8n, APIs, webhooks e sistemas internos.
6. Depois aponte riscos.
7. Depois proponha um exercício, documento ou experimento.

## Regras para análise de migração

Quando eu pedir comparação ou análise de migração ElevenLabs → LiveKit, sempre avalie:

- custo;
- controle;
- complexidade;
- manutenção;
- features disponíveis;
- features ausentes;
- dependências externas;
- tempo de implementação;
- risco operacional;
- curva de aprendizado da equipe;
- segurança;
- observabilidade;
- escalabilidade;
- viabilidade de MVP;
- possibilidade de abordagem híbrida.

## Regras para documentação

Quando criar documentos em `docs/`, use linguagem clara e organizada.

Cada documento deve conter:

- objetivo;
- contexto de negócio;
- explicação didática;
- arquitetura ou fluxo;
- comparação com ElevenLabs quando fizer sentido;
- vantagens;
- desvantagens;
- riscos;
- perguntas em aberto;
- próximos passos.

## Regras para código

Quando criar código:

- prefira MVP simples;
- explique estrutura de pastas;
- use nomes claros;
- documente variáveis de ambiente;
- não coloque secrets no código;
- crie `.env.example` quando necessário;
- explique como rodar;
- explique como testar;
- sinalize quando algo for apenas protótipo.

## Foco atual

O foco atual é chegar preparado para discutir LiveKit na empresa, entendendo:

- o que é LiveKit;
- para que serve;
- como ele se compara com ElevenLabs;
- o que ele não substitui sozinho;
- quais componentes são necessários para criar agentes próprios;
- onde entram STT, LLM e TTS;
- onde entram n8n, APIs e webhooks;
- como seria um front-end próprio conectado a APIs internas e LiveKit;
- quais riscos existem;
- qual seria um MVP inicial;
- quais perguntas levar para reunião;
- se a migração parece viável ou se uma abordagem híbrida é melhor.
