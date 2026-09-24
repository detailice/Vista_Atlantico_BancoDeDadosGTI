# Entrega 2 — Modelo Lógico, Implementação SQL e Apresentação Final
### Modelagem de um sistema de gestão de informações para uma organização de pequeno porte

> Este arquivo é o esqueleto dos artefatos finais do grupo, a serem organizados no repositório GitHub.
> Preencha cada seção com o conteúdo do seu projeto. Alguns itens são documentos Markdown, outros são arquivos separados (script `.sql`, massa de dados, slides) — está indicado em cada seção.
> Nesta etapa vocês atuam como uma **software house** implementando o banco de dados completo do sistema modelado na Entrega 1 — seja para uma empresa, uma ONG ou outra organização escolhida pelo grupo.
>
> **Lembrete:** termos como "empresa" e "negócio" usados abaixo são o vocabulário técnico padrão de modelagem de dados e se aplicam a qualquer tipo de organização, com ou sem fins lucrativos.
>
> **Importante:** esta etapa dá continuidade à **mesma organização real** escolhida na Entrega 1 — não é permitido trocar para uma organização fictícia ou diferente. O grupo deve manter o acesso à organização, pois pode ser necessário voltar a campo para validar regras, tirar dúvidas sobre o processo de normalização ou conferir se a massa de dados reflete a realidade observada.

---

## 1. Relatório Técnico Final
*(arquivo Markdown — reúne a maior parte da Dimensão Conceitual, 30%)*

### 1.1 Revisão do Modelo Conceitual
*Se necessário, ajuste o DER da Entrega 1 com base no feedback recebido. Explique o que mudou e por quê.*

*Reapresente também as evidências da organização (fotos, link no Google, endereço, forma de contato) — atualizadas se houve uma nova visita nesta etapa.*

### 1.2 Conversão do Modelo Conceitual para o Modelo Lógico
*(vale 7,5%)*
- **Entidades → Tabelas:** *como cada entidade virou tabela.*
- **Atributos → Colunas:** *conversão correta dos atributos.*
- **Relacionamentos → Chaves:** *como os relacionamentos foram traduzidos.*
- **Cardinalidades:** *como cada cardinalidade (1:1, 1:N, N:N) foi tratada (inclusive tabelas associativas, se houver).*

### 1.3 Definição de Chaves Primárias e Estrangeiras
*Liste as PKs e FKs de cada tabela (serve de base para a justificativa técnica abaixo).*

### 1.4 Processo de Normalização (1FN, 2FN e 3FN)
*(vale 7,5%)*
- **1FN:** *eliminação de grupos repetitivos/atributos multivalorados.*
- **2FN:** *eliminação de dependências parciais.*
- **3FN:** *eliminação de dependências transitivas.*
- **Justificativa do processo:** *por que cada forma normal foi necessária no seu caso.*

### 1.5 Justificativas Técnicas das Decisões
*(vale 7,5% — maior peso individual da dimensão conceitual)*
- Justificar as **chaves primárias** escolhidas.
- Justificar as **chaves estrangeiras** e os relacionamentos que elas implementam.
- Justificar as **restrições** aplicadas (unicidade, obrigatoriedade, valores permitidos etc.).
- Justificar **decisões arquiteturais** gerais do modelo.

### 1.6 Proposta de Arquitetura Analítica para BI e IA
*(vale 7,5%)*
- **Informações estratégicas** que podem ser extraídas dos dados para a gestão da organização.
- **Indicadores e métricas gerenciais** propostos (KPIs).
- **Potencial dos dados para BI:** como a estrutura apoia dashboards/relatórios.
- **Aplicações analíticas e de IA:** como o modelo pode alimentar análises preditivas, recomendações etc.

---

## 2. Modelo Lógico Relacional
*(diagrama/documento separado — vale 10% na Dimensão Procedimental)*

Deve apresentar claramente:
- Tabelas
- Atributos (colunas)
- Chaves primárias
- Chaves estrangeiras
- Restrições de integridade
- Cardinalidades já convertidas

---

## 3. Script SQL Completo
*(arquivo `.sql` — vale 12% na Dimensão Procedimental)*

O script deve conter, nesta ordem lógica:
1. `CREATE DATABASE`
2. `CREATE TABLE` (todas as tabelas, com tipos de dados adequados)
3. **Constraints** (PK, FK, `NOT NULL`, `UNIQUE`, `CHECK` etc.)
4. `INSERT INTO` (carga da massa de dados — ver seção 4)
5. `SELECT` com `JOIN` (consultas que cruzam múltiplas tabelas)
6. `UPDATE`
7. `DELETE`
8. **Consultas gerenciais** (que respondem perguntas de gestão, ex.: faturamento/arrecadação por período, número de atendimentos/beneficiários)
9. **Consultas de auditoria** (que verificam consistência/integridade dos dados)

*Teste o script do zero (banco vazio) antes de entregar, para garantir que ele executa sem erros.*

---

## 4. Massa de Dados
*(incluída no script ou em arquivo separado — parte da nota de Implementação SQL, 12%)*

- **Dados reais da organização (nomes de clientes, fiéis, beneficiários, doadores, valores reais etc.) não devem ser utilizados, em respeito à privacidade dessas informações.** A massa de dados deve ser **fictícia**, mas **coerente com as operações modeladas** (mesmos tipos de processo, volumes e regras observados na organização real).
- Volume de registros **coerente com a realidade da organização** (nada de 3 linhas de exemplo — mas também nada artificialmente inflado sem sentido).
- Dados consistentes o suficiente para validar os processos organizacionais modelados (ex.: pedidos que referenciam clientes e produtos existentes, ou doações que referenciam doadores e campanhas existentes).
- **Documente o uso de LLMs** para gerar essa massa de dados na seção **"Uso de Inteligência Artificial"** (item 6), incluindo ferramentas, prompts e ajustes feitos manualmente.

---

## 5. Repositório GitHub
*(vale 13% — Documentação e Repositório)*

O repositório deve conter:
- Documentação técnica em Markdown (Relatório Técnico + **Dicionário de Dados** atualizado)
- Diagramas (DER revisado e modelo lógico)
- Scripts SQL organizados
- **Histórico de commits** que evidencie o desenvolvimento ao longo do tempo (evite um único commit final)
- Evidências de colaboração entre os membros do grupo

---

## 6. Uso de Inteligência Artificial
*(documentação obrigatória — não é opcional se o grupo usou IA em qualquer etapa: pesquisa, escrita, organização de ideias, revisão de texto, geração de massa de dados ou apoio a scripts SQL)*

Para cada uso relevante de ferramenta de IA (ChatGPT, Claude, Gemini, Perplexity etc.), registre:

| Item | O que registrar |
|------|------------------|
| **Ferramenta e etapa** | Qual IA foi usada e em qual parte do trabalho (ex.: normalização, geração da massa de dados, escrita de queries SQL, redação do relatório, preparação dos slides). |
| **Motivação** | Por que o grupo recorreu à IA nesse ponto específico. |
| **Prompt(s) utilizados** | Texto exato (ou muito próximo) do que foi perguntado/pedido à IA. |
| **Resposta recebida** | Resumo ou trecho relevante da resposta da IA. |
| **Fontes consultadas e verificadas** | Se a IA citou fontes/dados, quais foram checadas pelo grupo e como. |
| **Trechos rejeitados ou corrigidos** | O que da resposta da IA foi descartado, editado ou corrigido manualmente (ex.: query SQL ajustada, dado fictício alterado), e por quê. |
| **Justificativa da escolha final** | Por que o grupo manteve, adaptou ou rejeitou o que a IA sugeriu. |
| **Reflexão crítica** | Limites, vieses ou erros identificados no uso da IA nessa etapa (ex.: normalização incorreta sugerida pela IA, script SQL com erro de sintaxe, dado fictício incoerente com o volume real da organização). |

*Se o grupo não usou nenhuma ferramenta de IA em alguma dessas etapas, declare isso explicitamente.*

---

## 7. Apresentação Corporativa Final
*(pitch cronometrado — vale 15%, maior peso individual da Dimensão Procedimental)*

Formato: slides com estética limpa e minimalista — **proibida a leitura de blocos longos de texto**.

Deve conter, nesta ordem:
1. **Contextualização do problema institucional/organizacional** solucionado
2. **Apresentação da solução** proposta
3. **Defesa do modelo lógico** (perguntas do professor e da turma)
4. **Demonstração da implementação** (SQL rodando)
5. **Demonstração de consultas** (gerenciais/auditoria)
6. **Potencial para BI e IA**
7. **Benefícios diretos** para a tomada de decisão da organização

---

## Critérios Atitudinais (20%)
**Estes critérios NÃO constam explicitamente como item de entrega nos artefatos do grupo.** Eles são avaliados por meio de **Avaliação 360º entre os integrantes do grupo** (cada membro avalia os colegas de equipe) e, no caso da colaboração, também pela **colaboração equilibrada no histórico de commits** do repositório GitHub (Seção 5) — não pela leitura do relatório ou pela apresentação:

- **Participação e colaboração (5%):** participação técnica ativa + colaboração com o grupo, incluindo colaboração equilibrada no histórico de commits do repositório GitHub.
- **Responsabilidade (5%):** cumprimento de prazos + entrega dos itens sob sua responsabilidade.
- **Postura profissional (5%):** comunicação profissional + conduta ética.
- **Autonomia e resolução de problemas (5%):** buscar soluções independentes + propor melhorias.

---

## Resumo dos Pesos

| Dimensão | Peso total | Itens principais |
|----------|-----------|-------------------|
| Conceitual | 30% | Conversão conceitual→lógico (7,5%), Normalização (7,5%), Justificativas técnicas (7,5%), Análise BI/IA (7,5%) |
| Procedimental | 50% | Modelo lógico (10%), Implementação SQL (12%), Documentação/repositório (13%), Apresentação final (15%) |
| Atitudinal | 20% | Participação/colaboração, responsabilidade, postura profissional, autonomia |

**Entrega final:** Relatório Técnico + Modelo Lógico + Script SQL + Massa de Dados + Repositório GitHub, seguidos da Apresentação Corporativa Final perante o professor e a turma.
