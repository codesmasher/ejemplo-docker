# Instrucciones de uso de la imagen

Crear la imagen de PHP en Apache:
```
docker build -t my-php-apache .
```

Iniciar la imagen de PHP en Apache:
```
docker run -d --name my-runnig-php my-php-apache
```

Iniciar sesión sobre la imagen de PHP en Apache:
```
docker exec -it my-runnig-php /bin/bash
```