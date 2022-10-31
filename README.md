# Fundación semillas (Dashboard)
Este proyecto contiene un Demo (MVP) del dashboard para la fundación semillas, enfocándose primordialmente en la salud emocional de los estudiantes, para lo cual se encontrarán indicadores emocionales de los mismos; siendo además de eso, una herramienta completa de visualización general del status del alumno, considerando cada una de sus actividades modulares para cada diplomado.

[![Semillas dashboard Demo](https://i.postimg.cc/SRqqZwn6/Group-231.png "Semillas dashboard Demo")](http://https://i.postimg.cc/SRqqZwn6/Group-231.png "Semillas dashboard Demo")

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

![Atomic design card estudiante](https://i.postimg.cc/PJ2pWZDX/Frame-6.png "Atomic design card estudiante")

![Atomic design estado estudiantes](https://i.postimg.cc/zDjgYmcs/Frame-7.png "Atomic design estado estudiantes")

[![Atomic design progreso](https://i.postimg.cc/Zn9y4ngV/Frame-4.png "Atomic design progreso")](http://https://i.postimg.cc/Zn9y4ngV/Frame-4.png "Atomic design progreso")

[![Atomic design barra de progreso circular](https://i.postimg.cc/MT3jCVsn/Frame-5.png "Atomic design barra de progreso circular")](http://https://i.postimg.cc/MT3jCVsn/Frame-5.png "Atomic design barra de progreso circular")
