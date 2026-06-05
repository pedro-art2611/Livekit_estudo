# Prompts iniciais para Codex

## 1. Validar agentes e skills

```text
Leia o AGENTS.md, os agentes em .agents/agents e as skills em .agents/skills. Depois me diga quais agentes e skills você reconheceu e como pretende usá-los neste projeto.
```

## 2. Análise inicial de migração

```text
Use o agente Voice AI & LiveKit Migration Architect e a skill voice-ai-migration-analysis.

Crie um documento em docs/01-analise-inicial-migracao-elevenlabs-livekit.md com:

1. Contexto do problema
2. O que provavelmente usamos da ElevenLabs hoje
3. O que o LiveKit poderia substituir
4. O que o LiveKit não substitui sozinho
5. Quais componentes precisaríamos construir
6. Como seria uma arquitetura com front-end próprio + API interna + LiveKit
7. Onde entram STT, LLM, TTS, n8n e webhooks
8. Riscos técnicos
9. Riscos operacionais
10. Riscos de custo
11. Possibilidade de abordagem híbrida
12. MVP recomendado
13. Perguntas para levar para a reunião de segunda
14. Recomendação inicial sem assumir que a migração é automaticamente melhor
```

## 3. Preparação para reunião

```text
Use o agente MB Finance Automation Mentor, Voice AI & LiveKit Migration Architect e a skill voice-ai-migration-analysis.

Crie um documento em docs/02-preparacao-reuniao-livekit.md para eu estudar antes da reunião.

O documento deve conter:

1. Explicação simples do que é LiveKit
2. Diferença entre plataforma pronta e infraestrutura customizável
3. Como explicar a diferença entre ElevenLabs e LiveKit em uma reunião
4. 10 perguntas inteligentes que eu posso fazer
5. 5 ideias de MVP para testar LiveKit
6. Riscos que eu devo mencionar com cuidado
7. Possíveis benefícios para a MB Finance
8. Pontos onde eu ainda devo evitar afirmar algo com certeza
```

## 4. Front próprio

```text
Use o agente Internal Voice AI Frontend Architect e a skill internal-voice-ai-frontend.

Crie um documento em docs/03-front-interno-voice-ai.md explicando como poderia ser um front-end interno para operar agentes próprios de Voice AI.

Inclua:
- usuários internos
- telas necessárias
- fluxos principais
- integração com API interna
- integração com LiveKit
- logs
- permissões
- MVP inicial
```

## 5. Arquitetura com n8n

```text
Use o agente n8n Automation Architect, API & Webhook Integration Engineer e a skill n8n-automation.

Crie um documento em docs/04-livekit-n8n-webhooks.md explicando onde o n8n poderia entrar em uma arquitetura com LiveKit.

Inclua:
- eventos possíveis
- webhooks
- chamadas HTTP
- integração com sistemas internos
- logs
- riscos de duplicidade
- tratamento de erro
```
