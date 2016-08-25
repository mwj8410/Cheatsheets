# Protractor

## Browser Control

Wait for condition. This is very useful when navigating between views or allowing the view to update with API interaction.

```
browser.wait(
  () => element(by.css('css-selector')).isPresent()
);
```

Reload
```
browser.driver.navigate().refresh();
```

Sleep for an amount of time
```
browser.driver.sleep(10000);
```

Scroll control
```
browser.executeScript('window.scrollTo(0,500);');
```
This is needed when interacting with elements that my be covered up by other elements that are shown on scroll events. `ele.click()` will automatically scroll the elemnt into view the viewport, but will not take into account elements shown based on the scroll action. There does need to some clerification on how to get the location of an element in total page space. `.getLocation()` is not useful for this.

## DOM and HTML

Retrieve an element's DOM structure
```
element(by.css('css-selector'))
  .getOuterHtml()
  .then(html => {
    console.log(html);
  });
```

## Element properties

Get element's location in the active viewport. This is different than the element's location in page space.
```
element(by.css('css-selector'))
  .getLocation();
```
