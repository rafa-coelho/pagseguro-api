<h1 align="center">Pagseguro Api</h1>

<p align="center">
  <img alt="Github top language" src="https://img.shields.io/github/languages/top/rafa-coelho/pagseguro-api?color=56BEB8">

  <img alt="Github language count" src="https://img.shields.io/github/languages/count/rafa-coelho/pagseguro-api?color=56BEB8">

  <img alt="Repository size" src="https://img.shields.io/github/repo-size/rafa-coelho/pagseguro-api?color=56BEB8">


</p>

<!-- Status -->

<!-- <h4 align="center"> 
	🚧  Pagseguro Api 🚀 Under construction...  🚧
</h4> 

<hr> -->

<p align="center">
  <a href="#rocket-tecnologias">Tecnologias</a> &#xa0; | &#xa0;
  <a href="#white_check_mark-requisitos">Requisitos</a> &#xa0; | &#xa0;
  <a href="#checkered_flag-começando">Começando</a> &#xa0; | &#xa0;
  <a href="#sparkles-criando-cobrança">Criando Cobrança</a> &#xa0; | &#xa0;
  <a href="https://github.com/rafa-coelho" target="_blank">Autor</a>
</p>

<br>

## :rocket: Tecnologias ##

Ferramentas usadas nesse projeto:

- [Axios](https://github.com/axios/axios)
- [Node.js](https://nodejs.org/en/)


## :white_check_mark: Requisitos ##

Antes de começar :checkered_flag:, você vai precisar do [Node](https://nodejs.org/en/) instalado.


## :checkered_flag: Começando ##

```bash
$ npm i pagseguro-api
```

É preciso criar uma variável de ambiente com a token do PagSeguro como abaixo:

```
PS_TOKEN={{SUA_TOKEN_PAG_SEGURO}}
```

Para testar no ambiente de SandBox, a classe deve ser instanciada com um `true` no construtor:

```javascript
const PagSeguro = require('pagseguro-api');

const pag = await PagSeguro(true);
```

## :sparkles: Criando Cobrança ##

Gerando uma cobrança de boleto

```javascript
const PagSeguro = require('pagseguro-api');

const pag = await PagSeguro();
pag.referencia = "BRL0123"; // Idenficador da cobrança
pag.Descricao("Cobrança por Boleto");
pag.Boleto({ // Informações do Pagador
  nome: "",
  cpf: "", 
  email: "", 
  endereco: {
    rua: "",
    rua : "",
    numero : "",
    bairro : "",
    cidade : "",
    estado : "",
    uf : "",
    cep : "",
    pais : "BR"
  }
});

// O valor fornecido deve ser em centavos.
const cobranca = await pag.Cobrar(10000); 
```

Gerando uma cobrança de Cartão de créditos

```javascript
const PagSeguro = require('pagseguro-api');

const pag = await PagSeguro();
pag.referencia = "BRL0123"; // Idenficador da cobrança
pag.Descricao("Cobrança por Cartão");
pag.Parcelas(1);
pag.Cartão({
  numero: "",
  mes: "",
  ano: "",
  cvv: "",
  nome: ""
});

// O valor fornecido deve ser em centavos.
const cobranca = await pag.Cobrar(10000); 

```

Extornando um pagamento:

```javascript
const PagSeguro = require('pagseguro-api');

const pag = await PagSeguro();
const extorno = await pag.Extorno({{CODIGO_TRANSACAO_PS}}, {{VALOR_CENTAVOS}});
```


Made with :heart: by <a href="https://github.com/rafa-coelho" target="_blank">Rafael Coelho</a>

&#xa0;

<a href="#top">Back to top</a>
