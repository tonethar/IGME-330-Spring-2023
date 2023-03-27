# Checkoff - TypeScript Practice

## I. Overview
- You will utilize the TypeScript "playground" to add an interface, enum, and strong typeing to the code fragment below
- The TypeScript "playground" is here: https://www.typescriptlang.org/play

<hr>

## II. Start code & Instructions

**lastName-firstInitial-ts-practice**

```js
// START CODE & Instructions

/*
  #1 - Create an interface that describes the structure of the items in the `todoItems` array.
  The strongly type the `todoItems` array
*/

/*
  #2 - strongly type the `status` property with an enum
*/

/*
  #3 - strongly type the parameters and return values of `addTodoItem()` and `getNextId()`
*/

const todoItems = [
    { id: 1, title: "Learn HTML", status: "done", completedOn: new Date("2021-09-11") },
    { id: 2, title: "Learn TypeScript", status: "in-progress" },
    { id: 3, title: "Write the best app in the world", status: "todo" },
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

<hr>

## IV. Submission

- Screenshot
- ZIP and post the folder to myCourses

