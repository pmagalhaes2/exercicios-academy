##  Palíndromo
Escreva um método que determina se uma palavra ou frase é um palindromo, ou seja, a palavra pode ser lida de da esquerda para a direita ou ao contrário, ignorando pontuação, números e qualquer outro caracter que não seja uma letra. Considere também que não há diferenças entre letras maiúsculas e minúsculas. Resolva o problema usando apenas expressões regulares.

```text
Exemplo de utilização:
console.log(palindrome('ana')); => true  
console.log(palindrome('maam')); => true  
console.log(palindrome('abracadabra')); => false
console.log(palindrome("Madam, I'm Adam"));  => true
```


**Resolução 1:**
```javascript
function  palindrome(str) {
	str  =  str.toLowerCase();
	str  =  str.normalize("NFD").replace(/([\u0300-\u036f]|[^0-9a-zA-Z])/g, "");
	let  reversed  =  str.split("").reverse().join("");
	return  reversed  ===  str;
}
```
**Resolução 2:**
```javascript
function  palindrome(str) {
	str  =  str.normalize("NFD").replace(/([\u0300-\u036f]|[^0-9a-zA-Z])/g, "");
	str  =  str.toLowerCase().split("");
	let  reversed  =  str.slice().reverse();
	return  reversed.toString() ===  str.toString();
}
```