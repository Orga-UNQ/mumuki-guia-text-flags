En una arquitectura Von Neumann, la ejecución de los programas se traduce en recuperar instrucciones que estan fisicamente consecutivas en la memoria principal. Esto no ocurre al ejecutar un CALL o un RET, pues se necesita una bifurcación en el flujo de control, mediante la modificación controlada del registro PC. 
Se necesita implementar:

```
Si el contenido de R0 es mayor a 1
      entonces R0=R0-1
```

Esto lo podemos reescribir como:
1. Comparar el contenido de R0 con 1
2. Si es menor saltar a ```E```
3. R0=R0-1
4. E: ...

¿Que tiene que agregarse a Q para poder hacer lo anterior? Veamos, la instrucción ```si es menor saltar``` es un **salto condicional**. ¿Cuál es el efecto que se espera?  

* debe reemplazarse el valor de PC con el valor de E. 
* esto debe ocurrir sólo si se cumple la condición

El salto condicional altera el valor de PC cuando se cumple una condición. Esto lo hace muy similar al CALL, pero ojo  :exclamation: **sin almacenar en la pila**. 

Entonces el formato de esta instrucción debe ser también similar (un operando origen). A esto volveremos más adelante  :relaxed:

#### Representar la condición

El desafío es ahora representar la condición. En general las condiciones están asociadas a una comparación de un valor con otro (por ej: R0=1)
Para evaluar la igualdad: Con las herramientas que tenemos (set de instrucciones de Q3) es posible resolver esto con una resta, y si el resultado es cero entonces ambos operandos son iguales:

```
SUB R0, 0x000
saltarSiResultadoEsCero E
```