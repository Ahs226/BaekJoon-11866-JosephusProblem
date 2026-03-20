# BaekJoon-11866-JosephusProblem
Efficient implementation of JosephusProblem


## Josephus Problem
Josephus problem is a sequence in which a group of N people surrounding a circle are eliminated. The sequence is as follows. A group of N people sits around a circular table, and k-th person is removed until everyone is eliminated. The sequence in whice the k-th person is removed is called the Josephus permutation. The Josephus problem is the process of finding the Josephus permutation.


## In BaekJoon-11866...
Given variations K and N in first line.
Program output is Josephus permutation for variation N and N

### Example
  Input : 7 3

  Output: <3, 6, 2, 7, 5, 1, 4>


## Normal solution
Use a queue, one of the data structures. 

<p allgn="center">
<img width="1376" height="768" alt="Image" src="https://github.com/user-attachments/assets/e3c99b4b-8e3c-4aa0-8b34-6906ccd7f574" />
</p>

If this index is ship of K, Pop data in queue. And shift all element before pop data index to right. Repeat this process to everyone eliminated.

<p allgn="center">
<img width="1376" height="768" alt="Image" src="https://github.com/user-attachments/assets/568f94d7-3dc4-4ca5-9b12-d15a698940f1" />
</p>

But this process have square of timecomplication.

Therefore, I suggest another way.

## ‼️My solution

### Normal solution's problems
  #### First. A function of pop needs to receive for a variable K.
    Function of pop needs a variable K for pop k-th data in queue.

  #### Second. A function of push needs to receive for a variable index
    Function of push need a variable for shift data.


### Concept
  I don't override function. Functions work that receive only sturct.

  #### step1. Pop K-th eliments
  
<p allgn="center">
<img width="1375" height="768" alt="Image" src="https://github.com/user-attachments/assets/89660ca4-93fd-4b83-a2eb-5dce4f4744f8" />
</p>

  #### step2. Pop and Push
    eliments before K-th move back of queue.
  
<p allgn="center">
<img width="1375" height="768" alt="Image" src="https://github.com/user-attachments/assets/6c113be3-fd78-4e90-aeb6-ae18e3718bec" />
</p>

    This consequence have low time compliment and simple sorce code.


### SORCE CODE

#### Important Point
```js
while (scanQueue.size != 0) {
		if ((index % k) == k-1 ) {
			Push(&printQueue, Pop(&scanQueue));
			index++;
			continue;
		}
		Push(&scanQueue, Pop(&scanQueue));
		index++;
	}
	
```

### Full code
```js
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h> 

#define MaxQueueSize 20000

struct Queue {
	int data[MaxQueueSize];
	int front;
	int back;
	int size;
};
//no error
void InitQueue(struct Queue* queue) {
	queue->front = 0;
	queue->back = 0;
	queue->size = 0;
}

int Push(struct Queue* queue, int x) {
	if (x == -1) {
		return 0;
	}
	queue->data[queue->back++ % MaxQueueSize] = x;
	queue->size++;
	return 0;
}
//no error
void FillQueue(struct Queue* queue, int n) {
	for (int i = 1; i <= n; i++) {
		Push(queue, i);
	}
}

int Pop(struct Queue* queue) {
	int x;
	if (queue->size == 0) {
		return -1;
	}
	else {
		x = queue->data[queue->front++ % MaxQueueSize];
		queue->size--;
		return x;
	}
}

int main() {
	int n;
	int k;
	int index = 0;

	scanf("%d %d", &n, &k);


	struct Queue scanQueue;
	struct Queue printQueue;

	InitQueue(&scanQueue);
	InitQueue(&printQueue);

	FillQueue(&scanQueue, n);

	while (scanQueue.size != 0) {
		if ((index % k) == k-1 ) {
			Push(&printQueue, Pop(&scanQueue));
			index++;
		#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h> 

#define MaxQueueSize 20000

struct Queue {
	int data[MaxQueueSize];
	int front;
	int back;
	int size;
};
//no error
void InitQueue(struct Queue* queue) {
	queue->front = 0;
	queue->back = 0;
	queue->size = 0;
}

int Push(struct Queue* queue, int x) {
	if (x == -1) {
		return 0;
	}
	queue->data[queue->back++ % MaxQueueSize] = x;
	queue->size++;
	return 0;
}
//no error
void FillQueue(struct Queue* queue, int n) {
	for (int i = 1; i <= n; i++) {
		Push(queue, i);
	}
}

int Pop(struct Queue* queue) {
	int x;
	if (queue->size == 0) {
		return -1;
	}
	else {
		x = queue->data[queue->front++ % MaxQueueSize];
		queue->size--;
		return x;
	}
}

int main() {
	int n;
	int k;
	int index = 0;

	scanf("%d %d", &n, &k);


	struct Queue scanQueue;
	struct Queue printQueue;

	InitQueue(&scanQueue);
	InitQueue(&printQueue);

	FillQueue(&scanQueue, n);

	while (scanQueue.size != 0) {
		if ((index % k) == k-1 ) {
			Push(&printQueue, Pop(&scanQueue));
			index++;
			continue;
		}
		Push(&scanQueue, Pop(&scanQueue));
		index++;
	}
	
	printf("<");
	for (int i = 0; i < n - 1; i++) {
		printf("%d, ", Pop(&printQueue));
	}
	printf("%d>", Pop(&printQueue));

	return 0;
}	continue;
		}
		Push(&scanQueue, Pop(&scanQueue));
		index++;
	}
	
	printf("<");
	for (int i = 0; i < n - 1; i++) {
		printf("%d, ", Pop(&printQueue));
	}
	printf("%d>", Pop(&printQueue));

	return 0;
}
```
