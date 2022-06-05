# Conexión entre Virtual Machines por Virtual Network
Este es un recopilatorio sobre como conectar dos Virtual Machines en Azure.
![Microsoft-Azure-Virtual-Machine](images\Microsoft-Azure-Virtual-Machine.png)
![Microsoft-Azure-Virtual-Network](images\Microsoft-Azure-Virtual-Network.png)
![Microsoft-Azure-Virtual-Machine](images\Microsoft-Azure-Virtual-Machine.png)

---

## Requisitos
- Cuenta en [Microsoft Azure](https://portal.azure.com)
- Un dispositivo, por ejemplo una computadora
- Acceso a internet
- Navegador de internet como Google Chrome, Opera, Mozilla Firefox, etc.

---

## Importante
- Las Virtual Machine de Azure **cobran por hora**, no es una cantidad demasiado grande, pero es importante tenerlo en cuenta por si creas una, para detenerla o borrarla cuando no se esté usando.
- Es super importante utilizar la **misma región** para la Virtual Machine, con su correspondiente Virtual Network, si no al momento de crear la Virtual Machine no detectará la Virtual Network, por lo que no se podrá realizar la conexión.
- Es importante durante el proceso crear las Virtual Machines **con contraseña**.

---

## Pasos a seguir
- En este caso empezaremos creando el "Grupo de recursos", para luego acomodar nuestras Virtual Machines y Virtual Networks, dentro de la misma para tener un mejor control, además de asegurarnos de que tengan la misma región, si no sabes por qué, revisa el apartado de **"Importante"**.
![P1](images\P1.png)
![P2](images\P2.png)

- Después de la creación del grupo de recursos, lo siguiente será la creación de las dos Virtual Network, lo primero es buscar "Virtual Network", entonces llenamos los datos que siempre necesitan los recursos, o sea "Suscripción", "Grupo de recursos", "Nombre" y "Región".

![P3](images\P3.png)
- Es importante el tener mínimo una subnet, aunque al momento de estar creando la Virtual Network ya te crea una por defecto.
![P4](images\P4.png)

- Entonces con todo listo, nos vamos al apartado de "Revisar y crear", y si todo está correcto ya podemos finalizar la creación de la primera Virtual Network con el botón "Crear".
![P5](images\P5.png)

- Ya solo sería esperar a que termine de realizar la implementación.
![P6](images\P6.png)

- Al finalizar nos indica que ya se completó la implementación.
![P7](images\P7.png)

- Entonces volvemos a repetir el proceso para crear ahora la segunda Virtual Network.
![P8](images\P8.png)

- Ahora toca la creación de las Virtual Machines, igual que con las Virtual Network, llenamos los datos que nos pidan, en este caso usaremos "Linux".
![P9](images\P9.png)

- Esto es muy importante, hay que conectar las Virtual Machines, con las Virtual Network, una con cada una.
![P10](images\P10.png)

- Después de terminar vamos al apartado de "Revisar y crear" y si todo está en orden le damos clic en "Crear", entonces toca esperar unos pocos minutos.
![P11](images\P11.png)

- Al terminar correctamente, nos indica que ya completó la implementación
![P12](images\P12.png)

- Entonces, ahora sigue la creación, de la segunda Virtual Machine. **Importante** enlazar cada Virtual Machine con una Virtual Network, por eso la creación de dos, para que cada una tenga la suya.
![P13](images\P13.png)

- Después de haber creado tanto las Virtual Networks como las Virtual Machines, lo siguiente es ir donde se encuentra nuestra primera Virtual Machine, ahora hay que ir al apartado de "Conectar", para este método usaremos el "SSH", copiamos la ruta de acceso de clave privada luego abriremos el "Azure Cloud Shell" (el cual se encuentra en la parte superior, al lado de la barra de busqueda), importante si no tenemos un almacenamiento, habrá que crearlo.
![P14](images\P14.png)

- Ahora dentro del "Azure Cloud Shell" escribimos (sin comillas) "ssh AQUI PONEMOS LA RUTA DE ACCESO DE CLAVE PRIVADA".
![P15](images\P15.png)

- Ahora podemos hacer una vaca escribiendo (sin comillas) "sudo apt-get moo". No es muy útil pero es divertido.
![P16](images\P16.png)

- Ahora nos vamos al recurso de la primera Virtual Network que creamos, y clicamos en el apartado de "Emparejamientos" y añadimos uno, dándole clic en "Agregar".
![P17](images\P17.png)

- Ahora le asignamos un nombre, en la parte de abajo nos volverá a pedir un nombre, en ese es recomendable escribir lo mismo que asignamos en el primero, pero al revés, ejemplo "VN1-VN2" y en el segundo escribiríamos "VN2-VN1".
![P18](images\P18.png)

- Y ya creada nos saldría algo parecido a esto.
![P19](images\P19.png)

- Y ya casí para terminar, vamos al recurso de la segunda Virtual Network que creamos y nos vamos al apartado de "Dispositivos conectados", aquí encontraremos la conexión que tenemos con su respectiva Virtual Machine, y su "IP de la conexión", esta la copiamos y ahora regresamos al "Azure Cloud Shell" donde escribiremos (sin comillas) "ping Y LA IP"

- Y ya casí estarían conectadas las dos Virtual Machines, ya solo toca esperar un poco.
![P20](images\P20.png)

- Y después de terminar ya estarían conectas las dos Virtual Machines.