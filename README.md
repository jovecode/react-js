# react-js
React is a library that Facebook invented to help build custom HTML elements. 

Introduction to React js
You've heard about this UI library called React and want to see what it's about. Or maybe someone told you to come here. Either way, I'll try my best to show and teach you React.

This guide assumes some familiarity with HTML, CSS, and JavaScript. Knowing what closures are and how "this" works in JavaScript will help but you'll learn React regardless.

First off, React is not a JavaScript framework. It's simply a JavaScript library that helps you build modular UI. That's all.

No routes.

No controllers.

Just good ol' views.

React's basic philosophy is that components trigger events (e.g. after a name is input into a field). That event can then be listened to by a model. The model can then trigger an event (e.g., name updated), and then the view can respond to the model's event to re-render.

Events flow out/up, data flows in/down.

So Will It Replace Angular?

Uh, no. Comparing React to Angular is like comparing Bootstrap to Ember. Again, React is just a UI library for building components.

Since React only represents the "V"** in MVC, you could potentially use React as the view layer in Angular.

**Well, actually, some could argue that complex UI views in React also act as a "C", but this is more like the concept of a "Presenter" -- a presenter is basically a root view that controls sub views -- think of it as a "view controller".

What Are The Pros?

Data travels down. In short, this has the same benefit as dependency injection in object-oriented development.

Virtual DOM means the UI only updates when it is actually changed. This leads to super fast rendering times.

Can render a lot of frames per second

You can render your views on both the server and the client. No more rendering with PhantomJS and serving that up to search engines like you would have to do with a client-only rendering system like Angular's view layer. Yuck.

Makes modifying and reusing UI components super easy

Backed by Facebook (and powering their site), so not likely to disappear anytime soon

Even though it's still not at 1.0 release, it is already in production use by Facebook, Netflix, Airbnb, Yahoo

Big community online

As it is not a framework, it can be used with other frameworks and libraries such as Angular, jQuery, Backbone, Vue, etc

What Are The Cons?

Again, React is only concerned about the view. There is nothing related to data modelling or routing, etc. If you're looking for a golden hammer to solve all of your JavaScript woes, React is not the answer.

Because it is only concerned with the view layer, it means gluing the other parts has been a bit chaotic during early adoption. It doesn't come bundled with an event framework, so a lot of people have reinvented the wheel there.

React is a large library for not being a framework

Documentation is not the best, so the learning curve can be steep. Not something you want to roll out for a large new project -- best to start practicing with it on side projects.

The problem with trying to learn React is that there are so many other web technologies that are usually combined with it that, if you are not familiar with those technologies, you can easily get lost of all of the new and shiny

No native support for IE8 or below

React Speak

Components. Think of these as custom HTML elements.

<code>

<VideoPlayer startAtFrame="30"/>, <LikeButton likes="100"> or <Login>

</code>

Follow Single Responsibility here: each component does one thing and one thing well -- several smaller components are better than one big monolithic component

E.g. Don't build a list and the ajax call to fetch that list data in the same component -- first build the list component and then use that component inside the data fetcher. A good example of this is shown here.

Just like when refactoring functions -- if a function does more than one thing, you break it down until it does only one thing -- do this same thing with components

Props: Initialize component state

These are declarative attributes of a component. Think of these in the same way you would think of things like 'src', 'width' and 'height' on an '' element. Another way to think of this is the component's config options. This is injected into the component: "data travels down". These are immutable -- set once during initialization, and not changed. If you need to change these values, that is handled with State (see below).

Accessible via this.props in the component

E.g., if we have a "startAtFrame" variable, it would be in this.props.startAtFrame

Think of props as the "public" data that you can set

PropTypes: Allows your properties to be strictly typed.

<code>

const ListOfNumbers = props => (
 <ol className={props.className}>
   {
     props.numbers.map(number => (
       <li>{number}</li>)
     )
   }
 </ol>
);

ListOfNumbers.propTypes = {
 className: React.PropTypes.string.isRequired,
 numbers: React.PropTypes.arrayOf(React.PropTypes.number)
};
</code>

Events: used to communicate updates and changes to a component

React wraps native browser events to given them a standard interface

More info on the types of events available are available here: https://facebook.github.io/react/docs/events.html

State: Mutable data of a component.

Accessible via this.state in the component

If you "like" a photo, that photo's state now changes to "liked"

Managing state can get complicated. Rather than reinvent the wheel, it's best to start off with a community supported library, such as Redux, which was based on Facebook's Flux theory for state management. Here is a cartoon intro to Redux that helps explain it.

Think of state as "private" data that only the component can set

You will typically have a root component, such as <App>, that will act as your view presenter (or view controller). This container component manages state by pushing data down, in reaction to events that have flown up.

JSX

JSX is the part inside the render() function that looks like HTML. This was done to allow you create components in the way you would think of them like in HTML.

Some tips:

Do not use class. Instead, use className. It's because JSX gets translated to JS, and class is a keyword in the newest version of JS.

If you use <code><br></code> instead of <code><br/></code>

, it won't work. Make sure to use self-closing tags.

JSX is not required, but is widely used.

React Native

https://facebook.github.io/react-native/

Allows you to use React to build mobile apps

Redux

Redux helps to manage how components interact with one another

Components are given callback functions which are called whenever a UI Event happens

The callback functions create and dispatch Actions based on the Event

Reducers process the Actions, computing the new State

oldState + Action = newState

Components receive the new State as props and re-render if needed

Redux makes it much easier to test transitions between states

Helps to reduce framework lock-in, since all the components have to do is receive new props (data flows in) and emit events (events flow out)

Immutable.Js

This library can be used to manage state for components. It ensures that, once set, the data cannot be changed.

Some Tips

Keep components small -- follow The Single Responsibility Theory here -- just like functions and classes, you want your components to do one thing and do it really well

Easier to understand

Easier to share

Easier to reuse

<code>

const LatestPostsComponent = props => (
 <section>
   <div><h1>Latest posts</h1></div>
   <div>
     { props.posts.map(post => <PostPreview key={post.slug} post={post}/>) }
   </div>
 </section>
);

</code>


Keep components free of state unless absolutely necessary

Do not place any business logic in components. That belongs on the domain model on the server. Only rendering logic should be handled in the components.

Warning signs include:

Validation

Calculations
