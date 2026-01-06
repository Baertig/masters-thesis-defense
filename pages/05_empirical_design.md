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
            <li>Classification </li>
            <li>HLL VM Architecture </li>
            <li>Benchmark 
                <ol>
                    <li>Design</li>
                    <li>Implementation</li>
                    <li>Results</li>
                </ol>
            </li>
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

.container {
    display: grid;
    grid-template-columns: 2fr 3fr;
    height: 100%;
}
</style>

<!--
**classify** into two groups
<br /> present basic architecture shared by **all** => basis to understand the (nature of the) overhead
<br
-->

---

## Candidates

<div class="candidates" >
    <div class="dynamic"><logos-javascript />JerryScript </div>
    <div class="dynamic"><logos-python />Micropython</div>
    <div class="dynamic"><logos-lua />Lua</div>
    <div class="static"><img src="../assets/ebpf-log.svg"/>Femto-Container</div>
    <div class="static"><img src="../assets/ebpf-log.svg"/>µBPF</div>
    <div class="static"><logos-webassembly /><span class="text-center"><strong>W</strong>eb<strong>A</strong>ssembly <strong>M</strong>icro <strong>R</strong>untime (WAMR)</span></div>
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

<!--
**Start:** All candidates are HLL VMs 
<br />**first row** are dynamic script languages, **input** to the engine is **text-based** script code
<br /> JerryScript and Micropython ==> specifically designed for low-resource devices
<br />Lua => lightweight language by design  

<br />**second row** all execute a form of pre-compiled bytecode
<br /> **Femto and µBPF** => research projects, ebpf, introduced in **Linux Kernel**, lightweight VM, 11 registers, 512-byte stack, **no heap**
<br /> WAMR => executes WebAssembly, compilation target for the browser, uses as **general-purpose** compilation target, with runtimes targeting different environments including constrained devices. **Two Modes** (evaluated separatly)

**End:** These six candidates **divided** into two categories
-->

---
clicks: 4
---

## Candidates Classification

<div class="m-t-8" />
<table style="position: relative">
    <Spotlight 
        :active-clicks="[1,2,3]" 
        :x="[23.5, 62.5, 82.5]" 
        :y="[11, 11, 11]" 
        :w="[39, 10.5, 7]" 
        :h="[89, 89, 89]" 
    />
    <thead>
        <tr style="border-bottom: 0px">
            <th />
            <th />
            <th colspan="3" style="text-align: center">Architectural Properties</th> 
            <th colspan="4" style="text-align: center">Feature Counts</th>
        </tr>
        <tr>
            <th />
            <th>HLL VM</th>
            <th>Garbage Collection</th>
            <th>Typing</th>
            <th>Bytecode Compilation</th>
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

<!--
**Start:** This table shows this **Categorization**
<br /> first column are the HLLVMs
<br /> then the architecutral properties, that are the reason for this classification
<br /> Feature-Counts from previous evaluation per feature category

<br /> **dynamic** => runtime object carry metadata information
<br /> source code compiled to **bytecode** 

**End:** All share the same **fundamental structure**
-->

---

## Fundamental HLL VM Architecture

<div class="m-t-16 flex items-center justify-center">
    <img src="../assets/VM architecture.png" width="500px"/>
</div>

<!--
**Start:** Bytecode Interpreter
<br /> execute bytecode instruction (opcode -> number; operands)
<br /> **processed** in 3 step **pipeline**
<br /> One of the main reason for overhead, executed for **every** instruction; for **native** programms done in hardware

<br />**End:** To measure the **exect** overhead => conducted **Benchmark**
-->

---
layout: full
---

<div class="container">
    <div class="heading">
        <h2>Benchmark</h2>
    </div>
    <div class="agenda">
        <ol>
            <li><strong>Design</strong>
                <ol>
                    <li>Metrics</li>
                    <li>Benchmark Programms</li>
                </ol>
            </li>
            <li><strong>Measurement Implementation</strong></li>
            <li><strong>Results</strong>
                <ol>
                    <li>Load Time</li>
                    <li>Execution Time</li>
                    <li>Code Size</li>
                    <li>ROM footprint</li>
                    <li>RAM usage</li>
                </ol>
            </li>
        </ol>
    </div>
</div>

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

.container {
    display: grid;
    grid-template-columns: 2fr 3fr;
    height: 100%;
}
</style>

<!--
**Start:** ....

<br />Detail for each metric the results
-->

---

## Design: Metrics

<img class="mt-8" src="../assets/application_execution_lifecycle.png" />

<div class="metrics mt-16 ml-12 mr-24 grid gap-4 ">
    <div>
        <div class="flex flex-col">
            <strong>Compilation</strong>
            <span><material-symbols-code />Code Size</span>
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

<!--
**Start:** To find relevant criteria: look at simple **Deployment Pipeline** (steps necessary to get the application to the device)
<br /> first produce a runable application artifact => how efficient is the **application encoded**
<br /> flash to device => footprint of the whole firmware image. 
<br /> then **Execution** RAM usage, measure runtime overhead in **2** metrics. How long does it take until the **first instruction** of the application is executed. 
<br /> **Execution** => how long to complete the workload.    

<br />**End:** ... which brings me to the benchmark programs.
-->

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

::right::

<div class="flex items-center justify-center">
    <img src="../assets/embench-iot-2-0.png" width="250px" />
</div>

<!--
**Start:** Designed to represent a set of benchmarks written in C, that represent common IoT Workloads. 
<br /> Each Programm is **modified** to run on the virtual machine.
<br /> Femto-Container and µBPF do **not** offer a **heap** region for dynamic memory allocations.
-->

---
layout: two-cols-header
---

## Implementation

::left::

<div class="flex justify-center flex-col h-full">

Implemented Measurements on top of **RIOT OS**

- **Code Size**: file size of the executable
- **Flash footprint**: cosy 
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

<!--
**Start:** All of the Virtual Machines run on top of RIOT OS. **Common Baseline** 
<br /> => enables a fair comparison
-->
