##  Contar palavras
Dado uma String como entrada, retorne um Dicionário/Objeto no qual as chaves são as palavras da string e os valores são o número de vezes que cada palavra aparece. Não use loops do tipo 'for/while'. Novamente, apenas letras devem ser consideradas como palavras, sem diferença entre maiúsculas e minúsculas. 

```text
Exemplo de utilização:
console.log(countWords('Doo bee doo bee doo')) => { doo: 3, bee: 2 }
```

**Resolução 1:**
```javascript
function  countWords(str) {
	str  =  str.toLowerCase();
	const  array_elements  =  str.split("  ");
	let  dict  = {};
	array_elements.forEach((el) => {
		if (el  in  dict) {
			dict[el]++;
		} else {
			dict[el] =  1;
		}
		return  dict;
	});
}
```

**Resolução 2:**
```javascript
function  countWords(str) {
	str  =  str.toLowerCase();
	const  array_elements  =  str.split("  ");
	array_elements.reduce((dict, el) => {
		if (el  in  dict) {
			dict[el]++;
		} else {
			dict[el] =  1;
		}
		return  dict;
	}, {});
}
```