// ==========================
// NAVBAR SCROLL
// ==========================

const navbar = document.querySelector(".navbar");

window.addEventListener("scroll", () => {

    if(window.scrollY > 50){

        navbar.classList.add("shadow");

    }else{

        navbar.classList.remove("shadow");

    }

});

// ==========================
// REVELAR ELEMENTOS
// ==========================

const revealElements = document.querySelectorAll(".reveal");

const observer = new IntersectionObserver(

    entries => {

        entries.forEach(entry => {

            if(entry.isIntersecting){

                entry.target.classList.add("active");

            }

        });

    },

    {
        threshold:0.15
    }

);

revealElements.forEach(el => observer.observe(el));

// ==========================
// BOTON VOLVER ARRIBA
// ==========================

const topButton = document.getElementById("btnTop");

window.addEventListener("scroll", () => {

    if(window.scrollY > 400){

        topButton.classList.add("show");

    }else{

        topButton.classList.remove("show");

    }

});

topButton.addEventListener("click", () => {

    window.scrollTo({
        top:0,
        behavior:"smooth"
    });

});

// ==========================
// SECCION ACTIVA MENU
// ==========================

const sections = document.querySelectorAll("section");
const navLinks = document.querySelectorAll(".nav-link");

window.addEventListener("scroll", () => {

    let current = "";

    sections.forEach(section => {

        const sectionTop = section.offsetTop - 150;

        if(window.scrollY >= sectionTop){

            current = section.getAttribute("id");

        }

    });

    navLinks.forEach(link => {

        link.classList.remove("active");

        if(
            link.getAttribute("href") === "#" + current
        ){
            link.classList.add("active");
        }

    });

});