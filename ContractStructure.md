# Estructura de un Contrato Inteligente

Escribiendo el contrato mínimo en Solidity, tenemos:

```solidity
// Empty.sol

contract Empty {
}
```

Hay una estructura `contract` con nombre y cuerpo; en
el caso de arriba, este cuerpo está vacío.

La línea que comienza con `//` es un comentario
que agregué para aclarar que este código podría
estar en un archivo de texto llamado `Empty.sol`, así
como podría estar en otro archivo de otro nombre. Pero
se acostumbra a que los archivos Solidity tengan extensión
`.sol`.

Si quisiéramos tener una variable interna, escribimos:

```solidity
// Counter.sol

contract Counter {
    uint counter;
}
```

Esta variable `counter` será parte del almacenamiento
asociado al contrato, mejor dicho a cada instancia de
contrato. Veremos que un contrato funciona como una
clase en otros lenguajes (Java, C#). Uno no despliega,
instala contratos en una blockchain, SINO INSTANCIAS, 
especímenes de ese contrato. Así que en el contrato de
arriba, podemos tener una instancia instalada que tenga
su variable de contrato `counter` con su valor asociado,
y tener OTRA instancia del mismo contrato, pero con otra
variable y su valor. Lo que se instala en una blockchain
resultan ser INSTANCIAS del contrato original, cada
una de las cuales tiene sus propias variables.
 
La variable `counter` así definida, tiene un tipo:
`uint`: es un número entero SIN signo (unsigned
integer). Vamos a ver en una próxima sección cuales
son los tipos de variables permitidos. Pero aprendamos
algo ahora: un `uint` es un entero de 32 bytes. Esto
puede sorprender, si estamos acostumbrados a otros lenguajes
donde los enteros pueden tener 4 u 8 bytes. Pero en Ethereum, 
en su máquina virtual, se manejan valores cuyo tamaño
natural son los 32 bytes. Esto es así para permitir
el manejo con comodidad de valores de `ether`, la moneda
nativa de Ethereum. Un `ether` es 10 ^ 18 unidades, y estamos
unidad se llama `wei`. Para manejar entonces tanto
el detalle de `weis` como de valores grandes de `ether` y otros
valores, como los hashes (de 32 bytes) y direcciones de cuenta (de
20 bytes), en Ethereum el tamaño natural de un número entero,
ya sea con signo o sin signo, es de 32 bytes.

En realidad, el tipo `uint` es un alias, equivalente al
tipo Solidity `uint256`, indicando que ocupa 256 bits.  Igual
veremos más adelante que en algún caso importa la diferencia,
y debemos recordar que, en el fondo, un `uint` es 
un `uint256`.

La variable `counter` que definimos arriba, vemos que
no tiene un valor inicial. Eso no significa que no tenga
nada o tenga un `null`. En el almacenamiento de contrato
toda celda de valor NACE con el valor 0 (cero). No hace
falta inicializarlo.

No podemos inicializar esa variable de contrato en el mismo lugar
que la declaramos. Pero podemos inicializarla en un código que se
ejecuta al comienzo de la vida de la instancia de este contrato, 
llamado el constructor. Si queremos que al desplegarse una instancia
del contrato se ejecute un código inicial, que ponga el valor uno
en esta variable interna de la instancia, podemos escribir:

```solidity
// Counter.sol

contract Counter {
    uint counter;
    
    constructor() public {
        counter = 1;
    }
}
```

Vean que se usa la palabra reservada `constructor` para describir este
bloque de código. El modificador `public` nos dice que se puede invocar
la creación de contrato desde una transacción de usuario, una transacción
pública.

Supongamos ahora que queremos agregar código, accesible públicamente, invocable
desde transacciones en la blockchain, que incremente el valor de la variable `counter`. Podemos
agregar una función `increment`:

```solidity
// Counter.sol

contract Counter {
    uint counter;
    
    constructor() public {
        counter = 1;
    }
    
    function increment() public {
        counter++;
    }
}
```

Vemos que los bloques de códigos invocables se denominan con `function`, de
manera similar a JavaScript. En este caso, la función `increment` CAMBIA el
estado interno de la instancia, Y NO DEVUELVE un resultado (asimilable a un `void` en lenguajes
como Java, C o C#).

