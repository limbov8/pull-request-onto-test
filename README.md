# pull-request-onto-test

## Stores
Stores can be found in any Flux architecture and can be compared a bit with controllers in the MVC pattern. The main responsibility of stores is to move logic and state out of your components into a standalone testable unit that can be used in both frontend and backend JavaScript.

### Stores for the user interface state
Most applications benefit from having at least two stores. One for the UI state and one or more for the domain state. The advantage of separating those two is you can reuse and test domain state universally, and you might very well reuse it in other applications. The ui-state-store however is often very specific for your application. But usually very simple as well. This store typically doesn't have much logic in it, but will store a plethora of loosely coupled pieces of information about the UI. This is ideal as most applications will change the UI state often during the development process.

Things you will typically find in UI stores:

### Session information
Information about how far your application has loaded
Information that will not be stored in the backend
Information that affects the UI globally
Window dimensions
Accessibility information
Current language
Currently active theme