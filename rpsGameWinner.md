##  Torneio
No jogo Pedra-Papel-Tesoura (Jan-Ken-Po), cada jogador escolhe a estratégia que irá usar: Pedra(PE); Papel(PA) ou Tesoura(TE). As regras são que Pedra ganha de Tesoura, Tesoura ganha de Papel e Papel ganha de Pedra.

### Jogo entre 2 pessoas
A entrada chamada _JOGO_ é na forma de lista (Array), no qual cada elemento é outra lista (_JOGADA_) formada por 2 elementos: [<nome_do_jogador>, <estrategia_do_jogador>]

Escreva um método que aceita uma lista com duas JOGADAS e se comporta da seguinte maneira:

1.  Se o número de jogadores não for igual a 2, lança o erro WrongNumberOfPlayersError
2.  Se algum jogador escolher uma estratégia que não seja "PE", "PA" ou "TE", ignorando se as letras são maiúsculas ou minúsculas, lança o erro NoSuchStrategyError
3.  Caso contrário, retorna a lista formada pelo jogador e sua estratégia. Se os dois jogadores usarem a mesma estratégia, o primeiro jogador vence
```text
Siga o modelo:
function rpsGameWinner(game) { if (game.length != 2) { throw 'WrongNumberOfPlayers'; } // your code here...}console.log(rpsGameWinner(game)) => [ 'Dave', 'TE' ]
```

**Resolução 1:**
```javascript
function rpsGameWinner(game) {
  if (game.length != 2) {
    return console.log("WrongNumberOfPlayers");
  }
  if (!game[0][1].match(/\bPE\b|\bPA\b|\bTE\b/gi) || !game[1][1].match(/\bPE\b|\bPA\b|\bTE\b/gi)){
    return console.log("NoSuchStrategyError");
  } else {
    if (game[0][1] == game[1][1]) return console.log(`Vencedor: ${game[0]}`);
    if (game[0][1].toUpperCase() == "PA" && game[1][1].toUpperCase() == "PE") 
	    return console.log(`Vencedor: ${game[0]}`);
    if (game[0][1].toUpperCase() == "PE" && game[1][1].toUpperCase() == "TE") 
	    return console.log(`Vencedor: ${game[0]}`);
    if (game[0][1].toUpperCase() == "TE" && game[1][1].toUpperCase() == "PA") 
	    return console.log(`Vencedor: ${game[0]}`);
    return console.log(`Vencedor: ${game[1]}`);
  }
}
```