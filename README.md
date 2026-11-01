<!DOCTYPE html>
<html lang="it">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Per Elena - Il Mio Grande Amore</title>
    <link href="https://fonts.googleapis.com/css2?family=Dancing+Script:wght@600;700&family=Poppins:wght@300;400;600&display=swap" rel="stylesheet">
    <style>
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }

        body {
            font-family: 'Poppins', sans-serif;
            color: #fff;
            min-height: 100vh;
            overflow-x: hidden;
            position: relative;
            background-color: #0d0d0d;
        }

        /* SFONDO DINAMICO (SLIDESHOW 6 FOTO) */
        .bg-slideshow {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -2;
        }

        .bg-slide {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-size: cover;
            background-position: center;
            opacity: 0;
            transition: opacity 1.5s ease-in-out;
            filter: brightness(0.45);
        }

        .bg-slide.active {
            opacity: 1;
        }

        .overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: radial-gradient(circle, rgba(0,0,0,0.2) 0%, rgba(0,0,0,0.85) 100%);
            z-index: -1;
        }

        /* CONTAINER PRINCIPALE */
        .container {
            max-width: 800px;
            margin: 0 auto;
            padding: 40px 20px;
            text-align: center;
        }

        /* VINILE / GIRADISCHI */
        .player-section {
            margin-bottom: 30px;
            display: flex;
            flex-direction: column;
            align-items: center;
        }

        .vinyl-container {
            position: relative;
            width: 140px;
            height: 140px;
            cursor: pointer;
            transition: transform 0.3s ease;
        }

        .vinyl-container:hover {
            transform: scale(1.08);
        }

        .vinyl {
            width: 100%;
            height: 100%;
            border-radius: 50%;
            background: repeating-radial-gradient(
                #111,
                #111 2px,
                #222 3px,
                #222 4px
            );
            box-shadow: 0 8px 25px rgba(0,0,0,0.6), inset 0 0 0 2px #333;
            display: flex;
            justify-content: center;
            align-items: center;
            animation: spin 4s linear infinite;
            animation-play-state: paused;
        }

        .vinyl.playing {
            animation-play-state: running;
        }

        .vinyl-center {
            width: 45px;
            height: 45px;
            background: linear-gradient(45deg, #ff4b2b, #ff416c);
            border-radius: 50%;
            border: 3px solid #111;
            display: flex;
            justify-content: center;
            align-items: center;
            font-size: 10px;
            font-weight: bold;
            color: #fff;
            text-transform: uppercase;
        }

        .music-hint {
            margin-top: 12px;
            font-size: 0.90rem;
            color: #ddd;
            background: rgba(0,0,0,0.5);
            padding: 6px 16px;
            border-radius: 20px;
            backdrop-filter: blur(5px);
            border: 1px solid rgba(255,255,255,0.2);
        }

        @keyframes spin {
            100% { transform: rotate(360deg); }
        }

        /* INTESTAZIONE */
        h1 {
            font-family: 'Dancing Script', cursive;
            font-size: 3.2rem;
            color: #ff6b81;
            text-shadow: 0 4px 15px rgba(255, 107, 129, 0.4);
            margin-bottom: 10px;
        }

        .subtitle {
            font-size: 1.1rem;
            color: #e0e0e0;
            margin-bottom: 40px;
            font-weight: 300;
        }

        /* SCHEDE DEDICHE */
        .card {
            background: rgba(20, 20, 20, 0.65);
            backdrop-filter: blur(10px);
            border-radius: 18px;
            padding: 30px;
            margin-bottom: 35px;
            border: 1px solid rgba(255, 255, 255, 0.12);
            box-shadow: 0 10px 30px rgba(0,0,0,0.5);
            text-align: left;
            transition: transform 0.3s ease, border-color 0.3s ease;
        }

        .card:hover {
            transform: translateY(-5px);
            border-color: rgba(255, 107, 129, 0.4);
        }

        .card-number {
            font-size: 0.85rem;
            text-transform: uppercase;
            letter-spacing: 2px;
            color: #ff6b81;
            margin-bottom: 8px;
            font-weight: 600;
        }

        .card-title {
            font-family: 'Dancing Script', cursive;
            font-size: 2rem;
            color: #fff;
            margin-bottom: 15px;
        }

        .card-text {
            font-size: 1rem;
            line-height: 1.8;
            color: #d1d1d1;
        }

        /* LETTERA FINALE */
        .final-letter {
            background: rgba(255, 255, 255, 0.08);
            border: 2px solid #ff6b81;
            border-radius: 20px;
            padding: 40px 30px;
            margin-top: 50px;
            position: relative;
        }

        .final-letter h2 {
            font-family: 'Dancing Script', cursive;
            font-size: 2.8rem;
            color: #ff6b81;
            margin-bottom: 20px;
        }

        .final-letter p {
            font-size: 1.05rem;
            line-height: 1.9;
            color: #f0f0f0;
            white-space: pre-line;
            text-align: left;
        }

        .countdown-box {
            margin-top: 30px;
            padding: 15px;
            background: rgba(255, 107, 129, 0.15);
            border-radius: 12px;
            border: 1px dashed #ff6b81;
            font-weight: 600;
            color: #fff;
        }

        footer {
            margin-top: 40px;
            font-size: 0.85rem;
            color: #888;
        }
    </style>
</head>
<body>

    <!-- SFONDO CON 6 FOTO -->
    <div class="bg-slideshow">
        <div class="bg-slide active" style="background-image: url('foto1.jpg');"></div>
        <div class="bg-slide" style="background-image: url('foto2.jpg');"></div>
        <div class="bg-slide" style="background-image: url('foto3.jpg');"></div>
        <div class="bg-slide" style="background-image: url('foto4.jpg');"></div>
        <div class="bg-slide" style="background-image: url('foto5.jpg');"></div>
        <div class="bg-slide" style="background-image: url('foto6.jpg');"></div>
    </div>
    <div class="overlay"></div>

    <div class="container">
        
        <!-- VINILE PLAYER -->
        <div class="player-section">
            <div class="vinyl-container" id="vinylBtn" onclick="toggleAudio()">
                <div class="vinyl" id="vinyl">
                    <div class="vinyl-center">PLAY</div>
                </div>
            </div>
            <div class="music-hint" id="musicHint">🎵 Clicca sul vinile per "Sentire la musica"</div>
        </div>

        <audio id="bgMusic" loop>
            <source src="canzone.mp3" type="audio/mpeg">
            Il tuo browser non supporta l'audio HTML5.
        </audio>

        <!-- INTESTAZIONE -->
        <h1>Per Elena, l'Amore della Mia Vita</h1>
        <p class="subtitle">La nostra storia, passo dopo passo... ❤️</p>

        <!-- 5 DEDICHE IN CRESCITA -->
        
        <!-- Dedica 1 -->
        <div class="card">
            <div class="card-number">Capitolo I</div>
            <h3 class="card-title">L'Inizio di Tutto</h3>
            <p class="card-text">
                Tutto è partito il <strong>22 agosto 2026 alle ore 11:57</strong>. Un giorno qualunque trasformato nel giorno più bello grazie a un messaggio su WhatsApp inviato dal mio migliore amico Andrea. Tra uno schermo e l'altro abbiamo iniziato a parlare, senza sapere che quel singolo momento avrebbe cambiato le nostre vite per sempre. Due giorni dopo, il <strong>24 agosto</strong>, è iniziato ufficialmente il nostro cammino insieme.
            </p>
        </div>

        <!-- Dedica 2 -->
        <div class="card">
            <div class="card-number">Capitolo II</div>
            <h3 class="card-title">Il Primo Incontro</h3>
            <p class="card-text">
                Nonostante i chilometri e la distanza che ci separano, l'attesa è svanita dopo qualche settimana da quel primo messaggio. Il momento in cui ti ho vista dal vivo per la prima volta rimarrà impresso nel mio cuore per sempre. Guardarti negli occhi dal vivo ha azzerato qualsiasi distanza: non c'era più uno schermo, c'eravamo solo io e te.
            </p>
        </div>

        <!-- Dedica 3 -->
        <div class="card">
            <div class="card-number">Capitolo III</div>
            <h3 class="card-title">Superare i Primi Ostacoli</h3>
            <p class="card-text">
                Come in ogni vera storia d'amore, abbiamo affrontato i primi momenti di difficoltà e le incomprensioni legate anche alla lontananza. Ma ogni piccolo ostacolo ci ha solo dimostrato quanto teniamo l'uno all'altra. Ogni volta ne siamo usciti più forti, più uniti e più certi che quello che c'è tra noi è unico e incrollabile.
            </p>
        </div>

        <!-- Dedica 4 -->
        <div class="card">
            <div class="card-number">Capitolo IV</div>
            <h3 class="card-title">Noi, la Mia Certezza</h3>
            <p class="card-text">
                Le 5 volte che ci siamo visti finora sono state tra i giorni più intensi della mia vita. Ogni abbraccio, ogni risata, ogni sguardo condiviso mi conferma che sei la persona giusta per me. Sei la mia certezza quotidiana, la ragazza speciale che riesce a farmi sorridere anche a distanza.
            </p>
        </div>

        <!-- Dedica 5 -->
        <div class="card">
            <div class="card-number">Capitolo V</div>
            <h3 class="card-title">I Nostri Primi 2 Mesi</h3>
            <p class="card-text">
                Abbiamo già superato il traguardo dei nostri primi 2 mesi insieme. Due mesi volati via, pieni d'amore, di chiamate, di attimi indimenticabili e di sogni condivisi. Questo è solo il primissimo capitolo di un libro lunghissimo che voglio scrivere interamente al tuo fianco.
            </p>
        </div>

        <!-- LETTERA FINALE -->
        <div class="final-letter">
            <h2>Lettera per la Mia Futura Moglie</h2>
            <p>
Cara Elena,
Questa lettera la dedico all'amore della mia vita, nonché tu, la mia futura moglie. 

Non serve un'occasione speciale per ricordarti quanto sei importante per me. Ho voluto creare questo piccolo spazio per lasciarti un segno del mio amore, qualcosa che puoi guardare ogni volta che ti manco o quando vuoi sentire quanto sei amata.

Non importa la distanza, non contano i chilometri: il mio cuore è sempre lì con te. Grazie per ogni momento, per ogni sorriso e per come mi fai sentire ogni giorno. Sei l'unica per me.

Con tutto l'amore che ho,
Vincenzo.
            </p>

            <div class="countdown-box">
                🗓️ Prossimo incontro: <strong>14 Novembre</strong> (Mancano pochissimi giorni! ❤️)
            </div>
        </div>

        <footer>
            Realizzato con amore per Elena 💖
        </footer>

    </div>

    <!-- JAVASCRIPT PER AUDIO E SLIDESHOW FOTO -->
    <script>
        // Gestione Musica e Vinile
        const audio = document.getElementById('bgMusic');
        const vinyl = document.getElementById('vinyl');
        const musicHint = document.getElementById('musicHint');

        function toggleAudio() {
            if (audio.paused) {
                audio.play();
                vinyl.classList.add('playing');
                musicHint.textContent = "🎵 Musica in riproduzione... Clicca per mettere in pausa";
            } else {
                audio.pause();
                vinyl.classList.remove('playing');
                musicHint.textContent = "🎵 Clicca sul vinile per 'Sentire la musica'";
            }
        }

        // Gestione Slideshow 6 Foto (Ogni 4 secondi)
        const slides = document.querySelectorAll('.bg-slide');
        let currentSlide = 0;

        function nextSlide() {
            slides[currentSlide].classList.remove('active');
            currentSlide = (currentSlide + 1) % slides.length;
            slides[currentSlide].classList.add('active');
        }

        // Cambia foto ogni 4 secondi (4000 ms)
        setInterval(nextSlide, 4000);
    </script>
</body>
</html>
