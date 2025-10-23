
// Si el usuario presiona "Limpiar"
if (isset($_GET['clear']) && $_GET['clear'] == 'y') {
    setcookie('estilo', '', time() - 3600, '/'); // Borrar cookie
    header('Location: ' . basename(__FILE__)); // Recargar página limpia
    exit;
}

// Si se envía el formulario con un estilo
if (isset($_POST['estilo'])) {
    $estilo = $_POST['estilo'];
    // Guardar cookie por una semana
    setcookie('estilo', $estilo, time() + (7 * 24 * 60 * 60), '/');
    header('Location: ' . basename(__FILE__)); // Recargar para aplicar estilo
    exit;
}

// Comprobar si existe cookie de estilo, si no, usar "default"
$estilo = isset($_COOKIE['estilo']) ? $_COOKIE['estilo'] : 'default';
?>
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ejercicio 3.3.1</title>
    <link rel="stylesheet" href="<?php echo htmlspecialchars($estilo); ?>.css">
</head>
<body>
    <form action="" method="post">
        <label for="estilo">Estilo</label>
        <select name="estilo">
            <option value="default" <?php if($estilo == 'default') echo 'selected'; ?>>Default</option>
            <option value="oscuro" <?php if($estilo == 'oscuro') echo 'selected'; ?>>Oscuro</option>
            <option value="claro" <?php if($estilo == 'claro') echo 'selected'; ?>>Claro</option>
            <option value="matrix" <?php if($estilo == 'matrix') echo 'selected'; ?>>Matrix</option>
        </select>
        <button type="submit">Guardar</button>
        <a href="?clear=y">Limpiar</a>
    </form>

    <h1>Lorem ipsum</h1>
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Aenean iaculis dignissim finibus. Vestibulum vitae tempor quam. Curabitur faucibus dui felis, quis laoreet sem tristique sed. Maecenas non convallis massa, eget vulputate nulla. Fusce fringilla enim justo, ut dictum felis feugiat at. Interdum et malesuada fames ac ante ipsum primis in faucibus. Pellentesque pretium ante at lectus dapibus, vitae bibendum nulla gravida. Pellentesque non odio urna. Aenean laoreet a mauris at sodales. In vel sem vel justo sollicitudin lobortis. Nulla facilisi. Curabitur vel mattis nisl. Praesent dapibus tincidunt fringilla. Interdum et malesuada fames ac ante ipsum primis in faucibus.

    <h2>Donec in eros eu diam convallis mollis a ut velit</h2>
    <p>
        Donec in eros eu diam <strong>convallis mollis a ut velit</strong>. Donec id purus enim. Morbi porta lacus venenatis erat consectetur efficitur. Nam molestie diam tellus, vitae bibendum tortor sagittis nec. Fusce id finibus dui. Integer tempor convallis nulla, at pulvinar leo feugiat et. Praesent ut risus ex. Interdum et malesuada fames ac ante ipsum primis in faucibus. Curabitur vel lobortis odio. Vestibulum et mi odio.
    </p>

    <h2>Duis quis accumsan eros, sit amet luctus urna</h2>
    <p>
        Sed semper convallis diam, sed feugiat felis iaculis eget. <strong>Proin a varius</strong> magna, ac bibendum lectus. Curabitur at tristique urna. Duis ut feugiat magna. Pellentesque volutpat urna sed lacinia aliquam. Aenean at est lacus. Pellentesque orci ex, tincidunt non purus sit amet, finibus hendrerit arcu. In vitae ante et nisl semper hendrerit.
    </p>
</body>
