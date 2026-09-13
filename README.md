# BancoDeDados_GTI2S
Repositório criado para o Projeto Semestral de Modelagem de Banco de Dados.

1. Caracterização da Organização

- Nome e natureza da organização: VISTA ATLANTICO NEGOCIOS IMOBILIARIOS LTDA

- Contexto e porte:
Fins lucrativos: Com fins lucrativos. A empresa é registrada como uma Sociedade Empresária Limitada (Ltda.) voltada ao setor privado.
Tamanho da operação: Classificada no regime de EPP (Empresa de Pequeno Porte). Tem sede localizada em Praia Grande / SP.
Número de pessoas envolvidas:
Volume de atividades: Atua no ramo imobiliário. A empresa registra uma carteira com cerca de 900 a 1.000 anúncios de imóveis disponíveis na região da Baixada Santista/Praia Grande. Não realiza doações públicas, rituais ou eventos de caráter comunitário/religioso

- Problemas e necessidades identificados: A descentralização de dados, gerada pela dependência de planilhas e registros em papel, limita o acesso rápido a informações históricas de vendas, carteira de clientes e dados da equipe interna.

- Justificativa da escolha: A organização foi selecionada devido à proximidade e abertura do contato com a direção, comandada pela prima de uma das integrantes da equipe. Outro fator determinante foi o volume de seu portfólio e a oscilação sazonal no fluxo de clientes, típica de períodos como o inverno.

- Evidências da organização:
Razão Social: Vista Atlântico Negócios Imobiliários LTDA (Nome Fantasia: Vista Atlântico Imóveis)
CNPJ: 55.866.811/0001-61 (Ativa na Receita Federal do Brasil)
Registro de Classe: CRECI 46844-J
Endereço Completo: Rua Tupi, 50 – Vila Tupi, Praia Grande - SP, CEP 11703-260
Telefone / WhatsApp de Contato: +55 11 96094-7604
Website Oficial: www.vistaatlanticoimoveis.com.br
Presença no Google / Maps: https://maps.google.com/?cid=15350459088759669626

2. Processos de Negócio

- **Principais processos mapeados:** Cadastro de clientes; Cadastro de imóveis; Cadastro de corretores; Assinatura de contrato; Agendamento de visitas; Encomenda de imóveis (preenchimento de informações do imóvel desejado que gera um alerta em e-mail ou telefone se encontrado);

3. Requisitos do Sistema

3.1 Requisitos Funcionais:

*O que o sistema precisa FAZER (ex.: "o sistema deve permitir registrar uma venda").*

3.2 Requisitos Não Funcionais:
Segurança, usabilidade, disponibilidade, adaptabilidade, acessível,
*Características de qualidade (ex.: desempenho, segurança, usabilidade, disponibilidade).*


4. Regras de Negócio

**Regras operacionais:** 
Apenas indivíduos com maioridade podem anunciar, comprar ou alugar um imóvel;
Um imóvel só pode ser alugado ou vendido se estiver disponível;
Um imóvel só pode ser alugado, vendido ou comprado por um cliente cadastrado na plataforma;
O cliente só pode comprar ou alugar um imóvel mediante a comprovante de renda (holerite);
Nenhum imóvel pode ser cadastrado na plataforma com ausência de imagens em boa qualidade

**Restrições organizacionais:** 

**Conformidade com a LGPD:** a imobiliária não pode armazenar nem compartilhar documentos pessoais de clientes (CPF, comprovante de renda, escrituras) em plataformas abertas sem criptografia e consentimento explícito assinado;
  
**Exigência do CRECI:** Todos os anúncios, contratos e transações precisam registrar formalmente o número do CRECI do corretor responsável e da imobiliária, sob pena de autuação e multa.

**Baixa maturidade digital empresarial:** Funcionários e corretores mais velhos de casa tem maior resistência à novas tecnologias, além do uso de equipamentos domésticos e de baixo potencial utilizados no trabalho.


5. Dicionário de Dados Conceitual (Preliminar)
*(vale 10% — Dimensão Procedimental - Segue o modelo do arquivo 02-03g_Exemplo_Dicionario_Dados.pdf)*

Para cada entidade identificada, liste:

| Atributo | Descrição | Regra de negócio associada |
|----------|-----------|------------------------------|
| *nome do atributo* | *o que ele representa* | *se houver alguma regra (obrigatoriedade, valores possíveis, etc.)* |

*Mantenha o dicionário organizado e padronizado (mesmo formato de tabela para todas as entidades).*

**Atenção à privacidade:** se forem usados exemplos de valores para ilustrar os atributos, esses exemplos devem ser **fictícios** — não utilize dados reais de clientes, fiéis, beneficiários, doadores ou funcionários da organização (nomes, CPFs, contatos etc.), mesmo que tenham sido observados durante a pesquisa de campo. Os exemplos devem apenas ser **coerentes com as operações reais** observadas.


6. Modelagem Conceitual (Entidades, Atributos, Relacionamentos)

- **Entidades reconhecidas:** *liste e justifique brevemente cada uma.*
- **Atributos e classificações:** *quais atributos pertencem a cada entidade.*
- **Relacionamentos pertinentes:** *como as entidades se conectam.*
- **Restrições e políticas organizacionais aplicadas ao modelo.**


7. Diagrama Entidade-Relacionamento (DER)

- Anexe o DER (em imagem).
- O diagrama deve representar corretamente:
  - Entidades
  - Atributos
  - Relacionamentos
  - **Cardinalidades**
- O modelo deve ser **consistente** e já demonstrar potencial de **escalabilidade e integração** (pensando nas próximas etapas do projeto).


8. Justificativa Técnica

*Explique e defenda as decisões de abstração e modelagem tomadas: por que essas entidades, esses atributos, esses relacionamentos e essas cardinalidades — e não outras alternativas possíveis?*


9. Uso de Inteligência Artificial
*(documentação obrigatória — não é opcional se o grupo usou IA em qualquer etapa: pesquisa, escrita, organização de ideias ou revisão de texto)*
generalização incorreta sobre o tipo de organização). |

*Se o grupo não usou nenhuma ferramenta de IA, declare isso explicitamente nesta seção.*
