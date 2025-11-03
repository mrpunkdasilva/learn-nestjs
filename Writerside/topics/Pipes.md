# Pipes

Pipes são funcionalidades poderosas do NestJS que podem ser usdas para transformar dados para fluxos na sua aplicação. Elas são declaradas usando o decorator `@Pipe` 


Temos varios tipos de Pipes, cada uma com uma finalidade, estas são as mais comuns:
- **Validation pipes:** podem ser usadas para validar dados antes de serem processadas pela aplicação
- **Transformation pipes:** podem ser usados para transformar dados em diferentes formatos
- **Logging pipes:** usados para fazer log dos dados no fluxo 
- **Error-handling pipes:** podem ser usadas para manipular erros que ocorram no fluxo dos dados da aplicação

> Podemos encadear as pipes e inclusive elas fazem referencia a **pipe** que temos no _UNIX_

```typescript

@Pipe({name: 'myPipe'})
export class MyPipe {
    constructor(private readonly logger: Logger) {
    }
    
    transform(value: any) {
        this.logger.log('The valiue is: ' + value);
        return value;
    }
}
```

## Beneficios

| Benefício do Uso de Pipes | Descrição/Vantagem Principal |
| :--- | :--- |
| **Flexibilidade** | Permite **transformar dados** de diversas maneiras (ex: validação, conversão de tipo), facilitando a adaptação da aplicação a diferentes requisitos. |
| **Manutenibilidade** | Podem ser facilmente **reutilizados** e **atualizados** em diferentes partes da aplicação, simplificando a manutenção e evolução do código. |
| **Performance** | São executados de forma **assíncrona**, o que contribui para melhorar o desempenho geral da aplicação. |