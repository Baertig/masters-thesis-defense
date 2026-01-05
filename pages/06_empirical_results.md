## Results: Code Size

<TwoColAnimated :active="$clicks >= 1">
    <template #left>
    <span v-click>
        <strong>Key Insights</strong>
        <ul>
            <li>Bytecode encoding more efficient than text based</li>
            <li>`0x77073096` 4 bytes as 32-bit int vs. 10 bytes in ASCII</li>
        </ul>
    </span>
    </template>
    <template #right>
        <img src="../assets/code_size.png"/>
    </template>
</TwoColAnimated>

<!--
**y-axis:** size in bytes  |  **x-axis**: each VM, grouped by type and benchmark.  
constant from the crc_32 benchmark
-->

---
clicks: 3
---

## Results: Flash footprint

<TwoColAnimated :active="$clicks >= 1">
    <template #left>
        <span v-click>
            <strong>Key Insights</strong>
            <ul>
               <li>Dynamic VMs occupy more space</li> 
               <li>femto container ~40 Kib lowest footprint</li>
            </ul>
        </span>
    </template>
    <template #right>
        <Spotlight 
            :active-clicks="[2]" 
            :x="[34]" 
            :y="[70]" 
            :w="[1.8]" 
            :h="[25]" 
        />
        <img src="../assets/flash_memory.png" />
    </template>
</TwoColAnimated>

<!--**Dynamic VMs** include compiler, garbage collection + type handling logic | **femto container** => minimal implementation without data relocations-->

---

## Results: RAM usage

<div v-click="[2,3]" class="absolute top-15 right-30">
    <img src="../assets/dynamic-vms-data-duplication.svg" width="400px" />
</div>

<TwoColAnimated :active="$clicks >= 1">
    <template #left>
        <span v-click>
            <strong>Key Insights</strong>
            <ul>
                <li>Dynamic VMs incur highest RAM (data duplication)</li>
                <li>Lua has overall highest footprint</li>
            </ul>
        </span>
    </template>
    <template #right>
        <img class="mt-16" src="../assets/RAM_usage.png" />
    </template>
</TwoColAnimated>

<!--
**WAMR**: moderate RAM usage => runtime structures occupy more space  
Why is µBPF only blue? all allocations are done on the system stack / this could only be assigned one label. It is not precise.
-->

---
clicks: 3
---

## Results: Load Time

<TwoColAnimated :active="$clicks >= 1">
  <template #left>
    <span v-click> 
        <strong>Key Insights</strong>
        <ul>
            <li>Load Time of dynamic VMs <strong>orders of magnitude</strong> higher</li>
            <li><strong>Reason:</strong> Bytecode compilation overhead</li>
            <li>WAMR (fast) longest load time of <strong>static VMs</strong></li>
        </ul>
    </span>
  </template>

  <template #right>
    <Spotlight 
        :active-clicks="[2]" 
        :x="[48]" 
        :y="[9]" 
        :w="[19]" 
        :h="[84]" 
    />
    <img src="../assets/load_time.png" />
  </template>

</TwoColAnimated>


---
clicks: 4
---

## Results: Execution Time

<TwoColAnimated :active="$clicks >= 1">
    <template #left>
        <span v-click>
            <strong>Key Insights</strong>
            <ul>
                <li>HLL VMs impose significant slowdown (16x at best)</li>
                <li>WAMR (fast) most efficient (24x avg)</li>
                <li>Dynamic VMs are slower than static VMs</li>
                <li>Lua is the fastest of the dynamic VMs (~60x), except for string operations</li>
            </ul>
        </span>
    </template>
    <template #right>
        <Spotlight 
            :active-clicks="[2,3]" 
            :x="[84,94.7]" 
            :y="[5,70]" 
            :w="[13.5,2.5]" 
            :h="[86, 20]" 
        />
        <img src="../assets/execution_time_to_native.png"/>
    </template>
</TwoColAnimated>
