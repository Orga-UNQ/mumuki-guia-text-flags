### Saltar si se cumple la condición

En una arquitectura Von Neumann, la ejecución de los programas se traduce en recuperar instrucciones que estan fisicamente consecutivas en la memoria principal. Esto no ocurre al ejecutar un CALL o un RET, pues se necesita una bifurcación en el flujo de control, mediante la modificación controlada del registro PC. 
Se necesita implementar:

```
Si el contenido de R0 es 1
      entonces R0=R0-1
```

Esto lo podemos reescribir como:
1. Comparar el contenido de R0 con 1
2. Si es distinto saltar a ```E```
3. R0=R0-1
4. E: ...

¿Que tiene que agregarse a Q para poder hacer lo anterior? Veamos, la instrucción ```si es distinto saltar``` es un **salto condicional**. ¿Cuál es el efecto que se espera?  

* debe reemplazarse el valor de PC con el valor de E. 
* esto debe ocurrir sólo si se cumple la condición

El salto condicional altera el valor de PC cuando se cumple una condición. Esto lo hace muy similar al CALL, pero ojo  :exclamation: **sin almacenar en la pila**. 

Entonces el formato de esta instrucción debe ser también similar (un operando origen). A esto volveremos más adelante  :relaxed:

#### Representar la condición

El desafío es ahora representar la condición. En general las condiciones están asociadas a una comparación de un valor con otro, y en este caso, el registro R0 y la constante 1.

Con las herramientas que tenemos (repertorio de instrucciones de Q3) es posible evaluar la igualdad con una resta:

> R0 = 1   sii  R0-1=0

y si el resultado es cero entonces ambos operandos son iguales:

```
SUB R0, 0x001
saltarSiResultadoEsCero E
```

¿Cómo se implementa esta nueva instrucción ```saltarSiResultadoEsCero```? Se necesita **caracterizar el resultado  de la ALU**. Supongamos que ahora la ALU tiene, además de el resultado, una señal que se enciende cuando el resultado es cero. 

Gráficamente sería algo como lo siguiente:

![](https://github.com/Orga-UNQ/mumuki-guia-text-flags/blob/master/images/ALU-con-flag.png?raw=true)

#### Flags

Esta señal es una de varias que lleva la ALU y que se denominan **flags** o banderas. En particular, este es el **flag Zero**, o **Flag Z**.

### A trabajar

Diseñá un circuito que calcule el flag Z a partir de una resta en BSS(4). Considerá que contás con un restador de 4 bits y que sus salidas se llaman: r0, r1, r2 y r3.
