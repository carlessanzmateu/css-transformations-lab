# About this project

This project _pretend_ to be a **css lab testing environment**. I'm going to write here all theory stuff I get during my lab sessions and also i'll push all the little things I code for have them all together.

From here, the readme goes to spanish. The real focus of doing this lab sessions is to achive a quick guide reference, so it has more sense to me print a guide in my language

-----
## Teoría   v0.2.1
-----

### Elementos de bloque:

Elementos que de forma predeterminada, comienzan una nueva línea en el documento.

### Elementos de línea:

Elementos que pueden comenzar en cualquier parte de una línea.

-----

### display:

Especifíca el _tipo de caja_ usada para un elemento HTML.

##### display values:

**inline**: _muestra un elemento cómo un elemento de línea._

**block**: _muestra un elemento cómo un elemento de bloque._

**none**: _No se mostrará el elemento (su "hueco o espacio" que de normal tendría su etiqueta HTML en el documento no tendrá efecto, es decir, es cómo si no existiera y fuera transparente)._

**initial**: _Devuelve a un elemento a su valor por defecto:_

_**~index.html**_
```html
<div>
  <h1>Hola Mundo</h1>
</div>
```

_**~style.css**_
```css
div {
  color: blue;
}

h1 {
  display: initial;
}
```
\*_El texto 'Hola Mundo', a pesar de tener un elemento padre que lo convertiría al color azul, el display initial lo devuelve a su estado por defecto: negro._

**inherit**: _el elemento **hereda** las propiedades del elemento padre:_

_**~index.html**_
```html
<div>
  <p>Hola mundo<p>
</div>

<div>
  <p>Lorem ipsum<p>
</div>

<div style="color: orange;">
  <p class="notBlue">Foo bar<p>
</div>
```

_**~style.css**_
```css
  p {
    color: blue;
  }

  p.notBlue {
    display: inherit;
  }
```

\*_El código anterior, debería mostar tres párrafos con el texto color azul. Pero hemos definido, que quien tenga la clase_ `.notBlue` _heredará los estilos del elemento padre. En este caso, el tercer párrafo, será de color naranja dado que el `<div>` padre tiene la propiedad `color:orange`._

**table**: _el elemento actúa como un elemento tabla: ```<table>```_

**table-cell**: _el elemento actúa cómo un elemento:_```<td>```

**table-column**: _el elemento actúa cómo un elemento:_```<col>```

**table-row**: _el elemento actúa cómo un elemento:_```<tr>```

-----

### position
Determina el _tipo_ de posicionamiento de un elemento en el documento.

##### position values:

**static**: _El elemento se renderiza en el orden en el que aparece en el documento. Es el valor por defecto._

**absolute**: _El elemento se posiciona relativamente respecto a su a primer elemento ancestro que no esté posicionado de forma estática._

**fixed**: _El elemento se posiciona respecto a la ventana del navegador._

**relative**: _El elemento se posiciona respecto a su posición su posición por defecto._

**initial**: _El elemento se posiciona respecto a su posición por defecto._

**inherit**: _El elemento hereda esta propiedad de su elemento padre._
