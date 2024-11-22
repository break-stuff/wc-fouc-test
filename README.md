# Web Component FOUC Test

The purpose of this project is to demonstrate a method to reduce "flash of unstyled content" (FOUC) when loading custom elements. These are [Shoelace](https://shoelace.style/) web components that are lazy-loaded from a CDN to increase the dramatic effect of the FOUC. This should be more apparent than if the components were imported directly locally on the site.

The following lines of code are what are bing test:

```html
<style>
  body:not(.wc-loaded) {
    opacity: 0;
  }
</style>

<script>
  (() => {
    Promise.allSettled(
      [...document.querySelectorAll(":not(:defined)")].map((component) =>
        customElements.whenDefined(component)
      )
    ).then(() => {
      setTimeout(() => document.body.classList.add("wc-loaded"), 200);
    });
  })();
</script>
```

The project can be viewed here - https://break-stuff.github.io/wc-fouc-test/.

## Running the project locally

To run this locally you should be able to run the following command or you can open the `.html` files directly in your browser.

```bash
npm i && npm start
```
