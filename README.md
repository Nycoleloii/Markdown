# **Documentação do Código: Fatorial e Número Primo**  

> # **Explicação do Código: Interface da Calculadora**  

Essa parte do código define a **interface HTML** de uma calculadora que recebe um número do usuário, calcula seu **fatorial** e verifica se é **primo**. O **h2** exibe um título descritivo, enquanto o **label** e o **input type="number"** permitem que o usuário insira um valor numérico. O **button** aciona a função calcular(), que processará os cálculos. O **div id="resultado"** serve como um **espaço reservado** onde os resultados serão exibidos dinamicamente após a execução da função. Essa estrutura garante **interatividade e usabilidade** na aplicação.  

``` html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Fatorial e Número Primo</title>
</head>
<body>
    <h2>Calculadora de Fatorial e Verificador de Número Primo</h2>
    <label for="numero">Digite um número:</label>
    <input type="number" id="numero">
    <button onclick="calcular()">Calcular</button>
    <div id="resultado"></div>
```
> # **Explicação do Código: Função Fatorial**  

A função calcularFatorial(n) utiliza **recursão** para calcular o fatorial de um número inteiro não negativo. Primeiro, verifica se a entrada é válida, garantindo que seja um número inteiro (Number.isInteger(n)) e não negativo (n >= 0), lançando um erro caso contrário. O **caso base** ocorre quando n é 0 ou 1, retornando 1. Para valores maiores, a função se chama recursivamente (n * calcularFatorial(n - 1)), reduzindo n até atingir o caso base. Isso assegura **correção, eficiência e segurança**, prevenindo erros como chamadas infinitas ou entradas inválidas.

``` javascript
function calcularFatorial(n) {
    if (typeof n !== "number" || !Number.isInteger(n) || n < 0) {
        throw new Error("Entrada inválida! O número deve ser um inteiro não negativo.");
    }

    if (n === 0 || n === 1) {
        return 1;
    } else {
        return n * calcularFatorial(n - 1);
    }
}

```
> # **Explicação do Código: Verificação de Número Primo**  

A função verificarNumeroPrimo(numero) determina se um número é **primo**. Primeiro, verifica se numero é um **inteiro positivo maior que 1**, pois números menores ou negativos não são primos. Em seguida, utiliza um **loop** para testar divisibilidade, mas em vez de percorrer todos os números até numero - 1, otimiza verificando **até a raiz quadrada de numero** (Math.sqrt(numero)), pois qualquer divisor maior já teria um par menor. Se encontrar um divisor (numero % i === 0), retorna false, caso contrário, retorna true, indicando que o número é primo. Essa abordagem reduz significativamente o número de operações, tornando o código **mais eficiente**.

``` javascript
function verificarNumeroPrimo(numero) {
    if (typeof numero !== "number" || !Number.isInteger(numero) || numero <= 1) {
        return false; 
    }

    for (let i = 2; i <= Math.sqrt(numero); i++) {
        if (numero % i === 0) {
            return false; 
        }
    }
    return true; 
}

```
> # **Explicação do Código: Cálculo de Fatorial e Verificação de Número Primo**  

O código implementa uma página HTML interativa que recebe um número do usuário, calcula seu **fatorial** e verifica se é **primo**. A função calcularFatorial(n) usa **recursão** para calcular o fatorial, enquanto verificarNumeroPrimo(numero) otimiza a verificação testando divisores apenas até a **raiz quadrada do número**. A função calcular() captura o valor inserido, valida a entrada (isNaN(numero) evita erros), e exibe os resultados na página. Melhorias incluem **tratamento de erros** e **uso de template literals** (\`\`) para maior clareza e eficiência na exibição do resultado. 

``` javascript

        function calcular() {
            let numero = parseInt(document.getElementById("numero").value);
            if (isNaN(numero)) {
                document.getElementById("resultado").innerHTML = "Por favor, insira um número válido.";
                return;
            }
            let fatorial = calcularFatorial(numero);
            let primo = verificarNumeroPrimo(numero);
            document.getElementById("resultado").innerHTML =
                `O fatorial de ${numero} é ${fatorial} <br> O número ${numero} ${primo ? "é primo." : "não é primo."}`;
        }
    </script>
</body>
</html>
```

# Respostas 
1. O código ficou mais organizado, legível e compreensível, facilitando a manutenção e depuração.  

2. A rastreabilidade permite identificar rapidamente a origem e a evolução do código, facilitando correções e melhorias.  

3. Uso de **comentários claros**, **nomes de variáveis e funções descritivos**, **estrutura bem organizada** e **documentação detalhada**.  

4. O **Markdown** facilita a formatação da documentação, tornando-a mais **legível** e **acessível** em diversas plataformas.  

5. A **padronização** reduz erros, melhora a **colaboração** entre equipes e torna o código mais **escalável** e **fácil de modificar** no futuro.  
