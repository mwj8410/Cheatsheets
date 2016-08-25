# Protractor

## Browser Control

## DOM and HTML

Retrieve an element's DOM structure
```
element(by.css('css-selector'))
  .getOuterHtml()
  .then(html => {
    console.log(html);
  });
```
