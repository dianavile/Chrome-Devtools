# Chrome-Devtools
How to debug Javascript in Chrome Devtools
![Breakpoint types](https://github.com/dianavile/Chrome-Devtools/blob/main/0Breakpoint-types.JPG)

## 1 To set a line-of-code breakpoint in DevTools:
- 1 Click the Sources tab.
- 2 Open the file containing the line of code you want to break on.
- 3 Go the line of code.
- 4 To the left of the line of code is the line number column. Click on it. A blue icon appears on top of the line number column.
![Add breakpoint](https://github.com/dianavile/Chrome-Devtools/blob/main/1breakpoint.png)
OR 
Call debugger from your code to pause on that line. 
```
console.log('a');
console.log('b');
debugger;
console.log('c');
```

## 2 Conditional line-of-code breakpoints
Use a conditional line-of-code breakpoint when you know the exact region of code that you need to investigate, but you want to pause only when some other condition is true.

- 1 Click the Sources tab.
- 2 Open the file containing the line of code you want to break on.
- 3 Go the line of code.
- 4 To the left of the line of code is the line number column. Right-click it.
- 5 Select Add conditional breakpoint. A dialog displays underneath the line of code.
- 6 Enter your condition in the dialog.
- 7 Press Enter to activate the breakpoint. An orange icon appears on top of the line number column.
![]()

## 3 Manage line-of-code breakpoints
Use the Breakpoints pane to disable or remove line-of-code breakpoints from a single location.

- 1 Check the checkbox next to an entry to disable that breakpoint.
- 2 Right-click an entry to remove that breakpoint.
- 3 Right-click anywhere in the Breakpoints pane to deactivate all breakpoints, disable all breakpoints, or remove all breakpoints. 
    Disabling all breakpoints is equivalent to unchecking each one. Deactivating all breakpoints instructs DevTools to ignore all line-of-code breakpoints,
    but to also maintain preserve their enabled state so that they are in the same state as before when you reactivate them.
![]()

## 4 DOM change breakpoints
Use a DOM change breakpoint when you want to pause on the code that changes a DOM node or its children.

- 1 Click the Elements tab.
- 2 Go the element that you want to set the breakpoint on.
- 3 Right-click the element.
- 4 Hover over Break on then select Subtree modifications, Attribute modifications, or Node removal.
![]()

## Types of DOM change breakpoints
- Subtree modifications. Triggered when a child of the currently-selected node is removed or added, or the contents of a child are changed. Not triggered on child node attribute changes, or on any changes to the currently-selected node.
- Attributes modifications: Triggered when an attribute is added or removed on the currently-selected node, or when an attribute value changes.
- Node Removal: Triggered when the currently-selected node is removed.

## 5 XHR/Fetch breakpoints
Use an XHR breakpoint when you want to break when the request URL of an XHR contains a specified string. DevTools pauses on the line of code where the XHR calls send(). This feature also works with Fetch requests.
One example of when this is helpful is when you see that your page is requesting an incorrect URL, and you want to quickly find the AJAX or Fetch source code that is causing the incorrect request.

- 1 Click the Sources tab.
- 2 Expand the XHR Breakpoints pane.
- 3 Click Add breakpoint.
- 4 Enter the string which you want to break on. DevTools pauses when this string is present anywhere in an XHR's request URL.
- 5 Press Enter to confirm.
![]()

## 6 Event listener breakpoints 
Use event listener breakpoints when you want to pause on the event listener code that runs after an event is fired. You can select specific events, such as click, or categories of events, such as all mouse events.

- 1 Click the Sources tab.
- 2 Expand the Event Listener Breakpoints pane. DevTools shows a list of event categories, such as Animation.
- 3 Check one of these categories to pause whenever any event from that category is fired, or expand the category and check a specific event.
![]()

## 7 Exception breakpoints
Use exception breakpoints when you want to pause on the line of code that's throwing a caught or uncaught exception.

- 1 Click the Sources tab.
- 2 Click Pause on exceptions Pause on exceptions. It turns blue when enabled.
- 3 (Optional) Check the Pause On Caught Exceptions checkbox if you also want to pause on caught exceptions, in addition to uncaught ones.
![]()

## 8 Function breakpoints
Call debug(functionName), where functionName is the function you want to debug, when you want to pause whenever a specific function is called. You can insert debug() into your code (like a console.log() statement) or call it from the DevTools Console. debug() is equivalent to setting a line-of-code breakpoint on the first line of the function.
```
function sum(a, b) {
  let result = a + b; // DevTools pauses on this line.
  return result;
}
debug(sum); // Pass the function object, not a string.
sum();
```
## Make sure the target function is in scope
DevTools throws a ReferenceError if the function you want to debug is not in scope.
```
(function () {
  function hey() {
    console.log('hey');
  }
  function yo() {
    console.log('yo');
  }
  debug(yo); // This works.
  yo();
})();
debug(hey); // This doesn't work. hey() is out of scope.
```
![]()

Ensuring the target function is in scope can be tricky if you're calling debug() from the DevTools Console. 
Here's one strategy:

- 1 Set a line-of-code breakpoint somewhere where the function is in scope.
- 2 Trigger the breakpoint.
- 3 Call debug() in the DevTools Console while the code is still paused on your line-of-code breakpoint.

### Resources Chrome-Devtools

- [Chrome Devtools](https://www.youtube.com/watch?v=H0XScE08hy8)
- [Demo](https://googlechrome.github.io/devtools-samples/debug-js/get-started)
- [Chrome Devtools-DOCUMENTATION](https://developers.google.com/web/tools/chrome-devtools/javascript/breakpoints)
- [Chrome Devtools-Debug Javascript](https://developers.google.com/web/tools/chrome-devtools/javascript/reference)

