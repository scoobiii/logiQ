# FLUXOGRAMAS COMPLETOS: PROJETO SOLAR CD01

## 1. FLUXOGRAMA DECISORES (Aprovações e Hierarquia)

```
┌─────────────────────────────────────────────────────────────────────┐
│                  FASE 0: INICIATIVA (Semana 1-2)                    │
└─────────────────────────────────────────────────────────────────────┘

[START] Oportunidade Solar Identificada (LOGIQ Platform Alert)
   │
   ▼
┌──────────────────────────────────────────┐
│ DECISOR 1: PROPERTY MANAGER (Barzel)     │ ⏱️ 2 dias
│ Responsável: João Silva (exemplo)        │
│ Ação: Análise preliminar viabilidade     │
│ Critérios:                               │
│ • Área telhado > 50.000 m²               │
│ • Estrutura suporta 15 kg/m²             │
│ • Contrato locatário > 5 anos            │
│ • OPEX energia > R$ 3M/ano               │
└──────────────────────────────────────────┘
   │
   ├─ ❌ NÃO → [Arquivar oportunidade + Log razão]
   │
   ▼ SIM
┌──────────────────────────────────────────┐
│ DECISOR 2: DIRETOR OPERAÇÕES (Barzel)   │ ⏱️ 3 dias
│ Responsável: Maria Santos                │
│ Ação: Avaliação estratégica              │
│ Documentos necessários:                  │
│ • Relatório técnico preliminar           │
│ • Carta intenção locatário (GPA)         │
│ • Análise risco (matriz 5x5)             │
│ Critérios:                               │
│ • TIR estimada > 12% aa                  │
│ • Payback < 8 anos                       │
│ • Alinhamento ESG (certificações)        │
└──────────────────────────────────────────┘
   │
   ├─ ❌ NÃO → [Feedback PM + Possível revisão]
   │
   ▼ SIM
┌──────────────────────────────────────────┐
│ DECISOR 3: CFO (Barzel)                  │ ⏱️ 5 dias
│ Responsável: Ricardo Oliveira            │
│ Ação: Análise financeira profunda        │
│ Documentos necessários:                  │
│ • Modelo financeiro (Excel 15 anos)      │
│ • Estrutura captação (CRI/Cotas)         │
│ • Impacto DY e P/VP                      │
│ • Análise sensibilidade (3 cenários)     │
│ Critérios:                               │
│ • WACC < TIR projeto                     │
│ • LTV pós-emissão < 50%                  │
│ • DSCR > 1,3x                            │
│ • Covenant compliance                    │
└──────────────────────────────────────────┘
   │
   ├─ ❌ NÃO → [Reestruturar financiamento]
   │
   ▼ SIM
┌──────────────────────────────────────────┐
│ DECISOR 4: COMITÊ INVESTIMENTOS          │ ⏱️ 7 dias
│ Membros: CEO + CFO + CIO + 2 Externos    │
│ Ação: Aprovação colegiada                │
│ Documentos necessários:                  │
│ • Investment memo (20 páginas)           │
│ • Due diligence técnica (engenharia)     │
│ • Due diligence legal (contratos)        │
│ • Parecer consultoria externa (CBRE)     │
│ Votação: Maioria simples (3/5)           │
└──────────────────────────────────────────┘
   │
   ├─ ❌ NÃO → [Revisar ou Arquivar definitivo]
   │
   ▼ SIM
┌──────────────────────────────────────────┐
│ DECISOR 5: CONSELHO ADMINISTRATIVO       │ ⏱️ 14 dias
│ Membros: 5 conselheiros (Barzel + FII)   │
│ Ação: Ratificação estratégica            │
│ Documentos necessários:                  │
│ • Ata comitê investimentos               │
│ • Relatório impacto stakeholders         │
│ • Plano comunicação (RI)                 │
│ Votação: 2/3 (4/5 conselheiros)          │
└──────────────────────────────────────────┘
   │
   ├─ ❌ NÃO → [Rare case - Revisão governança]
   │
   ▼ SIM
┌──────────────────────────────────────────┐
│ DECISOR 6: ASSEMBLEIA COTISTAS (FII)     │ ⏱️ 45 dias
│ Quórum: 25% cotas presentes              │
│ Ação: Aprovação emissão + projeto        │
│ Documentos necessários:                  │
│ • Edital convocação (publicado 30d antes)│
│ • Proposta emissão cotas/CRI             │
│ • Laudo avaliação independente           │
│ • Apresentação executiva (roadshow)      │
│ Votação: Maioria simples (50% + 1)       │
└──────────────────────────────────────────┘
   │
   ├─ ❌ NÃO → [Fim projeto OU Reestruturar]
   │
   ▼ SIM
┌──────────────────────────────────────────┐
│ DECISOR 7: CVM (Regulador)               │ ⏱️ 60 dias
│ Ação: Registro emissão                   │
│ Documentos necessários:                  │
│ • Prospecto definitivo                   │
│ • Demonstrações financeiras auditadas    │
│ • Parecer jurídico                       │
│ • Comprovante assembleia                 │
│ Análise: Conformidade regulatória        │
└──────────────────────────────────────────┘
   │
   ├─ ❌ NÃO → [Complementar documentação]
   │
   ▼ SIM
┌──────────────────────────────────────────┐
│ DECISOR 8: INVESTIDORES (Mercado)        │ ⏱️ 14 dias
│ Ação: Subscrição cotas/CRI               │
│ Análise:                                 │
│ • Rating (Fitch AAA)                     │
│ • Yield vs alternativas                  │
│ • Due diligence própria                  │
│ Resultado: Book building                 │
└──────────────────────────────────────────┘
   │
   ├─ Demanda < Oferta ❌ → [Repricing ou Cancelar]
   │
   ▼ Demanda ≥ Oferta ✅
┌──────────────────────────────────────────┐
│ DECISOR 9: EPC CONTRACTOR (Canadian)     │ ⏱️ 30 dias
│ Ação: Assinatura contrato turnkey        │
│ Documentos necessários:                  │
│ • PO (Purchase Order) R$ 52M             │
│ • Garantia performance bond (10%)        │
│ • Cronograma aprovado                    │
│ • Seguros contratados                    │
└──────────────────────────────────────────┘
   │
   ▼
┌──────────────────────────────────────────┐
│ DECISOR 10: ANEEL (Homologação)          │ ⏱️ 90 dias
│ Ação: Registro geração distribuída       │
│ Documentos necessários:                  │
│ • Projeto elétrico aprovado              │
│ • ART (Anotação Resp. Técnica) CREA      │
│ • Parecer acesso Enel (distribuidora)    │
│ • Certificados equipamentos (Inmetro)    │
└──────────────────────────────────────────┘
   │
   ▼
[INÍCIO OBRA] → Vide Cronograma Físico-Financeiro


┌─────────────────────────────────────────────────────────────────────┐
│                    RESUMO TIMELINE APROVAÇÕES                        │
├─────────────────────────────────────────────────────────────────────┤
│ Property Manager → Diretor Ops:      2 semanas                      │
│ Diretor Ops → CFO:                   1 semana                       │
│ CFO → Comitê Investimentos:          2 semanas                      │
│ Comitê → Conselho:                   2 semanas                      │
│ Conselho → Assembleia:               6 semanas (convocação 30d)     │
│ Assembleia → CVM:                    8 semanas (registro)           │
│ CVM → Distribuição:                  2 semanas (roadshow)           │
│ Distribuição → EPC:                  4 semanas (contrato)           │
│ EPC → ANEEL:                         12 semanas (paralelo obra)     │
│                                                                      │
│ TOTAL CRÍTICO: 22 semanas (5,5 meses) até início obra               │
└─────────────────────────────────────────────────────────────────────┘
```

---

## 2. FLUXOGRAMA DOCUMENTOS E CONTRATOS

```
┌─────────────────────────────────────────────────────────────────────┐
│              MATRIZ DE DOCUMENTOS POR FASE (67 docs)                 │
└─────────────────────────────────────────────────────────────────────┘

FASE A: ESTUDOS PRELIMINARES (Semana 1-4)
════════════════════════════════════════════════════════════════

📄 A01 - Relatório Técnico Preliminar
   ├─ Responsável: Barzel Engenharia
   ├─ Conteúdo: Análise telhado, área útil, sombreamento
   ├─ Prazo: 7 dias
   └─ Aprovador: Property Manager ✍️

📄 A02 - Carta Intenção Locatário (GPA)
   ├─ Responsável: GPA Facilities
   ├─ Conteúdo: Concordância instalação, uso energia
   ├─ Prazo: 5 dias
   └─ Assinaturas: GPA CFO + Barzel Diretor Ops ✍️✍️

📄 A03 - Estudo Viabilidade Financeira (Preliminar)
   ├─ Responsável: Barzel CFO
   ├─ Conteúdo: TIR, VPL, Payback (básico)
   ├─ Prazo: 3 dias
   └─ Aprovador: Diretor Operações ✍️

📄 A04 - Matriz Riscos (5x5)
   ├─ Responsável: Comitê Investimentos
   ├─ Conteúdo: 15 riscos identificados + mitigação
   ├─ Prazo: 5 dias
   └─ Aprovador: CIO (Chief Investment Officer) ✍️


FASE B: DUE DILIGENCE (Semana 5-10)
════════════════════════════════════════════════════════════════

📄 B01 - Laudo Estrutural Telhado
   ├─ Responsável: Bureau Veritas (consultoria)
   ├─ Conteúdo: Capacidade carga, reforços necessários
   ├─ Prazo: 14 dias
   ├─ Custo: R$ 80k
   └─ Aprovador: Engenheiro civil (ART CREA) ✍️

📄 B02 - Levantamento Topográfico
   ├─ Responsável: Geotec (topografia)
   ├─ Conteúdo: Curvas nível, coordenadas GPS, drenagem
   ├─ Prazo: 7 dias
   └─ Formato: AutoCAD DWG + Memorial descritivo

📄 B03 - Estudo Sombreamento (PVSyst)
   ├─ Responsável: Canadian Solar (pré-venda)
   ├─ Conteúdo: Simulação anual, perdas, otimização layout
   ├─ Prazo: 10 dias
   └─ Software: PVSyst 7.2 (padrão mercado)

📄 B04 - Análise Jurídica Contratos
   ├─ Responsável: Mattos Filho Advogados
   ├─ Conteúdo: Review contrato locação GPA, regulamento FII
   ├─ Prazo: 21 dias
   ├─ Custo: R$ 120k
   └─ Parecer: 45 páginas + memo executivo

📄 B05 - Due Diligence Ambiental
   ├─ Responsável: ERM Brasil
   ├─ Conteúdo: Fase I (histórico), licenças, passivos
   ├─ Prazo: 30 dias
   ├─ Custo: R$ 60k
   └─ Resultado: Nenhum passivo identificado ✅

📄 B06 - Modelo Financeiro Definitivo
   ├─ Responsável: Barzel CFO + LOGIQ
   ├─ Conteúdo: Excel 200 linhas, 15 anos, 3 cenários
   ├─ Prazo: 14 dias
   └─ Validação: Deloitte (auditoria externa) ✍️

📄 B07 - Laudo Avaliação Independente
   ├─ Responsável: CBRE Valuation
   ├─ Conteúdo: Valor ativo pré/pós solar (R$ 158M → R$ 188M)
   ├─ Prazo: 21 dias
   ├─ Custo: R$ 90k
   └─ Metodologia: Renda (Cap Rate) + Comparativo


FASE C: ESTRUTURAÇÃO FINANCEIRA (Semana 11-20)
════════════════════════════════════════════════════════════════

📄 C01 - Term Sheet CRI
   ├─ Responsável: BTG Pactual
   ├─ Conteúdo: Termos preliminares (taxa, prazo, garantias)
   ├─ Prazo: 7 dias
   └─ Assinaturas: BTG + Barzel CFO ✍️✍️ (não vinculante)

📄 C02 - Contrato Securitizadora (CRI)
   ├─ Responsável: Gaia Securitizadora
   ├─ Conteúdo: Emissão R$ 40M, remuneração 0,5% aa
   ├─ Prazo: 14 dias
   └─ Assinaturas: Gaia CEO + Barzel CFO + Advogados ✍️✍️✍️

📄 C03 - Prospecto Preliminar CRI
   ├─ Responsável: Mattos Filho + BTG
   ├─ Conteúdo: 150 páginas (riscos, financeiro, legal)
   ├─ Prazo: 30 dias
   └─ Revisões: 3 versões até definitivo

📄 C04 - Rating Report (Fitch)
   ├─ Responsável: Fitch Ratings Brasil
   ├─ Conteúdo: Análise crédito, nota AAA(bra)
   ├─ Prazo: 21 dias
   ├─ Custo: R$ 160k
   └─ Apresentação: Comitê rating (defesa oral)

📄 C05 - Second Party Opinion (ISS ESG)
   ├─ Responsável: ISS ESG
   ├─ Conteúdo: Certificação "Green Bond" compliance
   ├─ Prazo: 14 dias
   ├─ Custo: R$ 200k
   └─ Padrão: Climate Bonds Initiative

📄 C06 - Edital Convocação Assembleia
   ├─ Responsável: Administrador Fiduciário (Ouribank)
   ├─ Conteúdo: Pauta emissão, data/local, docs anexos
   ├─ Prazo: Publicar 30 dias antes assembleia
   ├─ Veículos: DOU + Valor Econômico + site B3
   └─ Custo: R$ 15k (publicações)

📄 C07 - Apresentação Assembleia (Pitch Deck)
   ├─ Responsável: Barzel RI + LOGIQ
   ├─ Conteúdo: 40 slides (projeto, financeiro, benefícios)
   ├─ Prazo: 10 dias antes assembleia
   └─ Formato: PDF + vídeo 10min (híbrido)

📄 C08 - Ata Assembleia Geral
   ├─ Responsável: Secretário assembleia
   ├─ Conteúdo: Presença, votação, aprovação (82% SIM)
   ├─ Prazo: 5 dias pós-assembleia
   └─ Registro: Cartório + CVM + B3 ✍️ (tabelião)

📄 C09 - Prospecto Definitivo CRI
   ├─ Responsável: Mattos Filho
   ├─ Conteúdo: Incorpora ata assembleia + ajustes CVM
   ├─ Prazo: 7 dias pós-assembleia
   └─ Páginas: 180 (final)

📄 C10 - Formulário Referência CVM
   ├─ Responsável: Ouribank (Administrador)
   ├─ Conteúdo: FRE (ITR atualizado, fatos relevantes)
   ├─ Prazo: 3 dias antes protocolo CVM
   └─ Sistema: CVMWeb (upload XML)


FASE D: APROVAÇÕES REGULATÓRIAS (Semana 21-28)
════════════════════════════════════════════════════════════════

📄 D01 - Protocolo CVM (Emissão)
   ├─ Responsável: Coordenador líder (BTG)
   ├─ Conteúdo: Prospecto + docs societários + atas
   ├─ Prazo: 1 dia (eletrônico)
   └─ Acompanhamento: 45-60 dias até deferimento

📄 D02 - Ofício CVM (Solicitação Complementação)
   ├─ Responsável: CVM Superintendência
   ├─ Conteúdo: 12 questionamentos (típico)
   ├─ Prazo: 15 dias após protocolo
   └─ Resposta: 10 dias úteis (prazo regulatório)

📄 D03 - Respostas CVM (Complementação)
   ├─ Responsável: Mattos Filho + Barzel
   ├─ Conteúdo: 85 páginas detalhando respostas
   ├─ Prazo: 8 dias (dentro do prazo 10d)
   └─ Anexos: 15 documentos adicionais

📄 D04 - Deferimento CVM
   ├─ Responsável: CVM (órgão regulador)
   ├─ Conteúdo: Registro definitivo emissão
   ├─ Prazo: 45 dias após protocolo (se sem ressalvas)
   └─ Publicação: DOU + site CVM

📄 D05 - Contrato EPC (Canadian Solar)
   ├─ Responsável: Barzel Procurement + Canadian
   ├─ Conteúdo: Turnkey R$ 52M, prazo 12 meses, warranty 25a
   ├─ Prazo: Assinatura 5 dias pós-deferimento CVM
   └─ Assinaturas: Canadian CEO Brazil + Barzel CEO ✍️✍️
   └─ Garantias: Performance bond 10% (R$ 5,2M Bradesco)

📄 D06 - Projeto Executivo Elétrico
   ├─ Responsável: Canadian Solar Engineering
   ├─ Conteúdo: Unifilar, memoriais, cálculos (ABNT)
   ├─ Prazo: 30 dias pós-assinatura EPC
   ├─ Páginas: 250+ desenhos AutoCAD
   └─ ART: Eng° Eletricista CREA-SP (R$ 2k) ✍️

📄 D07 - Aprovação Bombeiros (AVCB)
   ├─ Responsável: Corpo Bombeiros SP
   ├─ Conteúdo: Análise carga incêndio adicional
   ├─ Prazo: 45 dias
   ├─ Custo: R$ 8k (taxa)
   └─ Vistoria: Presencial (agendada)

📄 D08 - Parecer Acesso Enel
   ├─ Responsável: Enel Distribuição SP
   ├─ Conteúdo: Aprovação ponto conexão 13,8kV
   ├─ Prazo: 60 dias
   ├─ Custo: R$ 45k (análise + eventual upgrade trafo)
   └─ Validade: 2 anos

📄 D09 - Registro ANEEL (Micro-geração)
   ├─ Responsável: Canadian (via portal ANEEL)
   ├─ Conteúdo: SIGA (Sistema Informações Geração)
   ├─ Prazo: 30 dias
   └─ Código gerador: GD.SP.XXXX.YYYY-Z (exemplo)


FASE E: CONSTRUÇÃO (Semana 29-72)
════════════════════════════════════════════════════════════════

📄 E01 - Diário de Obras (Digital)
   ├─ Responsável: Canadian Site Manager
   ├─ Conteúdo: Progresso diário, fotos, pendências
   ├─ Prazo: Atualizado diariamente (300 dias)
   ├─ Plataforma: Procore (software gestão obra)
   └─ Acesso: Barzel, GPA, LOGIQ (read-only)

📄 E02 - Relatórios Progresso Mensal
   ├─ Responsável: Canadian PMO
   ├─ Conteúdo: Avanço físico (%), desvios, forecast
   ├─ Prazo: Todo dia 5 (mês anterior)
   └─ Apresentação: Reunião steering committee

📄 E03 - Notas Fiscais Equipamentos (1.200 NFs)
   ├─ Responsável: Canadian Procurement
   ├─ Conteúdo: Painéis, inversores, estruturas, cabos
   ├─ Prazo: Conforme entrega (4-10 meses)
   └─ Validação: Barzel contabilidade (conferência)

📄 E04 - Certificados Inmetro (Equipamentos)
   ├─ Responsável: Fabricantes (Jinko, Sungrow, CATL)
   ├─ Conteúdo: Conformidade portaria Inmetro 357/2014
   ├─ Prazo: Antes instalação (apresentar ANEEL)
   └─ Quantidade: 3 certificados (painéis, inversores, BESS)

📄 E05 - Apólices Seguro (3 tipos)
   ├─ Responsável: Marsh Brasil (broker)
   ├─ Tipos:
   │   ├─ Riscos Engenharia (construção): R$ 180k/ano
   │   ├─ RC Geral (responsabilidade civil): R$ 120k/ano
   │   └─ Performance (garantia EPC): R$ 5,2M (bond)
   ├─ Prazo: Antes início obras
   └─ Seguradoras: Swiss Re + Zurich + Bradesco

📄 E06 - Termos Recebimento Provisório (Etapas)
   ├─ Responsável: Barzel Engenharia + Canadian
   ├─ Conteúdo: 5 etapas (fundação, estrutura, painéis, elétrica, BESS)
   ├─ Prazo: Ao fim de cada etapa (pontos pagamento)
   └─ Assinaturas: Eng° residente Barzel + Canadian PM ✍️✍️

📄 E07 - Relatórios Comissionamento
   ├─ Responsável: Canadian Commissioning Team
   ├─ Conteúdo: Testes isolação, hi-pot, curva I-V, load test
   ├─ Prazo: Semana 69-72 (último mês obra)
   └─ Páginas: 180 (protocolos + resultados)

📄 E08 - Vistoria ANEEL (Inspeção Final)
   ├─ Responsável: ANEEL Fiscalização SP
   ├─ Conteúdo: Conformidade projeto vs executado
   ├─ Prazo: Agendar após comissionamento
   ├─ Duração: 1 dia (presencial 3 fiscais)
   └─ Resultado: Habilitação operação comercial

📄 E09 - Termo Recebimento Definitivo (COD)
   ├─ Responsável: Barzel CEO
   ├─ Conteúdo: Aceite final obra + início warranty
   ├─ Prazo: 7 dias pós-vistoria ANEEL
   ├─ Data: 18/10/2026 (Commercial Operation Date)
   └─ Pagamento final: R$ 5,2M (10% retido) ✍️ → Canadian


FASE F: OPERAÇÃO (Mensal - 25 anos)
════════════════════════════════════════════════════════════════

📄 F01 - Relatório O&M Mensal
   ├─ Responsável: Canadian (Y1-5) → Ecori (Y6+)
   ├─ Conteúdo: Geração kWh, incidentes, manutenções
   ├─ Prazo: Todo dia 10 (mês anterior)
   └─ Formato: PDF + dashboard LOGIQ Platform

📄 F02 - Fatura Venda Energia (CCEE)
   ├─ Responsável: LOGIQ Trading Desk
   ├─ Conteúdo: MWh vendidos, preço, liquidação
   ├─ Prazo: Toda sexta-feira (semanal)
   └─ Destinatário: Barzel contabilidade (receita)

📄 F03 - Certificados I-REC
   ├─ Responsável: I-REC Registry
   ├─ Conteúdo: 9.214 certificados/ano (1 por MWh)
   ├─ Prazo: Mensal (após medição)
   └─ Comprador: Google Brasil (contrato anual)

📄 F04 - Demonstrativos Financeiros (FII)
   ├─ Responsável: Ouribank (Administrador)
   ├─ Conteúdo: Balanço, DRE, fluxo caixa (incorpora solar)
   ├─ Prazo: Mensal (até dia 15)
   └─ Auditoria: Trimestral (PwC)

📄 F05 - Informe Rendimentos (Cotistas)
   ├─ Responsável: Barzel RI
   ├─ Conteúdo: DY, fatos relevantes, perspectivas
   ├─ Prazo: Mensal + anual (IR)
   └─ Canais: Email + site + app B3


┌─────────────────────────────────────────────────────────────────────┐
│         TOTAL DOCUMENTOS: 67 (50 páginas médio = 3.350 páginas)     │
│         Assinaturas físicas: 23 contratos (47 assinaturas totais)   │
│         Certificações digitais: 15 (ICP-Brasil padrão)              │
│         Custos documentação: R$ 890k (2,3% CAPEX - normal setor)    │
└─────────────────────────────────────────────────────────────────────┘
```

---

## 3. FLUXOGRAMA ASSINATURAS (Sequência e Responsáveis)

```
┌────────────────────────────────────────────────────────────────────┐
│           CADEIA DE ASSINATURAS (Ordem Cronológica)                │
└────────────────────────────────────────────────────────────────────┘

SEMANA 1-2: Aprovações Internas
═══════════════════════════════════════════════════════════════

🖊️ #001 - Relatório Técnico Preliminar
    ├─ Preparador: Eng° João Silva (Barzel) 
    ├─ Revisor: Diretor Eng° Maria Santos (Barzel) ✍️
    ├─ Aprovador: Property Manager (Barzel) ✍️
    └─ Data: 15/01/2025

🖊️ #002 - Carta Intenção GPA
    ├─ Redator: Facilities Manager GPA (Paulo Costa)
    ├─ Revisor Jurídico: GPA Legal (Dr. Ana Lima) ✍️
    ├─ Signatário GPA: CFO GPA (Roberto Mendes) ✍️
    ├─ Signatário Barzel: Diretor Ops (Maria Santos) ✍️
    └─ Data: 20/01/2025

🖊️ #003 - NDA (Non-Disclosure Agreement)
    ├─ Partes: Barzel ↔ Canadian Solar (cotação)
    ├─ Signatários: 
    │   ├─ Barzel CEO (Fernando Rocha) ✍️
    │   └─ Canadian CEO Brazil (Richard Wong) ✍️
    └─ Data: 22/01/2025


SEMANA 3-6: Due Diligence Técnica
═══════════════════════════════════════════════════════════════

🖊️ #004 - Contrato Bureau Veritas (Laudo Estrutural)
    ├─ Valor: R$ 80k
    ├─ Signatários:
    │   ├─ Bureau Veritas Dir Comercial (Jean Dupont) ✍️
    │   └─ Barzel Procurement (Carla Souza) ✍️
    └─ Data: 28/01/2025

🖊️ #005 - ART CREA-SP (Laudo Estrutural)
    ├─ Responsável Técnico: Eng° Civil João Martins
    ├─ CREA: SP-123456/D
    ├─ Assinatura digital: Certificado ICP-Brasil ✍️
    └─ Data: 10/02/2025

🖊️ #006 - Contrato CBRE (Laudo Avaliação)
    ├─ Valor: R$ 90k
    ├─ Signatários:
    │   ├─ CBRE Managing Director (Thomas Green) ✍️
    │   └─ Barzel CFO (Ricardo Oliveira) ✍️
    └─ Data: 05/02/2025


SEMANA 7-10: Estruturação Financeira
═══════════════════════════════════════════════════════════════

🖊️ #007 - Mandato Coordenação (BTG Pactual)
    ├─ Tipo: Mandato exclusivo 180 dias
    ├─ Fee: 2,5% (R$ 1,45M sobre R$ 58M)
    ├─ Signatários:
    │   ├─ BTG Managing Director (André Esteves Jr) ✍️
    │   └─ Barzel CEO (Fernando Rocha) ✍️
    └─ Data: 15/02/2025

🖊️ #008 - Contrato Mattos Filho Advogados
    ├─ Escopo: Estruturação + Regulatório CVM
    ├─ Valor: R$ 400k (fixo) + R$ 50k (success fee)
    ├─ Signatários:
    │   ├─ Mattos Filho Sócio (Dr. Carlos Matos) ✍️
    │   └─ Barzel CFO (Ricardo Oliveira) ✍️
    └─ Data: 18/02/2025

🖊️ #009 - Contrato Fitch Ratings
    ├─ Rating inicial: AAA(bra) esperado
    ├─ Valor: R$ 160k (setup) + R$ 40k/ano (surveillance)
    ├─ Signatários:
    │   ├─ Fitch Director (Rogério Santos) ✍️
    │   └─ Barzel CFO (Ricardo Oliveira) ✍️
    └─ Data: 20/02/2025

🖊️ #010 - Contrato ISS ESG (SPO Verde)
    ├─ Certificação: Green Bond Principles
    ├─ Valor: R$ 200k
    ├─ Signatários:
    │   ├─ ISS ESG VP (Dr. Klaus Schmidt) ✍️
    │   └─ Barzel ESG Officer (Beatriz Lima) ✍️
    └─ Data: 25/02/2025


SEMANA 11-14: Preparação Assembleia
═══════════════════════════════════════════════════════════════

🖊️ #011 - Investment Memo (Interno)
    ├─ Preparador: Barzel CFO
    ├─ Aprovação Comitê Investimentos:
    │   ├─ CEO (Fernando Rocha) ✍️
    │   ├─ CFO (Ricardo Oliveira) ✍️
    │   ├─ CIO (Patricia Alves) ✍️
    │   ├─ Conselheiro Externo 1 (Luiz Barsi) ✍️
    │   └─ Conselheiro Externo 2 (Dr. José Silva) ✍️
    ├─ Quórum: 5/5 (unanimidade!)
    └─ Data: 10/03/2025

🖊️ #012 - Ata Comitê Investimentos
    ├─ Secretário: Jurídico Barzel (Dr. Marcos Pinto)
    ├─ Lavrado por: Tabelião (reconhecimento firmas)
    ├─ Registro: Junta Comercial SP
    └─ Data: 12/03/2025

🖊️ #013 - Aprovação Conselho Administrativo
    ├─ Convocação: 7 dias antes (email registrado)
    ├─ Votação: 5/5 conselheiros (unanimidade)
    ├─ Assinaturas Ata:
    │   ├─ Presidente Conselho (Antonio Barzel) ✍️
    │   ├─ Conselheiro 1 (Maria Helena Costa) ✍️
    │   ├─ Conselheiro 2 (Roberto Tavares) ✍️
    │   ├─ Conselheiro 3 (Dra. Silvia Ramos) ✍️
    │   └─ Conselheiro 4 (Prof. João Mendes) ✍️
    └─ Data: 20/03/2025

🖊️ #014 - Edital Convocação Assembleia
    ├─ Publicações (3x com 5 dias intervalo):
    │   ├─ DOU (Diário Oficial União)
    │   ├─ Valor Econômico
    │   └─ Site B3 + site FII
    ├─ Responsável: Ouribank (Administrador)
    ├─ Assinatura: Dir Juridico Ouribank (Dra. Lucia Martins) ✍️
    └─ Datas: 22/03, 27/03, 01/04/2025


SEMANA 15-18: Assembleia de Cotistas
═══════════════════════════════════════════════════════════════

🖊️ #015 - Procurações Cotistas (Registro votos)
    ├─ Formato: Eletrônico (B3 sistema)
    ├─ Total cotas: 10.000.000
    ├─ Presentes: 3.200.000 cotas (32% presença - bom!)
    ├─ Assinaturas digitais: 847 cotistas ✍️ (ICP-Brasil)
    └─ Data: 15/04/2025 (prazo até 17h)

🖊️ #016 - Ata Assembleia Geral Extraordinária
    ├─ Presença: 32% (quórum atingido: min 25%)
    ├─ Pauta: Emissão R$ 58M (CRI + Cotas) + Projeto Solar
    ├─ Votação: 
    │   ├─ SIM: 2.624.000 cotas (82%)
    │   ├─ NÃO: 448.000 cotas (14%)
    │   └─ ABSTENÇÃO: 128.000 cotas (4%)
    ├─ Resultado: APROVADO ✅
    ├─ Assinaturas:
    │   ├─ Presidente Mesa (Ouribank) ✍️
    │   ├─ Secretário Mesa (Advogado Barzel) ✍️
    │   ├─ 2 Cotistas testemunhas ✍️✍️
    │   └─ Tabelião (lavrado em cartório) ✍️
    └─ Data: 15/04/2025


SEMANA 19-26: Registro CVM
═══════════════════════════════════════════════════════════════

🖊️ #017 - Prospecto Definitivo CRI
    ├─ Páginas: 180
    ├─ Revisões: 5 versões (v.1.0 → v.5.0 final)
    ├─ Assinaturas:
    │   ├─ Barzel CEO (Fernando Rocha) ✍️
    │   ├─ Barzel CFO (Ricardo Oliveira) ✍️
    │   ├─ Ouribank Administrador (José Carlos Nunes) ✍️
    │   ├─ BTG Coordenador (André Esteves Jr) ✍️
    │   ├─ Gaia Securitizadora CEO (Marcos Viana) ✍️
    │   ├─ Mattos Filho Sócio (Dr. Carlos Matos) ✍️
    │   └─ PwC Auditor Independente (Sócio Ricardo Luz) ✍️
    └─ Data: 20/04/2025

🖊️ #018 - Protocolo CVM (Requerimento)
    ├─ Sistema: CVMWeb (eletrônico)
    ├─ Documentos anexos: 47 PDFs (1,2 GB)
    ├─ Responsável: BTG Compliance Officer
    ├─ Certificado digital: ICP-Brasil A3 ✍️
    └─ Data: 22/04/2025
    └─ Protocolo: CVM/SRE/2025/XXX

🖊️ #019 - Respostas Ofício CVM
    ├─ Ofício CVM nº: 45/2025/CVM/SRE/GER-1
    ├─ Questionamentos: 12 itens
    ├─ Respostas: 85 páginas + 15 anexos
    ├─ Assinatura: Mattos Filho + Barzel CFO ✍️✍️
    └─ Data: 15/05/2025 (dentro prazo 10 dias úteis)

🖊️ #020 - Ofício Deferimento CVM
    ├─ Tipo: Registro automático (sem exigências)
    ├─ Nº Registro: CVM/SRE/CRI/2025/YYYY
    ├─ Assinatura: Superintendente CVM ✍️
    ├─ Publicação: DOU 05/06/2025
    └─ Data: 03/06/2025


SEMANA 27-28: Distribuição (Book Building)
═══════════════════════════════════════════════════════════════

🖊️ #021 - Boletim Subscrição (Investidores)
    ├─ Total: 420 boletins (investidores institucionais)
    ├─ Demanda: R$ 87M (oversubscription 2,2x)
    ├─ Alocação: R$ 40M (rateio proporcional)
    ├─ Assinaturas digitais: 420 investidores ✍️
    └─ Data: 08-12/06/2025 (5 dias úteis)

🖊️ #022 - Contrato Distribuição (Anúncio Início)
    ├─ Coordenador: BTG Pactual
    ├─ Consorciados: XP, Itaú BBA
    ├─ Comissão: 2,5% (R$ 1M rateado)
    ├─ Assinaturas:
    │   ├─ BTG (líder) ✍️
    │   ├─ XP ✍️
    │   ├─ Itaú BBA ✍️
    │   └─ Barzel/Ouribank ✍️
    └─ Data: 05/06/2025

🖊️ #023 - Anúncio Encerramento (Fato Relevante)
    ├─ Conteúdo: Resultado distribuição, uso recursos
    ├─ Publicação: Site CVM + B3 + Valor Econômico
    ├─ Assinatura: Barzel DRI (Diretor RI) ✍️
    └─ Data: 15/06/2025


SEMANA 29: Contrato EPC & Início Obra
═══════════════════════════════════════════════════════════════

🖊️ #024 - Contrato EPC Turnkey (PRINCIPAL)
    ├─ Partes: Barzel Logística FIP ↔ Canadian Solar Brasil
    ├─ Valor: R$ 52.000.000,00
    ├─ Prazo: 365 dias corridos (COD: 18/06/2026)
    ├─ Escopo: Design + Procurement + Construction + Commissioning
    ├─ Penalidades: 0,5%/dia atraso (max 10% valor)
    ├─ Garantias:
    │   ├─ Performance bond: 10% (R$ 5,2M)
    │   ├─ Warranty: 25 anos painéis, 10 anos inversores
    │   └─ Disponibilidade: 97% ano 1-5
    ├─ Condições pagamento:
    │   ├─ Sinal: 10% assinatura (R$ 5,2M)
    │   ├─ Mobilização: 20% M1 (R$ 10,4M)
    │   ├─ Procurement: 40% M3 (R$ 20,8M)
    │   ├─ Construção: 20% progressivo M6-M11 (R$ 10,4M)
    │   └─ COD: 10% aceite final (R$ 5,2M)
    ├─ Assinaturas (cerimônia presencial):
    │   ├─ Barzel CEO (Fernando Rocha) ✍️
    │   ├─ Barzel CFO (Ricardo Oliveira) ✍️
    │   ├─ Barzel Jurídico (Dr. Marcos Pinto) ✍️
    │   ├─ Canadian CEO Brazil (Richard Wong) ✍️
    │   ├─ Canadian CFO LATAM (Jennifer Lee) ✍️
    │   ├─ Canadian Legal (Dr. Paulo Andrade) ✍️
    │   ├─ Testemunhas (2 advogados) ✍️✍️
    │   └─ Reconhecimento firmas (Cartório SP) ✍️
    ├─ Idiomas: Português (oficial) + Inglês (referência)
    ├─ Lei aplicável: Brasil (foro SP)
    ├─ Arbitragem: CAM-CCBC (se litígio > R$ 5M)
    └─ Data: 18/06/2025

🖊️ #025 - Ordem de Serviço (Kick-off Obra)
    ├─ Emitido por: Barzel Project Manager
    ├─ Destinatário: Canadian Site Manager
    ├─ Conteúdo: Autorização mobilização canteiro
    ├─ Assinaturas:
    │   ├─ Barzel PM (Eng° Carlos Dias) ✍️
    │   └─ Canadian SM (Eng° Rafael Torres) ✍️
    └─ Data: 20/06/2025

🖊️ #026 - ART CREA-SP (Projeto Executivo)
    ├─ Responsável: Canadian Eng° Eletricista
    ├─ CREA: SP-234567/D
    ├─ Assinatura digital ✍️
    └─ Data: 15/07/2025

🖊️ #027 - Apólice Riscos Engenharia
    ├─ Seguradora: Swiss Re Brasil
    ├─ Importância segurada: R$ 60M (full replacement)
    ├─ Prêmio: R$ 180k/ano
    ├─ Vigência: 20/06/2025 - 20/06/2026
    ├─ Assinaturas:
    │   ├─ Swiss Re (Subscritor) ✍️
    │   ├─ Marsh (Corretor) ✍️
    │   └─ Barzel (Segurado) ✍️
    └─ Data: 19/06/2025


SEMANA 30-70: Execução Obra (Docs Recorrentes)
═══════════════════════════════════════════════════════════════

🖊️ #028-#032 - Termos Medição (5 etapas)
    ├─ Etapa 1: Fundações/Estruturas (10%)
    │   ├─ Valor: R$ 5,2M
    │   └─ Data: 20/08/2025 ✍️✍️
    ├─ Etapa 2: Painéis (30%)
    │   ├─ Valor: R$ 15,6M
    │   └─ Data: 20/10/2025 ✍️✍️
    ├─ Etapa 3: Inversores/Elétrica (20%)
    │   ├─ Valor: R$ 10,4M
    │   └─ Data: 20/01/2026 ✍️✍️
    ├─ Etapa 4: BESS (20%)
    │   ├─ Valor: R$ 10,4M
    │   └─ Data: 20/03/2026 ✍️✍️
    └─ Etapa 5: Comissionamento (10%)
        ├─ Valor: R$ 5,2M
        └─ Data: 18/05/2026 ✍️✍️

🖊️ #033-#037 - Notas Fiscais (Principais)
    ├─ Painéis (Jinko Solar): NF R$ 28M (ago/2025)
    ├─ Inversores (Sungrow): NF R$ 8M (set/2025)
    ├─ BESS (CATL): NF R$ 7M (fev/2026)
    ├─ Estruturas (Alumínio): NF R$ 5M (ago/2025)
    └─ Cada NF assinada digitalmente (XML NF-e)


SEMANA 71-72: Comissionamento & Aceite
═══════════════════════════════════════════════════════════════

🖊️ #038 - Relatório Comissionamento
    ├─ Preparador: Canadian Commissioning Lead
    ├─ Páginas: 180 (testes + fotos + medições)
    ├─ Testes realizados:
    │   ├─ Isolação (megger): ✅ Pass
    │   ├─ Hi-pot (tensão): ✅ Pass
    │   ├─ Curva I-V (100 painéis amostra): ✅ Pass
    │   ├─ Load test inversores: ✅ Pass (100% capacity)
    │   └─ BESS cycles: ✅ Pass (100 charge/discharge)
    ├─ Assinaturas:
    │   ├─ Canadian Commissioning Lead ✍️
    │   └─ Barzel Eng° Eletricista (fiscal) ✍️
    └─ Data: 10/06/2026

🖊️ #039 - Laudo Vistoria ANEEL
    ├─ Fiscal ANEEL: Eng° José Santos (ANEEL-SP)
    ├─ Data vistoria: 15/06/2026 (1 dia, 8h-17h)
    ├─ Resultado: APROVADO (sem ressalvas) ✅
    ├─ Não-conformidades: 0
    ├─ Assinatura: Fiscal ANEEL ✍️
    └─ Data laudo: 17/06/2026

🖊️ #040 - Habilitação Operação Comercial (HOC)
    ├─ Emitido por: ANEEL
    ├─ Código usina: UFV.SP.CD01.7425kWp
    ├─ Vigência: Indeterminada (enquanto operar)
    ├─ Assinatura: Superintendente ANEEL-SP ✍️
    └─ Data: 18/06/2026 (COD! 🎉)

🖊️ #041 - Termo Aceite Definitivo (TAD)
    ├─ Conteúdo: Obra entregue conforme especificado
    ├─ Início warranty: 18/06/2026
    ├─ Pagamento final: R$ 5,2M (10% retido)
    ├─ Liberação performance bond: R$ 5,2M (Bradesco)
    ├─ Assinaturas (cerimônia):
    │   ├─ Barzel CEO (Fernando Rocha) ✍️
    │   ├─ Canadian CEO Brazil (Richard Wong) ✍️
    │   ├─ GPA Facilities (testemunha) ✍️
    │   └─ LOGIQ CTO (testemunha tech) ✍️
    └─ Data: 18/06/2026


OPERAÇÃO: Docs Recorrentes (25 anos)
═══════════════════════════════════════════════════════════════

🖊️ #042 - Contrato O&M (Canadian Y1-5)
    ├─ Escopo: Manutenção preventiva + corretiva
    ├─ Valor: Incluso no EPC (warranty period)
    ├─ SLA: Disponibilidade 97% (penalidade 0,1%/dia)
    ├─ Assinatura: Já no contrato EPC #024
    └─ Vigência: 18/06/2026 - 18/06/2031

🖊️ #043 - Contrato O&M (Ecori Y6-25)
    ├─ Escopo: Manutenção + monitoramento
    ├─ Valor: 0,8% receita bruta (~R$ 67k/ano)
    ├─ Reajuste: IPCA anual
    ├─ Assinaturas:
    │   ├─ Ecori CEO ✍️
    │   ├─ Barzel Ops ✍️
    │   └─ LOGIQ Platform (intermediador) ✍️
    └─ Data: 01/06/2031 (assinar antes warranty end)

🖊️ #044 - Contrato Trading (LOGIQ Platform)
    ├─ Escopo: Venda excedente mercado livre
    ├─ Fee: R$ 5k/mês + 1,5% receita venda
    ├─ Duração: 5 anos (renovável)
    ├─ Assinaturas:
    │   ├─ LOGIQ CEO ✍️
    │   └─ Barzel CFO ✍️
    └─ Data: 01/06/2026 (antes COD)

🖊️ #045 - Registro CCEE (Agente Gerador)
    ├─ Tipo: Registro online CCEE
    ├─ Representante: LOGIQ Comercializadora
    ├─ Garantia: R$ 500k (carta fiança Itaú)
    ├─ Assinatura digital: Certificado ICP-Brasil ✍️
    └─ Data: 15/06/2026

🖊️ #046 - Contrato PPA (Power Purchase Agreement) - OPCIONAL
    ├─ Comprador: AES Tietê ou Google Brasil
    ├─ Volume: 953 MWh/mês (excedente)
    ├─ Preço: R$ 240/MWh fixo (10 anos)
    ├─ Alternativa: Spot market (mais volátil)
    └─ Decisão: A definir pelo Barzel (após 6m operação)


┌─────────────────────────────────────────────────────────────────────┐
│              RESUMO CADEIA DE ASSINATURAS                            │
├─────────────────────────────────────────────────────────────────────┤
│ Total documentos com assinatura: 46                                 │
│ Total assinaturas físicas: 127                                      │
│ Total assinaturas digitais (ICP): 1.289 (cotistas + investidores)  │
│ Cartórios envolvidos: 3 (reconhecimento + registro)                │
│ Custo cartório + registro: R$ 45k                                   │
│                                                                      │
│ Documento mais crítico: #024 (Contrato EPC) - R$ 52M                │
│ Documento mais complexo: #017 (Prospecto CRI) - 180 páginas         │
│ Maior nº assinaturas: #021 (Boletins subscrição) - 420              │
└─────────────────────────────────────────────────────────────────────┘
```

---

## 4. FLUXOGRAMA FINANCEIRO (Entradas e Saídas)

```
┌─────────────────────────────────────────────────────────────────────┐
│          FLUXO DE CAIXA DETALHADO (18 meses + 24 meses ops)         │
└─────────────────────────────────────────────────────────────────────┘

═══════════════════════════════════════════════════════════════════════
FASE 1: CAPTAÇÃO (Mês 0-5) - ENTRADAS
═══════════════════════════════════════════════════════════════════════

📥 ENTRADA #1 - Emissão CRI Verde
   ├─ Data: 15/06/2025 (liquidação)
   ├─ Valor bruto: R$ 40.000.000
   ├─ Custos emissão:
   │   ├─ Estruturação: R$ 800k (2%)
   │   ├─ Distribuição: R$ 600k (1,5%)
   │   ├─ Rating: R$ 160k
   │   ├─ SPO Verde: R$ 200k
   │   └─ Legal: R$ 240k
   ├─ Total custos: R$ 2.000.000
   └─ ✅ LÍQUIDO: R$ 38.000.000
   └─ Conta: Barzel Logística FIP - Itaú (AG 0123)

📥 ENTRADA #2 - Emissão Debêntures Incentivadas
   ├─ Data: 20/06/2025
   ├─ Valor bruto: R$ 10.000.000
   ├─ Custos emissão:
   │   ├─ Estruturação: R$ 180k (1,8%)
   │   ├─ Distribuição: R$ 120k (1,2%)
   │   └─ Certificação ANBIMA: R$ 80k
   ├─ Total custos: R$ 380.000
   └─ ✅ LÍQUIDO: R$ 9.620.000

📥 ENTRADA #3 - Emissão Cotas FII (Prioridade Cotistas)
   ├─ Data: 25/06/2025
   ├─ Cotas emitidas: 800.000 novas cotas
   ├─ Preço: R$ 10,00/cota
   ├─ Valor bruto: R$ 8.000.000
   ├─ Custos emissão:
   │   ├─ Estruturação: R$ 120k (1,5%)
   │   ├─ Distribuição: R$ 80k (1%)
   │   └─ CVM: R$ 40k
   ├─ Total custos: R$ 240.000
   └─ ✅ LÍQUIDO: R$ 7.760.000

💰 TOTAL CAPTADO: R$ 55.380.000
💰 SALDO INICIAL CAIXA: R$ 55.380.000
Data: 30/06/2025


═══════════════════════════════════════════════════════════════════════
FASE 2: ESTRUTURAÇÃO & ENGENHARIA (Mês 1-3) - SAÍDAS
═══════════════════════════════════════════════════════════════════════

📤 SAÍDA #1 - Sinal Contrato EPC (10%)
   ├─ Data: 18/06/2025
   ├─ Beneficiário: Canadian Solar Brasil Ltda
   ├─ Valor: R$ 5.200.000 (10% de R$ 52M)
   ├─ Forma: TED Itaú → Santander (Canadian)
   └─ Comprovante: Recibo assinado #024

📤 SAÍDA #2 - Mobilização EPC (20%)
   ├─ Data: 20/07/2025 (M+1)
   ├─ Beneficiário: Canadian Solar
   ├─ Valor: R$ 10.400.000
   ├─ Justificativa: Canteiro obras, logística, seguros
   └─ Comprovante: Medição 0 (mobilização)

📤 SAÍDA #3 - Consultoria + Legal (Diversos)
   ├─ Período: Jun-Ago/2025
   ├─ Beneficiários:
   │   ├─ Mattos Filho (legal): R$ 400k
   │   ├─ Bureau Veritas (laudo): R$ 80k
   │   ├─ CBRE (avaliação): R$ 90k
   │   ├─ Deloitte (auditoria): R$ 150k
   │   └─ Outros (geo, topo, etc): R$ 80k
   └─ TOTAL: R$ 800.000

📤 SAÍDA #4 - Seguros (Anual antecipado)
   ├─ Data: 19/06/2025
   ├─ Beneficiários:
   │   ├─ Swiss Re (Riscos Eng): R$ 180k
   │   ├─ Zurich (RC Geral): R$ 120k
   │   └─ Bradesco (Performance bond): R$ 520k (5,2M garantia×10%)
   └─ TOTAL: R$ 820.000

📤 SAÍDA #5 - Taxas Regulatórias
   ├─ Período: Jun-Ago/2025
   ├─ Destinos:
   │   ├─ CVM (registro emissão): R$ 85k
   │   ├─ ANEEL (registro gerador): R$ 12k
   │   ├─ CREA-SP (ART múltiplas): R$ 8k
   │   ├─ Bombeiros (AVCB análise): R$ 8k
   │   └─ Prefeitura Osasco (retrofit): R$ 15k
   └─ TOTAL: R$ 128.000

💸 TOTAL SAÍDO (M1-3): R$ 17.348.000
💰 SALDO CAIXA (fim M3): R$ 38.032.000
Data: 30/09/2025


═══════════════════════════════════════════════════════════════════════
FASE 3: PROCUREMENT - EQUIPAMENTOS (Mês 4-6) - SAÍDAS GRANDES
═══════════════════════════════════════════════════════════════════════

📤 SAÍDA #6 - Pagamento Equipamentos (40% EPC)
   ├─ Data: 20/09/2025 (M+3 do EPC)
   ├─ Beneficiário: Canadian Solar (repassa fabricantes)
   ├─ Valor: R$ 20.800.000
   ├─ Breakdown:
   │   ├─ Painéis (13.500× R$ 1.200): R$ 16.200k
   │   ├─ Inversores (50× R$ 160k): R$ 8.000k
   │   ├─ BESS containers (2× R$ 3,5M): R$ 7.000k
   │   ├─ Estruturas alumínio: R$ 4.500k
   │   ├─ Cabeamento + proteções: R$ 2.800k
   │   └─ Transformadores: R$ 2.300k
   │   (Total equipamentos: R$ 40,8M mas Canadian paga à vista
   │    e recebe parcelado conforme contrato)
   └─ Comprovante: NFs importação + Medição 1

📤 SAÍDA #7 - OPEX Administrativo (Trimestral)
   ├─ Período: Jul-Set/2025
   ├─ Despesas:
   │   ├─ Gestão Barzel (1% PL): R$ 158k
   │   ├─ Administração Ouribank: R$ 35k
   │   ├─ Auditoria (provisionado): R$ 50k
   │   ├─ Custódia B3: R$ 12k
   │   └─ Comunicação/RI: R$ 20k
   └─ TOTAL: R$ 275.000

💸 TOTAL SAÍDO (M4-6): R$ 21.075.000
💰 SALDO CAIXA (fim M6): R$ 16.957.000
Data: 31/12/2025

⚠️ ALERTA: Caixa crítico! Apenas 30% do total captado
           Próxima parcela EPC (20%) em M9 = R$ 10,4M
           Necessário gerenciar timing pagamentos


═══════════════════════════════════════════════════════════════════════
FASE 4: CONSTRUÇÃO (Mês 7-14) - SAÍDAS PROGRESSIVAS
═══════════════════════════════════════════════════════════════════════

📤 SAÍDA #8 - Etapa Construção Civil (20% EPC)
   ├─ Período: Jan-Abr/2026 (M7-M10)
   ├─ Beneficiário: Canadian Solar
   ├─ Medições mensais:
   │   ├─ M7 (Jan): R$ 2.600k (5% estruturas)
   │   ├─ M8 (Fev): R$ 2.600k (5% painéis 50%)
   │   ├─ M9 (Mar): R$ 2.600k (5% painéis 100%)
   │   └─ M10 (Abr): R$ 2.600k (5% elétrica)
   └─ TOTAL: R$ 10.400.000

📤 SAÍDA #9 - OPEX Operacional (Preparação)
   ├─ Período: Jan-Jun/2026
   ├─ Despesas:
   │   ├─ Contratação equipe O&M: R$ 120k (6×R$20k)
   │   ├─ Treinamento GPA operadores: R$ 80k
   │   ├─ Sistema SCADA/LOGIQ: R$ 150k (setup)
   │   ├─ Registro CCEE agente: R$ 12k + R$ 500k garantia
   │   └─ Marketing/comunicação: R$ 50k
   └─ TOTAL: R$ 912.000

📤 SAÍDA #10 - Juros CRI + Debêntures (Carência)
   ├─ Período: Jun/2025 - Jun/2026 (12 meses carência)
   ├─ CRI (R$ 40M × CDI+1,5% = 13,2% aa):
   │   └─ Juros mensais: R$ 440k × 12 = R$ 5.280k
   ├─ Debêntures (R$ 10M × CDI+2,5% = 14,25% aa):
   │   └─ Juros mensais: R$ 118k × 12 = R$ 1.416k
   ├─ TOTAL JUROS ANO 1: R$ 6.696.000
   └─ ⚠️ Carência amortização, mas paga juros!

💸 TOTAL SAÍDO (M7-14): R$ 18.008.000
💰 SALDO CAIXA (fim M14): -R$ 1.051.000 ❌ NEGATIVO!
Data: 30/04/2026

🚨 PROBLEMA: Caixa insuficiente!
   Faltam R$ 5,2M para pagamento final EPC (10% no COD)
   
📊 SOLUÇÃO: Antecipar dividendos cotistas (retenção temporária)
            OU: Bridge loan R$ 5M (60 dias até COD gerar receita)


═══════════════════════════════════════════════════════════════════════
FASE 5: FINALIZAÇÃO & COD (Mês 15-18)
═══════════════════════════════════════════════════════════════════════

📥 ENTRADA EMERGENCIAL - Bridge Loan (Itaú)
   ├─ Data: 01/05/2026
   ├─ Valor: R$ 6.000.000
   ├─ Taxa: CDI + 3,5% (curto prazo = caro)
   ├─ Prazo: 90 dias (vence 31/07/2026)
   ├─ Garantia: Recebíveis futuros energia
   └─ Custo: R$ 6M × 16% aa × 3/12 = R$ 240k juros

💰 SALDO CAIXA (com bridge): R$ 4.949.000
Data: 01/05/2026

📤 SAÍDA #11 - Finalização Obra (10% EPC)
   ├─ Data: 18/06/2026 (COD!)
   ├─ Beneficiário: Canadian Solar
   ├─ Valor: R$ 5.200.000 (último pagamento)
   ├─ Retenção: Performance bond R$ 520k liberado (vai para Canadian)
   └─ Comprovante: TAD (Termo Aceite Definitivo) #041

💰 SALDO CAIXA pós-COD: -R$ 251.000
Data: 18/06/2026


═══════════════════════════════════════════════════════════════════════
OPERAÇÃO: RECEITAS (Mês 19+) - FINALMENTE! 💰
═══════════════════════════════════════════════════════════════════════

📥 RECEITA #1 - Economia Energia GPA (Autoconsumo)
   ├─ Início: Julho/2026
   ├─ Volume: 690 MWh/mês (consumo CD01)
   ├─ Valor evitado: R$ 550/MWh (tarifa Eletropaulo)
   ├─ RECEITA MENSAL: R$ 379.500
   ├─ Destinatário: Barzel FIP (reduz OPEX GPA)
   └─ Modelo contábil: Receita operacional (NOI +)

📥 RECEITA #2 - Venda Excedente (Mercado Livre)
   ├─ Início: Julho/2026
   ├─ Volume: 952 MWh/mês (58% excedente)
   ├─ Preço spot médio: R$ 250/MWh
   ├─ RECEITA BRUTA: R$ 238.000/mês
   ├─ Fee LOGIQ (1,5%): -R$ 3.570
   ├─ Fee CCEE (taxa): -R$ 1.000
   ├─ RECEITA LÍQUIDA: R$ 233.430/mês
   └─ Liquidação: Semanal (CCEE)

📥 RECEITA #3 - Créditos Carbono (I-REC)
   ├─ Início: Agosto/2026 (após 1 mês medição)
   ├─ Volume: 768 MWh/mês × 0,0923 tCO2/MWh = 71 tCO2
   ├─ Preço: R$ 10/tCO2 (mercado voluntário)
   ├─ RECEITA MENSAL: R$ 710
   └─ Comprador: Google Brasil (contrato anual)

💰 RECEITA TOTAL MENSAL: R$ 613.640
💰 RECEITA ANUAL (12 meses): R$ 7.363.680
Data início: 01/07/2026


📤 DESPESAS OPERACIONAIS (Mês 19+)
   ├─ O&M Canadian (warranty, incluso EPC): R$ 0
   ├─ SCADA/Monitoramento: R$ 8k/mês
   ├─ Seguro operacional: R$ 15k/mês (R$ 180k/ano ÷12)
   ├─ LOGIQ Trading fee: R$ 5k/mês fixo + variável (já descontado)
   ├─ Taxa gestão Barzel: R$ 15,8k/mês (1% PL crescente)
   ├─ Administração Ouribank: R$ 3,5k/mês
   └─ TOTAL OPEX: R$ 47.300/mês

💰 NOI MENSAL: R$ 613.640 - R$ 47.300 = R$ 566.340
💰 NOI ANUAL: R$ 6.796.080


📤 SERVIÇO DÍVIDA (Mês 19+)
   
   🔴 Bridge Loan Itaú (quitação)
   ├─ Data: 31/07/2026 (M+90 do saque)
   ├─ Principal: R$ 6.000.000
   ├─ Juros: R$ 240.000
   └─ TOTAL: R$ 6.240.000
   └─ ✅ Quitado com 1 mês receita operacional

   🔴 CRI (amortização começa M19)
   ├─ Principal: R$ 40.000.000
   ├─ Prazo: 84 meses (7 anos)
   ├─ Carência: 18 meses (já passou)
   ├─ Sistema: Tabela Price
   ├─ Taxa: CDI + 1,5% = 13,2% aa
   ├─ PMT mensal: R$ 734.000 (juros + amortização)
   └─ Início: Julho/2026

   🔴 Debêntures (amortização começa M19)
   ├─ Principal: R$ 10.000.000
   ├─ Prazo: 72 meses (6 anos)
   ├─ Carência: 18 meses
   ├─ Taxa: CDI + 2,5% = 14,25% aa
   ├─ PMT mensal: R$ 205.000
   └─ Início: Julho/2026

💸 SERVIÇO DÍVIDA TOTAL: R$ 939.000/mês
   (R$ 734k CRI + R$ 205k Debêntures)


═══════════════════════════════════════════════════════════════════════
FLUXO DE CAIXA OPERACIONAL (Steady State - Mês 20+)
═══════════════════════════════════════════════════════════════════════

📊 RESUMO MENSAL:
┌─────────────────────────────────────────────────────────────┐
│ RECEITAS                                                     │
├─────────────────────────────────────────────────────────────┤
│ Economia energia (GPA):        R$ 379.500                   │
│ Venda excedente:                R$ 233.430                   │
│ Créditos carbono:               R$     710                   │
│ ────────────────────────────────────────────                │
│ RECEITA BRUTA:                  R$ 613.640                   │
│                                                              │
│ DESPESAS OPERACIONAIS                                        │
├─────────────────────────────────────────────────────────────┤
│ O&M + monitoramento:            R$   8.000                   │
│ Seguros:                        R$  15.000                   │
│ LOGIQ Platform:                 R$   5.000                   │
│ Gestão + Administração:         R$  19.300                   │
│ ────────────────────────────────────────────                │
│ OPEX TOTAL:                     R$  47.300                   │
│                                                              │
│ NOI (Receita - OPEX):           R$ 566.340 ✅                │
│                                                              │
│ SERVIÇO DÍVIDA                                              │
├─────────────────────────────────────────────────────────────┤
│ CRI (amortização + juros):      R$ 734.000                   │
│ Debêntures:                     R$ 205.000                   │
│ ────────────────────────────────────────────                │
│ DÍVIDA TOTAL:                   R$ 939.000                   │
│                                                              │
│ FLUXO LIVRE (NOI - Dívida):     R$ -372.660 ❌ NEGATIVO!    │
│                                                              │
│ ⚠️  PROBLEMA: Dívida consome 166% do NOI!                   │
│     DSCR = 566k ÷ 939k = 0,60x (mínimo 1,3x!)              │
└─────────────────────────────────────────────────────────────┘


🚨 ANÁLISE CRÍTICA: ESTRUTURA INSUSTENTÁVEL!

Cenário atual: Fluxo negativo R$ 373k/mês
Burn acumulado: R$ 373k × 12 = R$ 4,5M/ano

Necessário REESTRUTURAÇÃO:

OPÇÃO 1: Aumentar Carência Dívida
├─ Negociar com CRI: carência 36 meses (não 18)
├─ Ganho tempo: +18 meses sem amortização
├─ Fluxo durante carência: +R$ 566k/mês (só NOI)
└─ Acumular caixa para início amortização forte

OPÇÃO 2: Reduzir Dívida (mais Equity)
├─ Emissão cotas: R$ 50M (não R$ 8M)
├─ Dívida: R$ 8M CRI (não R$ 50M)
├─ PMT menor: R$ 147k/mês (não R$ 939k)
├─ Fluxo livre: +R$ 419k/mês ✅ POSITIVO
└─ Diluição maior: 83% (não 14%)

OPÇÃO 3: Aumentar Receita (mais ativos)
├─ Portfólio 3 CDs (não 1)
├─ Receita: R$ 1,84M/mês (3× R$ 613k)
├─ NOI: R$ 1,7M/mês (economias escala)
├─ Dívida: R$ 939k/mês (mesma)
├─ Fluxo livre: +R$ 761k/mês ✅ VIÁVEL
└─ DSCR: 1,81x (saudável!)

RECOMENDAÇÃO: OPÇÃO 3
Fazer captação única R$ 174M para 3 CDs simultâneos
Diluir risco, melhorar DSCR, viabilizar dívida


═══════════════════════════════════════════════════════════════════════
PROJEÇÃO LONGO PRAZO (25 anos)
═══════════════════════════════════════════════════════════════════════

ANO 1-6: Amortização Debêntures
├─ PMT: R$ 205k/mês × 72 = R$ 14,76M
└─ Quitação: Junho/2032

ANO 1-7: Amortização CRI
├─ PMT: R$ 734k/mês × 84 = R$ 61,66M
└─ Quitação: Junho/2033

ANO 8-25: Livre de Dívida (17 anos!)
├─ NOI: R$ 566k/mês
├─ OPEX adicional (O&M pago): R$ 67k/mês
├─ Fluxo livre: R$ 499k/mês × 12 = R$ 6M/ano
└─ Acumulado 17 anos: R$ 102M (VPL ~R$ 45M)

VALUATION IMPACTO:
Sem solar: Cap Rate 9,5%, Valor R$ 158M
Com solar (livre dívida Y8+): Cap Rate 8%, Valor R$ 212M
GANHO: +R$ 54M (+34%) 🚀


═══════════════════════════════════════════════════════════════════════
DISTRIBUIÇÃO COTISTAS (Dividendos)
═══════════════════════════════════════════════════════════════════════

Durante amortização (Y1-Y7):
├─ Fluxo negativo: -R$ 373k/mês
├─ Dividendo: ZERO (necessário reter para pagar dívida)
└─ ⚠️  Cotistas não recebem por 7 anos!

Alternativa: Separar solar em SPE
├─ SPE Solar detém projeto (isolado)
├─ FII investe como equity holder
├─ Dividendos FII principais continuam
└─ SPE distribui após quitar dívida (Y8+)

Pós-dívida (Y8-Y25):
├─ Fluxo livre: R$ 499k/mês
├─ Mandatório 95%: R$ 474k/mês
├─ Cotas: 10,8M (diluídas 8%)
├─ DY por cota: R$ 0,044/mês
├─ Yield anual: 5,3% (sobre R$ 10/cota)
└─ Atrativo comparado DI futuro (4-5%)


═══════════════════════════════════════════════════════════════════════
CRONOGRAMA CONSOLIDADO (Financeiro + Datas)
═══════════════════════════════════════════════════════════════════════

📅 MARCO 1: Aprovação Projeto
Data: 15/04/2025 (Assembleia)
Fluxo: R$ 0 (pré-captação)

📅 MARCO 2: Captação Concluída
Data: 30/06/2025
Fluxo: +R$ 55,4M (entrada) | Saldo: R$ 55,4M

📅 MARCO 3: Início Obra
Data: 20/06/2025 (5 dias antes captação, risco gerenciado)
Fluxo: -R$ 5,2M (sinal EPC) | Saldo: R$ 50,2M

📅 MARCO 4: Procurement Equipamentos
Data: 20/09/2025
Fluxo: -R$ 20,8M (40% EPC) | Saldo: R$ 17M

📅 MARCO 5: Caixa Crítico
Data: 31/12/2025
Fluxo: -R$ 11M (construção) | Saldo: R$ 6M ⚠️

📅 MARCO 6: Bridge Loan
Data: 01/05/2026
Fluxo: +R$ 6M (empréstimo ponte) | Saldo: R$ 5M

📅 MARCO 7: COD (Commercial Operation Date) 🎉
Data: 18/06/2026
Fluxo: -R$ 5,2M (pagamento final) | Saldo: -R$ 200k
Início geração: Receita R$ 614k/mês começa!

📅 MARCO 8: Primeira Receita
Data: 15/07/2026 (liquidação CCEE)
Fluxo: +R$ 614k | Saldo: R$ 414k ✅ Positivo!

📅 MARCO 9: Quitação Bridge
Data: 31/07/2026
Fluxo: -R$ 6,24M (principal + juros)
Fonte: 1 mês receita acumulada

📅 MARCO 10: Início Amortização Dívida
Data: 01/07/2026
Fluxo mensal: -R$ 939k (84 meses CRI + 72 Deb)

📅 MARCO 11: Quitação Debêntures
Data: 30/06/2032 (6 anos)
Fluxo: Última PMT R$ 205k
Dívida restante: Apenas CRI R$ 25M (60% amortizado)

📅 MARCO 12: Quitação CRI (Jubileu!)
Data: 30/06/2033 (7 anos)
Fluxo: Última PMT R$ 734k
Status: 100% LIVRE DE DÍVIDA 🎊

📅 MARCO 13: Steady State
Data: 01/07/2033 onwards (18 anos restantes)
Fluxo mensal: +R$ 499k livre
Distribuição cotistas: 95% = R$ 474k/mês
DY: 5,3% aa (atrativo vs renda fixa)


═══════════════════════════════════════════════════════════════════════
RESUMO EXECUTIVO: FLUXO FINANCEIRO
═══════════════════════════════════════════════════════════════════════

INVESTIMENTO TOTAL: R$ 58.000.000

FONTES (Como financiamos):
├─ CRI Verde:        R$ 38,0M (66%)
├─ Debêntures:       R$  9,6M (16%)
├─ Cotas FII:        R$  7,8M (13%)
├─ Bridge (temp):    R$  6,0M (10%, quitado em 1 mês)
└─ WACC médio: 11,8% aa

USOS (Para que gastamos):
├─ EPC Turnkey:      R$ 52,0M (90%)
├─ Consultorias:     R$  0,8M (1,4%)
├─ Legal:            R$  0,7M (1,2%)
├─ Seguros:          R$  0,8M (1,4%)
├─ Emissões:         R$  2,6M (4,5%)
├─ Taxas/Registros:  R$  0,1M (0,2%)
└─ OPEX pré-op:      R$  1,0M (1,7%)

RETORNO:
├─ TIR Projeto: 11,2% aa (25 anos)
├─ Payback: 7,4 anos
├─ VPL: +R$ 28,4M (TMA 10%)
├─ Valuation uplift: +19% (R$ 158M → R$ 188M)

RISCO PRINCIPAL:
⚠️  DSCR < 1,3x durante anos 1-7 (dívida pesada)
✅  Mitigação: Portfólio 3+ CDs (escala) ou mais equity

CONCLUSÃO FINANCEIRA:
Projeto VIÁVEL mas estrutura atual é APERTADA.
Recomendação: Replicar para 3 CDs simultâneos ou
reduzir dívida para 30% (não 86% como modelado).
