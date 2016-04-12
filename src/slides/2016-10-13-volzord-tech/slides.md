name: title
layout: true
class: template-base, template-title

---
name: slide
layout: true
class: template-base, template-slide

---
template: title
class: template-title-coffee

# VOLZORD
## Sous le capot du Framework-UI

13/10/2016

**Antonin Messinger** et **Guillaume Gérard**

---
template: title
class: template-title-transition

# Recherche

---
template: slide

# Recherche
## Objectifs

- ### Être consistant

  * Lisible pour les utilisateurs (API publique consistante)
  * Lisible pour les contributeurs (Guidelines)


--

- ### Maintenable

  * Gestion des dépendances (bye bye jQuery 1.6)
  * Tests pour éviter que @GreatWizard ne casse le code d'@amessinger ![icon-32](img/troll.png)


--

- ### Automate all the things

  * Documentation déployée automatiquement
  * Release sans les mains (ou presque)
  * Ce que la machine peut faire, la machine doit le faire !

---
template: slide

# Recherche
## État des lieux

- ### Bootstrap2, Bootstrap3, code custom


--

- ### SASS, LESS, compass, CSS


--

- ### jQuery chargé plusieurs fois sur la même page


--

- ### peopledoc-sites VS peopletheme VS applications

---
template: slide

# Recherche
## Tests

- ### Frameworks existants

  * Bootstrap, Foundation, Material Lite ont été évalués
  * Nous nous retrouvions à lutter contre ces frameworks, hello Bourbon !


--

- ### Méthodologies pour le markup

  * BEM, OOCSS, RSCSS
  * BEM est verbeux mais la quantité d'écrits présents sur les internets nous ont permis de mieux répondre à nos interrogations

---
template: slide

# Recherche
## Tests

- ### Tooling

  - SASS > LESS, techniquement satisfaisants, départagés par la force de leurs communautées
  - Syntaxe ES6 pour Javascript, parce que plaisant à écrire, transpilable de manière satisfaisante en ES5
  - Broccoli car ember-cli est basé dessus, offre de bonne performances même avec des milliers de fichiers en sources
  - QUnit, toujours parce que proche d'Ember !
  - Nightwatch pour les tests visuels, parce qu'il n'y a pas trop d'alternatives (pour l'instant)
  - Browserstack, évidemment.
  - CircleCI car rien à maintenir, setup les doigts dans le nez, FREE !

---
template: title
class: template-title-transition

# Développement

---
template: slide

# Développement
## Milestones

- ### Milestone des grandes étapes:

  - ### 1. (Janvier) Tooling et identité visuelle
  - ### 2. (Fevrier) Composants bas-niveau
  - ### 3. (Mars-Avril) Composants haut-niveau
  - ### 4. (Mai) Layouts
  - ### 5. (Mai-Juin) Theme et polish
  - ### 6. (Juin) Packaging et documentation

---
template: slide

# Développement
## Workflow

- ### 1. Ticket


- ### 2. Pull-Request


- ### 3. Review


--


- ### Refactor pour harmoniser le code

---
template: slide

# Développement
## SCSS -> CSS

- ### Linting avec **sass-lint**


--

- ### Compilation avec **sass**


--

- ### Prefixing avec **autoprefixer**
  (IE9, IE10, IE11 + 2 dernières versions des browsers modernes)

---
template: slide

# Développement
## JavaScript

- ### Linting avec **jscs** et **jshint**


--

- ### Transpiling avec **Babel** (ES6 -> ES5)
  - Les mot-clés let et const
  - Template String
  - Paramètres par défaut
  - Fonctions Arrow (lambda)
  - Classes et Héritages

---
template: slide

# Développement
## Documentation

- ### Utilisation de Styledown


--

- ### Markdown


--

- ### Documentation inline SCSS (devs et docs)


--

- ### Documentation dans des fichiers markdown

---
template: slide

# Développement
## Tests unitaires

- ### Utilisation de **QUnit**


--

- ### Test de chaque composant par l'API


--

- ### Test de chaque composant par l'interface (click, hover...)


--

- ### Test de l'écoute des events


--

- ### CircleCI

---
template: slide

# Développement
## Tests unitaires

```javascript
/* global QUnit */
const { test, module } = QUnit;

module('Unit | Block | Dropdown');

const dropdownTemplate = '<div class="dropdown">...<div>';

test('dropdown should be openable', function(assert) {
  assert.expect(4);
  const $dropdown = $(dropdownTemplate);
  const $button = $dropdown.find('[data-toggle="dropdown"]');
  const $body = $dropdown.find('.dropdown__body');
  assert.notOk($button.hasClass('button--pressed'), 
  $dropdown.appendTo('#qunit-fixture');'button is pressed');
  assert.notOk($body.is(':visible'), 'body is visible');
  $button.click();
  assert.ok($button.hasClass('button--pressed'), 'button is not pressed');
  assert.ok($body.is(':visible'), 'body is not visible');
});
```

---
template: slide

# Développement
## Tests visuels

![full-screen](slides/2016-10-13-volzord-tech/visual-testing.jpg)

---
template: title
class: template-title-transition

# Utilisation

---
template: slide

# Utilisation

```scss
// B(lock)E(lement)M(modifier)
// Un block est un composant
.modal

// Un element est une partie de ce composant
.modal__header

// Un modifier est un état particulier d'un block ou d'un élément
.modal--danger
.modal__header--dimmed

// Les elements n'ont pas de parentée
.modal__header__close-button // INVALIDE

// Un element peut en inclure un autre
.modal__header .modal__close-button

// Un block peut être inclus dans un autre block
.modal .button

// Un block inclus peut être modifié dans le contexte de son parent (mixie)
.modal .button.modal__button
```

---
template: slide

# Utilisation
## Plugins

### Via markup

```html
* <div class="alert alert--hidden" data-autoclose>
  <div class="alert__close-button button">
    <svg class="icon button__icon">
      <use xlink:href="../icons.svg#cross">
      </use>
    </svg>
  </div>
  <p>Alert auto-close</p>
</div>
```

---
template: slide

# Utilisation
## Plugins

### Via javascript

```html
* <div class="alert alert--hidden">
  <div class="alert__close-button button">
    <svg class="icon button__icon">
      <use xlink:href="../icons.svg#cross">
      </use>
    </svg>
  </div>
  <p>Ecrire votre message ici!</p>
</div>

*$('.alert').alert('open', options)

// options = {
//   isAutoclose: false, // boolean, optional
//   delay: 2            // integer, unit in seconds, optional
// }
```

---
template: title
class: template-title-desk

# Questions ?
## Merci à vous!


Prochaine présention ?
- Live coding: Ajout d'un composant (SCSS, JS et Tests)
- ...?
