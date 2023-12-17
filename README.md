# HTMX basic

Test de <a href="https://htmx.org/" target="_blank">HTMX</a> pour un comportement de type SPA avec chargement de contenu, mise à jour de l'url et gestion de l'historique des urls.

## Description

Les pages (index.html, page1.html, ...) ne contiennent pas de contenu, seulement le squelette de base d'une page HTML5 ainsi qu'un menu et une div vide servant à accueillir du contenu.

Le contenu est dans les fichiers /content/contentX.html.

Ce contenu est chargé dans les pages de 2 manières :
1. Lorsque l'on saisi l'url d'une page, ou que l'on rafraichi une page (cad qu'on y accès d'une autre manière que par le menu), le contenu est chargé avec `<div hx-get="/content/content1.html" hx-trigger="load" hx-swap="outerDiv settle:0.3s"></div>` :
    - **hx-get** indique quel contenu requêté
    - **hx-trigger="load"** indique de récupérer ce contenu au chargement de la page
    - **hx-swap="outerDiv settle:0.3s"** indique de remplacer la div courante par le contenu récupéré, et de mettre une class de chargement (.htmx-added) pendant 0.3s (Voir la <a href="https://htmx.org/examples/animations/#fade-in-on-addition" target="_blank">doc</a>)
2. Lorsqu'on affiche une page via un clic dans le menu, le contenu est chargé avec `<a hx-get="/content/content2.html" hx-push-url="/page2.html" hx-target="#content" hx-swap="innerHTML swap:0.3s settle:0.3s" class="nav-link" aria-current="page">Page 2</a>` :
    -  **hx-get** indique quel contenu requêté
    -  **hx-target="#content"** indique dans quelle div inséré ce contenu récupéré
    -  **hx-swap="innerHTML swap:0.3s settle:0.3s"** indique d'insérer le contenu dans la div courant (et non de la remplacer), de mettre une class de chargement pendant 0.3s et une class de "déchargement" (.htmx-swapping) pendant 0.3s (Voir la <a href="https://htmx.org/examples/animations/#fade-out-on-swap" target="_blank">doc</a>)