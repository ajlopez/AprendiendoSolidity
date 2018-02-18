# TestRPC

Para ejecutar contratos inteligentes y transacciones en general, necesitamos
conectarnos a un nodo Ethereum. Hay varias implementaciones, en distintos lenguajes
de programación, como Go, Rust y Java. Pero para estas lecciones voy
a usar uno escrito en JavaScript que se ejecuta desde [NodeJS](NodeJS.md).

Luego, hay que instalar TestRPC como módulo NodeJS pero de forma global, para
que podamos lanzarlo desde cualquier directorio

```
npm install -g ethereumjs-testrpc
```

(puede que en algún Linux necesitemos ejecutarlo con `sudo` antes de `npm`).

Una vez instalado globalmente, queda disponible un comando en nuestro path, que
sirve para lanzar el nodo:

```
testrpc
```

Un ejemplo de salida:

```
EthereumJS TestRPC v6.0.3 (ganache-core: 2.0.2)

Available Accounts
==================
(0) 0x3eb7b3799921e065bd33714cb38398da4821fc0d
(1) 0xa280ccb243f36c0d3523397466d87a8da05c0b14
(2) 0x59f2b3fed3e0a75027d7650c6a12ef4994739012
(3) 0x194663e4656138b4cd67f5c8cab6f85f257a1f42
(4) 0x32fe421612cf7354cb9e08ce198ac1680fdfd183
(5) 0xd79e64a780977ddf6ab02a621c66ef22b27a526e
(6) 0x3af0a57624134a0d61a6f6c00f4dbb21f1ee7722
(7) 0x1cdb59d4f7f4949e897f4a50a3a69866f09e7cd0
(8) 0x9f6f4dcaa1cf623ab268e40932032eaca5ada0ab
(9) 0x7ab786e35ce10cd1f819b2b5c1806e6a5caf0843

Private Keys
==================
(0) c48c6393ede748f059dd9366c94b728b17926a54ef0e7f0b140793bab3df8e56
(1) ebd65ca586a9bade77f223bcee49a589c2ef869ce34cc131dbea433cd99ab832
(2) 67b7ea7de6051c15ab84371b0ebed7dc4bcd4976683ff6ce42550f96db0efc3f
(3) e7abf4fab1eb415b8f15c880b4abba0cf1d6fc252897ce92c6d3176894daae46
(4) 8698e4c4f1adce6dac7c0bb57c2452f5278347244287646be0beef69f82312bd
(5) 995707663d5cae9fe43c13e323298ab6f94dc507e4e2850e589d45ae2fec74d9
(6) 7464ded88ae8af37b3b4a7999d939107744454e17bd6f7017a04e00a4771d046
(7) b65f31898b3ef23361ce6848d123a48fd3b8ded966bbba185a973faf43a391d8
(8) 128934f6a06de778a3c7d76fe751be4245bfeac13f60c4a214e3fa8e1d0d8f61
(9) caeed53bd1fdc13a0f1ef98e2f335bb35226bec2355ad91b8fc89ff0af127817

HD Wallet
==================
Mnemonic:      only collect submit patrol order wrist when open athlete coffee bounce recipe
Base HD Path:  m/44'/60'/0'/0/{account_index}

Listening on localhost:8545
```

Vean que nos da diez cuentas iniciales, disponibles para nuestras pruebas
y experimentos, y una billetera que las maneja en memoria. Hay que tomar
en cuenta el port (`8545` en el ejemplo de arriba) porque lo vamos a usar
en las librerías y ejemplos cliente que ejecutar.


