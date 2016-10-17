### ¿Cuál es mayor?

Pensemos ahora en como usar lo anterior para comparar dos números. Veamos que si A-B>0 entonces A>B. De aquí que para determinar si A>B, se debe realizar la resta A-B y ver si el resultado es mayor a cero.

Entonces el problema se traslada a determinar si el resultado es positivo o negativo... y eso ya aprendimos a hacerlo! Observando el primer bit de la cadena. Claro que **esto no sirve en cualquier sistema** pero si en complemento a 2. 

Pasando en limpio, necesitamos una señal que se encienda cuando el primer bit del resultado es 1.

!["flag Negative"](https://github.com/Orga-UNQ/mumuki-guia-text-flags/blob/master/images/ALU-con-flagCyN.png?raw=true "flag Negative") 

Esta señal se denomina **Flag Negative** o Flag N.

### A trabajar en otro circuito


Diseñá un circuito que calcule el flag N a partir de una resta en BSS(4). Considerá que contás con un restador de 4 bits y que sus salidas se llaman: r0, r1, r2 y r3.

