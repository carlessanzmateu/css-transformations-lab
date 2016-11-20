# About this project

This project _pretend_ to be a **css lab testing environment**. I'm going to write here all theory stuff I get during my lab sessions and also i'll push all the little things I code for have them all together.

From here, the readme goes to spanish. The real focus of doing this lab sessions is to achive a quick guide reference, so it has more sense to me print a guide in my language

-----
## Teoría   v0.6.0
-----

### Elementos de bloque:

Elementos que de forma predeterminada, comienzan una nueva línea en el documento.

### Elementos de línea:

Elementos que pueden comenzar en cualquier parte de una línea.

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

### top, bottom, left, right

Para elementos con `position: absolute`:

**top**: Esta propiedad hubicará un elemento arriba o abajo respecto al lado **superior** del ancestro posicionado más cercano.
**bottom**: Esta propiedad hubicará un elemento arriba o abajo respecto al lado **inferior** del ancestro posicionado más cercano.

**left**: Esta propiedad hubicará un elemento arriba o abajo respecto al lado **izquierdo** del ancestro posicionado más cercano.

**right**: Esta propiedad hubicará un elemento arriba o abajo respecto al lado **derecho** del ancestro posicionado más cercano.

**NOTA**: Si un elemento posicionado `absolute`, no tiene ancestros posicionados, usa el body del documento.
**NOTA 2**: Un elemento '_posicionado_', serán aquellos cuya posición sea cualquier valor excepto `static`.

Para elementos posicionados `relative`, el elemento se desplazará arriba o abajo de su borde, respecto a su posición normal de **él mismo**.

**NOTA 3**: Si la posición es `static`, estas propiedades no tendrán efecto.

##### top, bottom, left, right  values:

**auto**: _El navegador calcula la posición correcta respecto al lado seleccionado. Es la opción por defecto._

**length**: _Posiciona el elemento respecto a un valor dado: 20px, 2cm, 6em... Se permiten valores negativos._

**%**: _Permite posicionar un elemento respecto al borde seleccionado en tanto por cien (%) dependiendo del padre contenedor._

**initial**: _Recupera su posición por defecto respecto a ese lado._

**inherit**: _Hereda esta propiedad respecto al elemento padre._

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

### transition:

Permite cambiar los valores de un elemento en una duración predeterminada.

##### transition-timing-function values

Esta _función_ determina la curva de velocidad de la transición.

**ease**: _Transición con inicio lento, luego rápido y el final nuevamente lento._

**ease-in**: _Inicio lento._

**ease-out**: _Final lento._

**ease-in-out**: _Inicio y final lento._

**linear**: _La transición conserva la misma velocidad de inicio a fin._


##### Análisis de transition

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

-----

### overflow

Esta propiedad determina que ocurre si un elemento sobrepasa el elemento _caja_ que lo contiene. (Por ejemplo añadir barras de scroll).

**Esta propiedad solo funciona para elementos de bloque y que tengan un `height` definido.**

##### overflow values:

**visible**: _No se recorta lo que sobresale. Se renderiza por fuera de la caja. Es el comportamiento por defecto._

**hidden**: _Se corta el `overflow`, y el resto del elemento se vuelve invisible._

**scroll**: _Se corta el `overflow`, pero se añaden barras de scroll para ver el resto del contenido._

**auto**: _**Si** se corta el `overflow`, debería aparecer una barra de scroll._

**initial**: _Devuelve al elemento a su estado inicial por defecto._

**inherit**: _Hereda esta propiedad de su elemento padre._

-----

### HTML - Valores importantes:

##### Atributos:

**hidden**: Los elementos HTML con este atributo, no son relevantes, por lo que no deben ser renderizados en el documento.

**aria-hidden**: `aria-hidden="true"`, indica que este elemento y ninguno de sus descendientes debe ser visible.
