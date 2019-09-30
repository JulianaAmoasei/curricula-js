# Flexbox

- Tipo: `lectura`
- Formato: `individual`
- Duración: `2h`

## Objetivos de aprendizaje

- Aprender los fundamentos de la herramienta de CSS _flexbox_, utilizado para alinear y posicionar elementos, así como cómo utilizar todas sus funcionalidades correctamente.

***

## ¿Qué es Flexbox?

Por mucho tiempo las únicas herramientas disponibles para la creación de _layouts_
en CSS y posicionar elementos con una buena compatibilidad entre diferentes navegadores era `float` y `position`.
Sin embargo, estas herramientas tenían algunas limitaciones bastante frustrantes, especialmente cuando teníamos en cuenta lo _responsive_.
Algunas tareas que consideramos básicas en un _layour_, como centrar de manera vertical un elemento según el contenedor en el que esté, hacer que elementos en fila ocupen la misma cantidad de espacio y que las columnas sean del mismo tamaño independientemente del contenido que tengan dentro, eran imposibles o muy dificiles de lograrse con `float` o `position`, al menos de una forma practica y _flexible_.

Flexbox (que viene de _Flexible Box_) fue creada para que estas tareas fuesen mucho más simples y funcionales: los hijos de un elemento con Flexbox pueden posicionarse en cualquier dirección y pueden tener dimensiones flexbiles para adaptarse.

## Elementos

**Flex container** es el elemento que va a contener una estructura de elementos. Se puede definir utilizando la propiedad `display` con valor `flex` o `inline-flex`.

```html
  <div class="flex-container">
    <div>1</div>
    <div>2</div>
    <div>3</div>
  </div>
```

```css
  .flex-container {
    display: flex;
  }
```


**Flex Item** los elementos _hijos_ de un flex container.

**Ejes** son las direcciones basicas que existen en un flex container: _main axis_ que sería el eje horizontal o el eje principal y _cross axis_ que es el eje vertical.

## Propriedades para elementos madre

![container flex](https://css-tricks.com/wp-content/uploads/2018/10/01-container.svg)

Cuando utilizamos _Flexbox_, es muy importante saber que propiedades son declaradas en los elementos madre (por ejemplo, un `div` que alineará a los elementos hijos o _flex items_) y cuales seran declarados en los elementos hijos.
Abajo estan algunas de las propiedades que deben ser declaradas utilizando un elemento madre como selector (para alinear a sus hijos):


**flex-direction** determina el origen y el fin del flujo de dos items. Siguen el patrón establecido en la escritura occidental: de izquierda hacia derecha en `row`, de arriba hacia abajo en `column`, y para indicar que sea el sentido inverso, podemos utilizar `-reverse`.

```css
  .flex-container {
    flex-direction: row | row-reverse | column | column-reverse;
  }
```

![flex-direction](https://css-tricks.com/wp-content/uploads/2018/10/flex-direction.svg)

Podrás definir si los elementos tienen que caber en una misma línea o se iran rompiendo en varias líneas con la propiedad **flex-wrap**.

```css
  .flex-container {
    flex-wrap: nowrap | wrap | wrap-reverse;
  }
```

![flex-wrap](https://css-tricks.com/wp-content/uploads/2018/10/flex-wrap.svg)

La propiedad **flex-flow** es un tipo de propiedad _shorthand_ (una sola declaración que incluye varios valores relaciones a una misma propiedad) que incluye `flex-direction` y `flex-wrap`. Determina el orden en el cual apareceran los elementos.

**justify-content** define la alineación de los hijos en el largo del eje principal.

```css
  .flex-container {
    justify-content: flex-start | flex-end | center | space-between | space-around | space-evenly;
  }
```

![justify-content](https://css-tricks.com/wp-content/uploads/2018/10/justify-content.svg)

**align-items** define el comportamiento predeterminado de como los _flex items_ son alineados de acuerdo al eje vertical (_cross axis_). De esta forma, funciona de una manera similar a `justify-content`, pero en el eje perpendicular.

```css
  .flex-container {
    align-items: stretch | flex-start | flex-end | center | baseline;
  }
```

![align-items](https://css-tricks.com/wp-content/uploads/2018/10/align-items.svg)

**align-content** alinea el contenido dentro del contener cuando haya espacio extra en el eje vertical, similar a como `justify-content` alinea los items individuales en el eje principal.

```css
  .flex-container {
    align-content: flex-start | flex-end | center | space-between | space-around | stretch;
  }
```

![align-content](https://css-tricks.com/wp-content/uploads/2018/10/align-content.svg)

## Propriedades para elementos-filhas

A seguir, veremos propriedades que devem ser declaradas tendo como seletor
elementos-filhas, ou seja:

```html
  <div class="flex-container">
    <div class="flex-item">1</div>
    <div class="flex-item">2</div>
    <div class="flex-item">3</div>
  </div>
```

Isso significa que, onde existe um elemento-mãe com propriedade _flex_, é
possível atribuir propriedades flex específicas também para as filhas.

_Importante!_

- O CSS só enxerga a hierarquia mãe-filha; não vai aplicar as propriedades flex
  para elementos HTML que não estejam diretamente relacionados;
- Para que as propriedades funcionem nos elementos-filhas, as mães devem ter
  propriedade _flex_.
- As propriedades `float`, `clear` e `vertical-align` não têm efeito em
  flex-items.

A propriedade **order** determina o lugar que os elementos aparecerão.

```css
  .flex-item {
    order: <numero>; /* o valor default(padrão) é 0 */
  }
```

![order](https://css-tricks.com/wp-content/uploads/2018/10/order.svg)

**flex-grow** define a habilidade de um elemento-filha de "crescer" e ocupar
uma área maior, se necessário. Por exemplo, se em uma lista de 3 filhas, 2
delas têm propriedade `flex-grox: 1` e 1 delas tem `flex-grow:2`, essa última
crescerá para ocupar o dobro do tamanho das irmãs.

```css
  .flex-item {
    flex-grow: <numero>; /* o valor default(padrão) é 0 */
  }
```

![grow](https://css-tricks.com/wp-content/uploads/2018/10/flex-grow.svg)

**align-self** permite que o alinhamento padrão (definido por `align-items`)
seja sobrescrito para ítens individuais.

```css
  .flex-item {
    align-self: auto | flex-start | flex-end | center | baseline | stretch;
  }
```

![align-self](https://css-tricks.com/wp-content/uploads/2018/10/align-self.svg)

Existem outras propriedades para as filhas, como `flex-shrink`, `flex-basis` e
a shorthand `flex`, você pode pesquisar sobre elas para aumentar seu repertório.

## Vamos praticar?

[Flexbox Froggy](https://flexboxfroggy.com/)

## Links úteis

Assim como qualquer outra nova funcionalidade que aprendemos, é imprescindível
praticar bastante e pesquisar sempre que temos dúvidas. A seguir, alguns links
úteis.

Este conteúdo se baseia em grande parte no tutorial da [CSS Tricks](https://css-tricks.com/snippets/css/a-guide-to-flexbox/),
guarde nos seus favoritos para consultar sempre que precisar!

- [Flexbox explicado com gifs (em inglês)](https://medium.freecodecamp.org/even-more-about-how-flexbox-works-explained-in-big-colorful-animated-gifs-a5a74812b053)

- [Tutorial da tableless (em português)](https://tableless.com.br/flexbox-organizando-seu-layout/)

- [Flexbox no MDN](https://developer.mozilla.org/en-US/docs/Learn/CSS/CSS_layout/Flexbox)

- [Flexbox no W3C](https://www.w3schools.com/csS/css3_flexbox.asp)

- [Tabela com algumas funcionalidades do flexbox](https://internetingishard.com/html-and-css/flexbox/flexbox-layouts-7abd58.png)
