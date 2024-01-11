# Componentes HTML

Compondo uma página HTML com JavaScript a partir de vários arquivos HTML e trechos de código utilizados como componentes.

## Usando Fetch API

Como fetch é assíncrono, ele não garante que os elementos sejam carregados na página na ordem em que os arquivos são chamados. Por isso o fetch deve ser encadeado como no exemplo abaixo:

```js
fetch('header.html')
    .then(resposta => resposta.text())
    .then(codigo => {
        document.querySelector('body').insertAdjacentHTML('beforeend', codigo);
        return fetch('main.html');
    })
    .then(resposta => resposta.text())
    .then(codigo => {
        document.querySelector('body').insertAdjacentHTML('beforeend', codigo);
        return fetch('footer.html');
    })
    .then(resposta => resposta.text())
    .then(codigo => {
        document.querySelector('body').insertAdjacentHTML('beforeend', codigo);
    })
    .catch(erro => console.error('Erro ao carregar o conteúdo:', erro));
```
