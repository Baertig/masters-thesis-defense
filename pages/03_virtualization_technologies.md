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
- Classic System VMs
- Whole System VMs
- OS-Level Container
- High-Level Virtual Machine

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
    <div class="flex justify-center flex-col items-center"><img :class="{gray: $clicks > 1}" src="../assets/classic-system-vm.png" /> </div>
    <div class="flex justify-center flex-col items-center"><img :class="{gray: $clicks > 2}"src="../assets/whole-system-vm.png" /></div>
    <div class="flex justify-center flex-col items-center"><img :class="{gray: $clicks > 3}" src="../assets/os-level-container.png"/></div>
    <div class="flex justify-center flex-col items-center"><img src="../assets/high-level-language-vm.png"/></div>
    <Spotlight
        :active-clicks="[1,2,3,4]"
        :x="[12,62.2,12,62.2]"
        :y="[6,3,56.5,64]"
        :w="[25.2,25,25.2,24.8]"
        :h="[41.5,48,33.7,24]"
    />
</div>

<style>
.virtualizations {
    position: relative;
    display: grid;
    grid-template-columns: 1fr 1fr;
    margin-top: 32px;
    font-size: 14px;
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
**Classic System VM:** VMware, Virtualbox, relies on CPU extension like Intel-V
<br />**Whole System VM** QEMU, emulates **different** hardware target, to complex for constrained devices **cpu** / **memory**
<br />**OS-Level Container:** Docker, LXC: rely on special operating system mechanisms
<br />**HLL VM:** Java VM, don't have to emulate a whole other hardware with all its state, but only keep state for executing a single program => efficient 

<br /> **Only** feasible solution

<br /> **End:** All the evaluated virtual machines are of *this* type
-->
