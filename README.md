# Portafolio CV - Alexis Mauriz

Este es mi portafolio profesional en línea, diseñado para mostrar mis habilidades y experiencia en desarrollo web y otros campos.

## Acerca de

Este sitio web es una representación de mi trayectoria profesional y educativa, donde encontrarás información sobre los servicios que ofrezco, ejemplos de mis trabajos anteriores y cómo contactarme.

## Tecnologías Utilizadas

- HTML5
- CSS3
- JavaScript
- Git
- GitHub

## Estructura del Proyecto

El proyecto sigue una estructura básica de archivos y carpetas:

- `index.html`: Página principal del sitio web.
- `style.css`: Hoja de estilos para el diseño y la presentación.
- `assets/`: Carpeta que contiene las imágenes y otros recursos utilizados en el sitio.
- `README.md`: Este archivo, proporcionando información básica sobre el proyecto.

## Instalación

1. Clona este repositorio en tu máquina local usando `git clone`.
2. Abre el archivo `index.html` en tu navegador web para visualizar el sitio.

## Contacto

Si deseas contactarme, puedes hacerlo a través de:

- Email: [maurizalexis@gmail.com](mailto:maurizalexis@gmail.com)
- LinkedIn: [Alexis Mauriz](https://www.linkedin.com/in/alexis-n%C3%A9stor-jos%C3%A9-mauriz-barros-a84088157/)

¡Gracias por visitar mi portafolio!

# Estilos CSS para Sitio Web

Este repositorio contiene estilos CSS para un sitio web. El código está organizado en diferentes secciones para estilizar componentes específicos y establecer variables globales para colores, fuentes y tamaños.

## Estructura del Código

- **Custom Properties**: Define variables globales (`--nombre-variable: valor;`) para colores, fuentes y tamaños utilizados en todo el sitio.
- **Reset**: Establece reglas generales para `html`, `body` y configuraciones de fuente predeterminadas para una experiencia consistente en navegadores.
- **Componentes**: Estilos específicos para componentes como Carruseles, Formularios de Contacto, Imágenes de Héroe, Menús, Modales y Barras de Progreso.
- **Utilidades**: Clases de utilidad para bordes, sombras, alineaciones de texto y propiedades comunes.

## Uso

- Vincula el archivo CSS a tu documento HTML: `<link rel="stylesheet" href="ruta/al/archivo.css">`.
- Aplica las clases y estilos definidos a tus elementos HTML según sea necesario.

## Personalización

- Modifica las variables CSS en `:root` para cambiar rápidamente colores, fuentes y tamaños en todo el sitio.

## Contribuciones

¡Las contribuciones son bienvenidas! Si tienes mejoras, correcciones o sugerencias, siéntete libre de abrir un issue o enviar un pull request.

## Licencia

Este código se proporciona bajo la [Licencia MIT](ruta/a/tu/licencia).

# Funcionalidades JavaScript

Este código JavaScript contiene funciones para manejar un menú y un formulario de contacto en un sitio web.

## Menú

```javascript
((d) => {
  const $btnMenu = d.querySelector(".menu-btn"),
    $menu = d.querySelector(".menu");

  $btnMenu.addEventListener("click", (e) => {
    $btnMenu.firstElementChild.classList.toggle("none");
    $btnMenu.lastElementChild.classList.toggle("none");
    $menu.classList.toggle("is-active");
  });

  d.addEventListener("click", (e) => {
    if (!e.target.matches(".menu a")) return false;

    $btnMenu.firstElementChild.classList.remove("none");
    $btnMenu.lastElementChild.classList.add("none");
    $menu.classList.remove("is-active");
  });
})(document);

((d) => {
  const $form = d.querySelector(".contact-form"),
    $loader = d.querySelector(".contact-form-loader"),
    $response = d.querySelector(".contact-form-response");

  $form.addEventListener("submit", (e) => {
    e.preventDefault();
    $loader.classList.remove("none");
    fetch("https://formsubmit.co/ajax/maurizalexis@gmail.com", {
      method: "POST",
      body: new FormData(e.target)
    })
      .then((res) => (res.ok ? res.json() : Promise.reject(res)))
      .then((json) => {
        console.log(json);
        location.hash = "#¡Muchas Gracias!";
        $form.reset();
      })
      .catch((err) => {
        console.log(err);
        let message =
          err.statusText ||
          "Ocurrió un error al enviar tu mensaje, intenta nuevamente";
        $response.querySelector(
          "h3"
        ).innerHTML = `Error ${err.status}: ${message}`;
      })
      .finally(() => {
        $loader.classList.add("none");
        setTimeout(() => {
          location.hash = "#close";
        }, 3000);
      });
  });
})(document);
```
