# Sistema de Simulação Socioeconômico

Projeto Acadêmico – Análise e Desenvolvimento de Sistemas  
Centro Universitário do Distrito Federal (UDF) — 2026.2

---

## 1. Visão Geral

O **Sistema de Simulação Socioeconômico** é uma plataforma web (PWA) de utilidade pública concebida para desburocratizar e democratizar o acesso às informações de assistência social no Distrito Federal.

A aplicação permite que cidadãos em geral realizem uma verificação prévia, ágil e anônima de elegibilidade aos programas assistenciais estaduais (**DF Social** e **Prato Cheio**), reduzindo a assimetria informacional e orientando quanto aos procedimentos e documentações necessárias antes do atendimento presencial nos postos de assistência social.

---

## 2. Alinhamento com a ODS 10 (ONU)

O projeto alinha-se diretamente ao **Objetivo de Desenvolvimento Sustentável 10: Redução das Desigualdades**, especificamente à **Meta 10.2**, cujo foco é empoderar e promover a inclusão social, econômica e política de todos, independentemente de renda ou condição social, mediante o aumento da transparência sobre direitos assistenciais.

---

## 3. Especificação de Requisitos

### 3.1. Requisitos Funcionais (RF)

- **[RF01] Simulação de Elegibilidade DF Social:** O sistema deve calcular a elegibilidade do cidadão para o programa DF Social com base na renda familiar per capita (limite de até R\$ 218,00) e na inscrição ativa no Cadastro Único (CadÚnico).
- **[RF02] Simulação de Elegibilidade Prato Cheio:** O sistema deve verificar os critérios para a concessão do crédito alimentação (Prato Cheio), considerando a renda per capita de até meio salário mínimo e a situação de vulnerabilidade social declarada.
- **[RF03] Formulário Dinâmico Guiado:** O sistema deve apresentar um formulário passo a passo com perguntas objetivas, indicador de progresso e linguagem acessível.
- **[RF04] Emissão de Diagnóstico Socioeconômico:** O sistema deve exibir na tela final a síntese consolidada dos benefícios aos quais o perfil atende aos requisitos (status: *Elegível*, *Não Elegível* ou *Pendente de Cadastro*).
- **[RF05] Direcionamento por Região Administrativa:** O sistema deve identificar a Região Administrativa (RA) informada pelo usuário e apresentar as orientações de atendimento presencial correspondentes.

### 3.2. Requisitos Não-Funcionais (RNF)

- **[RNF01] Acessibilidade Web:** A interface deve fornecer alto contraste, suporte a leitores de tela e redimensionamento de texto para garantir a usabilidade por pessoas com baixo letramento digital.
- **[RNF02] Privacidade e Conformidade (LGPD):** O sistema não deve armazenar ou solicitar dados pessoais identificáveis (como nome completo ou CPF) durante o processo de simulação.
- **[RNF03] Desempenho de Processamento:** A execução das regras de negócio e a renderização do diagnóstico devem ser concluídas em tempo inferior a 2 segundos.
- **[RNF04] Arquitetura Mobile First:** A interface da aplicação deve ser projetada prioritariamente para dispositivos móveis de telas pequenas.

---

## 4. Regras de Negócio (RN)

| Código | Denominação | Descrição Operacional |
| :--- | :--- | :--- |
| **RN01** | Cálculo de Renda Per Capita | Renda Per Capita = (Soma das rendas brutas da família) / (Número total de residentes). |
| **RN02** | Parâmetro DF Social | Renda per capita <= R\$ 218,00 E registro ativo no CadÚnico. |
| **RN03** | Parâmetro Prato Cheio | Renda per capita <= R\$ 706,00 (1/2 salário mínimo) E declaração de vulnerabilidade alimentar. |
| **RN04** | Tratamento de Incompatibilidade | Quando os limites de renda forem superados, o sistema deve fornecer orientação informativa sem emitir atestado de elegibilidade. |

---

## 5. Arquitetura Conceitual do Fluxo de Dados

```text
[Usuário / Cidadão]
        │
        ▼
[Interface Web / PWA (HTML5, CSS3, JavaScript)]
        │  (Entrada via formulário sequencial)
        ▼
[Motor de Regras de Negócio]
        ├──> Aplicação da RN01 (Cálculo de Renda)
        ├──> Avaliação da RN02 (Critérios DF Social)
        └──> Avaliação da RN03 (Critérios Prato Cheio)
        │
        ▼
[Exibição do Diagnóstico e Relação Documental]
```

## 6. Identificação e Autoria

- **Instituição:** Centro Universitário do Distrito Federal (UDF).
- **Curso:** Análise e Desenvolvimento de Sistemas (ADS)
- **Integrantes:** 

1. HEBERT VINICIUS.
2. ANDRÉ CELERINO.
3. DANILO GUILHERME.
4. GUSTAVO MAGALHÃES.
5. PEDRO HENRIQUE NEVES.
