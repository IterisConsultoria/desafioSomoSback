# SomoS - Desafio Backend

Obrigado por participar do nosso desafio e pelo seu interesse em trabalhar conosco. Nós preparamos um desafio muito legal para você: Criar um jogo de comparação de cartas.

## Orientações

---

- Faça o desafio sozinho;
- Você poderá desenvolver seu backend utilizando qualquer linguagem/framework ou banco de dados;
- Faça sua aplicação utilizando o padrão REST. Escolha bem os métodos, endpoints e status codes de retorno;
- Crie um repositório **público** no GitHub;
- Inicie seu projeto, crie suas branches e faça seus commits regularmente;
- Você pode consultar qualquer site para auxiliá-lo no seu desenvolvimento;
- Na raiz do seu projeto, adicione um arquivo README detalhando como que buildamos e executamos o seu projeto. Você pode usar [este template](https://github.com/IterisConsultoria/desafioSomoSback/blob/main/README-exemplo.md) para criar o seu;
- Qualquer dúvida sobre o desafio crie uma issue neste projeto e iremos te responder o mais rápido possível;
- Escolha sua playlist favorita e bora codar! Estamos torcendo por você 🤞🤞🏻🤞🏼🤞🏽🤞🏾🤞🏿

Boa sorte!

## O desafio

---

Neste desafio, você fará um jogo de comparação de cartas, com tema livre, onde deverá ser possível enviar duas cartas para a aplicação fazer uma comparação de atributos e a carta com a maior quantidade de atributos fortes será a vencedora. Por exemplo:

Imagine as seguintes cartas de pokemons:

![image.png](https://i.imgur.com/X4QiG1j.png)

Ao realizar a comparação destas cartas conseguimos ver que:

- Os atributos `hp`, `defense`, `special-attack` e `special-defense` do Bulbasaur são mais fortes que os do Charmander
- Os atributos `attack` e `speed` do `Charmander` são mais fortes que os do Bulbasaur

Logo, o Bulbasaur possui a maior quantidade de atributos que são maiores que os do Charmander, então o Bulbasaur é o vencedor.

### O que queremos que você construa

---

#### Obrigatório

- Operações para cadastro, listagem, consulta e alteração de cartas
- Operações para comparação de cartas e resultado acumulado
- Banco de dados para armazenar as cartas e os resultados das comparações

#### Opcional

- Operação de exclusão de cartas
- Adicionar paginação e filtros na listagem de cartas
- Configurar a sua aplicação para rodar dentro de um container

### O que iremos avaliar

---

- O README
- Se a aplicação funciona
- Se contém todos os itens obrigatórios detalhados em [O que queremos que você construa](#o-que-queremos-que-voce-construa)
- A organização do seu código
- Seus commits, branches e etc
- A sua modelagem do banco de dados

### O que não iremos avaliar

---

- Testes unitários

### As Operações

---

#### Cadastro de cartas

Esta operação deverá realizar o cadastro de uma carta e retornar o identificador dela na resposta.

##### Requisição

**Método**: À sua escolha

**Endpoint**: À sua escolha

**Body**: A entrada deverá ser algo parecido com este Json, com o nome da carta e seus atributos, fique à vontade para alterar caso ache necessário:

``` json
{
  "name": "bulbasaur",
  "attributes": {
    "hp": 45,
    "attack": 49,
    "defense": 49,
    "special-attack": 65,
    "special-defense": 65,
    "speed": 45
  }
}
```

##### Resposta

Na resposta é importante devolver o identificador da carta cadastrada, fique à vontade para escolher onde retornar esta informação.

**Status Code**: À sua escolha

**Body**: À sua escolha

#### Listagem de cartas

Esta operação deverá listar todas as cartas cadastradas na aplicação.

##### Requisição

**Método**: À sua escolha

**Endpoint**: À sua escolha

**Body**: À sua escolha

##### Resposta

Devolver uma listagem das cartas.

**Status Code**: À sua escolha

**Body**: O retorno deverá ser um array com as cartas cadastradas:

``` json
[
  {
    "name": "bulbasaur",
    "attributes": {
      "hp": 45,
      "attack": 49,
      "defense": 49,
      "special-attack": 65,
      "special-defense": 65,
      "speed": 45
    }
  }
]
```

#### Consulta de cartas

Esta operação deverá retornar uma carta específica baseada em seu identificador.

##### Requisição

**Método**: À sua escolha

**Endpoint**: À sua escolha

**Body**: À sua escolha

##### Resposta

Devolver uma listagem das cartas.

**Status Code**: À sua escolha

**Body**: O retorno deverá ser a carta solicitada:

``` json
{
  "id": 1,
  "name": "bulbasaur",
  "attributes": {
    "hp": 45,
    "attack": 49,
    "defense": 49,
    "special-attack": 65,
    "special-defense": 65,
    "speed": 45
  }
}
```

#### Comparação de cartas

Esta operação deverá fazer a comparação seguindo a explicação dada anteriormente e após cada comparação, registre em banco de dados os resultados.

##### Requisição

**Método**: À sua escolha

**Endpoint**: À sua escolha

**Body**: A entrada deverá ser algo parecido com este Json, com o identificador das duas cartas, fique à vontade para alterar caso ache necessário:

``` json
{
  "playerOneCard": 1,
  "playerTwoCard": 2
}
```

##### Resposta

**Status Code**: À sua escolha

**Body**: O retorno deverá ser o resultado da comparação e os detalhes sobre o vencedor em cada um dos atributos:

``` json
{
  "winner": 1,
  "loser": 2,
  "details": {
    "hp": 1,
    "attack": 2,
    "defense": 1,
    "special-attack": 1,
    "special-defense": 1,
    "speed": 2
  }
}
```

> OBS.: Em caso de empate você deverá retornar um Status Code diferente, a comparação não deverá ser registrada no banco de dados o corpo da resposta pode ser vazio.

#### Resultado acumulado

Esta operação deverá fornecer um resultado acumulado de todas as comparações feitas dentro da aplicação, informando o somatório de vitórias dos dois jogadores. Neste caso, não há a necessidade de envio de dados na requisição, sendo importante termos apenas a resposta.

##### Requisição

**Método**: À sua escolha

**Endpoint**: À sua escolha

**Body**: Não é necessário

##### Resposta

**Status Code**: À sua escolha

**Body**: O retorno deverá ser o resultado acumulado de vitórias dos jogadores:

``` json
{
  "playerOne": 123,
  "playerTwo": 23
}
```

### O Banco de Dados

---

Você poderá escolher qualquer banco de dados (SQL ou NoSQL). Faça a modelagem do seu banco para atender às especificações detalhadas no desafio, crie um desenho como achar melhor para detalhar a estrutura/organização do seu banco de dados e deixe este arquivo na raiz do seu projeto. 

## A Entrevista

---

Para a entrevista, certifique-se de que a sua aplicação estará funcionando na sua máquina para que você a apresente para nós.

## Links úteis

---

- [Conventional Commits](https://www.conventionalcommits.org/pt-br/v1.0.0/)
- [REST: Princípios e boas práticas](https://www.alura.com.br/artigos/rest-principios-e-boas-praticas)
