# Entrega 2 — Modelo Lógico, Implementação SQL e Apresentação Final

## 1\. Relatório Técnico Final

### Integrantes
| Nome completo do aluno | RGM | Usuário do GitHub |
| :---- | :---- | :---- |
| Alice de Lima | RGM 47612614| detailice (usuário ativo) e AliceLima (conta antiga) |
| Laura Sophia Collado | RGM 48128406 | Laura-collado |
| Nicole Xavier | RGM 48329002 | NicoleXaav |
| Paulo Ricardo Freitas | RGM 47917687 | pauloneymar400-cloud |
| Thiago Barbante | RGM 47856564 | tbarbante |


### 1.1 Revisão do Modelo Conceitual

### **Caracterização da organização:**

- **Nome e natureza da organização:** VISTA ATLANTICO NEGOCIOS IMOBILIARIOS LTDA  
- **Razão Social:** Vista Atlântico Negócios Imobiliários LTDA (Nome Fantasia: Vista Atlântico Imóveis)  
- **CNPJ:** 55.866.811/0001-61 (Ativa na Receita Federal do Brasil)  
- **Registro de Classe:** CRECI 46844-J  
- **Endereço Completo:** Rua Tupi, 50 – Vila Tupi, Praia Grande - SP, CEP 11703-260  
- **Telefone / WhatsApp de Contato:** +55 11 96094-7604  
- **Website Oficial:** www.vistaatlanticoimoveis.com.br  
- **Presença no Google / Maps:** https://maps.google.com/?cid=15350459088759669626
  
### **Contexto e porte:**

- **Fins lucrativos:** Com fins lucrativos. A empresa é registrada como uma Sociedade Empresária Limitada (Ltda.) voltada ao setor privado.  
- **Tamanho da operação:** Classificada no regime de EPP (Empresa de Pequeno Porte). Tem sede localizada em Praia Grande / SP.  
- **Número de pessoas envolvidas:** 8  
- **Volume de atividades:** Atua no ramo imobiliário. A empresa registra uma carteira com cerca de 900 a 1.000 anúncios de imóveis disponíveis na região da Baixada Santista/Praia Grande. Não realiza doações públicas, rituais ou eventos de caráter comunitário/religioso.  

### **Problemas e necessidades identificados:**  
- **P1 - Descentralização de dados:** atualmente, a imobiliária utiliza diversos sistemas e ferramentas para guardar dados dos clientes, compras, vendas, contratos, encomendas de imóveis etc, demandando muito tempo para reunir informações e aplicá-las em processos (geração de contratos, recomendação de imóveis por encomenda etc)  

- **P2 -**
  
**Escopo do sistema:** O banco de dados armazenará dados pertinentes aos principais processos da imobiliária, como cadastros (clientes, proprietários e imóveis), compra e/ou locação de imóveis, contratos, visitas e encomendas. Estes dados são utilizados pelos corretores, analistas jurídicos e serviços terceirizados (divulgação dos anúncios da página da imobiliária).
  
**Justificativa da escolha:** A organização foi selecionada devido à proximidade e abertura do contato com a direção, comandada pela prima de uma das integrantes da equipe. Outro fator determinante foi o volume de seu portfólio e a oscilação sazonal no fluxo de clientes, típica de períodos como o inverno.  

- **Evidências da organização:** Inseridas no repositório, pasta "LEVANTAMENTO".

- **Responsável pela organização:**

**Relato da entrevista**
- **Quem:** 
- **Quando e onde:** 
- **Comprovação:**
- **O que foi levantado:** 

---

**Processos de negócio:**

---

### **Requisitos:**

**Requisitos Funcionais:**

- **RF01:** O sistema deve permitir o cadastro de clientes como usuários, com nome completo, telefone e e-mail;

- **RF02:** O sistema deve permitir o cadastro de corretores como usuários, com nome completo, CRECI (código de registro no Conselho Regional de Corretores de Imóveis), telefone, e-mail, idiomas falados e status na plataforma (ativo, afastado, férias ou demitido);

- **RF03:** O sistema deve permitir o cadastro de imóveis, com a área em metros quadrados, preço, finalidade, tipo de oferta (venda ou locação), status do imóvel (disponível, em obras, indisponível etc), IPTU, quantidade de vagas de garagem, quartos e banheiros, bem como o tipo de imóvel (casa, apartamento, estúdio, sobrado, terreno etc) e suas fotos;

- **RF04:** O sistema deve permitir o armazenamento de contratos e suas principais informações: preço, tipo (compra ou locação), forma de pagamento, data de início e data de finalização (em casos de locação);

- **RF05:** O sistema deve permitir que um usuário encomende um imóvel, inserindo a descrição, cidade e bairro desejados, bem como uma faixa de valor (máximo e mínimo);

- **RF06:** O sistema deve armazenar a data em que uma encomenda de imóvel é realizada e seu status atual (não atendida, em análise ou concluída);

- **RF07:** O sistema deve permitir que um corretor registre cada visita realizada à um imóvel, com data, horário e anotações;

- **RF08:** O sistema deve permitir que os usuários busquem imóveis, informando sua pretensão (compra, locação, visualizar imóveis novos ou pesquisa por código) e tipo de imóvel, utilizando ou não filtros de busca (preço, região, quantidade de quartos, banheiros etc);

- **RF09:** O sistema deve permitir que os usuários agendem visitas diretamente na página do imóvel, selecionando data, horário, bem como insiram nome completo, telefone e e-mail obrigatóriamente;

- **RF10:** O sistema deve permitir que os usuários enviem mensagens aos corretores, se identificando com nome completo, telefone e e-mail;

- **RF11:** O sistema deve permitir que os clientes que encomendaram imóveis na plataforma recebam recomendações de imóveis pelos meios de contato disponibilizados durante o processo de encomenda (SMS, ligações ou e-mails);

- **RF12:** O sistema deve permitir que corretores cadastrados na plataforma recebam mensagens de clientes, filtrando-as por lidas ou não lidas;

- **RF13:** O sistema deve permitir que corretores cadastrados na plataforma visualizem as visitas marcadas;

---
  
**Requisitos Não Funcionais:**

- **RNF01 — Segurança da Informação:** O sistema deverá exigir autenticação para o acesso às informações restritas, controlar as permissões dos usuários e utilizar conexões criptografadas para proteger a transmissão de dados pessoais e contratuais;

- **RNF02 — Usabilidade:** O sistema deverá apresentar interface intuitiva, com menus identificados, linguagem simples e funcionalidades claramente organizadas, permitindo que os usuários realizem operações de cadastro e consulta sem necessidade de conhecimentos técnicos avançados;

- **RNF03 — Disponibilidade:** O sistema deverá apresentar disponibilidade mínima de 99% durante o horário de funcionamento da imobiliária, considerando períodos mensais de operação e excluindo manutenções previamente programadas;

- **RNF04 — Compatibilidade e Desempenho:** O sistema deverá ser compatível com computadores e dispositivos móveis, adaptando sua interface aos diferentes tamanhos de tela. Em condições de teste documentadas, pelo menos 95% das consultas deverão apresentar resultados em até 3 segundos, considerando uma base de 1.000 imóveis cadastrados;

- **RNF05 — Acessibilidade:** O sistema deverá permitir navegação por teclado nas principais funcionalidades, apresentar identificação textual nos campos e botões e manter contraste adequado entre textos e elementos visuais, facilitando sua utilização por pessoas com diferentes necessidades de acesso;

--- 

**Requisitos prováveis não incluídos:** O sistema não permite que os clientes visualizem as visitas que já realizaram, somente os corretores possuem essa visão, visto que dentro da organização somente corretores podem registrar visitas realizadas.

### **Regras de negócio**

> **Justifique as regras prováveis não incluídas:** se uma regra comum nesse tipo de organização ficou de fora, explique por quê (ex.: a organização não realiza o processo correspondente, ou a regra não se aplica ao porte ou à natureza dela).

**Regras operacionais:**

- **RN01:** Apenas indivíduos com maioridade podem anunciar, comprar ou alugar um imóvel;

- **RN02:** Um imóvel só pode ser alugado ou vendido se estiver disponível; 

- **RN03:** Um imóvel só pode ser alugado, vendido ou comprado por um cliente cadastrado na plataforma;

- **RN04:** O cliente só pode comprar ou alugar um imóvel mediante a comprovante de renda (holerite); 

- **RN05:** Nenhum imóvel pode ser cadastrado na plataforma com ausência de imagens em boa qualidade

- **RN06:** 

- **RN07:**

**Restrições legais e organizacionais:**

- **RN01 - Conformidade com a LGPD:** a imobiliária não pode armazenar nem compartilhar documentos pessoais de clientes (CPF, comprovante de renda, escrituras) em plataformas abertas sem criptografia, consentimento explícito assinado e politica de privacidade disponível para leitura;

- **RN02 - Exigência do CRECI:** Todos os anúncios, contratos e transações precisam registrar formalmente o número do CRECI do corretor responsável e da imobiliária, sob pena de autuação e multa.

---

**Notação do DER conceitual**

**Caso A — mesma organização da Entrega 1**
*Apresente o **DER conceitual revisado**, na notação descrita acima. A revisão parte da correção da Entrega 1 recebida pelo grupo — o DER e os demais itens acima. Para cada apontamento da correção, registre o que foi feito:*
| Apontamento da correção da E1 | O que mudou no trabalho | Por quê |
| :---- | :---- | :---- |
| *ex.: N:N entre PEDIDO e PRODUTO sem quantidade* | *criada a entidade associativa ITEM\_PEDIDO com quantidade e preço praticado* | *sem ela não é possível saber quanto de cada produto foi vendido* |
| *ex.: chaves estrangeiras desenhadas no DER* | *removidas — passam a aparecer só no modelo lógico (seção 2\)* | *FK é decisão do modelo lógico, não do conceitual* |
&nbsp;
*Se o grupo discordar de algum apontamento e mantiver o modelo como estava, registre isso na tabela com a justificativa. Apontamento não citado na tabela é tratado como não corrigido.*

### 1.2 Conversão do Modelo Conceitual para o Modelo Lógico
*(vale 7,5%)*
- **Entidades → Tabelas:** *como cada entidade virou tabela.*  
- **Atributos → Colunas:** *conversão correta dos atributos.*  
- **Relacionamentos → Chaves:** *como os relacionamentos foram traduzidos.*  
- **Cardinalidades:** *como cada cardinalidade (1:1, 1:N, N:N) foi tratada (inclusive tabelas associativas, se houver).*  
- **Generalização/especialização:** *se o DER tiver, qual estratégia de conversão foi usada (tabela única, uma tabela por entidade ou só as especializadas) e por quê.*
### 1.3 Definição de Chaves Primárias e Estrangeiras
*Liste as PKs e FKs de cada tabela (serve de base para a justificativa técnica abaixo).*
### 1.4 Processo de Normalização (1FN, 2FN e 3FN)
*(vale 7,5%)*
- **1FN:** *eliminação de grupos repetitivos/atributos multivalorados.*  
- **2FN:** *eliminação de dependências parciais.*  
- **3FN:** *eliminação de dependências transitivas.*  
- **Justificativa do processo:** *por que cada forma normal foi necessária no seu caso.*
### 1.5 Justificativas Técnicas das Decisões
*(vale 7,5%)*
- Justificar as **chaves primárias** escolhidas.  
- Justificar as **chaves estrangeiras** e os relacionamentos que elas implementam.  
- Justificar as **restrições** aplicadas (unicidade, obrigatoriedade, valores permitidos etc.), citando o código da regra de negócio (`RNxx`) que cada restrição implementa, quando houver.  
- Justificar **decisões arquiteturais** gerais do modelo.
### 1.6 Proposta de Arquitetura Analítica para BI e IA
*(vale 7,5%)*
- **Informações estratégicas** que podem ser extraídas dos dados para a gestão da organização.  
- **Indicadores e métricas gerenciais** propostos (KPIs).  
- **Potencial dos dados para BI:** como a estrutura apoia dashboards/relatórios.  
- **Aplicações analíticas e de IA:** como o modelo pode alimentar análises preditivas, recomendações etc.
**Rastreabilidade:** inclua uma tabela que ligue cada problema declarado na caracterização da organização e cada KPI proposto às tabelas que o sustentam e à consulta do script SQL que o responde (pelo código da consulta — ver seção 3):
| Problema ou KPI | Tabelas envolvidas | Consulta no script |
| :---- | :---- | :---- |
| *ex.: P1 — ruptura de estoque de bebidas* | *PRODUTO, MOVIMENTACAO\_ESTOQUE* | *G03* |
| *ex.: ticket médio por ambiente* | *PEDIDO, ITEM\_PEDIDO, AMBIENTE* | *G05* |
&nbsp;
*KPI sem consulta no script que o calcule não é considerado KPI. Cada problema declarado deve ter pelo menos uma consulta que o responda.*
> **O que é KPI:** *Key Performance Indicator* (indicador-chave de desempenho) é um número que mostra, de forma objetiva, se a organização está indo bem em algo que importa para a gestão dela. Um KPI tem **fórmula** (como é calculado), **período** (por dia, semana, mês) e, de preferência, uma **meta** para comparação. Exemplos: ticket médio por venda, taxa de cancelamento de pedidos, produtos abaixo do estoque mínimo, tempo médio de atendimento, número de beneficiários atendidos por mês, percentual de doações recorrentes. "Melhorar o atendimento" não é KPI; "tempo médio entre o pedido e a entrega, por semana" é.
> **Como levantar:** é recomendável usar pesquisas e ferramentas de IA para descobrir quais indicadores são usados por organizações do mesmo tipo (ex.: "principais KPIs de uma pizzaria", "indicadores de gestão de uma ONG de doação de alimentos") e quais análises de BI e de IA costumam ser aplicadas a elas. Depois, **filtre pelo que o seu banco consegue calcular**: um KPI só vale se as tabelas do modelo tiverem os dados necessários e se houver uma consulta no script que o calcule (ver *Rastreabilidade*, abaixo). Se possível, confirme com o responsável pela organização quais indicadores seriam úteis para ele. Registre esse uso de IA na seção 6\.
---
## 2\. Modelo Lógico Relacional
*(diagrama separado — vale 10% na Dimensão Procedimental)*
O modelo lógico deve seguir a **notação visual do brModelo** para o modelo lógico, como no exemplo abaixo. Informe no README **em qual software ou aplicativo ele foi criado**.
![Exemplo de modelo lógico na notação do brModelo](Exemplo_Logico.png)
| Elemento | Como aparece | No exemplo |
| :---- | :---- | :---- |
| **Tabela** | retângulo com o nome da tabela no topo e uma linha por coluna | `Entity 1`, `Entity 5` |
| **Coluna** | nome da coluna, à esquerda, com o tipo de dado à direita | `Attribute 30` — `INT` |
| **Chave primária** | marca `PK` ao lado do tipo | `Chave 1`, em `Entity 1`; `Chave 50` \+ `Chave 51`, em `Entity 5` (chave primária composta) |
| **Chave estrangeira** | marca `FK` ao lado do tipo | `Chave 3`, em `Entity 4` |
| **Coluna que é chave primária e estrangeira** | marcas `PK, FK` | `Chave 1`, em `Entity 2` |
| **Ligação entre tabelas** | linha entre a tabela da FK e a tabela referenciada, com a cardinalidade `(mín, máx)` em cada ponta | `Entity 3` — `Entity 4`: `(1, 1)` e `(0, n)` |
&nbsp;
Deve apresentar claramente:
- Tabelas  
- Atributos (colunas), com seus tipos de dados  
- Chaves primárias  
- Chaves estrangeiras  
- Cardinalidades já convertidas
As **demais restrições de integridade** — obrigatoriedade (`NOT NULL`), unicidade (`UNIQUE`), valores permitidos (`CHECK`), valores padrão (`DEFAULT`) — não aparecem no diagrama do brModelo e devem ser documentadas no **dicionário de dados** (seção 5\) e implementadas no **script SQL** (seção 3).
---
## 3\. Script SQL Completo
*(arquivo `.sql` — vale 12% na Dimensão Procedimental)*
O script completo é **um arquivo no formato `.sql` disponível no repositório**, de preferência numa pasta chamada **`docs`** (ex.: `docs/script.sql`), com link no README. Script colado só no README, em PDF, em imagem ou em outro formato não é aceito.
**SGBD:** MySQL — o disponível no laboratório ou outra instalação equivalente a que o grupo tenha acesso. O script deve executar no MySQL.
O script deve conter, nesta ordem lógica:
1. `CREATE DATABASE`  
2. `CREATE TABLE` (todas as tabelas, com tipos de dados adequados)  
3. **Constraints** (PK, FK, `NOT NULL`, `UNIQUE`, `CHECK` etc.)  
4. `INSERT INTO` (carga da massa de dados — ver seção 4\)  
5. `SELECT` com `JOIN` (consultas que cruzam múltiplas tabelas)  
6. `UPDATE`  
7. `DELETE`  
8. **Consultas gerenciais** (que respondem perguntas de gestão, ex.: faturamento/arrecadação por período, número de atendimentos/beneficiários)  
9. **Consultas de auditoria** (que verificam consistência/integridade dos dados)
Cada **consulta gerencial** e cada **consulta de auditoria** deve ter um cabeçalho em comentário com um código (`G01`, `G02`… para gerenciais; `A01`, `A02`… para auditoria), a pergunta que ela responde em português e o que ela atende:
```sql
-- G03 — Quais bebidas estão abaixo do estoque mínimo hoje?
-- Atende: P1 (ruptura de estoque de bebidas)
SELECT ...
-- A02 — Existe pedido registrado sem nenhum item?
-- Verifica: RN04 (todo pedido tem ao menos um item)
SELECT ...
```
&nbsp;
- **Consultas gerenciais** respondem aos problemas declarados e aos KPIs da seção 1.6 — pelo menos uma por problema declarado e por KPI.  
- **Consultas de auditoria** verificam regras de negócio, citando o código da regra (`RNxx`) que cada uma confere.  
- Essas mesmas consultas são as usadas na demonstração da apresentação final (seção 7).
*Teste o script do zero (banco vazio) antes de entregar, para garantir que ele executa sem erros.*
---
## 4\. Massa de Dados
*(incluída no script ou em arquivo separado — parte da nota de Implementação SQL, 12%)*
Se a massa de dados ficar em arquivo separado, ele deve seguir a mesma regra do script: **um arquivo no formato `.sql` no repositório**, de preferência na pasta **`docs`** (ex.: `docs/massa_de_dados.sql`), com link no README.
- **Dados reais da organização (nomes de clientes, fiéis, beneficiários, doadores, valores reais etc.) não devem ser utilizados, em respeito à privacidade dessas informações.** A massa de dados deve ser **fictícia**, mas **coerente com as operações modeladas** (mesmos tipos de processo, volumes e regras observados na organização real).  
- Volume de registros **coerente com a realidade da organização** (nada de 3 linhas de exemplo — mas também nada artificialmente inflado sem sentido).  
- **Explique como o volume real da organização** — os números informados em *Contexto e porte* (seção 1.1), como clientes ativos, pedidos por mês, atendimentos por semana, itens no estoque — **justifica a quantidade de registros de cada tabela** da massa de dados.  
- Dados consistentes o suficiente para validar os processos organizacionais modelados (ex.: pedidos que referenciam clientes e produtos existentes, ou doações que referenciam doadores e campanhas existentes).  
- **Variedade e quantidade coerentes com a organização, para que os testes sejam possíveis:** os dados devem cobrir as situações reais — não só o caso comum, mas também pedidos cancelados, clientes sem compras, produtos abaixo do estoque mínimo, pagamentos em formas diferentes, registros em períodos diferentes. Sem essa variedade, as consultas gerenciais e de auditoria (seção 3\) não têm o que mostrar: uma consulta de produtos abaixo do estoque mínimo que retorna vazio não demonstra nada.  
- **Documente o uso de LLMs** para gerar essa massa de dados na seção 6 (**Uso de Inteligência Artificial**), incluindo ferramentas, prompts e ajustes feitos manualmente.
---
## 5\. Repositório GitHub (CHECKLIST)
*(vale 13% — Documentação e Repositório)*
O repositório deve conter:
- Relatório Técnico (no `README.md`)  
- **Dicionário de Dados** atualizado, no modelo do arquivo `02-03g_Exemplo_Dicionario_Dados.pdf` e com as restrições de integridade de cada coluna (obrigatoriedade, unicidade, valores permitidos, valor padrão), em **um único arquivo HTML** no repositório. **Exceção — turma de GTI:** o dicionário é apresentado em **um único arquivo Markdown (`.md`) separado do README**, seguindo o mesmo modelo do `02-03g_Exemplo_Dicionario_Dados.pdf`.  
- Diagramas (DER revisado e modelo lógico)  
- Levantamento (pasta `levantamento`, recomendada) e evidências da organização e da entrevista (fotos JPG ou PNG)  
- Script SQL completo em arquivo `.sql` (de preferência na pasta `docs`)  
- **Histórico de commits** que evidencie o desenvolvimento ao longo do tempo (evite um único commit final)  
- **Evidências de colaboração entre os membros do grupo:** é a listagem de commits do repositório, que deve estar **equilibrada entre os integrantes** — a quantidade de commits deve se distribuir de forma proporcional entre todos os membros do grupo, cada um fazendo commits com a própria conta do GitHub. O integrante precisa ser **identificável na conta do GitHub**: o nome configurado na conta deve ser compatível com o nome do aluno na tabela de Integrantes, onde também deve constar o usuário do GitHub de cada um


## 6\. Uso de Inteligência Artificial
*(documentação obrigatória — não é opcional se o grupo usou IA em qualquer etapa: pesquisa, levantamento de processos, requisitos e regras típicos, escrita, organização de ideias, revisão de texto, geração de massa de dados ou apoio a scripts SQL)*
Para cada uso relevante de ferramenta de IA (ChatGPT, Claude, Gemini, Perplexity etc.), registre:
| Item | O que registrar |
| :---- | :---- |
| **Ferramenta e etapa** | Qual IA foi usada e em qual parte do trabalho (ex.: normalização, geração da massa de dados, escrita de queries SQL, redação do relatório, preparação dos slides). |
| **Motivação** | Por que o grupo recorreu à IA nesse ponto específico. |
| **Prompt(s) utilizados** | Texto exato (ou muito próximo) do que foi perguntado/pedido à IA. |
| **Resposta recebida** | Resumo ou trecho relevante da resposta da IA. |
| **Fontes consultadas e verificadas** | Se a IA citou fontes/dados, quais foram checadas pelo grupo e como. |
| **Trechos rejeitados ou corrigidos** | O que da resposta da IA foi descartado, editado ou corrigido manualmente (ex.: query SQL ajustada, dado fictício alterado), e por quê. |
| **Justificativa da escolha final** | Por que o grupo manteve, adaptou ou rejeitou o que a IA sugeriu. |
| **Reflexão crítica** | Limites, vieses ou erros identificados no uso da IA nessa etapa (ex.: normalização incorreta sugerida pela IA, script SQL com erro de sintaxe, dado fictício incoerente com o volume real da organização). |
&nbsp;
*Se o grupo não usou nenhuma ferramenta de IA em alguma dessas etapas, declare isso explicitamente.*
**Uso de IA observado e não declarado será penalizado.**
