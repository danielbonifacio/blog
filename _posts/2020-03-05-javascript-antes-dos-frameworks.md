---
layout: post
author: Daniel Bonifacio
title: JavaScript antes de qualquer framework
---

> Olá. Antes de iniciar, só para te contextualizar: escrevi esse arquivo na intenção de ser um roteiro para uma série de vídeos, por isso, em alguns casos, verão eu me referindo a este como se fosse um vídeo. No mais, espero que aprendam bastante, e compartilhe o conhecimento. Abs, Daniel Bonifacio.

# JavaScript before any framework

É claro que todo desenvolvedor web já ouviu falar (ou ao menos deveria ter ouvido) sobre React, Vue ou Angular. Estas ferramentas são chamadas de frameworks, que são, basicamente, um conjunto de ferramentas para agilizar o desenvolvimento de aplicações front-end.

Escolher um framework para trabalho, às vezes, é uma decisão difícil. Empresas usam X, você gosta de Y, mas Z paga melhor, enfim... uma porra!

Mas existe algo em comum entre eles que você precisa saber antes de escolher um: JavaScript. Me chamo Daniel Bonifacio, sou Engenheiro de Software e nessa série eu vou te ensinar tudo que você precisa saber sobre JavaScript antes de entrar de cabeça em estudos de algum framework.

Observação: Não vou ensinar coisas muito básicas, como declaração de variáveis, tipos, etc. Imagino que você já saiba isso. Vou ensinar pontos chave do JavaScript **moderno** e metodologias/teorias que grande parte dos frameworks usam.

Antes de iniciar a série de vídeos, vou pedir que compartilhe este vídeo com seus amigos, comente e avalie com um like, pois deu muito trabalho escrever tudo isso. De verdade. Mais de mil linhas de roteiro e exemplos.

Também é importante que você não pule nenhuma aula. Mesmo que você já saiba sobre algum assunto, assista todas as aulas, pois posso falar algo importante ou fazer referência a outra aula no meio.

Então pode se acomodar na cadeira, que lá vem conteúdo bom. Muito bom.

## HTTP Request

Não tem como falar de frameworks front-end sem, antes, entender o que é e como funciona uma requisição HTTP.

Em resumo, toda e qualquer ação que você comete na internet, como acessar uma página ou enviar um formulário, envia uma nova requisição HTTP.

Uma requisição HTTP contém cabeçalhos, (*headers*) corpo, (*body*) verbo (*method* || *verb*) e um destino, que é a URL para onde você vai enviar os dados anteriores.

### Headers

Cabeçalhos são, basicamente, meta informações sobre sua requisição. Nele, geralmente, enviamos e recebemos tokens, cookies, informações sobre o servidor, etc.

### Body

O corpo da requisição é, como o nome sugere, o local onde enviamos e recebemos todas as informações que nossa requisição precisa, com exceção de tokens e outros metadados.

Os dados preenchidos no formulário, credenciais, arquivos, enfim, tudo isso será enviado no corpo da requisição.

### Verbo

O verbo da requisição é apenas outro metadado, mas de exetrema importância para a execução da requsição. Eles definem se a requisição será para recuperar uma informação, enviar uma informação, atualizar um dado ou mesmo deletar algo.

As mais conhecidas:

- GET - geralmente, utilizado para receber algo
- POST - geralmente, utilizado para enviar algo
- PUT, PATCH - geralmente, utilizados para atualizar algo
- DELETE - geralmente, utilizado para deletar algo

Mas não para por aí. A gente falou de como uma requisição, geralmente, é montada, mas não falamos ainda dos tipos de requisição que podemos fazer no nosso navegador.

Como eu falei no começo do capítulo, qualquer ação que você comete na internet, gera uma nova requisição, e dei dois exemplos: acessar uma página e enviar um formulário, e eis a diferença entre eles:

Ao acessar uma página, o seu navegador faz uma requisição HTTP para a URL que você digitou (obrigatoriamente do tipo GET) e recebe, no corpo da resposta, toda a estrutura/marcação HTML da sua página.

Já no envio de um formulário, você pode perceber que, geralmente, a página permanece parada e não atualiza, apenas te da um feedback sobre o status do envio do seu formulário.

Esse tipo de requisição se popularizou com o nome de AJAX. AJAX é um acrônimo para, em tradução livre: JavaScript Assíncrono e XML.

Mesmo que, atualmente, se utilizem formatos mais sustentáveis, como JSON, ao invés do XML, esta técnica ainda é conhecida por este nome, e, sinceramente, foi uma revolução na época.

Em resumo, JavaScript assíncrono é um código JavaScript que roda em outro bloco, lado a lado. Ou seja: você pode fazer várias coisas ao mesmo tempo, com JavaScript assíncrono. Caso você queira saber mais sobre JavaScript assícrono, eu já tenho uma aula sobre isso, veja no link, na descrição.

Pronto, agora você sabe o suficiente sobre requisições HTTP para prosseguir.

### Modules

Outro ponto que você precisa dominar, antes de entrar no mundo dos frameworks JavaScript são módulos. Especificamente, ESModules.

Módulos são formas de importar e exportar objetos dentro do seu código JavaScript.

A sintaxe de módulos é muito simples de ser utilizada. Digamos que você cria uma classe `Human` e quer exportar ela, para usar em outro módulo.

Bom, isso pode ser feito através do `export`.

```javascript
import Animal from './Animal.js' // spoiler

class Human extends Animal {
	say (words) {
		console.log(words)
	}
}

// exports Human constructor
export Human
```

Uma vez importada, você 

Você pode importar assim:

```javascript
import { Human }  from './Human.js'

import Human, { adam } from './human.js' // shortcut

const eve = new Human('Eve')
eve.eat('apple')
adam.say('oh sheet')
```

Claro que não existe somente essa forma de importar ou exportar algo, mas são as mais comuns. A todo caso, existe uma ótima documentação da MDN sobre import e exeport, no link que se encontra na descrição.

- https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Statements/import

Mas esse básico já vai te salvar muito na hora de mexer com os frameworks.

### Classes

Se você não sabe o conceito de orientação à objeto, cara, ce precisa aprender. É amplamente utilizado em, basicamente, toda programação. Mas relaxa que eu tô aqui para ensinar, e é isso que vou fazer.

Antes disso, vou deixar um aviso: caso você não consiga entender o conceito de classes e orientação à objetos no geral, não se sinta mal, este é um paradigma diferente do que, provavelmente, você está acostumado, é um pouco complexo e as pessoas demoram um pouquinho mesmo para entender. Vá com garra! Procure mais fontes de conhecimento depois dessa aula, pois você precisa dominar esse assunto. Não é uma opção.

A orientação à objetos é um conceito muito velho inventado por um programador influente muito velho e que veio a se popularizar há muito tempo. Acredite ou não: da pra reescrever a porra do universo usando esse conceito.

O conceito sugere que, tudo deve ser um objeto. E um objeto é composto por um conjunto de propriedades e métodos. Não sei se você percebeu, mas é assim que o universo funciona.

Uma caneta, por exemplo. Ela tem propriedades, como a tampa, a cor, a marca, a ponta, etc. E métodos, como escrever, tampar, destampar, etc.

Um animal também tem propriedades: olhos, peso, sexo, etc. assim como métodos: respirar, movimentar, ou sei lá, peidar. Animais peidam.

Acho que deu pra entender que objetos possuem propriedades (que são características deles) e métodos (que ações executadas por ele).

O que você também deve ter percebido é que todas as canetas possuem métodos em comum, como, por exemplo: escrever. Todos os animais também, como, por exemplo, respirar.

Agora você, que é o gênio da programação moderna está pensando: "Mas nem toda a caneta tem tampa. Refutado". Agora que essa parada fica interessante: você já estudou sobre evolução e ramificação? Então, da pra fazer isso com a orientação a objetos. Por essa você não esperava.

Resumidamente, existe um conceito de herança na OOP. Uma classe pode basicamente, exender de outra classe.

Se sua cabeça ta explodindo com esse tanto de informação ao mesmo tempo sobre, classes, objetos, heranças, peidos, relaxa, vou te explicar tudo com calma agora.

#### Classes, objects and inheritance

Uma classe é, resumidamente, uma fôrma para um objeto. Ela vai conter todos os métodos daquele objeto. Pensa nela como um esqueleto do objeto.

Um objeto é uma instância dessa classe. Ou seja, posso usar minha forma para fazer vários objetos. Na hora de instanciar, isto é, criar meu objeto, que eu irei informar quais são suas características.

Herança é o ato de você extender uma classe da outra. Esse pode dar um pouquinho mais de trabalho para entender, mas vou tentar resumir na mesma linha de raciocínio.

Imagine que você tem uma classe `Animal`, e esta classe possui as seguintes propriedades e métodos:

- `name` - Propriedade; o nome do animal;
- `class` - Propriedade; o tipo do animal;
- `birthdate` - Propriedade; a data de nascimento do animal;
- `breath` - Método; o que mantem o animal vivo;
- `fart` - Método; você sabe o que é isso.

Essa classe pode ser usada como base para qualquer animal, certo?

Então, se eu quiser criar uma classe de mamíferos, posso simplesmente extender dessa classe e adicionar qualquer outra propriedade e/ou métodos, como amamentar. Uma de peixes, por exemplo, poderia acrescentar chorar, ou nadar.

Como assim "chorar"? Quem que colocou isso no roteiro? Isso provavelmente é uma piada muito sem graça sobre signos que tirou toda minha credibilidade!

Voltando.

Eu também posso herdar de classes herdadas. Uma classe de humanos, por exemplo, herda da classe de mamíferos, que, por sua vez, herda da classe de animais. Nela eu poderia acrescentar diversas novas propriedades, como cor dos olhos, cabelo, tom da pele, sexo, etc. e vários métodos, como andar, falar, etc.

Acho que o resumão é esse mesmo:

adão = nova instância de um Humano com (propriedades)

ou, em JavaScript:

```javascript
const properties = { name: 'adam', sex: 'male' }
const adam = new Human(properties)
```

#### Prática

Criando uma nova classe:

```javascript
class Animal {
	// props and methods goes here
}
```

No exemplo, eu criei uma classe com o nome `Animal`. Por convenção, o nome de classes é dado em *PascalCase*, enquando as instâncias, propriedades e métodos, em *camelCase*.

Adicionando propriedades nessa classe:

```javascript
class Animal {
	constructor(properties) {
		this.name = properties.name
		this.type = properties.type
	}
}
```

No exemplo eu tenho dois novos elementos: o método construtor e a palavra reservada `this`.

- Método construtor (`constructor`): Método que é executado automaticamente assim que uma nova instância é criada. Podemos passar parâmetros para ele.
- Palavra reservada `this`: você já deveria conhecer, mas vou quebrar essa. A palavra reservada `this` sempre irá se referir ao contexto (objeto) em que está sendo executada.

No exemplo acima, eu defini que meu objeto ganharia duas propriedades: `name` e `class` e que estas viriam do meu parâmetro `properties`. Ou seja, defini que as propriedades do meu objeto são as que eu passar no momento que criar ele.

Como o `constructor` é um método, também podemos adicionar propriedades automaticamente, sem depender de um input na instância:

```javascript
class Animal {
	constructor(properties) {
		this.name = properties.name
		this.type = properties.type
		
		// adding birthdate automatically
		this.birthdate = Date.now()
	}
}
```

Mas como falei objetos, além de propriedades, possuem métodos. E eles são criados assim como o método `constructor`, a diferença é que eles não são chamados automaticamente (a não ser que você chame eles no construtor) na criação da instância:

```javascript
class Animal {
	constructor(properties) {
		this.name = properties.name
		this.type = properties.type
		
		// adding birthdate automatically
		this.birthdate = Date.now()
	}
	
	breath() {
		console.log('Huff')
	}
	
	fart() {
		console.log('Poot')
	}
}
```

Agora que temos nossa classe, podemos criar quantas instâncias queremos.

```javascript
class Animal {
	// [... class stuff]
}

// creating an instance
const frog = new Animal({
	name: 'froggy',
	type: 'amphibian'
})

// accessing instance methods
frog.fart() // -> "Poot"

// accessing instance properties
console.log(frog.type) // -> "amphibian"
```

Agora ta na hora de aprender a herdar de classes. É isso que move o mundo!

Existes peculiaridades na hora de herdar de uma classe:

- Você precisa herdar de uma classe, nunca de uma instância;
- Você precisa chamar o método `super` no construtor da classe a ser extendida, para passar as propriedades dela para para a classe-pai;
- Você pode adicionar novos métodos, e estes métodos estarão disponíveis somente nesta classe ou em classes que herdam dela. A classe pai ou irmãs não serão afetadas.

```javascript
class Mammal extends Animal {
	constructor(properties) {
		// super calls the parent constructor
		// I've called with the type setted
		super({
			...properties,
			type: 'mammal'
		})
	}
	
	// adding new methods
	// this method will only be accessible in this class instances
	// parent or siblings instances will not have this method
	breastfeed(time = 1500) {
		// I rlly dont know how2 represent this in javascript, srry
		console.log('*breastfeeding')
		setTimeout(() => console.log('*finished'), time)
	}
}
```

No exemplo, eu criei uma classe `Mammal` (mamífero) que extende de `Animal`, e diretamente no construtor, eu chamei o método `super` repassando as propriedades que recebo como parâmetro na criação da instância, mas sobescrevendo a propriedade `class` como mamífero.

Também adicionei o método `breastfeed` (amamentar), sendo este um método que só poderá ser acessado por instâncias dessa classe (*Mammal*) ou de classes herdadas dela.

Caso não tenha entendido muito bem a parte do super, deixo [esse artigo da MDN](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Operators/super) como referência para estudo.

Uma pergunta recorrente é "mas e se eu não quiser herdar o método X ou propriedade Y?". A resposta ficará mais óbvia e aceitável com o passar do tempo e experiência com o paradígma.

Se você precisa remover um método herdado, sua evolução está incorreta.

Agora você tem duas opções: refazer sua arvore genealógica da forma correta, ou seja, acrescendo um ancestral primordial que não possui aquela propriedade ou método, ou seguir o baile e torcer pra ninguém nunca chamar aquele método que não deveria estar ali.

Agora você já sabe sobre classes.

### Spread

Chegamos num dos carinhas mais legais do JavaScript moderno, o operador de Spread.

Eu chamo ele de operador da liberdade. Mais pra frente cê vai ver o motivo.

Na descrição oficial da MDN sobre o Spread, dizem que esse operador:

> "permite que um objeto iterável, como um array ou string, seja expandida em locais onde zero ou mais argumentos (para chamadas de função) ou elementos (para literais de array) sejam esperados ou uma expressão de objeto seja expandida em locais onde zero ou mais pares de chave-valor (para literais de objeto) são esperados."

Vamos entender isso com calma, por partes.

Ela diz que ele *"permite que um objeto iterável [...] seja expandido em locais onde zero ou mais argumentos [...] são esperados"*

Isso significa que se eu tenho uma função que espera, vamos dizer, 3 argumentos, posso chamar ela com um objeto iterável com o operador Spread, onde cada item será um parâmetro:

```javascript
class Person extends Human {
	constructor(name, age, career) {
		this.name = name
		this.age = age
		this.career = career
	}
}

const iterableObject = ['Daniel', 20, 'Engenheiro de Software']

// this
const me = new Person(...iterableObject)
// has same effect as this
const me = new Person('Daniel', 20, 'Engenheiro de Software')
```

Isso significa, também, que eu posso ter uma função que espera um número indefinido de argumentos, fazendo a lógica inversa:

```javascript
function spell(...chars) {
	// chars will be an array with all arguments received
	chars.forEach(console.log)
}

spell('A', 'E', 'I', 'O', 'U')
```

Se você já trabalhou com Ruby alguma vez, vai notar que é, basicamente, a mesma coisa que o operador *\*Splat*.

Mas lembra que eu disse que chamava o Spread de "operador da liberdade"? Acho que é muito mais simples se você visualizar que este operador liberta os itens que estão contidos no objeto.

```javascript
spell('A', 'E', 'I', 'O', 'U') // normal
spell(...['A', 'E', 'I', 'O', 'U']) // com spread
```

Se você reparar bem, o que ele faz é "remover" as chaves/colchetes que seguram os itens. Simples assim. E isso também é válido para objetos.

Se você imaginar que o spread remove as chaves ou colchetes que estão ao redor do objeto, vai conseguir utilizar ele bem facilmente em várias situações.

```diff
-['A', 'E', 'I', 'O', 'U']
+'A', 'E', 'I', 'O', 'U'
```

E, falando em objetos, vamos ir para a parte do spread que fala sobre ele. Na referência diz que ele *"permite que [...] uma expressão de objeto seja expandida em locais onde zero ou mais pares de chave-valor [...] são esperados."*.

O que eles querem dizer com isso é que você pode espalhar um objeto da mesma forma que espalha um array.

Eu fiz isso quando falei de classes, não sei se você lembra.

```javascript
class Mammal extends Animal {
	constructor(properties) {
		super({
			...properties, // bem aqui
			type: 'mammal'
		})
	}
}
```

Imagine que o valor de `properties` seja um objeto com 2 propriedades: `name` e `sex`. E eu preciso passar um objeto com 3 propriedades (`name`, `type` e `sex`) para o meu método `super()`.

Para fazer isso sem o spread, teria que fazer isso:

```javascript
class Mammal extends Animal {
	constructor(properties) {
		super({
			name: properties.name,
			sex: properties.sex,
			type: 'mammal'
		})
	}
}
```

O que, por enquanto, não é ruim. Mas a medida que essas propriedades vão aumentando, vai ficando horrível para quem vai dar manutenção.

Você pode estar pensando: "mas e se eu passar o objeto inteiro sem o spread, não iria surtir o mesmo efeito?". A resposta é não. 

Esse seria o resultado:

```javascript
class Mammal extends Animal {
	constructor(properties) {
		super({
			properties,
			type: 'mammal'
		})

		// expected:
		// { name, sex, class }

		// received:
		// {
		//   properties: { name, sex },
		// 	 class
		// }
	}
}
```

Talvez agora que você entenda o que eu disse sobre remover as chaves ou colchetes.

Ao utilizar o Spread, eu removi as chaves ao redor do meu objeto, elevando trazendo os filhos dele para o mesmo nível do objeto onde o Spread foi utilizado.

#### Spread and Functional Programming

O operador Spread se torna muito útil, por exemplo, em aplicações de programação funcional.

```javascript
const toDos = ['wash car', 'buy milk']
const newTodos = [...toDos, 'play videogames']

console.log(newTodos) // -> ['wash car', 'buy milk', 'play videogames']
```

Vale lembrar que, em casos de objetos e duplicidade de chaves, a ordem de prioridade é igual a do CSS: o último item declarado que prevalece.

```javascript
const me = {
	name: 'Daniel',
	age: 20,
	height: 1.93
}
const newMe = {
	...me,
	age: 21 // placed after, will overwrite
}

const notSoNewMe = {
	age: 21, // placed befor, will be overwrited
	...me
}

console.log(newMe) // -> { name: 'Daniel', age: 21, height: 1.93 }
console.log(notSoNewMe) // -> { name: 'Daniel', age: 20, height: 1.93 }
```

Pronto. Agora você já sabe o suficiente de spread para continuar.

### Fetch

A gente já falou de requisição HTTP antes, lembra? O fetch é a API moderna do JavaScript que permite, de forma muito fácil, que a gente faça requisições AJAX nas nossas aplicações.

Você incondicionalmente precisa saber o que são promises, async e await para prosseguir sobre este assunto. Eu já falei sobre isso antes. O Link está na descrição.

Bom, como esta é uma API, pra facilitar, vou mostrar alguns exemplos e explicar o que eles fazem.

```javascript
fetch('https://jsonplaceholder.typicode.com/posts', {
	method: 'GET',
	headers: {
		authorization: 't0p_s3cr3t_t0k3n',
	}
})
	.then(response => response.json())
	.then(posts => {
		posts.forEach(post => console.log(post))
	})
	.catch(console.err)
```

Mesmo o código sendo autoexplicativo, vamos explicar ele.

O objetivo do código é acessar a API do JSON Placeholder, recuperar todos os posts e logar cada um, separadamente, no console.

Na primeira linha, a gente inicia uma nova requisição para a URL `https://jsonplaceholder.typicode.com/posts`, passando ela como o primeiro parâmetro do método `fetch()`.

Já nas linhas de 2 a 5 a gente passa algumas opções para a nossa requisição, como o `method` (verbo) e um objeto de headers, que contém uma chave `authorization`, que é um padrão de envio de Token.

Essa API retorna uma Promise, então vamos capturar seu retorno com `then()` e `catch()`.

Reparem que existe um Promise chaining no código. Isso se deve pelo fato de que o retorno da promise é um objeto completo de resposta de requisição, com código de status, headers, etc.

Mas, na maiorias massiva das vezes, a gente só precisa do corpo da resposta. Os dados em si. Por isso o objeto de resposta possui um método chamado `json()`, que retorna apenas o corpo.

Então, na segunda liga da corrente, temos acesso aos posts diretamente. Agora iteramos sobre o array de posts, logando cada um separadamente.

O catch tá ali esperando algum erro de conexão ou falha na resposta do servidor.

#### Error handling

Agora vamos entrar num dos pontos negativos de se trabalhar com a fetch API, ao invés de uma biblioteca específica para requisições HTTP, como o axios.

Em APIs REST a comunicação de erros é feita por código de status. Independente do que aconteça dentro do servidor, sempre haverá uma requisição e uma resposta.

Geralmente, identificamos um erro por meio do código de status da requisição.

O grande problema com a fetch API é que ela considera que "existe uma diferença entre um "erro" e uma "exception". [...] Não existe exception em receber códigos 4xx ou 5xx [...].".

Por mais que eu tenha que concordar com quem disse isso, no ponto de vista teórico, isso significa que, na prática, você vai receber as respostas de erro da API no mesmo bloco que suas respostas de sucesso.

Isso te obrigrar a comparar o status da requisição e, dependendo da camada onde você está, isso é, no meu ponto de vista, algo muito errado.

``` javascript
fetch('https://jsonplaceholder.typicode.com/posts', {
	method: 'GET',
	headers: {
		authorization: 't0p_s3cr3t_t0k3n',
	}
})
	.then(response => {
		const { status } = response

		if (status >= 400 && status < 600) {
			throw { status, response }
		}

		return response.json()
	})
	.then(posts => {
		posts.forEach(post => console.log(post))
	})
	.catch(console.err)
```

Como no exemplo acima. Isso é totalmente fora do padrão de responsabilidade.

Então, entenda que se for mesmo usar fetch API, você terá 2 opções:

- Quebrar padrões de desenvolvimento, aplicando responsabilidade que não deveriam estar ali, ali;
- Encapsular ela em uma classe de requisições, e usar a classe. (melhor opção, no meu ponto de vista)

Pronto, você sabe o suficiente sobre a fetch API.

### Array manipulation

Especialmente em sistemas, você vai trabalhar muito com listagens e filtros. E o JavaScript moderno facilitou tanto isso pra gente, que você não vai mais trabalhar com arrays da mesma forma, depois desta aula.

Você vai aprender os métodos `map()`, `filter()` e `reduce()` e algumas técnicas legais que vão te ajudar no dia a dia.

Mas, antes, vamos entender o básico de programação funcional, pois estes métodos são funcionais.

#### Functional Programming

Já dei um exemplo de programação funcional anteriormente, quando falamos no *Spread operator*. Mas agora vou dar um resumo sobre o que ela é.

A programação funcional trabalha com um conceito de imutabilidade, e isso significa que, na programação funcional, nada tem seu valor alterado, tudo retorna um novo valor.

Sei que isso pode parecer estranho, e esse assunto é tão complexo que merece uma série vídeos só pra ele, mas, por agora, entenda apenas que, na programação funcional, o valor de variáveis não é alterado. Novas variáveis que tomam seu lugar.

E, como sei que você tá pensando "Mas por que caralhos?", vou dar um resuminho das vantagens da programação funcional:

1. Facilidade nos testes e na busca por bugs;
2. Uso de gerenciamento de memória automático;
3. Semântica simples;
4. Reduz a complexidade do código;
5. Aumenta a modularização do código.

Resumo: existem muitas vantagens em trabalhar com Programação Funcional, e alguns frameworks, como React, por exemplo, adotam ela como base.

#### `map()`

Agora vamos falar do `Array.map()`, o mais famoso de todos, sem dúvidas.

Lembrando: todos os métodos estão contidos no construtor `Array`, então podem ser acessados por meio deles.

Você lembra como que se cria um array baseado em outro array, manipulando os dados internos?

Existem `N` formas de fazer isso, mas vou fazer do jeito mais antigo que lembro.

```javascript
const numbers = [0, 1, 2, 3, 4, 5]

const multiplyTimes = (array, times = 2) => {
	const newNumbers = []

	for (let i = 0; i < array.length; i++) {
		const newNumber = array[i] * 2
		newNumbers.push(newNumber)
	}

	return newNumbers
}
```

No exemplo, criamos um array de números de 1 a 5, e depois criamos uma função que retorna os mesmos números multiplicados por 2.

Fizemos isso com um laço de repetição `for`, da forma mais clássica possível.

E se eu te disser que isso tudo pode se resumir em 1 linha de código, vai surtar? Pois é, com o `map()` pode.

``` javascript
const numbers = [0, 1, 2, 3, 4, 5];

const multiplyTimes = (array, times = 2) => array.map(number => number * times)
```

Antes de tudo, lembre-se que disse que os métodos que eu disse aqui, são funcionais, isto é, eles retorna um novo valor que será um array.

O método map recebe uma função como parâmetro, e esta função será executada em cada iteração. Ela recebe o valor do item que está sendo percorrido, no primeiro parâmetro, o segundo, o índice daquele valor, e, em terceiro, o array completo que está sendo iterado.

Se você executar no console:

```javascript
['A', 'B', 'C', 'D'].map(console.log)
```

terá uma noção básica do que ela recebe como parâmetro.

E, para cada iteração, eu **preciso** retornar um valor. Esse será o valor inserido naquele índice, no novo array. Caso você não retorne nada, aquele índice receberá `undefined`.

Então, voltando ao código do exemplo, eu criei uma função com o mesmo nome, que recebe os mesmos parâmetros, ela retorna um array (`Array.map()` retorna um array). Esse array é resultado do map do array passado como parâmetro, onde, em cada índice, eu retorno o valor daquele índice multiplicado por 2.

E, como este é um método funcional, ou seja, não modifica o valor original, `numbers`, permanece com o mesmo valor de antes.

O map é muito útil no react, quando você vai renderizar uma lista.

Um spoiler seria mais ou menos assim:

```jsx
const List = (list) => <ul>
	{ list.map(item => <li key={item.id}>{item.title}</li>) }
</ul>
```

Se você nunca viu, esse negócio aí em cima, te apresento um código simples em React.


#### `filter()`

Vimos, anteriormente, que o método `map()` precisa retornar um valor para o índice, do contrário, aquele índice retornará `undefined`. Isso impede a gente de criar uma lista filtrada, afinal, iremos ter objetos inconsistentes no array, gerando problemas futuros.

Mas, para resolver estes casos, existe o `filter()`.

Ele recebe os mesmos parâmetros que o `map()`, mudando apenas sua forma de retorno.

Com o filter, você precisa retornar um *booleano*. Caso este booleano seja `true`, aquele item será adicionado no array final, caso seja `false`, será ignorado.

Ou seja, ele server para filtrar itens de um array mesmo, como o nome sugere.

```javascript
const numbers = [0, 1, 2, 3, 4, 5]

// without filter
const getOdds = (array) => {
	const odds = []

	for (let i = 0; i < array.length; i++) {
		const isOdd = array[i] % 2 !== 0
		if (isOdd) {
			odds.push(array[i])
		}
	}

	return odds
}
```

No exemplo criamos um algorítmo que, basicamente, retorna todos os números que não são divisores por 2, ou seja ímpares, do nosso array.

Esse mesmo método pode ser escrito da seguinte forma, com `filter()`:

```javascript
const numbers = [0, 1, 2, 3, 4, 5]

const getOdds = (arr) => arr.filter(number => number % 2 !== 0)
```

Novamente, nosso array de origem (`numbers`) está intácto.

Uma aplicação muito comum do filter em frameworks, como o React ou Vue, é para remover um item de um array.

A técnica consiste em, basicamente, retornar todos os itens do array, exceto aquele que estamos querendo remover.

```javascript
const removePerson = (people, id) => people.filter(person => person.id !== id)
```

E, para usar nosso método, é simples:

```javascript
const people = [
	{id: 1, name: 'Jake'},
	{id: 2, name: 'John'},
	{id: 3, name: 'Jacob'},
	{id: 4, name: 'Jasmine'}
]

const newPeople = removePerson(people, 1)
```

#### `reduce()`

O propósito do `reduce()` é, basicamente, iterar por um array, trazendo um único valor como retorno. Esse retorno pode ser de qualquer tipo.

O método `reduce()` recebe, dois parâmetros. O primeiro é a função que será executada a cada iteração, e o segundo é o valor inicial do resultado final.

Basicamente, são esses parâmetros:

```javascript
Array.reduce(function(accumulator, currentValue, currentIndex, originalArray), initialValue)
```

Vamos começar com o básico, depois a gente vai aprofundando.

Nosso primeiro algoritmo com o reduce, vai simplesmente somar todos os números de um Array.

```javascript
const toSum = [1, 2, 3, 4]
toSum.reduce((accumulator, currentValue) => acumulator + currentValue)
```

O resultado deve se 10, certo? Pois `1 + 2 = 3`, `3 + 3 = 6` e  `6 + 4 = 10`.

Vamos fazer nosso script dizer o passo a passo também?

```javascript
toSum.reduce((accumulator, currentValue) => {
  const result = accumulator + currentresult
  console.log(`${accumulator} + ${currentValue} = ${result}`)
  return result
})
```

E se a gente quiser passar um valor inicial para o `accumulator`? Simples, existe o parâmetro para isso.

```javascript
toSum.reduce((accumulator, currentValue) => {
  const result = accumulator + currentresult
  console.log(`${accumulator} + ${currentValue} = ${result}`)
  return result
}, 5)
```

Pronto, agora você tem uma contagem que inicia a partir de 5. E, também, já sabe como trabalhar com reduce.

Lembrando que o `reduce()` é um caso complexo. Tem gente que não entende sua necessidade de jeito nenhum. Eu recomendo que se ainda restarem dúvidas, você acesse os três links que estarão da descrição.

O primeiro é um post do Raul Esteves, ["Entendendo o reduce() de uma vez por todas"](https://medium.com/@raullesteves/javascript-entendendo-o-reduce-de-uma-vez-por-todas-c4cbaa16e380) onde ele explica o método passo a passo, achei muito bom.

O segundo é a [documentação do reduce no MDN](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Array/reduce).

O terceiro, por fim, é um vídeo do Wes Doyle: ["Javascript Reduce by Example"](https://www.youtube.com/watch?v=CXxVjQ1VTEo), que é um live coding resumido muito bom também.

É isso. Espero que agora você já saiba como manipular arrays da melhor forma, com JavaScript.


### Arrow function

Nossa, achei que não ia chegar nunca nesse assunto. Mas deixei ele mais pro final, pois eu queria que você, que não conhece as *Arrow functions* ficasse impressionado com o poder que elas têm sobre a legibilidade e manutebilidade do código.

Claro que *Arrow functions* não se resumem em deixar o código mais legível, existe uma finalidade (muito importante) por trás dela, e é nessa aula que você vai descobrir.

#### Syntax

A sintaxe das arrow functions é muito simples.

No JavaScript *oldschool*, você declarava funções através da keyword `function`:

```javascript
function myCommonFunction () {
	// do my stuff
}
```

Você podia, também, definir que o valor de uma variável recebe uma função.

```javascript
var myCommonFunction = function () {
	// do my stuff
}
```

Com a chegada das *Arrow functions*, você pode fazer a mesma coisa.

```javascript
const myArrowFuncion = () => {
	// do my stuff
}
```

Percebe que apenas removemos a chave `function` e acrescentamos o `=>`? Daí o nome *Arrow functions*.

Mas calma. A mágica das *Arrows functions* ainda está por vir.

Imagine que você tem uma função que retorna algum valor, por exemplo, uma ternária. Antes das *Arrow functions* você tinha isso:

```javascript
var myCommonFunction = function (condition) {
	return condition
		? 'foo'
		: 'bar'
}
```

E se você pudesse resumir isso em, digamos 1 linha? Bom, na verdade, você pode. Com arrow functions.

```javascript
const myArrowFuncion = condition => condition ? 'foo' : 'bar' 
```

Isso acontece por que o interpretador permite que você retorne expressões diretamente após o `=>`. Vai falar que isso não é demais?

Você também pode retornar objetos e arrays diretamente, mas com uma peculiaridade: deve colocar entre parênteses:

```javascript
const updateUser = (newProps, user) => ({ ...user, ...newProps }) 
```

```javascript
const addFruit = (newFruit, fruits) => ([ ...fruits, newFruit ]) 
```

Juntamos o *Spread operator* com *Arrow functions*.

Mas calma, não para por aí. Agora vamos ao real sentido das *Arrow functions*, a permanência do contexto.

Como você já sabe, ou, ao menos, deveria saber, no JavaScript existe uma chave reservada `this` que se refere ao contexto a qual está sendo executado.

Funções geram um novo valor para o this, e isso é um problema, especialmente em casos de callbacks. Vamos demosntrar o problema:

```javascript
function Person() {
  this.age = 0;

  setInterval(function growUp() {
    this.age++;
  }, 1000);
}

var p = new Person();
```

No exemplo, o construtor de Person() define o valor de `this` como a própria instância. Já dentro da função que é executada como callback do setInterval, o valor de this já não é o mesmo, pois ele agora recebe um novo valor. No caso, em modo não estrito, o valor de `this` será o objeto *global*, que é onde growUp foi executado.

Isso significa que, para obtermos acesso valor de `this` definido pelo construtor, precisávamos alocar em uma variável e acessar por meio dela.

```javascript
function Person() {
  this.age = 0;

	const self = this

  setInterval(function growUp() {
    self.age++;
  }, 1000);
}

var p = new Person();
```

Ou usamos uma *Arrow function*. :)

Arrow functions não recriam o valor de `this`, elas mantém o valor do executor.

O problema inicial do exemplo poderia ser resolvido apenas com uma *Arrow function*:

```javascript
function Person() {
  this.age = 0;
  setInterval(() => this.age++, 1000);
}

var p = new Person();
```

Você vai ver muito o uso de *Arrow functions* em tudo quanto é lugar ou framework. Então vou deixar outras referências:

- [Fireship: Functions - What's your function? (inglês)](https://www.youtube.com/watch?v=gigtS_5KOqo)
- 

### Destructuring

Destructuring é uma técnica simples, que vai te ajudar na produtividade com JavaScript.

Ela consiste em fazer o assign de variáveis com base em objetos ou arrays, de forma simples, como se você estivesse, realmente, desconstruindo o objeto.

Digamos que eu queira criar duas variáveis com o valor originial do meu objeto. Eu posso fazer isso criando meu objeto, depois criando quantas variáveis eu quiser capturando o valor das propriedades do meu objeto:

```javascript
const original = { a: 'foo', b: 'bar' }

const a = original.a // => 'foo'
const b = original.b // => 'bar'
```

O que funciona de boa. Mas, imagina se eu tenho uma outra propriedade, `c`, que será adicionada. Vou ter mais uma linha de código que faz o mesmo trabalho, e assim sucessivamente para todo e qualquer item que eu queira capturar.

Ou eu posso declarar essas constantes usando destructuring, que é muito mais simples.

```javascript
const original = { a: 'foo', b: 'bar' }

const { a, b } = original
```

Dessa forma eu criei duas constantes, `a` e `b`, que recebem o valor das mesmas propriedades no objeto `orginial`, surtindo o mesmo efeito da linha anterior, mas, dessa vez, de forma resumida.

Eu também posso renomear as variáveis, basta dizer o novo nome de cada uma após os dois pontos.

```javascript
const axis = { x: 2, y: 3 }

const { x: xAxis, y: yAxis } = axis

console.log(x, y)
```

Existe uma outra técnica chamada deep destructuring, que permite a busca de propriedades aninhadas em árvores complexas de objetos.

```javascript
const tree = {
	very: {
		deep: {
			prop: 'foo'
		}
	}
}

const { very: { deep: { prop } } } = tree

console.log(prop)
```

No caso, `very` e `deep` não serão asignadas, elas servem apenas para o mapeamento.

Se tentar acessar elas, provavelmente vai receber um *ReferenceError*.

Outro ótimo caso de uso do destructuring é quando você vai receber um objeto gerérico como parâmetro de uma função, mas precisa apenas de algumas propriedades dele.

```javascript
const genericPersonObject = {
	name: 'Daniel',
	age: 20,
	contact: {
		mail: 'contato@danielbonifacio.com.br',
		phone: '27992699969'
	}
}

const fooFunction = ({ name, age, contact: { mail } }) => {
	console.log(name, age, mail)
}
```

Eu somente precisava das propriedades `name`, `age` e `contact.mail` do meu objeto, então desestruturei ele.

Caso as propriedades não sejam encontradas no objeto, o valor do parâmetro será `undefined`.

#### Destructuring in arrays

Destructuring não acontece somente com objetos, você também pode desestruturar objetos, levando em consideração que chaves de arrays são os índices.

Vamos dizer que você receba um array com 3 parâmetros diferentes, que é muito comum em criação de CLIs, por exemplo. Dentro do código, para não se perder, uma boa alternativa seria nomear eles em variáveis.

```javascript
const fooFunction = service => {
	const name = service[0]
	const url = service[1]
	const generateDefinitions = service[2]

	console.log(name, url, generateDefinitions)
}

fooFunction(['PetStore', 'https://petstore.swagger.io/', true])
```

Bom, você pode fazer isso de forma mais simples com destructuring.

```javascript
const fooFunction = service => {
	const [name, url, generateDefinitions] = service

	console.log(name, url, generateDefinitions)
}

fooFunction(['PetStore', 'https://petstore.swagger.io/', true])
```

Lembra do *Spread operator*? Então, você pode combinar ele com o destructuring, e receber o resto dos argumentos em um array.

```javascript
const fooFunction = service => {
	const [name, url, generateDefinitions, ...rest] = service

	console.log(name, url, generateDefinitions, rest)
}

fooFunction(['PetStore', 'https://petstore.swagger.io/', true, 'foo', 'bar', 'baz'])
```

Pronto, agora você já sabe destructuring. Esse era o último item da lista essencial de JavaScript antes dos frameworks.

Agora você está pronto para desbravar todos os frameworks e trabalhar com JavaScript em qualquer stack que sentir vontade.

Essa mini-série foi criada por um jovem apaixonado por tecnologia. Eu, Daniel Bonifacio.

Estou muito feliz que você tenha assistido a todos os vídeos, e mais feliz ainda em saber que você escolheu aprender JavaScript, que é a linguagem que eu amo.

Não se esqueça que os vídeos não param por aqui, ainda temos muito a desbravar, por isso, se inscreva no meu canal, dê um joinha 