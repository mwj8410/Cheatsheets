# Protractor

## Browser Control

Sleep for an amount of time
```
browser.driver.sleep(10000);
```

## DOM and HTML

Retrieve an element's DOM structure
```
element(by.css('css-selector'))
  .getOuterHtml()
  .then(html => {
    console.log(html);
  });
```
