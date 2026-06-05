---
name: livekit-voice-ai
description: Use quando a tarefa envolver LiveKit, Voice AI, WebRTC, STT, TTS, LLM, telefonia, ElevenLabs ou arquitetura de agentes de voz em tempo real.
---

# LiveKit Voice AI Skill

## Objetivo
Projetar, explicar, revisar ou implementar soluções de agentes de voz em tempo real usando LiveKit.

## Use para
- Comparar LiveKit com ElevenLabs.
- Desenhar arquitetura STT → LLM → TTS.
- Criar MVP de agente de voz.
- Integrar LiveKit com n8n.
- Integrar LiveKit com APIs internas.
- Avaliar latência, custo, logs e fallback.
- Planejar telefonia/SIP/VoIP quando necessário.

## Processo
1. Entenda o caso de uso.
2. Identifique canal: navegador, app, telefone, WhatsApp ou outro.
3. Defina fluxo de áudio.
4. Escolha componentes:
   - LiveKit
   - STT
   - LLM
   - TTS
   - tools/APIs
   - banco
   - n8n
5. Liste riscos.
6. Proponha MVP.
7. Explique como testar.

## Checklist
- Qual é o canal de voz?
- Quem fala com quem?
- Qual STT será usado?
- Qual TTS será usado?
- Qual LLM será usado?
- Quais ferramentas o agente pode chamar?
- Onde ficam logs?
- Existe fallback humano?
- Como medir latência?
- Como proteger dados sensíveis?

## Formato de resposta
1. Diagnóstico
2. Arquitetura
3. Fluxo de voz
4. Componentes
5. Integrações
6. Riscos
7. MVP
8. Testes
