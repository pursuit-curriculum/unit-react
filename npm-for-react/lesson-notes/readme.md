# NPM for React

## Introduction

Let's build a small node application together. We will work on an imaginary business venture where the local zoo is looking to partner with a candy manufacturer to make unique and memorable jellybeans to help raise some money.

The company has sent over some data on some possible jellybeans, but it's a bit hard to read and analyze the data in its current format. We'll build a little app that imports the data, and then we will write a couple of functions to explore the data.

## Learning Objectives

- Create a `package.json` file using the npm command-line tool.
- Describe the importance and purpose of the `package.json `file.
- Ignore common folders and files with the `.gitignore` file.
- Define your own scripts through the `package.json` file.
- Import and export JavaScript data types from files using `import` and `export` statements by modifying the `package.json` to have a `type` of `module`.

## Getting started

- `mkdir zoo-jellybeans`.
- `cd zoo-jellybeans`.
- `touch index.js jellybeans.js jellybeans.json`.
- `echo "node_modules\n.DS_Store" >> .gitignore`.
- `npm init -y`, the flag `-y` will automatically set all default input for `package.json`.
- Update the `package.json` to be type module, so that you can use `import` and `export` statements.

<details><summary>Copy and paste only the array into <code>jellybeans.js</code>:</summary>

```js
[
  {
    name: "Wiggly Chilean Corralero",
    color: "sky blue",
    flavorType: "bitter",
    inStock: true,
  },
  {
    name: "Impish Argente Brun",
    color: "gold",
    flavorType: "spicy",
    inStock: false,
  },
  {
    name: "Venerated Pulikulam",
    color: "yellow",
    flavorType: "salty",
    inStock: true,
  },
  {
    name: "Well-to-do Hognosed viper",
    color: "blue",
    flavorType: "salty",
    inStock: false,
  },
  {
    name: "Attractive Australian Freshwater Crocodile",
    color: "black",
    flavorType: "fruity",
    inStock: true,
  },
  {
    name: "Mediocre West African Lion",
    color: "olive",
    flavorType: "fruity",
    inStock: true,
  },
  {
    name: "Ill-informed Bolognese",
    color: "salmon",
    flavorType: "salty",
    inStock: false,
  },
  {
    name: "Warped Bouvier des Flandres",
    color: "lime",
    flavorType: "spicy",
    inStock: true,
  },
  {
    name: "Serene Allmogekor",
    color: "tan",
    flavorType: "bitter",
    inStock: false,
  },
  {
    name: "Brisk Grass Carrying Wasp",
    color: "fuchsia",
    flavorType: "savory",
    inStock: true,
  },
];
```

</details>

<details><summary>Copy and paste only the array into <code>jellybeans.json</code>:</summary>

```json
[
  {
    "name": "Perfumed Savannah",
    "color": "yellow",
    "flavorType": "fruity",
    "inStock": true
  },
  {
    "name": "Agitated Northeast Congo Lion",
    "color": "fuchsia",
    "flavorType": "fruity",
    "inStock": false
  },
  {
    "name": "Royal Australian Draught Horse",
    "color": "magenta",
    "flavorType": "spicy",
    "inStock": true
  },
  {
    "name": "Unselfish Kurilian Bobtail",
    "color": "turquoise",
    "flavorType": "salty",
    "inStock": true
  },
  {
    "name": "Glorious Northeast Congo Lion",
    "color": "magenta",
    "flavorType": "nutty",
    "inStock": false
  },
  {
    "name": "Rotating Silver",
    "color": "gold",
    "flavorType": "fruity",
    "inStock": false
  },
  {
    "name": "Speedy Toyger",
    "color": "gold",
    "flavorType": "spicy",
    "inStock": true
  },
  {
    "name": "Flowery Australian Freshwater Crocodile",
    "color": "grey",
    "flavorType": "salty",
    "inStock": true
  },
  {
    "name": "Upset Chinese River Dolphin",
    "color": "indigo",
    "flavorType": "nutty",
    "inStock": true
  },
  {
    "name": "Smoggy Württemberger",
    "color": "pink",
    "flavorType": "savory",
    "inStock": false
  }
]
```

</details>

## Import the data

In `index.js`:

- Import `jellybeans.js` and set it to a variable `jellybeans`.
- Import `jellybeans.json` and set it to a variable `jellybeansJSON`.
- Log each one to confirm you've successfully imported each set of data.

## Work with the data

### See a list of salty jellybeans

There are 6 `flavorTypes`:

- spicy
- salty
- fruity
- nutty
- savory
- bitter

Create a variable called `salty` that will be an array of all the salty jellybeans from the `jellybeans` array.

To do this, we can approach this by realizing that we want to `filter` out all the jellybeans that are not salty. Therefore we can use the `filter` method:

```js
const salty = jellybeansJSON.filter();
```

Then, we want to confirm that the jellybean(jb) `flavorType` is equal to `salty`. If this value is true, it will be added to a new array. If it is false, it will not be added to the new array.

```js
const salty = jellybeansJSON.filter((jb) => {
  return jb.flavorType === "salty";
});

console.log(salty);
```

- [Filter method documentation](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter)

### Write a function that allows you to see jellybeans listed alphabetically by color

Create a function called `organizeByColor` that will take arguments of a jellybeans array and return the array with the objects organized by color.

```js
const organizeByColor = (candies) => {
  return candies;
};
```

> **Question:** Why is it important to NOT name the parameter the same as the data variable?

#### Review the sort method

`a` will represent the first array object, and `b` will represent the second object.

`.sort()` will iterate over the array and compare `a` to `b`.

Strings are compared by the first character only. The character values are based on their [character code values](https://www.w3schools.com/charsets/ref_utf_basic_latin.asp). For example, lowercase `a` is valued at 97, `b` is valued at 98, and `z`'s value is 122. Notice that capital letters have different codes. For example, the letter `A` has a value of 65.

There are three possibilities when comparing values. To sort the items in alphabetically ascending order, we will follow the following:

- `a` is smaller than `b`. Therefore it must move to the left. In order to move it to the left, we will return a value of `-1`.
- `a` is larger than `b`. Therefore it must move to the right. In order to move it to the right, we will return a value of `1`.
- `a` and `b` are the same. Therefore the order should not d. We will return a value of 0.

#### Complete the function

```js
const organizeByColor = (candies) => {
  return candies.sort((a, b) => {
    if (a.color < b.color) {
      return -1;
    } else if (a.color > b.color) {
      return 1;
    } else {
      return 0;
    }
  });
};
```

```js
console.log(organizeByColor(jellybeansJSON));
```

What happened to the `jellyBeansJSON` data? Is it permanently sorted? Or has this data remained the same?

When would you want the original data changed? When would you not want the original data changed?

- [Sort method documentation](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/sort)

## Write a custom script

Open the `package.json` file. Write a custom script that prints the name of your favorite animal in the terminal.

```json
{
  "name": "jellybeans-lesson-notes",
  "type": "module",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "animal": "echo 'My favorite animal is a cat'"
  },
  "keywords": [],
  "author": "",
  "license": "ISC"
}
```

How do you run this script?
