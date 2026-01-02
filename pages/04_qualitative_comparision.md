
# Qualitative Comparision

<div class="grid grid-cols-2 gap-4 m-t-8 categories">
    <div>
        <material-symbols-code class="text-6xl w-full font-center"/>
        <strong class="font-center">Development</strong>
        <ul>
            <li>Automatic Memory Management</li>
            <li>Application Portability,...</li>
        </ul>
    </div>
    <div>
        <material-symbols-engineering class="text-6xl w-full font-center"/>
        <strong>Operational</strong>
        <ul>
            <li>Updates At Runtime</li>
            <li>Remote Management,...</li>
        </ul>
    </div>
    <div>
        <material-symbols-security class="text-6xl w-full font-center"/>
        <strong>Security</strong>
        <ul>
            <li>Address Space Isolation</li>
            <li>Memory Usage Configuration,...</li>
        </ul>
    </div>
    <div>
        <material-symbols-memory class="text-6xl w-full font-center"/>
        <strong>Compilation Modes</strong>
        <ul>
            <li>JIT Compilation</li>
            <li>AOT Compilation,...</li>
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


---
hideInToc: true
---

## Qualitative Comparision Summary

<table>
    <thead>
        <tr>
            <th>Virtualization Technology</th>
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
        <tr><td class="first-col">Cape VM</td><td>✓</td><td>✓</td><td></td><td></td><td></td><td>✓</td><td></td><td></td><td>✓</td><td></td><td>✓</td><td>✓</td><td>✓</td><td></td><td></td><td>✓</td></tr>
        <tr><td class="first-col">Femto-Container</td><td></td><td>✓</td><td></td><td></td><td></td><td>✓</td><td></td><td></td><td>✓</td><td>✓</td><td>✓</td><td></td><td>✓</td><td></td><td></td><td></td></tr>
        <tr><td class="first-col">JerryScript</td><td>✓</td><td>✓</td><td></td><td>✓</td><td>✓</td><td>✓</td><td></td><td></td><td>✓</td><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr>
        <tr><td class="first-col">Lua</td><td>✓</td><td>✓</td><td></td><td>✓</td><td>✓</td><td>✓</td><td></td><td></td><td>✓</td><td></td><td>✓</td><td>✓</td><td></td><td></td><td></td><td></td></tr>
        <tr><td class="first-col">MicroPython</td><td>✓</td><td>✓</td><td>✓</td><td>✓</td><td></td><td>✓</td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr>
        <tr><td class="first-col">nanoframework</td><td>✓</td><td>✓</td><td>✓</td><td>✓</td><td>✓</td><td>✓</td><td></td><td></td><td>✓</td><td></td><td></td><td></td><td>✓</td><td></td><td></td><td></td></tr>
        <tr><td class="first-col">Toit</td><td>✓</td><td>✓</td><td>✓</td><td></td><td></td><td>✓</td><td>✓</td><td>✓</td><td>✓</td><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr>
        <tr><td class="first-col">Velox VM</td><td>✓</td><td>✓</td><td>✓</td><td>✓</td><td></td><td>✓</td><td></td><td></td><td>✓</td><td>✓</td><td>✓</td><td>✓</td><td>✓</td><td>✓</td><td></td><td></td></tr>
        <tr><td class="first-col">WAMR</td><td></td><td>✓</td><td>✓</td><td>✓</td><td></td><td>✓</td><td>✓</td><td></td><td>✓</td><td>✓</td><td>✓</td><td>✓</td><td></td><td></td><td></td><td>✓</td></tr>
        <tr><td class="first-col">WARDuino</td><td></td><td>✓</td><td>✓</td><td></td><td>✓</td><td>✓</td><td></td><td></td><td>✓</td><td>✓</td><td>✓</td><td>✓</td><td></td><td></td><td></td><td></td></tr>
        <tr><td class="first-col">Wasmico</td><td></td><td>✓</td><td></td><td></td><td></td><td>✓</td><td>✓</td><td>✓</td><td>✓</td><td>✓</td><td>✓</td><td>✓</td><td>✓</td><td></td><td></td><td></td></tr>
        <tr><td class="first-col">μBPF</td><td></td><td>✓</td><td></td><td></td><td></td><td>✓</td><td>✓</td><td></td><td>✓</td><td>✓</td><td>✓</td><td></td><td>✓</td><td></td><td></td><td>✓</td></tr>
    </tbody>
</table>
<div class="legend">✓ = implemented</div>

<style>
    table {
        border-collapse: collapse;
        width: 100%;
        font-family: sans-serif;
        font-size: 8px;
    }

    th, td {
        border: 1px solid #ddd;
        padding: 4px;
        text-align: center;
    }

    /* Header styling */
    th {
        background-color: #f2f2f2;
        height: 150px;
        white-space: nowrap;
    }

    /* Vertical text for headers */
    .vertical-text {
        writing-mode: vertical-rl;
        transform: rotate(180deg);
        text-align: left;
        font-weight: bold;
        height: 100%;
    }

    /* Zebra striping: light blue for even rows */
    tr:nth-child(even) {
        background-color: var(--blau-2);
    }

    .first-col {
        text-align: left;
        font-weight: bold;
        white-space: nowrap;
    }

    caption {
        padding: 10px;
        font-weight: bold;
    }

    .legend {
        font-size: 11px;
        text-align: left;
        margin-top: 5px;
    }
</style>

<!--
**Generally** operational and development features vary between solution | 
**Universally Provided:** Application Portability, Updates at Runtime | **Address Space Isolation:** implemented by all except MicroPython, **AOT** is supported by some, ahowever not solution supports JIT. 

-->

    