
```javascript
/**
 * @param {number[]} guess
 * @param {number[]} answer
 * @return {number}
 */
var game = function (guess, answer) {
    return guess.reduce((count, value, index) => +(guess[index] === answer[index]) + count, 0);
};
```