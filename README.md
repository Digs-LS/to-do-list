## Diferença entre `var`, `let` e `const`

### `var`
'var ' declara variáveis com escopo limitado à função ou escopo global, sendo facultado inicializar cada um a um valor.
### `let`
'let' declara variáveis locais, reatribuíveis, com escopo de bloco que também pode ser inicializadas cada uma a um valor, como as variáveis de declaração 'var'.
### `const`
'const' declara variáveis locais de escopo de bloco (como 'let'), porém o valor delas não pode ser reatribuído usando  operador de atribuição. Caso a constante (variável) seja um objeto, suas propriedades podem ser adicionadas, atualizadas ou removidas.

## O que é o this em JavaScript, e como seu valor é determinado?

'this' é uma palavra reservada de Javascript que ser refere ao contexto em que uma parte de um código, como uma função, deve fazer funcionar. Normalmente é usada em métodos de objetos, em que 'this' se refere ao objeto que o método está atrelado, permitindo que seja reutilizado. Seu valor, nesse sentido, é determinado pelo contexto de utilização, seja o resultado de uma função ou atributo que está sendo referenciado.

### Como funciona o modelo de eventos em JavaScript? Explique o conceito de "event bubbling" e "event delegation".

O modelo de eventos em JavaScript é baseado no conceito de que ações ou ocorrências (eventos) podem ser detectadas e tratadas por funções específicas chamadas de "event handlers" (manipuladores de eventos). Esses eventos podem ser gerados pelo usuário (como cliques, teclas pressionadas, etc.) ou pelo próprio sistema (como carregamento de página ou conclusão de uma chamada).

Quando um evento ocorre, ele é propagado através do DOM (Document Object Model) de duas maneiras: "capturing" (captura) e "bubbling".

#### Event Bubbling

Processo em que um evento começa no elemento mais profundo do DOM e vai subindo até o elemento pai, e assim por diante, até chegar ao elemento raiz. Por exemplo, se um usuário clicar em um botão dentro de um div, o evento de clique será primeiro capturado pelo botão e depois "borbulhará" para o div pai, e assim por diante.

#### Event Delegation

Event delegation é uma técnica que aproveita o processo de 'event bubbling' para gerenciar eventos de forma mais eficiente. Em vez de adicionar um event listener a cada elemento filho, você pode adicionar um único event listener ao elemento pai. Quando um evento é acionado, ele "borbulha" até o elemento pai, onde pode ser tratado. Isso é especialmente útil quando você tem muitos elementos filhos ou quando os elementos filhos são gerados dinamicamente.

## O que são Promises em JavaScript? Dê um exemplo básico de uso.

Promise é um objeto que representa a compleção eventual, ou falha, de uma operação assíncrona e seu valor resultante. É uma proxy para um valor que não necessariamente sabemos quando a Promise é criada. Em qualquer situação de funções assíncronas, em que o resultado fim pode ser diferente do projetado, como a criação de um arquivo de áudio, que pode ter falhas na finalização, são situações que merecem a avaliação do uso de Promises.