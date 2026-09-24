# Vista Atlântico — Banco de Dados
Repositório criado para o Projeto Semestral de Modelagem de Banco de Dados.  
**Alice de Lima (RGM 47612614), Laura Sophia Collado (RGM 48128406), Lucas Praxedes (RGM 47832550), Paulo Ricardo Freitas (RGM 47917687) e Thiago Barbante (RGM 47856564)**

## 1. Caracterização da Organização

- **Nome e natureza da organização:** VISTA ATLANTICO NEGOCIOS IMOBILIARIOS LTDA

**Contexto e porte:**
- **Fins lucrativos:** Com fins lucrativos. A empresa é registrada como uma Sociedade Empresária Limitada (Ltda.) voltada ao setor privado.
- **Tamanho da operação:** Classificada no regime de EPP (Empresa de Pequeno Porte). Tem sede localizada em Praia Grande / SP.
- **Número de pessoas envolvidas:** 8
- **Volume de atividades:** Atua no ramo imobiliário. A empresa registra uma carteira com cerca de 900 a 1.000 anúncios de imóveis disponíveis na região da Baixada Santista/Praia Grande. Não realiza doações públicas, rituais ou eventos de caráter comunitário/religioso

- **Problemas e necessidades identificados:** A descentralização de dados, gerada pela dependência de planilhas e registros em papel, limita o acesso rápido a informações históricas de vendas, carteira de clientes e dados da equipe interna.

- **Justificativa da escolha:** A organização foi selecionada devido à proximidade e abertura do contato com a direção, comandada pela prima de uma das integrantes da equipe. Outro fator determinante foi o volume de seu portfólio e a oscilação sazonal no fluxo de clientes, típica de períodos como o inverno.

- **Evidências da organização:**
**Razão Social:** Vista Atlântico Negócios Imobiliários LTDA (Nome Fantasia: Vista Atlântico Imóveis)  
**CNPJ:** 55.866.811/0001-61 (Ativa na Receita Federal do Brasil)  
**Registro de Classe:** CRECI 46844-J  
**Endereço Completo:** Rua Tupi, 50 – Vila Tupi, Praia Grande - SP, CEP 11703-260  
**Telefone / WhatsApp de Contato:** +55 11 96094-7604  
**Website Oficial:** www.vistaatlanticoimoveis.com.br  
**Presença no Google / Maps:** https://maps.google.com/?cid=15350459088759669626  

## 2. Processos de Negócio

- **Principais processos mapeados:**  cadastro de clientes; cadastro de imóveis; cadastro de corretores; assinatura de contrato; agendamento de visitas; encomenda de imóveis (preenchimento de informações do imóvel desejado que gera um alerta em e-mail ou telefone se encontrado);  

## 3. Requisitos do Sistema

**3.1 Requisitos Funcionais:**

**Usuário (clientes)**:  
O sistema deve permitir: cadastro de clientes como usuários; cadastro imóveis; busca de imóveis (com ou sem uso de filtros);  agendamento de visitas; envio mensagens aos corretores; encomenda de um imóvel; envio de  mensagem caso a encomenda seja finalizada nos canais de comunicação disponibilizados;

**Usuário (Corretores)**:  
O sistema deve permitir: cadastro de novos corretores; recebimento de mensagens de clientes; exibir os imóveis que cada corretor é responsável; visualizar visitas marcadas; acesso aos contratos; visualização das informações dos imóveis e demais detalhes;

**3.2 Requisitos Não Funcionais:**
Segurança, usabilidade, disponibilidade, versatilidade (bom desempenho em *desktop* e *mobile*) e acessibilidade.

## 4. Regras de Negócio

**Regras operacionais:**  
Apenas indivíduos com maioridade podem anunciar, comprar ou alugar um imóvel;    
Um imóvel só pode ser alugado ou vendido se estiver disponível;   
Um imóvel só pode ser alugado, vendido ou comprado por um cliente cadastrado na plataforma;  
O cliente só pode comprar ou alugar um imóvel mediante a comprovante de renda (holerite);  
Nenhum imóvel pode ser cadastrado na plataforma com ausência de imagens em boa qualidade  

**Restrições organizacionais:** 

**Conformidade com a LGPD:** a imobiliária não pode armazenar nem compartilhar documentos pessoais de clientes (CPF, comprovante de renda, escrituras) em plataformas abertas sem criptografia, consentimento explícito assinado e politica de privacidade disponível para leitura;
  
**Exigência do CRECI:** Todos os anúncios, contratos e transações precisam registrar formalmente o número do CRECI do corretor responsável e da imobiliária, sob pena de autuação e multa.

**Baixa maturidade digital empresarial:** Funcionários e corretores mais velhos de casa tem maior resistência à novas tecnologias, além do uso de equipamentos domésticos e de baixo potencial utilizados no trabalho.


## 5. Dicionário de Dados Conceitual

Para cada entidade identificada, liste:

| Entidade | Relaciona-se com | Cardinalidade |
|----------|-----------|------------------------------|
| Proprietário  | Imovel | 0:N — um proprietário pode ou não ter um imóvel cadastrado |
| Imovel | Contrato | 1:N — um imóvel pode estar em vários contratos  |
| Contrato  | Cliente | 1:N — um contrato é assinado por um ou mais clientes |
| Cliente  | Visita | 1:1 opcional — um cliente pode ou não visitar um imóvel  |
| Visita  | Corretor | 1:1 opcional — um corretor pode ou não acompanhar visitas a um imóvel  |
| Corretor  | Contrato | 1:N — um contrato é assinado por um ou mais clientes  |

VISITA constrói um relacionamento ternário entre CLIENTE e CORRETOR (um cliente se interessa por um imóvel e aciona o corretor, a negociação pode exigir uma visita) 

**PROPRIETARIO** é a pessoa física que possui um imóvel e procura o serviço corretagem da imobiliária 

**IMOVEL** é o bem físico fixo que é anunciado para venda ou locação 

**CONTRATO** é o registro autenticado em cartório acerca da venda, locação ou corretagem de um imóvel 

**CLIENTE** é a pessoa física que procura a plataforma para comprar ou alugar um imóvel. 

**CORRETOR** é a pessoa física formada em curso técnico em Transações Imobiliárias e possui registro válido no Conselho Regional de Corretores de Imóveis.

**VISITA** é o evento no qual um ou mais clientes acompanham um corretor a um imóvel 

### 5.1 **Fluxo de dados**

Cliente se cadastra/loga no sistema → cliente seleciona o tipo de imóvel que deseja visualizar → cliente seleciona o imóvel de interesse, marcando uma visita → o agendamento gera um registro em VISITA, ligando esse CLIENTE a um CORRETOR → a critério do cliente, a negociação pode avançar e gerar um CONTRATO, que é referenciado nos registros do CLIENTE e do CORRETOR → toda leitura ou escrita nessas quatro tabelas é registrada pelo log de acesso do SGBD (§5), o que sustenta auditoria e conformidade com a LGPD (§6). 

### 5.2 Convenções do dicionário
**SGBD:** MySQL 8, mecanismo de armazenamento InnoDB — cuida da persistência dos arquivos de dados, do log de transações (redo/undo) e mantém o índice primário clusterizado por chave. 

**Codificação de caracteres:** utf8mb4 com collation utf8mb4_0900_ai_ci. Escolhida em vez de latin1 por cobrir acentuação do português sem perda em campos de nome e texto livre.

Notação Formal utilizada:

| Símbolo | Significado |
|----------|-----------|
| = | é composto de |
| + | e (conecta elementos obrigatórios) |
| [] | escolha obrigatória entre alternativas|
| @ |identificador (chave primária) |
| * * | comentários fora da estrutura formal |

**Prefixos:** NM_nome, ID_identificador, QT_quantidade, TP_tipo (categorização), IN_ indicador booleano. O caso também utiliza TL_(telefone), EM_(endereço de e-mail), HR_(horário), MQ_(metros quadrados), PR_(preço), LG_(linguas) e DS_(descrição/texto livre), que não estão entre os prefixos padrões, porém seguem os princípios básicos.  

**Versão deste dicionário:** v1.0, 6/setembro/2026. Qualquer alteração de estrutura deve gerar nova revisão registrada nesta seção; a prática atende, ela própria, ao princípio de rastreabilidade exigido pela LGPD (art. 6º, X). 

### 5.3 Dicionário de dados por entidade

**PROPRIETARIO**
> **PROPRIETARIO = ID_PROPRIETARIO + NM_PROPRIETARIO + TL_PROPRIETARIO + EM_PROPRIETARIO**  

**Leitura:** @ID_Proprietário é o identificador único; os outros três campos seguintes são obrigatórios e conectados por +.

| Atributo | Tipo físico | Obrigatório | Significado e relevância |
| -------- | --------- |---------|---------|
| ID_PROPRIETARIO | Integer | Sim (PK) | Identificador do proprietário |
| NM_PROPRIETARIO | Varchar(120) | Sim | Nome completo, que pode ser o nome social declarado ou o nome civil; identifica o proprietário nas negociações e nos contratos.|
| TL_PROPRIETARIO | Varchar(11) | Sim | Número de telefone ativo para contato. Permite um meio de comunicação direta entre o proprietário e a imobiliária.|
| EM_PROPRIETARIO | Varchar(100) | Sim | Endereço de e-mail ativo, possibilita outra forma de comunicação com o proprietário.|

**IMOVEL**
> **IMOVEL = @ID_IMOVEL + ID_PROPRIETARIO + TP_IMOVEL + [TP_VENDA| TP_LOCAÇÃO] + MQ_ÁREA + IN_STATUS + QT_VAGA_GARAGEM + QT_BANHEIROS + QT_QUARTOS + PR_IMOVEL + TP_FINALIDADE + EN_endereço + PR_IPTU** 

**Leitura:** @ID_IMOVEL é identificador único, seguido pelo ID_PROPRIETÁRIO obrigatório, que garante com que todo imóvel possua um proprietário prévio; os outros onze campos são obrigatórios e conectados por +, [TP_VENDA|TP_LOCAÇÃO] exige escolher um tipo de oferta para cadastro e posteriormente filtragem de pesquisa. <sup> *notação formal da escolha obrigatória modificada para compatibilidade com markdown de tabela do github.*</sup>

| Atributo | Tipo físico | Obrigatório | Significado e relevância |
| -------- | --------- |---------|---------|
| ID_IMOVEL | Integer | Sim (PK)| Identificador do imóvel. |
| ID_PROPRIETARIO | Integer | Sim (FK) | Referência ao titular do imóvel em contratos e negociações. |
| TP_IMOVEL | Varchar(50) | Sim | Classificação dos imóveis de acordo com seu tipo; Permite filtragem nas pesquisas no site. |
| TP_OFERTA_VENDA;TP_OFERTA_LOCAÇÃO | Varchar(10) | Sim (escolha) | Modelos de oferta para obtenção de um imóvel, seja de maneira temporária ou permanente; Direciona os clientes de acordo com suas necessidades. |
| MQ_ÁREA | Real | Sim | Área de metros quadrados em cada imóvel; Contextualiza o tamanho dos imóveis. |
| IN_STATUS | Boolean | Sim | Indicador da condição do imóvel; Imóveis já vendidos ou alugados não aparecem nas telas de anuncio e busca, com registros salvos por questões de auditória interna ou juridica. |
| QT_VAGA_GARAGEM | Integer | Sim | Quantidade de vagas de garagem disponíveis; Define um dos critérios para negociação, acerca da necessidade dos clientes. |
| QT_BANHEIROS | Integer | Sim | Quantidade de banheiros contidos no imóvel; Define um dos critérios para negociação, acerca da necessidade dos clientes. |
| QT_QUARTOS | Integer | Sim | Quantidade de quartos contidos no imóvel; Define um dos critérios para negociação, acerca da necessidade dos clientes. |
| PR_IMOVEL | Real | Sim | Preço de negociação do imóvel; Um dos critérios basais para a decisão final dos clientes |
| TP_FINALIDADE | Varchar(50) | Sim | Uso especifico do imóvel; Determinada em contrato, passível de multa ou rescisão contratual em caso de mudança não autorizada |
| EN_IMOVEL | Varchar(120) | Sim | Localização do imóvel|
| PR_IPTU | Real | Sim | Preço do IPTU (Imposto Predial e Territorial Urbano); Um dos dados primordiais em negociações de compra e/ou venda de imóveis |


**CONTRATO**
> **CONTRATO = @ID_CONTRATO + ID_CLIENTE + ID_PROPRIETARIO + ID_CORRETOR + TP_CONTRATO + FORMA_PAGAMENTO + PR_IMÓVEL + DATA_INICIO + (DATA_FIM)**

Leitura: ID_CONTRATO é o identificador único, seguido por outros três identificadores estrangeiros, que garantem que nenhum contrato seja registrado sem as devidas partes; TP_contrato diferencia contratos entre venda e locação, o campo DATA_FIM vêm entre parênteses pois é utilizado somente em contratos de locação.

| Atributo | Tipo físico | Obrigatório | Significado e relevância |
| -------- | --------- |---------|---------|
| ID_CONTRATO | Integer | Sim  (PK)| Código de localização do registro em sistema. |
| ID_CLIENTE | Integer | Sim (FK, único) | Referência ao cliente; Opera como um dos pilares do contrato. |
| ID_PROPRIETARIO | Integer | Sim (FK, único) | Referência ao proprietário; Diz respeito a uma das principais partes interessadas na negociação. |
| ID_CORRETOR | Integer | Sim (FK, único) | Referência ao corretor; De suma importância em negociações com corretagem. |
| FORMA_PAGAMENTO | Text | Sim | Opção escolhida para subsídio do imóvel; Solicitada por lei em contratos imobiliários. |
| PR_IMOVEL | Real | Sim | Preço de negociação do imóvel; dado basal para cálculo de comissão do corretor que mediou a negociação |
| DATA_INICIO | date | Sim | Data em que o contrato entra em vigor; Solicitada por lei em contratos imobiliários. |
| DATA_FIM | date | Não | Data de expiração do contrato; Exigida por lei em contratos de locação. |

**CORRETOR**
> **CORRETOR = @ID_CORRETOR + ID_CRECI + NM_CORRETOR + TL_CORRETOR + EM_CORRETOR + LG_CORRETOR + [TP_ATIVO| TP_AFASTADO|TP_FÉRIAS]** 
Leitura: ID_CRECI usa o prefixo de identificador por ser um registro emitido por órgão externo (Conselho Regional de Corretores de Imóveis), não trata-se de um código interno de domínio; [TP_ATIVO| TP_AFASTADO|TP_FÉRIAS] exige que cada corretor informe seu status de disponibilidade na plataforma. <sup> *notação formal da escolha obrigatória modificada para compatibilidade com markdown de tabela do github.*</sup>

| Atributo | Tipo físico | Obrigatório | Significado e relevância |
| -------- | --------- |---------|---------|
| ID_CORRETOR | Integer | Sim (PK) | Identificador do corretor |
| ID_CRECI | Varchar(20) | Sim (único) | Registro no Conselho Regional de Corretores de Imóveis; exigido por lei para validar atividades de corretagem. |
| NM_CORRETOR | Varchar(120) | SIM | Nome civil ou social completo como constante no Conselho Regional de Corretores de Imóveis; Aparece na assinatura do contrato.|
| TL_CORRETOR | Varchar(11) | Sim | Número de telefone ativo para contato. Permite um meio de comunicação direta com seus clientes. |
| EM_CORRETOR | Varchar(100) | Sim | Endereço de e-mail ativo, possibilita outra forma de comunicação com o corretor.|
| LG_CORRETOR | Text | Sim | Línguas faladas pelo corretor; Orienta a escolha de clientes estrangeiros ou imigrantes recém migrados. |
| TP_ATIVO; TP_AFASTADO; TP_FÉRIAS | Varchar(20) | Sim (escolha)| Indicador de disponibilidade do corretor; Corretores em período de férias ou afastados das funções não são exibidos como agentes disponíveis para contato.|

**CLIENTE**
> **CLIENTE = @ID_CLIENTE + NM_PROPRIETARIO + TL_CLIENTE + EM_CLIENTE**
Leitura:@ID_CLIENTE é o identificador único; os outros três campos seguintes são obrigatórios e conectados por +.

| Atributo | Tipo físico | Obrigatório | Significado e relevância |
| -------- | --------- |---------|---------|
| ID_CLIENTE | Interger | Sim (PK) | Identificador do cliente.|
| NM_CLIENTE | Varchar(120) | Sim | Nome completo, que pode ser o nome social declarado ou o nome civil; identifica o cliente nas negociações e nos contratos.|
| TL_CLIENTE | Varchar(11) | Sim | Número de telefone ativo para contato. Permite um meio de comunicação direta com a imobiliária e o corretor.|
| EM_CLIENTE | Varchar(100) | Sim | Endereço de e-mail ativo, possibilita outra forma de comunicação com a imobiliária e o corretor.|

**VISITA**
> **VISITA = @ID_VISITA + ID_IMOVEL + ID_CLIENTE + ID_CORRETOR + DT_VISITA + TM_HORARIO + DS_ANOTACOES**
Leitura: ID_VISITA é identificador único, as três chaves seguintes são estrangeiras e referenciais aos indivíduos presentes e o local a ser visitado. As anotações são pessoais e ficam a critério do corretor registrá-las ou não.

| Atributo | Tipo físico | Obrigatório | Significado e relevância |
| -------- | --------- |---------|---------|
| ID_VISITA | Integer | Sim (PK) | Identificador da visita. |
| ID_IMOVEL| Integer | Sim (FK)| Referencial do imóvel visitado; impede que visitas sejam marcadas sem um imóvel informado|
| ID_CLIENTE | Integer | Sim (FK) | Referencial do cliente; garante que toda visita possua um par de cliente e corretor |
| ID_CORRETOR | Integer | Sim (FK)| Referencial do corretor; garante que toda visita seja acompanhada por um corretor autenticado na plataforma. |
| DT_VISITA | Data | Sim | Data marcada para visitação de cada imóvel. Necessária para organização da agenda de compromissos de cada corretor. |
| TM_HORARIO | Time | Sim | Horário marcado para visitação do imóvel; Necessária para organização da agenda de compromissos de cada corretor. |
| DS_ANOTACOES | Text | Não | Descrição livre das opiniões e impressores dos clientes.|

### 5.3 Log de acesso (metadado operacional) 
As quatro tabelas ficam sob o mesmo mecanismo de auditoria do SGBD: o plugin audit_log do MySQL, configurado para gravar em formato JSON no caminho definido por audit_log_file (variável de sistema, sob $HOME neste ambiente — nunca sob /tmp, pelas mesmas razões que valem para LibreOffice/ffmpeg). Na ausência do plugin, a alternativa é o log geral (general_log=ON, log_output=TABLE), consultável em mysql.general_log. Retenção e rotação do log seguem política própria, independente da retenção dos dados de negócio. 

### 5.4 Acesso por operação e conformidade com a LGPD

| Tabela | Leitura | Inserção | Atualização | Exclusão |
| ----- | ---- | ----| ----| ----|
| PROPRIETARIO | Corretores; auditoria| Proprietários| Proprietários| Apenas anonimização ao fim da retenção
| IMOVEL | Corretores; clientes; proprietários; auditoria | Proprietários| Proprietários; corretores | Nenhum contrato, apenas dados utilizados para fins comerciais|
| CONTRATO | Corretores; clientes; proprietários; auditoria | Corretores; clientes; proprietários; auditoria | Corretores | Nenhum papel |
| CORRETOR | Corretor; auditoria | Administrativo/RH| Administrativo/RH| Administrativo/RH (desligamento)|
| CLIENTE | Corretor; auditoria | Corretores| Cliente | Apenas anonimização ao fim da retenção|
| VISITA | Corretor autor; auditoria | Corretor| Corretor| Corretor|

## 6. Modelagem Conceitual (Entidades, Atributos, Relacionamentos)

- **Entidades reconhecidas:**

**PROPRIETARIO:** Representa as pessoas físicas detentoras dos direitos de posse dos imóveis cadastrados na imobiliária.  
**IMOVEL:** Representa a unidade imobiliária (casa, apartamento, terreno, etc.) disponível para comercialização ou locação.  
**CLIENTE:** Representa o indivíduo interessado em realizar buscas, agendar visitas e firmar contratos de compra ou aluguel.  
**CORRETOR:** Representa o profissional credenciado encarregado de intermediar negociações, acompanhar visitas e gerenciar contratos.  
**CONTRATO:** Representa o instrumento legal de formalização de uma transação imobiliária de compra ou locação.  
**VISITA:** Representa o registro do evento de visitação presencial a um determinado imóvel.  

- **Atributos e classificações:**

<ins>**PROPRIETARIO**</ins>

**Chave Primária:** ID (Atributo Identificador).  
**Atributo Simples:** NOME, TELEFONE, E-MAIL.  

<ins>**IMOVEL**</ins>

ID_IMOVEL: Atributo Identificador (Chave Primária).  
**Atributo Composto:** ENDEREÇO (desmembrado em logradouro, número e bairro).  
**Atributos Simples:** AREA_M2, VALOR, FINALIDADE, OFERTA, IPTU, QTDE_QUARTOS, QTDE_BANHEIROS, VAGA_GARAGEM, STATUS, TIPO_IMOVEL.  

<ins>**CLIENTE**</ins>

**Chave Primária:** ID (Atributo Identificador).  
**Atributo Simples:** NOME, E-MAIL, TELEFONE.  

<ins>**CORRETOR**</ins>

**Chave Primária:** CRECI (Atributo Identificador).  
**Atributos Simples:** NOME, TELEFONE, E-MAIL, COMISSÃO.  
**Atributo Multivalorado/Composto:** IDIOMAS (opções: Português, Inglês, Espanhol).  
**Atributo Multivalorado/Composto:** STATUS (opções: ativo, férias, afastado).

<ins>**CONTRATO**</ins>

**ID_CONTRATO:** Atributo Identificador (Chave Primária).  
**Atributos Simples:** FORMA_PAGAMENTO, VALOR, DATA_INICIO, DATA_FIM.

<ins>**VISITA**</ins>

**Chave Primária:** ID_VISITA (Atributo Identificador).  
**Atributos Simples:** DATA_VISITA, HORARIO, ANOTACOES_VISITA .

- **Relacionamentos pertinentes:**  
**POSSUI (PROPRIETARIO $\leftrightarrow$ IMOVEL)** Cardinalidade: (0, n) para (1, n) — Um proprietário pode possuir de zero a vários imóveis, e um imóvel pode pertencer a zero ou a múltiplos proprietários.  
**REFERENTE_A (IMOVEL $\leftrightarrow$ CONTRATO)** Cardinalidade: (1, n) para (1, n) — Um imóvel pode ser objeto de zero a vários contratos ao longo do tempo, assim como um contrato pode associar-se a imóveis.  
**ASSINA (CLIENTE $\leftrightarrow$ CONTRATO)** Cardinalidade: (0, n) para (1, n) — Um cliente pode assinar zero ou vários contratos. Um contrato pode ser assinado por um ou mais clientes. Esse relacionamento contém o atributo tipo.  
**REALIZA (CLIENTE $\leftrightarrow$ VISITA)** Cardinalidade: (1,1) para (0, n) - Uma visita só pode ser realizada com um par de cliente(s) e corretor(es)
**REALIZA (CORRETOR $\leftrightarrow$ VISITA)** Cardinalidade: (1, n) para (1, n) — Uma visita só pode ser realizada com um par de cliente(s) e corretor(es).
 
- **Restrições e políticas organizacionais aplicadas ao modelo:**  
**Unicidade de Identificação:** Cada entidade principal possui um atributo identificador único obrigatório (ID para Cliente/Proprietário, CRECI para Corretor, ID_IMOVEL, ID_CONTRATO e ID_VISITA).  
**Controle Operacional do Corretor:** O modelo restringe a gestão de corretores através do rastreamento de disponibilidade operacional (Status: ativo, férias ou afastado) e competência de atendimento por idioma.

## 8. Diagrama Entidade-Relacionamento (DER)

https://app.brmodeloweb.com/publicview/6aaadb52c23c0151509a80d4

## 9. Justificativa Técnica:
A modelagem foi desenvolvida com base na perspectiva de uso externo do sistema, mapeando os requisitos essenciais da rotina da imobiliária a partir da visão do cliente. A separação das entidades foi adotada para deixar clara a função de cada participante e permitir o registro individual de eventos, como as informações de cada visita. Os atributos atendem às necessidades práticas identificadas e as recomendações de segurança e abstração; e a opção pelas cardinalidades garante a flexibilidade do sistema.

## 10. Uso de Inteligência Artificial

| Item | registros|
|--------|----------|
| **Ferramenta e etapa** | Utilizamos o GEMINI 3.6 Flash na formatação do tópico de Relacionamentos Pertinentes |
| **Motivação** | Não sabíamos a melhor maneira de registrar do READ.ME, então preferimos pedir ajuda para organizar o que escrevemos |
| **Prompt(s) utilizados** | "Vou te dar algumas orientações e preciso que você se baseie no diagrama que vou mandar aqui para responder, segue: Relacionamentos pertinentes: como as entidades se conectam. Restrições e políticas organizacionais aplicadas ao modelo."|
| **Resposta recebida** | Relacionamentos pertinentes POSSUI (PROPRIETARIO $\leftrightarrow$ IMOVEL) Cardinalidade: (0, n) para (0, n) — Um proprietário pode possuir de zero a vários imóveis, e um imóvel pode pertencer a zero ou a múltiplos proprietários. (...) |
| **Fontes consultadas e verificadas** | Se a IA citou fontes/dados, quais foram checadas pelo grupo e como (ex.: comparação com o que foi observado na visita de campo). | A fonte usada como base foi o DER que anexamos, comparamos as resposta com ele e com os materiais de aula fornecidos |
| **Trechos rejeitados ou corrigidos** | Corrigimos o espaçamento entre as frases e ajustamos algumas palavras para melhor compreensão da equipe |
| **Justificativa da escolha final** | A resposta do Gemini se baseou no diagrama que fizemos, mas certas partes continham palavras que não utilizamos e trechos que fugiam do que mostramos, em resumo, ela alucinou. |
| **Reflexão crítica** | A IA alucinou em algumas partes, inseriu informações além do necessário e além da compreensão técnica do time acerca do trabalho. |

---
