# Observaciones

Cande, felicitaciones por tu trabajo. Es increible el nivel de atención al detalle que demostras con este trabajo: cada espaciado, cada linea, se nota que está pensada y repensada para seguir a la perfección el modelo. Espero que hayas disfrutado hacer este segundo trabajo, creo al menos que es un excelente agrgado a tu portfolio ya que brilla aquí tu talento. 

Tengo, lamentablmemente, pocos comentarios para hacerte, ya que el nivel de este trabajo es realmente muy alto. Pero siempre hay algo que comentar! :) Como dije en clase, este trabajo no se hace para que constates conocimientos, sino para que aprendas: en ese sentido, mi intencion es que estos comentarios te sirvan para aprender, mejorar tu codigo a futuro e ir apreciando mejor qué se espera de nosotras como desarrolladoras front end.

## Estructura correcta de documento HTML

Tu HTML esta realmente excelente. Claro, prolijo, muy bien comentado e identado.

Tu `header` termina junto a la `nav`: si bien en algunos diseños identificar el `header` es complejo, creo que en este caso definitivamente debe incluir a la primera sección "introduction-text-container". Un `header` representa siempre lo que llamamos "contenido introductorio": todo aquello que da la bienvenida a nuestra web, sin dar información más específica (pero invitándonos a verla)

## Respeta la consigna

- El portfolio cuenta con las secciones solicitadas
- Al clickear en los links de navegación, debe llevar a la sección correspondiente
- Al clickear en los links de contacto, debe llevar a la página externa
  correspondiente
- El portfolio debe tener un diseño responsivo y verse correctamente en distintos dispositivos
- El portfolio debe estar deployado y ser accesible desde una URL
- El repositorio en GitHub debe tener un readme adecuado

Todos estos puntos están cumplidos. Menciono especialmente tu responsive: es increíble lo bien que solucionaste las distintas resoluciones, y las poquisimas media queries que necesitas hablan de que desde el principio tuviste una excelente estrategia para maquetar tu pagina. 

Un comentario es que en las resoluciones de 1100 a 820px(escritorios pequeños) tu codigo "rebalsa". Te das cuenta porque hay un scroll horizontal, y una especie de barra blanca que cubre todo el extremo derecho. Esto ocurre normalmente cuando hay un elemento que rebalsa su contenedor, forzando que el body sea más grande que la pantalla. En tu caso, ese elemento es `about-image-container`, dado que la segunda imagen rebalsa. En ese caso, podemos o bien modificar un poquito el diseño, o directamente decirle a `about-image-container`: `overflow:hidden`. 

Sobre tus media queries, es muy recomendable que las ordenes de mayor a menor. Hoy en tu CSS no parecen seguir un orden especifico. Creo que es por este motivo que debiste separar en dos media query diferentes los estilos para celulares. Efectivamente, en un código en el cual una orden cambie para dos resoluciones trae problemas por la cascada de CSS. 

Considerá este ejemplo: en pantallas de escritorio queremos que el `h1` sea rojo, en tablet queremos que se vea verde y en celulares queremos que se vea azul. 

```css
h1 {
    color: red;
}

/* celulares */
@media screen and (max-width: 576px) {
    h1 {
    color: blue;
    }
}

/* tablet */
@media screen and (max-width: 992px)  {
    h1 {
    color: green;
    }
}
```

En escritorio y tablet todo parece verse bien... pero en celulares, seguimos viendo el `h1` de color verde en lugar de verlo azul. Eso ocurre porque en la orden para tablets solo hemos dicho `(max-width: 992px)`, es decir: "siempre que el tamaño de la pantalla sea menor a 992px, veremos ese estilo". Inmediatamente antes de esa orden tenemos una que dice "siempre que el tamaño de la pantalla sea menor a 576px..." pero la orden para 992px está por debajo y, por lo tanto, termina imponiéndose por la cascada de CSS. 

### Respeta el diseño dado

Cumplido a la perfección. 

### Buena estructura de proyecto

Cumplido. 

### Código bien indentado

Tabulas muy bien, lo cual parece un detalle extra cuando una recien comienza pero ayuda un monton a su legibilidad, y que lo hayas logrado en esta etapa es un gran mérito. 

### Comentarios que permiten mejorar la legibilidad del código

Impecables. 

### Uso correcto de etiquetas semánticas

En general usas bien las etiquetas semánticas. Ya te comenté el uso de `header`. Creo también que las tarjetas de producto deberían ser `article` (en este caso, como descendientes directos del `a`). Esto permite que los usuarios de lectores de pantalla los encuentren fácilmente, y también ayuda al SEO. Todo elemento que sea autocontenido, reusable, repetible y pueda usarse en diferentes contextos, debe ser un article. Sobre ese tema te dejo una lectura: https://www.smashingmagazine.com/2020/01/html5-article-section/

### Buenos nombres de clases

Cumplido. 

### Código CSS bien estructurado

Cumplido. Noto unos pocos estilos innecesarios o confusos, que te voy indicando en tu archivo de css. El comentario general que te haría es que en general no vas a necesitar nunca width: 100%, ese es el estilo por defecto. Hay excepciones, pero son pocas: en general, cuando un elemento tenga position: absolute, o cuando quieras que un elemento con width especifico en desktop ocupe el 100% en la media query. 

### Reutilización de estilos

Cumplido en general, a veces podría mejorar. Como ejemplo, tomemos las siguientes imagenes: 

```css
.about-image-1 {
  max-width: 371px;
  position: relative;
  top: 50px;
  width: 100%;
}

.about-image-2 {
  bottom: 50px;
  left: 100px;
  max-width: 371px;
  position: relative;
  width: 100%;
}
```

La única diferencia que tienen es que .about-image-2 tiene  left: 100px;. Este es un buen caso para darle a ambos la misma clase, y solo agregar el left: 100px; en la segunda con una clase aparte. 

Mismo ocurre por ejemplo con "brands-section" y "about-section". 

### Cumple con criterios básicos de accesibilidad

- Los colores tienen un contraste adecuado

Cumplido.

- Las imágenes tiene el atributo `alt` que corresponde

Cumplido. 

- Los íconos y elementos que no presentan texto agregan la información correspondiente por otros medios (etiquetas aria, texto oculto)

No cumplido. 

- En los links a redes sociales de tu footer, los `a` necesitan un aria, o el lector no podrá informarle al usuario adónde dirige ese link. 
- También en el form, el input deberia tener un aria label. (nota que nada que ver: qué bien resolviste ese diseño con el boton y el input juntos!). 
- El `a` que rodea al ícono con la flecha hacia abajo de la primera sección, debería tener un aria label que le indique al usuario qué ocurre si hace click allí. 

Este último punto estaría para discutir con el equipo de diseño de esta web, pero vimos en clase que el lector de pantalla agrupa los links. Si pido ver todos los links en tu navbar, por ejemplo, el lector de pantalla dirá: "Link: about us. Link: shop. Link: portfolio". Eso está perfecto. Ahora, un poco más adelante el lector dirá  "Link: view more". Ese es el link que tenemos en la sección de productos, pero al agrupar links el lector de pantalla no anuncia en qué sección estamos. "Ver más... ver más qué?" va a preguntarse nuestro usuario, y con razón. No es buena idea usar links con frases como "Ver más", o "Click aquí", dado que no le dan al usuario de lector de pantalla la información necesaria para entender adónde lleva ese link. 

En este caso la decisión de poner ese "View More" es del equipo de diseño, y como desarrolladoras debemos respetar esas decisiones (si bien en el ámbito laboral tenemos la posibilidad, y yo diría que también la responsabilidad, de discutir esas decisiones si pensamos que impactaran negativamente en los usuarios). Supongamos que el equipo de diseño no acepta nuestra sugerencia: este es también un buen caso de uso para una `aria-label`:

```html
<a href="#" aria-label="See all products" class="products-cta">VIEW MORE →</a>
```

- Los íconos y elementos que no necesitan ser anunciados por un lector de pantalla tienen la etiqueta aria
  correspondiente

No lo usas, pero tampoco veo que sea necesario en este diseño. 

- Commits con mensajes adecuados

Cumplido, noto muchos y buenos commits en tu proyecto, lo que siempre se agradece.

- Cuenta con un favicon

Cumplido, aunque debería estar en la carpeta principal, en lugar de en la carpeta de imágenes. Muchos servicios de hosting van a buscarlo allí. 

### Nota: 9
