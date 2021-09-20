# Docker PHP FPM NGINX (+Laravel)

## Description

Docker environment with additional [Laravel](https://laravel.com/) setup
## Build Image

```
$ sudo docker build -f ${SelectedDockerfile} -t ${imagename} .
```

Example

```
$ sudo docker build -f 8.0php-fpm-alpine -t php-fpm:8.0-alpine .
```  

## Run Image

### Preparation
You can use "Docker-laravel" context to build an image, but first you must copy directory "docker", copy "Docker-laravel" as "Dockerfile" and copy ".dockerignore" to your project root directory

```
|- .docker
|- app
 |- Console
 |- Http
 |- ...
|- database
|- routes
|- ...
|- .env.example
|- .dockerignore
|- Dockerfile
|- ...
```

Notes: 
- Default expose PORT is 8080, you can you another available PORT but you can't use PORT 80, because only root user can use that.
- You can change the PORT or other NGINX configuration in /.docker/nginx/nginx.conf 
- Make SURE the value EXPOSE in Dockerfile is equal on listening port in /.docker/nginx/nginx.conf

### Execute

Example build

```
$ sudo docker build -t laravel-project:1.0 .
```

Example run image

```
$ sudo docker run -dp 7000:8080 --name laravel-project-name laravel-project:1.0
```

## License
The MIT License (MIT)

Copyright (c) 2021 Malik Abdul Aziz

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.