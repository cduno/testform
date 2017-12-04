# Documentacion
## Estructura del Proyecto
- Backend en **Zend Framework 1.12**
  - application -> carpeta principal
    - configs -> contiene un archivo para configurar las variables de entorno
    - controllers -> carpeta para controladores
      - **ApiController.php** -> Interfaz para comunicar el Frontend con el API DE Alegra.com
    - layouts -> contiene diseños principales del proyecto
    - models -> carpeta para modelos
      - **Contact.php** -> contiene la class del model de la tabla
      - **ContactMapper.php** -> contiene la comunicacion del backend con el api de Alegra.com
    - views -> carpeta para las vistas
  - library -> carpeta para librerias
  - test -> carpeta para tests
- Frontend en **Ext.js 4.2**
  - public -> carpeta de acceso publico
    - app -> contiene la estructura del mvc
      - controller -> contiene el controlador de la vista
      - model -> contiene el modelo de la tabla
      - store -> contiene la configuracion de la comunicacion del frontend con el backend en **ZF1**
      - view -> contiene las vistas
    - ext4 -> contiene la libreria de ExtJS
    - resources -> carpeta que contiene los recursos como css, img, etc
  - **app.js** -> contiene el codigo para iniciar el frontend


## Requisitos para el Auth de la API de Alegra.com

* Crear cuenta free [aqui](https://www.alegra.com/)
* Generar token [aqui ](https://app.alegra.com/configuration/api)

Debe crear el archivo **application/configs/application.ini** apartir del **application/configs/application.ini.example** en el cual debe configurar las siguientes variables:
```
configAlegra.email = "correoregistrado@enalegra"
configAlegra.token = "tokengeneradodesdelaconfiguraciondealegra"
```

## Instalación

- Instalar composer
- Entrar en la raiz del proyecto e instalar las dependencias con **composer install**
- Configurar un **VHost** por ejemplo:
```
<VirtualHost *:80>
   DocumentRoot "C:/xampp/htdocs/alegra/public"
   ServerName .local

   # This should be omitted in the production environment
   SetEnv APPLICATION_ENV development

   <Directory "C:/xampp/htdocs/alegra/public">
       Options Indexes MultiViews FollowSymLinks
       AllowOverride All
       Order allow,deny
       Allow from all
   </Directory>
</VirtualHost>
```
