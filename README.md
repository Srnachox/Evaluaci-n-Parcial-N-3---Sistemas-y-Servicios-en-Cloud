# Evaluaci-n-Parcial-N-3---Sistemas-y-Servicios-en-Cloud
Evaluación Parcial N° 3 de Sistemas Operativos Corporativos (AAY1108). Evidencias de implementación de servidores web en entornos cloud Linux (Apache) y Windows Server 2019 (IIS + FTP)
Sistemas y servicios en cloud
Nombre de alumno: Ignacio Fernando San Martin Riera y Matias Rebolledo Bahamondes
Profesor: GONZALO ADRIAN LEPIN GONZALEZ
Fecha: 15/6/2026
Sección: AAY1108
Asignatura: SISTEMAS OPERATIVOS CORPORATIVOS
Descripción general de la evaluación
▪La evaluación consiste en implementar Windows Server 2019 en una máquina virtual en la nube, en la cual debe ejecutar el rol Web Server y una máquina virtual Linux RHEL9 o similar (Rocky, Alma, Amazon Linux), en la que debe instalar un servidor web, y personalizar si sitio de bienvenida.  
Ítem 1: Servidor Linux (RHEL 9 / Rocky / AlmaLinux)
1. Creación de la Instancia en AWS
●Instancia: Selecciona una AMI de Red Hat Enterprise Linux 9, Rocky Linux 9 o AlmaLinux 9.
●Tamaño: Para cumplir con el requisito estricto de 2 vCPU y 4 GB de RAM, elige el tipo de instancia t3.medium (o t2.medium según disponibilidad).
●Llave de conexión: Crea un par de llaves nuevo. Guárdalo con TuApellido.pem (o .ppk si usas PuTTY antiguo).
●Security Group: Configura las siguientes reglas de entrada agregando tu nombre y apellido en la descripción:
Tipo de Tráfico	Puerto	Origen	Descripción
SSH	22	Mi IP (o Anywhere)	[Tu Nombre] [Tu Apellido] - Acceso Remoto
HTTP	80	Anywhere (0.0.0.0/0)	[Tu Nombre] [Tu Apellido] - Servidor Web
imagenes
1. Preparación en AWS Academy (El primer paso)
<img width="639" height="498" alt="image" src="https://github.com/user-attachments/assets/079648bd-fe89-48cf-9996-969e235b495e" />
<img width="639" height="498" alt="image" src="https://github.com/user-attachments/assets/00a9a65d-7407-45e0-adec-3bc2f17f25af" />
<img width="537" height="225" alt="image" src="https://github.com/user-attachments/assets/8bc0f47c-1a38-4f3e-a160-02739790e67e" />
Linux aws
1. Lanzamiento de la Instancia en AWS Academy
Cuando estés en el panel de EC2 de AWS, asegúrate de configurar lo siguiente para cumplir con los requerimientos técnicos: 
•	AMI: Selecciona RHEL 9, Rocky Linux 9 o AlmaLinux 9. 
•	Tipo de instancia: Elige t3.medium (o t2.medium según disponibilidad en tu lab) para garantizar que tengas los 2 vCPU y 4 GB de RAM exigidos. 
•	Security Group: Crea uno nuevo y agrega las siguientes reglas de entrada: 
o	SSH (Puerto 22): Origen "My IP" o "Anywhere" (según lo que indique tu profesor). 
o	HTTP (Puerto 80): Origen "Anywhere" (0.0.0.0/0). 
o	Nota: En la columna de descripción de cada regla, escribe: Nombre y Apellido. 
2. Configuración y Despliegue (SSH)
<img width="1094" height="235" alt="image" src="https://github.com/user-attachments/assets/3eb8d65b-a685-4b87-8672-a05d1499c36a" />
<img width="1081" height="701" alt="image" src="https://github.com/user-attachments/assets/1acda12f-6b2f-4466-a804-69c9af7e93b2" />
<img width="1093" height="424" alt="image" src="https://github.com/user-attachments/assets/4cf33a2f-74a1-4ef3-8cc3-be4c73d7ad9e" />
<img width="1089" height="613" alt="image" src="https://github.com/user-attachments/assets/3b01dbb3-cde1-4110-bbff-342b1b9b9463" />
<img width="1092" height="453" alt="image" src="https://github.com/user-attachments/assets/6f4876a2-225f-42c4-9364-fdf266903d7e" />
<img width="596" height="572" alt="image" src="https://github.com/user-attachments/assets/e916d303-9c03-4ffe-a4f9-71a8a2764c2e" />
<img width="1903" height="701" alt="image" src="https://github.com/user-attachments/assets/de5f577b-93f1-470c-8a91-448cc85afa2c" />
<img width="1327" height="34" alt="image" src="https://github.com/user-attachments/assets/ebf7eccb-5e19-4175-9148-02ec2b9390a3" />
<img width="488" height="48" alt="image" src="https://github.com/user-attachments/assets/96a57205-b48d-45c0-808f-f19fca5c96a8" />
<img width="857" height="51" alt="image" src="https://github.com/user-attachments/assets/8e6a26d6-da1a-4a30-9dd9-0a2033fdc8d8" />
<img width="1631" height="724" alt="image" src="https://github.com/user-attachments/assets/f6020d8c-157a-4968-a103-2c15c660400b" />
Una vez que la instancia esté en estado Running, conéctate a ella vía SSH (puedes usar PuTTY o la terminal de VS Code) usando tu llave .pem. 
A continuación, ejecuta estos comandos en orden para instalar y configurar tu servidor web:
•	Actualizar el sistema:
sudo dnf update -y 
•	Instalar el servidor web (httpd):
sudo dnf install httpd -y 
•	Verificar el estado e iniciarlo:
sudo systemctl status httpd (Aquí verás que está inactive). sudo systemctl start httpd. sudo systemctl enable httpd (Para que inicie automáticamente al encender). 
4. Personalización del Sitio (Evidencia)
Para que el sitio tenga tu nombre y el logo de Duoc UC, edita el archivo principal:
1.	Accede a la carpeta web: cd /var/www/html/. 
2.	Crea tu página: sudo nano index.html. 
3.	Escribe el contenido HTML con tu información y asegúrate de incluir el logo de Duoc UC que hayas subido previamente a esa misma carpeta. 
💡 Recordatorio de Evidencias (Checklist)
Para no perder puntos en tu informe: 
•	[ ] Captura de pantalla de la configuración del Security Group con tu nombre en la descripción. 
•	[ ] Captura de pantalla del comando systemctl status httpd mostrando que el servicio está activo. 
•	[ ] Captura de pantalla de tu navegador mostrando tu página web con tu nombre y el logo de Duoc UC, incluyendo la fecha y hora de tu sistema operativo visible en la captura. 
•	[ ] Al terminar, recuerda ir al panel de AWS y detener la instancia (no terminarla).
Windows server 20219
1. Configuración de la Instancia (Paso a Paso)
•	Nombre de la instancia: Ponle algo claro, como Servidor Windows - [TuNombre].
•	Aplicación e Imagen de SO (AMI):
o	En el buscador de AMIs, selecciona Windows. 
o	En el menú desplegable, asegúrate de elegir rigurosamente: Microsoft Windows Server 2019 Base. 
o	¡Ojo! Verifica que abajo diga "Desktop Experience" (o "con GUI"), ya que la pauta exige explícitamente la edición estándar con interfaz gráfica (gui). 
•	Tipo de instancia: Para que el entorno gráfico de Windows se mueva de forma fluida, te sugiero elegir t3.medium (2 vCPU y 4 GB de RAM) o la que te permita por defecto tu laboratorio institucional. 
•	Par de claves (Inicio de sesión): Haz clic en "Crear un nuevo par de claves". 
o	Nombre de la llave: Guárdala estrictamente con TuApellido (por ejemplo: Perez-Win). 
o	Descarga el archivo .pem y guárdalo bien, porque lo usaremos en unos minutos para descifrar la contraseña de administrador. 
2. Configuración de Red (Security Group) 🔒
En la sección de Configuraciones de red, haz clic en "Crear grupo de seguridad". Aquí debes configurar manualmente tres reglas de entrada esenciales para este ítem: 
Debes agregar y configurar las reglas para que queden exactamente así:
1.	Regla de RDP:
o	Tipo: RDP. 
o	Puerto: 3389. 
o	Origen: Cualquier lugar (0.0.0.0/0) o Mi IP. 
o	Descripción: [Tu Nombre y Apellido] - Acceso RDP. 
2.	Regla de HTTP:
o	Tipo: HTTP. 
o	Puerto: 80. 
o	Origen: Cualquier lugar (0.0.0.0/0). 
o	Descripción: [Tu Nombre y Apellido] - Servidor IIS. 
3.	Regla de FTP:
o	Tipo: FTP. 
o	Puerto: 21. 
o	Origen: Cualquier lugar (0.0.0.0/0). 
o	Descripción: [Tu Nombre y Apellido] - Servicio FTP. 
📸 ¡Momento de Evidencia! Antes de lanzar, o justo después de crear el grupo de seguridad, toma una captura de pantalla donde se vean claramente estas tres reglas con tu nombre y apellido en los comentarios de conexión. Recuerda incluir la fecha y hora de tu pantalla. 
3. Lanzar la Instancia
Una vez revisado todo, haz clic en el botón naranja "Lanzar instancia". 
Cuando se haya creado exitosamente, ve a la lista de instancias. Espera un par de minutos hasta que el estado de la instancia cambie a "En ejecución" (Running) y las comprobaciones de estado pasen a 2/2. 
📝 ¿Qué haremos apenas esté encendida?
1.	Anotaremos la IP pública y el Nombre de DNS para tu informe. 
2.	Nos conectaremos mediante el cliente de Conexión a Escritorio Remoto (RDP) usando tu llave para obtener la clave de Administrador.
<img width="1087" height="230" alt="image" src="https://github.com/user-attachments/assets/98e275da-3801-40d6-a6fd-0440c6707106" />
<img width="969" height="620" alt="image" src="https://github.com/user-attachments/assets/f2f68c45-3a6c-429b-be1c-d818e177201d" />
<img width="1090" height="444" alt="image" src="https://github.com/user-attachments/assets/14dc8d88-3a99-45c8-8f1e-1e0a000293b7" />
<img width="1633" height="30" alt="Captura de pantalla 2026-06-17 143334" src="https://github.com/user-attachments/assets/26c4869e-5025-4d24-9836-b6e249ddf386" />
<img width="1901" height="693" alt="Captura de pantalla 2026-06-17 143150" src="https://github.com/user-attachments/assets/acb931d9-8a1f-4de3-882a-14854b7b81d7" />
<img width="540" height="521" alt="Captura de pantalla 2026-06-17 143122" src="https://github.com/user-attachments/assets/2f26b279-88b6-45bd-98be-3afd26eeacf7" />
<img width="1085" height="611" alt="Captura de pantalla 2026-06-17 143108" src="https://github.com/user-attachments/assets/7c4c5bb5-39a0-43ec-8381-35da021961ce" />
<img width="1090" height="444" alt="Captura de pantalla 2026-06-17 142932" src="https://github.com/user-attachments/assets/b31f59b5-6b99-44af-97dd-4697d9985fa7" />
<img width="259" height="52" alt="image" src="https://github.com/user-attachments/assets/b4adba9c-e52d-445d-858f-74f14062fa61" />
<img width="463" height="57" alt="image" src="https://github.com/user-attachments/assets/664c4650-883c-4f7a-94ed-992ee1e6404f" />
<img width="1670" height="67" alt="image" src="https://github.com/user-attachments/assets/7b155b0a-e6d1-4507-80a6-f7dcfd5cadbb" />
<img width="1639" height="766" alt="image" src="https://github.com/user-attachments/assets/e0dc78f7-bf04-4813-bd94-84112efda5fd" />
<img width="1639" height="766" alt="image" src="https://github.com/user-attachments/assets/e3bffed2-0d40-487e-aea0-901c4fb08c08" />
<img width="1635" height="575" alt="image" src="https://github.com/user-attachments/assets/2182d9c2-6c2f-4135-9bca-7c50eef7cdbd" />
<img width="1638" height="638" alt="image" src="https://github.com/user-attachments/assets/3829c260-d92f-4518-801c-d38f03cbd2f8" />

<img width="1633" height="30" alt="image" src="https://github.com/user-attachments/assets/c6627ed3-f51e-407d-8182-039c1d87b83d" />
El orden de las pantallas en el asistente:
1.	Before You Begin (Antes de comenzar): Esta es la primera pantalla que se abre. No tienes que configurar nada aquí. Solo haz clic en Next (Siguiente) abajo a la derecha. 
2.	Installation Type (Tipo de instalación): Asegúrate de que esté marcada la primera opción, que se llama "Role-based or feature-based installation". Luego, haz clic en Next. 
3.	Server Selection (Selección del servidor): Aquí verás el nombre de tu servidor Windows en la nube resaltado en una lista. No cambies nada y vuelve a hacer clic en Next. 
4.	Server Roles (Roles del servidor) 🎯 ¡AQUÍ ES! Esta es la pantalla que estabas buscando. En la lista del medio es donde debes buscar y marcar la casilla "Web Server (IIS)". 
💡 ¿Qué pasa cuando marcas "Web Server (IIS)"?
Apenas pinches ese cuadrado, te saldrá automáticamente un cuadro flotante (una ventana emergente) que dice que el servidor necesita instalar herramientas adicionales. Debes hacer clic en el botón que dice "Add Features". 
Al hacer eso, la casilla de Web Server (IIS) quedará con un ticket. Después de eso, continúas dándole a Next hasta llegar a la parte del FTP Server al final del menú. 
¿Estás parado en la primera pantalla o te costó encontrar el botón de "Add roles and features" en el Server Manager?

Para asegurar el éxito, sigue este orden lógico en la consola:
•	Lanzamiento de instancias: Asegúrate de seleccionar las AMIs correctas para cada SO. Para Linux, utiliza RHEL9, Rocky, Alma o Amazon Linux. Para Windows, selecciona Windows Server 2019 con GUI. 
•	Recursos de Hardware: Configura ambas máquinas con 2 vCPU y 4 GB de RAM. 
•	Security Groups: Es fundamental configurar las reglas de entrada con tu nombre y apellido como comentario. 
o	Linux: Debes habilitar acceso a los servicios SSH y HTTP. 
o	Windows: Debes habilitar acceso a los servicios RDP, HTTP y FTP. 
•	Gestión de llaves: Crea las llaves de conexión personalizadas con tu apellido. 
4. Ejecución y Evidencia (¡Muy importante!)
La rúbrica es estricta: debes registrar el proceso de desarrollo de cada punto a través de pantallazos. Recuerda que en cada captura debe aparecer: 
•	La fecha. 
•	La hora. 
•	Tu nombre y apellido. 
5. Tareas técnicas por SO
Mientras trabajas en la consola, recuerda cumplir estos hitos:
•	Para Linux:
o	Conéctate mediante un cliente SSH (como PuTTY u otro). 
o	Instala el servicio httpd. 
o	Verifica su estado y asegúrate de iniciarlo mediante comandos. 
o	Modifica la página de bienvenida para que incluya tu nombre y el logo de Duoc UC (asegúrate de que la imagen esté en el servidor, no mediante enlace externo). 
•	Para Windows:
o	Conéctate al servidor a través de RDP. 
o	Instala el rol Web Server - IIS (que incluye HTTP y FTP). 
o	Verifica que los servicios HTTP y FTP estén activos. 
o	Personaliza la página de bienvenida con tu nombre y el logo de Duoc UC. 
o	Realiza las pruebas de funcionamiento en tu navegador para el sitio web y el servicio FTP. 

📌 ¡Nota para el Informe! Toma una captura de pantalla del panel de AWS donde se vea la IP pública, el Nombre de DNS y los detalles de hardware de la instancia.
3. Configuración y Despliegue Web (SSH)
Conéctate por SSH a tu servidor e interactúa usando la terminal con los siguientes comandos:
●Paso A: Actualizar el sistema e instalar Apache (HTTPD)
sudo dnf update -y
sudo dnf install httpd -y
●Paso B: Iniciar y verificar el servicio
# Iniciar y habilitar para que arranque con el sistema
sudo systemctl start httpd
sudo systemctl enable httpd

# Verificar el estado (Toma captura aquí)
sudo systemctl status httpd
●Paso C: Personalizar la página de bienvenida La ruta por defecto del servidor web es /var/www/html/. Debes descargar o subir el logo de Duoc UC directamente al servidor (puedes usar wget o curl para bajar la imagen y dejarla localmente).
Crea el archivo index:
sudo nano /var/www/html/index.html
Agrega una estructura HTML simple:
HTML
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <title>Evaluación Parcial 3 - Linux</title>
</head>
<body>
    <h1>Servidor Web Linux - [Tu Nombre y Apellido]</h1>
    <p>Bienvenido a mi sitio web corriendo en RHEL9/Similar en la nube.</p>
    <img src="logo-duoc.png" alt="Logo Duoc UC" width="300">
</body>
</html>
●Paso D: Comprobación y Apagado
1.Abre tu navegador e ingresa la http://[IP_Publica_Linux].
2.Toma captura de pantalla completa (donde se vea la hora, fecha de tu PC y tu nombre en la web).
3.Anda al panel de AWS y Detén la instancia (Stop instance).
Ítem 2: Servidor Windows Server 2019
1. Creación de la Instancia en AWS
●Instancia: Selecciona la AMI Microsoft Windows Server 2019 Base (asegúrate de que diga "with Desktop Experience" o GUI).
●Tamaño: Al igual que el anterior, configúrala preferentemente con una capacidad similar para soportar bien el entorno gráfico (ej. t3.medium).
●Llave de conexión: Crea una nueva llave llamada TuApellido-Win.pem.
●Security Group: Configura las reglas de entrada con tu comentario personalizado:
Tipo de Tráfico	Puerto	Origen	Descripción
RDP	3389	Mi IP (o Anywhere)	[Tu Nombre] [Tu Apellido] - Acceso Windows
HTTP	80	Anywhere (0.0.0.0/0)	[Tu Nombre] [Tu Apellido] - Sitio Web IIS
FTP	21	Anywhere (0.0.0.0/0)	[Tu Nombre] [Tu Apellido] - Servidor FTP

2. Configuración y Despliegue (RDP)
Conéctate mediante el cliente de Conexión a Escritorio Remoto (RDP) de Windows usando la IP pública y descifrando la contraseña de Administrador con tu llave .pem.
●Paso A: Instalar Rol Web Server (IIS) + FTP
1.Abre el Server Manager.
2.Haz clic en Add roles and features.
3.Avanza hasta Server Roles y marca Web Server (IIS).
4.Al expandir las opciones de IIS, busca la sección FTP Server y marca FTP Service.
5.Dale a Next e Install.
●Paso B: Modificar la página de bienvenida de IIS
1.La ruta del sitio web por defecto en Windows es C:\inetpub\wwwroot\.
2.Modifica el archivo iisstart.htm o crea un index.html allí.
3.Pega el mismo código HTML con tu nombre, y guarda la imagen del logo de Duoc UC físicamente dentro de C:\inetpub\wwwroot\.
●Paso C: Iniciar y verificar servicios
1.En las herramientas administrativas, abre Internet Information Services (IIS) Manager.
2.Verifica que tanto el Sitio Web como el Sitio FTP (si configuraste uno básico) estén en estado Started.
●Paso D: Comprobación y Apagado
1.Desde tu máquina física, accede a http://[IP_Publica_Windows] para ver la web.
2.Accede a ftp://[IP_Publica_Windows] (o usa un cliente como FileZilla) para validar el protocolo FTP.
3.Toma capturas de pantalla de todo (recordando mostrar fecha/hora del sistema).
4.Detén la instancia en AWS.
📂 Plantilla Sugerida para tu Repositorio de GitHub (README.md)
Como la entrega consiste en enviar un enlace de GitHub público, te recomiendo estructurar tu archivo principal de la siguiente manera para facilitarle la corrección al docente:
# Evaluación Parcial N° 3 - Sistemas y Servicios en Cloud
**Asignatura:** Sistemas Operativos Corporativos (AAY1108)  
**Estudiante:** Ignacio Fernando San Martin Riera
**Docente:** GONZALO ADRIAN LEPIN GONZALEZ
**Fecha:** 17 de Junio, 2026  
---
## 🐧 Ítem 1: Servidor Linux en la Nube
* **IP Pública:** `54.xx.xx.xx`
* **DNS:** `ec2-54-xx...compute-1.amazonaws.com`
### Evidencias Linux:
1. **Configuración de Instancia y SG:** ![Captura SG Linux](ruta-a-tu-captura1.png)  
   *(Asegúrate de que se vea tu nombre en la descripción y la hora del PC)*
2. **Estado del Servicio HTTPD:** ![Estado Apache](ruta-a-tu-captura2.png)
3. **Sitio Web Funcionando desde Navegador:** ![Web Linux](ruta-a-tu-captura3.png)
---
## 🪟 Ítem 2: Servidor Windows Server 2019
* **IP Pública:** `3.xx.xx.xx`
* **DNS:** `ec2-3-xx...compute-1.amazonaws.com`
### Evidencias Windows:
1. **Configuración de Instancia y SG:** ![Captura SG Windows](ruta-a-tu-captura4.png)
   
2. **Instalación de Roles (IIS + FTP):** ![Roles IIS](ruta-a-tu-captura5.png)
3. **Sitio Web IIS e Interfaz FTP Funcionando:** ![Web Windows](ruta-a-tu-captura6.png)

Opción 1: Corta y directa (Ideal para el campo "Description" de GitHub)
Repositorio para la Evaluación Parcial N° 3 de Sistemas Operativos Corporativos (AAY1108). Implementación de servidores web en Linux y Windows Server 2019 en la nube.  

💼 Opción 2: Un toque más formal y técnico
Proyecto correspondiente a la Evaluación Parcial N° 3 de la asignatura Sistemas y Servicios en Cloud. Contiene la documentación y evidencia de despliegue de servidores web (HTTP/FTP) en entornos virtuales cloud (Linux y Windows Server).  

🚀 Opción 3: Formato Portafolio (Pensando en el futuro)
Despliegue práctico de infraestructura en la nube: Configuración de instancias virtuales Linux (Apache) y Windows Server 2019 (IIS + FTP) con acceso remoto seguro. Evaluación Sumativa 3 - Duoc UC.  

💡 Un tip extra de organización
Si estás editando el campo "Description" (el que está abajo del nombre del repositorio en la barra lateral derecha), recuerda que tienes un límite de caracteres, por lo que la Opción 1 o la Opción 3 te vendrán como anillo al dedo.

¿Estás buscando la descripción para el cuadro de texto general del repositorio o quieres una introducción más detallada para redactar el archivo README.md completo?
