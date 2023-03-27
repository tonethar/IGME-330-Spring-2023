# Checkoff - TypeScript Practice

## I. Overview
- You will utilize the TypeScript "playground" to add an interface, enum, and strong typeing to the code fragment below
- The TypeScript playground is here: https://www.typescriptlang.org/play
- Note that the playground will initially complain about the start code - `"Parameter 'todo' implicitly has an 'any' type."` - and so on. Your job is to fix these errors by utilizing strong typing

<hr>

## II. Start code & Instructions

***lastName*-*firstInitial*-ts-practice**

```js
// START CODE & Instructions

/*
  #1 - Create an interface that describes the structure of the item objects in the `todoItems` array
  Then strongly type the `todoItems` array
*/

/*
  #2 - Strongly type the `status` property with an enum
  Note the `status` values below: "done", "in-progess" etc
*/

/*
  #3 - Strongly type the parameters and return values of `addTodoItem()` and `getNextId()`
*/

// **When you are done, there must not be any errors under the Playground's "Errors" tab**

const todoItems = [
    { id: 1, title: "Learn HTML", status: "done", completedOn: new Date("2021-09-11") },
    { id: 2, title: "Learn TypeScript", status: "in-progress" },
    { id: 3, title: "Write the best web app in the world", status: "todo" },
]

function addTodoItem(todo) {
    const id = getNextId(todoItems)

    const newTodo = {
        id,
        title: todo,
        status: "todo",
    }

    todoItems.push(newTodo)

    return newTodo
}

function getNextId(items) {
    return items.reduce((max, x) => x.id > max ? max : x.id, 0) + 1
}

const newTodo = addTodoItem("Buy lots of stuff with all the money we make from the app")

console.log(JSON.stringify(newTodo))
```

<hr>

## III. Hints & Tips
- The above code is from the [LinkedIn Learning - TypeScript Essential Training](https://www.linkedin.com/learning/typescript-essential-training-14687057) course - the Chapter 2 Challenge
  - RIT gives you free access to all of the LinkedIn Learning courses - and you will need to sign in with your RIT email to access them
  - If you get stuck on this checkoff, go ahead and look at Challenge and Challenge solutions videos for ideas
  - But do not use "generics" in the `getNextId(items)` function like they did in the video

<hr>

## IV. Submission

- Screenshot
- ZIP and post the folder to myCourses

