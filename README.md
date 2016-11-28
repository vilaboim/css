# Vitta CSS / Stylus Styleguide

*Esse styleguide é baseado no [Airbnb CSS Styleguide](https://github.com/airbnb/css)*

## Conteúdo

  1. [Terminologia](#terminologia)
    - [Declaração](#declaração)
    - [Seletores](#seletores)
    - [Propriedades](#propriedades)
  1. [CSS](#css)
    - [Formatação](#formatação)
    - [Comentários](#comentários)
    - [OOCSS e BEM](#oocss-e-bem)
    - [Seletores ID](#seletores-id)
    - [Funções JavaScript](#funcoes-javascript)
    - [Borda](#borda)
  1. [Stylus](#stylus)
    - [Sintaxe](#syntaxe)
    - [Ordenação](#ordenação)
    - [Variáveis](#variáveis)
    - [Mixins](#mixins)
    - [Extend](#extend)
    - [Seletores aninhados](#seletores-aninhados)

## Terminologia

### Declaração

Uma “declaração” é o nome dado a um seletor (ou grupo de seletores) acompanhado de um grupo de propriedades. Um exemplo:

```css
.body {
  color: #CCC;
  font: 300 10px/1.5 Open Sans, Arial, sans-serif;
}
```

### Seletores

Em uma declaração,  “seletores” são os termos que determinam quais elementos no DOM serão estilizados pelas propriedades definidas. Seletores podem corresponder a elementos HTML, bem como a classe, ID ou qualquer atributo de um elemento. Alguns exemplos de seletores:

```css
.MyElementClass {
  /* ... */
}

input[type="textarea"] {
  /* ... */
}
```

### Propriedades

Propriedades dão estilo ao elemento selecionado em uma declaração. Propriedades são pares chave-valor, e uma declaração pode conter uma ou mais propriedades. Propriedades são parecidas com isso:

```css
/* seletor */ {
  background: #F1F1F1;
  color: #333;
}
```

## CSS

### Formatação

* Use tabs (4 espaços) para identação.
* Use Underscores e PascalCasing nos nomes de classes (veja [OOCSS e BEM](#oocss-e-bem) abaixo).
* Não use seletores ID.
* Deixe apenas um seletor por linha em uma declaração com múltiplos seletores.
* Coloque um espaço antes da chave de abertura em uma declaração.
* Em uma propriedade, coloque um espaço depois de `:`.
* Deixe as propriedades em ordem alfabética.
* Coloque a chave de fechamento em uma nova linha.
* Salte uma linha entre declarações.

**Ruim**

```css
.use-espacos-e-salte-linhas{
    margin-right:15px;
    font-size:17px;}
.salte-linhas, .entre, .seletores, .e-declaracoes {
    // ...
}
#nao-use-id {
  // ...
}
```

**Bom**

```css
.Tabs__Icon {
  border-radius: 50%;
  border: 2px solid white;
}

.um,
.seletor,
.por-linha {
  // ...
}
```

### Comentários

* Prefira comentários de linha (`//` em Stylus).
* Use comentários na mesma linha da propriedade.
* Escreva comentários para propriedades que não sejam autodocumentadas:
  - z-index
  - Compatibilidade ou browser hacks

### OOCSS e BEM

Nós acreditamos em uma combinação de OOCSS e BEM, por estas razões:

  * Deixa HTML e CSS limpos.
  * Ajuda a criar componentes reutilizáveis.
  * Permite menos seletores aninhados e especificidade baixa
  * Ajuda na criação de folhas de estilo escaláveis

**OOCSS**, ou “CSS Orientado a Objetos”, é uma abordagem que ajuda a criar folhas de estilo como uma coleção de “objetos”: componentes reutilizáveis que podem ser usados de forma independente na aplicação.

  * [OOCSS wiki](https://github.com/stubbornella/oocss/wiki) por Nicole Sullivan
  * [Introduction to OOCSS](http://www.smashingmagazine.com/2011/12/12/an-introduction-to-object-oriented-css-oocss/) por Smashing Magazine

**BEM**, ou “Block-Element-Modifier”, é uma convenção de nomes para classes em HTML e CSS. Foi criado pensando em escabilidade e serve como um guia para implementar OOCSS.

  * [BEM 101](https://css-tricks.com/bem-101/) por CSS Tricks
  * [Introduction to BEM](http://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/) por Harry Roberts

Recomendamos o uso de uma variação do BEM, usando UpperCamelCase.

```css
/* ConfigList.css */
.ConfigList { }
.ConfigList__Row { }
.ConfigList__Row--header { }
```

  * `.ConfigList` é o “bloco” e representa o componente de mais alto nível.
  * `.ConfigList__Row` é um “elemento” e representa uma parte de `.ConfigList` que ajuda a compor o bloco.
  * `.ConfigList__Row--header` é um “modificador” e representa uma variação ou estado diferente do elemento `.ConfigList__Row`.

### Seletores ID

tl;dr
Não use.

Seletores ID causam um nível de [especificidade](https://developer.mozilla.org/en-US/docs/Web/CSS/Specificity) desnecessário nas suas declarações, e não são reutilizáveis.

### Eventos JavaScript

Não use classes como trigger para eventos JavaScript, use atributos [data-*](http://blog.realstuffforabstractpeople.com/post/31753521367/classnames-for-styling-data-attributes-for) no lugar. Classes CSS devem servir apenas para estilização, você pode desencorajar outros desenvolvedores a fazer mudanças colocando-as com outras funções.

```html
<button class="Btn--primary" data-role="save-patient">Salvar</button>
```

### Zero

`0` é `0` independente de unidade, então omita-a.

**Ruim**

```css
.Schedule {
  margin: 0px auto;
}
```

**Bom**

```css
.Schedule {
  margin: 0 auto;
}
```

## Stylus

### Syntaxe

* Use () entre os parâmetros de Mixins e Funções

### Ordenação de propriedades

Ordene as propriedades em ordem alfabética

### Variáveis

Use $ na declaração de variáveis ($bg-color = #FFF). Prefira nomes de variáveis em dash-cased (ex.: `$primary-color`) em vez de camelCased ou snake_cased.
Coloque um underscore como prefixo de variáveis que serão usadas apenas em um arquivo (ex. : `$_primary-color`).

### @extend

Se precisar usar `@extend`, coloque-o antes de qualquer propriedade.

### Seletores aninhados

Seletores aninhados, **se necessários**, vão por último. Adicione uma linha em branco entre suas declarações e seletores aninhados.
Aplique as mesmas regras acima também entre seletores aninhados.

```stylus
.btn
  background green
  font-weight bold
  transition(background 0.5s ease)

  .icon
    margin-right 10px
  }
}
```

**Não aninhe seletores em mais de três níveis**

```stylus
.page-container
  .content
    .profile
      // PARE!
```

Quando existem muitos níveis de aninhamento, você provavelmente está cometendo um (ou mais) desses erros no seu CSS:
* Muito preso ao HTML
* Excessivamente específico
* Não reutilizável

**Nunca aninhe seletores ID**

Se você precisar usar um seletor ID, eles nunca podem ser aninhados. Se isso acontecer você deve reavaliar sua marcação HTML ou avaliar a necessidade de tanta especificidade.
