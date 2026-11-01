# Escribo Coding Challenge

Two small coding exercises: a PHP endpoint that sums the multiples of 3 or 5, and a two-player Snakes and Ladders game in the browser.

Technical-assessment exercises for Escribo, written in January 2021 (commits "Teste Técnico 01" on 2021-01-07 and "Segundo Desafio" on 2021-01-11).

## What it does

### `primeiro.desafio/` (first challenge)

- A form asks for a positive integer N.
- jQuery posts it via AJAX to `dist/php/somatorio.php`, which adds up every integer below N that is divisible by 3 or 5 and returns `{"vl_resultante": <sum>}` as JSON.
- If `numero` is missing, the endpoint returns `{"ds_erro": "Número não informado"}`.

### `segundo.desafio/` (second challenge)

- A Snakes and Ladders game ("Cobras e Escadas") for two players on a 100-square board. The board image is `dist/img/jogo.jpg`.
- The game logic is the `CobrasEscadas` class in `dist/js/CobrasEscadas.js`:
  - the board is an array of offsets: positive for ladders, negative for snakes;
  - each turn rolls two dice and moves the current player by their sum;
  - going past 100 bounces back by the extra amount;
  - rolling doubles gives the same player another turn;
  - the first player to reach 100 wins ("Jogador 1 venceu!" / "Jogador 2 venceu!").
- The page has "Iniciar/Reiniciar Jogo" to restart and "Jogar Dados" to roll, and shows both positions, whose turn it is and the dice values.

## Tech stack

- PHP (first challenge only), with no framework.
- HTML and JavaScript (ES6 class), jQuery 3.5.1.
- Bootstrap 4.5.2 (second challenge). `dist/js/bootstrap.js` is the bundle build that includes Popper.

## Running locally

- **First challenge**: needs PHP. From the repository root, run `php -S localhost:8000`, then open `http://localhost:8000/primeiro.desafio/index.html`. Apache works too.
- **Second challenge**: static files only. Open `segundo.desafio/index.html` in a browser.

No database is needed.

## Project structure

```
primeiro.desafio/
  index.html             form + AJAX call
  dist/php/somatorio.php sum of multiples of 3 or 5
  dist/js/jquery.js
segundo.desafio/
  index.html             game UI
  dist/js/CobrasEscadas.js game logic
  dist/js/, dist/css/    jQuery, Bootstrap
  dist/img/jogo.jpg      board image
```

## Notes

- These are short exercises with no tests and no build step. Libraries are committed as files.
- The UI text and identifiers are in Portuguese.
- `CobrasEscadas.js` still has a leftover `console.log` in the bounce-back branch.
