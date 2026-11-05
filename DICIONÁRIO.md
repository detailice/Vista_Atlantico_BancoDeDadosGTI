## Caso: Dicionário de dados de uma Imobiliária

## 1. Modelo conceitual

Este modelo representa uma imobiliária, na qual cada cliente possui seu cadastro e quando há interesse em alugar, comprar ou anunciar algum imóvel, entra em contato com um corretor. O contato pode gerar uma visita em um imóvel e por fim, um contrato de negociação.

| Entidade | Relaciona-se com | Cardinalidade |
|----------|-----------|------------------------------|
| Proprietário  | Imovel | 0:N — um proprietário pode ou não ter um imóvel cadastrado |
| Imovel | Contrato | 1:N — um imóvel pode estar em vários contratos  |
| Contrato  | Cliente | 1:N — um contrato é assinado por um ou mais clientes |
| Cliente  | Visita | 1:1 opcional — um cliente pode ou não visitar um imóvel  |
| Visita  | Corretor | 1:1 opcional — um corretor pode ou não acompanhar visitas a um imóvel  |
| Corretor  | Contrato | 1:N — um contrato é assinado por um ou mais corretores (co-corretagem)  |
| Cliente  | Encomenda | 1:N — um cliente pode realizar uma ou mais encomendas  |
| Corretor  | Documento | 1:N — um corretor pode registrar um ou mais documentos  |

VISITA constrói um relacionamento ternário entre CLIENTE e CORRETOR (um cliente se interessa por um imóvel e aciona o corretor, a negociação pode exigir uma visita) 

**PROPRIETARIO** é a pessoa física que possui um imóvel e procura o serviço corretagem da imobiliária 

**IMOVEL** é o bem físico fixo que é anunciado para venda ou locação 

**CONTRATO** é o registro autenticado em cartório acerca da venda, locação ou corretagem de um imóvel 

**CLIENTE** é a pessoa física que procura a plataforma para comprar ou alugar um imóvel. 

**CORRETOR** é a pessoa física formada em curso técnico em Transações Imobiliárias e possui registro válido no Conselho Regional de Corretores de Imóveis.

**VISITA** é o evento no qual um ou mais clientes acompanham um corretor a um imóvel 

**ENCOMENDA** é o preenchimento de informações do imóvel desejado que gera um alerta por e-mail ou telefone se encontrado para o cliente

**DOCUMENTO** é o documento de negociação resgistrado pelo corretor

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
| ( ) | Dados opcionais |

> A notação formal possuí outros símbolos, que não foram utilizados por não serem pertinentes aos tipos de dados e suas formatações referentes ao presente contexto.

**Prefixos:** NM_nome, ID_identificador, QT_quantidade, TP_tipo (categorização), IN_ indicador booleano, DT_data. O caso também utiliza TL_(telefone), EN_(endereço), EM_(endereço de e-mail), HR_(horário), MQ_(metros quadrados), VL_(valor), LG_(linguas) e DS_(descrição/texto livre), NM_(número), que não estão entre os prefixos padrões, porém seguem os princípios básicos.  

**Versão deste dicionário:** v1.0, 6/setembro/2026. Qualquer alteração de estrutura deve gerar nova revisão registrada nesta seção; a prática atende, ela própria, ao princípio de rastreabilidade exigido pela LGPD (art. 6º, X). 

### 5.3 Dicionário de dados por entidade

**PROPRIETARIO**
> **PROPRIETARIO = @ID_PROPRIETARIO + NM_PROPRIETARIO + TL_PROPRIETARIO + EM_PROPRIETARIO**  

**Leitura:** @ID_Proprietário é o identificador único; os outros três campos seguintes são obrigatórios e conectados por +.

| Atributo | Tipo físico | Obrigatório | Significado e relevância |
| -------- | --------- |---------|---------|
| ID_PROPRIETARIO | Integer | Sim (PK) | Identificador do proprietário |
| NM_PROPRIETARIO | Varchar(100) | Sim | Nome completo, que pode ser o nome social declarado ou o nome civil; identifica o proprietário nas negociações e nos contratos.|
| TL_PROPRIETARIO | Varchar(20) | Sim | Número de telefone ativo para contato. Permite um meio de comunicação direta entre o proprietário e a imobiliária.|
| EM_PROPRIETARIO | Varchar(100) | Sim | Endereço de e-mail ativo, possibilita outra forma de comunicação com o proprietário.|

**índices:** PK ID_PROPRIETARIO; índice secundário em NM_PROPRIETARIO (busca por nome nos registros do sistema)

**IMOVEL**
> **IMOVEL = @ID_IMOVEL + ID_PROPRIETARIO + TP_IMOVEL + TP_OFERTA + MQ_AREA + DS_STATUS + QT_VAGA_GARAGEM + QT_BANHEIROS + QT_QUARTOS + VL_IMOVEL + TP_FINALIDADE + NM_NUMERO + EN_LOGRADOURO + EN_BAIRRO + EN_COMPLEMENTO + EN_CIDADE + EN_CEP + VL_IPTU**

**Leitura:** @ID_IMOVEL é identificador único, seguido pelo ID_PROPRIETÁRIO obrigatório, que garante com que todo imóvel possua um proprietário prévio; os outros onze campos são obrigatórios e conectados por +, [TP_VENDA|TP_LOCAÇÃO] exige escolher um tipo de oferta para cadastro e posteriormente filtragem de pesquisa. <sup> *notação formal da escolha obrigatória modificada para compatibilidade com markdown de tabela do github.*</sup>

| Atributo | Tipo físico | Obrigatório | Significado e relevância |
| -------- | --------- |---------|---------|
| ID_IMOVEL | CHAR(11) | Sim (PK)| Identificador do imóvel. |
| ID_PROPRIETARIO | Integer | Sim (FK) | Referência ao titular do imóvel em contratos e negociações. |
| TP_IMOVEL | Varchar(30) | Sim | Classificação dos imóveis de acordo com seu tipo; Permite filtragem nas pesquisas no site. |
| TP_OFERTA_VENDA;TP_OFERTA_LOCAÇÃO | Varchar(10) | Sim (escolha) | Modelos de oferta para obtenção de um imóvel, seja de maneira temporária ou permanente; Direciona os clientes de acordo com suas necessidades. |
| MQ_AREA | Decimal(8,2) | Sim | Área de metros quadrados em cada imóvel; Contextualiza o tamanho dos imóveis. |
| TP_OFERTA| Varchar (30) | Sim | Modalidade de negociação. Domínio restrito por constraint. |
| QT_VAGA_GARAGEM | Integer | Sim | Quantidade de vagas de garagem disponíveis; Define um dos critérios para negociação, acerca da necessidade dos clientes. |
| QT_BANHEIROS | Integer | Sim | Quantidade de banheiros contidos no imóvel; Define um dos critérios para negociação, acerca da necessidade dos clientes. |
| QT_QUARTOS | Integer | Sim | Quantidade de quartos contidos no imóvel; Define um dos critérios para negociação, acerca da necessidade dos clientes. |
| VL_IMOVEL | DECIMAL(10,2) | Sim | Preço de negociação do imóvel; Um dos critérios basais para a decisão final dos clientes |
| TP_FINALIDADE | Varchar(30) | Sim | Uso especifico do imóvel; Determinada em contrato, passível de multa ou rescisão contratual em caso de mudança não autorizada |
| NM_NUMERO | Varchar(10) | Sim | Elemento principal da localização do imóvel|
| EN_LOGRADOURO |VARCHAR(150) | Sim | Elemento principal da localização do imóvel|
| EN_BAIRRO | Varchar(80) | Sim | Elemento principal da localização do imóvel|
| EN_COMPLEMENTO | Varchar(100) | Sim | Elemento principal da localização do imóvel|
| EN_CIDADE | Varchar(80) | Sim | Elemento principal da localização do imóvel|
| EN_CEP |CHAR(9) | Sim | Elemento principal da localização do imóvel|
| VL_IPTU | DECIMAL(12,2) | Sim | Preço do IPTU (Imposto Predial e Territorial Urbano); Um dos dados primordiais em negociações de compra e/ou venda de imóveis |

**índices:** PK ID_IMOVEL; índice secundário em ID_PROPRIETARIO (Chave estrangeira para acelerar a pesquisa do imóvel)


**CONTRATO**
> **CONTRATO = @ID_CONTRATO + ID_IMOVEL + ID_CLIENTE + ID_PROPRIETARIO + ID_CORRETOR + TP_CONTRATO + TP_FORMA_PAGAMENTO + VL_CONTRATO + DT_INICIO + (DT_FIM)**

Leitura:@ID_CONTRATO é o identificador único, seguido da chave estrangeira ID_IMOVEL. O atributo DT_FIM está entre parênteses por ser um dado opcional (aplicado prioritariamente a contratos de locação).

| Atributo | Tipo físico | Obrigatório | Significado e relevância |
| -------- | --------- |---------|---------|
| ID_CONTRATO | CHAR(10) | Sim (PK) | Código de localização do registro em sistema. |
| ID_IMOVEL | CHAR(11) | Sim (FK) | Referência ao imóvel; Opera como um dos pilares do contrato. |
| ID_CLIENTE | INT | Sim (FK) | Referência ao cliente; Opera como um dos pilares do contrato. |
| ID_PROPRIETARIO | INT | Sim (FK) | Referência ao proprietário; Diz respeito a uma das principais partes interessadas na negociação. |
| ID_CORRETOR | INT | Sim (FK) | Referência ao corretor; De suma importância em negociações com corretagem. |
| TP_CONTRATO | VARCHAR(30) | Sim | Característica diferencial entre locações e aquisições de imóveis |
| TP_FORMA_PAGAMENTO | VARCHAR(30) | Sim | Opção escolhida para subsídio do imóvel; Solicitada por lei em contratos imobiliários. |
| VL_CONTRATO | DECIMAL(12,2) | Sim | Preço de negociação do imóvel; dado basal para cálculo de comissão do corretor que mediou a negociação |
| DT_INICIO | DATE | Sim | Data em que o contrato entra em vigor; Solicitada por lei em contratos imobiliários. |
| DT_FIM | DATE | Não | Data de expiração do contrato; Exigida por lei em contratos de locação. |

**índices:** PK ID_CONTRATO; índice em ID_CLIENTE (localiza o contrato a partir do locador ou comprador); índice em ID_CORRETOR (relatórios de performance por período)

**CORRETOR**
> **CORRETOR = @ID_CORRETOR + ID_CRECI + NM_CORRETOR + TL_CORRETOR + EM_CORRETOR + LG_CORRETOR + TP_STATUS_CORRETOR**
Leitura: @ID_CORRETOR é o identificador único. ID_CRECI utiliza o prefixo de identificador por se tratar de um registro formal junto ao conselho regional. O campo TP_STATUS_CORRETOR marca a disponibilidade em sistema.

| Atributo | Tipo físico | Obrigatório | Significado e relevância |
| -------- | --------- |---------|---------|
| ID_CORRETOR | INT | Sim (PK) | Identificador do corretor |
| ID_CRECI | VARCHAR(15) | Sim (único) | Registro no Conselho Regional de Corretores de Imóveis; exigido por lei para validar atividades de corretagem. |
| NM_CORRETOR | VARCHAR(100) | Sim | Nome civil ou social completo como constante no Conselho Regional de Corretores de Imóveis; Aparece na assinatura do contrato. |
| TL_CORRETOR | VARCHAR(20) | Sim | Número de telefone ativo para contato. Permite um meio de comunicação direta com seus clientes. |
| EM_CORRETOR | VARCHAR(100) | Sim | Endereço de e-mail ativo, possibilita outra forma de comunicação com o corretor. |
| LG_CORRETOR | VARCHAR(30) | Sim | Línguas faladas pelo corretor; Orienta a escolha de clientes estrangeiros ou imigrantes recém migrados. |
| TP_STATUS_CORRETOR | VARCHAR(30) | Sim | Indicador de disponibilidade do corretor, domínio restrito por constraint; Corretores em período de férias ou afastados das funções não são exibidos como agentes disponíveis para contato. |

**índices:** PK ID_CORRETOR; índice único em ID_CRECI (evita duplicidade de registros profissionais e agiliza validações)

**CLIENTE**
> **CLIENTE = @ID_CLIENTE + NM_CLIENTE + TL_CLIENTE + EM_CLIENTE**
Leitura:@ID_CLIENTE é o identificador único; os demais campos são dados obrigatórios de identificação e contato.

| Atributo | Tipo físico | Obrigatório | Significado e relevância |
| -------- | --------- |---------|---------|
| ID_CLIENTE | INT | Sim (PK) | Identificador do cliente. |
| NM_CLIENTE | VARCHAR(100) | Sim | Nome completo, que pode ser o nome social declarado ou o nome civil; identifica o cliente nas negociações e nos contratos. |
| TL_CLIENTE | VARCHAR(20) | Sim | Número de telefone ativo para contato. Permite um meio de comunicação direta com a imobiliária e o corretor. |
| EM_CLIENTE | VARCHAR(100) | Sim | Endereço de e-mail ativo, possibilita outra forma de comunicação com a imobiliária e o corretor. |

**índices:** PK ID_CLIENTE; índice secundário em NM_CLIENTE (busca por nome na base de dados)

**VISITA**
> **VISITA = @ID_VISITA + ID_IMOVEL + ID_CLIENTE + ID_CORRETOR + DT_HR_VISITA + (DS_ANOTACAO_VISITA)**
Leitura: @ID_VISITA é o identificador único e ID_IMOVEL é a chave estrangeira do imóvel visitado. DT_HR_VISITA combina data e horário. DS_ANOTACAO_VISITA está entre parênteses por ser opcional.

| Atributo | Tipo físico | Obrigatório | Significado e relevância |
| -------- | --------- |---------|---------|
| ID_VISITA | VARCHAR(9) | Sim (PK) | Identificador da visita. |
| ID_IMOVEL | CHAR(11) | Sim (FK) | Referencial do imóvel visitado; impede que visitas sejam marcadas sem um imóvel informado |
| ID_CLIENTE | INT | Sim (FK) | Referencial do cliente; garante que toda visita possua um par de cliente e corretor |
| ID_CORRETOR | INT | Sim (FK) | Referencial do corretor; garante que toda visita seja acompanhada por um corretor autenticado na plataforma. |
| DT_HR_VISITA | DATETIME | Sim | Data e hora marcadas para visitação de cada imóvel. Necessária para organização da agenda de compromissos de cada corretor. |
| DS_ANOTACAO_VISITA | VARCHAR(500) | Não | Descrição livre das opiniões e impressões dos clientes. |

**índices:** PK ID_VISITA; índice em ID_IMOVEL (relatórios comerciais de análise de popularidade entre os clientes); índice em ID_CORRETOR (relatórios de performance por período).

**ENCOMENDA**
> **ENCOMENDA = @ID_ENCOMENDA + ID_CLIENTE + VL_MINIMO + EN_CIDADE_DESEJADA + EN_BAIRRO_DESEJADO + VL_MAXIMO + DT_ENCOMENDA + (DS_IMOVEL)**
Leitura: ID_ENCOMENDA é identificador único, a chave seguinte é estrangeira e referencia aos clientes. DS_Imovel é um campo descritivo e opcional.

| Atributo | Tipo físico | Obrigatório | Significado e relevância |
| -------- | --------- |---------|---------|
| ID_ENCOMENDA | INT | Sim (PK) | Identificador da encomenda. |
| ID_CLIENTE | INT | Sim (FK) | Referencial do cliente |
| VL_MINIMO | DECIMAL(12,2) | Sim | Valor mínimo do imóvel encomendado |
| EN_CIDADE_DESEJADA | VARCHAR(80) | Sim | Cidade desejada que o imóvel pertence |
| EN_BAIRRO_DESEJADO | VARCHAR(80) | Sim | Bairro desejado que o imóvel pertence |
| VL_MAXIMO | DECIMAL(12,2) | Sim | Valor máximo do imóvel encomendado |
| DT_ENCOMENDA | DATE | Sim | Data da encomenda feita pelo cliente |
| DS_IMOVEL | VARCHAR(500) | Não | Descrição do imóvel desejado |

**índices:** PK ID_ENCOMENDA; índice secundário em ID_CLIENTE (busca de encomendas por cliente).

**DOCUMENTO**
> **DOCUMENTO = @ID_DOC + NM_DOC + DT_DOC + TP_DOC + ID_CORRETOR**
Leitura:@ID_DOC é o identificador único; os outros três campos seguintes são obrigatórios e conectados por +, para rastreabilidade de atividades, os documentos são ligados aos corretores que os inseriram na plataforma

| Atributo | Tipo físico | Obrigatório | Significado e relevância |
| -------- | --------- |---------|---------|
| ID_DOC | INT | Sim (PK) | Identificador do documento.|
| NM_DOC | Varchar(120) | Sim | Nome declarado no documento.|
| DT_DOC | Date | Sim | Data do registro do documento.|
| TP_DOC | Varchar(100) | Sim | Tipo de documento para melhor localização.|
| ID_CORRETOR | INT | Sim (FK) | Corretor responsável por inserir o documento.

**índices:** PK ID_DOC; índice secundário em NM_DOC (busca por nome do documento).


### 5.3 Log de acesso (metadado operacional) 
As quatro tabelas ficam sob o mesmo mecanismo de auditoria do SGBD: o plugin audit_log do MySQL, configurado para gravar em formato JSON no caminho definido por audit_log_file (variável de sistema, sob $HOME neste ambiente — nunca sob /tmp, pelas mesmas razões que valem para LibreOffice/ffmpeg). Na ausência do plugin, a alternativa é o log geral (general_log=ON, log_output=TABLE), consultável em mysql.general_log. Retenção e rotação do log seguem política própria, independente da retenção dos dados de negócio. 

### 5.4 Acesso por operação e conformidade com a LGPD

A matriz abaixo estabelece os níveis de acesso propostos para as entidades do sistema, considerando usuários padrão (clientes e proprietários) e usuários privilegiados da imobiliária (corretores e administradores). As permissões deverão respeitar as responsabilidades de cada perfil e o princípio do menor privilégio.

| Tabela | Leitura | Inserção | Atualização | Exclusão |
|---|---|---|---|---|
| PROPRIETARIO | Usuário padrão relacionado ao cadastro; corretores responsáveis; administradores | Administradores | Usuário padrão, somente nos próprios dados pessoais; administradores | Sem exclusão direta; anonimização quando cabível, respeitadas as hipóteses legais de conservação |
| CLIENTE | Usuário padrão relacionado ao cadastro; corretores responsáveis; administradores | Usuários padrão, por meio do próprio cadastro; administradores | Usuário padrão, somente nos próprios dados pessoais; administradores | Sem exclusão direta; anonimização quando cabível, respeitadas as hipóteses legais de conservação |
| IMOVEL | Usuários padrão; corretores responsáveis; administradores | Administradores e corretores autorizados | Administradores e corretores autorizados | Sem exclusão direta de registros vinculados a negociações; avaliar inativação ou remoção quando aplicável |
| CONTRATO | Usuários padrão participantes da negociação; corretores responsáveis; administradores | Administradores e corretores autorizados | Administradores e corretores autorizados | Sem exclusão direta; preservação conforme obrigações legais e exercício regular de direitos |
| CORRETOR | Próprio corretor, quanto aos seus dados; administradores | Administradores | Administradores; corretor, somente nos próprios dados pessoais quando autorizado | Sem exclusão direta; inativação do cadastro em caso de desligamento |
| VISITA | Usuários padrão envolvidos na visita; corretor responsável; administradores | Corretores responsáveis | Corretores responsáveis; administradores | Sem exclusão direta; priorizar cancelamento ou inativação do registro |
| ENCOMENDA | Usuários padrão envolvidos na visita; corretor responsável; administradores | Usuários padrão, por meio do próprio cadastro; administradores | Usuários padrão, por meio do próprio cadastro; administradores | Sem exclusão direta; priorizar cancelamento ou inativação do registro |
| DOCUMENTO | Usuários padrão envolvidos na visita; corretor responsável; administradores | Administradores e corretores autorizados | Administradores e corretores autorizados | Sem exclusão direta; priorizar cancelamento ou inativação do registro |


**Observações sobre as permissões:**

- Usuários padrão abrangem clientes e proprietários, utilizando o mesmo nível de acesso. Cada usuário poderá consultar e atualizar somente seus próprios dados pessoais e acessar informações relacionadas à sua participação nas negociações.
- Corretores possuem acesso privilegiado às informações necessárias para suas atividades, limitado aos clientes, imóveis, contratos e visitas sob sua responsabilidade.
- Administradores possuem permissões de gerenciamento dos cadastros e registros da plataforma, conforme suas atribuições.
- A exclusão direta de registros deverá ser evitada quando puder comprometer o histórico de negociações, contratos ou obrigações legais. Quando aplicável, deverão ser avaliadas a inativação ou a anonimização dos dados.
- O acesso aos registros de auditoria deverá ser restrito a pessoas autorizadas, conforme a necessidade de acompanhamento e fiscalização das operações.

Os níveis de acesso deverão respeitar o princípio do menor privilégio, permitindo que cada usuário consulte ou altere somente as informações necessárias ao desempenho de suas atividades ou relacionadas à sua participação nas negociações. O tratamento de dados pessoais deverá observar as finalidades estabelecidas e as bases legais aplicáveis, conforme a Lei Geral de Proteção de Dados Pessoais (Lei nº 13.709/2018).
