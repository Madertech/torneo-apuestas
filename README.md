<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Torneo de Apuestas</title>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@700&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Poppins', sans-serif;
            margin: 0;
            padding: 0;
            color: #ffffff;
            text-align: center;
            background: linear-gradient(45deg, #ff6600, #003366, #ffcc00, #6600cc);
            background-size: cover; /* Asegura que el fondo cubra toda la pantalla */
            background-position: center;
            animation: backgroundShift 15s ease infinite;
            height: 100vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
        }

        @keyframes backgroundShift {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }

        header {
            background-color: rgba(255, 102, 0, 0.8);
            padding: 1em;
            font-size: 2em;
            text-transform: uppercase;
            border-bottom: 3px solid #ffcc00;
        }

        .alias {
            font-size: 1.2em;
            color: #ffcc00;
            margin-bottom: 1em;
        }

        .premio {
            font-size: 3em;
            color: #ffcc00;
            margin: 1em 0;
            animation: brillar 1.5s infinite alternate;
        }

        @keyframes brillar {
            from { opacity: 0.7; }
            to { opacity: 1; }
        }

        .mesa {
            background-color: rgba(51, 51, 51, 0.8);
            border-radius: 20px;
            padding: 2em;
            display: grid;
            grid-template-columns: repeat(5, 1fr);
            gap: 1em;
            margin: 2em;
        }

        .jugador {
            background-color: #444;
            padding: 1.5em;
            border-radius: 10px;
            font-size: 1.5em;
            font-weight: bold;
            position: relative;
            cursor: pointer;
            transition: opacity 0.3s ease, transform 0.3s ease, background-color 0.3s ease;
        }

        .jugador:hover {
            background-color: #ff6600;
        }

        .eliminado {
            opacity: 0.4;
            transform: scale(0.8);
            background-color: #666;
            text-decoration: line-through;
        }

        .x-roja {
            position: absolute;
            top: 0;
            left: 0;
            font-size: 3em;
            color: red;
            font-weight: bold;
            visibility: hidden;
            width: 100%;
            text-align: center;
        }

        .jugador.eliminado .x-roja {
            visibility: visible;
        }

        .reglas {
            background-color: rgba(51, 51, 51, 0.8);
            padding: 2em;
            margin: 2em;
            border-radius: 10px;
            text-align: left;
        }

        .reglas p {
            margin: 0.5em 0;
        }

        /* Responsividad para dispositivos móviles */
        @media (max-width: 768px) {
            .mesa {
                grid-template-columns: repeat(2, 1fr); /* 2 columnas para pantallas medianas */
            }
        }

        @media (max-width: 480px) {
            .mesa {
                grid-template-columns: 1fr; /* 1 columna para pantallas pequeñas */
            }

            .jugador {
                font-size: 1.2em; /* Ajustar el tamaño de la fuente en pantallas pequeñas */
                padding: 1em;
            }

            .premio {
                font-size: 2em; /* Ajustar tamaño del texto del premio */
            }
        }
    </style>
</head>
<body>
<header>
    Torneo de Apuestas
</header>
<div class="alias">Inscripción: sanchez.jorge.mp</div>
<div class="premio">💰 Premio $25.000 pesos 💰</div>
<div class="mesa" id="mesaApuestas"></div>
<div class="reglas">
    <h2>Reglas del Torneo</h2>
    <p>1. El torneo dura 48 hs desde el sábado 00.00 hs hasta el lunes 00.00 hs.</p>
    <p>2. Se puede apostar en cualquier deporte, no se permite jugar en casino.</p>
    <p>3. No se pueden cashout las apuestas, hacerlo elimina al jugador del premio.</p>
    <p>4. Los jugadores eliminados se tacharán automáticamente.</p>
    <p>5. Si nadie gana, el premio se guarda para la siguiente semana.</p>
    <p>6. El primero en llegar a $25.000 con los $2.500 gana el torneo.</p>
    <p>7. Se aceptan todo tipo de apuestas pre-match y en vivo.</p>
    <p>8. Si hay empate, el premio se reparte.</p>
</div>
<script>
    const usuarios = ['EMILIANO', 'VALENTINO', 'FACU', 'NAHUEL', 'ENANO', 'ENZO', 'FRAMBU', 'MILTON', 'FRANCO', 'ABUELO'];

    function crearMesa() {
        const mesa = document.getElementById('mesaApuestas');
        usuarios.forEach((usuario, index) => {
            const div = document.createElement('div');
            div.classList.add('jugador');
            div.textContent = usuario;
            
            // Crear la "X" roja
            const xRoja = document.createElement('div');
            xRoja.classList.add('x-roja');
            xRoja.textContent = 'X';
            div.appendChild(xRoja);

            div.onclick = () => eliminarJugador(div);
            mesa.appendChild(div);
        });
    }

    function eliminarJugador(elemento) {
        elemento.classList.toggle('eliminado');
    }

    window.onload = crearMesa;
</script>
</body>
</html>
