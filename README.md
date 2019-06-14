# Lab4
Laboratorio 4 CRUD
1.	Se creo una aplicación con asp.net Core utilizando una base de datos SQL Server creada en RDS de AWS. Se instalo NGINX como proxy server y se instalado ASP.Net Core en la instancia de EC2 para poder levantar la aplicación Web junto con un servicio que mantuviera activa la página Web.
 

Se utilizo de referencia la siguiente página Web para poder crear el server proxy he instalar lo demás componentes necesarios.
LINK: http://www.projectcodify.com/hosting-aspnet-core-on-linux-using-nginx  

2.	Se procedió a crear 2 imágenes de la instancia principal donde ya se encontraba la aplicación corriendo para poder crear el LB. Esto con el fin de administrar el tráfico de aplicaciones entrantes a través de varios destinos. Pasos a seguir:
 

Se habilita el puerto 80 ya que este puerto es el que escucha el proxy server

 







Se utilizo el securito Group por default ya que en este grupo se han configurado los protocolos por los cuales la aplicación podrá escuchar y conectarse.
 
Ya que la aplicación no fue creada en Node.Js no se configura ningún “Ping Path”, al ser creada en ASP.NET este tiene por defecto el index, entonces al iniciar la pagina se direccionara a este automáticamente. 
 






Seleccionamos nuestras instancias creadas anteriormente para que el LB pueda configurarlas

 
Seleccionamos Create

 
 


Seguido creamos nuestro Auto Scaling 
 
 
 
 
  
 
 

Pruebas de estrés
Se utilizaron los siguientes comandos para las pruebas de estrés en la instancia principal:
1.	 sudo yum install https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
2.	sudo yum install stress -y
3.	stress --cpu 1 --timeout 900
4.	Seguidamente podemos notar como el load Balance crea una nueva instancia de nuestra instancia para poder soportar la carga.
4.1	 
Antes de la prueba de estres
 Despues de la prueba de estrés.

 



