# Roteiro de configuração — livekit_estudos

## 1. Criar biblioteca

Extraia este zip em:

```text
C:\Users\SEU_USUARIO\Documents\Codex-Library\mbfinance-livekit-migration-agent-library
```

## 2. Criar/clonar projeto

```powershell
cd C:\Users\SEU_USUARIO\Documents\Projetos
git clone URL_DO_REPOSITORIO_LIVEKIT_ESTUDOS
cd livekit_estudos
code .
```

## 3. Copiar starter

Copie o conteúdo de:

```text
mbfinance-livekit-migration-agent-library/project-starter/
```

para dentro do seu repositório `livekit_estudos`.

## 4. Abrir Codex

```powershell
codex
```

## 5. Primeiro prompt

```text
Leia o AGENTS.md, os agentes em .agents/agents e as skills em .agents/skills. Depois me diga quais agentes e skills você reconheceu e como pretende usá-los neste projeto.
```

## 6. Primeiro documento

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
