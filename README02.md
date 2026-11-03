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
- **P1 - Descentralização de dados:** atualmente, a imobiliária utiliza diversos sistemas e ferramentas (planilhas excel, registros em papéis) para guardar dados dos clientes, compras, vendas, contratos, encomendas de imóveis etc, demandando muito tempo para reunir informações e aplicá-las em processos (geração de contratos, recomendação de imóveis por encomenda etc)  
  
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

### **Processos de negócio:**

**Principais processos mapeados:** 

- **Cadastro de clientes e proprietários:** Clientes preenchem suas informações (nome completo, telefone e e-mail) para ter acesso aos imóveis por meio de contato com os corretores, seja pelo envio de mensagens direto pelo site ou via WhatsApp da imobiliária, sendo registrados automaticamente no banco pelo site ou manualmente pelo corretor que recebeu a mensagem. Proprietários se registram na plataforma (nome completo, telefone e e-mail) ao registrarem seus imóveis, o registro passa pela avaliação de um corretor, que filtra e aprova os cadastros de acordo com os requisitos (fotos em boa qualidade de todos os cômodos e todos os campos preenchidos).

- **Cadastro de imóveis:** Um proprietário pode cadastrar seu próprio imóvel, preenchendo suas informações pessoais (nome completo, telefone e e-mail) e as características do imóvel (endereço completo, tipo de oferta, preço, quantidade de vagas, quartos e banheiros, etc), que serão enviadas e sujeitadas a aprovação por um dos corretores. Os corretores também podem cadastrar imóveis, mediante contrato de autorização de corretagem assinado por ambas as partes (corretor e proprietário), declarando todas as características do imóvel, bem como outras clausulas pertinentes.

- **Cadastro de corretores:** Corretores que queiram integram o time podem enviar suas informações (nome completo, telefone e e-mail) com link URL do perfil no LinkedIn ou anexar seu currículo, sendo sujeitados a avaliação da diretora da imobiliária. Caso se tornem parte da equipe, a diretora quem realiza o cadastro, inserindo nome completo, telefone, e-mail e quais idiomas fala, bem como os imóveis pelos quais está responsável pela corretagem, separados por venda ou locação.

- **Assinatura de contrato:** Após enviarem todas as informações pertinentes a elaboração do contrato para o time jurídico externo, a imobiliária recebe o contrato e o submete às demais partes interessadas (proprietário e comprador/locador), que podem assinar de maneira virtual ou presencial.

- **Agendamento e realização de visitas:** Após o cliente manifestar interesse por um imóvel, ele acessa a página deste imóvel na plataforma e clica no botão "Agendar visita", que exibe os campos de decisão do dia e horário da visita, bem como deixar uma mensagem. O sistema envia essas informações para a caixa de mensagens do corretor responsável por aquele imóvel, o notificando de que há uma nova agenda pendente. (incompleto(?)

- **Encomenda de imóveis (preenchimento de informações do imóvel desejado que gera um alerta em e-mail ou telefone se encontrado);** Caso o usuário navegue por toda a plataforma e não encontre um imóvel ao seu gosto, ele realiza a encomenda de um imóvel, preenchendo nome completo, telefone, e-mail e a descrição do que procura. Os corretores recebem aquela solicitação e caso encontrem um imóvel que se encaixe naquela descrição, enviam um e-mail para o usuário.

- **Proposta e negociação:** Após um cliente se interessar por um imóvel, ele entra em contato com o corretor via telefone ou no botão "Enviar mensagem" na página do imóvel. Os corretores recebem a mensagem e formalizam a proposta, que depois de ser aceita pelo proprietário, a imobiliária solicita os documentos<sup>**1,2**</sup> do imóvel e os documentos do proprietário<sup>**3**</sup>. Caso tudo esteja regular e o pagamento for a vista, as partes interessadas formalizam no cartório com assinatura de escrituras públicas, caso seja um imóvel financiado, tudo é enviado ao correspondente bancário da imobiliária e ele dá andamento.

- **Comissão:** Após a negociação ser firmada com a assinatura do contrato, o corretor tem direito a 6% do valor da venda, que é pago pelo vendedor, sendo esses 6% divididos entre corretor e imobiliária, ficando 50% para cada.

- **Administração da locação (Cobrança e repasse de aluguéis):** A imobiliária atua como mediadora financeira, consolidando o valor e os encargos (IPTU e condomínio, se houver), em um único boleto, envia ao locatário e faz a conciliação bancária assim que o pagamento é efetuado. Dessa quantia, é descontada a taxa de administração devida à imobiliária, além de eventuais despesas autorizadas de manutenção ou retenções de impostos. Depois da compensação, o valor líquido é transferido para a conta do proprietário dentro do prazo contratual (até 5 dias úteis) , acompanhado de um extrato detalhado da transação. Em caso de atraso ou inadimplência, a imobiliária executa a régua de cobrança com aplicação de multa e juros e, se necessário, aciona as garantias locatícias do contrato — como seguro fiança, fiadores ou a cláusula de aluguel garantido — para assegurar o recebimento dos valores.

- **Vistoria de entrada e saída:** Antes da assinatura de contrato, o corretor responsável elabora um laudo que registra as condições de pintura, instalações e hidráulicas, pisos, revestimentos, portas, janelas e qualquer mobília existente, com fotos anexadas. Esse documento é validado por ambas as partes (locador e locatário) e assinado antes da entrega oficial de chaves. No encerramento do contrato, a vistoria de saída compara o estado atual do imóvel com o laudo inicial para identificar se houve danos extraordinários causados pelo uso indevido ou falta de manutenção por parte do locatário. O inquilino não responde pelo desgastes naturais decorrentes do uso regular do imóvel ao longo do tempo, mas fica obrigado a reparar estragos causados por mau uso, como furos não autorizados em azulejos ou avarias em equipamentos. Uma vez constatada a igualdade com a vistoria inicial ou finalizados os reparos devidos, o imóvel é recebido e o contrato é formalmente rescindido com a devolução das chaves.

**Processos prováveis não incluídos:**

- **Ações jurídicas :** A imobiliária contrata um time jurídico externo, que processa, elabora, emite e cuida dos contratos aplicados na organização, bem como auxilia na verificação dos d.

- **Anúncio e divulgação em outros portais:** A imobiliária não possuí uma equipe de marketing ou divulgação, a diretora<sup>**1**</sup> contrata serviços esterno terceirizados para anunciar a página. 
> <sup>**1**</sup>(Os custos e processos de cada contratação ficam somente a encargo dela, o grupo não obteve acesso a informações detalhadas).

- **Repasse de contas:** Com exceção da divulgação e anúncios em portais externos, que é de responsabilidade da diretora da imobiliária, o repasse de contas internas e demais rotinas financeiras internas (salário, benefícios, comissões) são organizadas por um agente financeiro externo. (novamente, a equipe não obteve acesso a detalhes desses processos)

> <sup>**1**</sup> **Venda:** Certidão de Matrícula no CRI (Cartório de Registro de Imóveis) atualizada (atesta quem é o dono real e se não há pendências jurídicas), certidão negativa de débitos IPTU, declaração de quitação de débitos condominiais, caso seja um imóvel localizado em condomínio, certidão Negativa de Utilidade Pública / Desapropriação. (todos estes documentos verificam se o imóvel não possuí dívidas ou pendências financeiras antes de ser vendido)  
> <sup>**2**</sup> **Locação:** Cópia da matrícula ou da escritura, comprovante de IPTU e condomínio, laudo de vistoria inicial (se optado pelo locador), garantia locatícia (**Fiador:** matrícula atualizada de um imóvel quitado em nome do fiador + comprovação de renda; **Seguro-Fiança:** Análise aprovada diretamente pela seguradora ou comprovante de aporte da apólice; **Caução** (até 3 aluguéis): Comprovante de depósito em conta poupança conjunta/vinculada.)

> <sup>**3**</sup>Certidões dos Distribuidores Cíveis e Criminais (verifica a ficha criminal e possíveis processos pendentes), Certidão Negativa de Débitos Trabalhistas, Certidão Conjunta de Débitos Relativos a Tributos Federais e à Dívida Ativa da União (regularidade na Receita Federal e Procuradoria-Geral da Fazenda Nacional), Certidão dos Protestos de Títulos e comprovantes de renda

---

### **Requisitos:**

**Requisitos Funcionais:**

- **RF01:** O sistema deve permitir o cadastro de usuários padrão, contemplando clientes e proprietários de imóveis em um mesmo tipo de conta, com nome completo, telefone e e-mail. Cada usuário deverá ter acesso somente às informações relacionadas ao seu próprio cadastro e à sua participação nas negociações.

- **RF02:** O sistema deve permitir o cadastro de corretores como usuários privilegiados, com nome completo, CRECI (código de registro no Conselho Regional de Corretores de Imóveis), telefone, e-mail, idiomas falados e status na plataforma (ativo, afastado, férias ou demitido), com permissões de acesso às informações relacionadas às negociações sob sua responsabilidade.

- **RF03:** O sistema deve permitir que usuários privilegiados autorizados realizem o cadastro de imóveis, vinculando cada imóvel ao seu respectivo proprietário e registrando área em metros quadrados, preço, finalidade, tipo de oferta (venda ou locação), status do imóvel, IPTU, quantidade de vagas de garagem, quartos e banheiros, tipo de imóvel e suas respectivas fotos.

- **RF04:** O sistema deve permitir o cadastro e armazenamento de contratos por usuários privilegiados autorizados, contendo suas principais informações, como preço, tipo (compra ou locação), forma de pagamento, data de início e data de finalização, quando aplicável. Os usuários padrão que participarem de uma negociação poderão consultar os respectivos contratos, enquanto os corretores poderão consultar os contratos vinculados às negociações sob sua responsabilidade.

- **RF05:** O sistema deve permitir que um usuário encomende um imóvel, inserindo a descrição, cidade e bairro desejados, bem como uma faixa de valor (máximo e mínimo);

- **RF06:** O sistema deve armazenar a data em que uma encomenda de imóvel é realizada e seu status atual (não atendida, em análise ou concluída);

- **RF07:** O sistema deve permitir que corretores registrem visitas realizadas ou agendadas aos imóveis, informando data, horário, cliente relacionado e anotações pertinentes, permitindo a consulta dos registros pelos corretores responsáveis e pelos usuários padrão envolvidos na respectiva visita, conforme suas permissões de acesso.

- **RF08:** O sistema deve permitir que os usuários busquem imóveis, informando sua pretensão (compra, locação, visualizar imóveis novos ou pesquisa por código) e tipo de imóvel, utilizando ou não filtros de busca (preço, região, quantidade de quartos, banheiros etc);

- **RF09:** O sistema deve permitir que usuários padrão agendem visitas diretamente na página do imóvel, selecionando data e horário e informando nome completo, telefone e e-mail. As informações do agendamento deverão ficar disponíveis para o corretor responsável e para os usuários envolvidos na visita, respeitando as permissões de acesso.

- **RF10:** O sistema deve permitir que os usuários enviem mensagens aos corretores, se identificando com nome completo, telefone e e-mail;

- **RF11:** O sistema deve permitir que os clientes que encomendaram imóveis na plataforma recebam recomendações de imóveis pelos meios de contato disponibilizados durante o processo de encomenda (SMS, ligações ou e-mails);

- **RF12:** O sistema deve permitir que corretores cadastrados na plataforma recebam mensagens de clientes, filtrando-as por lidas ou não lidas;

- **RF13:** O sistema deve permitir que corretores cadastrados visualizem e gerenciem os registros de visitas relacionados aos imóveis e clientes sob sua responsabilidade, respeitando as permissões de acesso estabelecidas.

- **RF14:** O sistema deve estabelecer níveis de acesso conforme o tipo de usuário, contemplando usuários padrão (clientes e proprietários) e usuários privilegiados da imobiliária. Os usuários privilegiados deverão possuir permissões específicas de acordo com suas funções, distinguindo as atividades dos corretores e dos administradores, enquanto os usuários padrão poderão consultar e atualizar seus próprios dados e acessar somente as informações relacionadas à sua participação nas negociações.

---
  
**Requisitos Não Funcionais:**

- **RNF01 — Segurança da Informação:** O sistema deverá exigir autenticação para o acesso às informações restritas, controlar as permissões dos usuários e utilizar conexões criptografadas para proteger a transmissão de dados pessoais e contratuais;

- **RNF02 — Usabilidade:** O sistema deverá apresentar interface intuitiva, com menus identificados, linguagem simples e funcionalidades claramente organizadas, permitindo que os usuários realizem operações de cadastro e consulta sem necessidade de conhecimentos técnicos avançados;

- **RNF03 — Disponibilidade:** O sistema deverá apresentar disponibilidade mínima de 99% durante o horário de funcionamento da imobiliária, considerando períodos mensais de operação e excluindo manutenções previamente programadas;

- **RNF04 — Compatibilidade e Desempenho:** O sistema deverá ser compatível com computadores e dispositivos móveis, adaptando sua interface aos diferentes tamanhos de tela. Em condições de teste documentadas, pelo menos 95% das consultas deverão apresentar resultados em até 3 segundos, considerando uma base de 1.000 imóveis cadastrados;

- **RNF05 — Acessibilidade:** O sistema deverá permitir navegação por teclado nas principais funcionalidades, apresentar identificação textual nos campos e botões e manter contraste adequado entre textos e elementos visuais, facilitando sua utilização por pessoas com diferentes necessidades de acesso;

**Requisitos prováveis não incluídos:** O sistema não permite que os clientes visualizem as visitas que já realizaram, somente os corretores possuem essa visão, visto que dentro da organização somente corretores podem registrar visitas realizadas.

---

### **Regras de negócio**

**Regras operacionais:**

- **RN01:** Apenas indivíduos com maioridade podem anunciar, comprar ou alugar um imóvel;

- **RN02:** Um imóvel só pode ser alugado ou vendido se estiver disponível; 

- **RN03:** Um imóvel só pode ser alugado, vendido ou comprado por um cliente cadastrado na plataforma;

- **RN04:** O cliente só pode comprar ou alugar um imóvel mediante a comprovante de renda (holerite); 

- **RN05:** Nenhum imóvel pode ser cadastrado na plataforma com ausência de imagens em boa qualidade

- **RN06:** Todo imóvel cadastrado deverá estar vinculado a pelo menos um proprietário, sendo permitida a existência de múltiplos proprietários para um mesmo imóvel.  

- **RN07:** Um imóvel poderá possuir múltiplos contratos ao longo do tempo, desde que não existam contratos ativos simultâneos que representem negociações incompatíveis sobre o mesmo imóvel.

- **RN08:** Uma visita somente poderá ser agendada para um imóvel devidamente cadastrado na imobiliária, devendo estar vinculada ao cliente interessado e ao corretor responsável pelo acompanhamento.

- **RN09:** Um cliente pode comprar ou alugar um imóvel sem obrigatoriamente visitá-lo

- **RN10:** Uma visita só pode ser realizada com o acompanhamento de um corretor cadastrado na plataforma.

- **RN11:** Um mesmo corretor não poderá ser designado para acompanhar visitas diferentes em horários conflitantes.

- **RN12:** Todo contrato deverá estar vinculado a pelo menos um imóvel, um cliente participante e um corretor responsável pela intermediação.

- **RN13:** A situação de disponibilidade do imóvel deverá ser atualizada após a formalização de uma negociação que impeça novas ofertas incompatíveis.

- **RN14:** Toda transação imobiliária deverá ser realizada por um corretor com registro CRECI ativo e situação funcional regular no sistema, não sendo permitida a participação de corretores afastados ou demitidos.

- **RN15:** Um proprietário pode conceder exclusividade de corretagem a um corretor mediante a contrato, com prazo definido entre 60 e 180 dias.

- **RN16:** Uma negociação só pode ser concluída (assinatura de contrato e entrega das chaves) mediante análise dos documentos do imóvel e do proprietário, como mencionado nos processos de negócio.

**Restrições legais e organizacionais:**

- **RN01 - Conformidade com a LGPD:** a imobiliária não pode armazenar nem compartilhar documentos pessoais de clientes (CPF, comprovante de renda, escrituras) em plataformas abertas sem criptografia, consentimento explícito assinado e politica de privacidade disponível para leitura;

- **RN02 - Exigência do CRECI:** Todos os anúncios, contratos e transações precisam registrar formalmente o número do CRECI do corretor responsável e da imobiliária, sob pena de autuação e multa.

- **RN03 - Lei do inquilinato<sup>**4**</sup>:** Todos os contratos de aluguel devem seguir as normas de regulamentação da Lei nº 8.245/91, com direitos e deveres do locador e do locatário, bem como todos os processos que acompanham a locação.

- **RN03 - Percentual de comissão:** Todo corretor tem direito a comissão por cada venda ou locação que intermedia, sendo de 6% para vendas, um valor equivalente ao primeiro mês de aluguel em casos de locação e 30% em casos de locação por temporada, que dura até 90 dias.

- **RN04 - Autorização ou exclusividade:** O anúncio público de um imóvel só pode ocorrer mediante assinatura de contrato de autorização, podendo ou não conceder exclusividade em uma das clausulas, de acordo com o art.5 da Lei nº 6.530/1978.

- **RN05: - Repasse do aluguel (Lei do Inquilinato (Lei nº 8.245/91)):** Toda imobiliária que realiza corretagem em locações deve repassar os aluguéis aos proprietários, sujeitos a prazos e condições definidas em contrato de locação.

> <sup>**4**</sup>**O contratos devem obrigatoriamente possuir:**  
  **Identificação das partes:** dados do locador, do inquilino e, quando houver, do fiador;  
  **Descrição do imóvel:** endereço, características e finalidade da locação;  
  **Prazo:** início, duração e condições para encerrar o contrato;  
  **Pagamento:** valor do aluguel, vencimento e forma de pagamento;  
  **Reajuste:** índice, periodicidade e data de aplicação;  
  **Garantias financeiras:** modalidade escolhida<sup> **5** </sup> ) suas condições;  
  **Despesas:** divisão de encargos, como IPTU, condomínio e seguro;  
  **Rescisão:** multa e condições para a saída antecipada;  
  **Entrega e devolução:** registro do estado do imóvel e procedimentos para devolver as chaves. 
  
> <sup> **5:** </sup> **Caução:** valor de 3 meses de aluguel ou bens; **Fiança:** um fiador responsável pelas obrigações garantidas; **Seguro-fiança locatícia:** uma seguradora oferece cobertura conforme as condições da apólice.

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

- **PROPRIETARIO:**
  ID_PROPRIETARIO (PK)

- **IMOVEL:**
  ID_IMOVEL (PK)

- **CONTRATO:**
   ID_CONTRATO (PK), ID_IMOVEL (FK)

- **CLIENTE:**
   ID_CLIENTE (PK)

- **CORRETOR:**
   ID_CORRETOR (PK)

- **ENCOMENDA:**
   ID_ENCOMENDA (PK), ID_CLIENTE (FK)

- **VISITA:**
   ID_VISITA (PK), ID_IMOVEL (FK)

- **DOCUMENTO:**
   ID_DOC (PK)

- **AGENDA:**
   ID_VISTA (FK), ID_CLIENTE (FK)

- **REALIZA:**
   ID_VISITA (FK), ID_CORRETOR (FK)

- **REGISTRA:**
   ID_DOC (FK), ID_CORRETOR (FK)

- **POSSUI:**
   ID_IMOVEL (FK), ID_PROPRIETARIO (FK)

- **ASSINA:**
   ID_CONTRATO (FK), ID_CLIENTE (FK)

- **INTERMEDIA:**
   ID_CORRETOR (FK), ID_CONTRATO (FK)

- **FOTOS_IMOVEL:**
   FOTOS_IMOVEL (PK), ID_IMOVEL (FK)

- **IDIOMA:**
   IDIOMA (PK), ID_CORRETOR (FK)
  
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

- **Informações estratégicas**
- A centralização das informações no banco de dados permitirá à VISTA ATLANTICO IMOVEIS obter uma visão mais organizada de suas operações comerciais , facilitando  acompanhamento da carteira de imoveis , dos clientes , dos proprietáios , dos corretores , das visitas e dos contratos. Aparti dessas informações , a imobiliaria poderá acompanhar indicadores relacionados a disponibilidade dos imoveis, à movimentações de visitas , ao volume de negociações e ao desempenho comercial dos corretores. Essas informações poderão auxiliar a gestão na identificação de oportunidade de negocio, no acompanhamneto dos resultados, e no planejamento das atividades comercias, considerando também as variações sazonais da procura por imovéis na região da baixada santista.
  
- **Indicadores e métricas gerenciais** propostos (KPIs):
- 
-   
- **Potencial dos dados para BI:**
- A utlilização de ferramentas de Business Intlligence poderá transformar os dados armazenados no banco em paineis gerenciaveis e relatorios visuais, facilitando a interpretação dos resultados pela administração da imobiliaria. entre as possibilidades de aplicação , destacam-se:
- Painel de desempenho da imobiiaria: apresentaçao da quantidade de imoveis cadastrados , disponiveis e distribuidos por tipo e finalidade.
- Painel de desempenho comercial: acompanhamento da quantidade de contratos , valores negociados e participação dos corretores nas negociações.
- Relatório de visitas : identificação dos imoveis mais visitados e acompanhamento da movimentação de interessados.
- Análise temporal: comparação mensal dos registros de visitas e contratos, permitindo observar períodos de maior ou menor movimentação comercial.
Essas ferramentas poderão contribuir para uma gestão baseada em dados, reduzindo a dependência de controles decentralizados e facilitando o acesso às informações estratégicas. 
-
- - **Aplicações analíticas e de IA:**
  -A estrutura de dados proposta poderá servir como base para futuras aplicações de Inteligência Artificial, com a finalidade de apoiar os processos comerciais e melhorar o atendimento aos clientes.
As principais possibilidades identificadas são:

- Sistema de recomendação de imóveis: utilização de algoritmos para recomendar imóveis aos clientes de acordo com critérios como localização, faixa de preço, tipo de imóvel, quantidade de quartos, banheiros e vagas de garagem. Para essa aplicação, será necessário armazenar as preferências e os critérios de busca dos clientes.
- Análise do interesse dos clientes: utilização dos registros de visitas para identificar quais imóveis despertam maior interesse, considerando a frequência de visitação e as características dos imóveis.
- Previsão de demanda imobiliária: aplicação de modelos analíticos sobre dados históricos de visitas e contratos para identificar padrões de procura ao longo dos meses e auxiliar no planejamento comercial.
- Análise de desempenho dos corretores: utilização dos registros de visitas e contratos para identificar padrões de desempenho e apoiar a distribuição de oportunidades comerciais.
As aplicações apresentadas representam possibilidades futuras, não funcionalidades já implementadas. Sua viabilidade dependerá da disponibilidade de dados históricos suficientes, da qualidade das informações armazenadas e da validação dos resultados obtidos pelos modelos analíticos.

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
