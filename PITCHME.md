---

# Using React with BEM

---

## BEM

* `block__element--modifier`
* `class="my-block"`
* `class="my-block__my-element"`
* `class="my-block__my-element my-block__my-element--my-modifier"`
* `class="my-block__my-element my-block__my-element--my-modifier my-block__my-element--another-modifier"`

---

## BEM with React (our standard)

* A React component is a Block
* An element inside is an Element
* Variations on Blocks or Elements are Modifiers

---

```js
const Page1 = ({history: {push}}) => (
  <div className="react-app-page-1--some-modifier">
    <h1 className="react-app-page-1__heading react-app-page-1__heading--another-modifier">
      Page 1
    </h1>
    <button
      className="react-app-page-1__button react-app-page-1__button--my-modifier react-app-page-1__button--another-modifier"
      onClick={() => push(absoluteRoutePath(RoutePath.PAGE_2))}
    >
      Next page
    </button>
  </div>
);
```

---

## We can do better than this

`className="react-app-page-1__button react-app-page-1__button--my-modifier react-app-page-1__button--another-modifier"`

---

```js
const bem = bemForBlock('page-1');

const Page1 = ({history: {push}}) => (
  <div className={bem(null, {'some-modifier': true})}>
    <h1 className={bem('heading', 'another-modifier')}>
      Page 1
    </h1>
    <button
      className={bem('button', {'my-modifier': true, 'another-modifier': true})}
      onClick={() => push(absoluteRoutePath(RoutePath.PAGE_2))}
    >
      Next page
    </button>
  </div>
);
```

---

## SCSS

```scss
.react-app { // Namespace
  .page-1 { // Block
    // block rules...
    
    &--some-modifier { // Modifier
      // modifier rules...
    }
    
    &__heading { // Element
      // element rules...
      
      &--another-modifier { // Modifier
        // modifier rules...
      }
    }
    
    &__button { // Element
      // element rules...
      
      &--some-modifier { // Modifier
        // modifier rules...
      }
      
      &--another-modifier { // Modifier
        // modifier rules...
      }
    }
  }
}
```

---

## Thanks!
