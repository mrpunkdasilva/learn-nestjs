# Pontos chaves do NestJS

Primeiramente, feche seus olhos, agora image tudo que ele pode ser ao eu dizer: N E S T J S

Eu sei, você sabe, nós sabemos, tu sabereis; a primeira coisa a se pensar foi: 

> "Mais um framework de JavaScript?"

Sim, você está enormemente errado, não é só um framework JavaScript, e sim um ecossistema vivo e bulgante, completamente novo, desacoplado e cheia de vida feito para ser organizado em módulos, facil de manter, facil de escalar, facil de iniciar;

> Modulos para caso você não souber, são unidades de código que são independentes e eu importo e exporto quando preciso. Assim o desenvolvimento se torna mais fácil e reutilizavel 
> {style="note"}


No Nest, temos dois principais **tipos de módulos**:

- Módulo root: o módulo root é o principal, aquele que importa todos os outros módulos na tua aplicação e iniciar ela
- Módulo feature: é todo módulo que é usado para conter um código especifico para alguma _feature_ (funcionalidade) da sua aplicação. 

O NestJS é organizado em uma arquitetura de _tree_ (árvore), onde o módulo root é o topo:

- _Exemplo de como seria essa arquitetura em tree:_

```asciidoc
Root Module (AppModule)
|
|____ Feature Module A (UsersModule)
|      |
|      |____ Service A (UserService)
|      |____ Controller A (UsersController)
|
|____ Feature Module B (OrdersModule)
       |
       |____ Service B (OrdersService)
       |____ Guard B (AuthGuard)
```

> Assim perdemos acoplamento e temos mais eficiencia na dependencia dos ente os módulos

_Exemplo de criação de módulo:_

```typescript
@Module({
    imports: [UsersModule, OrdersModule],
    controllers: [AppController],
    providers: [AppService],
})
export class AppModule {}
```

**Dissecando a estrutura:**
- `@Module({...}` => É o decorator: decoradores são funções especiais que provem metadados nas classes decoradas
- `imports` => é o array de módulos que você vai precisar para a aplicação
- `controllers` => array com os controllers: controller gerenciam requisições e retorno de respostas para o cliente
- `providers` => um array com os providers: provider pode fazer varias coisas no NestJS é como um utilitario
- `export class AppModule {}` => classe do módulo root 

