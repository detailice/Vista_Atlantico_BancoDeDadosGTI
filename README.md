# Vista Atlântico — Banco de Dados
Repositório criado para o Projeto Semestral de Modelagem de Banco de Dados.

## 1. Caracterização da Organização

- **Nome e natureza da organização:** VISTA ATLANTICO NEGOCIOS IMOBILIARIOS LTDA

**Contexto e porte:**
- **Fins lucrativos:** Com fins lucrativos. A empresa é registrada como uma Sociedade Empresária Limitada (Ltda.) voltada ao setor privado.
- **Tamanho da operação:** Classificada no regime de EPP (Empresa de Pequeno Porte). Tem sede localizada em Praia Grande / SP.
- **Número de pessoas envolvidas:**
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

| Atributo | Descrição | Regra de negócio associada |
|----------|-----------|------------------------------|
| - | - | - |



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
**Atributo Simples:** nome, telefone, e-mail.  

<ins>**IMOVEL**</ins>

ID_IMOVEL: Atributo Identificador (Chave Primária).  
**Atributo Composto:** endereço (desmembrado em longradouro, número e bairro).  
**Atributos Simples:** area_m2, valor, finalidade, oferta, IPTU, QTDE_quartos, QTDE_banheiros, vaga_garagem, status, tipo_imovel.  

<ins>**CLIENTE**</ins>

**Chave Primária:** CPF (Atributo Identificador).  
**Atributo Simples:** nome, e-mail, telefone.  

<ins>**CORRETOR**</ins>

**Chave Primária:** CRECI (Atributo Identificador).  
**Atributos Simples:** nome, comissão, telefone, e-mail  
**Atributo Multivalorado/Composto:** idiomas (opções: Português, Inglês, Espanhol).  
**Atributo Multivalorado/Composto:** Status (opções: ativo, férias, afastado).

<ins>**CONTRATO**</ins>

**ID_CONTRATO:** Atributo Identificador (Chave Primária).  
**Atributos Simples:** forma_pagamento, valor, data_inicio, data_fim

<ins>**VISITA**</ins>

**Chave Primária:** ID_VISITA (Atributo Identificador).  
**Atributos Simples:** data_visita, horário, anotacoes_visita 

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

- Anexe o DER (em imagem).
- O diagrama deve representar corretamente:
  - Entidades
  - Atributos
  - Relacionamentos
  - **Cardinalidades**
- O modelo deve ser **consistente** e já demonstrar potencial de **escalabilidade e integração** (pensando nas próximas etapas do projeto).


## 8. Justificativa Técnica:
A modelagem foi desenvolvida com base na perspectiva de uso externo do sistema, mapeando os requisitos essenciais da rotina da imobiliária a partir da visão do cliente.
A separação das entidades foi adotada para deixar clara a função de cada participante e permitir o registro individual de eventos, como as informações de cada visita.
Os atributos atendem às necessidades práticas identificadas; e a opção pelas cardinalidades garante a flexibilidade do sistema.

## 9. Uso de Inteligência Artificial

| Item | O que registrar |
|------|------------------|
| **Ferramenta e etapa** | Utilizamos o GEMINI 3.6 Flash na formatação do tópico de Relacionamentos Pertinentes |
| **Motivação** | Não sabíamos a melhor maneira de registrar do READ.ME, então preferimos pedir ajuda para organizar o que escrevemos |
| **Prompt(s) utilizados** | "Vou te dar algumas orientações e preciso que você se baseie no diagrama que vou mandar aqui para responder, segue:
Relacionamentos pertinentes: como as entidades se conectam.
Restrições e políticas organizacionais aplicadas ao modelo." |
| **Resposta recebida** | Relacionamentos pertinentes POSSUI (PROPRIETARIO $\leftrightarrow$ IMOVEL) Cardinalidade: (0, n) para (0, n) — Um proprietário pode possuir de zero a vários imóveis, e um imóvel pode pertencer a zero ou a múltiplos proprietários. |
| **Fontes consultadas e verificadas** | Se a IA citou fontes/dados, quais foram checadas pelo grupo e como (ex.: comparação com o que foi observado na visita de campo). |
| **Trechos rejeitados ou corrigidos** | Corrigimos o espaçamento entre as frases e ajustamos algumas palavras para melhor compreensão da equipe |
| **Justificativa da escolha final** | A resposta do Gemini se baseou no diagrama que fizemos, mas certas partes continham palavras que não utilizamos e trechos que fugiam do que mostramos, em resumo, ela alucinou. |
| **Reflexão crítica** | A IA alucinou em algumas partes, inseriu informações além do necessário e além da compreensão técnica do time acerca do trabalho. |

---
