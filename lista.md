# Ejercicio 1: Mostrar una lista de usuarios desde la base de datos

## Objetivo:
Aprender a utilizar un controlador para obtener datos de la base de datos y mostrarlos en una vista.

1. **Crear una tabla de usuarios en la base de datos:**
   - Utiliza las migraciones de Laravel para crear una tabla de usuarios con al menos dos columnas: nombre y email.
     - **Explicación:** Las migraciones en Laravel son una forma conveniente de modificar la estructura de la base de datos de tu aplicación. Te permiten definir los cambios en la estructura de la base de datos utilizando código PHP en lugar de escribir consultas SQL directamente. Las migraciones se utilizan para crear, modificar o eliminar tablas y sus columnas en la base de datos.

2. **Crear un modelo para el usuario:**
   - Utiliza el generador de modelos de Laravel (`php artisan make:model Usuario`) para crear un modelo para la tabla de usuarios.
     - **Explicación:** En el contexto de Laravel, un modelo es una representación de la tabla de la base de datos. Los modelos en Laravel se utilizan para interactuar con la base de datos. Cada modelo está asociado con una tabla específica en la base de datos y se utiliza para realizar consultas, inserciones, actualizaciones y eliminaciones de registros en esa tabla.

3. **Crear un controlador para gestionar los usuarios:**
   - Utiliza el generador de controladores de Laravel (`php artisan make:controller UsuarioController`) para crear un controlador para gestionar las operaciones relacionadas con los usuarios.
     - **Explicación:** Un controlador en Laravel es una clase que agrupa la lógica relacionada con las solicitudes HTTP dentro de tu aplicación. Los controladores manejan las solicitudes entrantes y generan una respuesta apropiada. Ayudan a mantener tu código organizado y modular, ya que separan la lógica de la aplicación de las rutas y las vistas.

4. **Modificar el método del controlador para obtener usuarios:**
   - En el método del controlador, consulta todos los usuarios de la base de datos utilizando el modelo y pasa los datos a la vista.
     - **Explicación:** Dentro de un controlador, definimos métodos que manejan las diferentes solicitudes HTTP. En este caso, modificamos el método para obtener los usuarios de la base de datos utilizando el modelo correspondiente. Luego, pasamos esos datos a la vista para que puedan ser mostrados al usuario.

5. **Crear una vista para mostrar la lista de usuarios:**
   - Crea una vista llamada `lista-usuarios.blade.php` en el directorio `resources/views`. Utiliza un bucle para mostrar la lista de usuarios obtenida desde el controlador.
     - **Explicación:** En el contexto de Laravel, una vista es una plantilla que define la apariencia de la interfaz de usuario de tu aplicación. Las vistas se utilizan para mostrar datos a los usuarios y pueden contener HTML, CSS, JavaScript y código PHP. Laravel utiliza el motor de plantillas Blade para facilitar la escritura de vistas.

6. **Definir una ruta para acceder a la lista de usuarios:**
   - En el archivo `routes/web.php`, crea una nueva ruta que invoque al método del controlador para mostrar la lista de usuarios.
     - **Explicación:** Las rutas en Laravel son definiciones de URI (Identificador Uniforme de Recursos) que mapean las solicitudes HTTP a acciones específicas dentro de tu aplicación. Las rutas determinan cómo se responde a las solicitudes entrantes y pueden estar asociadas a controladores, closures o vistas directamente.

7. **Acceder a la ruta:**
   - Navega en tu navegador a la ruta que has definido y verifica que se muestre correctamente la lista de usuarios.
     - **Explicación:** Al acceder a la ruta definida en el paso anterior, el controlador se activará y se mostrará la lista de usuarios en la vista correspondiente.

Siguiendo estos pasos, habrás aprendido a utilizar migraciones, modelos, controladores, vistas y rutas en Laravel para mostrar una lista de usuarios desde una base de datos. ¡Espero que te sea útil! Si tienes alguna pregunta adicional o necesitas más ayuda, no dudes en preguntar.
