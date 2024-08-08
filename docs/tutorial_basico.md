## Tutorial Completo: Configurando Código TypeScript com AWS CDK e Lambda Layers

Este tutorial aborda a configuração de um projeto AWS CDK (Cloud Development Kit) em TypeScript, integrando Lambda Layers para organizar e reutilizar o código das suas funções Lambda.

### Estrutura do Projeto

A estrutura de arquivos proposta demonstra uma organização clara, separando a infraestrutura (CDK) das camadas Lambda:

```
projeto_cdk/
├── bin/             
│   └── app.ts       
├── lib/             
│   ├── productsApp-stack.ts
│   ├── ecommerceApi-stack.ts
│   ├── productsAppLayers-stack.ts
│   ├── eventsDdb-stack.ts
│   ├── ordersAppLayers-stack.ts
│   ├── ordersApp-stack.ts
│   ├── invoiceWSApi-stack.ts
│   ├── invoicesAppLayers-stack.ts
│   └── auditEventBus-stack.ts
├── lambda-layers/
│   ├── audit/       
│   ├── auth/       
│   ├── invoices/     
│   ├── orders/      
│   └── products/
├── cdk.json          
└── package.json   
```

### Configuração do Projeto

1. **Crie o projeto:**
   - Se você ainda não tiver um projeto CDK, crie um novo:
     ```bash
     mkdir projeto_cdk
     cd projeto_cdk
     cdk init app --language typescript
     ```
   - Caso já tenha um projeto, navegue até o diretório do projeto.

2. **Instale as dependências:**
   ```bash
   npm install aws-cdk-lib constructs @aws-cdk/aws-lambda @aws-cdk/aws-apigateway @aws-cdk/aws-dynamodb @aws-cdk/aws-s3 @aws-cdk/aws-sns @aws-cdk/aws-ses @aws-cdk/aws-cognito @aws-cdk/aws-xray @aws-cdk/aws-cloudwatch
   ```

3. **Crie as camadas Lambda:**
   - Dentro de `lambda-layers/`, crie uma pasta para cada camada (ex: `audit/`, `auth/`, `invoices/`, etc.).
   - Em cada pasta, crie os arquivos `.ts` com o código das suas funções Lambda.
   - Compile o código TypeScript:
     ```bash
     tsc
     ```

4. **Configure as pilhas (stacks):**
   - Em `bin/app.ts`:
     * Importe as pilhas do CDK que você criou.
     * Crie instâncias das pilhas, passando as configurações necessárias.
     * Exemplo:

       ```
       import * as cdk from 'aws-cdk-lib';
       import { ProductsAppStack } from '../lib/productsApp-stack';
       import { ECommerceApiStack } from '../lib/ecommerceApi-stack';
       // ... (outras importações)

       const app = new cdk.App();
       new ProductsAppStack(app, 'ProductsAppStack');
       new ECommerceApiStack(app, 'ECommerceApiStack');
       // ... (outras instâncias de pilhas)

       ```
   - Em cada arquivo de pilha (ex: `lib/productsApp-stack.ts`):
     * Crie construções (constructs) para cada recurso da AWS que você precisa (Lambdas, DynamoDB, API Gateway, etc.).
     * Use os construtores `@aws-cdk/aws-lambda.LayerVersion` para definir suas camadas Lambda.
     * Exemplo:
       ```typescript
       import * as lambda from '@aws-cdk/aws-lambda';
       // ... (outras importações)

       const auditLayer = new lambda.LayerVersion(this, 'AuditLayer', {
         code: lambda.Code.fromAsset('lambda-layers/audit'),
         compatibleRuntimes: [lambda.Runtime.NODEJS_14_X] 
       });

       const myLambdaFunction = new lambda.Function(this, 'MyFunction', {
         // ... (configuração da função Lambda)
         layers: [auditLayer]  
       });
       ```


5. **Implante:**
   ```bash
   cdk bootstrap
   cdk deploy
   ```

### Dicas e Boas Práticas

* **Mantenha as camadas pequenas:** Camadas muito grandes podem aumentar o tempo de inicialização das funções Lambda.
* **Gerencie dependências:** Use um gerenciador de pacotes como npm para gerenciar as dependências das suas camadas.
* **Teste localmente:** Teste suas funções Lambda localmente antes de implantá-las na AWS.
* **Automatize o deploy:** Utilize ferramentas de CI/CD para automatizar a implantação da sua infraestrutura.
* **Monitore:** Utilize o Amazon CloudWatch para monitorar o desempenho e os logs das suas funções Lambda e outros recursos.

Com este guia completo, você estará apto a configurar seu projeto com o AWS CDK e Lambda Layers em TypeScript, otimizando a estrutura do seu código e facilitando o desenvolvimento e a implantação de aplicações serverless na AWS.

[Créditos: Curso Udemy - AWS Serverless com TypeScript e AWS Cloud Development Kit ](https://www.udemy.com/course/aws-serverless-nodejs-cdk-pt/?couponCode=LETSLEARNNOWPP)
