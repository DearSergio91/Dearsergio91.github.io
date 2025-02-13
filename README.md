# Dearsergio91.github.io
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Hablemos Ahora para Cambiar el Futuro</title>
    <link rel="stylesheet" href="styles.css">
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script> <!-- Librería de gráficos -->
</head>
<body>

    <header>
        <h1>Hablemos Ahora para Cambiar el Futuro</h1>
        <p>Pequeñas acciones generan un gran impacto.</p>
    </header>

    <nav>
        <ul>
            <li><a href="#hogar">Hogar</a></li>
            <li><a href="#jardin">Jardín</a></li>
            <li><a href="#comunidad">Comunidad</a></li>
            <li><a href="#compromiso">Compromiso</a></li>
        </ul>
    </nav>

    <section id="hogar" class="tips-section">
        <h2>💧 Consejos para el Hogar</h2>
        <ul>
            <li>🚿 Dúchate en menos de 5 minutos (ahorras 80L/día).</li>
            <li>🚰 No dejes el grifo abierto mientras lavas los platos.</li>
            <li>🚽 Instala sanitarios de bajo consumo de agua.</li>
        </ul>
    </section>

    <section id="jardin" class="tips-section">
        <h2>🌿 Consejos para el Jardín</h2>
        <ul>
            <li>💦 Riega las plantas al amanecer o anochecer.</li>
            <li>🌱 Usa plantas nativas que requieran menos agua.</li>
            <li>🍂 Instala sistemas de recolección de agua de lluvia.</li>
        </ul>
    </section>

    <section id="comunidad" class="tips-section">
        <h2>🏙️ Consejos para la Comunidad</h2>
        <ul>
            <li>🔍 Reporta fugas de agua en la calle.</li>
            <li>♻️ Organiza campañas de concienciación sobre el agua.</li>
            <li>🚰 Fomenta el uso de estaciones de recarga de agua.</li>
        </ul>
    </section>

    <section id="compromiso" class="compromiso-section">
        <h2>🤝 Comprométete con el Cuidado del Agua</h2>
        <p>Selecciona qué acciones tomarás para reducir tu consumo de agua:</p>
        <form id="commitment-form">
            <label><input type="checkbox" value="80"> Ducharme en menos de 5 minutos</label><br>
            <label><input type="checkbox" value="30"> Cerrar el grifo mientras me cepillo</label><br>
            <label><input type="checkbox" value="60"> Reparar fugas en mi casa</label><br>
            <label><input type="checkbox" value="100"> Usar un balde en lugar de manguera</label><br>
            <button type="submit">Calcular Ahorro</button>
        </form>
        <p id="total-ahorro"></p>
    </section>

    <section class="grafico">
        <h2>📊 Impacto del Cuidado del Agua</h2>
        <canvas id="graficoAgua"></canvas>
    </section>

    <footer>
        <p>&copy; 2025 Hablemos Ahora para Cambiar el Futuro - Cuidemos el agua</p>
    </footer>

    <script src="script.js"></script>

</body>
</html>

</body>
{
    font-family: Arial, sans-serif;
    margin: 0;
    padding: 0;
    text-align: center;
    background-color: #e3f2fd;
    color: #333;
}

header {
    background-color: #0288d1;
    color: white;
    padding: 20px;
}

h1 {
    margin: 0;
}

nav {
    background-color: #01579b;
    padding: 10px;
}

nav ul {
    list-style: none;
    padding: 0;
}

nav ul li {
    display: inline;
    margin: 0 15px;
}

nav ul li a {
    color: white;
    text-decoration: none;
    font-weight: bold;
}

.tips-section {
    background-color: #b3e5fc;
    margin: 20px;
    padding: 20px;
    border-radius: 10px;
}

.tips-section ul {
    list-style: none;
    padding: 0;
}

.tips-section li {
    font-size: 18px;
    padding: 5px 0;
}

.compromiso-section {
    background-color: #fff3e0;
    padding: 20px;
    margin: 20px;
    border-radius: 10px;
}

button {
    background-color: #0288d1;
    color: white;
    border: none;
    padding: 10px;
    margin-top: 10px;
    cursor: pointer;
    font-size: 16px;
}

button:hover {
    background-color: #0277bd;
}

footer {
    background-color: #01579b;
    color: white;
    padding: 10px;
    position: relative;
    bottom: 0;
    width: 100%;
}
document.getElementById("commitment-form").addEventListener("submit", function(event) {
    event.preventDefault();

    let totalAhorro = 0;
    document.querySelectorAll("#commitment-form input[type='checkbox']:checked").forEach((input) => {
        totalAhorro += parseInt(input.value);
    });

    document.getElementById("total-ahorro").innerText = `¡Ahorrarás aproximadamente ${totalAhorro} litros de agua al día!`;

    // Actualizar gráfico
    actualizarGrafico(totalAhorro);
});

function actualizarGrafico(ahorro) {
    let ctx = document.getElementById("graficoAgua").getContext("2d");
    
    if (window.miGrafico) {
        window.miGrafico.destroy();
    }

    window.miGrafico = new Chart(ctx, {
        type: "doughnut",
        data: {
            labels: ["Agua Ahorrada", "Consumo Diario Promedio"],
            datasets: [{
                data: [ahorro, 200], // 200L es un consumo aproximado por persona
                backgroundColor: ["#0288d1", "#ff5252"]
            }]
        }
    });
}
