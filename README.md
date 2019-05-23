# pull-request-onto-test

## Stores
Stores can be found in any Flux architecture and can be compared a bit with controllers in the MVC pattern. The main responsibility of stores is to move logic and state out of your components into a standalone testable unit that can be used in both frontend and backend JavaScript.

### Stores for the user interface state
Most applications benefit from having at least two stores. One for the UI state and one or more for the domain state. The advantage of separating those two is you can reuse and test domain state universally, and you might very well reuse it in other applications. The ui-state-store however is often very specific for your application. But usually very simple as well. This store typically doesn't have much logic in it, but will store a plethora of loosely coupled pieces of information about the UI. This is ideal as most applications will change the UI state often during the development process.

Things you will typically find in UI stores:

### Session information
- Information about how far your application has loaded
- Information that will not be stored in the backend
- Information that affects the UI globally
- Window dimensions
- Accessibility information
- Current language
- Currently active theme




## Domain Stores
Your application will contain one or multiple domain stores. These stores store the data your application is all about. Todo items, users, books, movies, orders, you name it. Your application will most probably have at least one domain store.

A single domain store should be responsible for a single concept in your application. However a single concept might take the form of multiple subtypes and it is often a (cyclic) tree structure. For example: one domain store for your products, and one for your orders and orderlines. As a rule of thumb: if the nature of the relationship between two items is containment, they should typically be in the same store. So a store just manages domain objects.

These are the responsibilities of a store:

- Instantiate domain objects. Make sure domain objects know the store they belong to.
- Make sure there is only one instance of each of your domain objects. The same user, order or todo should not be stored twice in memory. This way you can safely use references and also be sure you are looking at the latest instance, without ever having to resolve a reference. This is fast, straightforward and convenient when debugging.
- Provide backend integration. Store data when needed.
- Update existing instances if updates are received from the backend.
- Provide a stand-alone, universal, testable component of your application.
- To make sure your store is testable and can be run server-side, you probably will move doing actual websocket / http requests to a separate object so that you can abstract over your communication layer.
- There should be only one instance of a store.