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

- **Responsável pela organização: Valéria Nogueira**

**Relato da entrevista**
- **Quem: Claudia Regina da Silva Santos.** 
- **Quando e onde: A entrevista foi realizada no dia 02/09/2026, em Rua Tupi- Praia Grande.** 
- **Comprovação:(Arquivos anexados na pasta :"LEVANTAMENTO")**
- **O que foi levantado:** 
## Levantamento de Requisitos

O levantamento de requisitos foi realizado junto à gestão da **Vista Atlântico Negócios Imobiliários LTDA**, uma imobiliária de pequeno porte localizada na Baixada Santista, composta por uma diretora/gerente e sete corretores, com aproximadamente 900 a 1.000 anúncios ativos.

Foi identificada como principal dificuldade a **descentralização das informações**, devido ao uso de planilhas e registros em papel, dificultando o acesso ao histórico de clientes, imóveis, visitas e contratos.

### Funcionalidades do Sistema

A plataforma deverá permitir o cadastro de usuários, proprietários, clientes e corretores. Os proprietários poderão cadastrar imóveis com fotos e informações detalhadas, sujeitos à aprovação de um corretor. Os clientes poderão pesquisar imóveis, entrar em contato, agendar visitas e registrar encomendas com suas preferências, recebendo alertas sobre oportunidades compatíveis.

Os corretores também poderão cadastrar imóveis captados diretamente, mediante autorização do proprietário. Todos os anúncios e transações deverão identificar o responsável por meio do número do CRECI.

### Negociações e Contratos

O sistema deverá registrar agendamentos de visitas, acompanhamentos e observações dos corretores. Após o interesse do cliente, serão realizadas propostas e análises documentais.

Os contratos serão elaborados pelo setor jurídico terceirizado. Nas locações, deverão ser registrados a garantia locatícia e os laudos de vistoria de entrada e saída. Nas vendas, a conclusão ocorrerá em cartório ou por meio de financiamento bancário.

### Gestão Financeira e Comissões

O sistema deverá contemplar as seguintes regras financeiras:

- **Vendas:** comissão de 6% sobre o valor da transação, dividida igualmente entre imobiliária e corretor.
- **Locações:** comissão equivalente ao primeiro mês de aluguel.
- **Temporada:** comissão de 30% para locações de até 90 dias.
- **Administração de imóveis:** cobrança de aluguel, IPTU e condomínio, retenção da taxa administrativa e repasse do valor líquido ao proprietário em até cinco dias úteis.
- **Inadimplência:** controle de cobranças e acompanhamento dos pagamentos pendentes.

### Objetivo do Sistema

Centralizar as informações e automatizar os principais processos da imobiliária, proporcionando maior organização, agilidade no atendimento, controle das negociações e eficiência na gestão de imóveis, clientes e operações financeiras.

---

### **Processos de negócio:**

**Principais processos mapeados:** 

- **Cadastro de clientes e proprietários:** Clientes preenchem suas informações (nome completo, telefone e e-mail) para ter acesso aos imóveis por meio de contato com os corretores, seja pelo envio de mensagens direto pelo site ou via WhatsApp da imobiliária, sendo registrados automaticamente no banco pelo site ou manualmente pelo corretor que recebeu a mensagem. Proprietários se registram na plataforma (nome completo, telefone e e-mail) ao registrarem seus imóveis, o registro passa pela avaliação de um corretor, que filtra e aprova os cadastros de acordo com os requisitos (fotos em boa qualidade de todos os cômodos e todos os campos preenchidos).

- **Cadastro de imóveis:** Um proprietário pode cadastrar seu próprio imóvel, preenchendo suas informações pessoais (nome completo, telefone e e-mail) e as características do imóvel (endereço completo, tipo de oferta, preço, quantidade de vagas, quartos e banheiros, etc), que serão enviadas e sujeitadas a aprovação por um dos corretores. Os corretores também podem cadastrar imóveis, mediante contrato de autorização de corretagem assinado por ambas as partes (corretor e proprietário), declarando todas as características do imóvel, bem como outras clausulas pertinentes.

- **Cadastro de corretores:** Corretores que queiram integram o time podem enviar suas informações (nome completo, telefone e e-mail) com link URL do perfil no LinkedIn ou anexar seu currículo, sendo sujeitados a avaliação da diretora da imobiliária. Caso se tornem parte da equipe, a diretora quem realiza o cadastro, inserindo nome completo, telefone, e-mail e quais idiomas fala, bem como os imóveis pelos quais está responsável pela corretagem, separados por venda ou locação.

- **Assinatura de contrato:** Após enviarem todas as informações pertinentes a elaboração do contrato para o time jurídico externo, a imobiliária recebe o contrato e o submete às demais partes interessadas (proprietário e comprador/locador), que podem assinar de maneira virtual ou presencial.

-  **Agendamento e realização de visitas:** Após o cliente manifestar interesse por um imóvel, ele acessa a página deste imóvel na plataforma e clica no botão "Agendar visita", que exibe os campos de decisão do dia e horário desejados, bem como o espaço para deixar uma mensagem. O sistema envia essas informações diretamente para a caixa de mensagens do corretor responsável por aquele imóvel, notificando-o de que há uma nova agenda pendente. Em seguida, o corretor entra em contato com o cliente para confirmar os detalhes, alinhar as expectativas e prosseguir com o acompanhamento presencial, registrando posteriormente todas as observações pertinentes no sistema.
    
- **Encomenda de imóveis (preenchimento de informações do imóvel desejado que gera um alerta em e-mail ou telefone se encontrado);** Caso o usuário navegue por toda a plataforma e não encontre um imóvel ao seu gosto, ele realiza a encomenda de um imóvel, preenchendo nome completo, telefone, e-mail e a descrição do que procura. Os corretores recebem aquela solicitação e caso encontrem um imóvel que se encaixe naquela descrição, enviam um e-mail para o usuário.

- **Proposta e negociação:** Após um cliente se interessar por um imóvel, ele entra em contato com o corretor via telefone ou no botão "Enviar mensagem" na página do imóvel. Os corretores recebem a mensagem e formalizam a proposta, que depois de ser aceita pelo proprietário, a imobiliária solicita os documentos<sup>**1,2**</sup> do imóvel e os documentos do proprietário<sup>**3**</sup>. Caso tudo esteja regular e o pagamento for a vista, as partes interessadas formalizam no cartório com assinatura de escrituras públicas, caso seja um imóvel financiado, tudo é enviado ao correspondente bancário da imobiliária e ele dá andamento.

- ***Comissão:** Após a negociação ser firmada com a assinatura do contrato, o corretor tem direito a 6% do valor da venda, que é pago pelo vendedor, sendo esses 6% divididos entre corretor e imobiliária, ficando 50% para cada.

- ***Administração da locação (Cobrança e repasse de aluguéis):** A imobiliária atua como mediadora financeira, consolidando o valor e os encargos (IPTU e condomínio, se houver), em um único boleto, envia ao locatário e faz a conciliação bancária assim que o pagamento é efetuado. Dessa quantia, é descontada a taxa de administração devida à imobiliária, além de eventuais despesas autorizadas de manutenção ou retenções de impostos. Depois da compensação, o valor líquido é transferido para a conta do proprietário dentro do prazo contratual (até 5 dias úteis) , acompanhado de um extrato detalhado da transação. Em caso de atraso ou inadimplência, a imobiliária executa a régua de cobrança com aplicação de multa e juros e, se necessário, aciona as garantias locatícias do contrato — como seguro fiança, fiadores ou a cláusula de aluguel garantido — para assegurar o recebimento dos valores.

- **Vistoria de entrada e saída:** Antes da assinatura de contrato, o corretor responsável elabora um laudo que registra as condições de pintura, instalações e hidráulicas, pisos, revestimentos, portas, janelas e qualquer mobília existente, com fotos anexadas. Esse documento é validado por ambas as partes (locador e locatário) e assinado antes da entrega oficial de chaves. No encerramento do contrato, a vistoria de saída compara o estado atual do imóvel com o laudo inicial para identificar se houve danos extraordinários causados pelo uso indevido ou falta de manutenção por parte do locatário. O inquilino não responde pelo desgastes naturais decorrentes do uso regular do imóvel ao longo do tempo, mas fica obrigado a reparar estragos causados por mau uso, como furos não autorizados em azulejos ou avarias em equipamentos. Uma vez constatada a igualdade com a vistoria inicial ou finalizados os reparos devidos, o imóvel é recebido e o contrato é formalmente rescindido com a devolução das chaves.

**Processos prováveis não incluídos:**

- **Ações jurídicas :** A imobiliária contrata um time jurídico externo, que processa, elabora, emite e cuida dos contratos aplicados na organização, bem como auxilia na verificação dos d.

- **Anúncio e divulgação em outros portais:** A imobiliária não possuí uma equipe de marketing ou divulgação, a diretora<sup>**1**</sup> contrata serviços esterno terceirizados para anunciar a página. 
> <sup>**1**</sup>(Os custos e processos de cada contratação ficam somente a encargo dela, o grupo não obteve acesso a informações detalhadas).

- ***Ações financeiras:** Com exceção da divulgação e anúncios em portais externos, que é de responsabilidade da diretora da imobiliária, o repasse de contas internas e demais rotinas financeiras internas (salário, benefícios, comissões, aluguel, contabilidade) são organizadas por um agente financeiro externo, a equipe não teve acesso a maiores detalhes. Os processos estão descritos acima para acordarem com as regras de negócio organizacionais e jurídicas.
- 
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

link para visualização no repositório: https://github.com/detailice/Vista_Atlantico_BancoDeDadosGTI/blob/main/MODELO_CONCEITUAL_VISTA_ATLANTICO.jpeg

| Apontamento da correção da E1 | O que mudou no trabalho | Por quê |
| :---- | :---- | :---- |
| *Chaves estrangeiras em três entidades* | *Removemos as chaves estrangeiras das entidades no modelo conceitual* | *As chaves estrangeiras não pertencem ao modelo conceitual, apenas ao modelo lógico* |
| *Link externo do BrModelo no repositório ao invés da imagem do modelo conceitual* | *Removemos o link e adicionamos a imagem no repositório* | *É obrigatório a imagem no repositório para a melhor visualização* |
| *Cardinalidades presentes nos relacionamentos do modelo conceitual divergem do README* | *Modificamos as cardinalidades do DER para serem compatíveis com as cardinalidades do README* | *As cardinalidades precisam ser iguais nos dois documentos* |
|*A entidade CORRETOR não se liga a CONTRATO e VISITA não se liga a IMÓVEL*|*Adicionamos relações entre CORRETOR com CONTRATO e VISITA com IMOVEL*|*São relações obrigatórias pelas regras de negócio e o contexto*|
|*Valores de domínio desenhado como atributos*|*Retiramos valores de domínio*|*Valores de domínio não pertencem ao modelo conceitual*|
|*TIPO como atributo de ASSINA*|*Retiramos o atributo tipo em ASSINA e colocamos somente em CONTRATO*|*O atributo tipo é pertinente ao tipo de contrato (venda ou locação), e não ao tipo de assinatura*|
|*Ausência da entidade encomenda de imóvel*|*Criamos a entidade ENCOMENDA*|*A encomenda é um dos processos principais e possui dados a serem armazenados, portanto deve ser entidade*|
|*Divergência na chave primária do CORRETOR*|*Declaramos como chave primaria ID_CORRETOR e o CRECI como atributo único*|*O ID_CORRETOR garante a segurança de dados do corretor e o CRECI é único e somente em cada estado, usar ID garante unicidade em todos os casos*|

### 1.2 Conversão do Modelo Conceitual para o Modelo Lógico

link para visualização no repositório: https://github.com/detailice/Vista_Atlantico_BancoDeDadosGTI/blob/main/MODELO_LOGICO_VISTA_ATLANTICO.png

- **Entidades → Tabelas** 
**Imóvel → `imovel`**:
A entidade Imóvel virou a tabela `imovel`, com `id_imovel` como PK. É a entidade central do sistema: não recebe chaves estrangeiras, mas é referenciada por `contrato`, `visita`, `fotos_imovel` e pela tabela associativa `possui`. O atributo composto de endereço foi dividido em colunas, e o atributo multivalorado de fotos gerou a tabela `fotos_imovel`.

**Corretor → `corretor`**:
A entidade Corretor virou a tabela `corretor`, com `id_corretor` como PK. O `CRECI` (registro profissional) foi mantido como coluna comum, e não como PK, pois a chave artificial é mais simples de referenciar. O atributo multivalorado de idiomas gerou a tabela `idioma`. Os relacionamentos com Contrato, Visita e Documento geraram as tabelas associativas `intermedia`, `realiza` e `registra`.

**Contrato → `contrato`**:
A entidade Contrato virou a tabela `contrato`, com `id_contrato` como PK. Recebeu a chave estrangeira `id_imovel`, pois cada contrato refere-se a um imóvel. Os relacionamentos com Corretor e Cliente são tratados pelas tabelas `intermedia` e `assina`.

**Proprietário → `proprietario`**:
A entidade Proprietário virou a tabela `proprietario`, com `id_proprietario` como PK. Não recebeu FK, pois o vínculo com o imóvel é feito pela tabela associativa `possui`.

**Visita → `visita`**:
A entidade Visita virou a tabela `visita`, com `id_visita` como PK. Recebeu a FK `id_imovel`, pois cada visita é feita em um imóvel. Os vínculos com Corretor e Cliente são feitos pelas tabelas `realiza` e `agenda`.

**Cliente → `cliente`**:
A entidade Cliente virou a tabela `cliente`, com `id_cliente` como PK. Não recebeu FK, é referenciada por `encomenda` e pelas tabelas associativas `assina` e `agenda`.

**Documento → `documento`**:
A entidade Documento virou a tabela `documento`, com `id_doc` como PK. Não recebeu FK, o vínculo com o corretor que o registrou é feito pela tabela associativa `registra`.

**Encomenda → `encomenda`**:
A entidade Encomenda virou a tabela `encomenda`, com `id_encomenda` como PK. Recebeu a FK `id_cliente`, pois cada encomenda é feita por um cliente.

- **Atributos → Colunas**

**Imóvel → `imovel`**
O endereço é um atributo composto, então foi dividido em `logradouro`, `numero`, `complemento`, `bairro`, `cidade` e `cep`. Os demais atributos viraram uma coluna cada.
- ID_IMOVEL → `id_imovel` (PK)
- QTDE_QUARTOS → `qtde_quartos`
- QTDE_BANHEIROS → `qtde_banheiros`
- TIPO_IMOVEL → `tipo_imovel`
- QTDE_VAGAS_GARAGEM → `qtde_vagas_garagem`
- AREA_M2 → `area_m2`
- VALOR_IMOVEL → `valor_imovel`
- FINALIDADE → `finalidade`
- TIPO_OFERTA → `tipo_oferta`
- IPTU → `iptu`
- STATUS_IMOVEL → `status_imovel`
- LOGRADOURO → `logradouro`
- NUMERO → `numero`
- COMPLEMENTO → `complemento`
- BAIRRO → `bairro`
- CIDADE → `cidade`
- CEP → `cep`

**Corretor → `corretor`**
Todos os atributos viraram colunas diretamente. O `CRECI` foi mantido como coluna comum, e não como PK.
- ID_CORRETOR → `id_corretor` (PK)
- CRECI → `creci`
- NOME → `nome`
- TELEFONE → `telefone`
- STATUS_CORRETOR → `status_corretor`
- EMAIL → `email`

**Contrato → `contrato`**
Todos os atributos viraram colunas diretamente, além da FK que liga o contrato ao imóvel.
- ID_CONTRATO → `id_contrato` (PK)
- ID_IMOVEL → `id_imovel` (FK)
- DATA_INICIO → `data_inicio`
- TIPO_CONTRATO → `tipo_contrato`
- VALOR_CONTRATO → `valor_contrato`
- FORMA_PAGAMENTO → `forma_pagamento`

**Proprietário → `proprietario`**
Todos os atributos viraram colunas diretamente.
- ID_PROPRIETARIO → `id_proprietario` (PK)
- NOME → `nome`
- TELEFONE → `telefone`
- EMAIL → `email`

**Visita → `visita`**
Data e horário foram mantidos em uma única coluna, pois descrevem o mesmo momento.
- ID_VISITA → `id_visita` (PK)
- ID_IMOVEL → `id_imovel` (FK)
- DATA_HORARIO_VISITA → `data_horario_visita`
- ANOTACAO_VISITA → `anotacao_visita`

**Cliente → `cliente`**
Todos os atributos viraram colunas diretamente.
- ID_CLIENTE → `id_cliente` (PK)
- NOME → `nome`
- TELEFONE → `telefone`
- EMAIL → `email`

**Documento → `documento`**
Todos os atributos viraram colunas diretamente.
- ID_DOC → `id_doc` (PK)
- NOME_DOC → `nome_doc`
- DATA_DOC → `data_doc`
- TIPO_DOC → `tipo_doc`

**Encomenda → `encomenda`**
Todos os atributos viraram colunas diretamente, além da FK que liga a encomenda ao cliente.
- ID_ENCOMENDA → `id_encomenda` (PK)
- ID_CLIENTE → `id_cliente` (FK)
- VALOR_MINIMO → `valor_minimo`
- VALOR_MAXIMO → `valor_maximo`
- CIDADE_DESEJADA → `cidade_desejada`
- BAIRRO_DESEJADO → `bairro_desejado`
- DATA_ENCOMENDA → `data_encomenda`
- DESC_IMOVEL → `desc_imovel`
- STATUS_ENC → `status_enc`

**Fotos do imóvel (atributo multivalorado) → `fotos_imovel`**
Como um imóvel pode ter várias fotos, o atributo virou uma tabela própria, ligada ao imóvel por uma FK.
- FOTOS_IMOVEL → `fotos_imovel` (PK)
- ID_IMOVEL → `id_imovel` (FK)

**Idioma do corretor (atributo multivalorado) → `idioma`**
Como um corretor pode falar vários idiomas, o atributo virou uma tabela própria, ligada ao corretor por uma FK.
- IDIOMA → `idioma` (PK)
- ID_CORRETOR → `id_corretor` (FK)

**Tabelas associativas (relacionamentos N:N)**
Cada tabela contém apenas as duas chaves estrangeiras, que juntas formam a chave primária composta.
**intermedia**: `id_corretor` (FK), `id_contrato` (FK)
**assina**: `id_contrato` (FK), `id_cliente` (FK)
**possui**: `id_imovel` (FK), `id_proprietario` (FK)
**realiza**: `id_visita` (FK), `id_corretor` (FK)
**agenda**: `id_visita` (FK), `id_cliente` (FK)
**registra**: `id_doc` (FK), `id_corretor` (FK)



- **Relacionamentos → Chaves**

**Possui (proprietário – imóvel):** O relacionamento virou a tabela `possui`. Um proprietário pode ter vários imóveis e um imóvel pode ter vários proprietários, então nem `proprietario` nem `imovel` poderiam guardar a chave do outro sem repetir registros. Na tabela `possui`, cada linha liga um proprietário a um imóvel, usando `id_proprietario` e `id_imovel`. Juntas, essas duas colunas formam a chave primária.

**Referente_a (contrato – imóvel):**  O relacionamento virou uma coluna. Como cada contrato se refere a um único imóvel, a tabela `contrato` passou a guardar o `id_imovel` do imóvel a que pertence. Essa coluna é obrigatória, pois todo contrato precisa ter um imóvel.

**Recebe (imóvel – visita):**  O relacionamento virou uma coluna. Como cada visita é feita em um único imóvel, a tabela `visita` passou a guardar o `id_imovel` do imóvel visitado. 

**Realiza (corretor – visita):**  O relacionamento virou a tabela `realiza`. Um corretor realiza várias visitas e uma visita pode ter mais de um corretor, então cada linha da tabela liga um corretor a uma visita, usando `id_corretor` e `id_visita`. 

**Registra (corretor – documento):**  O relacionamento virou a tabela `registra`. Um corretor registra vários documentos e um documento pode ser registrado por mais de um corretor, então cada linha liga um corretor a um documento, usando `id_corretor` e `id_doc`, que juntas formam a chave primária. 

**Intermedia (corretor – contrato):**  O relacionamento virou a tabela `intermedia`. Um corretor intermedia vários contratos e um contrato pode ter mais de um corretor, então cada linha liga um corretor a um contrato, usando `id_corretor` e `id_contrato`. 

**Assina (cliente – contrato):**  O relacionamento virou a tabela `assina`. Um cliente assina vários contratos e um contrato pode ter mais de um cliente, então cada linha liga um cliente a um contrato, usando `id_cliente` e `id_contrato`.

**Agenda (cliente – visita):**  O relacionamento virou a tabela `agenda`. Um cliente agenda várias visitas e uma visita pode ser agendada por mais de um cliente, então cada linha liga um cliente a uma visita, usando `id_cliente` e `id_visita`. 

**Realiza (cliente – encomenda):**  O relacionamento virou uma coluna. Como cada encomenda é feita por um único cliente, a tabela `encomenda` passou a guardar o `id_cliente` de quem a fez. A coluna é obrigatória.
 
 **Atributos multivalorados:**  Os atributos multivalorados seguiram a mesma lógica de coluna: a tabela `fotos_imovel` guarda o `id_imovel` do imóvel a que cada foto pertence, e a tabela `idioma` guarda o `id_corretor` do corretor que fala cada idioma.
 
- **Cardinalidades:**
  
**Contrato 0:N Referente_a 1:1 Imóvel →**
Um contrato se refere a exatamente um imóvel, e um imóvel pode ter de 0 a muitos contratos. A FK `id_imovel` ficou em `contrato`. 

**Imovel 1:1 Recebe 0:N Visita →**
Uma visita é feita em exatamente um imóvel, e um imóvel pode receber de 0 a muitas visitas. A FK `id_imovel` ficou em `visita`.

**Cliente 1:1 Realiza 0:N Encomenda →**
Uma encomenda é feita por exatamente um cliente, e um cliente pode fazer de 0 a muitas encomendas. A FK `id_cliente` ficou em `encomenda`.

Os atributos multivalorados também geraram relações 1:N: um imóvel tem várias fotos (`fotos_imovel` recebe `id_imovel`) e um corretor fala vários idiomas (`idioma` recebe `id_corretor`).

**Proprietário 1:N Possui 0:N Imóvel →**
Um imóvel pode ter vários proprietários e um proprietário pode ter vários imóveis. A tabela contém `id_proprietario` e `id_imovel`.

**Corretor 1:N Realiza 0:N Visita →**
Uma visita pode ter mais de um corretor e um corretor pode realizar várias visitas. A tabela contém `id_corretor` e `id_visita`.

**Corretor 1:N Registra 1:N Documento →**
Um documento pode ser registrado por mais de um corretor e um corretor pode registrar vários documentos. A tabela contém `id_corretor` e `id_doc`.

**Corretor 1:N Intermedia 0:N Contrato →**
Um contrato pode ser intermediado por mais de um corretor e um corretor pode intermediar vários contratos. A tabela contém `id_corretor` e `id_contrato`.

**Cliente 1:N Assina 0:N Contrato →**
Um contrato pode ser assinado por mais de um cliente e um cliente pode assinar vários contratos. A tabela contém `id_cliente` e `id_contrato`.

**Cliente 1:N Agenda 0:N Visita →**
Uma visita pode ser agendada por mais de um cliente e um cliente pode agendar várias visitas. A tabela contém `id_cliente` e `id_visita`.


- **Generalização/especialização:**
  
- O DER não possui generalização/especialização, portanto nenhuma das estratégias de conversão foi necessária. Corretor, Cliente e Proprietário têm atributos parecidos (`nome`, `telefone`, `email`), mas foram modelados como entidades independentes, pois têm papéis e relacionamentos diferentes no sistema.

  
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
O processo de normalização foi considerado durante a elaboração e revisão do modelo em sala de aula , cm o objetivo de organizar os dados, reduzir redundâncias e preservar a integridade das informações armazenadas.

- **1FN:**
A 1FN foi considerada na organização dos atributos, buscando garantir que cada coluna armazene valores individuais. No modelo, os atributos multivalorados foram separados em tabelas próprias: `fotos_imovel`, para armazenar as fotos dos imóveis, e `idioma`, para registrar os idiomas falados pelos corretores. Além disso, o endereço do imóvel foi dividido em campos específicos, como logradouro, número, complemento, bairro, cidade e CEP.

- **2FN:**
A 2FN foi considerada na organização das tabelas e na definição das chaves primárias. Os relacionamentos muitos para muitos foram separados em tabelas associativas, como `possui`, `assina`, `intermedia`, `realiza`, `registra` e `agenda`. Nessas tabelas, as chaves estrangeiras que identificam cada relacionamento devem formar uma chave primária composta, evitando a ocorrência de dependências parciais de atributos não-chave.
- **3FN:**
A 3FN foi considerada na organização das entidades e de seus atributos, buscando garantir que os atributos não-chave dependam diretamente da chave primária, sem dependências transitivas. A separação das informações em entidades específicas, como `cliente`, `proprietario`, `corretor`, `imóvel` e `contrato`, contribui para reduzir a repetição desnecessária de informações.
   
- **Justificativa do processo:**
Conforme a revisão realizada em sala de aula, as formas normais foram consideradas durante a construção do modelo. A separação dos atributos multivalorados, a organização dos relacionamentos muitos para muitos e a divisão dos atributos compostos contribuíram para estruturar os dados de maneira organizada. A validação definitiva da normalização será realizada por meio da conferência do modelo lógico relacional e do script SQL completo.

### 1.5 Justificativas Técnicas das Decisões

A arquitetura e a modelagem do banco de dados da Vista Atlântico Negócios Imobiliários LTDA foram concebidas para solucionar a descentralização de informações — caracterizada pela dependência de planilhas e registros em papel — e fornecer uma base robusta para a gestão e a escalabilidade das operações da imobiliária.

**Modelagem Entidade-Relacionamento e Normalização**

* **Separação de Entidades Principais:** A estruturação em entidades independentes (`PROPRIETARIO`, `CLIENTE`, `CORRETOR`, `IMOVEL`, `CONTRATO`, `VISITA`, `ENCOMENDA`) garante o princípio da responsabilidade única. Embora clientes, proprietários e corretores compartilhem atributos básicos de contato, seus papéis no sistema e regras de negócio diferem substancialmente, o que é sustentado pela obrigatoriedade de vínculos específicos para cada perfil de usuário **(Regras Operacionais RN03, RN06 e RN14)**.
* **1ª Forma Normal (1FN):** Atributos compostos foram decompostos (ex.: o endereço do `IMOVEL` foi dividido em logradouro, número, bairro, cidade, CEP). Atributos multivalorados foram isolados em tabelas próprias (`fotos_imovel` e `idioma` do corretor), eliminando repetições na mesma tupla.
* **2ª e 3ª Formas Normais (2FN e 3FN):** Relacionamentos de cardinalidade Muitos-para-Muitos (N:N) foram convertidos em tabelas associativas (ex.: `possui`, `assina`, `intermedia`, `realiza`, `agenda`, `registra`). Essa decomposição elimina dependências parciais e transitivas de atributos não-chave.
* **Relacionamento Ternário de Visita:** O evento `VISITA` vincula obrigatoriamente um `CLIENTE`, um `CORRETOR` e um `IMOVEL`. Essa modelagem atende à restrição de obrigatoriedade, espelhando a regra que exige que qualquer visita presencial seja acompanhada por um corretor credenciado e ligada a um interessado real **(Regras Operacionais RN08 e RN10)**.

**Definição de Chaves Primárias e Unicidade**

* **Chaves Primárias Artificiais:** Adotou-se o uso de identificadores numéricos únicos (como `id_imovel`, `id_corretor`) como chaves primárias (*Surrogate Keys*). Isso otimiza a indexação do SGBD e simplifica o mapeamento de chaves estrangeiras em tabelas associativas.
* **Identificadores Profissionais e Unicidade:** O número de registro do Conselho Regional de Corretores de Imóveis (`CRECI`) foi implementado com uma restrição `UNIQUE` na tabela `CORRETOR` **(Restrição Legal RN02)**. A prática atende à obrigatoriedade da Lei nº 6.530/1978, evitando a duplicidade de profissionais na plataforma sem engessar a chave primária interna.

**Chaves Estrangeiras e Restrições de Integridade**

* **Integridade Referencial e Cardinalidades:** A aplicação rigorosa de chaves estrangeiras (*Foreign Keys*) previne inconsistências e a geração de registros órfãos, garantindo a obrigatoriedade de vínculos válidos — como impossibilitar o agendamento de uma visita para um imóvel deletado ou criar um contrato sem associar as partes devidas **(Regras Operacionais RN08 e RN12)**.

**Conformidade Legal e Decisões Arquiteturais**

* **Controle de Acesso e Minimização:** O modelo prevê suporte a níveis de acesso distintos (usuários padrão vs. privilegiados). O armazenamento atende ao princípio da finalidade da Lei Geral de Proteção de Dados (Lei nº 13.709/2018), colhendo apenas dados necessários para a execução de procedimentos preliminares e contratos (Art. 7º, II e V) **(Restrição Legal RN01)**.
* **Preservação de Histórico (*Soft Delete*):** Em conformidade com as regras da Lei do Inquilinato (Lei nº 8.245/91), o sistema evita a exclusão física (instrução `DELETE`) de dados ligados a negociações, implementando a exclusão lógica (*soft delete*) ou inativação de cadastros **(Restrição Legal RN03)**. Isso preserva o histórico necessário para fins de auditoria financeira e resolução de litígios.
* **Auditoria de Banco de Dados:** O sistema e suas tabelas estão projetados para trabalhar com ferramentas de auditoria (como o plugin `audit_log` do MySQL), garantindo rastreabilidade total das operações de leitura e atualização, atendendo ao princípio da responsabilização (Art. 6º, X da LGPD) **(Restrição Legal RN01)**.

**Arquitetura para Inteligência de Negócios (BI)**

O banco de dados relacional foi estruturado não apenas para a operação diária (OLTP), mas como fundação para a extração analítica. A modelagem viabiliza o cálculo de KPIs fundamentais com junções (`JOINs`) eficientes:

* **Taxa de Conversão de Visitas:** Cruzamento entre as tabelas `VISITA`, `AGENDA` e `CONTRATO`.
* **Tempo Médio de Vacância e Giro:** Análise de disponibilidade através do status do `IMOVEL` e a data de seu último `CONTRATO`.
* **Demanda Não Atendida:** Mapeamento cruzando os parâmetros da tabela de `ENCOMENDA` (o que os clientes buscam) com as características do estoque de imóveis disponíveis.
* **Produtividade Comercial:** Apuração de comissionamento cruzando a tabela `INTERMEDIA` com os respectivos contratos firmados.

### 1.6 Proposta de Arquitetura Analítica para BI e IA

- **Informações estratégicas**
- A centralização das informações no banco de dados permitirá à VISTA ATLANTICO IMOVEIS obter uma visão mais organizada de suas operações comerciais , facilitando  acompanhamento da carteira de imoveis , dos clientes , dos proprietáios , dos corretores , das visitas e dos contratos. Aparti dessas informações , a imobiliaria poderá acompanhar indicadores relacionados a disponibilidade dos imoveis, à movimentações de visitas , ao volume de negociações e ao desempenho comercial dos corretores. Essas informações poderão auxiliar a gestão na identificação de oportunidade de negocio, no acompanhamneto dos resultados, e no planejamento das atividades comercias, considerando também as variações sazonais da procura por imovéis na região da baixada santista.
  
- **Indicadores e métricas gerenciais** propostos (KPIs):

- **G01 – Faturamento por período:** valor total contratado por mês e por tipo de contrato (tabela `contrato`).
- **G02 – Produtividade por corretor:** corretores que mais fecham contratos e realizam visitas (tabelas `corretor`, `intermedia`, `contrato`, `realiza` e `visita`).
- **G03 – Taxa de conversão de visitas:** percentual de visitas que terminam em contrato (tabelas `visita`, `contrato`, `agenda` e `assina`).
- **G04 – Negócios sem visita:** quantidade de contratos fechados sem visita prévia do cliente ao imóvel (tabelas `contrato`, `assina`, `agenda` e `visita`).
- **G05 – Imóveis sem giro:** imóveis disponíveis que estão parados, sem nenhum contrato (tabelas `imovel` e `contrato`).
- **G06 – Demanda não atendida:** bairros com mais encomendas e se há imóvel disponível compatível com a faixa de valor pedida (tabelas `encomenda` e `imovel`).
- **G07 – Desempenho por localização e tipo de imóvel:** bairros e tipos de imóvel que concentram mais visitas, contratos e valor (tabelas `imovel`, `visita` e `contrato`).
- **G08 – Taxa de atendimento das encomendas:** quantidade de encomendas abertas, atendidas e canceladas (tabela `encomenda`).
- **G09 – Volume de atendimentos:** quantidade de visitas e de imóveis visitados por mês (tabelas `visita` e `imovel`).
- **G10 – Estoque (carteira) de imóveis:** carteira de imóveis por situação e tipo de oferta, com o valor total (tabela `imovel`).


- **Potencial dos dados para BI:**
- A utlilização de ferramentas de Business Intlligence poderá transformar os dados armazenados no banco em paineis gerenciaveis e relatorios visuais, facilitando a interpretação dos resultados pela administração da imobiliaria. entre as possibilidades de aplicação , destacam-se:
- Painel de desempenho da imobiiaria: apresentaçao da quantidade de imoveis cadastrados , disponiveis e distribuidos por tipo e finalidade.
- Painel de desempenho comercial: acompanhamento da quantidade de contratos , valores negociados e participação dos corretores nas negociações.
- Relatório de visitas : identificação dos imoveis mais visitados e acompanhamento da movimentação de interessados.
- Análise temporal: comparação mensal dos registros de visitas e contratos, permitindo observar períodos de maior ou menor movimentação comercial.
Essas ferramentas poderão contribuir para uma gestão baseada em dados, reduzindo a dependência de controles decentralizados e facilitando o acesso às informações estratégicas.

- **Aplicações analíticas e de IA:**
- A estrutura de dados proposta poderá servir como base para futuras aplicações de Inteligência Artificial, com a finalidade de apoiar os processos comerciais e melhorar o atendimento aos clientes.
As principais possibilidades identificadas são:

- Sistema de recomendação de imóveis: utilização de algoritmos para recomendar imóveis aos clientes de acordo com critérios como localização, faixa de preço, tipo de imóvel, quantidade de quartos, banheiros e vagas de garagem. Para essa aplicação, será necessário armazenar as preferências e os critérios de busca dos clientes.
- Análise do interesse dos clientes: utilização dos registros de visitas para identificar quais imóveis despertam maior interesse, considerando a frequência de visitação e as características dos imóveis.
- Previsão de demanda imobiliária: aplicação de modelos analíticos sobre dados históricos de visitas e contratos para identificar padrões de procura ao longo dos meses e auxiliar no planejamento comercial.
- Análise de desempenho dos corretores: utilização dos registros de visitas e contratos para identificar padrões de desempenho e apoiar a distribuição de oportunidades comerciais.
As aplicações apresentadas representam possibilidades futuras, não funcionalidades já implementadas. Sua viabilidade dependerá da disponibilidade de dados históricos suficientes, da qualidade das informações armazenadas e da validação dos resultados obtidos pelos modelos analíticos.

**Rastreabilidade:** inclua uma tabela que ligue cada problema declarado na caracterização da organização e cada KPI proposto às tabelas que o sustentam e à consulta do script SQL que o responde (pelo código da consulta — ver seção 3):
| Problema ou KPI | Tabelas envolvidas | Consulta no script |
| :---- | :---- | :---- |
| *P1 — Descentralização de dados* | *ENCOMENDA, IMOVEL, VISITA, CONTRATO, CLIENTE* | *G06, G07* |
| *KPI de faturamento por período* | *CONTRATO* | *G01* |
| *KPI de produtividade por corretor* | *CORRETOR, INTERMEDIA, CONTRATO, REALIZA, VISITA* | *G02* |
| *KPI de taxa de conversão de visitas* | *VISITA, CONTRATO, AGENDA, ASSINA* | *G03* |
| *KPI de negócios sem visita* | *CONTRATO, ASSINA, AGENDA, VISITA* | *G04* |
| *Imóveis sem giro* | *IMOVEL, CONTRATO* | *G05* |
| *Demanda não atendida* | *ENCOMENDA, IMOVEL* | *G06* |
| *KPI de desempenho por localização/tipo* | *IMOVEL, VISITA, CONTRATO* | *G07* |
| *KPI de taxa de atendimento das encomendas* | *ENCOMENDA* | *G08* |
| *KPI de volume de atendimentos* | *VISITA, IMOVEL* | *G09* |
| *KPI de estoque (carteira) de imóveis* | *IMOVEL* | *G10* |
&nbsp;

---
## 2\. Modelo Lógico Relacional

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
Presente no SCRIPT SQL, visualização disponível aqui: https://github.com/detailice/Vista_Atlantico_BancoDeDadosGTI/blob/main/Vista_Atlantico0411.sql

## 5. Uso de Inteligência Artificial

Durante o desenvolvimento deste projeto, utilizamos diferentes ferramentas de Inteligência Artificial para ajudar em dúvidas técnicas, revisão de modelagem, geração de dados e polimento do texto. O grupo alternou entre os modelos, e documentamos abaixo como lidamos com as informações (aproveitando o que era útil e corrigindo alucinações):

| Item | O que registrar |
| :--- | :--- |
| **Ferramenta e etapa** | **Claude 3.5 Sonnet (Versão Gratuita)** - Levantamento de Processos e Requisitos Típicos (Seção 1). |
| **Motivação** | Como não temos vivência no mercado imobiliário, precisávamos de uma base para saber se as informações que pegamos na entrevista faziam sentido e se esquecemos de mapear alguma regra importante. |
| **Prompt(s) utilizados** | *"Quais são as regras de negócio e processos normais de uma imobiliária do litoral? O que o sistema deles precisa ter de requisito funcional pra parte de locação de temporada?"* |
| **Resposta recebida** | O modelo detalhou bem o fluxo de aluguel e vistoria. O mais interessante foi que ele lembrou de processos operacionais específicos de imóveis na praia (como controle de manutenção por maresia), que ajudaram a complementar nossos requisitos. |
| **Fontes consultadas e verificadas** | Conferimos se os processos faziam sentido com as anotações da entrevista e ajustamos os requisitos para a realidade do nosso cliente. |
| **Trechos rejeitados ou corrigidos** | Rejeitamos as sugestões de processos muito complexos (como integração automática com bancos) e corrigimos o que não era pertinente ou que não se encaixava no que levantamos pós-entrevista. |
| **Justificativa da escolha final** | Mantivemos a estrutura básica do fluxo de aluguel porque nos deu uma base sólida, mas adaptamos apenas para as funções que o cliente relatou que fazia manualmente hoje. |
| **Reflexão crítica** | Fizemos uma revisão de todas as respostas para entender a pertinência das informações. A IA tende a sugerir sistemas de grande porte e adicionar funções irreais para o nosso contexto, então precisamos filtrar bastante para não fugir do escopo da disciplina. |

<br>

| Item | O que registrar |
| :--- | :--- |
| **Ferramenta e etapa** | **Gemini 1.5 Pro** - Revisão da Normalização do Modelo Lógico (1FN, 2FN, 3FN). |
| **Motivação** | Estávamos na dúvida se a nossa tabela de imóveis e proprietários estava normalizada direito ou se ia dar problema na hora de criar as chaves estrangeiras. |
| **Prompt(s) utilizados** | *"Dá uma olhada nas nossas tabelas do projeto da imobiliária [colar esquema]. Tem algum erro de normalização aí? Vê se já tá na 3FN ou se a gente precisa separar o endereço do imóvel em outra tabela."* |
| **Resposta recebida** | A IA percebeu que alguns dados do proprietário estavam misturados na tabela do imóvel e sugeriu a correção. A explicação ajudou bastante o grupo a entender como aplicar a 3FN sem complicar demais. |
| **Fontes consultadas e verificadas** | Revisamos a literatura teórica da disciplina sobre dependência transitiva e aplicamos as correções no nosso DER. |
| **Trechos rejeitados ou corrigidos** | Descartamos a sugestão da IA de separar até o Bairro e Cidade em tabelas próprias, pois consideramos desnecessário para o tamanho do nosso sistema. |
| **Justificativa da escolha final** | Adotamos a correção principal (separar dados do proprietário do imóvel), pois fazia total sentido para manter o modelo na Terceira Forma Normal e evitar redundância. |
| **Reflexão crítica** | A IA ajuda a identificar anomalias no banco, mas pode ter o viés de sugerir níveis de normalização excessivos (over-engineering). Revisamos tudo criticamente para aplicar apenas o que o modelo realmente pedia, sem inventar tabelas inúteis. |

<br>

| Item | O que registrar |
| :--- | :--- |
| **Ferramenta e etapa** | **Claude 3.5 Sonnet (Versão Gratuita)** - Adequação do Dicionário de Dados à LGPD. |
| **Motivação** | Como a imobiliária guarda muito dado pessoal de cliente e locatário, queríamos adicionar campos no banco para garantir que o sistema estaria preparado para a LGPD. |
| **Prompt(s) utilizados** | *"O professor pediu pra pensar na LGPD no nosso banco de dados da imobiliária. Que campos eu tenho que colocar na tabela de clientes pra não dar problema com a lei de proteção de dados?"* |
| **Resposta recebida** | O Claude sugeriu colocar colunas de `data_consentimento` e um status para saber se o cliente pediu pra excluir os dados. Foi útil porque inicialmente tínhamos focado só no cadastro básico. |
| **Fontes consultadas e verificadas** | Lemos materiais sobre os princípios da LGPD e adaptamos nosso Dicionário de Dados incluindo essas novas colunas. |
| **Trechos rejeitados ou corrigidos** | Rejeitamos lógicas complexas de mascaramento e criptografia pontual de CPF sugeridas pela IA, que fugiam do escopo da disciplina. |
| **Justificativa da escolha final** | Optamos por manter apenas as colunas de controle (consentimento e exclusão), pois agregam valor na adequação sem tornar a modelagem impossível de fazer no nosso nível de conhecimento. |
| **Reflexão crítica** | A IA às vezes ignora limitações técnicas de um projeto de faculdade e joga conceitos muito avançados. Sempre filtramos o que era irreal de fazer e implementamos os conceitos de privacidade de forma funcional e simplificada. |

<br>

| Item | O que registrar |
| :--- | :--- |
| **Ferramenta e etapa** | **ChatGPT Plus (GPT-4o)** - Geração de Massa de Dados (Seção 4). |
| **Motivação** | Fazer na mão centenas de linhas de INSERT interligadas (Cliente, Imóvel e Contrato) ia levar dias e era muito fácil errar um ID, gerando erro de chave estrangeira no script. |
| **Prompt(s) utilizados** | *"Cria pra mim uns 50 INSERTs na tabela de Cliente e uns 100 na de Contrato de Aluguel pra nossa imobiliária. Finge que são clientes do Brasil, cria uns nomes falsos, e bota as datas variando nesse último semestre."* |
| **Resposta recebida** | Os scripts foram gerados quase completos, mantendo bem a lógica das chaves estrangeiras. |
| **Fontes consultadas e verificadas** | Rodamos o arquivo `.sql` gerado direto no nosso banco de dados local para testar a sintaxe e as constraints. |
| **Trechos rejeitados ou corrigidos** | A IA gerou algumas datas de aluguel no futuro e CPFs com formatações inconsistentes. Corrigimos tudo isso manualmente no arquivo `.sql` antes de submeter no repositório. |
| **Justificativa da escolha final** | Mantivemos o uso da ferramenta pela agilidade absurda. Apesar dos pequenos erros, foi mais fácil corrigir as anomalias geradas do que digitar 150 linhas de inserção do zero. |
| **Reflexão crítica** | Ao gerar a massa, notamos que a IA se perde no meio do processo e começa a dar dados irreais. Revisamos rigorosamente os registros e corrigimos as falhas na cronologia para o banco de dados parecer um ambiente de produção realista. |

<br>

| Item | O que registrar |
| :--- | :--- |
| **Ferramenta e etapa** | **ChatGPT Plus (GPT-4o)** - Criação de Triggers para Auditoria. |
| **Motivação** | Precisávamos criar uma automação no banco pra salvar o histórico de alterações, como quando o valor do aluguel ou o status do contrato muda. |
| **Prompt(s) utilizados** | *"Como que eu faço uma trigger no MySQL pra salvar o histórico de quando alguém altera o status de um contrato na imobiliária? Faz o código pra mim salvando o valor antigo e o novo numa tabela de log."* |
| **Resposta recebida** | O chat entregou o esqueleto da Trigger usando `OLD` e `NEW` e também o código para criar a tabela de log prévia. |
| **Fontes consultadas e verificadas** | Fizemos testes manuais dando `UPDATE` nos contratos no nosso banco para ver se a trigger disparava corretamente. |
| **Trechos rejeitados ou corrigidos** | Rejeitamos comandos extras que o chat gerou (como Procedures complementares) e corrigimos o delimitador do banco (`DELIMITER //`) que veio com um erro de sintaxe. |
| **Justificativa da escolha final** | Aproveitamos a estrutura principal de `NEW` e `OLD`, porque a lógica de armazenamento estava correta e otimizava o que queríamos fazer. |
| **Reflexão crítica** | A IA é ótima para criar o "esqueleto" de automações SQL, mas raramente entrega o código executável de primeira. O código gerado muitas vezes vem misturado com sintaxe de outros bancos, exigindo revisão crítica para adaptar ao nosso SGBD. |

<br>

| Item | O que registrar |
| :--- | :--- |
| **Ferramenta e etapa** | **Gemini 1.5 Pro** - Definição de KPIs e Consultas Gerenciais (Seção 3). |
| **Motivação** | A gente precisava de ideias para indicadores gerenciais e ajuda pra montar os comandos `JOIN` mais complexos sem errar a sintaxe SQL. |
| **Prompt(s) utilizados** | *"Pensando nessa imobiliária, quais métricas legais a gente pode tirar? Faz uns 3 SELECTs usando JOIN e GROUP BY que mostrem dados interessantes, tipo faturamento por mês."* |
| **Resposta recebida** | Recebemos três consultas estruturadas. A resposta surpreendeu porque ele calculou a taxa de ocupação dos imóveis usando funções de data (`DATEDIFF`), economizando nosso tempo. |
| **Fontes consultadas e verificadas** | Revisamos se os KPIs resolviam as dores relatadas pelo cliente na entrevista e testamos todas as consultas no banco de dados. |
| **Trechos rejeitados ou corrigidos** | Rejeitamos métricas mirabolantes (como cálculo preditivo de inadimplência) que não faziam sentido para os dados que tínhamos, corrigindo as consultas apenas para o que levantamos na entrevista. |
| **Justificativa da escolha final** | Escolhemos usar os SELECTs sugeridos para faturamento e taxa de ocupação pois batiam exatamente com os problemas que a imobiliária tem hoje, encaixando bem com a justificativa do projeto. |
| **Reflexão crítica** | Fizemos a revisão para garantir que a IA não inventasse métricas que o sistema não suporta. Quando ela deu consultas fictícias ou inviáveis, descartamos e citamos no repositório apenas o que testamos ser factível. |

<br>

| Item | O que registrar |
| :--- | :--- |
| **Ferramenta e etapa** | **ChatGPT Plus (GPT-4o)** - Estruturação de BI (Views). |
| **Motivação** | Queríamos deixar o banco preparado para um futuro painel (dashboard), criando Views que facilitassem a leitura dos dados consolidados sem precisar rodar queries pesadas na produção. |
| **Prompt(s) utilizados** | *"O que a gente pode fazer de VIEW pro nosso banco de dados da imobiliária pensando em usar num dashboard depois? Monta o SQL de uma view legal que junte clientes, imóveis e contratos."* |
| **Resposta recebida** | A IA criou a VIEW desnormalizando as três tabelas principais para melhorar a velocidade de leitura para o BI. |
| **Fontes consultadas e verificadas** | Executamos o script de criação da VIEW e validamos a resposta no banco local. |
| **Trechos rejeitados ou corrigidos** | A IA tinha agrupado os dados cortando o ID do imóvel e do cliente. Corrigimos o código para manter esses IDs, pois precisaremos deles como chaves no futuro. |
| **Justificativa da escolha final** | A VIEW final foi mantida e adaptada porque o conceito de "achatar" os dados (desnormalizar para leitura) que a IA explicou faz todo sentido em projetos de Business Intelligence. |
| **Reflexão crítica** | Ao pedir scripts de BI, a IA otimizou de forma que eliminou dados cruciais de rastreabilidade. Percebemos o viés da IA de focar apenas no visual do resultado em vez da arquitetura relacional, exigindo correção manual do SELECT. |

<br>

| Item | O que registrar |
| :--- | :--- |
| **Ferramenta e etapa** | **Gemini 1.5 Pro** - Polimento e Revisão Textual Geral (Problemas, Relato da entrevista, Processos, Requisitos, etc.). |
| **Motivação** | Nós tínhamos rascunhos com anotações de todas as seções descritivas da imobiliária, mas queríamos deixar a escrita mais coesa e técnica para o repositório do GitHub, já que é super normal usar a IA pra estruturar ideias com uma linguagem melhor. |
| **Prompt(s) utilizados** | *"Reescreva de uma maneira mais profissional. Esse texto vai para o meu repositório do GitHub em um trabalho de banco de dados. Melhore a linguagem, mas não adicione informações novas e nem faça alterações nos pontos principais e nem nos nossos levantamentos da imobiliária."* |
| **Resposta recebida** | A IA devolveu os textos com uma fluidez muito melhor, transformando nossas anotações informais num vocabulário de projeto técnico. |
| **Fontes consultadas e verificadas** | Fizemos a leitura minuciosa de cada seção após a reescrita, comparando com nossos rascunhos originais para ter certeza de que a essência do negócio foi mantida. |
| **Trechos rejeitados ou corrigidos** | Rejeitamos os trechos em que a IA inventou dados sobre o porte da empresa ou colocou jargões técnicos exagerados que fugiam do nosso tom acadêmico, e reescrevemos com as nossas palavras. |
| **Justificativa da escolha final** | Decidimos usar a versão polida pela IA nas partes estruturais porque a leitura ficou muito mais agradável e direta, o que ajuda na clareza da documentação do README. |
| **Reflexão crítica** | A IA tem um vício em querer "florear" demais textos descritivos e tentar preencher lacunas com dados imaginários (mesmo quando pedimos pra não inventar). Tivemos que fazer uma revisão crítica pesada para cortar essas alucinações e manter a fidelidade da nossa entrevista. |
