---
layout: two-cols-header
---

# Conclusion

::left::

**Qualitative Comparison**

Universal Features: 
- Portability
- Updates at Runtime
- Memory Isolation

<v-click at="2">

**Outlook**

- Vary hardware targets
- Add virtualization technologies
- Explore on-board AOT compilation capabilities

</v-click>

::right::

<v-click at="1">

**Empirical Evaluation**

Substantial Performance Cost

Developer-friendly **Dynamic** VMs vs. Performance and Security focused **Static** VMs 

Recommendations for Use Cases:
- **WAMR** as a default choice
- **Lua** for developer experience
- **Femto-Container** for memory constrained use-cases

</v-click>

<!--
Add **Capabilites** not supported by native hardware. Solve challenges mentioned at the beginning.
<br />
<br />**Runtime**: Best case (16x)
<br />**Load Time**: => add startup latency
<br />RAM usage + Flash Footprint increases
<br />VMs offer different trade-offs => There is not one solution for all use-cases
<br />
<br />**WAMR** => fastest runtime / two modes flexibility / moderate memory requirements
<br />**Lua** => Lua by far **fastes execution time** among dynamic VMs (except for string operations) 
<br />**Femto-Container** => low-memory  / **BUT:** reduced features i.e. **no** heap
-->
