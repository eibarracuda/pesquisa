---
{"dg-publish":true,"permalink":"/04-cadernos/2023-01-30-logica-da-programacao/","tags":["🧠️/📝️/🌿️"],"created":"2023-05-15 21:39","updated":"2023-05-15 21:45"}
---

***
| Relacionados |
| ------------ |

{ .block-language-dataview}
***
>[!NOTE] Fazer esse programa 
> quanta agua vc tomou hoje 

# = 2023-01-30 - 📝️ Lógica da programação

## Ferramentas
![sublime|50](https://avatars3.githubusercontent.com/u/684879?s=400&amp;v=4)

## Cursos
![logoaula|50](https://www.alura.com.br/assets/api/cursos/logica-programacao-javascript-html.svg)

## Até agora, fiz isso usando o que aprendi
- 

## Sobre editores de texto e navegadores
Introdução sobre quais softwares usar e como obter paridade visual com o instrutor. São recomendados o [Sublime](https://www.sublimetext.com/3) ou  [Notepad++](https://notepad-plus-plus.org) como editores e o navegador [Chrome](https://www.google.com.br/chrome/browser/desktop/) devido ao debugger.

> [!warning] Comandos no Chrome
> `CTRL+O` para abrir o arquivo HTML
> `F12` para abrir a janela das ferramentas de desenvolvedor (DevTools)

## Tipos de valores
```javascript
var nome = "Regina"; // texto, ou tecnicamente falando, uma string
var idade = 22; // número
var temCarteira = true; // booleano
var coisas = ["Gisele", 12, true]; // string
```

## Aula 01

> [!info]  Nova *Tag*
```html
<meta charset="UTF-8">
```

- Boa prática de programação.
- Usada para declarar o *encoding* da página no navegador, em alguns navegadores esse processo é detectado automaticamente.


> [!warning] Boas práticas ao nomear arquivos
> `nomear_assim.html`
> Letras minúsculas separadas por `_`, uso do `.html` na hora de salvar no editor de texto.
> 

> [!info]  Nova *Tag*
```html
<br>
```

 Pula linha. Essa tag não precisa ser fechada. Abreviação de *break*.

> [!info]  Nova *Tag*
```html
<h1> Meu primeiro teste! </h1>
```

Titulos, de `h1` a `h6`, vários tamanhos.

 > [!info]  Nova *Tag*
```html
<a href="http://www.alura.com.br">aqui</a>
```

Links


 > [!info]  Novo

```html&Javascript
<script> // Declara bloco de codigo javascript
alert("Isso sim é um programa"); // "" é parametro tipo texto ou string
</script>
```

```javascript
alert("Isso sim é um programa");
```

`script` declara o bloco de código javascript

`string` ➜ parâmetro tipo texto


### O depurador

O depurador (debugger) do Chrome aponta erros no código.
Bom para aprender também

```javascript
Uncaught SyntaxError: Unexpected string
```
## Aula 02
> [!info]  Novo
```javascript
document.write("sua string");
```

é possível a concatenação e operações
```javascript
document.write("A soma das idades é" + (20 + 10 + 30));
document.write("A soma das idades é" + (20 + 10 + 30)/3);
document.write("sua string" + var + 5);
document.write("Flávio nasceu em " + (2016 - 39) + "<br>");
```

```javascript
<script>

    document.write("A idade do Flávio é ");
    document.write(18 * 20);
    document.write((20 + 10 + 30)/3);

</script>
```

### Estrutura JavaScript
![infográfico alert](https://s3.amazonaws.com/caelum-online-public/alert.png)
## Aula 03

### Variaveis

``` javascript
var ano;
```

```html
<script>

    var ano = 2023;

    document.write("Nemona tem " + (ano - 1977) + " anos");

</script>
```

Retorna como

> Nemora tem 46 anos

```javascript
var media = (39 + 20 + 41)/3;

document.write('A média das idades é ' + media);
```

>[!info] Novo
```javascript
Math.round()
```

Para arredondar o resultado

```javascript
var media = (39 + 20 + 41)/3;

document.write('A média das idades é ' + Math.round(media));
```

```javascript
var idadeFlavio = 39;
var idadeJoaquim = 20;
var idadeBarney = 41;
var media = (idadeFlavio + idadeJoaquim + idadeBarney)/3;

document.write('A média das idades é ' + Math.round(media));
```

```html
    <meta charset="UTF-8">
    
    <h3>Álcool ou Gasolina?</h3>
    
    <script>
    
    var tanque = 40;
    
    var caminhoComGasolina = 480;
    var consumoDeGasolina = caminhoComGasolina/tanque;
    
    var caminhoComAlcool = 300;
    var consumoDeAlcool = caminhoComAlcool/tanque;
    
    document.write("O consumo de Gasolina é " + consumoDeGasolina + " km/L");
    
    document.write("<br>");
    
    document.write("O consumo de Álcool é " + consumoDeAlcool + " km/L");
    
    </script>
    ```

## Aula 04

### Funções
```javascript
function pulaLinha() {

        document.write("<br>");

} // criar funções

pulaLinha(); // executar a função

```

#### Exemplo
```html
<meta charset="UTF-8">

<script>

    function pulaLinha() {
        document.write("<br>");
        document.write("<br>");
	} // Declarar a função; usar nomes descritivos

var ano = 2023; // Declara variavel

document.write("Nemona tem " + (ano - 1970) + " anos"); // Escreve essa concatenação de arrays, variavel e numero

pulaLinha(); // Executa a função

document.write("Arven tem " + (ano - 1996) + " anos");

pulaLinha();

ano = 2022; // Altera o valor da variavel

document.write("Penny tem " + (ano - 1976) + " anos"); // É o unico afetado pela alteração do valor da variavel

</script>
```


### Funções com parametros

```javascript
function mostra(frase) {

    document.write(frase);

} // A função recebe o parametro entre ( )

mostra("Olá pessoal!"); // Usar a função
```

```javascript
function mostra(frase) {

    document.write(frase);
    pulaLinha(); // Podemos usar funções dentro de outras funções desde que declaradas antes no código
}
```

#### Exemplo

```html
<meta charset="UTF-8">
<script>
    function fazPegadinha() {
        alert("Olá");
        alert("amiga!");
        alert("Tá");
        alert("bastante");
        alert("entediada?");
        alert("Em ficar");
        alert("Clicando em");
        alert("Ok");
        alert("né?");
    } // Essa function dá varios alerts estáticos

    fazPegadinha(); // Executa

</script>
```

```javascript
<meta charset="UTF-8">
<script>
    function exibeAlerta(mensagem) {
        alert("***" + mensagem + "***"); // Conteudo do exibeAlerta concatenado com array
    } 

    var idade1 = 10;
    var idade2 = 20;
    var idade3 = 30;
    var totalIdades = idade1 + idade2 + idade3;
    var mediaIdades = totalIdades/3;

    exibeAlerta("Total de idades é " + totalIdades); // Função concatenada com variavel
    exibeAlerta("A média das idades é " +  mediaIdades);
</script>
```

```javascript
<meta charset="UTF-8">
<script>

    function pulaLinha() {
        document.write("<br>");
    }

    function exibeTitulo(titulo) { // Nomes autoexplicativos
        document.write("<h1>" + titulo + "</h1>"); // Arrays com tag html
        pulaLinha();
    }

    function exibeParagrafo(paragrafo) {
        document.write("<p>" + paragrafo + "</p>");
        pulaLinha();
    }

    // pede para alguém ler daqui em diante e veja se ele entende o que esta sendo feito
    exibeTitulo("Bem-vindos");
    exibeParagrafo("Este é um simples programa");
</script>
```


```javascript
<meta charset="UTF-8">
<script>

function pulaLinha() {
    // pulando duas linhas
    document.write("<br><hr><br>"); // hr faz um traço
}

function mostra(frase) {
    document.write("<big>" + frase + "</big>"); // tags html no array
    pulaLinha();
}
</script>
```


## Aula 05
### Retorno de funções
```javascript
function calculaImc(altura, peso) {

    var imc = peso / (altura * altura); // Primeiro a função apenas calcura
    return imc; // Aqui retorna o calculo quanfo for chamada

}

var imcFlavio = calculaImc(1.71, 73); // Aqui declara uma variavel para calcular usando a função
var imcAmigo = calculaImc(1.72, 68);

mostra(imcFlavio); // Aqui mostra a variavel, que depende do return
mostra(imcAmigo);
```

```javascript
function calculaImc(altura, peso) { // Nomeia duas entradas de valores

    return peso / (altura * altura); // Pode retornar calculos com esses nomes
}

var imcFlavio = calculaImc(1.71, 73);
var imcAmigo = calculaImc(1.72, 68);

mostra(imcFlavio);
mostra(imcAmigo);
```

#### Exemplos

```javascript
function funcaoQualquer() {

    var n1 = 10;
    var n2 = 20;
    var n3 = 30;

    return n2; // Quando chamar esta função vai devolver "20"
}
```


### Interação com usuário
```javascript
var nome = prompt("Informe o seu nome"); // Variavel recebe o conteudo digitado pelo usuario no prompt
var alturaInformada = prompt(nome + ", informe sua altura");
var pesoInformado = prompt(nome + ", informe seu peso");

var imc = calculaImc(alturaInformada, pesoInformado); // Calculos com as variaveis contendo infos do usuário

document.write(nome + ", o seu IMC calculado é " + imc);
```
## Aula 06

### parseInt()
>[!info] Novo
> `parseInt(string a ser salva como numero)`

```javascript
var vitorias = parseInt(prompt("Entre com o número de vitórias."));

var empates = parseInt(prompt("Entre com o número de empates.")); // Recebe do prompt numero

var pontos = vitorias  * 3 + empates; // Calcula corretamente pois numeros

mostra("Os pontos do seu time são " + pontos);
```

#### Exemplos

```html
<meta charset="UTF-8">

<script>
    function pulaLinha() {
        document.write("<br>");
    }

    function mostra(frase) {
        document.write(frase);
        pulaLinha();
    }

    var convidados = parseInt(prompt("Número de convidados"));
    var vips = parseInt(prompt("Número de convidados VIP's"));

    var total = convidados + vips;

    mostra("O total de convidados é " + total);

</script>
```
### Condições
>[!info] Novo
> `if (true/false){}`
> `else{}`
> `Math.random()` ➜ retorna números decimais, multiplicar por 10
> `Math.round()` ➜ arredonda o número

>[!warning] 
> = para atribuição
> == para igualdade
> != para diferença

```javascript
if(pontos > 28)
    mostra("Seu time está melhor do que no ano passado.");

if(pontos < 28)
    mostra("Seu time está pior do que no ano passado.");

if(pontos == 28) // == notação para igual != notação para diferente
    mostra("Seu time está igual igual ao ano passado.");
```

#### Exemplos

```html
<meta charset="UTF-8">

<script>

    function pulaLinha() {

        document.write("<br>");
        document.write("<br>");
}

    function mostra(frase) {

        document.write(frase);
        pulaLinha();
}

var numeroPensado = Math.round(Math.random() * 10); // Pensa um nuimero inteiro e aleatorio
var chute = parseInt(prompt("digite seu chute!")); // Usuario entra com um numero

if(chute == numeroPensado) { // teste logico para responder o usuario
    mostra("Você acertou!");

} else {
    mostra("Você errou, o número pensado foi " + numeroPensado);
}

</script>
```
## Aula 07
>[!info] Novo
>`while(true/false){}`
>`for(variavel; condição; incremento da variavel){}`
>`break` para parar o loop
>`parseFloat` lê numeros decimais de um array

>[!warning] Nova notação
> `&&` para booleano AND

>[!warning] Nova notação
> Para incrementar de um em um `total = total + 1;` podemos escrever `total++;`
### Loops
#### While(){
```javascript
var anoCopa = 1930;

while(anoCopa <= 2016) { // Enquanto X faça Y

    alert("Teve copa em " + anoCopa); // Isso vai fazer 1 popup a cada ano q teve copa
    anoCopa = anoCopa + 4; // Altera o valor da variavel para dar fim ao loop

}

alert("FIM");
```

##### Exemplos
```javascript
var limite = parseInt(prompt("Entre com a data limite"));

var anoCopa = 1930;

while(anoCopa <= limite) { // loop que depende do usuario

    mostra("Teve copa em " + anoCopa);
    anoCopa = anoCopa + 4;
}

mostra("FIM");
```

```javascript
<meta charset="UTF-8">
<script>

    var loginCadastrado = "alura";
    var senhaCadastrada = "alura321";

    var loginInformado = prompt("Informe seu login");
    var senhaInformada = prompt("Informe sua senha");

    if( loginCadastrado == loginInformado && senhaCadastrada == senhaInformada ) {

        alert("Bem-vindo ao sistema " + loginInformado);
    } else {

        alert("Login inválido. Tente novamente");
    }
</script>
```

```javascript
<meta charset="UTF-8">

<script>

    var loginCadastrado = "alura";
    var senhaCadastrada = "alura321";

    var maximoTentativas = 3;
    var tentativaAtual = 1;

    while(tentativaAtual <= maximoTentativas) {

        var loginInformado = prompt("Informe seu login");
        var senhaInformada = prompt("Informe sua senha");

        if( loginCadastrado == loginInformado && senhaCadastrada == senhaInformada ) {

            alert("Bem-vindo ao sistema, " + loginInformado);

            tentativaAtual = maximoTentativas; // acertou, então faço o gasto de todas as tentativas para sair do loop. Lá embaixo vai incrementar + 1! 

        } else {

            if (tentativaAtual == 3) {
                alert("Número permitido de tentativas ultrapassado!");
            } else {
                alert("Login inválido. Tente novamente");
            }
        }

       // vai para a próxima tentativa
        tentativaAtual = tentativaAtual +1  
    }

</script>
```
#### For(){
```html
<meta charset="UTF-8">

<script>

    function pulaLinha() {

        document.write("<br>");
        document.write("<br>");
}

    function mostra(frase) {

        document.write(frase);
        pulaLinha();
}

for(var multiplicador = 1; multiplicador <= 10; multiplicador = multiplicador + 1) {

    mostra(7 * multiplicador);

}

mostra("FIM");

</script>
```

##### A mesma funcionalidade porem usando while

```javascript
var multiplicador = 1;

while(multiplicador <= 10) {

    mostra(7 * multiplicador);
    multiplicador = multiplicador + 1;
}
```


#### Exemplos
```javascript
for( var i = 0; i < 10; i++ ) {
    alert( "O resultado é " + (2 * i) );
}
```

Converta-o para usar a instrução while. Lembre-se: o resultado do programa tem que ser o mesmo!

```html
<script>
var i = 0;
while( i < 10) {
    alert( "O resultado é " + (2 * i) );
    i++;    
}
</script>
```

### Acumular resultado

```javascript
<script>

function pulaLinha() {

    document.write("<br>");
    document.write("<br>");

}

function mostra(frase) {

    document.write(frase);
    pulaLinha();

}

var totalFamiliares = parseInt(prompt("Quantidade de familiares?"));

var numero = 1;
var totalIdades = 0;
while(numero <= totalFamiliares) { //Pede a idade pelo numero de vezes que o sujeito disse ter familiares
    var idade = parseInt(prompt("Informe idade do familiar")); // salva em idade
    totalIdades = totalIdades + idade; // soma a idade desse loop numa variavel e aguarda o proximo loop
    numero++; //incrementa uma passada de loop

}
var mediaDasIdades = totalIdades/totalFamiliares //usa a variavel somada depois do loop
mostra("A média das idades dos familiares é " + mediaDasIdades);
mostra("FIM");
</script>
```
### Break
```html
<meta charset="UTF-8">

<script>

    function pulaLinha() {

        document.write("<br>");
        document.write("<br>");
}

    function mostra(frase) {

        document.write(frase);
        pulaLinha();
}

var numeroPensado = Math.round(Math.random() * 10);

var tentativas = 1;

while(tentativas <= 3) {

    var chute = parseInt(prompt("Digite seu chute!"));

    if(chute == numeroPensado) {

        mostra("Você ACERTOU, o número pensado era " + numeroPensado);
        break; // Interrompe ao acertar

    } else {

        mostra("Você ERROU!");
    }

    tentativas++;
}

mostra("FIM");
</script>
```


### Aninhar repetições

```html
<script>

    function pulaLinha() {

        document.write("<br>");
    }

    function mostra(frase){

        document.write(frase);
        pulaLinha();
    }

    for(var linha = 1; linha <= 3; linha++) { // repete as linha

        for(var coluna = 1; coluna <= 10; coluna++) { // repete em linha
            document.write("*"); 
        }
        pulaLinha();
    }

</script>
```
## Aula 08 - 
>[!info] Novo Javascript
>`document.querySelector("nome")` ➜ interação com o html
>> `nome.value` = > < ➜  comparação, chama o valor
>> `nome.onclick` ➜ quando clicar naquele trem faz X, com para executar funções
>> `nome.focus()` ➜ chama o foco na pagina

>[!info] Novo HTML
>`<input/>` ➜ caixa de texto
>`<button> Texto dentro do botão </button> `

```html
<meta charset="UTF-8">

<input/>
<button>Compare com o meu segredo</button>

<script>
    var segredo = 5;

    var input = document.querySelector("input"); // Busca a tag html e salva

    function verifica() {

        if(input.value == segredo) { // Comparação do valor do input com o segredo

        alert("Você ACERTOU!");
        } else {

        alert("Você ERROU!!!!!!!!");
        }

    }

    var button = document.querySelector("button"); // Declaramos outra tag html

    button.onclick = verifica; //On click

</script>
```

```html
<meta charset="UTF-8">

<input/>
<button>Exibir texto digitado</button>

<script>
    var input = document.querySelector("input");

    function exibeTexto() {

        alert(input.value);
    }

    var button = document.querySelector("button");
    button.onclick = exibeTexto;
</script>
```

```html
<meta charset="UTF-8">

<input/>
<button>Compare com o meu segredo</button>

<script>
    var segredo = 5;

    var input = document.querySelector("input");

    function verifica() {

        if(input.value == segredo) {

        alert("Você ACERTOU!");
        } else {

        alert("Você ERROU!!!!!!!!");
        }

                input.value = "";
                input.focus();

    }

    var button = document.querySelector("button");

    button.onclick = verifica;

</script>
```

## Aula 09
>[!info] Novo Javacript
> `var codigos  = ["IDNOCLIP" , "IDDQD", "IDKFA"];`
> `codigos.length` ➜ 3, conta quantos valores
> codigos.push ➜ insere valor no array codigos
> console.log() ➜ imprime no debugger

### Arrays
```javascript
var segredos = [5,7,10,2]

```

```javascript
var segredos = [5,7,10,2]
undefined
segredos
[5,7,10,2]
segredos[1]
7
segredos[0]
5
segredos[1]
7
segredos[3]
2
segredos[4]
undefined
```

```javascript
var frutas = ["abacaxi", "banana", "melão"];
frutas.push("abacate");
```

```html
<meta charset="UTF-8">

<input/>
<button>Compare com o meu segredo</button>

<script>

    var segredos = [5,7,10,2,3];

    var input = document.querySelector("input");
        input.focus();

    function verifica() {

    var achou = false;

    for(var posicao = 0; posicao < segredos.length; posicao++) {

        if(input.value == segredos[posicao]) {

            alert("Você ACERTOU!");
            achou = true;
            break;
        }
    }

    if(achou == false) {
        alert("Você ERROU!");
    }

    input.value = "";
    input.focus();

    }

    var button = document.querySelector("button");

    button.onclick = verifica;

</script>
```

```html
<meta charset="UTF-8">
<script>
var parcelas = [10.40, 40.00, 100.18, 200];
for(var i = 0; i < parcelas.length; i = i + 1) {
    document.write(parcelas[i]);
    document.write("<br>");
}

document.write("FIM");
</script>
```

```html
<meta charset="UTF-8">
<script>
var jogadores = ["Saladino", "Cage", "Xur", "Rayson"];

for( var i = 0; i < jogadores.length; i++) {

    alert(jogadores[i]);
}

</script>
```

```html
<meta charset="UTF-8">

<input/> // Onde usuário entra o chute
<button>Compare com o meu segredo</button> // Botão de verificação

<script>
    function sorteia() { // Função para sortear numeros

       return Math.round(Math.random() * 10); 

    }

    function sorteiaNumeros(quantidade) { // função para gerar a quantidade certa de numeros

        var segredos = [];

        var numero = 1;

        while(numero <= quantidade) { // Enquanto numero <= quantidade

              segredos.push(sorteia()); // Salvar em segredos o numero sorteado
              numero++; // Incrementa 1 numero

        }

        return segredos; // Devolve os segredos

    }

    var segredos = sorteiaNumeros(3); // Quantidade de numeros

    console.log(segredos); // Imprime esses numeros no console para conferir (dev)

    var input = document.querySelector("input");
    input.focus(); // Declara e foca no input de texto para experiencia do usuário

    function verifica() {

       var achou = false;

       for(var posicao = 0; posicao < segredos.length; posicao++) { // Confere no array

              if(input.value == segredos[posicao]) {

                     alert("Você ACERTOU!");
                     achou = true;
                     break;
              } 
       }

       if(achou == false) {

              alert("Você ERROU!");
       }

       input.value = ""; // Deleta o conteudo
       input.focus(); // Foca

    }

    var button = document.querySelector("button");

    button.onclick = verifica; // Onclick executa a função verifica

</script>
```

```html
<meta charset="UTF-8">

<input/>
<button>Compare com o meu segredo</button>

<script>
    function sorteia() {

       return Math.round(Math.random() * 10);

    }

    function sorteiaNumeros(quantidade) {

        var segredos = [];

        var numero = 1;

        while(numero <= quantidade) {

              var numeroAleatorio = sorteia();
              var achou = false;

              if (numeroAleatorio !== 0) { // Se o numero for zero  
                     for(var posicao = 0; posicao < segredos.length; posicao++) {

                           if(segredos[posicao] == numeroAleatorio){ // compara e vê se no array ja tem um numero igual
                                achou = true;
                                break;
                           }

                     }

                     if (achou == false) {
                           segredos.push(numeroAleatorio); // senão salva
                           numero++;
                     }
              }

        }

        return segredos;

    }

    var segredos = sorteiaNumeros(3);

    console.log(segredos);

    var input = document.querySelector("input");
    input.focus();

    function verifica() {

       var achou = false;

       for(var posicao = 0; posicao < segredos.length; posicao++) {

              if(input.value == segredos[posicao]) {

                     alert("Você ACERTOU!");
                     achou = true;
                     break;
              } 
       }

       if(achou == false) {

              alert("Você ERROU!");
       }

       input.value = "";
       input.focus();

    }

    var button = document.querySelector("button");

    button.onclick = verifica;

</script>
```