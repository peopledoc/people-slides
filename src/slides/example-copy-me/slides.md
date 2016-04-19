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

# Your presentation title
## Your presentation subtitle

dd/mm/yyyy

**Your name**

---
template: title
class: template-title-teamwork

# A different title slide
## Your presentation subtitle

dd/mm/yyyy

**Your name**

---
template: title
class: template-title-desk

# A third title slide
## Your presentation subtitle

dd/mm/yyyy

**Your name**

---
template: slide

# A standard slide
## With a subtitle

### Use h3s for inline headings

- And you
- can also
- use dot points

???

* You can add notes by creating a triple question mark divider
* Notes will show to you, but not your audience
* Remember, they will be committed to the repository!

---
template: title
class: template-title-transition

# A section divider
## aka - a sub title slide
---

template: slide

# A code example
## With syntax highlighting

```js
let app = MyApp.create({ autoboot: false });
  let options = {
    location: 'none',
    rootElement: '#location',
    APP: {
*      facets: { /*...*/ }
    }
  };
  App.visit('/', options).then((/* appInstance */) => {
    console.log('Smooth');
  });
```

---
template: title
class: template-title-desk

# Closing slide
## use any title slide
