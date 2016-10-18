## Las instruccióones JN y JC

Como dijimos antes, para determinar si un número es mayor a otro (o si es menor) puede ser posible considerando el bit mas significativo, y por se calcula el flag N, pero veamos el siguiente caso: **0000-1100=0100** 

Vemos que el resultado no empieza con 1, asi que en estos casos no alcanza con ese flag. Interpretemos operandos y resultados

|cadenas| Ibss|Ica2|
|:---:|:---:|:---:|
|0000|0|0|
|1100|12|-4|
|0100|4|4|

Podemos ver que al resolver la cuenta se produjo un acarreo.
