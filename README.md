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

[![Atomic design progreso](https://i.postimg.cc/Zn9y4ngV/Frame-4.png "Atomic design progreso")](http://https://i.postimg.cc/Zn9y4ngV/Frame-4.png "Atomic design progreso")

[![Atomic design barra de progreso circular](https://i.postimg.cc/MT3jCVsn/Frame-5.png "Atomic design barra de progreso circular")](http://https://i.postimg.cc/MT3jCVsn/Frame-5.png "Atomic design barra de progreso circular")
