## Crea los siguientes objetos de forma declarativa con las siguientes especificaciones:

- imagen: nginx
- Version: 1.19.4
- 3 replicas
- Label: app: nginx-server
- Exponer el puerto 80 de los pods
- Limits: CPU: 20 milicores, Memoria: 128Mi
- Requests:CPU: 20 milicores, Memoria: 128Mi

### A continuación, tras haber expuesto el servicio en el puerto 80, se deberá acceder a la página principal de Nginx a través de la siguiente URL:

http://<student_name>.student.lasalle.com

Objetos:

<img alt="" src="./image4.png" style="width: 601.70px; height: 349.33px;" title="">

Accediendo a http://keven.student.lasalle.com
<img alt="" src="./image19.png" style="width: 601.70px; height: 134.67px; " title="">

Otra forma, mediante la terminal a partir de la ejecución de la siguiente instrucción:

```jsx
curl -k keven.student.lasalle.com
```

<img alt="" src="./image5.png" style="width: 601.70px; height: 393.33px;" title="">

### Una vez realizadas las pruebas con el protocolo HTTP, se pide acceder al servicio mediante la utilización del protocolo HTTPS, para ello:

Creamos el certificado autofirmado y la clave privada con el comando:

openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout key.pem -out cert.pem -subj "/CN=keven.student.lasalle.com/O=keven.student.lasalle.com"

```jsx
kubectl create secret tls kevensallecert --key key.pem --cert cert.pem
```

<img alt="" src="./image10.png" style="width: 601.70px; height: 80.00px; " title="">

Creamos el secret por comando y luego visualizamos:

```jsx
kubectl create secret tls kevensallecert --key key.pem --cert cert.pem
```

<img alt="" src="./image15.png" style="width: 601.70px; height: 30.67px; " title="">

<img alt="" src="./image3.png" style="width: 483.50px; height: 63.45px;" title="">

Luego lo exportamos para tenerlo como referencia:

```jsx
kubectl get secret kevensallecert -o yaml > secret.yml
```

<img alt="" src="./image14.png" style="width: 601.70px; height: 32.00px; " title="">

Creamos otro archivo ingress_tls.yaml para la configuración del TLS que hemos creado:

<img alt="" src="./image24.png" style="width: 316.50px; height: 345.37px; " title="">

Verificamos en el navegador el certificado autofirmado:
<img alt="" src="./image20.png" style="width: 486.50px; height: 180.22px; " title="">
<img alt="" src="./image12.png" style="width: 435.50px; height: 364.60px; " title="">

Guardamos el certificado desde el navegador keven-student-lasalle-com.pem y lo probamos desde el terminal con curl viendo como resultado la web nginx.

```jsx
curl --cacert keven-student-lasalle-com.pem  https://keven.student.lasalle.com
```

<img alt="" src="./image13.png" style="width: 601.70px; height: 298.67px; " title="">
