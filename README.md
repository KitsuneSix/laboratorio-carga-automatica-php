Informe de Laboratorio: Implementación de Carga Automática (Autoload) PSR-4

UNIVERSIDAD TECNOLÓGICA DE PANAMÁ

FACULTAD DE INGENIERÍA EN SISTEMAS COMPUTACIONALES

Materia: Desarrollo de Software VII
Estudiante: Jorge Osorio

Cédula: 3-754-696

Grupo: 1GS132

Profesora: Irina Fong

INTRODUCCIÓN
Este proyecto consiste en la implementación del estándar PSR-4 utilizando Composer para gestionar la carga automática de clases en PHP. El objetivo principal es eliminar el uso manual de include y require, optimizando la organización del código y la mantenibilidad del sistema.

METODOLOGÍA PASO A PASO

Paso 1: Configuración de la Estructura (D.2.1)
Se creó la carpeta raíz del proyecto y una subcarpeta llamada src/ para almacenar las clases bajo el estándar PSR-4.

Paso 2: Configuración de composer.json
Se inicializó el archivo de configuración de Composer definiendo el mapa de carga automática:

Namespace: App\ (mapeado a la carpeta src/).  

Archivo: composer.json.

Paso 3: Generación del Autoloader (D.2.2)
Se ejecutó el comando en la terminal de Visual Studio Code:
"composer dump-autoload"
Este comando generó la carpeta vendor/ y el archivo autoload.php, encargados de gestionar las dependencias de forma automática.

Paso 4: Refactorización y Uso de "use"
Se creó la clase Saludo.php dentro de src/ con el namespace correspondiente. En el archivo index.php, se sustituyeron las inclusiones manuales por una única llamada al autoloader:
"require_once DIR . '/vendor/autoload.php';"
"use App\Saludo;"

Paso 5: Higiene del Repositorio (D.4.3)
Se configuró un archivo .gitignore en la raíz del proyecto para excluir la carpeta vendor/. Esto garantiza que el repositorio sea ligero y que cada desarrollador genere su propio autoloader localmente.

PRUEBA DE FUNCIONAMIENTO (D.3)
La prueba se realizó mediante WampServer accediendo a localhost/laboratorio-autoload/index.php.  

Resultado: Visualización exitosa del mensaje "¡Carga automática funcionando con PSR-4!".  

Conclusión de la prueba: El sistema instancia objetos correctamente sin errores de "Class not found".

CONCLUSIONES TÉCNICAS (D.4.2)

Mantenibilidad: La carga automática permite agregar nuevas clases en src/ sin modificar archivos de configuración globales, facilitando el crecimiento del proyecto.  

Eficiencia de Memoria: Al implementar Lazy Loading, PHP solo carga las clases necesarias en el momento de su uso, optimizando los recursos del servidor.  

Estandarización: Seguir el estándar PSR-4 asegura la interoperabilidad del código y facilita el trabajo colaborativo bajo normas profesionales de la industria.

GUÍA DE INSTALACIÓN PARA EL USUARIO

Clone el repositorio.

Ejecute "composer dump-autoload" para generar el cargador de clases localmente.  

Asegúrese de que su servidor local apunte a la raíz del proyecto.
