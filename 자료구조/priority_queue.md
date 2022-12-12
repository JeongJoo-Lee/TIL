# 우선순위 큐
FIFO인 큐와 달리 우선 순위가 높은 요소가 먼저 나가는 큐

**우선순위 큐는 자료구조가 아닌 개념이다.

## 힙을 사용해서 자바스크립트로 구현 및 활용

### 힙 요소 추가
```javascript
class MaxHeap {
    constructor(){
        this.heap = [null];
    }
 
    push(value){
        this.heap.push(value);
        let currentIndex = this.heap.length - 1;
        let parentIndex = Math.floor(currentIndex / 2);

        while(parentIndex !== 0 && this.heap[parentIndex] < value){
            const temp = this.heap[parentIndex];
            this.heap[parentIndex] = value;
            this.heap[currentIndex] = temp;

            currentIndex = parentIndex;
            parentIndex = Math.floor(currentIndex / 2);
        }
    }
}
```
- 힙 요소 추가 활용 예제
```javascript
const heap = new MaxHeap();
heap.push(45);
heap.push(36);
heap.push(54);
heap.push(27);
heap.push(63);
console.log(heap.heap);

// Result is [null, 63, 54, 45, 27, 36];
```




### 힙 요소 제거
```javascript
pop(){
    const returnValue = this.heap[1];
    this.heap[1] = this.heap.pop();

    let currentIndex = 1;
    let leftIndex = 2;
    let rightIndex = 3;
    while(
        this.heap[currentIndex] < this.heap[leftIndex] || this.heap[currentIndex] < this.heap[rightIndex]
    ){
        if(this.heap[leftIndex] < this.heap[rightIndex]){
            const temp = this.heap[currentIndex];
            this.heap[currentIndex] = this.heap[rightIndex];
            this.heap[rightIndex] = temp;
            currentIndex = rightIndex;
        }else{
            const temp = this.heap[currentIndex];
            this.heap[currentIndex] = this.heap[leftIndex];
            this.heap[leftIndex] = temp;
            currentIndex = leftIndex;
        }
        leftIndex = currentIndex * 2;
        rightIndex = currentIndex * 2 + 1;
    }

    return returnValue;
}
```

- 힙 요소 제거 사용 예제
```javascript
// Heap state = [null, 63, 54, 45, 27, 36]

const array = [];
array.push(head.pop()); // 63
array.push(head.pop()); // 54
array.push(head.pop()); // 45
array.push(head.pop()); // 36
array.push(head.pop()); // 27
console.log(array);

// Result : [63, 54, 45, 36, 27]
```