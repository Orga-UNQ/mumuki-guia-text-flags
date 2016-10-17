### El caso 'sino'

Imaginemos que se debe implementar un programa que lleve a cabo una acción cuando se cumple una condición y **otra acción** diferente en el caso contrario.

Por ejemplo: si los valores en R5 y R6  son iguales, ponga en R2 un 1 **ó 0 en caso contrario**.

```
   SUB R5,R6
   JE soniguales
   MOV R2, 0x0000
sonIguales: MOV R2, 0x0001
```

Pero este programa tiene un problema :fearful:. Si la condicion de salto no se cumple, se ejecuta el ```MOV R2,0x0000``` y luego tambien el ```MOV R2,0x0001```. Es decir que este último MOV siempre se ejecuta.

Para corregir esta situación, incluiremos en nuestro repertorio una nueva instrucción: El **salto incondicional JMP**, cuyo efecto es modificar PC para desviar hacia una etiqueta, pero sin evaluar condiciones en los flags. Su sintaxis es: ```JMP etiqueta```, y en el ejemplo anterior se agrega:


```
   SUB R5,R6
   JE soniguales
   MOV R2, 0x0000
   JMP fin
sonIguales: MOV R2, 0x0001
fin: ...
```
