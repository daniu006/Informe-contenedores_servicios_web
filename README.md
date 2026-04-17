# Practica servidor web

## 1. Titulo

Despliegue y personalización de dos servidores web con Nginx utilizando contenedores Docker

## 2. Tiempo de duración

40 minutos

## 3. Fundamentos:

Docker es una plataforma que permite crear, desplegar y ejecutar aplicaciones dentro de contenedores. Un contenedor es una unidad ligera que incluye todo lo necesario para que una aplicación funcione, como el código, las librerías y las dependencias. A diferencia de las máquinas virtuales, los contenedores comparten el sistema operativo del host, lo que los hace más rápidos y eficientes.

Nginx es un servidor web de alto rendimiento utilizado para servir páginas web, balancear carga y actuar como proxy inverso. En esta práctica, se utiliza la imagen oficial de Nginx para desplegar servidores web de forma rápida sin necesidad de instalar el servidor manualmente.

El uso de Docker junto con Nginx permite crear entornos aislados, donde cada contenedor puede tener su propia configuración. Esto facilita la gestión de múltiples servicios en un mismo equipo sin conflictos de puertos o dependencias.

Además, en mi caso se emplean comandos básicos de Linux como cp, nano y history, los cuales permiten manipular archivos dentro del sistema y entre el contenedor y el host. El comando docker cp es especialmente importante, ya que permite copiar archivos desde el contenedor hacia el sistema anfitrión y viceversa, lo que facilita la personalización del archivo index.html.

El archivo index.html es la página principal que sirve Nginx. Al modificar este archivo, se puede cambiar el contenido que se muestra en el navegador. En esta práctica, se crean dos contenedores: uno con información institucional y otro con información personal del estudiante.

El uso de contenedores en el desarrollo moderno es fundamental, ya que permite replicar entornos fácilmente, mejorar la portabilidad de aplicaciones y optimizar el uso de recursos.

## 4. Conocimientos previos.

Para realizar esta práctica el estudiante necesita tener claro los siguientes temas:

* Comandos básicos de Linux
* Manejo de terminal
* Uso de editores de texto como nano o vi
* Conceptos básicos de redes (puertos)
* Uso básico de navegadores web
* Conceptos básicos de Docker

## 5. Objetivos a alcanzar

* Implementar contenedores utilizando Docker
* Desplegar servidores web con Nginx
* Manipular archivos dentro de contenedores
* Personalizar páginas web mediante edición de index.html
* Comprender el uso de puertos en contenedores
* Exportar historial de comandos en Linux

## 6. Equipo necesario:

* Computador con sistema operativo Windows/Linux/Mac
* WSL (en caso de usar Windows)
* Docker instalado (docker.io)
* Terminal de comandos (bash)
* Navegador web

## 7. Material de apoyo.

* Documentación oficial de Docker
* Documentación de Nginx
* Guía de la asignatura


## 8. Procedimiento

**Paso 1:** Instalar Docker

```bash
sudo apt update
sudo apt install docker.io -y
sudo service docker start
```

---

**Paso 2:** Verificar instalación

```bash
docker --version
```

---

**Paso 3:** Crear contenedores

```bash
docker run -d --name nginx1 -p 8089:80 nginx
docker run -d --name nginx2 -p 8090:80 nginx
```

---

**Paso 4:** Copiar archivo `index.html`

```bash
docker cp nginx1:/usr/share/nginx/html/index.html ./index1.html
```

---

**Paso 5:** Editar archivo

```bash
nano index1.html
```

---

**Paso 6:** Devolver archivo al contenedor

```bash
docker cp index1.html nginx1:/usr/share/nginx/html/index.html
```

---

**Paso 7:** Repetir para `nginx2`

```bash
docker cp nginx2:/usr/share/nginx/html/index.html ./index2.html
nano index2.html
docker cp index2.html nginx2:/usr/share/nginx/html/index.html
```

---

**Paso 8:** Verificar en navegador

* [http://localhost:8089](http://localhost:8089)

![Figura 8-1. Servidor nginx1 personalizado](https://github.com/user-attachments/assets/ae7176f2-b16a-4b3c-8a77-c99ed17107f3)

---

* [http://localhost:8090](http://localhost:8090)

![Figura 8-2. Servidor nginx2 personalizado](https://github.com/user-attachments/assets/e6cb154b-febd-40f4-9bef-9bc127b16fe8)

---

**Paso 9:** Guardar historial

```bash
history | tee tarea-s2-Daniela_Abad.txt
```

---


## 9. Resultados esperados:

Se logró desplegar dos contenedores con Nginx funcionando correctamente. Cada uno muestra una página personalizada en el navegador con diferente contenido.

Tanto en el contenedor nginx1 como en el nginx2 presenta información personal del estudiante.

Además, se generó correctamente el archivo de historial con los comandos ejecutados durante la práctica.

## 10. Bibliografía
- Daniela, A. (2026). Comnados Linux.
