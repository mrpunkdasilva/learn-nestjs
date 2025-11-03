# Interceptors

Permitem interceptar e transformar HTTP requests/responses na aplicação

> Usamo o decorator: `@Interceptor()`

Temos esses diferentes tipos segundo suas funções:

| Tipo de Interceptor | Uso/Função Principal | Exemplo de Aplicação |
| :--- | :--- | :--- |
| **Logging Interceptors** | Usado para **registrar (log)** informações sobre requisições e respostas (ex: tempo de execução, dados da requisição) no fluxo da aplicação. | Medir o desempenho das rotas e monitorar o tráfego. |
| **Error-handling Interceptors** | Usado para **manipular erros** que ocorrem durante o processamento da requisição ou resposta. | Transformar exceções genéricas em respostas HTTP padronizadas e amigáveis ao cliente. |
| **Security Interceptors** | Usado para aplicar **políticas de segurança** nas requisições e respostas. | Adicionar *headers* de segurança (ex: CORS, CSRF) ou sanitizar dados sensíveis. |
| **Caching Interceptors** | Usado para implementar mecanismos de **cache** para requisições e respostas. | Interceptar uma requisição `GET` para retornar dados em cache diretamente, evitando a execução do *handler* da rota. |



## Beneficios

- **Programação orientada a aspecto:** separação de responsabilidade como logging ou transformar respostas
- **Flexibilidade:** modificar requisições e respostas conforme for requerido


## Exemplo

```typescript
@Injectable()
export class  TransformInterceptor implements NestInterceptor {
    intercept(context: ExecutionContext, next: CallHandler) : Observable<any> {
        return next.handle().pipe(
            map(data => ({result: data}))
        );
    }
}
```