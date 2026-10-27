## Caso: Dicionário de dados de uma Imobiliária

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
| ( ) | Dados opcionais |

> A notação formal possuí outros símbolos, que não foram utilizados por não serem pertinentes aos tipos de dados e suas formatações referentes ao presente contexto.

**Prefixos:** NM_nome, ID_identificador, QT_quantidade, TP_tipo (categorização), IN_ indicador booleano, DT_data. O caso também utiliza TL_(telefone), EN_(endereço), EM_(endereço de e-mail), HR_(horário), MQ_(metros quadrados), PR_(preço), LG_(linguas) e DS_(descrição/texto livre), que não estão entre os prefixos padrões, porém seguem os princípios básicos.  

**Versão deste dicionário:** v1.0, 6/setembro/2026. Qualquer alteração de estrutura deve gerar nova revisão registrada nesta seção; a prática atende, ela própria, ao princípio de rastreabilidade exigido pela LGPD (art. 6º, X). 

### 5.3 Dicionário de dados por entidade

**PROPRIETARIO**
> **PROPRIETARIO = @ID_PROPRIETARIO + NM_PROPRIETARIO + TL_PROPRIETARIO + EM_PROPRIETARIO**  

**Leitura:** @ID_Proprietário é o identificador único; os outros três campos seguintes são obrigatórios e conectados por +.

| Atributo | Tipo físico | Obrigatório | Significado e relevância |
| -------- | --------- |---------|---------|
| ID_PROPRIETARIO | Integer | Sim (PK) | Identificador do proprietário |
| NM_PROPRIETARIO | Varchar(120) | Sim | Nome completo, que pode ser o nome social declarado ou o nome civil; identifica o proprietário nas negociações e nos contratos.|
| TL_PROPRIETARIO | Varchar(11) | Sim | Número de telefone ativo para contato. Permite um meio de comunicação direta entre o proprietário e a imobiliária.|
| EM_PROPRIETARIO | Varchar(100) | Sim | Endereço de e-mail ativo, possibilita outra forma de comunicação com o proprietário.|

**índices:** PK ID_PROPRIETARIO; índice secundário em NM_PROPRIETARIO (busca por nome nos registros do sistema)

**IMOVEL**
> **IMOVEL = @ID_IMOVEL + ID_PROPRIETARIO + TP_IMOVEL + [TP_VENDA| TP_LOCAÇÃO] + MQ_ÁREA + IN_STATUS + QT_VAGA_GARAGEM + QT_BANHEIROS + QT_QUARTOS + PR_IMOVEL + TP_FINALIDADE + EN_IMOVEL + PR_IPTU** 

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

**índices:** PK ID_IMOVEL; índice secundário em ID_PROPRIETARIO (Chave estrangeira para acelerar a pesquisa do imóvel)


**CONTRATO**
> **CONTRATO = @ID_CONTRATO + ID_CLIENTE + ID_PROPRIETARIO + ID_CORRETOR + TP_CONTRATO + TP_PAGAMENTO + PR_IMÓVEL + DT_INICIO + (DT_FIM)**

Leitura: ID_CONTRATO é o identificador único, seguido por outros três identificadores estrangeiros, que garantem que nenhum contrato seja registrado sem as devidas partes; TP_contrato diferencia contratos entre venda e locação, o campo DT_FIM vêm entre parênteses pois é utilizado somente em contratos de locação.

| Atributo | Tipo físico | Obrigatório | Significado e relevância |
| -------- | --------- |---------|---------|
| ID_CONTRATO | Integer | Sim  (PK)| Código de localização do registro em sistema. |
| ID_CLIENTE | Integer | Sim (FK) | Referência ao cliente; Opera como um dos pilares do contrato. |
| ID_PROPRIETARIO | Integer | Sim (FK) | Referência ao proprietário; Diz respeito a uma das principais partes interessadas na negociação. |
| ID_CORRETOR | Integer | Sim (FK) | Referência ao corretor; De suma importância em negociações com corretagem. |
| TP_CONTRATO | Text | Sim | Característica diferencial entre locações e aquisições de imóveis
| TP_PAGAMENTO | Text | Sim | Opção escolhida para subsídio do imóvel; Solicitada por lei em contratos imobiliários. |
| PR_IMOVEL | Real | Sim | Preço de negociação do imóvel; dado basal para cálculo de comissão do corretor que mediou a negociação |
| DT_INICIO | date | Sim | Data em que o contrato entra em vigor; Solicitada por lei em contratos imobiliários. |
| DT_FIM | date | Não | Data de expiração do contrato; Exigida por lei em contratos de locação. |

**índices:** PK ID_CONTRATO; índice em ID_CLIENTE (localiza o contrato a partir do locador ou comprador); índice em ID_CORRETOR (relatórios de performance por período)

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

**índices:** PK ID_CORRETOR; índice único em ID_CRECI (evita duplicidade de registros profissionais e agiliza validações)

**CLIENTE**
> **CLIENTE = @ID_CLIENTE + NM_CLIENTE + TL_CLIENTE + EM_CLIENTE**
Leitura:@ID_CLIENTE é o identificador único; os outros três campos seguintes são obrigatórios e conectados por +.

| Atributo | Tipo físico | Obrigatório | Significado e relevância |
| -------- | --------- |---------|---------|
| ID_CLIENTE | Interger | Sim (PK) | Identificador do cliente.|
| NM_CLIENTE | Varchar(120) | Sim | Nome completo, que pode ser o nome social declarado ou o nome civil; identifica o cliente nas negociações e nos contratos.|
| TL_CLIENTE | Varchar(11) | Sim | Número de telefone ativo para contato. Permite um meio de comunicação direta com a imobiliária e o corretor.|
| EM_CLIENTE | Varchar(100) | Sim | Endereço de e-mail ativo, possibilita outra forma de comunicação com a imobiliária e o corretor.|

**índices:** PK ID_CLIENTE; índice secundário em NM_CLIENTE (busca por nome na base de dados)

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

**índices:** PK ID_VISITA; índice em ID_IMOVEL (relatórios comerciais de análise de popularidade entre os clientes); índice em ID_CORRETOR (relatórios de performance por período).

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

Os atributos estruturados previstos nas entidades PROPRIETARIO, CLIENTE, CORRETOR, IMOVEL, CONTRATO e VISITA não contemplam, em princípio, dados pessoais sensíveis nos termos do art. 5º, II, da Lei nº 13.709/2018, abrangendo principalmente dados pessoais comuns, como identificação, contato, registro CRECI e informações financeiras e patrimoniais. O tratamento desses dados deverá observar as bases legais aplicáveis, especialmente a execução de contrato ou de procedimentos preliminares relacionados (art. 7º, V) e o cumprimento de obrigações legais ou regulatórias (art. 7º, II). O campo livre DS_ANOTACOES, da entidade VISITA, representa um risco de armazenamento de informações excessivas ou sensíveis, devendo seu preenchimento observar os princípios da finalidade e da necessidade (art. 6º, I e III), com acesso restrito conforme as permissões definidas na matriz da seção 5.4. Os mecanismos de controle de acesso e auditoria deverão permitir a rastreabilidade das operações, contribuindo para a responsabilização e prestação de contas (art. 6º, X). Quanto à retenção, os dados pessoais das entidades PROPRIETARIO e CLIENTE deverão ser eliminados ou anonimizados quando não forem mais necessários, respeitadas as hipóteses legais de conservação e a integridade referencial do banco de dados. Os registros de CONTRATO poderão ser preservados enquanto necessários ao cumprimento de obrigações legais, fiscais ou ao exercício regular de direitos, observados os critérios de retenção previstos na legislação aplicável.
