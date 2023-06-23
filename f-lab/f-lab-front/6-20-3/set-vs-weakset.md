# 📐 Set vs WeakSet

## Set

`Set` 객체는 자바스크립트에서 고유한 값들의 모음(collection)을 관리하는 데 사용됩니다. 이는 배열과 비슷하지만 몇 가지 주요 차이점이 있습니다:

* `Set`에 저장된 각 값은 고유합니다. 즉, 동일한 값을 두 번 이상 추가하더라도 `Set`에서는 하나의 항목만 유지됩니다.
* `Set`의 값은 순서가 없습니다. `Set`은 인덱스로 값을 접근하는 것을 지원하지 않습니다.
* `Set`은 `add`, `has`, `delete`, `clear`와 같은 유용한 메서드를 제공하여 값을 추가하고, 조회하고, 삭제하는 등의 작업을 수행할 수 있습니다.

ex)

```javascript
let set = new Set();

set.add(1); // Set [ 1 ]
set.add(2); // Set [ 1, 2 ]
set.add(3); // Set [ 1, 2, 3 ]
set.add(2); // Set [ 1, 2, 3 ], 2는 이미 Set에 있으므로 추가되지 않습니다.

console.log(set.has(1)); // true
console.log(set.size); // 3

set.delete(1); // Set [ 2, 3 ]
set.clear(); // Set []
```

`Set`은 이터러블하므로, `for...of` 루프를 사용하여 모든 값을 순회할 수 있습니다:

```javascript
let set = new Set([1, 2, 3, 4, 5]);

for (let value of set) {
    console.log(value); // 1, 2, 3, 4, 5를 순서대로 출력합니다.
}
```

`Set`은 배열과 유사하지만 중복된 값을 허용하지 않는다는 점에서 차이가 있으므로, 중복 없는 값들의 리스트를 관리하는 데 유용합니다.

ex)

1.  중복 제거: `Set`은 중복된 값을 허용하지 않기 때문에 중복된 값을 가지는 데이터에서 고유한 값들만을 추출하고자 할 때 사용됩니다. 예를 들어, 배열에서 중복된 요소를 제거하고 유일한 값들을 추출할 수 있습니다.

    ```javascript
    const arr = [1, 2, 3, 4, 2, 3, 1, 5];
    const uniqueValues = [...new Set(arr)];
    console.log(uniqueValues); // [1, 2, 3, 4, 5]
    ```
2.  검사: `Set`은 값의 존재 여부를 빠르게 확인할 수 있습니다. 특정 값이 `Set`에 포함되어 있는지 확인하고자 할 때 사용됩니다.

    ```javascript
    const set = new Set([1, 2, 3]);

    console.log(set.has(2)); // true
    console.log(set.has(4)); // false
    ```
3.  필터링: `Set`을 사용하여 고유한 값들로 구성된 데이터를 필터링하거나 유효성 검사를 수행할 수 있습니다.

    ```javascript
    const numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];

    const evenNumbers = numbers.filter(num => num % 2 === 0);
    console.log(evenNumbers); // [2, 4, 6, 8, 10]

    const uniqueNumbers = [...new Set(numbers)];
    console.log(uniqueNumbers); // [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
    ```
4.  &#x20;집계: `Set`은 고유한 값들의 집합을 관리하기 때문에 데이터에서 고유한 값들의 개수를 계산하거나 집계할 때 사용됩니다.

    ```javascript
    const fruits = ['apple', 'banana', 'apple', 'orange', 'banana', 'mango'];

    const uniqueFruits = new Set(fruits);
    console.log(uniqueFruits.size); // 4

    // 고유한 과일들을 배열로 변환
    const uniqueFruitsArray = Array.from(uniqueFruits);
    console.log(uniqueFruitsArray); // ['apple', 'banana', 'orange', 'mango']
    ```

`Set`은 중복되지 않는 값들을 관리하기 위해 사용되며, 위와 같은 상황에서 유용하게 활용될 수 있습니다. 데이터에서 고유한 값들을 추출하고 중복을 제거하거나 멤버십 검사를 수행하려는 경우 `Set`을 활용할 수 있습니다.

## WeakSet

`WeakSet`은 `Set`과 유사하지만 약한 참조(weak reference)를 가지는 객체만을 요소로 저장할 수 있는 특별한 종류의 `Set`입니다.

`WeakSet`의 특징은 다음과 같습니다:

1. `WeakSet`은 객체만을 요소로 가질 수 있습니다. 원시 값(primitive values)은 `WeakSet`에 저장할 수 없습니다.
2. `WeakSet`의 객체들에 대한 참조는 약하게 유지됩니다. 이는 `WeakSet`의 요소가 가비지 컬렉션의 대상이 될 수 있다는 것을 의미합니다. `WeakSet`에 있는 객체에 대한 다른 참조가 없다면, 그 객체는 언제든지 메모리에서 제거될 수 있습니다.
3. `WeakSet`은 이터러블이 아닙니다. 이는 `WeakSet`의 내용을 직접적으로 순회하거나, 모든 요소에 접근할 수 없다는 것을 의미합니다.
4. `WeakSet`은 `.size` 속성이 없습니다. `WeakSet`에 얼마나 많은 요소가 있는지를 확인할 수 있는 방법은 없습니다.

`WeakSet`은 `add`, `has`, `delete`라는 세 가지 메서드만을 제공합니다. 예를 들어:

```javascript
let weakSet = new WeakSet();
let obj = {};

weakSet.add(obj);
console.log(weakSet.has(obj)); // true

weakSet.delete(obj);
console.log(weakSet.has(obj)); // false
```

`WeakSet`은 가비지 컬렉션을 통해 메모리를 누수하지 않도록 도와주는 데 유용하며, 주어진 객체가 어디에 사용되었는지를 표시하는 데 사용될 수 있습니다. 가장 일반적인 사용 사례는 주어진 객체가 특정 `WeakSet`에 있는지 아닌지를 확인하는 것입니다.

ex)

```javascript
let weakSet = new WeakSet();

let obj1 = { name: 'Object 1' };
let obj2 = { name: 'Object 2' };

// 객체를 WeakSet에 추가합니다.
weakSet.add(obj1);
weakSet.add(obj2);

console.log(weakSet.has(obj1)); // true
console.log(weakSet.has(obj2)); // true

// 객체를 제거합니다.
weakSet.delete(obj1);

console.log(weakSet.has(obj1)); // false
console.log(weakSet.has(obj2)); // true

// 다음 코드는 에러를 발생시킵니다. WeakSet은 오직 객체만을 요소로 가질 수 있습니다.
// weakSet.add(1); // TypeError: Invalid value used in weak set
```

이 예시에서 `weakSet`은 `obj1`과 `obj2`에 대한 참조를 유지하지만, 이 참조는 약하게 유지됩니다. 이 말은, `obj1` 또는 `obj2`에 대한 다른 참조가 없다면, 이 객체들은 언제든지 메모리에서 제거될 수 있다는 것입니다. 이런 특징은 `WeakSet`이 주로 객체의 존재 여부를 확인하는 용도로 사용되는 이유입니다.



## Set vs WeakSet

`Set`과 `WeakSet`은 자바스크립트에서 제공하는 두 가지 서로 다른 데이터 구조입니다. \
하지만 몇가지 차이이 존재합니다.

1. **저장 가능한 값**: `Set`은 모든 종류의 값을 저장할 수 있습니다: 원시 값 (Numbers, Strings, Booleans 등등)과 객체들을 모두 포함합니다. 반면에 `WeakSet`은 오직 객체만을 저장할 수 있습니다.
2. **참조의 방식**: `Set`에서는 저장된 값들을 강한 참조로 가져갑니다.\
   즉 `Set`이 값을 유지하고 있는 동안 가비지 컬렉션(Garbage Collection)으로부터 그 값을 보호한다는 것을 의미합니다.\
   `WeakSet`은 저장된 객체에 대해 약한 참조를 가집니다. 이는 `WeakSet`에 저장된 객체가 다른 곳에서 사용되지 않게 되면 가비지 컬렉션의 대상이 될 수 있음을 의미합니다.
3. **순회 가능성**: `Set`은 이터러블합니다. \
   즉, `for...of` 루프나 `Set.prototype.forEach` 메서드를 사용하여 `Set`의 모든 값을 순회할 수 있습니다. \
   `WeakSet`은 이터러블이 아닙니다. `WeakSet`의 값을 직접적으로 접근하거나 순회할 수 있는 방법은 없습니다.
4. **메서드와 속성**: `Set`은 여러 가지 메서드 (`add`, `delete`, `clear`, `has`)와 속성 (`size`)을 제공합니다. \
   `WeakSet`은 `add`, `delete`, `has` 메서드만 제공하며, `size` 속성이나 `clear` 메서드는 제공하지 않습니다.

`Set`은 중복을 허용하지 않는 값을 저장할 때 사용되며, \
`WeakSet`은 객체의 존재 여부를 확인하고 가비지 컬렉션으로부터 보호하지 않는 경우에 사용됩니다.

