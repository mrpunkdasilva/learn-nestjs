# Exception Filters

Maneira de lidar com excessões por toda a aplicação uniformemente

## Beneficios: 

**Centralização de tratamento de erros:** gerenciar erros em um único lugar 

**Customizar respostar:** criar mensagens de erros amigas ao usuário

## Exemplo:

```typescript
@Catch(NotFoundException)
export class NotFoundExceptionFilter implements ExceptionFilter {
    catch (
        exception: NotFoundException,
        host: ArgumentHost
    ) {
        const ctx = host.switchToHttp();
        const response = ctx.getResponse();
        const status = exception.getStatus();
        
        response.status(status).json({
            statusCode: status,
            message: "Not Found!",
        })
    }
}
```

- **Destrinchando o significado dos blocos:**

| Componente/Método | Detalhe | Função Principal no Tratamento de Exceção |
| :--- | :--- | :--- |
| **`@Catch(NotFoundException)`** | Decorator do NestJS. | Indica que o filtro só deve capturar exceções do tipo **`NotFoundException`** (`404 Not Found`). |
| **`NotFoundExceptionFilter`** | Declaração de Classe. | **Implementa** a interface `ExceptionFilter`, garantindo a presença do método `catch()` com a estrutura correta para manipulação de exceções. |
| **`catch(exception, host)`** | Método Principal. | Onde a lógica de manipulação de exceção acontece. Recebe a **`exception`** e o **`host`** (`ArgumentsHost`) para contexto. |
| **`host.switchToHttp()`** | Context Switching. | Usado para obter o **contexto HTTP** da requisição (em contraste com RPC ou WebSockets), permitindo o acesso aos objetos de `request` e `response`. |
| **`ctx.getResponse()`** | Obtenção do Objeto. | Recupera o **objeto de resposta HTTP** (`Response`) nativo, necessário para manipular o que será enviado de volta ao cliente. |
| **`exception.getStatus()`** | Status da Exceção. | Retorna o **código de status HTTP** (ex: `404`) que está contido na exceção (já que é uma `HttpException`). |
| **`response.status().json()`** | Configuração da Resposta. | Define o **código de status HTTP** e envia uma resposta final formatada em **JSON** para o cliente, contendo a mensagem de erro personalizada (ex: "Not Found!"). |


