# Guards

Os guards vão determinar como qualquer requests é manipulada pela rota, baseado em certos critérios e condições

São classes intjetadas com o decorator @Injectable, eles devem estar implementando a interface `CanActivate` e ter a acesso ao contexto de execução da requisição o que faz com que ela seja mais inteligente que usar um middleware comum do Express


## Beneficio

| Benefício do Uso de Guards | Descrição/Vantagem Principal |
| :--- | :--- |
| **Lógica de Autorização Centralizada** | Permite definir a lógica de autorização em um **único local**, facilitando a gestão do controle de acesso em múltiplas rotas. |
| **Políticas de Segurança Reutilizáveis** | Os Guards podem ser **reutilizados** em diferentes *controllers* ou serviços (ex: verificar autenticação ou funções), promovendo a reutilização de código e evitando repetição. |
| **Segurança Aprimorada** | Fortalecem a segurança ao **interceptar requisições** no início do ciclo de vida, antes que atinjam o *handler* da rota, impedindo acesso não autorizado. |
| **Autorização Sensível ao Contexto** | Têm acesso ao **Contexto de Execução** (requisição, resposta, etc.), permitindo verificações de autorização complexas e **dinâmicas** (ex: checar cabeçalhos ou funções do usuário). |
| **Integração com Outros Recursos** | Integração perfeita com recursos do NestJS, como **Injeção de Dependência** e *Middleware*, possibilitando arquiteturas flexíveis e escaláveis. |



## Exemplo: 

```typescript
@Injectable()
export class AuthGuard implements CanActivate {
    canActivate (
        context: ExecutionContext,
    ): boolean | Promise<boolean> | Observable<boolean> {
        const request = context.switchToHttp().getRequest();
        return !!request;
    }
}


