# Division de subredes - actividad

## Contenido

1. [Dirección de las redes](#section-1)
2. [División en subredes](#section-2)

## Objetivo

1. Determinar las direcciones de red, broadcast y host
2. Determinar la división en subredes de la dirección IPv4
3. Calcular la división de subredes de una dirección IPv4

## 1 Determinar las direcciones de red, broadcast y host {#section-1}

Dadas una dirección IPv4 y una máscara de subred, determinará las direcciones de red, de
difusión, rango de direcciones IPv4 disponibles, además de la cantidad de hosts.

💡 Para determinar la dirección de red, realice la operación AND binaria en la dirección IPv4
utilizando la máscara de subred proporcionada. **El resultado será la dirección de red**. Sugerencia: si lamáscara de subred tiene el valor decimal “255” en un octeto, el resultado SIEMPRE será el valor original de dicho octeto. Si la máscara de subred tiene el valor decimal “0” en un octeto, el resultado SIEMPRE será “0”
para dicho octeto

| direccion IPv4 /longitud del prefijo | 192.168.10.10    |
| ------------------------------------ | ---------------- |
| Máscara de subred                    | 255.255.255.0    |
| dirección de red                     | 192.168.10.0 /24 |
| dirección de broadcast               | 192.168.10.255   |
| # host                               | 2⁸-2 = 254       |

| 11000000 | 10101000  | 00001010 | 00001010 |
| -------- | --------- | -------- | -------- |
| 11111111 | 111111111 | 11111111 | 00000000 |
| 11000000 | 10101000  | 00001010 | 00000000 |
| 11000000 | 10101000  | 00001010 | 00000000 |
|          |           |          |          |

Direccion de host cualquiera a partir de la que obtendremos la direccion de red y broadcast.

Máscara de subred, componente de la dirección IPv4 que define la porcion de red de la porcion de host.

Dirección de red obtenida a partir de la operación ANDing, se caracteriza por ocupar toda la porcion de host con 0 binario.

Dirección de red broadcast obtenida a partir de la operación ANDing, se caracteriza por ocupar toda la porcion de host con 1 binario.

Porcion de host de la direccion IPv4.

Para calcular el numero de direcciones IPv4 en una porcion de host especifica:

#hosts = 2^n -2

La longitud del prefijo indica la cantidad de 1 binario de la mascara de subred de izquierda a derecha.

💡Si sabe esto, es posible que solamente deba realizar la operación AND binaria en un octeto cuyo valor no sea “255” ni “0” en la porción de la máscara de subred

Ejercicios

| a ) Decimal                      |                   |
| -------------------------------- | ----------------- |
| direccion IPv4 /longitud prefijo | 172.30.239.145/18 |
| Máscara de subred                |                   |
| dirección de red                 |                   |
| dirección de broadcast           |                   |
| # host                           |                   |

| a) Binario |     |     |     |     |
| ---------- | --- | --- | --- | --- |
|            |     |     |     |     |
|            |     |     |     |     |
|            |     |     |     |     |
|            |     |     |     |     |
|            |     |     |     |     |

Al analizar este ejemplo, puede ver que solamente debe realizar la operación AND binaria en el tercer octeto. Los primeros dos octetos darán como resultado “172.30” debido a la máscara de subred. El cuarto octeto dará como resultado “0” debido a la máscara de subred. Realice la operación AND binaria únicamente en el tercer octeto.

La cantidad de hosts por red se puede calcular analizando la máscara de subred. La máscara de subred se representa en formato decimal punteado, como 255.255.192.0, o en formato de prefijo de red, como /18. Una dirección IPv4 siempre tiene 32 bits o /32. Al restar la cantidad de bits utilizados para la porción de red (como representa la máscara de subred), se obtiene la cantidad de bits utilizada para los hosts -> 32-18 = 14 bits de la porción de host y que nos dan la cantidad de hosts disponibles con la fórmula #host = 2^14 -2 = 16384 hosts, se restan 2 porque dentro de una dirección de red existen 2 direcciones especiales que no se pueden asignar a ningún dispositivo, los cuales son dirección de red y dirección de broadcast.

Bueno sin mas teoria ahora vamos a por los ejercicios:

| b) Decimal                       |                   |
| -------------------------------- | ----------------- |
| direccion IPv4 /longitud prefijo | 192.168.100.25/28 |
| Máscara de subred                |                   |
| dirección de red                 |                   |
| dirección de broadcast           |                   |
| # host                           |                   |

| c) Decimal                             |                  |
| -------------------------------------- | ---------------- |
| direccion IPv4 /longitud prefijo       | 172.30.10.130/30 |
| Máscara de subred                      |                  |
| dirección de red /longitud del prefijo |                  |
| dirección de broadcast                 |                  |
| # host                                 |                  |

| d) Decimal                       |                |
| -------------------------------- | -------------- |
| direccion IPv4 /longitud prefijo | 10.1.113.75/19 |
| Máscara de subred                |                |
| dirección de red                 |                |
| dirección de broadcast           |                |
| # host                           |                |

| b) Binario |     |     |     |
| ---------- | --- | --- | --- |
|            |     |     |     |
|            |     |     |     |
|            |     |     |     |
|            |     |     |     |
|            |     |     |     |

| c) Binario |     |     |     |
| ---------- | --- | --- | --- |
|            |     |     |     |
|            |     |     |     |
|            |     |     |     |
|            |     |     |     |
|            |     |     |     |

| d) Binario |     |     |     |
| ---------- | --- | --- | --- |
|            |     |     |     |
|            |     |     |     |
|            |     |     |     |
|            |     |     |     |
|            |     |     |     |

## 2 Determinar la división en subredes de la dirección IPv4 {section-2}

Dadas una dirección IPv4, la máscara de subred original podrá determinar:

- Máscara de las nuevas subredes.
- Cantidad de subredes.
- Dirección de red de las subredes.
- Dirección de broadcast de las subredes.
- Intervale de direcciones de host de las subredes
- Cantidad de host por subred

Tomemos el siguiente ejemplo: 172.16.77.120/16, este debe satisface cumplir con las necesidades de proporcionar 5 direcciones de red, vamos paso apaso:

1. convertir la direccion a binario y la longitud del prefijo.

   172.16.77.120 /16 == 10101100.00010000.01001000.01111000 &&

   /16 == 11111111.11111111.00000000.00000000

2. Obtener la direccion de red y determinar la porción de host:

   | direccion red binario | 10101100.00010000.01001000.01111000 |
   | --------------------- | ----------------------------------- |
   | mascara de subred     | 11111111.11111111.00000000.00000000 |
   | dirección de red      | 10101100.00010000.00000000.00000000 |

   Porción de host.

3. Basado en la cantidad de subredes y host necesarios en cada segmento solicitado realizamos los calculos.

   5 direcciones de red, usamos las formular para calcular subredes y cantidad de host disponibles.

   2^n ≥ 5 (subredes solicitadas); solo se cumple si n=3 dando un resultado de 2³ = 8 subredes.

   entonces son 3 bits prestados de la porción de host, con ese precedente definimos nuevamente nuestra porción de host == 13 bits.

   #hosts= 2¹³ -2 = 8190.

4. Nos prestamos 3 bits y tenemos 8 subredes, esto es porque en los siguientes 3 bits prestados podemos realizar 8 combinaciones posibles generando asi 8 direcciones de red y solo actuamos en 3 octeto.

   1 - 00000000 > aumentando 0 a la direccion de red actual para generar la direccion de subred

   2 - 00100000 > aumentando 32

   3 - 01000000 > aumentando 64

   4 - 01100000 > aumentando 96

   5 - 10000000 > aumentando 128

   6 - 10100000 > aumentado 160

   7 - 11000000 > aumentando 192

   8 - 11100000 > aumentando 224

5. de las combinaciones posibles solo usaremos las primera 5, dandonos de esta forma las siguientes direcciones de red, 1er ip utilizable, ultima IP utilizable, dirección de broadcast y # de host directamenta en formato punto decimal.

   (le damos nombres a las subredes para poder diferenciarlas mejor)

   | subred | direccion de red /prefijo | 1er IPv4     | ultima IPv4 | direccion de broadcast | #hosts |
   | ------ | ------------------------- | ------------ | ----------- | ---------------------- | ------ |
   | A      | 172.16.0.0 /19            | 172.16.0.1   | 172.16      | 172.16.31.255          | 8190   |
   | B      | 172.16.32.0 /19           | 172.16.32.1  | 172.16      | 172.16.63.255          | 8190   |
   | C      | 172.16.64.0 /19           | 172.16.64.1  | 172.16      | 172.16.95.255          | 8190   |
   | D      | 172.16.96.0 /19           | 172.16.96.1  | 172.16      | 172.16.127.255         | 8190   |
   | E      | 172.16.128.0 /19          | 172.16.128.1 | 172.16      | 172.16.159.255         | 8190   |
   | F      | 172.16.160.0 /19          | 172.16.160.1 | 172.16      | 172.16.191.255         | 8190   |
   | G      | 172.16.192.0 /19          | 172.16.192.1 | 172.16      | 172.16.223.255         | 8190   |
   | H      | 172.16.224.0 /19          | 172.16.224.1 | 172.16      | 172.16.255.255         | 8190   |

Bueno ahora es su turno:

a) Tomemos el siguiente ejemplo: 92.168.200.139/24, este debe satisface cumplir con las necesidades de proporcionar 3 direcciones de red:

| subred | direccion de red /prefijo | 1er IPv4 | ultima IPv4 | direccion de broadcast | #hosts |
| ------ | ------------------------- | -------- | ----------- | ---------------------- | ------ |
|        |                           |          |             |                        |        |
|        |                           |          |             |                        |        |
|        |                           |          |             |                        |        |
|        |                           |          |             |                        |        |
|        |                           |          |             |                        |        |
|        |                           |          |             |                        |        |
|        |                           |          |             |                        |        |
|        |                           |          |             |                        |        |

a) Tomemos el siguiente ejemplo: 10.101.99.228/27, este debe satisface cumplir con las necesidades de proporcionar 9 direcciones de red:

| subred | direccion de red /prefijo | 1er IPv4 | ultima IPv4 | direccion de broadcast | #hosts |
| ------ | ------------------------- | -------- | ----------- | ---------------------- | ------ |
|        |                           |          |             |                        |        |
|        |                           |          |             |                        |        |
|        |                           |          |             |                        |        |
|        |                           |          |             |                        |        |
|        |                           |          |             |                        |        |
|        |                           |          |             |                        |        |
|        |                           |          |             |                        |        |
|        |                           |          |             |                        |        |

a) Tomemos el siguiente ejemplo: 92.168.200.139/17, este debe satisface cumplir con las necesidades de proporcionar 13 direcciones de red:

| subred | direccion de red /prefijo | 1er IPv4 | ultima IPv4 | direccion de broadcast | #hosts |
| ------ | ------------------------- | -------- | ----------- | ---------------------- | ------ |
|        |                           |          |             |                        |        |
|        |                           |          |             |                        |        |
|        |                           |          |             |                        |        |
|        |                           |          |             |                        |        |
|        |                           |          |             |                        |        |
|        |                           |          |             |                        |        |
|        |                           |          |             |                        |        |
|        |                           |          |             |                        |        |

a) Tomemos el siguiente ejemplo: 172.22.32.12/19, este debe satisface cumplir con las necesidades de proporcionar 5 direcciones de red:

| subred | direccion de red /prefijo | 1er IPv4 | ultima IPv4 | direccion de broadcast | #hosts |
| ------ | ------------------------- | -------- | ----------- | ---------------------- | ------ |
|        |                           |          |             |                        |        |
|        |                           |          |             |                        |        |
|        |                           |          |             |                        |        |
|        |                           |          |             |                        |        |
|        |                           |          |             |                        |        |
|        |                           |          |             |                        |        |
|        |                           |          |             |                        |        |
|        |                           |          |             |                        |        |

a) Tomemos el siguiente ejemplo: 192.168.1.245/15, este debe satisface cumplir con las necesidades de proporcionar 6 direcciones de red:

| subred | direccion de red /prefijo | 1er IPv4 | ultima IPv4 | direccion de broadcast | #hosts |
| ------ | ------------------------- | -------- | ----------- | ---------------------- | ------ |
|        |                           |          |             |                        |        |
|        |                           |          |             |                        |        |
|        |                           |          |             |                        |        |
|        |                           |          |             |                        |        |
|        |                           |          |             |                        |        |
|        |                           |          |             |                        |        |
|        |                           |          |             |                        |        |
|        |                           |          |             |                        |        |

a) Tomemos el siguiente ejemplo: 128.107.0.55/16, este debe satisface cumplir con las necesidades de proporcionar 2 direcciones de red:

| subred | direccion de red /prefijo | 1er IPv4 | ultima IPv4 | direccion de broadcast | #hosts |
| ------ | ------------------------- | -------- | ----------- | ---------------------- | ------ |
|        |                           |          |             |                        |        |
|        |                           |          |             |                        |        |
|        |                           |          |             |                        |        |
|        |                           |          |             |                        |        |
|        |                           |          |             |                        |        |
|        |                           |          |             |                        |        |
|        |                           |          |             |                        |        |
|        |                           |          |             |                        |        |

a) Tomemos el siguiente ejemplo: 192.135.250.180/24, este debe satisface cumplir con las necesidades de proporcionar 8 direcciones de red:

| subred | direccion de red /prefijo | 1er IPv4 | ultima IPv4 | direccion de broadcast | #hosts |
| ------ | ------------------------- | -------- | ----------- | ---------------------- | ------ |
|        |                           |          |             |                        |        |
|        |                           |          |             |                        |        |
|        |                           |          |             |                        |        |
|        |                           |          |             |                        |        |
|        |                           |          |             |                        |        |
|        |                           |          |             |                        |        |
|        |                           |          |             |                        |        |
|        |                           |          |             |                        |        |

Reflexión
¿Por qué es tan importante la máscara de subred para analizar una dirección IPv4?
