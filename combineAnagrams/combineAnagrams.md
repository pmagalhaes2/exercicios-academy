## Anagramas

Um anagrama é uma palavra obtida por meio do rearranjo das letras de outras palavras. Por exemplo, "rats", "tars" e "star" são um grupo de anagramas pois são compostos pelas mesmas letras.

Dado um Array de Strings, escreva um método que agrupa as Strings em grupos de anagramas e retorna esses grupos. Letras maiúsculas e minúsculas podem ser tratadas como se fossem iguais, mas o retorno deve manter as letras maiúsculas e minúsculas. A ordem dos grupos ou das Strings não importa.

  

```text

Exemplo de utilização:

console.log(combineAnagrams(words));=>[ [ 'CaRs', 'racs', 'scar' ], [ 'foR' ], [ 'poTatos' ], [ 'four' ], [ 'creams', 'scream' ] ]

```
**Resolução 1:**

```javascript

function sortStr(str) {
  if (!str) {
    return;
  }
  str = str.toLowerCase().split('').sort().join('');
  return str;
}

function combineAnagrams(words) {
  const anagrams = {};
  words.forEach((word) => {
    const sortedWord = sortStr(word);
    if (anagrams[sortedWord]) {
      return anagrams[sortedWord].push(word);
    }
    anagrams[sortedWord] = [word];
  });
  const result = [];
  for (const value in anagrams) {
    if (anagrams.hasOwnProperty(value)) {
      result.push(anagrams[value]);
    }
  }
  return result;
}

```

**Resolução 2:**
```javascript

function combineAnagrams(words) {
  const anagrams = {};

  words.forEach((word) => {
    let sortedWord = word.toLowerCase().split("").sort().join("");

    if (anagrams[sortedWord]) {
      return anagrams[sortedWord].push(word);
    }
    anagrams[sortedWord] = [word];
  });

  return Object.values(anagrams);
}

```
