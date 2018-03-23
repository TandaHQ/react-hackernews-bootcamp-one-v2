---
path: "/chapters/views"
date: "2018-03-22"
title: "Views"
index: 4
---

# Views

So far we have learned JSX, how to create a component and how to write modular components with modular styles. Now we are going to put our first view together. While a component should be versatile in usage, a view is a specific arrangement of components for a user interface.

# A Simple View

Guess how we define a view in react? It's really just a component! We just acknowledge them differently as they serve a different purpose. To use the hackernews app as an example, our news feed is a view.


       Article (Component)           |         News Feed (View)
                                     |
                                     |         -----------------
                                     |         |               |
       ---------------------         |         |               |
       |                   |         |         -----------------
       |                   |         |         |               |
       |                   |         |         |               |
       |                   |         |         -----------------
       ---------------------         |         |               |
                                     |         |               |
                                     |         -----------------
                                     |

## Excercise

In our `source/index.jsx`, let's try make a `NewsFeed` view which takes the data in the snippet below and renders three `Article` components inside a div.

```js
// our fake articles from hackernews
const ARTICLES = [
  {
    by: 'Annie A',
    id: 1,
    title: 'Some Cool Techy Stuff',
    url: 'https://google.com',
  },
  {
    by: 'Diddy P',
    id: 2,
    title: 'Digital Rap',
    urk: 'https://google.com',
  },
  {
    by: 'Hoolio H',
    id: 3,
    title: 'Yeh Cool Keen',
    url: 'https://google.com',
  },
];

// lets pass the values in `ARTICLES` to our `NewsFeed` like so:
//
// eg.
//   <NewsFeed
//     article1={ARTICLES[0]}
//     article2={ARTICLES[1]}
//     article3={ARTICLES[2]}
//   />
//
```

## A List View
Commonly in a user interface we have to represent a list of things that we may not know the length of until compute time. For example if we are trying to display all the articles from hacker news for a specific week, the list of articles may vary in length. How do we do this then? The answer lies in Array#map.

### Mapping
If we have an array of values such as `[1, 2, 3]` and wanted to double them, we can map them like so:

```js
const numbers = [1, 2, 3]

const doubles = numbers.map(value => value * 2)

// [2, 4, 6]
```

If we wanted to change there type we can still use map:

```js
const numbers = [1, 2, 3]

const strings = numbers.map(value => value.toString())

// ['1', '2', '3']
```

Finally, if we wanted to make them into components:

```js
const numbers = [1, 2, 3]

const components = numbers.map(value => (
  <span key={value}>
    {value}
  </span>
))

// [<span>1</span>, <span>2</span>, <span>3</span>]
```

Yup thats right we can map to react elements just like they were any other value!

### The Catch

You will notice in the example mapping numbers to react components, I have assigned the value to a property on the span called `key`. Why is this?

It is because when our list gets rendered time and time again, react needs to be able to tell which component are the same as last render. The key you provide should be unique to the value the component is representing. To use the hackernews feed as an example, if the component you are mapping to represents one of the articles from the api the `id` of the article would be a good key as it is unique to the article.


## Excercise

Let's change the definition of our `NewsFeed` component to take an array of hackernews articles, and map them to `Article` components, then render them inside a `div`.

```jsx
// Usage should be like so:
//
//    <NewsFeed
//      articles={ARTICLES}
//    />
//

```

**_Additional Exercise_**

Let's refactor our NewsFeed component into its own file. This file should be `source/Views/NewsFeed/index.jsx`
