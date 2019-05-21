# Exeth

Para ejecutar transacciones, sembrar contratos e invocarlos, necesitamos
enviar comandos a un nodo Ethereum. Como nodo vamos a usar [TestRPC](TestRPC.md).
Para enviar comandos, usaremos JavaScript, con distintas librerías.

Los primeros ejemplos los haremos con [Exeth](https://github.com/ajlopez/exeth),
un ejecutor de archivos de texto con comandos simples que invocan a un nodo. Es
una especie de lenguaje de scripting, que nos servirá para introducirnos fácilmente
en la comunicación con un nodo.

Para usarlo, tenemos que instalarlo globalmente
```
npm install -g exeth
```

(puede que en algún Linux necesitemos ejecutarlo con `sudo` antes de `npm`).

Una vez instalado globalmente, queda disponible un comando en nuestro path, que
sirve para ejecutar un archivo de texto, generalmente grabado con extensión `.eth`:

```
exeth miscript.eth
```

Iremos viendo en los ejemplos los comandos disponibles en este lenguaje
de scripting. Cuando se ejecuta, se conecta con un nodo que esté escuchando
comandos externos en `http://localhost:8545` pero también vamos poder
conectarnos a otras direcciones.

Para conseguir eso, agregamos una opción al lanzarlo:

```
exeth miscript.eth -h http://localhost:4444
```

También podemos usar la opción larga:

```
exeth miscript.eth --host http://localhost:4444
```

Para tener más información de lo que va ejecutando,
podemos lanzar un script habilitando la opción de
logueo:

```
exeth miscript.eth -l
```
o
```
exeth miscript.eth --logging
```

Esta opción mostrará información adicional de cada 
comando en la
salida de la terminal.

