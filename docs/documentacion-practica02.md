# Práctica 02 - Documentación y código
### Enunciado:
Se nos pide una aplicación web donde debamos rellenar un formulario con información de nuestro sueldo y nuestro puesto de trabajo, datos los cuales se usarán para calcular el sueldo final tomando en cuenta los complementos de dicho puesto.

## Paso 1: Creación del archivo HTML (lado cliente)
Lo primero que necesitamos es un archivo .html que ofrezca un formulario que rellenar al usuario:
```
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>UT02 - P02</title>
    <style>
        @import "https://cdn.jsdelivr.net/npm/bulma@1.0.4/css/bulma.min.css";
    </style>
    <link rel="stylesheet"
        href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css">
    <script src="//unpkg.com/alpinejs" defer></script>
    <script src="//unpkg.com/axios/dist/axios.min.js"></script>
</head>
<body>
    <form name="myform" method="post" action="ut02p02.php">
        <label for="sueldo">Sueldo:</label>
        <input name="sueldo" class="input is-link" type="number" min="1000" placeholder="Introduce tu sueldo (mínimo 1000)" required>
        <label for="puesto">Puesto:</label>
        <select name="puesto" class="input is-link" required>
            <option value="base">Base</option>
            <option value="directivo">Directivo</option>
            <option value="alto-cargo">Alto cargo</option>
        </select>
        <input class="button is-link" type="submit" value="Enviar">
    </form>
</body>
</html>
```
Una vez rellenado el campo del sueldo (el cual de base está lo más restringido posible para evitar errores) y escogida una de las opciones del desplegable, al darle a enviar redirigirá al usuario a una segunda página la cual recibirá los datos introducidos.

## Paso 2: Creación del archivo PHP (lado servidor)
Este archivo será el que reciba los datos introducidos y el que, con ayuda de las etiquetas que nos ofrece PHP, aplicará la lógica del programa necesaria para hacer los cálculos deseados y mostrar la información pertinente por pantalla:
```
<!DOCTYPE html>
<html lang="es">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>UT02 - P02</title>
    <style>
        @import "https://cdn.jsdelivr.net/npm/bulma@1.0.4/css/bulma.min.css";
    </style>
    <link rel="stylesheet"
        href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css">
    <script src="//unpkg.com/alpinejs" defer></script>
    <script src="//unpkg.com/axios/dist/axios.min.js"></script>
</head>

<body>
    <?php
    $sueldo = $_POST['sueldo'] ?? 1000;
    $puesto = $_POST['puesto'];
    $complemento = 0;
    ?>
    <p>El sueldo base es de <?php echo $sueldo; ?>€</p>
    <br>
    <p>El complemento es del <?php
                                switch ($puesto) {
                                    case 'base':
                                        $complemento = 10;
                                        echo $complemento, '%';
                                        break;
                                    case 'directivo':
                                        $complemento = 15;
                                        echo $complemento, '%';
                                        break;
                                    case 'alto-cargo':
                                        $complemento = 20;
                                        echo $complemento, '%';
                                }
                                ?></p>
    <br>
    <p>El sueldo final es de <?php echo $sueldo + ($sueldo * ($complemento / 100)); ?>€</p>
</body>

</html>
```
Dependiendo del puesto de trabajo, el complemento variará, lo cual junto al sueldo base influirá a su vez en el resultado del sueldo final.