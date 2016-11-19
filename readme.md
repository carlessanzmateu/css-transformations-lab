# About this project

This project _pretend_ to be a **css lab testing environment**. I'm going to write here all theory stuff I get during my lab sessions and also i'll push all the little things I code for have them all together.

From here, the readme goes to spanish. The real focus of doing this lab sessions is to achive a quick guide reference, so it has more sense to me print a guide in my language

-----
## Teoría   v0.5.0
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

-----

### transition:

Permite cambiar los valores de un elemento en una duración predeterminada.

La propiedad `transition` por defecto debe definirse en el bloque css con los atributos por defecto y apuntar a las propiedades que se quieren alterar en algún momento o evento.

```css

div {
  width: 100px;
  transition: width;
}

div:hover {
  width: 200px;
}

```
Cuando se haga `hover` sobre un elemento `<div>`, este duplicara su ancho.

La propiedad `transition` admite cuatro parámetros, por lo tanto, se puede usar una única _función_ con al menos el primer parámetro (o los cuatro), o se puede definir cada parámetro por separado:

```css

div {
  width: 100px;
  transition: width 1s 1s ease;
}

div:hover {
  width: 200px;
}

```

```css

div {
  width: 100px;
  transition-property: width;
  transition-duration: 1s;
  transition-delay: 1s;
  transition-timing-function: ease;
}

div:hover {
  width: 200px;
}

```
\* Estos dos snippets **son equivalentes**


Las propiedades se pueden concatenar en una misma función o se puede poner por separado. Si se ponen juntas, basta con separar con comas:

```css
div {
  width: 100px;
  height: 100px;s
  background: orange;
  transition: background 1s, width 1s 10s, height 1s 1s ease;
}

div {
  width: 500px;
  height: 500px;
  background: blue;
}
```

```css
div {
  width: 100px;
  height: 100px;s
  background: orange;
  transition: background 1s;
  transition: width 1s 10s;
  transition: height 1s 1s ease;
}

div {
  width: 500px;
  height: 500px;
  background: blue;
}
```

**Por otro lado, el siguiente ejemplo no tendría efecto y sobreescribiría la transición**

```css
div {
  width: 100px;
  height: 100px;s
  background: orange;
  transition: background 1s, width 1s 10s, height 1s 1s ease;

  transition: height: 1s 1s ease;
}

div {
  width: 500px;
  height: 500px;
  background: blue;
}
```
Definir dos transiciones para una misma propiedad, sobreescribe la transición.


Por otro lado, también existe una abreviación para aplicar nuestros parámetros a todas las propiedades:

```css
div {
  width: 100px;
  height: 100px;s
  background: orange;
  transition: all 1s 1s ease;

}

div {
  width: 500px;
  height: 500px;
  background: blue;
}

```
\*transition all, modificará el width, el height y el background al hacer hover sobre el div

**Si definimos la `transition` en el hover:**

```css
div {
  width: 100px;
  height: 100px;s
  background: orange;

}

div {
  width: 500px;
  height: 500px;
  background: blue;
  transition: all 1s 1s ease;
}

```

La transición se aplicará al hacer hover, pero cuando dejemos de hacer hover, los valores iniciales volverán de forma brusca. Es decir, no habrá transción de "retorno". Esto es porque la transición entiende que se debe efectuar solo cuando exista evento `hover`, lo que ocurra después no debe tener efecto de transición.

**Definir la transición en el elemento principal y en el evento:**

```css
div {
  width: 100px;
  height: 100px;s
  background: orange;
  transition: all 0.5s;
}

div {
  width: 500px;
  height: 500px;
  background: blue;
  transition: all 10s;
}

```
En este caso, cuando se dispare el evento `hover`, se aplicará la transición definida en él, y en el cualquier otro caso, la definida en el principal.

En este código en concreto, crecerá durante 10 segundos y al terminar el evento de `hover`, volverá a sus valores iniciales en medio segundo. En este caso, no terminará de forma brusca, porque tiene una transición definida en el elemento principal.
