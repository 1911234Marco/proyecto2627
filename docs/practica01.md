# Práctica 01 - Documentación de la configuración inicial del proyecto
## PASO 1: Git instalado y configurado en la máquina local
Primero instalé Git en la máquina local. Para comprobar que está instalado correctamente, ejecutamos el siguiente comando en el terminal:
```
git --version
```
Seguido de esto, podemos ver la configuración usando el siguiente comando:
```
git config --list
```
![alt text](/img/practica01-1.PNG)
***
## PASO 2: GitHub CLI instalado y configurado
Una vez instalado, usaremos este comando para comprobar que funciona y ver el estado del servicio:
```
gh auth status
```
![alt text](/img/practica01-2.PNG)
***
## PASO 3: Herd instalado con la versión 8.4 de PHP
Instalamos Herd desde la página oficial. Una vez instalado, deberíamos ver esto en el Dashboard si todo funciona como debe:

![alt text](/img/practica01-3.PNG)
***
## PASO 4: Repositorio "misitio" clonado en local
Clonamos el repositorio de Github en nuestra máquina local dentro del directorio raíz de Herd con el comando:
```
gh repo clone tunombredeusuario/misitio
```
De tal forma que tengamos acceso al directorio desde nuestra máquina.

![alt text](/img/practica01-4.PNG)
***
## PASO 5: Herd enlazado al repositorio y sirviéndolo en HTTPS
En el terminal dentro de nuestro directorio de "misitio", ejecutamos el siguiente comando para enlazarlo a Herd:
```
herd link
```
Para servirlo en HTTPS, presionamos el icono del candado en la sección de Sites.

![alt text](/img/practica01-5.PNG)

### He utilizado "ReadtheDocs"