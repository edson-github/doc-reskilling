## Perguntas Frequentes (FAQ) - Loja Virtual na AWS

### Geral

**1. Qual a finalidade desta loja virtual?**

Esta loja virtual foi desenvolvida como um projeto de demonstração para ilustrar como construir uma aplicação de e-commerce escalável e confiável na AWS. Ela permite gerenciar produtos, pedidos, clientes, eventos, notas fiscais e muito mais.

**2. Quais as tecnologias utilizadas na construção da loja?**

A loja virtual utiliza o AWS CDK (Cloud Development Kit) para definir a infraestrutura em TypeScript, além de outros serviços da AWS, como Lambda, API Gateway, DynamoDB, S3, SNS, SES, Cognito, X-Ray e CloudWatch.


### Funcionalidades

**4. Como faço para adicionar produtos à minha loja?**

Você pode adicionar produtos utilizando a API REST da loja virtual. Consulte a seção "Referência da API" na documentação para obter mais informações sobre os endpoints e parâmetros necessários.

**5. Como os clientes podem fazer pedidos?**

Os clientes podem fazer pedidos através da interface web da loja virtual, que será construída utilizando os arquivos estáticos armazenados no Amazon S3.


Fonte: **Chat Copilot*

Para adicionar uma camada de frontend simples ao projeto AWS CDK TypeScript, você pode seguir estes passos:


1. Escolha uma Tecnologia de Frontend: Decida qual framework ou biblioteca você deseja usar para o frontend (por exemplo, React, Angular, Vue.js).

2. Crie o Projeto Frontend: Crie um novo diretório para o projeto frontend dentro do seu projeto CDK e inicialize o projeto frontend usando a ferramenta de linha de comando do framework escolhido.

3. Construa a Interface do Usuário: Desenvolva suas páginas, componentes e estilos conforme necessário.

4. Integre com o Backend: Use o AWS Amplify ou chamadas diretas de API (fetch, axios etc.) para conectar seu frontend com os serviços backend (por exemplo, API Gateway, Lambda).

5. Hospede o Frontend: Utilize um serviço de hospedagem compatível com SPA (Single Page Application) como o Amazon S3 junto com o Amazon CloudFront para servir e distribuir o frontend.

**6. Como posso acompanhar o status dos pedidos?**

Você pode acompanhar o status dos pedidos através da API REST ou da interface web da loja virtual.

**7. Como funciona o sistema de autenticação?**

O sistema de autenticação utiliza o Amazon Cognito para gerenciar o cadastro, login e logout dos usuários.

**8. Como posso importar notas fiscais?**

Você pode importar notas fiscais em formato XML utilizando a API REST da loja virtual.

### AWS

**9. Quais os principais serviços da AWS utilizados neste projeto?**

Os principais serviços utilizados são:

* **Lambda:** Para processamento de dados e lógica de negócios.
* **API Gateway:** Para criar a API REST da loja virtual.
* **DynamoDB:** Para armazenar dados de produtos, pedidos e clientes.
* **S3:** Para armazenar arquivos estáticos e notas fiscais.
* **SNS:** Para enviar notificações por e-mail (SES) ou SMS.
* **Cognito:** Para gerenciar a autenticação de usuários.

**10. Como posso monitorar o desempenho da minha loja virtual?**

Você pode utilizar o Amazon CloudWatch para monitorar o desempenho da sua loja virtual, criar alarmes e visualizar logs.

**11. Como posso garantir a segurança da minha loja virtual?**

A segurança da sua loja virtual é garantida através de diversas camadas, como:

* **Autenticação e autorização:** Utilizando o Amazon Cognito para controlar o acesso aos recursos da loja.
* **Criptografia:** Criptografando os dados em repouso (DynamoDB, S3) e em trânsito (HTTPS).
* **Firewall de aplicação web (WAF):** Protegendo a API REST contra ataques comuns.
* **Monitoramento:** Utilizando o CloudWatch para detectar atividades suspeitas.

### Suporte

**12. Onde posso obter ajuda para configurar e utilizar a loja virtual?**

Se você tiver alguma dúvida ou precisar de ajuda, consulte a documentação completa da loja virtual ou entre em contato com nossa equipe de suporte.
