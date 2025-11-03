# Dependency Injection

Injeção de dependencia é um design pattern para fazer com que tenhamos menos acoplamento, assim temos baixo acoplamento
e coesão entre todos os blocos do projeto

Assim usamos o decorator de `@Inject()` para determinar que alguma classe será usada para injeção de dependencia. A
dependencia será injetada dentro do construtor da classe quando a classe é instanciada

## Beneficios:

**Testabilidade**: fazer testes unitarios mocando as dependencias se torna mais fácil

**Perda de acoplamento:** classes não estão chumbadas, mas estão providas conforme as necessidades


_Um exemplo de código de dependency injection, onde temos o service que será injetado no módulo:_
```typescript
// typescript code
@Injectable()
export class UsersService {
    constructor(
        private readonly userRepository: UserRepository
    ) {
    }
}
```

