# Reflexiones

## Lo que aprendí

- La idea de tener una herramienta como css incorporado en el navegador es que puedas seleccionar un elemento del DOM a través de un selector de css y aplicar una variedad de atributos y valores que conforman una regla de estilo y especificar el estilo de un elemento.

- La idea de entender la cascada de css nos permitirá escribir reglas de estilo reutilizables entre los diferentes elementos sin sobreescribir o anular reglas que ya definimos con anterioridad

- CSS conversa con el navegador y le dice "como" debe mostrar el contenido de tu html

- Es sensible a las mayúsculas, por lo que  hay que tener mucho ojo al momento de definir las reglas de estilo.

- CSS es una herramienta que está adaptada a casi todos los navegadores y te permite controlar: `color`, `font (fuentes)`, `positioning(posicionamiento)`, `spacing(espaciado)`, `sizing(tamaño)`, `decorations(decoraciones)`, `transitions(transiciones)`

- Hay 3 maneras de aplicar estilos en nuestro html.`inline`,  a través del atributo `style` en el html, y como un recurso externo a través de la etiqueta `link`.

- Y aunque las 3 funcionen, se suele utilizar la tercera porque permite separar las responsabilidades, es decir, mantener las defininiones de estilos separadas del htlm que solo se encarga del marcado del contenido, todo esto, con el fin, de mejorar la legibilidad y poder reutilizar el código (escalar).

- Todos los elementos hijos del elemento `body` heredan los estilos que este tenga definido.


### Especificidad
Las reglas de estilo se aplican en cascada, es decir, de arriba hacia abajo.
- Si aplicas css inline pesa más que cualquier otra forma.
- En la cascada, si un elemento lo seleccionas a través de un selector de elemento y luego aplicas una clase, pesa más la clase
- Podemos decir, entonces que se prioriza un estilo sobre otro por la cascada.

- !important hace un tubo y se libera de la cascada y especificidad y hace que la regla que la use prevalezca.

- Si se aplica diferentes reglas de estiloa un mismo elemento, ganará el que sea más específico.

inline > id > class > elemento

```css
<style>
  body {
    background-color: black;
    font-family: monospace;
    color: green;
  }
  #orange-text {
    color: orange;
  }
  .pink-text {
    color: pink !important;
  }
  .blue-text {
    color: blue;
  }
</style>

<h1 id="orange-text" 
    class="pink-text blue-text" 
    style="color: white">
    Hello World!
</h1>
```



```css
h2 {
  color : red;
}

.text-blue: {
  color : blue;
}

  body {
    background-color: black;
    font-family: monospace;
    color: green;
  }

  .pink-text {  //especificidad 10
    color: pink; 
  }
  .blue-text { //especificidad 10
    color: blue; //gana porque está más abajo en la cascada anula los atributos de la clase .pink-text
  }             

```

```html
<h2 class="text-blue">Hola mundo</h2>

<h3 class="pink-text blue-text">Hola otra vez</h3>
```

### Sobre las fuentes (fonts)

- Podemos utilizar fuentes no standars (que no se encuentran en nuestro sistema opertivo).

- Google font es una librería libre de fuentes para la web y lo puedes usar en tu archivo css importandolo.

- Tienes dos maneras de hacer esto : a través de la etiqueta `link` en el html o con el comando `@import` en el archivo de css

```html
<link href="https://fonts.googleapis.com/css?family=Lobster" rel="stylesheet" type="text/css">
```

- Luego defines la la propiedad font de la siguiente manera

```css
font-family: FAMILY_NAME, GENERIC_NAME;.
```
- El `GENERIC_NAME` es una fuente `fallback` u opcional, para el caso en que la fuente no estandar que estás utilizando no se encuentre disponible.

- En el caso de que una fuente no se encuentre disponible le puedes decir al navegor que `degrade`a otra fuente

```css
h2 {
  font-family : Helvetica, sans-serif;
}
```

### Sobre el styling
- Vamos a partir del hecho de que lo único constante es el lienzo en donde yo voy a trabajar.

- Los elementos en html son esencialmente rectangulares

- Hay 3 propiedades que controlan el espacio que rodea a cada uno de los elementos html : `padding`, `border` y `margin` y los valores que pueden tomar pueden ser `positivos` o `negativos`

`padding` : contextura del elemento, controla la cantidad de espacio entre el contenido del elemento y su borde. 
Por lo tanto a mayor padding, aumenta la distancia entre el contenido del elemento y su borde, contextura ancha.
A menor padding, contextura delgada.

`margin`: la relación con el exterior, sabes que, mantente al margen. La cantidad de espacio que hay entre un elemento y los elementos que lo rodean. 

Por lo tanto a mayor margen, en un mismo lienzo,  el elemento se contrae, por lo que  aumenta el espacio entre el borde del elemento y los elementos que lo rodean.

Con un margen negativo el elemento crece, ocupa más espacio, por lo que se achica el espacio entre el borde del elemento y los elementos que lo rodean

`padding` 
  `padding-top`
  `padding-right`
  `padding-bottom`
  `padding-left`

`margin`
  `margin-top`
  `margin-right`
  `margin-bottom`
  `margin-left`

- Para evitar usar todas las propiedades usaremos la notación de agujas del reloj `Clockwise notation`

```css
padding : 10px 20px 10px 20px; (T, R, B, L)
margin : 10px 20px 10px 20px;

```
### Sobre los unidades de medida
- Los pixeles(px) son un tipo de unidad de longitud que le indica al navegador el tamaño o espacio de un elemento.
- En css existen diferentes unidades de longiud que se puede utilizar.

- Las dos principales unidades de longitud son `absolutas` y `relativas`.

- `Las unidades absolutas` se vinculan con las unidades fìsicas de longitud (cm, mm, inch) centimetros, milimetros, pulgadas. Por lo que se aproximan a la medida real de una pantalla, sin embargo hay diferencias porque depende de la resolución de la pantalla.


- `Las unidades relativas`:  `em` o `rem` son relativas a otra valor de longitud
`em - font`: se basa en el tamaño de la fuente del elemento.
Si usamos esta medida para definir el tamaño de la fuente de un elemento, será relativo al tamaño de la fuente de su elemento padre.

### Sobre los colores y la manera en como los representamos en css
- Hay dos maneras de reprensentar el color en css : `valores rgb` o `sistema hexadecimal - 6 digitos`
- Principalmente usamos el sistema decimal o de base 10 que usa simbolos 0 a 9 por cada dígito

- El sistema hexadecimal utiliza 16 simbolos (0-9,A,B,C,D,E,F)
[hexadecimal](https://en.wikipedia.org/wiki/Hexadecimal)

- El sistema hexadecimal se utiliza con mucha frecuencia por los diseñadores de sistemas de computo y programadores porque provee una representación amigable de los valores del código binario. 
`0` es el menor valor del sistema hexadecimal
`F` es el mayor valor del sistema hexadecimal

- 1 simbolo hex representa 4 bits(0110) tambien conocido como `nibble` la mitad de un byte(01110000)

- 1 byte puede tener valores desde 0000000-11111111 (binario)

- 1 byte puede tener valores desde 00-FF

- En CSS para representar los colores usamos `6 digitos 
hexadecimales` 

- 2 para el Red, 2 para Green y 2 para el Blue. (Modelo de color RGB)

- 1 digito hexadecimal puede tomar 16 opciones, 2 digitos 16 * 16 = 256 -> (0 - 255)

```css
body {
  background : #000000; #000; rgb(0,0,0)   //black
  background : #FF0000; #F00; rgb(255,0,0)  //rojo
  background : #00FF00; #0F0; rgb(0,255,0)   //verde
  background:  #0000FF; #00F; rgb(0,0,255)   //azul
} 

```

- `El modelo de color RGB` [modelo rgb](https://en.wikipedia.org/wiki/RGB_color_model) es un modelo de color aditivo en donde las luces roja, verde y azul se agregan juntas de varias maneras para reproducir una amplia gama de colores. 
Su objetivo principal es el de `detectar`, `representar` y `visualizar` imagenes en los sistemas electrónicos.
Es un modelo de color `device-dependent` que depende del dispositivo. 
Diferentes dispositivos `detectan` o  `reproducen` un valor RGB de manera diferente. Por lo tanto, un  valor de RGB no define el mismo color en todos los dispositivos sin algùn tipo de `gestión de color`.
`dispositivos de entreda RGB` : Tv y video camaras, scanner de imagenes, camaras digitales.
`dispositivos de salida RGB` : pantallas de celular o commputadora, CRT, LCD, Plasma, proyectores, LED, impresoras de color.




## Algunas propiedades básicas

`color` : responsable del color en los elementos del tipo texto



`font` : responsable de las fuentes
`font-size` : tamaño de la fuente
`font-family` : familia a la que pertenece, forma de la fuente

`width` : propiedad que controla el ancho de un elemento

`border`: pinta border alrededor de un elemento. Tiene a su vez las propiedades `style` `color` `width` `radius`

para hacer imagenes circular : border-radius : 50%

`padding` 
  `padding-top`
  `padding-right`
  `padding-bottom`
  `padding-left`

`margin`
  `margin-top`
  `margin-right`
  `margin-bottom`
  `margin-left`



```css
.thin-red-border {
  border-color: red,
  border-width: 5px,
  border-style: solid
}

.thin-yellow-border {
  border : 1px solid yellow
}


```

## Algunos selectores básicos

- `selector de elemento` : que tiene el mismo nombre del elemento del dom
`selector tipo clase` :se aplica al atributo class de cualquiern elemento html, y  me permite aplicar una regla de estilo a diferentes elementos

- `selecto del tipo id`: se aplica al atributo id de cualquier elemento en el html. Me permite trabajar de manera especìfica con un solo elemento.
A nivel de html el atributo `id` debe ser único. Se considera como buena práctica no dar a más de un elemento el mismo atributo id

- `selector de atributo` : [attr='value'] 
                         [type='checkbox']
                         [type='radio']

- :root : selector raíz 

## Uso de variables para cambiar muchos valores de un elemento en una

- El usar variables en css es lo máximo del mundo mundial!
- Podemos usar un fallback (valor por default para las variables)

```css
/*  definimos una variable en css */
--penguin-skin : gray;

/* para usar la variable */

background : var(--penguin-skin);

/* colocamos un valor por default, si la variable no se encuentra va a tomar el valor de negro */

background : var(--penguin-skin, black);

```

## Sobre la compatibilidad con el uso de fallbacks del navegador
- Cuando se trabaja con css una de las actividades que se tiene que realizar es el hecho de probar como se ve en diferentes navegadores

- Cuando el navegador analiza y parsea el css ignora cualquier propiedad que no reconoce o que no soporta. Por ejemplo si utilizas varibles, IE no lo reconocerá porque no lo soporta, en ese caso, ese navegador utilizará cualquier valor que tenga para esa propiedad, si no lo encuentra, trabajará con los valores por default que tiene predefinido.

- Lo que se puede hacer es en las declaraciones, regresar a los origines.

```css
  :root {
    --red-color: red;
  }

  body {
    background : red;
    background: var(--red-color, #c6faf1);

    /*Renombrar una variable */
   --red-color: white; 
  }

```
## Usando media queries para cambiar el valor de las variables
