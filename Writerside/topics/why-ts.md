# Porque TypeScript?

Essa é uma boa pergunta, talvez feita por quem ainda não usou TS (famosa sigla para TypeScript) ou quem ainda não passou de uma linguagem como Java em que você tem que levar muito a serio o type safety em que precisamos pensar em não ser **ambiquo** que é algo que o JavaScript possui, além outras coisas como ele não se autodocumenta já que não precisamos definir tipos por exemplo

Assim esse superset da **Microsoft** foi o primeiro a pegar as luzes dos milhares de frameworks JS que nasciam aos montes do amanhecer a alvorada

## O que a de oferecer então?

Com a tipagem estática do TS temos três principais ganhos: 
- Redução de Erros > obter o tipo de erro apropriado no tempo de compilação
- Qualidade de Código > com essa tipagem estática torna-se mais fácil o código ser legivel e auto documentado
- Suporte pelas IDEs > a maioria das IDEs já aceita o TS

_Diagrama para explicar como o TS funciona:_ Ele primeiro compila arquivos `.ts` via compilador, ts-loader, então escreve um código javascript equivalente antes de todo o código javascript ser colocado em um único bundle para ser o _entry point_ (ponto de entrada) fazendo isso via a bundler (webpack, por exemplo)

![](how ts works.svg)



