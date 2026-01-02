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


<!-- <div class="content h-full" :class="{ active: $clicks >= 1 }">
    <div class="flex flex-col items-center justify-center description gap-4">
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
    </div>
    <div class="flex items-center justify-center">
        <div class="relative p-4 rounded-md" style="overflow: hidden">
            <Spotlight 
                active 
                v-click
                :x="13" 
                :y="24" 
                :w="2.5" 
                :h="60" 
            />
            <img src="../assets/load_time.png" width="100%"/>
        </div>
    </div>
</div>

<style>
img {
    object-fit: contain;
}

.content {
    display: grid;
    gap: 4px;
    grid-template-columns: 0fr 1fr;
    transition: grid-template-columns 0.5s ease-in-out;
}

.content.active {
    grid-template-columns: 1fr 4fr;
}

.description {
    font-size: 10px;
    min-width: 0;
    min-height: 0;
}

.active .description :first-child {
    transition: opacity 0.4s ease-out 0.4s;
}
</style> -->

---

## Results: Execution Time

<img class="mt-16" src="../assets/execution_time_to_native.png"/>

---

## Results: Code Size

<div class="flex items-center justify-center mt-16">
    <img src="../assets/code_size.png" width="85%"/>
</div>


---

## Results: Flash footprint

<img class="mt-16" src="../assets/flash_memory.png" />

---

## Results: RAM usage

<img class="mt-16" src="../assets/RAM_usage.png" />