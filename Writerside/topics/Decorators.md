# Decorators

São funcionalidades que o NestJS possui que serve para modificar o comportamento das classes, métodos e propriedades

Os decorators são usados com o simbolo de `@`


| Decorator | Categoria Principal | Função Principal |
| :--- | :--- | :--- |
| **`@Injectable()`** | Provedor/Serviço | Marca uma classe como **injetável**, permitindo que ela seja usada e injetada em outras classes via **Injeção de Dependência** (DI). |
| **`@Controller()`** | Estrutura | Marca uma classe como um **Controlador**. Eles são responsáveis por **lidar** com requisições HTTP e enviar respostas. |
| **`@Get()`** | Roteamento HTTP | Marca um método como um *endpoint* que responde a requisições **GET**, usado para **recuperar dados** do servidor. |
| **`@Post()`** | Roteamento HTTP | Marca um método como um *endpoint* que responde a requisições **POST**, usado para **criar dados** no servidor. |
| **`@Put()`** | Roteamento HTTP | Marca um método como um *endpoint* que responde a requisições **PUT**, usado para **atualizar dados** existentes no servidor. |
| **`@Delete()`** | Roteamento HTTP | Marca um método como um *endpoint* que responde a requisições **DELETE**, usado para **apagar dados** do servidor. |


## Beneficios 

| Benefício | Descrição/Impacto Principal |
| :--- | :--- |
| **Reflexão de Metadados** | Permite anexar **metadados** a classes, métodos ou propriedades de forma fácil. |
| **Código Mais Limpo** | Resulta em menos código repetitivo (*boilerplate*) e um estilo de código mais **declarativo**. |
| **Melhor Legibilidade** | Facilita a compreensão imediata da **finalidade** de uma classe, método ou propriedade. |
| **Maior Flexibilidade** | Possibilita **modificar o comportamento** de classes, métodos e propriedades durante a execução (*runtime*). |
| **Melhor Manutenibilidade** | Permite **centralizar mudanças** de comportamento, tornando a manutenção do código mais simples. |
| **Redução de Duplicação** | Ajuda a **evitar a repetição** de código que modifica o comportamento de elementos estruturais. |


## Exemplo

```typescript
@Get('profile')
async getProfile(@Req() request: Request) {
    return this.usersService.find(request.userId);
}
```

