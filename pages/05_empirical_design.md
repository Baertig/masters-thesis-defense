---
layout: full
---

<div class="container">
    <div class="heading">
        <h1> Empirical Evaluation on RIOT OS</h1>
    </div>
    <div class="agenda">
        <ol>
            <li>Candidate Introduction </li>
            <li>HLL VM Architecture </li>
            <li>Classification </li>
            <li>Experiment Design </li>
            <li>Implementation </li>
            <li>Results </li>
        </ol>
    </div>
</div>

<!--**Design:** Metrics + Benchmark Programms-->

<style>
.heading {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    padding: 16px;
    background-color: var(--blau-2);
}

.agenda {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
}

ol > li {
    margin-bottom: 12px;
}

.container {
    display: grid;
    grid-template-columns: 2fr 3fr;
    height: 100%;
}
</style>

---

## Candidates

<div class="candidates" >
    <div class="dynamic"><logos-javascript />JerryScript </div>
    <div class="dynamic"><logos-python />Micropython</div>
    <div class="dynamic"><logos-lua />Lua</div>
    <div class="static"><img src="../assets/ebpf-log.svg"/>Femto-Container</div>
    <div class="static"><img src="../assets/ebpf-log.svg"/>µBPF</div>
    <div class="static"><logos-webassembly /><span class="text-center"><strong>W</strong>eb<strong>A</strong>ssembly <strong>M</strong>icro <strong>R</strong>untime</span></div>
</div>

<style>
.candidates {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    row-gap: 100px;
    transition: grid-template-columns 0.5s ease-in-out;
    margin-top: 60px;
}

.candidates > div {
    padding: 16px;
}

.candidates > div {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    gap: 4px;
}

.slidev-icon {
    font-size: 28px;
}

</style>

---

## Fundamental HLL VM Architecture

<div class="m-t-16 flex items-center justify-center">
    <img src="../assets/VM architecture.png" width="500px"/>
</div>

---

### Execution Model (Addition)

<div class="flex flex-col gap-4 mt-4">
    <strong>Stack based</strong>
    <img src="../assets/stack-based.svg" width="700px" class="mb-8 self-center"/>
    <strong>Register based</strong>
    <img src="../assets/register-based.svg" width="700px" class="self-center"/>
</div>

---

### Dispatch Mechanism

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
clicks: 5
---

## Candidates Classification

<div class="m-t-8" />
<table style="position: relative">
    <Spotlight 
        :active-clicks="[1,2,3,4]" 
        :x="[18, 46, 68, 85]" 
        :y="[11, 11, 11, 11]" 
        :w="[27, 19, 9, 6]" 
        :h="[89, 89, 89, 89]" 
    />
    <thead>
        <tr style="border-bottom: 0px">
            <th />
            <th />
            <th colspan="5" style="text-align: center">Architectural Properties</th> 
            <th colspan="4" style="text-align: center">Feature Counts</th>
        </tr>
        <tr>
            <th />
            <th>HLL VM</th>
            <th>Garbage Collection</th>
            <th>Typing</th>
            <th>Bytecode Compilation</th>
            <th>Exec-Model</th>
            <th>Dispatch</th>
            <th class="text-center">Development</th>
            <th class="text-center">Operation</th>
            <th class="text-center">Security</th>
            <th class="text-center">Compilation</th>
        </tr>
    </thead>
    <tbody>
        <tr class="dynamic">
            <td rowspan="3" class="border-right">Dynamic VMs</td>
            <td>JerryScript</td>
            <td>Yes</td>
            <td>Dynamic</td>
            <td>On-device</td>
            <td>Stack</td>
            <td>Switch-Case</td>
            <td class="text-center"><strong>4/5</strong></td>
            <td class="text-center"><strong>1/3</strong></td>
            <td class="text-center"><strong>1/6</strong></td>
            <td class="text-center"><strong>0/2</strong></td>
        </tr>
        <tr class="dynamic">
            <td>MicroPython</td>
            <td>Yes</td>
            <td>Dynamic</td>
            <td>On-Device</td>
            <td>Stack</td>
            <td>Switch-Case</td>
            <td class="text-center"><strong>4/5</strong></td>
            <td class="text-center"><strong>1/3</strong></td>
            <td class="text-center"><strong>0/6</strong></td>
            <td class="text-center"><strong>0/2</strong></td>
        </tr>
        <tr class="dynamic">
            <td>Lua</td>
            <td>Yes</td>
            <td>Dynamic</td>
            <td>On-Device</td>
            <td>Register</td>
            <td>Switch-Case</td>
            <td class="text-center"><strong>4/5</strong></td>
            <td class="text-center"><strong>1/3</strong></td>
            <td class="text-center"><strong>3/6</strong></td>
            <td class="text-center"><strong>0/2</strong></td>
        </tr>
        <tr class="static">
            <td rowspan=4 class="border-right">Static VMs</td>
            <td>WAMR</td>
            <td>No</td>
            <td>Static</td>
            <td>Off-Device</td>
            <td>Stack</td>
            <td>Switch-Case</td>
            <td class="text-center"><strong>3/5</strong></td>
            <td class="text-center"><strong>2/3</strong></td>
            <td class="text-center"><strong>4/6</strong></td>
            <td class="text-center"><strong>1/2</strong></td>
        </tr>
        <tr class="static">
            <td>WAMR (fast)</td>
            <td>No</td>
            <td>Static</td>
            <td>Off-Device</td>
            <td>Register</td>
            <td>Direct Threaded Interpretation</td>
            <td class="text-center"><strong>3/5</strong></td>
            <td class="text-center"><strong>2/3</strong></td>
            <td class="text-center"><strong>4/6</strong></td>
            <td class="text-center"><strong>1/2</strong></td>
        </tr>
        <tr class="static">
            <td>Femto-Container</td>
            <td>No</td>
            <td>Static</td>
            <td>Off-Device</td>
            <td>Register</td>
            <td>Indirect Threaded Interpretation</td>
            <td class="text-center"><strong>1/5</strong></td>
            <td class="text-center"><strong>1/3</strong></td>
            <td class="text-center"><strong>4/6</strong></td>
            <td class="text-center"><strong>0/2</strong></td>
        </tr>
        <tr class="static">
            <td>&mu;BPF</td>
            <td>No</td>
            <td>Static</td>
            <td>Off-Device</td>
            <td>Register</td>
            <td>Switch-Case</td>
            <td class="text-center"><strong>1/5</strong></td>
            <td class="text-center"><strong>2/3</strong></td>
            <td class="text-center"><strong>4/6</strong></td>
            <td class="text-center"><strong>1/2</strong></td>
        </tr>
    </tbody>
</table>

<style>
.border-right {
    border-right: 1px solid #222;
    border-bottom: 0px;
}

th {
    font-weight: bold;
}

thead {
    background-color: var(--blau-2);
}

tr {
    border-color: #222;
}

table {
    font-size: 10px;
}

.dynamic {
    background-color: var(--gelb-2)
}

.static {
    background-color: var(--rot-2)
}

</style>

---

## Design: Metrics

<img class="mt-8" src="../assets/application_execution_lifecycle.png" />

<div class="metrics mt-16 ml-12 mr-24 grid gap-4 ">
    <div>
        <div class="flex flex-col">
            <strong>Compilation</strong>
            <span><material-symbols-code /> Code Size</span>
        </div>
    </div>
    <div>
        <material-symbols-keyboard-arrow-right class="text-4xl"/>
    </div>
    <div>
        <div class="flex flex-col">
            <strong>Flash on Device</strong>
            <span><material-symbols-memory/>ROM footprint</span>
        </div>
    </div>
    <div>
        <material-symbols-keyboard-arrow-right class="text-4xl"/>
    </div>
    <div>
        <div>
            <strong>Execution</strong>
            <div><material-symbols-memory/>RAM usage</div>
            <div><material-symbols-timer/>Load Time</div>
            <div><material-symbols-timer/>Execution Time</div>
        </div>
    </div>
</div>

<style>
.metrics {
    font-size: 16px;
    grid-template-columns: 1fr auto 1fr auto 1fr;
}

.metrics > div {
    display: flex;
    flex-direction: column;
    justify-content: start;
    align-items: center;
    padding: 4px;
}
</style>

<!--- Benchmarks + Metrics-->

---
layout: two-cols-header
---

## Design: Benchmark Programms

<div class="m-4" />

::left::
Subset of Embench IoT 2.0 

*Static Memory*
- xgboost
- crc_32
- ud

*Dynamic Memory*
- md5sum
- tarfind


<!--
Each Programm is **modified** to run on the virtual machine.
Femto-Container and µBPF do **not** offer a **heap** region for dynamic memory allocations.
-->

---
layout: two-cols-header
---

## Implementation

::left::

<div class="flex justify-center flex-col h-full">

- **Code Size**: file size of the executable
- **Flash footpring**: cosy 
- **RAM Usage**: cosy + `malloc_monitor`
- **Load Time + Execution Time**: ztimer

Average of **5** Executions.
</div>

::right::

<div class="flex justify-center flex-col h-full">

**Hardware:** Adafruit Feather nRF52840 Sense
- CPU: ARM Cortex M4F (64 MHz)
- 1 MB flash
- 256 KB SRAM

</div>