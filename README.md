```javascript
let myArray = [
  [1, 2, 3, 4, 5, 6, 7],
  [8, 9, 10, 11, 12, 13, 14],
  [15, 16, 17, 18, 19, 20, 21],
  [22, 23, 24, 25, 26, 27, 28],
  [29, 30, 31, 32, 33, 34, 35],
  [36, 37, 38, 39, 40, 41, 42],
  [43, 44, 45, 46, 47, 48, 49]
];

const iterate = (items) => {

  let i = 0;

  // Array will contains our numbers
  const finalArr = [];

  // iNITIAL direction
  let direction = "right";

  // Iterate while array items is exist
  while (items.length) {
    if (direction === "right") {
      finalArr.push(...[...items.shift()]);
      direction = "bottom";
    }

    if (direction === "bottom" && items.length) {
      for (let o = 0; o < items.length; o++) {
        finalArr.push(items[o].pop());
      }
      direction = "left";
    }

    if (direction === "left" && items.length) {
      finalArr.push(...[...items.pop().reverse()]);
      direction = "top";
    }

    if (direction === "top" && items.length) {
      for (let o = 0; o < items.length; o++) {
        finalArr.push(items[items.length - o - 1].shift());
      }
      direction = "right";
    }
    i++;
  }
  return finalArr;
}

 
console.log(iterate(myArray)); 
// 1, 2, 3, 4, 5, 6, 7, 14, 21, 
28, 35, 42, 49, 48, 47, 46, 45, 44, 
43, 36, 29, 22, 15, 8, 9, 10, 11, 12,
13, 20, 27, 34, 41, 40, 39, 38, 37, 30, 
23, 16, 17, 18, 19, 26, 33, 32, 31, 24, 25

![alt text](https://i.stack.imgur.com/Hajfm.png)
