---
layout: full
---

<div class="container">
    <div class="heading">
        <h2>Qualitative Comparison</h2>
    </div>
    <div class="agenda">
        <ol>
            <li>Feature Categories</li>
            <li>Summary Table</li>
        </ol>
    </div>
</div>

<!--**Comparison** Based on the Implemented Features, **Table:** cannot cover all of it => focus on *key* insights.-->

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

<!--
**Start:** focus on features (16 in total)
<br /> across **4** different categories => briefly present each + one example feature of each
<br /> table + insights that can be drawn from it.
-->

---

## Feature Categories

<div class="grid grid-cols-2 gap-4 m-t-8 categories">
    <div>
        <material-symbols-code class="text-6xl w-full font-center"/>
        <strong class="font-center">1. Development</strong>
        <ul>
            <li>Automatic Memory Management</li>
            <li>...</li>
        </ul>
    </div>
    <div>
        <material-symbols-engineering class="text-6xl w-full font-center"/>
        <strong>2. Operational</strong>
        <ul>
            <li>Updates At Runtime</li>
            <li>...</li>
        </ul>
    </div>
    <div>
        <material-symbols-security class="text-6xl w-full font-center"/>
        <strong>Security</strong>
        <ul>
            <li>3. Address Space Isolation</li>
            <li>...</li>
        </ul>
    </div>
    <div>
        <material-symbols-memory class="text-6xl w-full font-center"/>
        <strong>4. Compilation Modes</strong>
        <ul>
            <li>JIT Compilation</li>
            <li>...</li>
        </ul>
    </div>
</div>

<style>
    .categories div{
        display: flex;
        flex-direction: column;
        justify-content: center;
        background-color: var(--blau-2);
        border-radius: 4px;
        padding: 8px;

    }
</style>

<!--
**1. Cat**: Features that ease development
<br /> ... he doesn't have to implement allocations / deallocations **manually**
<br />**2. Cat** decrease the effort of maintenance and operating 
<br />...  update behavior of the device without a **full reboot** (at runtime)
<br />**3. Cat** Increase Security
<br />... limit the address space a device can access
<br /> constrained device usually only **limited hardware** mechanisms to implement this
<br />**4. Cat**  

**End:**
-->

---
hideInToc: true
---

## Qualitative Comparison Summary

<TwoColAnimated :active="$clicks >= 1" :is-image="false" style="height: 92%">
    <template #left>
        <span v-click>
            <strong>Universal Features:</strong>
            <ul>
                <li>Portability of the Executable</li>
                <li>Updates at Runtime</li>
                <li>Address Space Isolation, Except for Micropython</li>
            </ul>
        </span>
        <span v-click="'+4'">Three Solutions suppore <strong>AOT</strong> Compilation
        <br />
        However, none support <strong>JIT</strong> Compilation
        </span>
    </template>
    <template #right>
        <table style="position: relative; overflow: hidden">
            <Spotlight 
                :active-clicks="[2,3,4,5]" 
                :x="[25, 43.4, 57.5, 85.4]" 
                :y="[5, 5, 5, 5]" 
                :w="[4.5, 4.5, 4.5, 15]" 
                :h="[95, 95, 95, 95]" 
            />
            <thead>
                <tr>
                    <th></th>
                    <th colspan="5">Development</th>
                    <th colspan="3">Operation</th>
                    <th colspan="6">Security</th>
                    <th colspan="2">Compilation</th>
                </tr>
                <tr>
                    <th>Virtual Machine</th>
                    <th><div class="vertical-text">Automatic Memory Management</div></th>
                    <th><div class="vertical-text">Portability of the Executable</div></th>
                    <th><div class="vertical-text">Hardware Abstraction Layer</div></th>
                    <th><div class="vertical-text">Runtime Portability</div></th>
                    <th><div class="vertical-text">On-board Debugging</div></th>
                    <th><div class="vertical-text">Updates at Runtime</div></th>
                    <th><div class="vertical-text">Remote Application Management</div></th>
                    <th><div class="vertical-text">Remote Monitoring</div></th>
                    <th><div class="vertical-text">Address Space Isolation</div></th>
                    <th><div class="vertical-text">Address Space Configuration</div></th>
                    <th><div class="vertical-text">Memory Usage Restriction</div></th>
                    <th><div class="vertical-text">Memory Usage Configuration</div></th>
                    <th><div class="vertical-text">CPU Usage Restriction</div></th>
                    <th><div class="vertical-text">CPU Usage Configuration</div></th>
                    <th><div class="vertical-text">JIT Compilation</div></th>
                    <th><div class="vertical-text">AOT Compilation</div></th>
                </tr>
            </thead>
            <tbody>
                <tr v-click.hide="7"><td class="first-col">Cape VM</td><td><material-symbols-check /></td><td><material-symbols-check /></td><td></td><td></td><td></td><td><material-symbols-check /></td><td></td><td></td><td><material-symbols-check /></td><td></td><td><material-symbols-check /></td><td><material-symbols-check /></td><td><material-symbols-check /></td><td></td><td></td><td><material-symbols-check /></td></tr>
                <tr><td class="first-col">Femto-Container</td><td></td><td><material-symbols-check /></td><td></td><td></td><td></td><td><material-symbols-check /></td><td></td><td></td><td><material-symbols-check /></td><td><material-symbols-check /></td><td><material-symbols-check /></td><td></td><td><material-symbols-check /></td><td></td><td></td><td></td></tr>
                <tr><td class="first-col">JerryScript</td><td><material-symbols-check /></td><td><material-symbols-check /></td><td></td><td><material-symbols-check /></td><td><material-symbols-check /></td><td><material-symbols-check /></td><td></td><td></td><td><material-symbols-check /></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr>
                <tr><td class="first-col">Lua</td><td><material-symbols-check /></td><td><material-symbols-check /></td><td></td><td><material-symbols-check /></td><td><material-symbols-check /></td><td><material-symbols-check /></td><td></td><td></td><td><material-symbols-check /></td><td></td><td><material-symbols-check /></td><td><material-symbols-check /></td><td></td><td></td><td></td><td></td></tr>
                <tr><td class="first-col">MicroPython</td><td><material-symbols-check /></td><td><material-symbols-check /></td><td><material-symbols-check /></td><td><material-symbols-check /></td><td></td><td><material-symbols-check /></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr>
                <tr v-click.hide="7"><td class="first-col">nanoframework</td><td><material-symbols-check /></td><td><material-symbols-check /></td><td><material-symbols-check /></td><td><material-symbols-check /></td><td><material-symbols-check /></td><td><material-symbols-check /></td><td></td><td></td><td><material-symbols-check /></td><td></td><td></td><td></td><td><material-symbols-check /></td><td></td><td></td><td></td></tr>
                <tr v-click.hide="7"><td class="first-col">Toit</td><td><material-symbols-check /></td><td><material-symbols-check /></td><td><material-symbols-check /></td><td></td><td></td><td><material-symbols-check /></td><td><material-symbols-check /></td><td><material-symbols-check /></td><td><material-symbols-check /></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr>
                <tr v-click.hide="7"><td class="first-col">Velox VM</td><td><material-symbols-check /></td><td><material-symbols-check /></td><td><material-symbols-check /></td><td><material-symbols-check /></td><td></td><td><material-symbols-check /></td><td></td><td></td><td><material-symbols-check /></td><td><material-symbols-check /></td><td><material-symbols-check /></td><td><material-symbols-check /></td><td><material-symbols-check /></td><td><material-symbols-check /></td><td></td><td></td></tr>
                <tr><td class="first-col">WAMR</td><td></td><td><material-symbols-check /></td><td><material-symbols-check /></td><td><material-symbols-check /></td><td></td><td><material-symbols-check /></td><td><material-symbols-check /></td><td></td><td><material-symbols-check /></td><td><material-symbols-check /></td><td><material-symbols-check /></td><td><material-symbols-check /></td><td></td><td></td><td></td><td><material-symbols-check /></td></tr>
                <tr v-click.hide="7"><td class="first-col">WARDuino</td><td></td><td><material-symbols-check /></td><td><material-symbols-check /></td><td></td><td><material-symbols-check /></td><td><material-symbols-check /></td><td></td><td></td><td><material-symbols-check /></td><td><material-symbols-check /></td><td><material-symbols-check /></td><td><material-symbols-check /></td><td></td><td></td><td></td><td></td></tr>
                <tr v-click.hide="7"><td class="first-col">Wasmico</td><td></td><td><material-symbols-check /></td><td></td><td></td><td></td><td><material-symbols-check /></td><td><material-symbols-check /></td><td><material-symbols-check /></td><td><material-symbols-check /></td><td><material-symbols-check /></td><td><material-symbols-check /></td><td><material-symbols-check /></td><td><material-symbols-check /></td><td></td><td></td><td></td></tr>
                <tr><td class="first-col">μBPF</td><td></td><td><material-symbols-check /></td><td></td><td></td><td></td><td><material-symbols-check /></td><td><material-symbols-check /></td><td></td><td><material-symbols-check /></td><td><material-symbols-check /></td><td><material-symbols-check /></td><td></td><td><material-symbols-check /></td><td></td><td></td><td><material-symbols-check /></td></tr>
            </tbody>
        </table>
    </template>
</TwoColAnimated>

<style>

.animated-grid.active {
    grid-template-columns: 1fr 2fr;
}

table {
    border-collapse: collapse;
    width: 100%;
    font-size: 10px;
}

th, td {
    padding: 2px;
    text-align: center;
}

tr {
    border-bottom-width: 0;
}

thead tr {
    border-top: 1px solid #000;
    border-bottom: 1px solid #000;
}


th:first-child, td:first-child,
th:nth-child(6), td:nth-child(6),
th:nth-child(9), td:nth-child(9),
th:nth-child(15), td:nth-child(15) {
    border-right: 1px solid #000;
}

td:not(:first-child) {
    font-size: 12px;
    font-weight: 700;
    line-height: 0;
}

/* Header styling */
thead tr:nth-child(2) th {
    height: 175px;
    white-space: nowrap;
    text-align: center;
    vertical-align: bottom;
}

thead tr:first-child th:not(:last-child) {
    border-right: 1px solid #000;
    text-align: center;
}


/* Vertical text for headers */
.vertical-text {
    writing-mode: vertical-rl;
    transform: rotate(180deg);
    text-align: left;
    font-weight: bold;
    display: inline-block;
}

/* Zebra striping: light blue for even rows */
tbody tr:nth-child(even) {
    background-color: var(--blau-2);
}

.first-col {
    text-align: left;
    white-space: nowrap;
}
</style>

<!--
left-most column displays each evaluated virtual machine 
<br />**Generally** operational and development features vary between solution
<
<br />**Universally Provided:** Application Portability, Updates at Runtime | **Address Space Isolation:** implemented by all except MicroPython, **AOT** is supported by some, ahowever not solution supports JIT.
-->
