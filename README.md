# Alura Books

Development of a responsive home page for Alura Books (which is in Portuguese) and a form page with autofill for address inputs when a valid ZIP Code is typed.

| :placard: Vitrine.Dev |     |
| -------------  | --- |
| :sparkles: Nome        | **Alura Books**
| :label: Tecnologias | HTML, CSS, JavaScript
| :rocket: URL         | https://zingarelli.github.io/alura-books/
| :fire: Course     | https://www.alura.com.br/curso-online-html-css-responsividade-mobile-first

<!-- Inserir imagem com a #vitrinedev ao final do link -->
![](https://user-images.githubusercontent.com/19349339/191834081-b8b3c1b2-368d-4763-a28a-cb14f1f25686.png#vitrinedev)

## Project Details

The **home page** was created using a **"Mobile First"** approach, in which we first created the layout for smaller screens (up to 428 pixels) and then adapted the layout for larger screens (1024 and 1728 pixels). The design was [provided in a Figma file](https://www.figma.com/file/sSMbIqKaGBd66Y8roxTk2p/AluraBooks?node-id=37%3A94). 

For the **form page**, HTML and CSS files were already provided, with the page being composed of several inputs for a customer to fill in his/her personal data (name, contact, address, etc.) The focus here was to work with **JavaScript** to autofill some of these inputs, by **fetching data from an API**. When the user types his/her ZIP Code (CEP in portuguese), we use an API called *viaCEP* to fetch data regarding the address for that ZIP code (or an error if the code is invalid or is a non-existent address). We then use this data to automatically fill the appropriate inputs (address, district, city and state) or show the user an error message.

## Credits

This project was developed in two courses from [Alura](https://www.alura.com.br):

- "HTML e CSS: responsividade com mobile-first" (HTML and CSS: mobile-first responsive design);
- "JavaScript: consumindo e tratando dados de uma API" (JavaScript: consuming and dealing with data from an API).

**Instructor: [Mônica Mazzochi Hillman](https://github.com/MonicaHillman)**

## How the project was developed

### Responsive home page

The home page was developed with a "mobile-first approach", which means that we structured HTML and CSS files in order to adapt the layout to a small screen and then proceeded to larger screens, where more space is available to position elements of even add new ones. In order to do that, we used "media queries":

```css
@media screen and (min-width: 1024px){ ... }
@media screen and (min-width: 1728px){ ... }
```

Since the home page has a lot of sections, CSS was split into several files, one for each section, for a better organization. These files were imported to a "main" CSS file, called `styles.css`, using the `@import` statement:

```css
@import url('styles/header.css');
@import url('styles/banner.css');
@import url('styles/carousel.css');
/* and so on */
```

We defined variables in the `styles.css` file for colors and fonts used, preventing repetition and favouring reuse and maintenance of our code. Whenever a change in color or font needs to be applied, we only modify these variables. For example:

```css
--light-grey: #858585;
--gradient-blue: linear-gradient(97.54deg, #002F52 35.49%, #326589 165.37%);
--main-font: 'Poppins';
```

There's a submenu that is shown only when the user touches/clicks a button (an "hamburger" icon for smaller screens or a nav button for largers screens). We used only HTML and CSS to enable this interaction (by using a checkbox input, CSS selectors and the `display` property). This can be checked in the `header.css` file. Here's an animation of this interaction:

![gif showing a submenu appearing when an icon is touched](https://user-images.githubusercontent.com/19349339/191840550-8d416861-8c70-479b-976b-0751b2587588.gif)

The home page has two sections showing book covers, using a "carousel style" effect. For that, we used [Swiper](https://swiperjs.com), a free JavaScript plugin. We learned the basics to configuring it and then styled it using CSS. The next animation shows the Swiper in action:

![gif showing the usage of Swiper](https://user-images.githubusercontent.com/19349339/191842107-26dc4d92-386c-4d5e-aed5-d2b02c016e60.gif)

We also learned how to use advanced selectors (`~` and `>`),  pseudoclasses (`:hover` and `:checked`) and pseudoelements (`::placeholder`) to add more style options to the layout.

### Autofill in form page

The form page can be accessed using this link: https://zingarelli.github.io/alura-books/form.html. 

For the form page, we focused on JavaScript and learned how to fetch and use data from an API. When the user types a ZIP Code (CEP in portuguese), we send that code to an API called ["viaCEP"](https://viacep.com.br), which returns data regarding the address for that code (or an error if the code is invalid or if it is a non-existent address). We then use this data to automatically fill the appropriate inputs (address, district, city and state). If an error is returned, a message is show right below the ZIP Code's input, informing the user to check if the code is correct.

The animation below shows the user typing valid and invalid ZIP codes:

![gif showing using typing a valid and then an invalid ZIP code](https://user-images.githubusercontent.com/19349339/191845910-dd756ccb-3bb6-4330-9d87-4229db96e8e8.gif)

During the development of this page, we learned several JavaScript topics:

- we learned how asynchronous JavaScript works;
- we used `fetch()` method to retrieve data from an API and learned the concept behind "promises" (the object returned by asynchronous functions);
- we learned how to work with promises using methods such as: `json()`, `then()`, `catch()`, `finally` and `Promise.all()`;
- we learned how to create asynchronous functions using keywords `async` and `await`;
- we manipulated the DOM using methods like `getElementById()` and `addEventListener()`;
- we modified values in the HTML file using the `innerText` and `value` properties.