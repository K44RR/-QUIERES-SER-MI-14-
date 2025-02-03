<div class="container"> 
    <div class="card">
        <h2>¿Quieres ser mi San Valentín Kata ❤️ ?</h2>
        <div class="buttons-container">
            <button class="btn yes" onclick="aceptar()">Sí ❤️</button>
            <button class="btn no" id="noBtn">No ❌</button>
        </div>
    </div>
</div>

<!-- Aquí se generarán los corazones -->
<div class="hearts-container"></div>
/* Estilo general */
body {
    font-family: Arial, sans-serif;
    text-align: center;
    background-color: #f9d8d8; /* Fondo color pastel rosado */
    margin: 0;
    padding: 0;
    overflow: hidden; /* Asegura que los corazones no causen scroll */
}

/* Contenedor de la tarjeta */
.container {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    position: relative;
    z-index: 1; /* Asegura que el contenido esté sobre los corazones */
}

/* Tarjeta */
.card {
    background: rgba(255, 255, 255, 0.9); /* Fondo blanco con transparencia */
    padding: 30px;
    border-radius: 10px;
    box-shadow: 0px 4px 8px rgba(0, 0, 0, 0.1);
    display: inline-block;
    max-width: 500px;
    text-align: center;
    z-index: 2; /* Asegura que la tarjeta esté por encima del fondo */
}

h2 {
    font-size: 2.5em;
    color: #ff6f61; /* Color rosado */
    margin-bottom: 20px;
}

/* Contenedor de los botones (centrado) */
.buttons-container {
    display: flex;
    justify-content: center;
    gap: 30px; /* Espacio entre los botones */
    align-items: center; /* Asegura que los botones estén alineados verticalmente */
}

/* Estilos para los botones */
.btn {
    padding: 15px 30px;
    margin: 10px;
    font-size: 18px;
    cursor: pointer;
    border: none;
    border-radius: 5px;
    transition: transform 0.3s, background-color 0.3s; /* Añadimos la transición del tamaño */
}

.yes {
    background-color: #28a745;
    color: white;
}

.yes:hover {
    background-color: #218838;
    transform: scale(1.2); /* Agranda el botón "Sí" al pasar el mouse */
}

.no {
    background-color: #dc3545;
    color: white;
    position: absolute; /* Asegura que se mueva libremente */
    z-index: 2;
    transition: left 0.2s ease, top 0.2s ease; /* Hace que el movimiento sea suave */
}

.no:hover {
    background-color: #c82333;
}

/* Estilo para los corazones */
.hearts-container {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    pointer-events: none; /* Los corazones no interfieren con la interacción */
    z-index: 0; /* Los corazones están en el fondo */
}

.heart {
    position: absolute;
    font-size: 2em;
    color: #ff6f61; /* Corazón color rosado */
    animation: moveHearts 5s infinite ease-in-out;
    opacity: 0.8;
}

@keyframes moveHearts {
    0% {
        transform: translate(0, 0) scale(1);
    }
    50% {
        transform: translate(20px, -30px) scale(1.2);
    }
    100% {
        transform: translate(0, 0) scale(1);
    }
}
// Generación de corazones aleatorios
const heartsContainer = document.querySelector('.hearts-container');

for (let i = 0; i < 500; i++) {
    const heart = document.createElement('div');
    heart.classList.add('heart');
    heart.innerHTML = '&#10084;';
    // Posicionamiento aleatorio de los corazones
    heart.style.left = `${Math.random() * 100}%`;
    heart.style.top = `${Math.random() * 100}%`;
    heart.style.animationDuration = `${Math.random() * 3 + 2}s`; // Duración aleatoria de cada corazón
    heartsContainer.appendChild(heart);
}

// Función para mover el botón "No" a una posición aleatoria dentro de la pantalla
document.getElementById("noBtn").addEventListener("mouseover", function() {
    // Calculamos los límites de la pantalla para que no se salga del área visible
    let maxX = window.innerWidth - this.offsetWidth;
    let maxY = window.innerHeight - this.offsetHeight;

    // Generamos una posición aleatoria dentro de esos límites
    let x = Math.random() * maxX;
    let y = Math.random() * maxY;
    
    // Movemos el botón "No" a la nueva posición aleatoria
    this.style.left = `${x}px`;
    this.style.top = `${y}px`;
});

// Función para cuando el usuario hace clic en "Sí"
function aceptar() {
    alert("¡Nos vemos el 14 de febrero! ❤️");
}
