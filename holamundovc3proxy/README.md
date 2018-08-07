# Proyecto con vue-cli 3 y proxy para el api

### 1. Instalación de vue-cli 3

Primero desinstalamos cualquier versión anterior de vuecli:

```shell
$ npm uninstall vue-cli -g
```

Y a continuación instalamos la nueva versión de vue-cli:

```shell
$ npm install -g @vue/cli
```

Comprobamos la versión:

```shell
$ vue --version
3.0.0-rc.11
```

### 2. Creación de un proyecto nuevo

Ejecutamos, desde la carpeta raíz desde donde crearemos una nueva carpeta para el nuevo proyecto:

```shell
$ vue create holamundovuecli3
```

### 3. Creación de proxy para el api de backend

Creamos un nuevo fichero en la raíz del proyecto, de nombre vue.config.js con el siguiente contenido:

```javascript
// vue.config.js
module.exports = {
  devServer: {
    proxy: {
      "/api": {
        target: "http://localhost:10080/api",
        secure: false
      }
    }
  }
};
```

Para probarlo (con 8080 como puerto del servidor de vue, y 10080 como servidor del api)

http://localhost:8080/api/healthcheck

El servidor de vue debería enrutar hacia el backend que escuche por el 10080 la petición.

NOTA: Si no tenemos el servidor del api backend escuchando, debería de dar este error:

```
Proxy error: Could not proxy request /api/healthcheck from localhost:8080 to http://localhost:10080/api (ECONNREFUSED).
```

### 4. Arranque del nuevo proyecto

```shell
$ cd holamundovuecli3
$ npm run serve
```

