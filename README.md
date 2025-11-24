# 📘 Documentação Final: Projeto DevFlow AI - Cliente: EcoSolutions Ltda

Este repositório contém a entrega final do projeto **DevFlow AI**, uma simulação acadêmica de desenvolvimento de software realizada inteiramente por uma equipe de agentes de Inteligência Artificial autônomos (Agentic AI).

## 1. Visão Geral e Estrutura da Equipe
O objetivo foi simular a concepção do sistema **"EcoTrack"**, um software de gestão de pegada de carbono para PMEs. A equipe utilizou a arquitetura `RoundRobinGroupChat` (fluxo circular), composta pelos seguintes agentes configurados no arquivo `team-config.json`:

| Agente | Função | Personalidade e Missão (Resumo dos Prompts) |
| :--- | :--- | :--- |
| **Líder Técnico** | Orquestrador | *Decisivo e estratégico.* Missão: Interpretar o briefing, criar o plano de trabalho e orquestrar a sequência de tarefas. |
| **Analista de Requisitos** | Espec. Funcional | *Analítico e minucioso.* Missão: Traduzir necessidades do cliente em requisitos funcionais e não funcionais. |
| **Arquiteto de Software** | Tech Lead | *Pragmático e visionário.* Missão: Definir a stack tecnológica focando em escalabilidade e segurança. |
| **Designer de Interface** | UX/UI | *Criativo e centrado no usuário.* Missão: Criar fluxos de navegação e conceitos visuais. |
| **Dev. Lógica (Back)** | Implementação | *Preciso e sistemático.* Missão: Planejar endpoints da API e regras de negócio. |
| **Dev. Interface (Front)** | Implementação | *Prático e visual.* Missão: Estruturar componentes reutilizáveis. |
| **Engenheiro de Testes** | QA | *Cético e metódico.* Missão: Criar cenários de teste para validar precisão e segurança. |
| **Gerente de Projeto** | Gestão | *Organizacional e proativo.* Missão: Monitorar riscos, cronograma e integração. |
| **Redator Técnico** | Documentação | *Formal e meticuloso.* Missão: Compilar o "Documento Técnico de Proposta de Software". |

## 2. Inputs Iniciais (Briefing e Artefatos)
Para garantir decisões técnicas realistas, foram fornecidos ao **Líder Técnico** quatro artefatos simulando o cliente *EcoSolutions Ltda*:

### Artefato A: O Problema (E-mail do Cliente)
> "Precisamos de um sistema SaaS para PMEs monitorarem consumo de energia. A dor principal é o erro no cálculo manual. O sistema precisa aceitar conta de luz (kWh) e combustível (Litros), aplicar fator de conversão oficial e gerar laudo PDF. Prioridade máxima em segurança."

### Artefato B: Contexto de Dados (JSON)
Foi fornecido um exemplo da estrutura de dados que o sistema deve processar:
```
json
{
  "cliente_id": "PME-4921",
  "entradas": [
    { "tipo": "ELETRICIDADE", "qtd": 4500.50, "unidade": "kWh" },
    { "tipo": "FROTA", "qtd": 600, "unidade": "L", "combustivel": "DIESEL_S10" }
  ]
}
```

### Artefato C: Diretrizes de Design
Paleta: Verde Floresta (#2E8B57) e Cinza.

Estilo: "Clean Corporate".

Foco: Dashboard com números grandes para facilitar a leitura por leigos.

### Artefato D: Regras de Negócio (Compliance)
Norma: GHG Protocol.

Fatores: Eletricidade = 0.092 kgCO2e/kWh; Diesel = 2.68 kgCO2e/L.

Auditoria: Log imutável de alterações obrigatório.

## 3. Roteiro Textual das Interações 

O sistema operou em fluxo circular (RoundRobin), onde o orquestrador (Líder) iniciou e o trabalho passou de mão em mão:

**Líder Técnico**: Recebeu o briefing do EcoTrack. Definiu que o projeto precisava de foco total em "precisão de cálculo" e "facilidade de uso". Instruiu o Analista a focar nos tipos de dados de entrada.

**Analista**: Detalhou que o sistema precisa aceitar inputs em kWh (energia) e Litros (combustível). Definiu requisitos de segurança para os dados sensíveis das empresas.

**Arquiteto**: Com base na segurança pedida, definiu uma arquitetura em nuvem (AWS) com banco de dados PostgreSQL. Escolheu Python para o Back-end devido à facilidade com bibliotecas de cálculo matemático.

**Designer**: Propôs um Dashboard limpo, com "cards" de resumo no topo e gráficos de linha para evolução mensal. Priorizou a acessibilidade.

**Dev. Lógica**: Mapeou a rota POST /api/v1/consumption que recebe os dados e aplica a fórmula de conversão CO2.

**Dev. Interface**: Planejou a estrutura de componentes React: ChartComponent, InputForm e ReportGenerator.

**Tester**: Identificou um risco crítico: "O que acontece se o usuário inserir consumo negativo?". Criou casos de teste para validação de input.

**Gerente**: Validou que todos os requisitos do briefing foram cobertos e alertou sobre o prazo de implementação da geração de PDF.

**Redator**: Compilou todas as decisões acima em um documento formatado e encerrou o projeto.

## 4. Evidências de Funcionamento 

(Trecho simulado do log de execução do terminal)

```
Plaintext

[Lider_Tecnico]: Iniciando análise do projeto EcoTrack... Plano de ação gerado.
--------------------------------------------------------------------------------
[Analista_Requisitos]: Requisitos extraídos. RF01: Input de Eletricidade. RF02: Cálculo de CO2.
--------------------------------------------------------------------------------
[Arquiteto_Software]: Stack definida: Backend Python (FastAPI), Frontend React, DB PostgreSQL.
--------------------------------------------------------------------------------
[Designer_Interface]: Wireframes conceituais definidos. Foco em Dashboards intuitivos.
--------------------------------------------------------------------------------
... (interações dos devs) ...
--------------------------------------------------------------------------------
[Redator_Tecnico]: DOCUMENTO TÉCNICO COMPILADO.
--------------------------------------------------------------------------------
PROJETO CONCLUÍDO. FIM DE COMUNICAÇÃO.
```

## 5. Curiosidades e Análise Crítica 

### 1. Influência da Personalidade nas Decisões
**O Tester (Cético)**: A personalidade "cética" do Engenheiro de Testes foi fundamental. Enquanto os devs focavam em fazer funcionar, ele questionou a integridade dos dados, forçando a inclusão de validações extras de input que não estavam no briefing original.

**O Arquiteto (Pragmático)**: Evitou o "over-engineering". Ao invés de propor uma arquitetura de microsserviços complexa para um sistema de PMEs, optou por um monolito modular, justificando pela facilidade de manutenção (compatível com sua personalidade "eficiente").

### 2. Conflitos e Resolução pelo Orquestrador
**Conflito Identificado**: Houve uma divergência leve entre o Designer (que queria gráficos animados complexos) e o Arquiteto (que priorizava performance em conexões lentas).

**Resolução**: Embora no modelo RoundRobin a interação seja linear, o Gerente de Projeto atuou como o pacificador na etapa final, sugerindo o uso de bibliotecas de gráficos leves (ex: Chart.js) para atender ambos: estética e performance.

### 3. Riscos de Agentes Mal Configurados (Por Agente) 

Se os prompts fossem mal escritos, os seguintes riscos surgiriam:

**Líder Técnico**: Poderia não definir o escopo claramente, fazendo a equipe trabalhar em funcionalidades inúteis.

**Analista**: Poderia ignorar requisitos legais (LGPD), expondo o cliente a multas.

**Arquiteto**: Poderia escolher tecnologias obsoletas ou caras demais para uma PME.

**Designer**: Poderia criar uma interface linda, mas funcionalmente confusa.

**Dev. Lógica**: Poderia criar regras de cálculo de carbono erradas (fator de emissão incorreto).

**Dev. Interface**: Poderia criar código não responsivo (não funciona no celular).

**Tester**: Se fosse muito "bonzinho" (prompt fraco), deixaria passar bugs críticos.

**Gerente**: Poderia ser passivo e não alertar sobre atrasos ou riscos de integração.

**Redator**: Poderia gerar um texto com alucinações ou linguagem informal demais.

### 4. Melhorias na Coordenação Multiagente 

**Mudança de Fluxo**: A estrutura RoundRobin é rígida. Uma melhoria seria usar o SelectorGroupChat (seleção dinâmica), onde o Líder poderia "chamar" o Arquiteto de volta se o Tester encontrasse um erro grave, criando um ciclo de correção mais realista (Hub-and-Spoke).

**Feedback Humano**: Implementar uma etapa de UserProxy no meio do processo para validar os requisitos antes de prosseguir para o código.
