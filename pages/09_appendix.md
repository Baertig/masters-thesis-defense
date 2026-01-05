## Execution Model

<div class="flex flex-col gap-4 mt-4">
    <strong>Stack based</strong>
    <img src="../assets/stack-based.svg" width="700px" class="mb-8 self-center"/>
    <strong>Register based</strong>
    <img src="../assets/register-based.svg" width="700px" class="self-center"/>
</div>

---

## Dispatch Mechanism

<div class="mt-4 grid grid-cols-3 gap-12 relative">
<div> 

**Switch Case Dispatch**

<div class="my-16" />

```c
switch(opcode) {
    case ADD: 
        push(op1 + op2);
    ...
}
```
</div> 

<div>

**Indirect Threaded Dispatch**

<img src="../assets/indirect-threaded-interpretation.svg" width="100%" />

</div>

<div>

**Direct Threaded Dispatch**

<img src="../assets/direct-threaded-interpretation.svg" width="100%" />

</div>

</div>

<style>
strong {
    margin-bottom: 20px;
}
</style>

---

## Bytecode Compilation Pipeline

<div class="flex h-full justify-center items-center">
    <img src="../assets/Bytecode Compilation Pipeline.svg" width="700px"/>
</div>

---

## Execution time vs. Heap size 

<div class="flex h-full justify-center items-center">
    <img src="../assets/heap-increase-benchmark.png" width="600px"/>
</div>

---

## Minimum Heap size vs Peak Heap Usage

<div class="flex h-full justify-center items-center">
    <img src="../assets/min_heap_vs_peak_heap.png" width="600px"/>
</div>



