= SPEC-001: DeuQuantas App

== Background

O aplicativo **DeuQuantas** surge como uma solução inovadora para trazer transparência e agilidade no relacionamento entre consumidores e estabelecimentos, especialmente bares e restaurantes. O projeto visa resolver desafios comuns enfrentados por ambas as partes, como:

- Consumidores que desejam acompanhar seus pedidos e consumos de forma clara e acessível.
- Estabelecimentos que buscam otimizar a gestão de pedidos, comandas abertas e o cardápio digital.

A partir da digitalização do processo de criação e gestão de comandas por meio de QR Codes, o **DeuQuantas** permitirá que consumidores tenham total controle sobre seus pedidos enquanto oferecem aos estabelecimentos ferramentas eficientes para gestão de operações e integração com a plataforma.

== Requirements

Os requisitos do projeto foram organizados de acordo com a priorização MoSCoW (Must have, Should have, Could have, Won't have), abordando as funcionalidades essenciais e complementares do **DeuQuantas**.

=== Requisitos para Consumidores

*Must have*
- Escanear QR Code para criar uma comanda vinculada ao bar, mesa, horário e usuário.
- Login ou cadastro simples com validação de telefone, utilizando nome, CPF e número de telefone.
- Tela de seleção de bebidas em formato de carrossel, com botões de "+" e "-" para ajustar a quantidade e botão de "Pedir".
- Notificações automáticas via SMS e notificação nativa após cada pedido efetuado.
- Linha do tempo dos pedidos, exibindo o histórico e valor total da comanda.
- Função de "Fechar comanda" com chamada ao garçom ou notificando o garçom.

*Should have*
- Personalização das notificações (ativar ou desativar).
- Interface com sugestões de combinações de pedidos baseadas no consumo anterior.

*Could have*
- Integração com sistemas de pagamento digital.
- Gamificação para consumidores (descontos baseados em uso).

=== Requisitos para Estabelecimentos

*Must have*
- Cadastro do estabelecimento com dados completos da empresa.
- Dashboard para gestão de pedidos e visualização de dados.
- Edição, inclusão e exclusão de itens no cardápio.
- Tela de fila de pedidos exibindo número da mesa e detalhes do pedido.
- Gestão de comandas abertas com possibilidade de fechamento ou adição manual de pedidos.

*Should have*
- Estatísticas de uso da plataforma (pedidos por dia, produtos mais vendidos).
- Configuração de promoções diretamente no app.

*Could have*
- Integração com sistemas de ponto de venda (POS).
- Relatórios avançados por período.

== Method

=== Arquitetura Geral

O **DeuQuantas** será construído utilizando uma arquitetura modular composta pelos seguintes componentes principais:

- **Frontend Web**: Desenvolvido em **Next.js**, será responsável pela interface para estabelecimentos, administradores e consumidores, permitindo acesso às comandas virtuais, visualização de pedidos e gerenciamento do consumo.
- **Frontend Mobile**: Desenvolvido em **React Native**, será a interface principal para consumidores, focando em uma experiência intuitiva para acessar a comanda virtual, realizar pedidos e acompanhar o consumo.
- **Backend**: Implementado em **Python** com **Flask**, gerenciará a lógica de negócios, integração com bancos de dados, autenticação e envio de notificações.
- **Infraestrutura**: Gerenciada com **Terraform** e conteinerização via **Docker**, permitindo escalabilidade e facilidade de implantação.

=== Fluxo de Dados

1. O consumidor escaneia o QR Code na mesa, que redireciona para o aplicativo ou site.
2. O backend valida o QR Code e verifica se o usuário está logado. Caso contrário, é solicitado o login/cadastro.
3. Após autenticação, as informações do cardápio do estabelecimento são carregadas via API.
4. Os pedidos realizados pelo consumidor são enviados ao backend, armazenados no banco de dados e enviados ao estabelecimento para execução.
5. Notificações são geradas automaticamente após cada ação relevante (pedidos, atualizações na comanda, fechamento da conta).

=== Estrutura do Banco de Dados

- **Usuários**:
  - id (PK)
  - nome
  - cpf
  - telefone
  - data_criacao

- **Estabelecimentos**:
  - id (PK)
  - nome
  - endereco
  - telefone
  - data_cadastro

- **Cardápio**:
  - id (PK)
  - estabelecimento_id (FK)
  - nome_produto
  - preco
  - disponivel

- **Comandas**:
  - id (PK)
  - estabelecimento_id (FK)
  - mesa
  - usuario_id (FK)
  - status (aberta, fechada)
  - data_abertura
  - data_fechamento

- **Pedidos**:
  - id (PK)
  - comanda_id (FK)
  - produto_id (FK)
  - quantidade
  - valor_total
  - data_pedido

== Implementation

1. **Configuração de Ambientes**:
   - Configurar ambientes de desenvolvimento para frontend, backend e infraestrutura.
   - Utilizar contêineres Docker para cada serviço, permitindo isolamento e consistência.
   - Provisionar recursos de nuvem usando Terraform para staging e produção.

2. **Desenvolvimento do Frontend Web**:
   - Implementar interfaces responsivas em Next.js para consumidores e estabelecimentos.
   - Garantir integração com o backend via API para login, cadastro e gestão de pedidos.

3. **Desenvolvimento do Frontend Mobile**:
   - Construir o aplicativo mobile em React Native com foco em usabilidade.
   - Implementar suporte para notificações nativas (push notifications).

4. **Configuração do Backend**:
   - Criar APIs RESTful utilizando Flask para gerenciar autenticação, pedidos, notificações e dados do cardápio.
   - Implementar testes unitários e de integração para assegurar a qualidade do código.

5. **Banco de Dados**:
   - Configurar o banco de dados relacional (ex.: PostgreSQL) com as tabelas descritas no modelo.
   - Criar scripts para migração e versionamento do banco de dados.

6. **Infraestrutura e CI/CD**:
   - Configurar pipelines CI/CD para testes, build e deploy automáticos.
   - Implementar monitoramento básico para as APIs e serviços.

7. **Testes e Validação**:
   - Realizar testes de carga e desempenho para garantir a estabilidade do sistema.
   - Conduzir testes de usabilidade com usuários finais.

8. **Deploy e Lançamento**:
   - Implantar a aplicação em ambiente de produção.
   - Garantir treinamento básico para os estabelecimentos utilizarem a plataforma.

== Milestones

1. **Configuração Inicial**:
   - Concluir a configuração dos ambientes de desenvolvimento.
   - Criar repositórios Git com submódulos para cada componente do sistema.

2. **Desenvolvimento dos Protótipos**:
   - Criar wireframes e protótipos funcionais para frontend web e mobile.
   - Validar os protótipos com partes interessadas.

3. **Implementação do Backend**:
   - Desenvolver a API inicial com suporte para autenticação e operações básicas de CRUD.
   - Implementar o modelo de banco de dados descrito.

4. **Desenvolvimento do Frontend Web e Mobile**:
   - Construir as páginas principais (login, cardápio, pedidos) no frontend web.
   - Implementar o fluxo de navegação no aplicativo mobile.

5. **Integração e Testes**:
   - Integrar frontend, backend e banco de dados.
   - Realizar testes unitários e de integração.

6. **Infraestrutura e Automação**:
   - Configurar o pipeline de CI/CD.
   - Automatizar a infraestrutura com Terraform.

7. **Testes de Produção**:
   - Conduzir testes de carga e estresse no ambiente de staging.
   - Corrigir bugs identificados.

8. **Lançamento e Monitoramento**:
   - Implantar o sistema em produção.
   - Monitorar a aplicação para identificar problemas iniciais e coletar feedback dos usuários.

9. **Ajustes Pós-Lançamento**:
   - Implementar melhorias com base no feedback inicial.
   - Adicionar funcionalidades secundárias planejadas.

== Gathering Results

1. **Critérios de Sucesso**:
   - Número de usuários ativos nos primeiros 3 meses.
   - Taxa de adoção pelos estabelecimentos (percentual de estabelecimentos cadastrados em relação ao mercado-alvo).
   - Feedback positivo de consumidores e estabelecimentos.
   - Redução do tempo médio de atendimento nos estabelecimentos.

2. **Métodos de Avaliação**:
   - Coleta de métricas por meio de ferramentas de analytics para monitorar o uso do sistema.
   - Pesquisas de satisfação com consumidores e estabelecimentos.
   - Monitoramento de logs do sistema para identificar padrões de uso e possíveis problemas.

3. **Ajustes Contínuos**:
   - Realizar análises trimestrais para identificar oportunidades de melhoria.
   - Priorizar ajustes e novas funcionalidades com base no feedback coletado.
   - Garantir que os resultados sejam compartilhados com as partes interessadas para ajustes estratégicos.

