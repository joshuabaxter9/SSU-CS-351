## Which program is fastest? Is it always the fastest?

The Program that was the fastest was the malloc.out. This consistently ran faster than all the other programs, in real and user time. It had the lowest average of 0.025000 seconds with the number of blocks being set to 40,000 and 10 trials. It was the fastest average every single time I ran `<make clean trials NUM_BLOCKS=40000 NUM_TRIALS=10>`, which I ran multiple times.

---

## Which program is slowest? Is it always the slowest?

The Program that was the slowest was list.out. It ran under the same 40,000 number of blocks and trials as the one before, and had an average runtime of 0.081000 seconds, which was the slowest out of all the programs, but not by much. new.out was a close second. It was the slowest average every single time I ran `<make clean trials NUM_BLOCKS=40000 NUM_TRIALS=10>`, which I ran multiple times, but its individual times were similar to the new.out, even though its average was higher every single time.

---

## Was there a trend in program execution time based on the size of data in each Node? If so, what, and why?

The size of data in each node had an impact on the amount of time it took to allocate the data. As I increased the size of the data, it became slower, and this can most likely be tied to cache efficiency. As the data grows, it requires more space to allocate in order to store a larger node. This can cause more cache cycles, making programs slower.

---

## Was there a trend in program execution time based on the length of the block chain?

Yes. As the blockchain increased in length, it also caused the program execution time to go up. This is because there is more data being allocated, and because there is more data being allocated, it takes longer to do so.

---

## Consider heap breaks, what's noticeable? Does increasing the stack size affect the heap? Speculate on any similarities and differences in programs?

alloca.out, has the least number of heap breaks by far. Increasing eh stack size should not affect the heap because they are both in separate regions of memory, with vastly different limits. This is also why when you change the number of blocks, the first one to break is alloca.out, and this is because stack memory is often smaller than heap memory. Therefore, increasing the stack size should not affect the heap. Some similarities were that everything but alloca.out had high numbers of heap breaks. This could be explained by alloca.out being more reliant on the stack compared to the other programs. When running `<make clean breaks NUM_BLOCKS=500000>` alloca.out had only 66 breaks, while all the other had 400+.

---

## Considering either the malloc.cpp or alloca.cpp versions of the program, generate a diagram showing two Nodes.

Include in the diagram:
- The relationship of the head, tail, and Node next pointers.
- Show the size (in bytes) and structure of a Node that allocated six bytes of data.
- Include the bytes pointer, and indicate using an arrow which byte in the allocated memory it points to.

```text
head ─┐
      v
   ┌───────────────────────────────┐        ┌───────────────────────────────┐
   │            Node A             │        │            Node B             │
   ├───────────────┬───────────────┤        ├───────────────┬───────────────┤
   │ next (8B)     │ →─────────────┼───┐    │ next (8B)     │ → nullptr     │
   ├───────────────┼───────────────┤   │    ├───────────────┼───────────────┤
   │ data_len (8B) │ = 6           │   │    │ data_len (8B) │ = 6           │
   ├───────────────┼───────────────┤   │    ├───────────────┼───────────────┤
   │ bytes* (8B)   │ ──────────────┼───┘    │ bytes* (8B)   │ ──────────────┤
   └───────────────┴───────────────┘        └───────────────┴───────────────┘
         (≈24 bytes for Node)                       (≈24 bytes for Node)

tail ──────────────────────────────────────────────────────────────┘
```


( chat gpt helped me make the graph nice )
---

## There's an overhead to allocating memory, initializing it, and eventually processing (in our case, hashing it). For each program, were any of these tasks the same? Which one(s) were different?

Many of the programs were the same; they generated memory using their specific memory allocation function, which was malloc, alloca, or new, but in a list.cpp, you are utilizing a vector and a list, which are kind of a mix of both. According to geeksforgeeks, vectors can be stored both on the stack and heap in order to efficiently and correctly handle the memory. Also, malloc and new allocate memory on he heap, and alloca, allocates memory on the stack.

---

## As the size of data in a Node increases, does the significance of allocating the node increase or decrease?

Yes, allocating memory has a cost, and if you are allocating memory in small chunks, the overhead is going to feel much more significant than if you are allocating large chunks of memory. This is because if there is less memory being allocated, then you will feel the overhead more, rather than if you are allocating larger chunks of data, which inherently take more time to allocate.


( chat gpt helped me format it in markdown )
