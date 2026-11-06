# 🌐 UrbiSafe — Urban Risk Intelligence Platform
**Global Solution 2 — CitizenTech | Engenharia de Software (FIAP)**

---

## 👥 Integrantes do Grupo
* **Rafael Lopes Bestilleiro Benedetti** — RM: 554781 — 3ECR
* **Breno Ferreira e Silva** — RM: 555503 — 3ECR
* **Vinicius de Abreu Fernandes** — RM: 558184 — 3ECA 

## 🔗 Links e Caminhos
* 💻 **Protótipo Web (HTML):** [UrbiSafe Web](index.html)
* 🎥 **Vídeo :**  

---

# 🌧️ Plataforma Inteligente de Monitoramento de Riscos Urbanos

## 🎯 1. Problema, Público-Alvo e Personas

* **O Problema:** Dados sobre enchentes, ondas de calor e quedas de serviços essenciais ficam dispersos. Sensores não cobrem todas as vias, bases públicas demoram a atualizar e relatos em redes sociais carecem de verificação de confiança, atrasando a resposta a emergências.
* **Público-Alvo:** Moradores urbanos, agentes da Defesa Civil e operadores de concessionárias de serviços públicos.

### Personas

1. **Carlos Mendes (Morador Urbano, 34 anos):** Desloca-se por áreas de risco. Precisa receber alertas rápidos no celular para alterar sua rota e quer relatar problemas na sua rua em poucos cliques, com anonimato garantido.
2. **Juliana Costa (Agente da Defesa Civil, 41 anos):** Precisa filtrar relatos falsos. Utiliza o painel operacional para auditar a origem do dado e o nível de confiança (%) antes de despachar equipes.

---

## 📋 2. Requisitos Funcionais (RF) e Mapeamento nas Telas do Sistema

O sistema possui 11 Requisitos Funcionais que definem as funcionalidades disponibilizadas aos moradores e agentes locais.

| ID | Descrição do Requisito Funcional | Prioridade | Tela |
| :--- | :--- | :--- | :--- |
| **RF01** | O sistema deve permitir a seleção de perfil (Morador ou Agente Local), mediante aceite explícito do termo de consentimento e das políticas de privacidade conforme a LGPD. | Alta | Tela Login |
| **RF02** | O sistema deve disponibilizar um mapa geoespacial com a localização dos eventos de risco ativos, identificados por cores e ícones de acordo com sua gravidade. | Alta | Tela Mapa em Tempo Real |
| **RF03** | O sistema deve permitir a filtragem dos eventos apresentados no mapa por categoria de risco: alagamentos, ondas de calor e falhas em serviços essenciais. | Média | Tela Mapa em Tempo Real |
| **RF04** | O sistema deve apresentar uma lista de alertas ordenada automaticamente pelo Score de Risco, exibindo a prioridade e o estado atual de cada evento. | Alta | Tela Alertas Priorizadas |
| **RF05** | O sistema deve permitir a visualização detalhada de cada ocorrência, apresentando localização, severidade, impacto populacional, nível de confiança, histórico e orientações de segurança. | Alta | Tela Detalhes da Ocorrência |
| **RF06** | O sistema deve apresentar a origem de cada informação (Sensor IoT, API Pública ou Registro Comunitário), acompanhada do respectivo nível de confiança (%) e dos critérios de validação. | Alta | Tela Origem e Confiança (%) |
| **RF07** | O sistema deve permitir que moradores registrem novas ocorrências informando categoria, localização GPS, descrição e fotografia opcional. | Alta | Tela Reportar Ocorrência |
| **RF08** | O sistema deve permitir que moradores confirmem ocorrências comunitárias próximas, incrementando em 10 pontos percentuais o nível de confiança do evento, respeitando o limite máximo definido pela regra de negócio. | Média | Tela Reportar Ocorrência |
| **RF09** | O sistema deve disponibilizar uma central de notificações com histórico de alertas e configurações de preferências por categoria de risco, permitindo o recebimento de atualizações em tempo real. | Alta | Tela Central de Notificações |
| **RF10** | O sistema deve disponibilizar um painel operacional para agentes locais, permitindo validar, emitir alertas, monitorar, encerrar ou descartar ocorrências por meio de uma máquina de estados. | Alta | Tela Centro Operacional |
| **RF11** | O sistema deve anonimizar os dados pessoais dos relatos comunitários por meio de um mecanismo de proteção de informações (PII Filter), além de permitir a consulta e revogação do consentimento do usuário. | Alta | Telas Login e Privacidade & LGPD |

---

## 🛡️ 3. Requisitos Não Funcionais (RNF — Norma ISO/IEC 25010)

Os Requisitos Não Funcionais estabelecem os critérios de qualidade, desempenho, segurança, disponibilidade e interoperabilidade que devem ser atendidos pela arquitetura do sistema.

| ID | Categoria ISO 25010 | Requisito Obrigatório | Especificação e Métrica |
| :--- | :--- | :--- | :--- |
| **RNF01** | Eficiência de Desempenho | **Notificações em Tempo Real** | O processamento de novos relatos e leituras de sensores, o recálculo do nível de confiança e a atualização dos alertas devem ocorrer em menos de **5 segundos**, utilizando WebSockets e serviços de Push Notification. |
| **RNF02** | Confiabilidade | **Disponibilidade do Sistema** | A plataforma deve operar continuamente, 24 horas por dia e 7 dias por semana, mantendo disponibilidade mínima de **99,9% (SLA)**, inclusive durante períodos de emergência. |
| **RNF03** | Eficiência de Desempenho | **Escalabilidade Horizontal** | A arquitetura deve permitir escalonamento automático dos serviços de aplicação para suportar picos de utilização de até **50.000 acessos simultâneos**, sem comprometer o processamento dos eventos. |
| **RNF04** | Usabilidade | **Facilidade de Utilização e Acessibilidade** | O registro de ocorrências deve ser realizado em até **3 passos**, com interface intuitiva e indicadores de risco que utilizem cores, ícones e textos para garantir acessibilidade, inclusive para usuários com daltonismo. |
| **RNF05** | Segurança | **Proteção de Dados e Conformidade com a LGPD** | O sistema deve implementar anonimização automática de relatos comunitários, gerenciamento de consentimento, comunicação protegida por **TLS 1.3** e criptografia **AES-256** para dados sensíveis armazenados. |
| **RNF06** | Compatibilidade | **Interoperabilidade com Fontes Externas** | A arquitetura deve permitir a integração de sensores IoT por meio do protocolo **MQTT** e de bases públicas e concessionárias por meio de APIs **REST/JSON**, garantindo padronização na ingestão de dados externos. |

---

## ⚙️ 4. Regras de Negócio Principais

As regras de negócio são responsáveis por determinar como os eventos recebidos são validados, classificados e priorizados pela aplicação.

### RN01 — Cálculo do Nível de Confiança do Dado (NC)

O sistema deve calcular automaticamente o nível de confiança de cada ocorrência considerando sua origem e as validações recebidas.

| Origem do Dado | Confiança Base |
| :--- | :--- |
| Base Pública / Concessionária | 90% |
| Sensor IoT Oficial Homologado | 85% |
| Registro Comunitário com Foto e GPS | 45% |
| Registro Comunitário somente com Texto | 30% |

**Regras complementares:**

- Cada confirmação de outro morador adiciona **10 pontos percentuais** ao nível de confiança.
- O incremento por confirmações comunitárias é limitado a **30 pontos percentuais**.
- Eventos com **NC ≥ 50%** podem passar automaticamente do estado *Em Validação* para *Confirmado*.
- O sistema deve registrar a origem e o histórico de validações para permitir auditoria.
- O cruzamento de informações deve considerar ocorrências em um raio de até **500 metros**, conforme definido na arquitetura.

### RN02 — Cálculo do Nível de Risco e Priorização (Score)

O sistema deve calcular automaticamente a prioridade de cada ocorrência considerando sua severidade, impacto populacional e nível de confiança.

**Fórmula:**

`Score de Risco = Severidade (1 a 5) × Impacto Populacional (1 a 5) × (NC ÷ 100)`

**Classificação dos eventos:**

| Classificação | Score de Risco | Comportamento do Sistema |
| :--- | :--- | :--- |
| 🔴 **Crítico** | ≥ 16 | Envio imediato de Push Notification, alerta sonoro e prioridade máxima no painel operacional. |
| 🟠 **Alto** | 10 a 15,9 | Envio de Push Notification padrão e recomendação de desvio de rota. |
| 🟡 **Moderado** | 5 a 9,9 | Registro na central de notificações e atualização do mapa de riscos. |
| 🔵 **Baixo** | < 5 | Monitoramento informativo no mapa, sem notificação emergencial. |

---

## 📐 5. Diagramas UML

### 5.1. Diagrama de Sequência
![Diagrama de Sequência](Imagens/Diagrama%20de%20Sequência.png)

### 5.2. Diagrama de Estado
![Diagrama de Estado](Imagens/Diagrama%20de%20Estado.png)

### 5.3 Arquiterura de camadas
![Arquitetura de Camada](Imagens/Arquitetura%20em%20camadas.png)

