# Fundación semillas (Dashboard)
Este proyecto contiene un Demo (MVP) del dashboard para la fundación semillas, enfocándose primordialmente en la salud emocional de los estudiantes, para lo cual se encontrarán indicadores emocionales de los mismos; siendo además de eso, una herramienta completa de visualización general del status del alumno, considerando cada una de sus actividades modulares para cada diplomado.

[![Semillas dashboard Demo](https://i.postimg.cc/SRqqZwn6/Group-231.png "Semillas dashboard Demo")](http://https://i.postimg.cc/SRqqZwn6/Group-231.png "Semillas dashboard Demo")

# Estructura del código

## Hecho con

<div>
<a href="https://developer.mozilla.org/en-US/docs/Glossary/HTML5" target="_blank" rel="noreferrer"><img src="https://raw.githubusercontent.com/danielcranney/readme-generator/main/public/icons/skills/html5-colored.svg" width="46" height="36" alt="HTML5" /></a>
<a href="https://www.w3.org/TR/CSS/#css" target="_blank" rel="noreferrer"><img src="https://raw.githubusercontent.com/danielcranney/readme-generator/main/public/icons/skills/css3-colored.svg" width="46" height="36" alt="CSS3" /></a>
<img src="https://images-wixmp-ed30a86b8c4ca887773594c2.wixmp.com/f/d843eb4d-482e-4f76-b676-25b073d1d522/d5lujy4-2908b934-c794-436e-92fe-1bd5f8df39f5.png/v1/fill/w_526,h_461,strp/corazon_rojo_png_by_catatini_d5lujy4-fullview.png?token=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJ1cm46YXBwOjdlMGQxODg5ODIyNjQzNzNhNWYwZDQxNWVhMGQyNmUwIiwiaXNzIjoidXJuOmFwcDo3ZTBkMTg4OTgyMjY0MzczYTVmMGQ0MTVlYTBkMjZlMCIsIm9iaiI6W1t7ImhlaWdodCI6Ijw9NDYxIiwicGF0aCI6IlwvZlwvZDg0M2ViNGQtNDgyZS00Zjc2LWI2NzYtMjViMDczZDFkNTIyXC9kNWx1ank0LTI5MDhiOTM0LWM3OTQtNDM2ZS05MmZlLTFiZDVmOGRmMzlmNS5wbmciLCJ3aWR0aCI6Ijw9NTI2In1dXSwiYXVkIjpbInVybjpzZXJ2aWNlOmltYWdlLm9wZXJhdGlvbnMiXX0.pNq_uQyIyT_9OM3KQsAPrUplcX6Oz6Br0Hz8MZudEUE" width="46" height="36" alt="Corazón"/>
</div>

## :root e importación
Se establece una base en la que se importan las tipografías a utilizar y se determinan variables de estilo para aquellas propiedades y/o valores con una alta frecuencia de uso.

```css
@import url('https://fonts.googleapis.com/css2?family=Dosis:wght@500&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Dosis:wght@700&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Playfair+Display&display=swap');

:root {
    --green-darker: #009458;
    --green-light: #69BF97;
    --white: #FFFFFF;

    --body-color: #F3F3F3;

    --border-radius-cards: 15px;
    --border-circular:50%;
    --transition: all 500ms ease;

    --filter-cards:drop-shadow(1px 0px 5px rgb(173, 173, 173));
}
```

# Atomic design

## Card de estudiante

![Atomic design card estudiante](https://i.postimg.cc/PJ2pWZDX/Frame-6.png "Atomic design card estudiante")

La tarjeta de información del estudiante parte de la imagen de perfil del alumno, que posteriormente conformará el resto de los perfiles de estudiantes.

```html
<article class="card_student" id="card_student">
    <h2>Id card Estudiante</h2><br>
        <div class="information_student">
            <div class="profile m-auto"><img src=".." alt=".." class="profile_image">
             <p></p>
            </div>
            <div>
                <h3>Andrea Ramirez</h3>
                <p>Diplomado en sostenibilidad ambiental</p>
                <a href="#modal">Ver perfil completo</a>
            </div>
        </div>
            <div class="other_students">
                 <img src="img/avatar_1.jpg" alt="Estudiante 1">...<img ... alt="Estudiante 5">
                 <div class="layer_text">+12</div>
            </div>
</article>
```

Todas las imágenes de esta tarjeta cuentan con propiedades y valores iguales, como lo son el borde y radio del mismo.

```css
/*Imágenes de perfil*/
.card_student img {
    border-radius: var(--border-circular);
    border: 5px solid var(--white)
}
```
Con el fin de hacer contenedores fluidos, se establecen medidas mínimas y máximas de las imágenes conforme al espacio que estas mismas dispongan Todo esto posible además gracias al "display:flex" para cada contenedor padre.

```css
/*Imagen  de perfil principal*/
.card_student .profile_image {
    width: min(120px, 100%);
}

/*Contenedor de otros perfiles*/
.other_students {
    display: flex;
    margin-top: 20px;
    justify-content: flex-end;
    position: relative;
    max-height: 70px;
}

.other_students img {
    max-width: 70px;
    max-height: 50px;
    margin-left: -25px;
}
```


## Estado de los estudiantes
![Atomic design estado estudiantes](https://i.postimg.cc/zDjgYmcs/Frame-7.png "Atomic design estado estudiantes")
Partiendo de un botón general y la imagen de perfil (anteriormente explicada), se construye la molécula (imagen, descripción y botón). Esta sección (organismo) muestra hasta un máximo de 4 alumnos, así que a partir del primer alumno, se maquetan del mismo modo los restantes tan solo cambiando su información. Por otra parte, dos de ellos poseen una clase adicional "hide", lo que permite mostrar u ocultar conforme el tamaño actual del viewport sin perder proporciones.

```html
<article class="student_status">
	<article class="status">
		<h4 class="m_auto">Hace 30 min</h4>
		<img src="img/avatar_3.jpg" alt="Foto perfil estudiante" class="picture_profile">
		<div class="status_information">
			<div class="status_summary">
				<h3>Anita Alvarez</h3>
				<p>1 año en el programa</p>
			</div>
			<div class="status_state">
				<h4>Estado: </h4>
				<span>Activo</span>
			</div>
		</div>
		<button class="button_modal">Revisar Dash</button>
	</article>
	<article class="status">...</article>
	<article class="status hide">...</article>
	<article class="status hide">...</article>
</article>
```

Fue preciso usar display grid para asignar proporciones (en porcentaje) a cada columna de la tarjeta, de este modo, el contenedor fluirá de un tamaño a otro siempre manteniendo las proporciones adecuadas. 
```css
/*Tarjeta de alumno*/
.student_status .status{
    display: grid;
    grid-template-columns: 28% 22% 50%;
    align-items: center;
    gap:10px ;
    margin: 15px;
    line-height: 1.5;
}
```

En cuanto a los elementos que se muestran y/u ocultan, para ello fue necesario implementar mediasqueries, una para cada elemento, ya que aparecen en diferentes momentos. Para no saturar de clases y tener distinción de un elemento a otro, se usó la pseudoclase ":last-of-type", para distinguir el último elemento con la misma clase.
```css
@media (min-width:768px){
	.student_status .hide{
			display: grid;
	}
}

@media (min-width:1024px){
	.student_status .hide:last-of-type{
			display: grid;
	}
}
```
## Tarjeta de progreso del diplomado
[![Atomic design progreso](https://i.postimg.cc/Zn9y4ngV/Frame-4.png "Atomic design progreso")](http://https://i.postimg.cc/Zn9y4ngV/Frame-4.png "Atomic design progreso")

Cada hojita (átomo) no es más que un contenedor vacío, con otro en su interior de características similares. Al estar lista la primera, las otras fueron réplicas de esta, cambiando únicamente la clase que correspondería al color específico de cada una.

```html
<article class="card-progress">
	<div class="leaf-progress">
		<div class="container-leaf">
			<div class="leaf green-darker"></div>
			<div class="leaf leaf-small"></div>
		</div>
		<div class="container-leaf">
			<div class="leaf green-medium"></div>...
		</div>
		<div class="container-leaf">
			<div class="leaf green-light"></div>...
		</div>
		<div class="container-leaf">
			<div class="leaf gray"></div>...
		</div>
		...
	</div>
</article>
```

Retomando lo anteriormente dicho, todas las hojas contienen unas propiedades y valores iguales, a grandes rasgos no es más que un cuadrado, con bordes redondeados y una rotación del mismo para dar ese efecto de rombo-hojita. En cuanto a las pequeñas hojitas en su interior, poseen una clase adicional para establecer aquellos valores diferentes (altura, color y tamaño del bordeado).
```css
/*Todas las hojas*/
.leaf {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%) rotate(-45deg);
    width: 50px;
    height: 50px;
    background: #000000;
    border-radius: 0 30px 0 30px;
    border: 2px solid var(--white);
}

/*hojas pequeñas*/
.leaf-small {
    background: rgb(255, 255, 255);
    width: 28px;
    height: 28px;
    border-radius: 0 20px 0 20px;
}
```

## Modal
> Se accede a él mediante el enlace en la tarjeta del estudiante que referencia la seeción del modal.
```html
<a href="#modal">Ver perfil completo</a>
```
[![Modal](https://i.postimg.cc/sgRfvXKD/image.png "Modal")](http://https://i.postimg.cc/sgRfvXKD/image.png "Modal")

> Se cierra a través de la x puesta como enlace en la cabecera del modal.
```html
<a href="#card_student" class="modalClose"><strong>x</strong></a>
```

En cuanto al modal, resulta ser una modificación de la tarjeta del estudiante, en la que se añaden unos datos extra, pero se mantiene su estructura base.
```html
<section id="modal" class="modal">
    <div class="modal_container">
        <div class="modal_header">
		<a href="#card_student" class="modalClose"><strong>x</strong></a>
	</div>
	<div class="modal_content card_student">...
		<div class="program_information">...</div>
		<button class="button_modal">Revisar Dash</button>
		<div class="other_students">
			<img src="img/avatar_1.jpg" alt="Estudiante 1">...
			<div class="layer_text">+12</div>
		</div>
	</div>
    </div>
</section>
```

Fue útil aquí usar la pseudoclase ":target" para determinar en qué momento el modal debe hacerse visible cambiando no solo su opacidad, sino convirtiéndose además en objetivo del puntero. El modal siempre permanece ahí, pero solo hasta que se pulse sobre el enlace, éste podra hacerse visible.

```css
.modal{
    position: fixed;
    z-index: 100;
    display: flex;
    --opacity:0;
    --pointer:none;

    opacity:var(--opacity);

    pointer-events: var(--pointer);
    transition: opacity 0.5s;
}

.modal:target{
    --opacity:1;
    --pointer:unset;
}
```

## Indicador de riesgos
[![Indicador de riesgos](https://i.postimg.cc/fLwJkv7K/Group-232.png "Indicador de riesgos")](http://https://i.postimg.cc/fLwJkv7K/Group-232.png "Indicador de riesgos")

Para esta sección se tiene un circulo base el cual es el indicador de colores, dentro otro contenedor circular que contiene el puntero. Y finalmente la sección de los emojis, los cuales siguen una misma estructura (Carita, ojos, boca)

```html
<div class="graphic-progress">
    <div class="circle">
        <div class="pointer"></div>
        <div class="triangle-pointer"></div>
    </div>
</div>
<article class="emojis-progress">
    <div class="emoji">
         <div class="eyes"><p>></p><p><</p></div>
               <div class="emoji-mouth">
                    <div id="a"></div>
                    <div id="b"></div>
                    <div id="c"></div>
                    <div id="d"></div>
                    <div id="e"></div>
               </div>
        </div>
        <div class="emoji happy">
               <div class="eyes"><p></p><p></p></div>
               <div class="emoji-mouth m-auto"> </div>
        </div>
        <div class="emoji superhappy">
               <div class="eyes"><p></p><p></p></div>
         <div class="emoji-mouth m-auto"> 
        </div>
     </div>
</article>
```

En cuanto al indicador de colores, se usó un "conic-gradient", con el cual, como su nombre lo indica, distribuye los colores en forma de cono, tomando en cuanto el grado que se les asigne. Importante aquí establecer para un mismo color, el ángulo de inicio y de finzalización para que logre un corte recto, de lo contrario mezclará los colores entre si generando un efecto degradé. Debido a que comienza a agregar colores desde un ángulo específico, se optó por rotar el circulo para lograr la posición adecuada.

```css
.graphic-progress{
    height: 110px;
    width: 110px;
    background: conic-gradient(#F95661 0deg, #F95661 36deg, #F8834E 36deg, #F8834E 72deg, #FBCE3E 72deg, #FBCE3E 108deg, #9ED77A 108deg, #9ED77A 144deg, #6AC96C 144deg, #6AC96C 180deg, white 180deg);
    transform: rotate(270deg);
    border-radius:0 50% 50% 0;
    border-top: 0;
    display: flex;
    align-items: center;
    justify-content: center;
}
```

Respecto al puntero, este es una composición de un círculo y un triángulo (Creado a partir de bordes), los cuales se ajustan a través de position absolute en su contenedor padre.

```css
.graphic-progress .pointer{
    height: 25px;
    width: 25px;
    border-radius: var(--border-circular);
    background: #868686;
    z-index: 1;
}

.triangle-pointer{
    width: 0; 
    height: 0; 
    border-left: 25px solid #000000;
    border-top: 12.5px solid transparent;
    border-bottom: 12.5px solid transparent; 
    position: absolute;
    right: 15px;
}
```
#Documentacion menú lateral y footer

Está es la documentación de la estructura de los elementos menú lateral y footer.

#Menu lateral
Se inicia creado la estructura html , usando metodologías grid para el posterior manejo de responsive

