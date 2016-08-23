# Guia de estilo CSS Airbnb fork

*Uma abordagem mais razoável para CSS*

## Tabela de conteúdo

  1. [Terminologia](#terminologia)
    - [Regras](#regras)
    - [Seletores](#seletores)
    - [Propriedades](#propriedades)
  1. [CSS](#css)
    - [Formato](#formato)
    - [Comentários](#comentarios)
    - [Seletores ID](#seletores-id)
    - [JavaScript hooks](#javascript-hooks)
    - [Border](#border)

## Terminologia

### Regras

Uma “declaração de regra” é o nome dado ao seletor (ou grupo de seletores) acompanhados de um grupo de propriedades. Segue um exemplo:

```css
.listing {
  font-size: 18px;
  line-height: 1.2;
}
```

### Seletores

Em uma declaraçao de regra, "seletores" são os bits que determinam quais elementos na árvore de DOM serão estilizados pelas propriedades definidas. Seletores podem coincidir com elementos HTML, assim como classes, ID ou qualquer um de seus atributos. Seguem exemplos de seletores:

```css
.my-element-class {
  /* ... */
}

[aria-hidden] {
  /* ... */
}
```

### Propriedades

Finalmente, propriedades são os elementos selecionados de uma regra de declaração. Propriedades são pares de chave-valor, onde uma regra de declaração pode conter uma ou mais declarações de propriedades. Declaração de propriedades são mostradas a seguir:

```css
/* some selector */ {
  background: #f1f1f1;
  color: #333;
}
```

## CSS

### Formato

* Use "soft tabs" (2 espaços) para identação.
* Prefira dashes `(-)` no lugar de camelCasing em nomes de classes.
  - Underscores `(_)` e PascalCasing podem ser utilizados caso você use BEM (veja [OOCSS e BEM](#oocss-e-bem) abaixo).
* Não use seletores ID.
* Quando usar múltiplos seletores em uma regra de declaração, ponha cada um em uma própria linha.
* Coloque um espaço antes da abertura de chaves `{` em declaração de regras.
* Em propriedades, coloque um espaço depois, mas não antes do caractere `:` (dois-pontos).
* Coloque chave de fechamento `}` de uma regra de declaração em uma nova linha.
* Coloque linhas em branco entre declarações de regra.

**Ruim**

```css
.avatar{
    border-radius:50%;
    border:2px solid white; }
.no, .nope, .not_good {
    // ...
}
#lol-no {
  // ...
}
```

**Bom**

```css
.avatar {
  border-radius: 50%;
  border: 2px solid white;
}

.one,
.selector,
.per-line {
  // ...
}
```

### Comentários

* Prefira comentários em uma única linha. Evite comentários no final da linha.
* Escreva comentários detalhados para códigos que não são auto-documentados:
  - Usos do z-index
  - Compatibilidade ou hacks específicos de navegadores

### Seletores ID

Evite enquanto possível selecionar elementos por ID em CSS. Seletores ID introduzem um nível alto de [especificidade](https://developer.mozilla.org/en-US/docs/Web/CSS/Specificity) para suas declarações de regras e eles não são reutilizáveis.

Para mais detalhes leia o seguinte [artigo do CSS Wizardry](http://csswizardry.com/2014/07/hacks-for-dealing-with-specificity/) sobre como ligar com especificidade.

### JavaScript hooks

Evite vincular a mesma classe em seu CSS e JavaScript. Combinando os dois, muitas vezes resulta em tempo perdido durante refatoração, quando um desenvolvedor deve fazer uma referência cruzada de cada classe que está alterando e, pior ainda, o medo de quebrar alguma funcionalidade.

Recomendamos a criação de classes específicas JavaScript para vinculação, com prefixo `.js-`:

```html
<button class="btn btn-primary js-request-to-book">Request to Book</button>
```

### Border

Utilizar `0` ao invés de `none` para especificar que um estilo não tem borda.

**Ruim**

```css
.foo {
  border: none;
}
```

**Bom**

```css
.foo {
  border: 0;
}
```

