### Fun with Flags

Como dijimos, los flags son señales que se usan para caracterizar el resultado de la ALU y cada uno indica una condición distinta. 


Los flags de nuestra arquitectura son 4:

* Z (Zero): se enciende cuando el resultado es todo cero
* N (Negative): se enciende cuando el primer bit es uno.
* C (Carry): un par de pantallas mas adelante,  :point_right:
* V (Overflow):  un par de pantallas mas adelante,  :point_right:

Además, la arquitectura debe proveer instrucciones que permitan ver su valor y actuar en consecuencia, así podemos utilizar los flags desde los programas.
**Estas instrucciones se denominan saltos**, y un ejemplo es la pseudo instrucción que mencionamos antes:  ```saltarSiResultadoEsCero```.

### La instrucción JE

La instrucción **JE** es un salto condicional que altera el PC si se cumple la condición de salto: ```Z```, es decir, cuando Z vale 1.

Si volvemos al ejemplo donde queríamos determinar si R0 tenía el valor 1 (R0 = 1   sii  R0-1=0) teníamos un programa:

```
SUB R0, 0x001
saltarSiResultadoEsCero E
```

Ahora lo reescribimos:

```
   SUB R0, 0x001
   JE E
   CALL otraRutinaQueDebeEjecutarseSiNoSonIguales
E: RET

```

### Practicando

Escribir una rutina que deje el valor 10 en el registro R5 si el valor de la celda E456 es 8.