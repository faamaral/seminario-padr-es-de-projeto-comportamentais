# Interpreter

## Intensão

A intensão do `interpreter` é definir uma representação para a gramatica de uma determinada linguagem
juntamente com um interpretador que usará a representação para representar sentenças dessa linguagem.

## Motivação

O padrão Interpreter descreve como definir uma gramatica para linguagens simples, representar sentenças na linguagem e interpretar essas sentenças. 

## Aplicabilidade

O uso do padrão Interpreter é recomendado quando houver uma linguagem a se interpretar e você puder representar sentenças da linguagem como arvores sintáticas abstratas.O padrão `Interpreter` funciona melhor nas seguintes ocasiões.

- Quando a gramática simples é simples.
    Para gramaticas complexas a hierarquia de classes para a gramatica se torna grande e incontrolável. Para esses casos, ferramentas como geradores de analisadores são uma melhor alternativa, pois são capazes de interpretar expressões sem a construção de árvores sintáticas abstratas.

- A eficiência não é a preocupação critica. Os interpretadores mais eficientes não são implementados pela interpretação direta de árvores de análise sintatica, mas pela sua tradução direta para uma outra forma.

## Estrutura

![Estrutura](/images/estrutura.png)

## Participantes

- AbstractExpression (RegularExpression).
    - Declara uma operação abstrata `Interpret` que é comum a todos os nós na arvore sintática abstrata.

- TerminalExpression (LiteralExpression)
    - Implementa uma operação Interpret associada aos simbolos terminais da gramatica;
    - é necessária uma instancia para cada simbolo terminal em uma sentença.
- NonterminalExpression (AlternationExpression, RepetitionExpression, SequencesExpressions)
    - É necessaria uma classe desse tipo para cada regra R::=R1R2...Rn da gramatica;
- Context
    - contém informação que é global para o interpretador
- Client 
    - constrói ou recebe uma arvore sintática abstrata que representa uma determinada sentença na linguagem definida pela gramática.
    - invoca a operação interpret.

## Colaboradores

 - O cliente constrói ou recebe a sentença como uma arvore sintática abstrata de instancias de NonTermanalExpression e TerminalExpression.Então o cliente inicia o contexto e invoca a função ``interpret``.
 - Cada nó NonTerminalExpressoin define interpret em termos de interpret em cada sub-expressão. A operação interpret de cada TerminalExpression define o caso base na recursão.
 - As operações ``interpret`` em cada nó utilizam o contexto para armazenar e acessar o estado do interpretador.

## Consequências

O padrão Interpreter tem os seguintes benefícios e deficiências.

1. É fácil de mudar e estender a gramatica.
2. Implementar a gramatica também é fácil.
3. Gramaticas complexas são difíceis de se manter.
4. Adicionando novas maneiras de se interpretar expressões.

## Implementação




