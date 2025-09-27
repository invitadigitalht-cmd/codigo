<!doctype html>
<html lang="es">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width,initial-scale=1" />
<title>Confirmación de asistencia</title>

<!-- Fuentes -->
<link href="https://fonts.googleapis.com/css2?family=EB+Garamond:wght@400;500;600&family=Cormorant+Garamond:wght@400;600;700&display=swap" rel="stylesheet">

<style>
  :root{
    --accent:#6a7a53;
    --gold:#b38a52;
    --card-bg: rgba(255,255,255,0.96);
    --text:#333;
  }

  html,body{
    height:100%;
    margin:0;
    background: transparent;
    font-family: "EB Garamond", serif;
    font-size:12px;
    color:var(--text);
  }

  .wrap{
    height:100vh;
    display:flex;
    align-items:center;
    justify-content:center;
    padding:20px;
    box-sizing:border-box;
  }

  .card{
    width:100%;
    max-width:420px;
    background: var(--card-bg);
    border-radius:18px;
    padding:28px 26px 40px;
    box-shadow: 0 8px 30px rgba(0,0,0,0.12);
    box-sizing:border-box;
    text-align:center;
  }

  .hero-title{
    font-family: "Cormorant Garamond", serif;
    font-size:30px;
    color:var(--gold);
    margin:6px 0 14px;
    font-weight:600;
  }

  .subtitle{
    font-size:12px;
    color:#6b6b6b;
    line-height:1.5;
    margin-bottom:22px;
    text-transform:uppercase;
    font-weight:400;
    letter-spacing:1px;
  }

  label{
    display:block;
    font-size:12px;
    margin:10px 0 6px;
    font-weight:600;
    letter-spacing:0.5px;
  }

  input[type="text"], textarea, select{
    width:100%;
    box-sizing:border-box;
    padding:10px 12px;
    border-radius:6px;
    border:1.2px solid rgba(100,100,100,0.2);
    font-size:12px;
    outline:none;
    background:transparent;
    font-family: "EB Garamond", serif;
  }

  textarea{
    min-height:60px;
    resize:vertical;
  }

  .btn{
    display:block;
    margin:18px auto 0;
    padding:8px 16px;
    border-radius:8px;
    background:var(--accent);
    color:white;
    font-size:12px;
    text-align:center;
    border:none;
    cursor:pointer;
    font-weight:600;
    letter-spacing:0.8px;
    box-shadow: 0 2px 8px rgba(0,0,0,0.08);
  }

  .btn:hover{
    background:#556444;
  }
</style>
</head>
<body>

  <div class="wrap">
    <form class="card" id="rsvpForm">
      <h1 class="hero-title">Confirma tu Asistencia</h1>

      <p class="subtitle">SERÁ UN HONOR CONTAR CON TU PRESENCIA EN ESTE DÍA TAN ESPECIAL</p>

      <label for="nombre">Nombre y Apellido</label>
      <input id="nombre" name="nombre" type="text" placeholder="Escribe tu nombre" required>

      <label for="confirm">Confirmación</label>
      <select id="confirm" name="confirm" required>
        <option value="SI, AHÍ ESTARÉ">SI, AHÍ ESTARÉ</option>
        <option value="NO PODRÉ ASISTIR">NO PODRÉ ASISTIR</option>
        <option value="TAL VEZ">TAL VEZ</option>
      </select>

      <label for="mensaje">Mensaje</label>
      <textarea id="mensaje" name="mensaje" placeholder="Escribe aquí"></textarea>

      <button class="btn" type="submit">ENVIAR</button>
    </form>
  </div>

<script>
  document.getElementById("rsvpForm").addEventListener("submit", function(e){
    e.preventDefault();

    const nombre = document.getElementById("nombre").value.trim();
    const confirm = document.getElementById("confirm").value;
    const mensaje = document.getElementById("mensaje").value.trim();

    if(!nombre){
      alert("Por favor ingresa tu nombre.");
      return;
    }

    // Crear el mensaje
    let texto = "📋 Confirmación de asistencia\n\n";
    texto += "👤 Nombre: " + nombre + "\n";
    texto += "✅ Confirmación: " + confirm + "\n";
    if(mensaje){
      texto += "💬 Mensaje: " + mensaje;
    }

    // Codificar para WhatsApp
    const url = "https://api.whatsapp.com/send?phone=59173623511&text=" + encodeURIComponent(texto);

    // Abrir en una pestaña nueva
    window.open(url, "_blank");
  });
</script>
</body>
</html>
