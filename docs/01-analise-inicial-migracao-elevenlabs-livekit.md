# Analise inicial de migracao: ElevenLabs para LiveKit

## Objetivo

Este documento organiza uma primeira analise sobre a possibilidade de migrar, total ou parcialmente, a operacao atual de agentes de voz da ElevenLabs para uma arquitetura propria baseada em LiveKit.

A ideia nao e concluir que LiveKit e automaticamente melhor. O objetivo e entender o problema de negocio, separar o que a ElevenLabs entrega pronto, identificar o que o LiveKit poderia substituir, mapear o que ainda precisaria ser construido e preparar perguntas para uma reuniao tecnica.

## 1. Contexto do problema

A MB Finance utiliza agentes de voz na ElevenLabs, mas existe preocupacao com custo elevado, subutilizacao de recursos contratados, limitacoes de funcionalidades e dependencia de uma plataforma fechada.

A hipotese em estudo e que uma arquitetura baseada em LiveKit poderia dar mais controle tecnico, mais flexibilidade de integracao com sistemas internos e talvez reduzir custos operacionais. Essa hipotese ainda precisa ser validada com dados reais de uso, custo, qualidade, manutencao e risco.

O ponto central da analise e:

> A empresa quer apenas pagar menos por agentes de voz, ou quer tambem ganhar controle tecnico sobre fluxo, prompts, integracoes, logs, metricas e experiencia operacional?

Essa diferenca importa porque LiveKit nao e uma plataforma pronta equivalente a ElevenLabs. LiveKit e uma infraestrutura de comunicacao em tempo real. Ele pode ser uma base forte para criar agentes proprios de Voice AI, mas exige que varios componentes sejam escolhidos, integrados e mantidos.

## 2. O que provavelmente usamos da ElevenLabs hoje

Sem acesso aos detalhes internos da operacao atual, esta secao deve ser tratada como uma hipotese inicial.

Provavelmente a ElevenLabs entrega ou facilita hoje:

- criacao e configuracao de agentes de voz;
- interface pronta para gerenciar agentes;
- vozes sinteticas e configuracao de TTS;
- parte da experiencia conversacional;
- conexao entre fala do usuario, modelo de IA e resposta em voz;
- testes manuais de agentes;
- possiveis integracoes via API ou webhooks;
- historico, logs ou registros basicos de interacoes;
- configuracoes de comportamento do agente;
- infraestrutura gerenciada pela propria plataforma;
- reducao da necessidade de manter servidores proprios para voz.

Tambem e possivel que a empresa use recursos que ainda precisam ser confirmados:

- telefonia;
- transcricao;
- gravacao de chamadas;
- metricas de uso;
- ferramentas chamadas pelo agente;
- integracoes com CRM, sistemas internos ou n8n;
- controle de custos por agente, campanha ou cliente;
- analytics de conversas.

## 3. O que o LiveKit poderia substituir

O LiveKit poderia substituir principalmente a camada de comunicacao em tempo real e parte da infraestrutura de voz.

Na pratica, ele pode ajudar com:

- salas de audio em tempo real;
- conexao WebRTC entre usuario, navegador, app, servidor ou agente;
- transporte de audio com baixa latencia;
- gerenciamento de participantes em uma chamada;
- eventos de entrada e saida de participantes;
- base para criar um agente de voz conectado a uma sala;
- integracao com pipelines de STT, LLM e TTS;
- possibilidade de criar experiencia propria no front-end;
- maior controle sobre logs, eventos e arquitetura.

Em uma arquitetura propria, LiveKit seria a camada que transporta o audio e conecta os participantes da conversa. Ele poderia ser usado para permitir que um usuario fale com um agente de IA em tempo real, enquanto o back-end coordena transcricao, raciocinio, resposta, ferramentas e logs.

## 4. O que o LiveKit nao substitui sozinho

LiveKit nao substitui sozinho a ElevenLabs como produto completo de agentes de voz.

Ele nao resolve automaticamente:

- STT, ou seja, conversao de fala para texto;
- TTS, ou seja, conversao de texto para voz;
- escolha e orquestracao do LLM;
- prompt do agente;
- memoria, contexto e historico de conversa;
- regras de negocio;
- integracao com sistemas internos;
- painel administrativo para operadores;
- analytics de custo e qualidade;
- observabilidade completa;
- gravacao, retencao e governanca de dados;
- fallback humano;
- controle de versoes de prompt;
- testes automatizados de comportamento;
- monitoramento de latencia ponta a ponta;
- seguranca de webhooks, tokens e APIs;
- operacao e suporte do produto final.

Essa e a diferenca mais importante: ElevenLabs tende a entregar uma experiencia mais pronta; LiveKit entrega uma base tecnica mais flexivel, mas exige construcao ao redor.

### Comparacao objetiva por camadas

Esta comparacao deve ser lida como uma visao inicial. Ela nao prova que uma alternativa e melhor que a outra; apenas ajuda a separar o que hoje tende a vir pronto em uma plataforma como ElevenLabs do que precisaria ser montado em uma arquitetura propria com LiveKit.

| Camada | ElevenLabs | Arquitetura com LiveKit |
| --- | --- | --- |
| Comunicacao em tempo real | Tende a abstrair a experiencia de conversa dentro da plataforma. | LiveKit e forte nessa camada: salas, audio em tempo real, WebRTC, participantes e eventos. |
| STT | Pode oferecer ou integrar transcricao dependendo do recurso contratado e configurado. Precisa ser confirmado no uso atual. | Precisa escolher e integrar um provedor externo de STT, avaliando portugues, latencia, custo e ruido. |
| TTS | E um dos pontos centrais da plataforma, com vozes prontas e configuraveis. | Precisa integrar um provedor de TTS. Pode continuar usando ElevenLabs apenas para voz em uma abordagem hibrida. |
| LLM/orquestracao | Pode entregar parte da experiencia de agente, configuracao e ferramentas dentro da plataforma. | Precisa construir ou integrar a orquestracao do agente, prompts, memoria, ferramentas, regras e chamadas ao LLM. |
| Telefonia | Pode ja oferecer recursos prontos ou integracoes, dependendo do plano e da configuracao atual. | Pode exigir integracao com SIP, provedor telefonico, roteamento, gravacao, numeros, qualidade de chamada e suporte operacional. |
| Logs e historico | Pode oferecer logs, historico e analytics basicos ou avancados, dependendo dos recursos usados. | Precisa desenhar persistencia, logs estruturados, metricas, auditoria, retencao e telas de consulta. |
| Front-end de operacao | Tende a oferecer uma interface pronta para configurar, testar e operar agentes. | Precisa construir um front-end interno, que vira um produto operacional com usuarios, permissoes, UX, suporte e evolucao. |
| Integracoes | Pode oferecer APIs, webhooks e ferramentas, mas dentro dos limites da plataforma. | Pode dar mais controle, mas exige API interna, contratos, seguranca, retries, n8n e manutencao das integracoes. |
| Manutencao | Parte da manutencao tecnica fica com a plataforma. | A equipe assume manutencao de arquitetura, provedores, bugs, logs, monitoramento, incidentes e evolucao. |
| Custo | Pode ser mais previsivel como assinatura/plano, mas caro se houver subutilizacao. | Pode reduzir custos em alguns cenarios, mas adiciona custos de STT, TTS, LLM, LiveKit, telefonia, infraestrutura, desenvolvimento e suporte. |
| Customizacao | Mais limitada ao que a plataforma permite. | Maior controle e flexibilidade, com maior complexidade tecnica e operacional. |

## 5. Quais componentes precisariamos construir

Para operar agentes proprios de Voice AI com LiveKit, a equipe provavelmente precisaria construir ou integrar os seguintes componentes:

- back-end de orquestracao do agente;
- servico para criar salas, tokens e sessoes LiveKit;
- pipeline STT -> LLM -> TTS;
- integracao com provedor de STT;
- integracao com provedor de TTS;
- integracao com um ou mais LLMs;
- camada de ferramentas do agente para consultar APIs internas;
- persistencia de chamadas, eventos, transcricoes e metricas;
- front-end interno para operar e configurar agentes;
- tela de teste de agente;
- historico de chamadas;
- logs tecnicos e logs de negocio;
- webhooks para eventos importantes;
- integracao com n8n para automacoes;
- mecanismos de retry e tratamento de erro;
- autenticacao e autorizacao;
- controle de permissao por usuario interno;
- protecao de dados sensiveis;
- monitoramento de custo por chamada;
- metricas de latencia, erro e qualidade.
- politica de retencao de audio, transcricoes, logs e dados sensiveis;
- auditoria de acoes do agente, chamadas a ferramentas e acessos internos.

Em um MVP, nem tudo precisa nascer completo. O foco inicial deveria ser provar o fluxo basico com seguranca e medicao.

## 6. Como seria uma arquitetura com front-end proprio + API interna + LiveKit

Uma arquitetura inicial poderia ser:

```text
Usuario/Operador
  |
  | acessa
  v
Front-end interno
  |
  | login, configuracao, teste, historico
  v
API interna da MB Finance
  |
  | cria sessao, gera token, registra chamada
  v
LiveKit
  |
  | audio em tempo real
  v
Agente de Voice AI
  |
  | envia audio para STT
  v
STT
  |
  | texto transcrito
  v
LLM
  |
  | chama ferramentas/APIs/n8n quando necessario
  v
TTS
  |
  | audio sintetizado
  v
LiveKit
  |
  | resposta em voz
  v
Usuario
```

O front-end proprio serviria para operadores internos criarem, testarem, acompanharem e configurarem agentes. A API interna concentraria regras de negocio, seguranca, tokens, logs, permissoes e integracoes. O LiveKit ficaria responsavel pela comunicacao em tempo real.

Essa separacao e importante porque regras de negocio nao deveriam ficar espalhadas apenas no prompt do agente. O prompt orienta comportamento; a API interna deve validar dados, permissao, regras deterministicas e integracoes sensiveis.

O front-end proprio nao deve ser tratado apenas como uma tela simples. Se a solucao evoluir, ele vira um produto interno: precisa ter usuarios claros, permissoes, historico, auditoria, estados de erro, UX para operadores, suporte, documentacao e manutencao continua. Um painel ruim pode reduzir a produtividade da operacao mesmo que a arquitetura tecnica funcione.

A API interna deve funcionar como camada de governanca. Ela deve concentrar autenticacao, autorizacao, validacao de dados, regras deterministicas, limites de acao do agente, auditoria, rate limits, protecao contra uso indevido de ferramentas e controle sobre quais dados podem ser enviados a provedores externos. O agente pode sugerir uma acao, mas a API interna deve decidir se a acao e permitida.

## 7. Onde entram STT, LLM, TTS, n8n e webhooks

### STT

STT entra quando o audio do usuario precisa virar texto para o agente entender a mensagem. Exemplos de provedores possiveis incluem Deepgram, AssemblyAI, OpenAI, Google, Azure ou outros. A escolha impacta latencia, custo, idioma, qualidade de transcricao e suporte a tempo real.

### LLM

O LLM interpreta a transcricao, decide a resposta e pode chamar ferramentas. Ele deve receber contexto, regras, historico relevante e instrucoes claras. Tambem precisa ser protegido contra respostas indevidas e contra chamadas erradas de ferramentas.

### TTS

TTS transforma a resposta textual do agente em audio. Pode continuar sendo ElevenLabs, mesmo em uma arquitetura com LiveKit, caso a voz da ElevenLabs seja boa ou estrategica. Tambem podem ser avaliados outros provedores.

### n8n

O n8n pode entrar como camada de automacao para processos empresariais, especialmente quando o fluxo nao precisa ocorrer em baixissima latencia. Exemplos:

- registrar resumo da chamada;
- disparar notificacao interna;
- atualizar CRM;
- criar tarefa para equipe;
- enviar dados para planilha ou banco;
- acionar webhook depois que a chamada termina;
- integrar sistemas que ainda nao possuem API interna padronizada.

Para decisoes em tempo real durante a fala, o n8n precisa ser usado com cuidado, porque pode adicionar latencia e pontos de falha.

Uma regra pratica para o MVP seria separar responsabilidades:

- API interna para decisoes sincronas e sensiveis em tempo real, como consultar dados, validar permissoes, executar acoes criticas e responder ao agente durante a chamada;
- n8n para automacoes assincronas ou pos-chamada, como registrar resumo, enviar notificacao, atualizar sistemas, criar tarefas e disparar fluxos que nao precisam bloquear a conversa.

### Webhooks

Webhooks podem ser usados para eventos como:

- chamada iniciada;
- chamada encerrada;
- erro no agente;
- transferencia para humano;
- lead qualificado;
- solicitacao de atendimento;
- resumo gerado;
- transcricao disponivel;
- alerta de custo ou latencia.

Cada webhook precisa ter autenticacao, validacao de payload, logs, estrategia de retry e idempotencia para evitar duplicidade de eventos.

## 8. Riscos tecnicos

- Latencia alta entre STT, LLM, TTS e LiveKit.
- Qualidade de voz inferior ou inconsistente em relacao a solucao atual.
- Transcricao ruim em portugues, sotaques, ruido ou chamadas telefonicas.
- Complexidade de streaming de audio em tempo real.
- Erros de sincronizacao entre audio, texto e estado da conversa.
- Dificuldade de integrar telefonia/SIP caso esse seja um canal importante.
- Falta de observabilidade desde o inicio.
- Agente chamar APIs erradas ou em momentos inadequados.
- Dificuldade de testar comportamento conversacional de forma repetivel.
- Dependencia de varios fornecedores ao mesmo tempo.
- Falhas em cascata quando STT, LLM, TTS, LiveKit ou API interna ficam instaveis.
- Falta de logs estruturados e correlation ID por chamada dificultar a investigacao de problemas.
- Metricas agregadas esconderem gargalos especificos em STT, LLM, TTS, LiveKit, API interna ou n8n.

Telefonia/SIP merece atencao especial. Se o canal principal for telefone, a complexidade do projeto aumenta: entram qualidade de ligacao, numeros telefonicos, roteamento, gravacao, transferencia, provedores SIP, custos por minuto, suporte a chamadas reais e possiveis requisitos regulatorios. Por isso, um MVP via navegador pode ser util para aprender rapido, mas nao prova sozinho que a solucao telefonica esta resolvida.

## 9. Riscos operacionais

- A equipe precisar manter uma solucao mais complexa do que a plataforma atual.
- Suporte interno virar responsabilidade da MB Finance.
- Falta de clareza sobre quem monitora, corrige e melhora os agentes.
- Operadores internos precisarem de um painel novo e treinamento.
- Dificuldade para investigar problemas em chamadas reais.
- Ausencia de processo para versionar prompts e configuracoes.
- Falta de fallback humano em casos sensiveis.
- Mudanca brusca prejudicar uma operacao que hoje ja funciona.
- O MVP crescer rapido demais e virar um produto interno dificil de manter.
- Front-end proprio exigir suporte, treinamento, melhorias de UX e manutencao como qualquer sistema interno.
- Falta de dono operacional claro para prompts, configuracoes, incidentes, qualidade e custos.

Tambem existe risco de governanca. A operacao precisa definir quem pode criar agentes, alterar prompts, acessar transcricoes, ouvir audios, exportar dados, disparar automacoes e aprovar acoes sensiveis. Sem isso, a arquitetura pode ficar flexivel tecnicamente, mas fragil operacionalmente.

### Seguranca, LGPD e dados sensiveis

Uma arquitetura propria aumenta o controle, mas tambem aumenta a responsabilidade sobre dados. Antes de qualquer piloto com dados reais, a equipe precisa definir:

- quais dados sensiveis podem aparecer nas conversas;
- se audios, transcricoes, resumos e logs podem ser armazenados;
- por quanto tempo cada tipo de dado deve ficar retido;
- quem pode acessar audio, transcricao, resumo, logs tecnicos e eventos de negocio;
- como registrar auditoria de acessos, alteracoes de prompt e chamadas a ferramentas;
- quais dados podem ser enviados para provedores externos de STT, LLM e TTS;
- como tratar exclusao, mascaramento ou anonimizacao de dados quando necessario;
- quais controles sao necessarios para reduzir risco de vazamento, uso indevido ou decisao automatizada inadequada.

Esse ponto precisa ser avaliado junto com seguranca, juridico/compliance e responsaveis de negocio. Nao e apenas uma decisao tecnica.

## 10. Riscos de custo

- Reduzir assinatura da ElevenLabs, mas aumentar custo de desenvolvimento.
- Criar custo novo com STT, TTS, LLM, LiveKit, telefonia, banco, logs e observabilidade.
- Subestimar custo de manutencao e suporte.
- Latencia ou bugs gerarem retrabalho e mais horas de engenharia.
- Custo por chamada ficar maior do que o esperado por uso ineficiente de LLM ou TTS.
- Necessidade de infraestrutura mais robusta caso o volume aumente.
- Economia depender de escala, mas o uso atual ser baixo.
- Custo de construir e manter o front-end interno, a API de governanca, observabilidade, seguranca e suporte ser maior do que o previsto.
- Custo de telefonia/SIP mudar bastante a conta caso o canal principal nao seja navegador.

O custo correto a comparar nao e apenas ElevenLabs versus LiveKit. A comparacao real e:

```text
Custo atual da ElevenLabs
versus
LiveKit + STT + LLM + TTS + telefonia + infraestrutura + logs + desenvolvimento + manutencao + suporte
```

## 11. Possibilidade de abordagem hibrida

Uma abordagem hibrida parece uma alternativa prudente para avaliacao inicial.

Possibilidades:

- manter ElevenLabs para agentes em producao enquanto o MVP com LiveKit e testado;
- usar LiveKit para novos casos de uso que exigem mais controle;
- usar LiveKit na camada de tempo real, mas manter ElevenLabs como TTS;
- migrar apenas agentes simples primeiro;
- manter ElevenLabs para fluxos de maior risco ou maior dependencia operacional;
- comparar o mesmo caso de uso nas duas arquiteturas;
- usar n8n e API interna para padronizar integracoes independentemente da plataforma de voz.

A abordagem hibrida reduz risco porque evita trocar uma solucao funcional por uma arquitetura ainda nao validada.

## 12. MVP recomendado

O MVP recomendado deve ser pequeno, mensuravel e focado em aprender.

Escopo sugerido:

- um agente simples de voz em ambiente de teste;
- canal inicial via navegador, nao telefone, para reduzir complexidade;
- sala LiveKit criada pela API interna;
- token LiveKit gerado pelo back-end;
- pipeline basico STT -> LLM -> TTS;
- um prompt simples e versionado;
- uma ou duas ferramentas internas no maximo;
- registro de eventos principais da chamada;
- log de transcricao e resposta;
- logs estruturados com correlation ID por chamada;
- metricas por etapa: LiveKit, STT, LLM, TTS, API interna e n8n;
- webhook de chamada encerrada para n8n;
- tela interna minima para iniciar teste e visualizar resultado.

### Criterios mensuraveis de sucesso do MVP

Os criterios exatos precisam ser definidos com a equipe antes do teste, mas o MVP deveria medir pelo menos:

- latencia ponta a ponta por turno de fala;
- latencia separada por etapa: LiveKit, STT, LLM, TTS e API interna;
- taxa de falha por chamada e por etapa;
- qualidade da transcricao em portugues em amostras reais ou simuladas;
- qualidade percebida da voz e naturalidade da resposta;
- custo estimado por chamada e por minuto;
- tempo necessario para configurar ou alterar um agente;
- capacidade de debugar uma chamada usando logs, transcricao e correlation ID;
- numero de intervencoes manuais ou erros de ferramenta;
- esforco tecnico para manter o MVP durante o periodo de teste.

Como criterio qualitativo, o MVP deve responder se a equipe consegue operar, entender, corrigir e evoluir a solucao sem depender de tentativa e erro excessiva.

### Criterios de parada ou nao migracao

A decisao tambem precisa ter criterios claros para nao continuar. Manter ElevenLabs ou adotar apenas uma abordagem hibrida pode ser melhor se:

- o custo total estimado da arquitetura propria ficar proximo ou maior que o custo atual sem ganho claro de controle ou qualidade;
- a latencia ficar perceptivelmente pior que a solucao atual;
- a qualidade de STT ou TTS nao for aceitavel para portugues, sotaques, ruido ou chamadas reais;
- a equipe nao tiver dono claro para manutencao, suporte, observabilidade e evolucao;
- o front-end proprio exigir mais esforco do que a empresa quer assumir;
- telefonia/SIP se mostrar essencial e complexa demais para o momento;
- os riscos de seguranca, LGPD, retencao de dados ou auditoria nao estiverem bem enderecados;
- as limitacoes atuais da ElevenLabs puderem ser resolvidas com renegociacao, melhor configuracao, prompts melhores ou integracoes mais simples;
- o MVP nao demonstrar ganho pratico em custo, controle, integracao ou experiencia operacional.

Resumo dos criterios de sucesso:

- o agente consegue manter uma conversa curta com latencia aceitavel;
- a transcricao em portugues e compreensivel;
- a resposta por voz e natural o suficiente para teste interno;
- logs permitem debugar erros;
- custo por chamada pode ser estimado;
- a equipe entende o esforco necessario para evoluir;
- fica claro se vale continuar, pausar ou manter abordagem hibrida.

## 13. Perguntas para levar para a reuniao de segunda

1. Qual e o custo mensal atual da ElevenLabs?
2. Quanto do plano contratado esta sendo realmente usado?
3. Quais recursos pagos estao subutilizados?
4. Quais agentes estao em producao hoje?
5. Qual e o volume mensal de chamadas ou minutos?
6. O canal principal e telefone, navegador, WhatsApp ou outro?
7. Quais funcionalidades da ElevenLabs sao indispensaveis hoje?
8. Quais limitacoes da ElevenLabs mais incomodam a equipe?
9. O problema principal e custo, controle, integracao, qualidade ou todos juntos?
10. Existem metricas atuais de latencia, sucesso, erro e satisfacao?
11. A empresa precisa manter a mesma voz dos agentes atuais?
12. O TTS da ElevenLabs poderia continuar sendo usado em uma arquitetura hibrida?
13. Quais sistemas internos o agente precisa consultar?
14. Quais acoes o agente pode executar sozinho?
15. Quais acoes precisam de aprovacao humana?
16. O n8n ja participa de algum fluxo dos agentes atuais?
17. Existe historico de chamadas, transcricoes ou logs disponivel para analise?
18. Quais dados sensiveis aparecem nas conversas?
19. Quem seria responsavel por operar e manter a nova arquitetura?
20. Qual seria um caso de uso pequeno e seguro para MVP?
21. Qual prazo seria aceitavel para um teste tecnico?
22. Quais criterios indicariam que LiveKit vale continuar sendo estudado?
23. Quais criterios indicariam que e melhor manter ElevenLabs?
24. A empresa considera uma abordagem hibrida aceitavel?
25. Quais dados podem ser enviados para provedores externos de STT, LLM e TTS?
26. Qual politica de retencao devemos aplicar para audios, transcricoes, logs e resumos?
27. Quem pode acessar historico de chamadas, transcricoes e audios?
28. O front-end atual da ElevenLabs atende os operadores? O que faltaria em um front proprio?
29. Quais acoes precisam ser sincronas durante a chamada e quais podem ir para n8n depois?
30. O canal telefonico/SIP e requisito do MVP ou pode ficar para uma fase posterior?
31. Quais metricas minimas precisam existir desde o primeiro teste?

## 14. Recomendacao inicial

A recomendacao inicial e nao decidir por migracao total neste momento.

O caminho mais prudente e tratar LiveKit como uma hipotese tecnica a ser validada por MVP. LiveKit pode oferecer mais controle, flexibilidade e integracao, mas tambem transfere para a equipe responsabilidades que hoje provavelmente estao dentro da ElevenLabs.

Uma migracao so faria sentido se pelo menos uma destas condicoes for verdadeira:

- o custo atual da ElevenLabs for alto e comprovadamente desproporcional ao uso;
- as limitacoes da plataforma estiverem bloqueando casos de negocio importantes;
- a empresa quiser investir em uma capacidade interna de Voice AI;
- a equipe tiver capacidade de manter a arquitetura;
- o MVP provar latencia, qualidade, custo e operacao aceitaveis.

Caso contrario, a melhor opcao pode ser manter ElevenLabs, renegociar plano, reduzir desperdicio, melhorar prompts e integracoes, ou adotar uma arquitetura hibrida.

## Proximos passos

1. Confirmar dados reais de custo e uso da ElevenLabs.
2. Mapear quais agentes existem hoje e quais features eles usam.
3. Escolher um caso de uso simples para MVP.
4. Definir canal inicial do teste: navegador ou telefone.
5. Estimar provedores de STT, LLM e TTS.
6. Desenhar um fluxo tecnico minimo com LiveKit.
7. Definir politica inicial de seguranca, LGPD, retencao, auditoria e acesso a dados.
8. Definir metricas, logs estruturados e correlation ID desde o MVP.
9. Medir latencia, custo por chamada e esforco de manutencao.
10. Comparar o resultado com a operacao atual antes de recomendar migracao.
