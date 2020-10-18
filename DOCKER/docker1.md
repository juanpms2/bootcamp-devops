# Docker I

### 1. Crear un contenedor con MongoDB, protegido con usuario y contraseña, añadir una colección, crear un par de documentos y acceder a ella a través de MongoDB Compass

### Pasos:

- Localizar la imagen en Docker Hub para crear un MongoDB

  https://hub.docker.com/_/mongo

- Ver qué parámetros necesito para crearlo
  `docker run -d -p 27017:27017 -e MONGO_INITDB_ROOT_USERNAME=root -e MONGO_INITDB_ROOT_PASSWORD=1234 --name mymongo mongo`
- Acceder a través del CLI para mongo y crear una colección llamada books con este formato {name: 'Kubernetes in Action', author: 'Marko Luksa'} en la base de datos test

  Nos conectamos al contenedor vía bash

  `docker exec -it mymongo bash`

  Nos conectamos y logeamos en mongo

  `mongo --auth -u root -p 1234`

- Creamos la base de datos y añadimos los campos

  ```javascript
      db.getName()
      use test
      db.books.insert({
          name: 'Kubernetes in Action',
          author: 'Marko Luksa'
      })
      db.books.find({})
      exit
  ```

- Ver los logs de tu nuevo mongo

- Descargar MongoDB Compass (https://www.mongodb.com/try/download/compass)

- Accede a tu MongoDB en Docker con la siguiente cadena de conexión: mongodb://mongoadmin:secret@localhost:27017 y tus credenciales:

  ![conexión a mongo desde compass](./assets/docker1.png)
  ![conexión a mongo desde compass](./assets/docker2.png)

- Revisa que tu colección está dentro de la base de datos test y que aparece el libro que insertaste.

  ![conexión a mongo desde compass](./assets/docker3.png)

- Intenta añadir otro documento

  Nos volvemos a logear: `mongo -u root -p 1234`

  Añadimos un nuevo libro: `db.books.insert({name: 'New book', author: 'new author'})`

  ![conexión a mongo desde compass](./assets/docker4.png)

## 2. Servidor Nginx

- Crea un servidor Nginx llamado lemoncoders-web y copia el contenido de la carpeta lemoncoders-web en la ruta que sirve este servidor web.

  `docker run -d --name lemoncoders-web -p 9090:80 nginx`

- Ejecuta dentro del contenedor la acción ls, para comprobar que los archivos se han copiado correctamente.

  ![conexión a mongo desde compass](./assets/docker5.png)

- Hacer que el servidor web sea accesible desde el puerto 9999 de tu local.

  ![conexión a mongo desde compass](./assets/docker6.png)

## 3. Eliminar todos los contenedores que tienes ejecutándose en tu máquina en una sola línea.

`docker rm -f $(docker ps -aq)`
