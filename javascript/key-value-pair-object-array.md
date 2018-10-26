---
description: >-
  JavaScript don't have ArrayList like in Java, but we can create object with
  different key value pair first, then assign them to an array.
---

# Array with key value pair using object

## Create object

```javascript
var obj = {};
obj['campaignID'] = '1001';
obj['qty'] = '2';
obj['price'] = '50';

var obj2 = {};
obj2['campaignID'] = '1002';
obj2['qty'] = '3';
obj2['price'] = '80';
```

## Push object into array

```javascript
var array = [];
array.push(obj);
array.push(obj2);
```

## Searching

```javascript
function search(nameKey, myArray){
    for (var i=0; i < myArray.length; i++) {
        if (myArray[i].campaignID === nameKey) {
            return myArray[i];
        }
    }
}
```



Or just get the value like this

```javascript
array.find(o => o.campaignID === '1001'); //or
array.find(o => o['campaignID'] === '1001')
```

## All together

```javascript
<script>
function search(nameKey, myArray){
    for (var i=0; i < myArray.length; i++) {
        if (myArray[i].campaignID === nameKey) {
            return myArray[i];
        }
    }
}

var obj = {};
obj['campaignID'] = '1001';
obj['qty'] = '2';
obj['price'] = '50';

var obj2 = {};
obj2['campaignID'] = '1002';
obj2['qty'] = '3';
obj2['price'] = '80';

var array = [];
array.push(obj);
array.push(obj2);

console.log(array); 
/* print out
(2) [{…}, {…}]
0: {campaignID: "1001", qty: "2", price: "50"}
1: {campaignID: "1002", qty: "3", price: "80"}
*/

var resultObject = search("1001", array);
console.log(resultObject);
/* print out
{campaignID: "1001", qty: "2", price: "50"}
*/

console.log(resultObject.qty);
/* print out
2
*/

console.log(array.find(o => o.campaignID === '1001'));
console.log(array.find(o => o['campaignID'] === '1001'));
/* print out, same with search function
{campaignID: "1001", qty: "2", price: "50"}
{campaignID: "1001", qty: "2", price: "50"}
*/
</script>
```





Reference: [https://stackoverflow.com/questions/12462318/find-a-value-in-an-array-of-objects-in-javascript](https://stackoverflow.com/questions/12462318/find-a-value-in-an-array-of-objects-in-javascript)

