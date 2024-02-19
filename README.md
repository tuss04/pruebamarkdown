Primeros ejercicios Laravel

---

**Nivel Básico:**

1. **Instalación de Laravel:**
   ~~- Instala Composer si aún no lo tienes.~~
   ~~- Abre la terminal o CMD y ejecuta el comando `composer create-project --prefer-dist laravel/laravel nombre-del-proyecto`.~~

2. **Crear una Ruta Simple:**

   ~~- Abre el archivo `routes/web.php`.~~
   ~~- Agrega una nueva ruta utilizando `Route::get()`.~~
   ~~- Retorna una cadena de texto con el mensaje "Hola Mundo".~~

4. **Crear una Vista:**
   ~~- Crea un nuevo archivo Blade en la carpeta `resources/views`.~~
   ~~- Utiliza la sintaxis de Blade para mostrar el mensaje.~~
   ~~- Desde la ruta, devuelve la vista utilizando `view('nombre-de-la-vista')`.~~

5. **Enviar Datos a una Vista:**
   - Desde la ruta, envía un array con los datos utilizando `view('nombre-de-la-vista', ['datos' => $datos])`.
   - En la vista, accede a los datos utilizando la sintaxis de Blade `{{ $datos['clave'] }}`.

6. **Crear un Controlador:**
   - Ejecuta `php artisan make:controller NombreController` en la terminal para generar un nuevo controlador.
   - Define un método en el controlador que devuelve una vista.
   - Crea una nueva ruta que apunte al método del controlador.

---

**Nivel Intermedio:**

1. **Crear un Modelo y Migración:**
   - Ejecuta el comando `php artisan make:model Nombre -m` para generar un modelo junto con su migración.
   - Define la estructura de la tabla en el archivo de migración y ejecuta `php artisan migrate`.

2. **Crear un Formulario:**
   - Define una nueva ruta en `routes/web.php` para mostrar el formulario.
   - Crea una vista con un formulario HTML que envíe datos a una nueva ruta.

3. **Guardar Datos en la Base de Datos:**
   - Define una nueva ruta en `routes/web.php` para procesar el formulario.
   - En el controlador, valida y guarda los datos en la base de datos utilizando el modelo.

4. **Mostrar Lista de Productos:**
   - Define una nueva ruta en `routes/web.php` para mostrar la lista de productos.
   - Crea un controlador llamado `ProductoController` y en su método `mostrarProductos()` obtén todos los productos desde el modelo y envíalos a la vista.

5. **Editar y Eliminar Productos:**
   - Define rutas en `routes/web.php` para editar y eliminar productos y apunta a los métodos correspondientes en el controlador.
   - Implementa la lógica para actualizar y eliminar productos en el controlador.

---

# Guía de Aprendizaje de Laravel

## Nivel Básico:

### Instalación de Laravel:

1. **Instalación de Composer**:
   - Composer es una herramienta de gestión de dependencias para PHP que necesitas para instalar Laravel. Puedes descargar e instalar Composer desde su sitio web oficial en [https://getcomposer.org/](https://getcomposer.org/).
   - Una vez instalado, abre la terminal o CMD en tu computadora.

2. **Instalación de Laravel**:
   - Navega al directorio donde deseas crear tu proyecto Laravel utilizando el comando `cd ruta-de-la-carpeta`.
   - Ejecuta el siguiente comando para crear un nuevo proyecto Laravel:
     ```bash
     composer create-project --prefer-dist laravel/laravel nombre-del-proyecto
     ```

### Crear una Ruta Simple:

3. **Crear una Ruta Simple**:
   - Abre el archivo `routes/web.php` en tu editor de texto.
   - Agrega una nueva ruta utilizando `Route::get()`.
   - Retorna una cadena de texto con el mensaje "Hola Mundo".
     ```php
     Route::get('/saludo', function () {
         return '¡Hola Mundo!';
     });
     ```

### Crear una Vista:

4. **Crear una Vista**:
   - Crea un nuevo archivo Blade en la carpeta `resources/views`.
   - Utiliza la sintaxis de Blade para mostrar el mensaje.
   - Desde la ruta, devuelve la vista utilizando `view('nombre-de-la-vista')`.
     ```html
     <!-- resources/views/saludo.blade.php -->
     <!DOCTYPE html>
     <html lang="en">
     <head>
         <meta charset="UTF-8">
         <meta name="viewport" content="width=device-width, initial-scale=1.0">
         <title>Saludo</title>
     </head>
     <body>
         <h1>¡Hola Mundo desde la vista!</h1>
     </body>
     </html>
     ```

### Enviar Datos a una Vista:

5. **Enviar Datos a una Vista**:
   - Desde la ruta, envía un array con los datos utilizando `view('nombre-de-la-vista', ['datos' => $datos])`.
   - En la vista, accede a los datos utilizando la sintaxis de Blade `{{ $datos['clave'] }}`.
     ```php
     Route::get('/saludo', function () {
         $datos = ['mensaje' => '¡Hola Mundo desde los datos!'];
         return view('saludo', $datos);
     });
     ```

### Crear un Controlador:

6. **Crear un Controlador**:
   - Ejecuta `php artisan make:controller NombreController` en la terminal para generar un nuevo controlador.
   - Define un método en el controlador que devuelve una vista.
   - Crea una nueva ruta que apunte al método del controlador.
     ```bash
     php artisan make:controller SaludoController
     ```
     ```php
     // app/Http/Controllers/SaludoController.php
     use App\Http\Controllers\Controller;

     class SaludoController extends Controller
     {
         public function saludar()
         {
             $datos = ['mensaje' => '¡Hola Mundo desde el controlador!'];
             return view('saludo', $datos);
         }
     }
     ```
     ```php
     Route::get('/saludo', [SaludoController::class, 'saludar']);
     ```

## Nivel Intermedio:

En este nivel, avanzaremos en el desarrollo de nuestra aplicación Laravel, profundizando en el manejo de datos y la interacción con bases de datos. También abordaremos la creación de formularios para recopilar información del usuario y la implementación de operaciones CRUD (Crear, Leer, Actualizar, Eliminar) en nuestra aplicación.

### 1. Crear un Modelo y Migración:

En Laravel, los modelos representan tablas de la base de datos y las migraciones son archivos que definen la estructura de estas tablas. Vamos a crear un modelo y su migración asociada para manejar los productos en nuestra aplicación.

```bash
php artisan make:model Producto -m
```

Este comando generará dos archivos:
- Un archivo de modelo en `app/Models/Producto.php`.
- Un archivo de migración en `database/migrations/`, que define la estructura de la tabla `productos` en la base de datos.

### 2. Crear un Formulario:

Vamos a crear un formulario para que los usuarios puedan agregar nuevos productos a nuestra aplicación.

1. Define una nueva ruta en `routes/web.php` para mostrar el formulario:
   ```php
   Route::get('/productos/crear', 'ProductoController@mostrarFormulario');
   ```

2. Crea una vista Blade en `resources/views/productos/crear.blade.php` con el siguiente contenido:
   ```html
   <form action="/productos/guardar" method="POST">
       @csrf
       <label for="nombre">Nombre:</label>
       <input type="text" id="nombre" name="nombre"><br>
       <label for="precio">Precio:</label>
       <input type="number" id="precio" name="precio"><br>
       <button type="submit">Guardar</button>
   </form>
   ```

3. Define una nueva ruta en `routes/web.php` para procesar el formulario:
   ```php
   Route::post('/productos/guardar', 'ProductoController@guardarProducto');
   ```

### 3. Guardar Datos en la Base de Datos:

En el controlador `ProductoController`, implementa el método `guardarProducto()` para validar y guardar los datos del formulario en la base de datos.

```php
use App\Models\Producto;
use Illuminate\Http\Request;

class ProductoController extends Controller
{
    public function guardarProducto(Request $request)
    {
        $request->validate([
            'nombre' => 'required|string|max:255',
            'precio' => 'required|numeric|min:0',
        ]);

        Producto::create([
            'nombre' => $request->nombre,
            'precio' => $request->precio,
        ]);

        return redirect('/productos')->with('success', 'Producto guardado correctamente.');
    }
}
```

### 4. Mostrar Lista de Productos:

Vamos a mostrar la lista de productos existentes en nuestra aplicación.

1. Define una nueva ruta en `routes/web.php` para mostrar la lista de productos:
   ```php
   Route::get('/productos', 'ProductoController@mostrarProductos');
   ```

2. En el método `mostrarProductos()` del controlador `ProductoController`, obtén todos los productos desde el modelo `Producto` y envíalos a la vista.

```php
use App\Models\Producto;

class ProductoController extends Controller
{
    public function mostrarProductos()
    {
        $productos = Producto::all();
        return view('productos.lista', ['productos' => $productos]);
    }
}
```

3. Crea una vista Blade en `resources/views/productos/lista.blade.php` para mostrar la lista de productos.

### 5. Editar y Eliminar Productos:

Implementa las funcionalidades de editar y eliminar productos en nuestra aplicación.

1. Define rutas en `routes/web.php` para editar y eliminar productos y apunta a los métodos correspondientes en el controlador.

```php
Route::get('/productos/{id}/editar', 'ProductoController@editarProducto');
Route::put('/productos/{id}', 'ProductoController@actualizarProducto');
Route::delete('/productos/{id}', 'ProductoController@eliminarProducto');
```

2. En el controlador `ProductoController`, implementa los métodos `editarProducto()`, `actualizarProducto()` y `eliminarProducto()` para estas funcionalidades.

```php
public function editarProducto($id)
{
    $producto = Producto::find($id);
    return view('productos.editar', ['producto' => $producto]);
}

public function actualizarProducto(Request $request, $id)
{
    // Validar y actualizar el producto
}

public function eliminarProducto($id)
{
    // Eliminar el producto de la base de datos
}
```

