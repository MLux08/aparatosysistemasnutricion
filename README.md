<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>BIO-CYBER 2050: Misión Nutrición II - Tema 2</title>
    <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;600;800;900&family=Rajdhani:wght@500;600;700&display=swap" rel="stylesheet">
    <style>
        :root {
            --bg-dark: #070913;
            --card-bg: rgba(15, 23, 42, 0.85);
            --cyber-cyan: #00f3ff;
            --cyber-purple: #bc13fe;
            --cyber-green: #00ff66;
            --cyber-pink: #ff007f;
            --cyber-yellow: #ffea00;
            --text-main: #f1f5f9;
            --text-muted: #94a3b8;
            --border-glow: 0 0 15px rgba(0, 243, 255, 0.4);
            --card-radius: 16px;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            user-select: none;
        }

        body {
            font-family: 'Rajdhani', sans-serif;
            background: radial-gradient(circle at center, #10172a 0%, #05070e 100%);
            color: var(--text-main);
            min-height: 100vh;
            padding: 20px;
            display: flex;
            flex-direction: column;
            align-items: center;
            overflow-x: hidden;
        }

        body::before {
            content: '';
            position: fixed;
            top: 0; left: 0; width: 100%; height: 100%;
            background: linear-gradient(rgba(0, 243, 255, 0.03) 1px, transparent 1px),
                        linear-gradient(90deg, rgba(0, 243, 255, 0.03) 1px, transparent 1px);
            background-size: 40px 40px;
            z-index: -1;
            pointer-events: none;
        }

        .cyber-header {
            width: 100%;
            max-width: 1000px;
            background: var(--card-bg);
            border: 2px solid var(--cyber-cyan);
            box-shadow: var(--border-glow);
            border-radius: var(--card-radius);
            padding: 20px 30px;
            margin-bottom: 25px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
            gap: 15px;
            backdrop-filter: blur(10px);
        }

        .game-title {
            font-family: 'Orbitron', sans-serif;
            font-size: 1.8rem;
            font-weight: 900;
            background: linear-gradient(135deg, var(--cyber-cyan), var(--cyber-purple));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            text-transform: uppercase;
            letter-spacing: 2px;
        }

        .stats-panel {
            display: flex;
            align-items: center;
            gap: 20px;
            background: rgba(0,0,0,0.4);
            padding: 10px 20px;
            border-radius: 30px;
            border: 1px solid rgba(0, 243, 255, 0.2);
        }

        .stat-box {
            display: flex;
            align-items: center;
            gap: 8px;
            font-size: 1.1rem;
            font-weight: 700;
        }

        .stat-value {
            color: var(--cyber-yellow);
            font-family: 'Orbitron', sans-serif;
        }

        .audio-btn {
            background: linear-gradient(135deg, var(--cyber-purple), #7e22ce);
            color: white;
            border: none;
            padding: 10px 18px;
            border-radius: 20px;
            font-family: 'Orbitron', sans-serif;
            font-size: 0.85rem;
            font-weight: 700;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0 0 10px rgba(188, 19, 254, 0.4);
        }

        .audio-btn:hover {
            transform: scale(1.05);
            box-shadow: 0 0 20px rgba(188, 19, 254, 0.8);
        }

        .game-wrapper {
            width: 100%;
            max-width: 1000px;
            display: flex;
            flex-direction: column;
            gap: 20px;
        }

        .mission-nav {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
            gap: 12px;
        }

        .mission-tab {
            background: rgba(15, 23, 42, 0.6);
            border: 1px solid rgba(255,255,255,0.1);
            padding: 15px;
            border-radius: 12px;
            text-align: center;
            cursor: pointer;
            transition: all 0.3s ease;
            font-family: 'Orbitron', sans-serif;
            font-size: 0.85rem;
            font-weight: 700;
            color: var(--text-muted);
            display: flex;
            flex-direction: column;
            gap: 5px;
        }

        .mission-tab.active {
            background: linear-gradient(135deg, rgba(0, 243, 255, 0.15), rgba(188, 19, 254, 0.15));
            border-color: var(--cyber-cyan);
            color: var(--cyber-cyan);
            box-shadow: 0 0 15px rgba(0, 243, 255, 0.3);
        }

        .mission-badge {
            font-size: 0.75rem;
            color: var(--cyber-yellow);
        }

        .progress-bar-container {
            width: 100%;
            height: 12px;
            background: rgba(0,0,0,0.5);
            border-radius: 6px;
            overflow: hidden;
            border: 1px solid rgba(0, 243, 255, 0.3);
        }

        .progress-fill {
            height: 100%;
            width: 0%;
            background: linear-gradient(90deg, var(--cyber-cyan), var(--cyber-green));
            transition: width 0.4s ease;
            box-shadow: 0 0 10px var(--cyber-green);
        }

        .quest-card {
            background: var(--card-bg);
            border: 1px solid rgba(0, 243, 255, 0.3);
            border-radius: var(--card-radius);
            padding: 28px;
            backdrop-filter: blur(12px);
            box-shadow: 0 10px 30px rgba(0,0,0,0.5);
            display: flex;
            flex-direction: column;
            gap: 20px;
        }

        .quest-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            border-bottom: 1px solid rgba(255,255,255,0.1);
            padding-bottom: 12px;
        }

        .quest-number {
            font-family: 'Orbitron', sans-serif;
            color: var(--cyber-purple);
            font-size: 1.1rem;
            font-weight: 800;
        }

        .quest-title {
            font-size: 1.35rem;
            font-weight: 700;
            color: var(--cyber-cyan);
        }

        .quest-body {
            font-size: 1.1rem;
            line-height: 1.6;
        }

        .img-preview-box {
            text-align: center;
            background: rgba(0,0,0,0.4);
            border: 1px solid rgba(0, 243, 255, 0.2);
            border-radius: 12px;
            padding: 15px;
            margin: 10px 0;
            max-height: 380px;
            display: flex;
            justify-content: center;
            align-items: center;
        }

        .img-preview-box img {
            max-width: 100%;
            max-height: 340px;
            object-fit: contain;
            border-radius: 8px;
        }

        .options-list {
            display: flex;
            flex-direction: column;
            gap: 12px;
        }

        .option-btn {
            background: rgba(30, 41, 59, 0.7);
            border: 1.5px solid rgba(255,255,255,0.15);
            color: var(--text-main);
            padding: 14px 20px;
            border-radius: 10px;
            font-size: 1.05rem;
            font-family: 'Rajdhani', sans-serif;
            font-weight: 600;
            text-align: left;
            cursor: pointer;
            transition: all 0.25s ease;
            display: flex;
            align-items: center;
            gap: 12px;
        }

        .option-btn:hover:not(:disabled) {
            background: rgba(0, 243, 255, 0.15);
            border-color: var(--cyber-cyan);
            transform: translateX(5px);
        }

        .option-btn.selected {
            border-color: var(--cyber-yellow);
            background: rgba(255, 234, 0, 0.15);
        }

        .option-btn.correct-opt {
            background: rgba(0, 255, 102, 0.2) !important;
            border-color: var(--cyber-green) !important;
            color: #86efac !important;
        }

        .option-btn.wrong-opt {
            background: rgba(255, 0, 127, 0.2) !important;
            border-color: var(--cyber-pink) !important;
            color: #fca5a5 !important;
        }

        .match-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 15px;
        }

        @media (max-width: 600px) {
            .match-grid { grid-template-columns: 1fr; }
        }

        .select-custom {
            background: rgba(15, 23, 42, 0.9);
            border: 1px solid var(--cyber-cyan);
            color: var(--text-main);
            padding: 10px;
            border-radius: 8px;
            font-size: 1rem;
            font-family: 'Rajdhani', sans-serif;
            width: 100%;
            outline: none;
        }

        .cyber-btn {
            background: linear-gradient(135deg, var(--cyber-cyan), #0284c7);
            color: #070913;
            border: none;
            padding: 12px 28px;
            border-radius: 10px;
            font-family: 'Orbitron', sans-serif;
            font-size: 0.95rem;
            font-weight: 800;
            cursor: pointer;
            transition: all 0.3s ease;
            text-transform: uppercase;
            box-shadow: 0 0 15px rgba(0, 243, 255, 0.4);
        }

        .cyber-btn:hover:not(:disabled) {
            transform: translateY(-2px);
            box-shadow: 0 0 25px rgba(0, 243, 255, 0.8);
        }

        .cyber-btn:disabled {
            opacity: 0.4;
            cursor: not-allowed;
            box-shadow: none;
        }

        .feedback-box {
            background: rgba(0,0,0,0.6);
            border-radius: 12px;
            padding: 18px 22px;
            border-left: 5px solid var(--cyber-cyan);
            display: none;
            flex-direction: column;
            gap: 10px;
            font-size: 1.05rem;
            line-height: 1.5;
        }

        .feedback-box.correct {
            border-left-color: var(--cyber-green);
            background: rgba(0, 255, 102, 0.08);
        }

        .feedback-box.wrong {
            border-left-color: var(--cyber-pink);
            background: rgba(255, 0, 127, 0.08);
        }

        .maestra-msg {
            font-style: italic;
            color: var(--cyber-yellow);
            font-weight: 700;
            background: rgba(255, 234, 0, 0.1);
            padding: 8px 14px;
            border-radius: 8px;
            border: 1px dashed var(--cyber-yellow);
        }

        .modal-overlay {
            position: fixed;
            top: 0; left: 0; width: 100%; height: 100%;
            background: rgba(0,0,0,0.85);
            display: none;
            justify-content: center;
            align-items: center;
            z-index: 100;
            backdrop-filter: blur(8px);
        }

        .modal-card {
            background: var(--card-bg);
            border: 2px solid var(--cyber-green);
            border-radius: 20px;
            padding: 35px;
            max-width: 500px;
            width: 90%;
            text-align: center;
            box-shadow: 0 0 30px rgba(0, 255, 102, 0.5);
            display: flex;
            flex-direction: column;
            gap: 20px;
        }
    </style>
</head>
<body>

<div class="cyber-header">
    <div class="game-title">⚡ BIO-CYBER 2050</div>
    <div class="stats-panel">
        <div class="stat-box">⭐ XP: <span id="xp-val" class="stat-value">0</span></div>
        <div class="stat-box">🏆 Rango: <span id="rank-val" class="stat-value" style="color:var(--cyber-cyan);">Recluta</span></div>
    </div>
    <button class="audio-btn" id="audio-toggle" onclick="toggleAudio()">🔊 MÚSICA ON</button>
</div>

<div class="game-wrapper">
    <div class="mission-nav">
        <div class="mission-tab active" id="tab-m1" onclick="switchMission(1)">
            <span>NIVEL 1: Conceptos</span>
            <span class="mission-badge" id="badge-m1">0/10 completados</span>
        </div>
        <div class="mission-tab" id="tab-m2" onclick="switchMission(2)">
            <span>NIVEL 2: Clasificación</span>
            <span class="mission-badge" id="badge-m2">0/10 completados</span>
        </div>
        <div class="mission-tab" id="tab-m3" onclick="switchMission(3)">
            <span>NIVEL 3: Anatomía Visual</span>
            <span class="mission-badge" id="badge-m3">0/10 completados</span>
        </div>
        <div class="mission-tab" id="tab-m4" onclick="switchMission(4)">
            <span>NIVEL 4: Procesos</span>
            <span class="mission-badge" id="badge-m4">0/10 completados</span>
        </div>
    </div>

    <div class="progress-bar-container">
        <div class="progress-fill" id="overall-progress"></div>
    </div>

    <div id="quest-container"></div>
</div>

<div class="modal-overlay" id="level-modal">
    <div class="modal-card">
        <div class="modal-title" style="font-family:'Orbitron',sans-serif; color:var(--cyber-green); font-size:1.8rem;">¡MISIÓN CUMPLIDA! 🎉</div>
        <p id="modal-desc" style="font-size:1.2rem; line-height:1.5;"></p>
        <button class="cyber-btn" style="margin: 0 auto;" onclick="closeModal()">Continuar Misión ➔</button>
    </div>
</div>

<script>
// Nombres de archivos de imágenes adjuntas en el proyecto
const IMAGES = {
    respiratorio: "3a3d0c94bb970b7c1dc99f34b9515d38.jpg",
    circulatorio: "OIP_(2).webp",
    corazon_flujo: "OIP_(3).webp",
    digestivo_mudo: "dI-aE53X2yz3yHF0zeBUOg_b.jpg",
    corazon_detalle: "m_Hop002_Fig_68-01.webp",
    digestivo_color: "image-92.webp"
};

const PRAISE_MSGS = [
    "🌟 ¡Excelente trabajo! Tu maestra Mª Luz está súper orgullosa de tu avance. ¡Sigue así, recluta!",
    "👏 ¡Impresionante deducción! La maestra Mª Luz dice: '¡Así se investiga con rigor científico!'",
    "🎉 ¡Respuesta perfecta! Mª Luz manda un gran aplauso virtual a tu esfuerzo.",
    "🚀 ¡Conocimiento bio-médico al máximo! Maestra Mª Luz te otorga una estrella dorada virtual."
];

const ENCOURAGE_MSGS = [
    "💪 ¡Oye, no pasa nada! Hasta los mejores científicos tropiezan. Mª Luz dice: ¡lee la explicación y a por la siguiente!",
    "🔍 ¡Casi lo tienes! Como dice tu maestra Mª Luz: 'De los errores se aprende el doble'. ¡Ánimo!",
    "✨ ¡Sigue intentándolo! La maestra Mª Luz confía al 100% en tu capacidad de superación.",
    "🚀 ¡No te rindas! Revisa la pista de Mª Luz y verás qué claro lo ves ahora."
];

let audioCtx = null, bgmGain = null, isAudioPlaying = false, bgmOsc1 = null, bgmOsc2 = null;

function initAudio() {
    if (!audioCtx) audioCtx = new (window.AudioContext || window.webkitAudioContext)();
}

function toggleAudio() {
    initAudio();
    const btn = document.getElementById('audio-toggle');
    if (!isAudioPlaying) {
        startBGM(); btn.textContent = "🔊 MÚSICA ON"; isAudioPlaying = true;
    } else {
        stopBGM(); btn.textContent = "🔇 MÚSICA OFF"; isAudioPlaying = false;
    }
}

function startBGM() {
    if (!audioCtx) return;
    bgmGain = audioCtx.createGain();
    bgmGain.gain.setValueAtTime(0.04, audioCtx.currentTime);
    bgmGain.connect(audioCtx.destination);
    bgmOsc1 = audioCtx.createOscillator();
    bgmOsc2 = audioCtx.createOscillator();
    bgmOsc1.type = 'sine'; bgmOsc2.type = 'triangle';
    bgmOsc1.frequency.setValueAtTime(110, audioCtx.currentTime);
    bgmOsc2.frequency.setValueAtTime(164.81, audioCtx.currentTime);
    bgmOsc1.connect(bgmGain); bgmOsc2.connect(bgmGain);
    bgmOsc1.start(); bgmOsc2.start();
}

function stopBGM() {
    if (bgmOsc1) bgmOsc1.stop(); if (bgmOsc2) bgmOsc2.stop();
}

function playSfx(type) {
    if (!audioCtx) return;
    const osc = audioCtx.createOscillator(), gain = audioCtx.createGain();
    osc.connect(gain); gain.connect(audioCtx.destination);
    if (type === 'correct') {
        osc.type = 'triangle';
        osc.frequency.setValueAtTime(523.25, audioCtx.currentTime);
        osc.frequency.exponentialRampToValueAtTime(880, audioCtx.currentTime + 0.3);
        gain.gain.setValueAtTime(0.2, audioCtx.currentTime);
        gain.gain.exponentialRampToValueAtTime(0.01, audioCtx.currentTime + 0.3);
        osc.start(); osc.stop(audioCtx.currentTime + 0.3);
    } else if (type === 'wrong') {
        osc.type = 'sawtooth';
        osc.frequency.setValueAtTime(220, audioCtx.currentTime);
        osc.frequency.linearRampToValueAtTime(110, audioCtx.currentTime + 0.3);
        gain.gain.setValueAtTime(0.2, audioCtx.currentTime);
        gain.gain.exponentialRampToValueAtTime(0.01, audioCtx.currentTime + 0.3);
        osc.start(); osc.stop(audioCtx.currentTime + 0.3);
    } else if (type === 'levelup') {
        osc.type = 'square';
        osc.frequency.setValueAtTime(440, audioCtx.currentTime);
        osc.frequency.setValueAtTime(659.25, audioCtx.currentTime + 0.3);
        gain.gain.setValueAtTime(0.2, audioCtx.currentTime);
        gain.gain.exponentialRampToValueAtTime(0.01, audioCtx.currentTime + 0.5);
        osc.start(); osc.stop(audioCtx.currentTime + 0.5);
    }
}

// Batería completa de 40 Desafíos pedagógicos
const QUEST_DATA = [
    // NIVEL 1
    { id: "m1_q1", mission: 1, idx: 1, type: "mc", title: "Diferencia entre Nutrición y Alimentación", text: "¿Cuál es la afirmación correcta sobre la nutrición humana?", options: ["La nutrición es solo masticar y tragar los alimentos.", "La nutrición engloba la digestión, respiración, circulación y excreción.", "La alimentación es un proceso involuntario de las células."], correct: 1, explain: "¡Exacto! La nutrición es el conjunto de procesos (digestión, respiración, circulación y excreción) mediante los cuales obtenemos energía y materiales de los alimentos." },
    { id: "m1_q2", mission: 1, idx: 2, type: "mc", title: "Las Vías Respiratorias", text: "¿Qué tubo conduce el aire desde la laringe hacia los dos bronquios?", options: ["La tráquea", "El esófago", "El uréter"], correct: 0, explain: "¡Correcto! La tráquea es un tubo rígido formado por anillos de cartílago que se divide en dos bronquios para llegar a cada pulmón." },
    { id: "m1_q3", mission: 1, idx: 3, type: "mc", title: "Componentes de la Sangre", text: "¿Qué células sanguíneas contienen hemoglobina y transportan el oxígeno?", options: ["Glóbulos blancos", "Plaquetas", "Glóbulos rojos"], correct: 2, explain: "¡Excelente! Los glóbulos rojos contienen la proteína hemoglobina, que se une al oxígeno para llevarlo a todas las células." },
    { id: "m1_q4", mission: 1, idx: 4, type: "mc", title: "El Concepto de Excreción", text: "¿En qué consiste exactamente la excreción?", options: ["En la expulsión de heces por el ano.", "En la eliminación de productos de desecho celular transportados por la sangre.", "En coger oxígeno del aire."], correct: 1, explain: "¡Muy bien! La excreción es la limpieza de la sangre mediante la eliminación de desechos metabólicos (urea, sales) a través de riñones y sudor." },
    { id: "m1_q5", mission: 1, idx: 5, type: "mc", title: "Tipos de Vasos Sanguíneos", text: "¿Qué vasos sanguíneos llevan la sangre saliente desde el corazón hacia los órganos?", options: ["Las venas", "Las arterias", "Las glándulas"], correct: 1, explain: "¡Correcto! Las arterias nacen en los ventrículos del corazón y conducen la sangre a gran presión hacia todos los tejidos." },
    { id: "m1_q6", mission: 1, idx: 6, type: "mc", title: "Intercambio Gaseoso Alveolar", text: "¿En qué lugar exacto de los pulmones pasa el oxígeno a la sangre?", options: ["En la tráquea", "En las fosas nasales", "En los alveolos pulmonares"], correct: 2, explain: "¡Perfecto! Los alveolos pulmonares son diminutas bolsas rodeadas de capilares donde se realiza el intercambio gaseoso (hematosis)." },
    { id: "m1_q7", mission: 1, idx: 7, type: "mc", title: "Anatomía del Corazón", text: "¿En cuántas cavidades está dividido el corazón humano?", options: ["En 2 cavidades", "En 4 cavidades (2 aurículas y 2 ventrículos)", "En 3 cavidades"], correct: 1, explain: "¡Así es! El corazón tiene 4 cavidades: dos aurículas superiores que reciben sangre y dos ventrículos inferiores que la impulsan." },
    { id: "m1_q8", mission: 1, idx: 8, type: "mc", title: "Órganos del Aparato Urinario", text: "¿Qué tubos conducen la orina desde los riñones hasta la vejiga?", options: ["Los uréteres", "La uretra", "Los bronquiolos"], correct: 0, explain: "¡Bien deducido! Los uréteres son dos conductos musculares que conectan los riñones con la vejiga urinaria." },
    { id: "m1_q9", mission: 1, idx: 9, type: "mc", title: "Excreción por la Piel", text: "¿Qué glándulas de la piel se encargan de producir el sudor?", options: ["Glándulas salivales", "Glándulas sudoríparas", "Glándulas renales"], correct: 1, explain: "¡Correcto! Las glándulas sudoríparas filtran la sangre de la piel expulsando sudor para eliminar desechos y regular la temperatura." },
    { id: "m1_q10", mission: 1, idx: 10, type: "mc", title: "Nutrición Celular", text: "¿Para qué utilizan el oxígeno y los nutrientes las células de nuestro cuerpo?", options: ["Para producir energía y reparar estructuras.", "Únicamente para fabricar saliva.", "Para expulsar aire por la nariz."], correct: 0, explain: "¡Fantástico! Las células combinan nutrientes con oxígeno en la respiración celular para obtener la energía vital." },

    // NIVEL 2
    { id: "m2_q1", mission: 2, idx: 1, type: "match", title: "Clasificación de Células Sanguíneas", text: "Relaciona cada componente con su función principal:", pairs: [{ key: "Glóbulos Rojos", correct: "Transporte de oxígeno" }, { key: "Glóbulos Blancos", correct: "Defensa contra gérmenes" }, { key: "Plaquetas", correct: "Taponar heridas (coagulación)" }], optionsList: ["Transporte de oxígeno", "Defensa contra gérmenes", "Taponar heridas (coagulación)"], explain: "¡Perfecto! Los glóbulos rojos transportan O2, los blancos combaten infecciones y las plaquetas forman coágulos." },
    { id: "m2_q2", mission: 2, idx: 2, type: "match", title: "Vasos Sanguíneos y sus Estructuras", text: "Empareja cada vaso con su propiedad:", pairs: [{ key: "Arterias", correct: "Salen del corazón con paredes gruesas" }, { key: "Venas", correct: "Llevan la sangre de vuelta con válvulas" }, { key: "Capilares", correct: "Vasos ultrafinos de intercambio" }], optionsList: ["Salen del corazón con paredes gruesas", "Llevan la sangre de vuelta con válvulas", "Vasos ultrafinos de intercambio"], explain: "¡Excelente clasificación! Las arterias aguantan gran presión, las venas evitan el retroceso y los capilares permiten la difusión." },
    { id: "m2_q3", mission: 2, idx: 3, type: "match", title: "Aparato Urinario y sus Partes", text: "Relaciona el órgano urinario con su tarea:", pairs: [{ key: "Riñones", correct: "Filtrar la sangre y formar orina" }, { key: "Vejiga", correct: "Almacenar la orina hasta expulsarla" }, { key: "Uretra", correct: "Conducto de salida al exterior" }], optionsList: ["Filtrar la sangre y formar orina", "Almacenar la orina hasta expulsarla", "Conducto de salida al exterior"], explain: "¡Gran trabajo! Los riñones fabrican la orina, la vejiga la almacena acumulando líquido y la uretra la expulsa." },
    { id: "m2_q4", mission: 2, idx: 4, type: "match", title: "Fases de la Digestión", text: "Relaciona la etapa digestiva con la mezcla resultante:", pairs: [{ key: "Boca + Saliva", correct: "Bolo alimenticio" }, { key: "Estómago + Jugo gástrico", correct: "Quimo" }, { key: "Intestino delgado + Bilis/Jugo", correct: "Quilo" }], optionsList: ["Bolo alimenticio", "Quimo", "Quilo"], explain: "¡Muy bien! El bolo se forma en la boca, se transforma en quimo en el estómago y finalmente en quilo en el intestino delgado." },
    { id: "m2_q5", mission: 2, idx: 5, type: "mc", title: "Movimientos Respiratorios", text: "Durante la INSPIRACIÓN, ¿qué ocurre con el diafragma y los pulmones?", options: ["El diafragma se contrae y baja, el tórax se expande y entra aire.", "El diafragma se relaja y sube, el tórax se estrecha y sale aire.", "Los pulmones se vacían sin moverse."], correct: 0, explain: "¡Correcto! Al inspirar, el diafragma baja aumentando el volumen torácico, creando succión para que entre el aire ambiental." },
    { id: "m2_q6", mission: 2, idx: 6, type: "mc", title: "Circuitos Sanguíneos", text: "¿Cuál es la meta de la CIRCULACIÓN PULMONAR (o menor)?", options: ["Llevar nutrientes al cerebro y las piernas.", "Llevar sangre del corazón a los pulmones para oxigenarse y eliminar CO2.", "Filtrar la orina en los riñones."], correct: 1, explain: "¡Exacto! La circulación menor conecta corazón y pulmones para recargar oxígeno y soltar dióxido de carbono." },
    { id: "m2_q7", mission: 2, idx: 7, type: "mc", title: "Clasificación de Hábitos Saludables", text: "¿Cuál combinación contiene ÚNICAMENTE hábitos saludables para la nutrición?", options: ["Beber 1,5L agua al día, ventilar el aula y hacer deporte.", "Fumar, beber refrescos azucarados y no ducharse.", "Comer solo hamburguesas y no salir."], correct: 0, explain: "¡Así se habla! La hidratación, la ventilación del aire y el ejercicio garantizan el rendimiento óptimo del corazón y riñones." },
    { id: "m2_q8", mission: 2, idx: 8, type: "match", title: "Glándulas Anejas", text: "Relaciona la glándula con su secreción:", pairs: [{ key: "Hígado", correct: "Bilis (para grasas)" }, { key: "Páncreas", correct: "Jugo pancreático" }, { key: "Glándulas salivales", correct: "Saliva" }], optionsList: ["Bilis (para grasas)", "Jugo pancreático", "Saliva"], explain: "¡Exacto! La bilis del hígado digiere grasas, el jugo pancreático actúa en el intestino y la saliva descompone el almidón." },
    { id: "m2_q9", mission: 2, idx: 9, type: "mc", title: "Movimientos Cardíacos", text: "¿Cómo se llama la fase en la que el corazón se relaja y se llena de sangre procedente de las venas?", options: ["Sístole", "Diástole", "Hematosis"], correct: 1, explain: "¡Muy bien! En la diástole el corazón se dilata y se llena. En la sístole se contrae con fuerza para impulsar la sangre." },
    { id: "m2_q10", mission: 2, idx: 10, type: "mc", title: "Órganos del Aparato Respiratorio", text: "¿A qué aparato pertenecen la tráquea, los bronquios y los alveolos?", options: ["Aparato Excretor", "Aparato Respiratorio", "Aparato Circulatorio"], correct: 1, explain: "¡Correcto! Todos estos conductos y estructuras forman el aparato respiratorio." },

    // NIVEL 3 (VISUAL)
    { id: "m3_q1", mission: 3, idx: 1, type: "visual_mc", title: "Aparato Respiratorio", imgKey: "respiratorio", text: "Observa la figura del aparato respiratorio. ¿Qué órgano señala la etiqueta verde en la parte inferior del cuello?", options: ["La Faringe", "La Tráquea", "Los Pulmones"], correct: 1, explain: "¡Correcto! La etiqueta verde señala la Tráquea, el conducto anillado que desciende hacia el pecho." },
    { id: "m3_q2", mission: 3, idx: 2, type: "visual_mc", title: "Circuitos de la Circulación", imgKey: "circulatorio", text: "Observa el mapa de circulación. El circuito superior en rojo y azul que conecta corazón y pulmones es:", options: ["La Circulación Pulmonar (Menor)", "La Circulación General (Mayor)", "El Aparato Excretor"], correct: 0, explain: "¡Exacto! El bucle superior es el circuito pulmonar donde la sangre se oxigena en los pulmones." },
    { id: "m3_q3", mission: 3, idx: 3, type: "visual_mc", title: "Anatomía del Corazón", imgKey: "corazon_flujo", text: "Observa las flechas del flujo cardíaco. Las cavidades superiores que reciben sangre de las venas son:", options: ["Los Ventrículos", "Las Aurículas", "Las Válvulas"], correct: 1, explain: "¡Así es! Las aurículas (derecha e izquierda) están arriba y reciben la sangre que entra al corazón." },
    { id: "m3_q4", mission: 3, idx: 4, type: "visual_mc", title: "Aparato Digestivo", imgKey: "digestivo_color", text: "En este esquema del aparato digestivo, ¿cuál es el órgano pardo que produce la bilis?", options: ["El Estómago", "El Hígado", "El Intestino Grueso"], correct: 1, explain: "¡Perfecto! El hígado es la glándula parda de gran tamaño situada a la derecha del estómago." },
    { id: "m3_q5", mission: 3, idx: 5, type: "visual_mc", title: "Sección Interna del Corazón", imgKey: "corazon_detalle", text: "En el dibujo del corazón se aprecian dos lados separados. ¿Por qué no se mezclan las sangres?", options: ["Porque el lado derecho (sangre azul) y el izquierdo (sangre roja) están separados por un tabique muscular.", "Porque la sangre se limpia sola.", "Porque el corazón se vacía totalmente."], correct: 0, explain: "¡Brillante! El tabique cardíaco impide que la sangre desoxigenada del lado derecho se mezcle con la oxigenada del izquierdo." },
    { id: "m3_q6", mission: 3, idx: 6, type: "visual_mc", title: "Aparato Urinario en el Cuerpo", imgKey: "circulatorio", text: "En la parte inferior del esquema circulatorio se aprecian dos órganos rojizos con forma de alubia. Son:", options: ["Los Riñones", "Los Pulmones", "Las Glándulas Salivales"], correct: 0, explain: "¡Correcto! Los riñones tienen forma de alubia y reciben un gran flujo sanguíneo para filtrarlo." },
    { id: "m3_q7", mission: 3, idx: 7, type: "visual_mc", title: "El Intestino Delgado", imgKey: "digestivo_mudo", text: "En el tubo digestivo inferior, ¿cuál es el conducto más largo y replegado donde se absorben los nutrientes?", options: ["El Esófago", "El Intestino Delgado", "El Intestino Grueso"], correct: 1, explain: "¡Muy bien! El intestino delgado mide varios metros de longitud y posee vellosidades para absorber nutrientes." },
    { id: "m3_q8", mission: 3, idx: 8, type: "visual_mc", title: "Vía Respiratoria Superior", imgKey: "respiratorio", text: "En la figura del aparato respiratorio, la vía común para el aire y los alimentos situada detrás de la boca es:", options: ["La Faringe", "Los Bronquiolos", "La Vejiga"], correct: 0, explain: "¡Excelente! La faringe es una cavidad compartida por el aparato digestivo y el respiratorio." },
    { id: "m3_q9", mission: 3, idx: 9, type: "visual_mc", title: "Tubo Digestivo Superior", imgKey: "digestivo_color", text: "¿Qué tubo muscular conecta la faringe con el estómago en la imagen?", options: ["La Tráquea", "El Esófago", "El Uréter"], correct: 1, explain: "¡Correcto! El esófago conduce el bolo alimenticio mediante movimientos peristálticos hacia el estómago." },
    { id: "m3_q10", mission: 3, idx: 10, type: "visual_mc", title: "Red de Capilares", imgKey: "circulatorio", text: "En el dibujo del cuerpo completo, la red de vasos sanguíneos llega hasta la punta de los dedos. ¿Qué vasos tan finos forman esta red?", options: ["Los Capilares sanguíneos", "La Arteria Aorta", "Los Uréteres"], correct: 0, explain: "¡Genial! Los capilares forman una tupida red microscópica que llega a cada célula." },

    // NIVEL 4
    { id: "m4_q1", mission: 4, idx: 1, type: "mc", title: "Proceso de Hematosis Alveolar", text: "¿Cómo se realiza exactamente el intercambio de gases en los alveolos pulmonares?", options: ["El O2 del aire pasa a los capilares y el CO2 de la sangre pasa al alveolo por difusión.", "El aire se convierte en agua.", "La sangre se limpia en el estómago."], correct: 0, explain: "¡Explicación perfecta! Debido a la diferencia de concentración, el O2 atraviesa la pared alveolar hacia los glóbulos rojos, mientras el CO2 realiza el camino inverso para ser expulsado." },
    { id: "m4_q2", mission: 4, idx: 2, type: "mc", title: "Secuencia Completa de la Digestión", text: "Selecciona el orden CRONOLÓGICO correcto de los estados del alimento a lo largo del tubo digestivo:", options: ["Alimento ➔ Bolo alimenticio (boca) ➔ Quimo (estómago) ➔ Quilo (intestino delgado) ➔ Heces (intestino grueso)", "Alimento ➔ Quilo ➔ Quimo ➔ Bolo alimenticio", "Alimento ➔ Orina ➔ Quimo ➔ Bilis"], correct: 0, explain: "¡Proceso impecable! 1º Masticación (Bolo) ➔ 2º Jugos gástricos (Quimo) ➔ 3º Bilis y jugo pancreático (Quilo) ➔ 4º Absorción y heces." },
    { id: "m4_q3", mission: 4, idx: 3, type: "mc", title: "El Recorrido de la Sangre (Circulación Doble)", text: "Sigue la pista de un glóbulo rojo cargado de CO2 que llega de la pierna al corazón. ¿Cuál es su recorrido?", options: ["Vena cava ➔ Aurícula dcha ➔ Ventrículo dcho ➔ Arteria pulmonar ➔ Pulmones ➔ Venas pulmonares ➔ Aurícula izq ➔ Ventrículo izq ➔ Aorta", "Aorta ➔ Ventrículo izq ➔ Pulmones ➔ Hígado", "Vena cava ➔ Vejiga ➔ Riñón ➔ Corazón"], correct: 0, explain: "¡Brillante recorrido! Pasa primero por el lado derecho hacia los pulmones para limpiarse y regresa al lado izquierdo para impulsarse a todo el cuerpo por la arteria Aorta." },
    { id: "m4_q4", mission: 4, idx: 4, type: "mc", title: "Mecanismo de Filtración Renal", text: "¿Cómo convierten los riñones la sangre filtrada en orina?", options: ["Filtran el plasma reteniendo sustancias útiles y concentran el agua sobrante con desechos (urea y sales).", "Mezclan la sangre con bilis.", "Evaporan la sangre."], correct: 0, explain: "¡Exacto! Los nefrones renales filtran la sangre de forma continua: devuelven a la circulación los nutrientes útiles y expulsan las toxinas disueltas en agua." },
    { id: "m4_q5", mission: 4, idx: 5, type: "mc", title: "Mecanismo de la Inhalación", text: "¿Por qué entra aire a nuestros pulmones cuando el diafragma baja?", options: ["Porque aumenta el volumen torácico, disminuyendo la presión interna y haciendo que el aire exterior entre empujado por la presión atmosférica.", "Porque el estómago empuja el aire.", "Porque los pulmones son globos eléctricos."], correct: 0, explain: "¡Fundamentación científica de 10! El aumento de volumen torácico genera una presión negativa interna que fuerza la entrada del aire." },
    { id: "m4_q6", mission: 4, idx: 6, type: "mc", title: "Doble Función del Sudor", text: "¿Qué dos funciones vitales realiza el sudor fabricado en las glándulas sudoríparas?", options: ["Excretora (elimina desechos) y Termorreguladora (al evaporarse en la piel absorbe calor y la enfría).", "Digestiva y Respiratoria.", "Circulatoria y Auditiva."], correct: 0, explain: "¡Excelente! El sudor elimina toxinas y evita que la temperatura corporal se eleve en exceso al evaporarse sobre la piel." },
    { id: "m4_q7", mission: 4, idx: 7, type: "mc", title: "Absorción y Distribución de Nutrientes", text: "¿Cómo viajan los nutrientes desde el intestino hasta las células del cuerpo?", options: ["Atraviesan las vellosidades del intestino delgado, entran a los capilares y el corazón los bombea por la sangre.", "Van flotando por el aire.", "Bajan por los uréteres."], correct: 0, explain: "¡Conexión de sistemas perfecta! El aparato digestivo aporta los nutrientes a la sangre y el circulatorio se encarga de su distribución a cada tejido." },
    { id: "m4_q8", mission: 4, idx: 8, type: "mc", title: "Efectos Nocivos del Tabaquismo", text: "¿Por qué el humo del tabaco destruye la capacidad respiratoria?", options: ["Porque el alquitrán destruye los cilios y rompe las paredes alveolares, reduciendo la superficie de intercambio de oxígeno.", "Porque convierte la sangre en bilis.", "Porque bloquea los uréteres."], correct: 0, explain: "¡Argumentación médica intachable! El tabaco destruye las paredes de los alveolos pulmonares, reduciendo drásticamente la captación de oxígeno." },
    { id: "m4_q9", mission: 4, idx: 9, type: "mc", title: "El Papel de las Válvulas Venosas", text: "¿Por qué las venas de las piernas tienen válvulas semilunares en su interior?", options: ["Para impedir que la sangre refluya hacia abajo debido a la gravedad mientras sube de vuelta al corazón.", "Para fabricar glóbulos blancos.", "Para enfriar la sangre."], correct: 0, explain: "¡Mecánica cardiovascular brillante! Como la sangre de las piernas sube contra la gravedad, las válvulas de las venas actúan como compuertas antirretorno." },
    { id: "m4_q10", mission: 4, idx: 10, type: "mc", title: "Integración Total de la Nutrición", text: "Sintetiza la colaboración de los 4 aparatos en la función de nutrición:", options: ["Digestivo (aporta nutrientes) + Respiratorio (aporta O2) ➔ Circulatorio (los transporta a células) ➔ Excretor (elimina residuos por orina/sudor).", "Digestivo y Excretor no se relacionan con la sangre.", "La nutrición la realiza solo el circulatorio."], correct: 0, explain: "¡SÍNTESIS MAESTRA! Has demostrado un dominio completo de la Nutrición Humana. ¡Felicidades, Máster Bio-Médico!" }
];

let currentMission = 1, userAnswers = {}, userXp = 0, completedQuests = new Set();

function renderQuests() {
    const container = document.getElementById('quest-container');
    container.innerHTML = '';
    const currentQuests = QUEST_DATA.filter(q => q.mission === currentMission);

    currentQuests.forEach((q) => {
        const card = document.createElement('div');
        card.className = 'quest-card';
        card.id = `card-${q.id}`;

        let html = `
            <div class="quest-header">
                <span class="quest-number">MISIÓN ${q.mission} - DESAFÍO ${q.idx}/10</span>
                <span style="font-size:0.85rem; color:var(--cyber-yellow);">+100 XP</span>
            </div>
            <div class="quest-title">${q.title}</div>
            <div class="quest-body">${q.text}</div>
        `;

        if (q.imgKey && IMAGES[q.imgKey]) {
            html += `<div class="img-preview-box"><img src="${IMAGES[q.imgKey]}" alt="${q.title}"></div>`;
        }

        if (q.type === 'mc' || q.type === 'visual_mc') {
            html += `<div class="options-list">`;
            q.options.forEach((opt, oIdx) => {
                html += `
                    <button class="option-btn" id="btn-${q.id}-${oIdx}" onclick="selectMcOption('${q.id}', ${oIdx})">
                        <span>⚡</span> <span>${opt}</span>
                    </button>
                `;
            });
            html += `</div>`;
        } else if (q.type === 'match') {
            html += `<div class="match-grid">`;
            q.pairs.forEach((pair, pIdx) => {
                html += `
                    <div style="font-weight:700; color:var(--cyber-cyan); display:flex; align-items:center;">${pair.key} ➔</div>
                    <div>
                        <select class="select-custom" id="sel-${q.id}-${pIdx}">
                            <option value="">-- Selecciona Correspondencia --</option>
                            ${q.optionsList.map(o => `<option value="\\({o}">\\){o}</option>`).join('')}
                        </select>
                    </div>
                `;
            });
            html += `</div>`;
        }

        html += `
            <div style="display:flex; justify-content:space-between; align-items:center; margin-top:15px;">
                <button class="cyber-btn" id="check-${q.id}" onclick="verifyQuest('${q.id}')">🔍 COMPROBAR & ANALIZAR</button>
            </div>
            <div class="feedback-box" id="fb-${q.id}">
                <div class="maestra-msg" id="msg-${q.id}"></div>
                <div id="exp-${q.id}"></div>
            </div>
        `;

        card.innerHTML = html;
        container.appendChild(card);
    });

    updateProgressUI();
}

function switchMission(mNum) {
    currentMission = mNum;
    for (let i = 1; i <= 4; i++) document.getElementById(`tab-m${i}`).classList.remove('active');
    document.getElementById(`tab-m${mNum}`).classList.add('active');
    renderQuests();
}

function selectMcOption(qId, oIdx) {
    const quest = QUEST_DATA.find(q => q.id === qId);
    quest.options.forEach((_, idx) => {
        document.getElementById(`btn-${qId}-${idx}`).classList.remove('selected');
    });
    document.getElementById(`btn-${qId}-${oIdx}`).classList.add('selected');
    userAnswers[qId] = oIdx;
}

function verifyQuest(qId) {
    initAudio();
    const quest = QUEST_DATA.find(q => q.id === qId);
    const fbBox = document.getElementById(`fb-${qId}`);
    const msgEl = document.getElementById(`msg-${qId}`);
    const expEl = document.getElementById(`exp-${qId}`);
    const checkBtn = document.getElementById(`check-${qId}`);

    let isCorrect = false;

    if (quest.type === 'mc' || quest.type === 'visual_mc') {
        const selected = userAnswers[qId];
        if (selected === undefined) {
            alert("⚠️ Selecciona una opción antes de comprobar.");
            return;
        }
        isCorrect = (selected === quest.correct);
        quest.options.forEach((_, idx) => {
            const btn = document.getElementById(`btn-${qId}-${idx}`);
            btn.disabled = true;
            if (idx === quest.correct) btn.classList.add('correct-opt');
            else if (idx === selected) btn.classList.add('wrong-opt');
        });
    } else if (quest.type === 'match') {
        let allCorrect = true;
        quest.pairs.forEach((pair, pIdx) => {
            const sel = document.getElementById(`sel-${qId}-${pIdx}`);
            if (sel.value !== pair.correct) allCorrect = false;
            sel.disabled = true;
        });
        isCorrect = allCorrect;
    }

    checkBtn.disabled = true;
    fbBox.style.display = 'flex';

    if (isCorrect) {
        playSfx('correct');
        fbBox.className = 'feedback-box correct';
        msgEl.innerHTML = PRAISE_MSGS[Math.floor(Math.random() * PRAISE_MSGS.length)];
        if (!completedQuests.has(qId)) {
            completedQuests.add(qId);
            userXp += 100;
            document.getElementById('xp-val').textContent = userXp;
            updateRank();
        }
    } else {
        playSfx('wrong');
        fbBox.className = 'feedback-box wrong';
        msgEl.innerHTML = ENCOURAGE_MSGS[Math.floor(Math.random() * ENCOURAGE_MSGS.length)];
    }

    expEl.innerHTML = `<strong>Análisis Razonado:</strong> ${quest.explain}`;

    updateProgressUI();
    checkMissionCompletion();
}

function updateRank() {
    const rankEl = document.getElementById('rank-val');
    if (userXp >= 3500) rankEl.textContent = "🥇 Máster Bio-Médico";
    else if (userXp >= 2500) rankEl.textContent = "🥈 Especialista Anatómico";
    else if (userXp >= 1200) rankEl.textContent = "🥉 Cadete Nutricional";
    else rankEl.textContent = "Recluta Bio-Cyber";
}

function updateProgressUI() {
    for (let m = 1; m <= 4; m++) {
        const mQuests = QUEST_DATA.filter(q => q.mission === m);
        const done = mQuests.filter(q => completedQuests.has(q.id)).length;
        document.getElementById(`badge-m${m}`).textContent = `${done}/10 completados`;
    }
    const percent = (completedQuests.size / QUEST_DATA.length) * 100;
    document.getElementById('overall-progress').style.width = `${percent}%`;
}

function checkMissionCompletion() {
    const currentMQuests = QUEST_DATA.filter(q => q.mission === currentMission);
    const mDone = currentMQuests.filter(q => completedQuests.has(q.id)).length;
    if (mDone === 10) {
        playSfx('levelup');
        const modal = document.getElementById('level-modal');
        document.getElementById('modal-desc').innerHTML = `🌟 ¡Has completado los 10 desafíos del <strong>NIVEL ${currentMission}</strong>!<br><br>Tu Maestra Mª Luz te felicita efusivamente por tu constancia y rigor científico. ¡Sigue así para lograr el rango de Máster Bio-Médico!`;
        modal.style.display = 'flex';
    }
}

function closeModal() {
    document.getElementById('level-modal').style.display = 'none';
    if (currentMission < 4) switchMission(currentMission + 1);
}

window.onload = () => { renderQuests(); };
</script>
</body>
</html>
