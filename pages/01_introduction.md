---
layout: two-cols-header
---

# Motivation

::left::

- 55 billion devices by **2035**

Deployment Domains: 
<div class="inline-grid grid-cols-2 grid-rows-2 gap-x-4 gap-y-4 m-b-4">
    <div class="domain"><material-symbols-watch-screentime />Wearables</div>
    <div class="domain"><material-symbols-house />Smart Home</div>
    <div class="domain"><material-symbols-health-metrics />Health Care</div>
    <div class="domain"><material-symbols-factory />Manifacturing</div>
    <div class="domain"><material-symbols-agriculture /> <span>Agricalture</span></div>
    <div class="domain">...</div>
</div>

**Consequence**: Application complexity grows

::right::

<div class="w-full h-full flex items-center justify-center">
    <img src="../assets/connected_devices_forcast.png" width="400px"/>
</div>

<span class="absolute bottom-12 right-2 text-xs max-w-md">Data from: IoT Analytics (Oct. 2025). State of IoT 2025. en-US. URL: https://iot-analytics.com/number-connected-iot-devices/ (visited on 11/25/2025).</span>


<!-- limited ressources 10kb to view hundered RAM; limited capabilies| From simple sensor value reading to **installing third-party** Apps during runtime -->
<style>
 .domain {
    text-align: center;
    padding: 4px 8px;
    border-width: 2px;
    border-color: var(--dunkelblau);
    border-radius: 8px;
    display: flex;
    gap: 8px;
    flex-direction: row;
    align-items: center;
    justify-content: center;
 }

</style>

<!--
Application Complexity developers face = more states / control flow / asynchronous  
network conditions / heterogeneous devices
-->

---
hideInToc: true
layout: full
---

<div class="container">
    <div class="left">
        <h3> <strong>Virtualization</strong> as an emerging paradigm for constrained devices </h3>
    </div>
    <div class="p-4 m-t-8">
        <strong>Potential Benefits: </strong>
        <ul class="m-b-4"> 
            <li>Memory Isolation</li>
            <li>Application Portability </li>
            <li>Usage of High-Level Programming Languages </li>
        </ul>
        <div class="m-b-4">Variety of different Solutions </div>
        <div class="font-bold m-b-2">Deployments: </div>
        <div class="inline-grid grid-cols-2 grid-rows-2 gap-x-4 gap-y-4 m-b-4">
            <div class="deployment"> <material-symbols-watch-screentime />FitBit LLC</div> 
            <div class="deployment"> <material-symbols-watch-screentime />Garmin LTD</div>
            <div class="deployment"> <material-symbols-house /> Moddable Tech Inc</div> 
            <div class="deployment"> <material-symbols-house />Tizen Project</div>
        </div>
        <div>
            <div class="research"> <material-symbols-search /> Lack of comprehensive Evaluations</div>
        </div>
    </div>
</div>

<style>
    .research {
        background-color: var(--blau-1);
        border-radius: 8px;
        text-align: center;
        color: var(--weiss);
        padding: 8px 0;
        margin-top: 56px;
    }

    .container {
        display: grid;
        grid-template-columns: 2fr 3fr;
        height: 100%
    }

    .left {
        background-color: var(--blau-2);
        color: var(--dunkelblau);
        display: flex;
        justify-content: center;
        align-items: center;
        padding: 8px;
    }

    .deployment {
        text-align: center;
        padding: 4px 8px;
        border-width: 2px;
        border-color: var(--dunkelblau);
        border-radius: 8px;
        display: flex;
        gap: 8px;
        flex-direction: row;
        align-items: center;
        justify-content: center;
    }
</style>

<!--
**RIOT OS** supports six solutions,
**Benefits:** Ease development + more security,
**Memory Isolation:** Important for constrained devices, because they lack hardware enforced isolation.
**Lack of Evaluations** ... to understand the trade-offs and pick the most suitable candidate for a use case
-->

---
hide: false
---

## Research Goals

<div class="goals grid grid-cols-3 gap-8">
    <div><img src="../assets/classify_approaches.png" /><span>Classify virtualization approaches</span></div>
    <div><img src="../assets/comparision_properties.png" /><span>Find relevant Comparision Properties</span></div>
    <div><img src="../assets/identify_tradeoffs.png" /><span>Identify Trade-offs</span></div>
</div>

<v-click>

<strong>Method:</strong>
<div class="method">
    <div class="step"> 1. Qualitative Feature Comparision </div>
    <div class="flex items-center justify-center">
        <material-symbols-keyboard-arrow-right class="text-4xl"/>
    </div>
    <div class="step"> 2. Empirical Evaluation on RIOT OS </div>
</div>

</v-click>


<style>
    .goals div {
        text-align: center;
        display: flex;
        flex-direction: column;
        justify-content: start;
        gap: 32px;
        align-items: center;
        padding: 32px;
    }

    .goals div img {
        height: 120px;
        width: auto;
    }

    .method {
        display: grid;
        grid-template-columns: 1fr auto 1fr;
        gap: 32px;
    }

    .method .step {
        background-color: var(--blau-1);
        border-radius: 8px;
        color: var(--weiss);
        text-align: center;
        padding: 16px;
    }
</style>

<!--
**Qualitative** comparision on the provided capabilites of a broad set of virtualization technologies.
**Empirical:** Quantify the Performance Overhead
-->
