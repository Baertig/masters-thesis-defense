## Results: Load Time

<TwoColAnimated :active="$clicks >= 1">
  <template #left>
    <span v-click> 
        <strong>General</strong>
        <ul>
            <li>Load Time of dynamic VMs <strong>orders of magnitude</strong> higher</li>
            <li><strong>Reason:</strong> Bytecode compilation overhead</li>
        </ul>
    </span>
    <span v-click> 
        <strong>Dynamic VMs:</strong>
        <ul>
            <li>Micropython least performant</li>
            <li><strong>Reason:</strong> JerryScript and Lua emit bytecode directly</li>
        </ul>
    </span>
    <span v-click> 
        <strong>Static VMs:</strong> 
        <ul>
            <li>eBPF based are faster</li>
            <li><strong>Reason:</strong> WASM file complexity</li>
            <li>WAMR (fast) longest load time</li>
            <li><strong>Reason:</strong> custom bytecode format</li>
        </ul> 
    </span>
  </template>

  <template #right>
    <!-- <Spotlight 
        :active="$clicks === 2" 
        :x="13" 
        :y="24" 
        :w="2.5" 
        :h="60" 
    /> -->
    <img src="../assets/load_time.png" />
  </template>

</TwoColAnimated>


---

## Results: Execution Time

<TwoColAnimated :active="$clicks >= 1">
    <template #left>
        <span v-click>
            <strong>General</strong>
            <ul>
                <li>HLL VMs impose significant slowdown (16x at best)</li>
                <li>WAMR (fast) most efficient (24x avg)</li>
                <li>Dynamic VMs are slower than static VMs</li>
            </ul>
        </span>
        <span v-click>
            <strong>Dynamic VMs</strong>
            <ul>
                <li>Lua is the fastest</li>
                <li>...except for string heavy operations</li>
            </ul>
        </span>
        <span v-click>
            <strong>Static VMs</strong>
            <ul>
                <li>WAMR (fast) ~2.4x faster than WAMR</li>
                <li>Femto container ~2.1x faster than µBPF</li>
            </ul>
        </span>
    </template>
    <template #right>
        <img src="../assets/execution_time_to_native.png"/>
    </template>
</TwoColAnimated>

---

## Results: Code Size

<TwoColAnimated :active="$clicks >= 1">
    <template #left>
    <span v-click>
        <strong>General</strong>
        <ul>
            <li>Bytecode encoding more efficient than text based</li>
            <li><strong>ud exception</strong>: eBPF overhead due to spill code + 32-bit cast</li>
        </ul>
    </span>
    <span v-click>
        <strong>Static VMs</strong>
        <ul>
            <li>WASM more efficient than eBPF</li>
        </ul>
    </span>
    </template>
    <template #right>
        <img src="../assets/code_size.png"/>
    </template>
</TwoColAnimated>



---

## Results: Flash footprint

<TwoColAnimated :active="$clicks >= 1">
    <template #left>
        <span v-click>
            <strong>General</strong>
            <ul>
               <li>Dynamic VMs occupy more space</li> 
            </ul>
        </span>
        <!-- <span v-click>
            <strong>RFC 7228</strong>
            <ul>
                <li>Class 0: Femto-Container</li>
                <li>Class 1: µBPF, WAMR, WAMR (fast)</li>
                <li>Class 2: JerryScript, MicroPyton, Lua</li>
            </ul>
        </span> -->
        <span v-click>
            <strong>Dynamic VMs</strong>
            <ul>
                <li>JerryScript crc_32: es.next modul</li>
                <li>Lua does not offer conditional module inclusion</li>
            </ul>
        </span>
        <span v-click>
            <strong>Static VMs</strong>
            <ul>
                <li>µBPF overhead: more features</li>
                <li>WAMR (fast) slight overhead over WAMR</li>
            </ul>
        </span>
    </template>
    <template #right>
        <img src="../assets/flash_memory.png" />
    </template>
</TwoColAnimated>

---

## Results: RAM usage

<TwoColAnimated :active="$clicks >= 1">
    <template #left>
        <span v-click>
            <strong>General</strong>
            <ul>
                <li>Dynamic VMs incure highest RAM (data duplication)</li>
            </ul>
        </span>
        <span v-click>
            <strong>Dynamic VMs</strong>
            <ul>
                <li>Lua has overall highest footprint</li>
            </ul>
        </span>
        <span v-click>
            <strong>Static VMs</strong>
            <ul>
                <li>WAMR requries relatively high RAM</li>
                <li>eBPF based VMs are the most RAM friendly</li>
            </ul>
        </span>
    </template>
    <template #right>
        <img class="mt-16" src="../assets/RAM_usage.png" />
    </template>
</TwoColAnimated>