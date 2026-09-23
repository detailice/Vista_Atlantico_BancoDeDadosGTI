# Vista Atlântico — Banco de Dados
Repositório criado para o Projeto Semestral de Modelagem de Banco de Dados.

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

**VISITA** constrói um relacionamento ternário entre CLIENTE e CORRETOR (um cliente se interessa por um imóvel e aciona o corretor, a negociação pode exigir uma visita) 

**PROPRIETARIO** é a pessoa física que possui um imóvel e procura o serviço corretagem da imobiliária 

IMOVEL é o bem físico fixo que é anunciado para venda ou locação 

CONTRATO é o registro autenticado em cartório acerca da venda, locação ou corretagem de um imóvel 

CLIENTE é a pessoa física que procura a plataforma para comprar ou alugar um imóvel. 

VISITA é o evento no qual um ou mais clientes acompanham um corretor a um imóvel 

### 5.1 **Fluxo de dados**
Cliente se cadastra/loga no sistema → cliente seleciona o tipo de imóvel que deseja visualizar → cliente seleciona o imóvel de interesse, marcando uma visita → o agendamento gera um registro em VISITA, ligando esse CLIENTE a um CORRETOR → a critério do cliente, a negociação pode avançar e gerar um CONTRATO, que é referenciado nos registros do CLIENTE e do CORRETOR → toda leitura ou escrita nessas quatro tabelas é registrada pelo log de acesso do SGBD (§5), o que sustenta auditoria e conformidade com a LGPD (§6). 

### 5.2 Convenções do dicionário
SGBD: MySQL 8, mecanismo de armazenamento InnoDB — cuida da persistência dos arquivos de dados, do log de transações (redo/undo) e mantém o índice primário clusterizado por chave. 
Codificação de caracteres: utf8mb4 com collation utf8mb4_0900_ai_ci. Escolhida em vez de latin1 por cobrir acentuação do português sem perda em campos de nome e texto livre.

Notação Formal utilizada:

| Símbolo | Significado |
|----------|-----------|
| = | é composto de |
| + | e (conecta elementos obrigatórios) |
|  | ---|
|  |--- |

Prefixos: NM_nome, ID_identificador, QT_quantidade, TP_tipo (categorização), IN_ indicador booleano. O caso também utiliza TL_(telefone), EM_(endereço de e-mail) não está entre os prefixos padrões, porém segue os princípios básicos  
Versão deste dicionário: v1.0, 6/setembro/2026. Qualquer alteração de estrutura deve gerar nova revisão registrada nesta seção; a prática atende, ela própria, ao princípio de rastreabilidade exigido pela LGPD (art. 6º, X). 

### 5.3 Dicionário de dados por entidade

**PROPRIETARIO**
> **PROPRIETARIO = @ID_PROPRIETÁRIO + NM_PROPRIETARIO + TL_PROPRIETARIO + EM_PROPRIETARIO**  

**Leitura:** @ID_Proprietário é o identificador único; os outros três campos seguintes são obrigatórios e conectados por +.

| Atributo | Tipo físico | Obrigatório | Significado e relevância |
| -------- | --------- |---------|---------|
| ID_PROPRIETARIO | Integer | Sim (PK) | Identificador do proprietário |
| NM_PROPRIETARIO | Varchar(120) | Sim | Nome completo, que pode ser o nome social declarado ou o nome civil; identifica o proprietário nas negociações e nos contratos.|
| TL_PROPRIETARIO | Varchar(11) | Sim | Número de telefone ativo para contato. Permite um meio de comunicação direta entre o proprietário e a imobiliária.|
| EM_PROPRIETARIO | Varchar(100) | Sim | Endereço de e-mail ativo, possibilita outra forma de comunicação com o proprietário.|

**IMOVEL**
> **IMOVEL = @ID_IMOVEL + ID_PROPRIETARIO (?) + TP_IMOVEL + [TP_VENDA| TP_LOCAÇÃO] + MQ_ÁREA + IN_STATUS + QT_VAGA_GARAGEM + QT_BANHEIROS + QT_QUARTOS + PR_IMOVEL + TP_FINALIDADE + EN_endereço + PR_IPTU**  

**Leitura:** @ID_IMOVEL é identificador único, 

| Atributo | Tipo físico | Obrigatório | Significado e relevância |
| -------- | --------- |---------|---------|
| ID_IMOVEL | Integer | Sim | Identificador do imóvel. |
| ID_PROPRIETARIO | Integer | Sim (FK) | Referência ao titular do imóvel em contratos e negociações. |
| TP_IMOVEL | Varchar(50) | Sim | Classificação dos imóveis de acordo com seu tipo; Permite filtragem nas pesquisas no site. |
| TP_VENDA;TP_LOCAÇÃO | Varchar(10) | Sim | Modelos de oferta para obtenção de um imóvel, seja de maneira temporária ou permanente; Direciona os clientes de acordo com suas necessidades. |
| MQ_ÁREA | Real | Sim | Área de metros quadrados em cada imóvel; Contextualiza o tamanho dos imóveis. |
| IN_STATUS | Boolean | Sim | Indicador da condição do imóvel; Imóveis já vendidos ou alugados não aparecem nas telas de anuncio e busca, com registros salvos por questões de auditória interna ou juridica. |
| QT_VAGA_GARAGEM | Integer | Sim | Quantidade de vagas de garagem disponíveis; Define um dos critérios para negociação, acerca da necessidade dos clientes. |
| QT_BANHEIROS | Integer | Sim | Quantidade de banheiros contidos no imóvel; Define um dos critérios para negociação, acerca da necessidade dos clientes. |
| QT_QUARTOS | Integer | Sim | Quantidade de quartos contidos no imóvel; Define um dos critérios para negociação, acerca da necessidade dos clientes. |
| PR_IMOVEL | Real | Sim | Preço de negociação do imóvel; Um dos critérios basais para a decisão final dos clientes |
| TP_FINALIDADE | Varchar(50) | Sim | Uso especifico do imóvel; Determinada em contrato, passível de multa ou rescisão contratual em caso de mudança não autorizada |
| EN_endereço | Varchar(120) | Sim | -|
| PR_IPTU | Real | Sim | -|



**PROPRIETARIO**
> **PROPRIETARIO = @ID_PROPRIETÁRIO + NM_PROPRIETARIO + TL_PROPRIETARIO + EM_PROPRIETARIO**
Leitura:

| Atributo | Tipo físico | Obrigatório | Significado e relevância |
| -------- | --------- |---------|---------|
| - | - | - | -|
| - | - | - | -|
| - | - | - | -|
| - | - | - | -|

**PROPRIETARIO**
> **PROPRIETARIO = @ID_PROPRIETÁRIO + NM_PROPRIETARIO + TL_PROPRIETARIO + EM_PROPRIETARIO**
Leitura:

| Atributo | Tipo físico | Obrigatório | Significado e relevância |
| -------- | --------- |---------|---------|
| - | - | - | -|
| - | - | - | -|
| - | - | - | -|
| - | - | - | -|

**PROPRIETARIO**
> **PROPRIETARIO = @ID_PROPRIETÁRIO + NM_PROPRIETARIO + TL_PROPRIETARIO + EM_PROPRIETARIO**
Leitura:

| Atributo | Tipo físico | Obrigatório | Significado e relevância |
| -------- | --------- |---------|---------|
| - | - | - | -|
| - | - | - | -|
| - | - | - | -|
| - | - | - | -|

**PROPRIETARIO**
> **PROPRIETARIO = @ID_PROPRIETÁRIO + NM_PROPRIETARIO + TL_PROPRIETARIO + EM_PROPRIETARIO**
Leitura:

| Atributo | Tipo físico | Obrigatório | Significado e relevância |
| -------- | --------- |---------|---------|
| - | - | - | -|
| - | - | - | -|
| - | - | - | -|
| - | - | - | -|

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

**Chave Primária:** CPF (Atributo Identificador).  
**Atributo Simples:** NOME, TELEFONE, E-MAIL.  

<ins>**IMOVEL**</ins>

ID_IMOVEL: Atributo Identificador (Chave Primária).  
**Atributo Composto:** ENDEREÇO (desmembrado em logradouro, número e bairro).  
**Atributos Simples:** AREA_M2, VALOR, FINALIDADE, OFERTA, IPTU, QTDE_QUARTOS, QTDE_BANHEIROS, VAGA_GARAGEM, STATUS, TIPO_IMOVEL.  

<ins>**CLIENTE**</ins>

**Chave Primária:** CPF (Atributo Identificador).  
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
**POSSUI (PROPRIETARIO $\leftrightarrow$ IMOVEL)** Cardinalidade: (1, n) para (1, n) — Um proprietário pode possuir de zero a vários imóveis, e um imóvel pode pertencer a zero ou a múltiplos proprietários.  
**REFERENTE_A (IMOVEL $\leftrightarrow$ CONTRATO)** Cardinalidade: (1, n) para (1, n) — Um imóvel pode ser objeto de zero a vários contratos ao longo do tempo, assim como um contrato pode associar-se a imóveis.  
**ASSINA (CLIENTE $\leftrightarrow$ CONTRATO)** Cardinalidade: (0, n) para (1, n) — Um cliente pode assinar zero ou mais contratos. Esse relacionamento contém o atributo tipo.  
**INTERMEDIA (CORRETOR $\leftrightarrow$ CONTRATO)** Cardinalidade: (0, n) para (1, n) — Um corretor pode intermediar zero ou vários contratos, e um contrato pode ser intermediado por corretores.  
**AGENDA (CLIENTE $\leftrightarrow$ VISITA)** Cardinalidade: (0, n) para (1, n) - Um cliente pode agendar várias visitas, e uma visita pode ser agendada por um ou mais clientes.  
**ACOMPANHA (CORRETOR $\leftrightarrow$ VISITA)** Cardinalidade: (1, n) para (1, n) — Uma visita pode ser acompanhada por um ou mais corretores, já que um imóvel pode ser vendido por um ou dois corretores, no mesmo contrato; e uma visita pode ser acompanhada por um ou mais corretores.  
 
- **Restrições e políticas organizacionais aplicadas ao modelo:**  
**Unicidade de Identificação:** Cada entidade principal possui um atributo identificador único obrigatório (CPF para Cliente/Proprietário, CRECI para Corretor, ID_IMOVEL, ID_CONTRATO e ID_VISITA).  
**Controle Operacional do Corretor:** O modelo restringe a gestão de corretores através do rastreamento de disponibilidade operacional (Status: ativo, férias ou afastado) e competência de atendimento por idioma.

## 7. Diagrama Entidade-Relacionamento (DER)

<img width="1124" height="713" alt="image" src="https://github.com/user-attachments/assets/12557d48-55b2-4ea4-9ccd-966904075290" />

## 8. Diagrama de classes

<img width="1227" height="814" alt="VistaAtlantico — Classes - Diagrama de Classes (1)" src="https://github.com/user-attachments/assets/e3b1bb34-655d-4993-8f4c-0365a638f4e9" />

## 9. Justificativa Técnica:
A modelagem foi desenvolvida com base na perspectiva de uso externo do sistema, mapeando os requisitos essenciais da rotina da imobiliária a partir da visão do cliente. A separação das entidades foi adotada para deixar clara a função de cada participante e permitir o registro individual de eventos, como as informações de cada visita. Os atributos atendem às necessidades práticas identificadas; e a opção pelas cardinalidades garante a flexibilidade do sistema.

## 10. Uso de Inteligência Artificial

| Item | registros do 1º uso | registros do 2º uso |
|--------|----------|----------|
| **Ferramenta e etapa** | Utilizamos o GEMINI 3.6 Flash na formatação do tópico de Relacionamentos Pertinentes | Utilizamos o Claude Sonnet 5 (médio, pensamento ativo) na correção do Diagrama de Classes 
| **Motivação** | Não sabíamos a melhor maneira de registrar do READ.ME, então preferimos pedir ajuda para organizar o que escrevemos | Tivemos o conteúdo somente por uma aula, com uma atividade não corrigida, temos somente o conhecimento básico |
| **Prompt(s) utilizados** | "Vou te dar algumas orientações e preciso que você se baseie no diagrama que vou mandar aqui para responder, segue: Relacionamentos pertinentes: como as entidades se conectam. Restrições e políticas organizacionais aplicadas ao modelo." | "Esse diagrama de classes é sobre o sistema de uma imobiliaria que aluga e vende imóveis, verifique se as associações e a multiplicidade estão corretas. O formato de saída deve ser um texto explicativo breve acerca das correções." e "Ok, poderia revisar se os métodos de cada classe e as visibilidades estão corretas? mantenha o mesmo formato, texto explicativo breve sobre as correções"
| **Resposta recebida** | Relacionamentos pertinentes POSSUI (PROPRIETARIO $\leftrightarrow$ IMOVEL) Cardinalidade: (0, n) para (0, n) — Um proprietário pode possuir de zero a vários imóveis, e um imóvel pode pertencer a zero ou a múltiplos proprietários. (...) | "Analisando o diagrama, encontrei algumas inconsistências nas multiplicidades e no tipo de relacionamento (composição x associação/agregação). Segue um resumo das correções sugeridas: 1. PROPRIETÁRIO "POSSUI" IMÓVEL (...) |
| **Fontes consultadas e verificadas** | Se a IA citou fontes/dados, quais foram checadas pelo grupo e como (ex.: comparação com o que foi observado na visita de campo). | A fonte usada como base foi o DER que anexamos, comparamos as resposta com ele e com os materiais de aula fornecidos | O conteúdo utilizado para as respostas vieram do treinamento do modelo Sonnet 5 com "documentação padronizada e aberta", analisamos as correções junto com o material dado em sala no semestre passado por outro docente.
| **Trechos rejeitados ou corrigidos** | Corrigimos o espaçamento entre as frases e ajustamos algumas palavras para melhor compreensão da equipe | Não corrigimos ou rejeitamos.
| **Justificativa da escolha final** | A resposta do Gemini se baseou no diagrama que fizemos, mas certas partes continham palavras que não utilizamos e trechos que fugiam do que mostramos, em resumo, ela alucinou. | As correções apresentaram informações relevantes e validadas posteriormente com os materiais da docente que nos deu a disciplina.
| **Reflexão crítica** | A IA alucinou em algumas partes, inseriu informações além do necessário e além da compreensão técnica do time acerca do trabalho. | 


---
