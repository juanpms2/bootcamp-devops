### 1. Dockeriza la aplicación de la carpeta hello-lemoncoder con Visual Studio Code

Si ejecutamos desde el mismo directorio utilizamos .

`docker build . -t lemon-web`

### 2. Ejecutar un contenedor con tu nueva imagen

`docker run --name hello-lemon -d -p 4000:3000 lemon-web`

### 3. Añade un archivo de prueba en el contenedor y crea una nueva imagen a partir de dicho contenedor.

`docker exec hello-lemon touch app.tsx`

`docker commit hello-lemon`
