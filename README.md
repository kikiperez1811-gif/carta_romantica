<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Carta Romántica 💌</title>
<style>
  body {
    margin: 0;
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    background: linear-gradient(135deg, #ffb6c1, #ff69b4);
    font-family: "Poppins", sans-serif;
    overflow: hidden;
  }

  .sobre {
    width: 300px;
    height: 180px;
    perspective: 1000px;
    cursor: pointer;
    z-index: 2;
  }

  .carta {
    width: 100%;
    height: 100%;
    position: relative;
    transform-style: preserve-3d;
    transition: transform 1s;
  }

  .carta.abierta {
    transform: rotateX(180deg);
  }

  .frente, .interior {
    position: absolute;
    width: 100%;
    height: 100%;
    border-radius: 12px;
    backface-visibility: hidden;
    box-shadow: 0 5px 20px rgba(0,0,0,0.3);
  }

  .frente {
    background: linear-gradient(135deg, #ff69b4, #ff1493);
    display: flex;
    justify-content: center;
    align-items: center;
    color: white;
    font-size: 36px;
    font-weight: bold;
  }

  .interior {
    background: #fff8f0;
    transform: rotateX(180deg);
    padding: 15px;
    overflow-y: auto;
    display: flex;
    justify-content: center;
    align-items: center;
    position: relative;
  }

  .interior textarea {
    width: 100%;
    height: 100%;
    border: none;
    background: transparent;
    resize: none;
    font-size: 16px;
    font-family: "Poppins", sans-serif;
    outline: none;
  }

  .interior::before {
    content: "";
    position: absolute;
    width: 90%;
    height: 90%;
    top: 5%;
    left: 5%;
    border: 2px dashed #ff69b4;
    border-radius: 10px;
    pointer-events: none;
  }

  .corazon {
    position: absolute;
    width: 20px;
    height: 20px;
    background: radial-gradient(circle at center, #ff69b4 0%, #ff1493 60%, transparent 100%);
    border-radius: 50%;
    opacity: 0.8;
    animation: caer linear forwards;
    pointer-events: none;
    z-index: 1;
  }

  @keyframes caer {
    0% { transform: translateY(-50px) scale(1); opacity: 1; }
    100% { transform: translateY(100vh) scale(0.8); opacity: 0; }
  }
</style>
</head>
<body>

<div class="sobre" id="sobre">
  <div class="carta" id="carta">
    <div class="frente">💌</div>
    <div class="interior">
      <textarea placeholder="Escribe tu mensaje romántico aquí..."></textarea>
    </div>
  </div>
</div>

<script>
  const sobre = document.getElementById('sobre');
  const carta = document.getElementById('carta');

  sobre.addEventListener('click', () => {
    carta.classList.toggle('abierta');
    if(carta.classList.contains('abierta')){
      // Genera corazones al abrir
      for(let i=0; i<20; i++){
        crearCorazon();
      }
    }
  });

  function crearCorazon(){
    const heart = document.createElement('div');
    heart.classList.add('corazon');
    heart.style.left = Math.random() * window.innerWidth + 'px';
    heart.style.animationDuration = (2 + Math.random()*2) + 's';
    document.body.appendChild(heart);
    setTimeout(() => heart.remove(), 4000);
  }
</script>

</body>
</html>
