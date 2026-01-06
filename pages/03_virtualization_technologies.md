---
layout: two-cols-header
---

# What is Virtualization?

::left::
**Definition** by Popek and Goldberg (1974):
- virtual Guest and real Host  
- Map Guest state and operation to Host

<div class="py-8" />

**Categorization** by J. E. Smith and Nair (2005)
<div class="taxonomy grid gap-x-4 gap-y-8 text-center">
    <div class="border rounded-md py-2">Same ISA</div>
    <div class="py-2">vs.</div>
    <div class="border rounded-md py-2">Different ISA</div>
    <div class="border rounded-md py-2">System VM</div>
    <div class="py-2">vs.</div>
    <div class="border rounded-md py-2">Process VM</div>
</div>

::right::
<div class="h-full flex flex-col items-center justify-center">
    <img src="../assets/Virtualization conceptually.png" width="300px" />
</div>

<style>
.taxonomy {
    grid-template-columns: 1fr auto 1fr;
    width: 70%;
}

p:first-child {
    margin-bottom: 2px;
}

.border {
    border-color: var(--brillantblau);
    border-width: 2px;
}
</style>

<!--
**Virtualization** divides a system into guest + host
<br /> This new Layer is an opportunity to add new features.  
<br /> 
<br /> different kind of each **implementations** 
<br /> following this categorization each can be assigned on of **four** types / approach
<br /> only one approach is relevant to constrained devices
<br /> categorization is based on **two properties**
<br />**ISA:** memory model + instruction (e.g. add, sub, ...) 
<br />**System** => emulates a whole system for **multiple** Applications including an OS
<br />
-->

---
clicks: 5
---

## Virtualization Categories


<div class="virtualizations">
    <div />
    <div class="text-center">Same ISA</div>
    <div class="text-center">Different ISA</div>
    <div class="flex justify-center items-center">System VM</div>
    <div class="flex justify-center items-center"><img :class="{gray: $clicks > 1}" src="../assets/classic-system-vm.png" /></div>
    <div class="flex justify-center items-center"><img :class="{gray: $clicks > 2}"src="../assets/whole-system-vm.png" /></div>
    <div class="flex justify-center items-center">Process VM</div>
    <div class="flex justify-center items-center"><img :class="{gray: $clicks > 3}" src="../assets/os-level-container.png"/></div>
    <div class="flex justify-center items-center"><img src="../assets/high-level-language-vm.png"/></div>
    <Spotlight
        :active-clicks="[1,2,3,4]"
        :x="[20.5,65.2,20.5,65.2]"
        :y="[13,9.5,60,66.5]"
        :w="[24.5,24.5,24.5,24.5]"
        :h="[37,44.5,30.5,22]"
    />
</div>

<style>
.virtualizations {
    position: relative;
    display: grid;
    grid-template-columns: auto 1fr 1fr;
    margin-top: 32px;
}

img {
    width: 240px;
    transition: filter 0.5s ease-in-out;
}

.gray {
    filter: grayscale(100%);
}
</style>

<!--
**Same ISA System VM:** VMware, Virtualbox, relies on CPU extension like Intel-V
<br />**Different ISA System VM:** QEMU, emulates **different** hardware target, to complex for constrained devices **cpu** / **memory**
<br />**Same ISA Process VM:** Docker, LXC: rely on special operating system mechanisms
<br />**Different ISA Process VM:** Java VM, don't have to emulate a whole other hardware with all its state, but only keep state for executing a single program => efficient 

<br /> **Only** feasible solution

<br /> **End:** All the evaluated virtual machines are of *this* type
-->
