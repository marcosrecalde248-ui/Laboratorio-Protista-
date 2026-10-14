<!DOCTYPE html>
<html lang="es" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Laboratorio Virtual de Biología: Reino Protista</title>
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- FontAwesome for Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <!-- Google Fonts -->
    <link href="https://fonts.googleapis.com/css2?family=Fredoka:wght@400;600;700&family=Plus+Jakarta+Sans:wght@400;600;700;800&display=swap" rel="stylesheet">
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    fontFamily: {
                        sans: ['"Plus Jakarta Sans"', 'sans-serif'],
                        display: ['"Fredoka"', 'cursive'],
                    },
                    colors: {
                        bio: {
                            50: '#f0fdf4',
                            100: '#dcfce7',
                            400: '#4ade80',
                            500: '#22c55e',
                            600: '#16a34a',
                            900: '#14532d'
                        }
                    }
                }
            }
        }
    </script>
    <style>
        .retro-card {
            background: #ffffff;
            border: 3px solid #0f172a;
            box-shadow: 5px 5px 0px #0f172a;
            transition: all 0.15s ease;
        }
        .retro-card:hover {
            transform: translate(-2px, -2px);
            box-shadow: 7px 7px 0px #0f172a;
        }
        .retro-btn {
            border: 2px solid #0f172a;
            box-shadow: 3px 3px 0px #0f172a;
            transition: all 0.1s ease;
        }
        .retro-btn:active {
            transform: translate(2px, 2px);
            box-shadow: 1px 1px 0px #0f172a;
        }
    </style>
</head>
<body class="bg-slate-900 text-slate-100 font-sans antialiased pb-12 select-none">

    <header class="sticky top-0 z-50 bg-slate-950/90 backdrop-blur-md border-b-2 border-slate-800 py-3">
        <div class="max-w-6xl mx-auto px-4 flex items-center justify-between">
            <div class="flex items-center gap-3">
                <div class="w-10 h-10 rounded-xl bg-bio-500 text-slate-950 flex items-center justify-center font-bold text-xl shadow-md">
                    <i class="fa-solid fa-flask"></i>
                </div>
                <div>
                    <h1 class="font-display font-bold text-lg text-white leading-none">LabBio <span class="text-bio-400">Protistas</span></h1>
                    <span class="text-[11px] text-slate-400">Guía de Laboratorio Didáctica</span>
                </div>
            </div>

            <div class="flex items-center gap-2 bg-slate-800 px-4 py-1.5 rounded-full border border-slate-700">
                <i class="fa-solid fa-trophy text-amber-400"></i>
                <span class="text-xs font-bold">Puntos Bio: <span id="user-score" class="text-bio-400 font-mono text-sm">0</span></span>
            </div>
        </div>
    </header>

    <main class="max-w-6xl mx-auto px-4 pt-6 space-y-10">

        <section class="bg-slate-800 p-4 sm:p-6 rounded-3xl border-2 border-slate-700 shadow-lg flex flex-col sm:flex-row gap-4 items-center justify-between">
            <div class="flex items-center gap-3 w-full sm:w-auto">
                <i class="fa-solid fa-id-card text-bio-400 text-2xl"></i>
                <div class="w-full">
                    <label class="block text-[10px] font-bold uppercase text-slate-400">Nombre del Alumno / Equipo</label>
                    <input type="text" id="student-name" placeholder="Escribe tu nombre..." class="bg-slate-950 text-white text-sm px-3 py-1.5 rounded-xl border border-slate-700 focus:outline-none focus:border-bio-400 w-full sm:w-64">
                </div>
            </div>
            <div class="flex flex-wrap gap-2 w-full sm:w-auto justify-end">
                <button onclick="copySummary()" class="retro-btn bg-amber-400 text-slate-950 font-display font-bold text-xs px-3 py-2 rounded-xl flex items-center gap-1.5">
                    <i class="fa-solid fa-copy"></i> Copiar Resumen
                </button>
                <button onclick="downloadJsonReport()" class="retro-btn bg-sky-400 text-slate-950 font-display font-bold text-xs px-3 py-2 rounded-xl flex items-center gap-1.5">
                    <i class="fa-solid fa-download"></i> Guardar Archivo
                </button>
                <button onclick="window.print()" class="retro-btn bg-bio-500 text-slate-950 font-display font-bold text-xs px-4 py-2 rounded-xl flex items-center gap-1.5">
                    <i class="fa-solid fa-print"></i> PDF / Imprimir
                </button>
            </div>
        </section>

        <section class="bg-slate-950 p-6 rounded-3xl border-2 border-slate-800 shadow-2xl space-y-6">
            <div class="flex flex-col sm:flex-row sm:items-center justify-between gap-2 border-b border-slate-800 pb-3">
                <div>
                    <span class="text-bio-400 font-bold text-xs uppercase tracking-wider">🔬 Experimento 1</span>
                    <h2 class="font-display font-bold text-xl text-white">Identificación Rápida por Locomoción y Organelas</h2>
                </div>
                <p class="text-xs text-slate-400">Selecciona el tipo de estructura celular para observar su mecanismo y responder.</p>
            </div>

            <div class="grid grid-cols-1 lg:grid-cols-12 gap-6 items-center">
                
                <!-- Simple Interactive Selector Box -->
                <div class="lg:col-span-6 flex flex-col space-y-4">
                    <div class="grid grid-cols-3 gap-3">
                        <button onclick="selectLocomotion('flagella')" id="btn-flagella" class="retro-btn bg-bio-600 text-slate-950 p-3 rounded-2xl flex flex-col items-center gap-1">
                            <span class="text-2xl">⚡</span>
                            <span class="font-display font-bold text-xs">Flagelo</span>
                        </button>
                        <button onclick="selectLocomotion('cilia')" id="btn-cilia" class="retro-btn bg-slate-900 text-white p-3 rounded-2xl flex flex-col items-center gap-1">
                            <span class="text-2xl">🪮</span>
                            <span class="font-display font-bold text-xs">Cilios</span>
                        </button>
                        <button onclick="selectLocomotion('pseudopod')" id="btn-pseudopod" class="retro-btn bg-slate-900 text-white p-3 rounded-2xl flex flex-col items-center gap-1">
                            <span class="text-2xl">🦠</span>
                            <span class="font-display font-bold text-xs">Seudópodo</span>
                        </button>
                    </div>

                    <div id="simple-display-card" class="bg-slate-900 p-5 rounded-2xl border border-slate-800 space-y-3">
                        <div class="flex items-center justify-between">
                            <h3 id="loco-title" class="font-display font-bold text-lg text-bio-400">Flagelo (Ejemplo: Euglena)</h3>
                            <span id="loco-badge" class="bg-bio-500/20 text-bio-400 font-bold text-[10px] px-2.5 py-1 rounded-lg">Movimiento látigo</span>
                        </div>
                        <p id="loco-desc" class="text-xs text-slate-300 leading-relaxed">
                            Proyección en forma de látigo que impulsa a la célula mediante giros helicoidales en medios acuáticos.
                        </p>
                    </div>
                </div>

                <!-- Simple Quiz Box -->
                <div class="lg:col-span-6 bg-slate-900 p-5 rounded-2xl border border-slate-800 space-y-4">
                    <h3 class="font-display font-bold text-base text-white border-b border-slate-800 pb-2 flex items-center justify-between">
                        <span>Pregunta de Verificación</span>
                        <span id="exp1-status" class="text-xs bg-amber-500 text-slate-950 font-bold px-2.5 py-0.5 rounded-md">1 Pregunta</span>
                    </h3>

                    <p id="exp1-question" class="text-sm text-slate-200">
                        ¿Qué protista utiliza cilios (pestañas microscópicas) para desplazarse rápidamente y capturar alimento?
                    </p>

                    <div id="exp1-options" class="grid grid-cols-1 gap-2 pt-1">
                        <!-- Options generated by JS -->
                    </div>

                    <div id="exp1-feedback" class="hidden p-3 rounded-xl text-xs font-bold"></div>
                </div>

            </div>
        </section>

        <section class="bg-slate-950 p-6 rounded-3xl border-2 border-slate-800 shadow-2xl space-y-4">
            <div class="flex flex-col sm:flex-row sm:items-center justify-between gap-2 border-b border-slate-800 pb-3">
                <div>
                    <span class="text-purple-400 font-bold text-xs uppercase tracking-wider">🌱 Experimento 2</span>
                    <h2 class="font-display font-bold text-xl text-white">Árbol Filogenético Eucariota (Cladograma)</h2>
                </div>
                <p class="text-xs text-slate-400">Haz clic en cada Supergrupo para explorar su parentesco evolutivo.</p>
            </div>

            <div class="grid grid-cols-1 md:grid-cols-5 gap-3">
                <button onclick="showCladeInfo('excavata')" class="retro-btn bg-slate-900 hover:bg-slate-800 border-sky-500 p-3 rounded-2xl text-left space-y-2">
                    <span class="text-[10px] font-bold text-sky-400 uppercase">Supergrupo 1</span>
                    <h3 class="font-display font-bold text-sm text-white">Excavata</h3>
                    <p class="text-[10px] text-slate-400">Flagelados con surco de alimentación. Ej: Euglenas.</p>
                </button>

                <button onclick="showCladeInfo('sar')" class="retro-btn bg-slate-900 hover:bg-slate-800 border-pink-500 p-3 rounded-2xl text-left space-y-2">
                    <span class="text-[10px] font-bold text-pink-400 uppercase">Supergrupo 2</span>
                    <h3 class="font-display font-bold text-sm text-white">SAR</h3>
                    <p class="text-[10px] text-slate-400">Stramenopila, Alveolata y Rhizaria. Ej: Paramecio.</p>
                </button>

                <button onclick="showCladeInfo('amoebozoa')" class="retro-btn bg-slate-900 hover:bg-slate-800 border-amber-500 p-3 rounded-2xl text-left space-y-2">
                    <span class="text-[10px] font-bold text-amber-400 uppercase">Supergrupo 3</span>
                    <h3 class="font-display font-bold text-sm text-white">Amoebozoa</h3>
                    <p class="text-[10px] text-slate-400">Seudópodos lobulados. Ej: Ameba proteus.</p>
                </button>

                <button onclick="showCladeInfo('archaeplastida')" class="retro-btn bg-slate-900 hover:bg-slate-800 border-emerald-500 p-3 rounded-2xl text-left space-y-2">
                    <span class="text-[10px] font-bold text-emerald-400 uppercase">Supergrupo 4</span>
                    <h3 class="font-display font-bold text-sm text-white">Archaeplastida</h3>
                    <p class="text-[10px] text-slate-400">Plástidos primarios. Ej: Algas verdes y rojas.</p>
                </button>

                <button onclick="showCladeInfo('opisthokonta')" class="retro-btn bg-slate-900 hover:bg-slate-800 border-purple-500 p-3 rounded-2xl text-left space-y-2">
                    <span class="text-[10px] font-bold text-purple-400 uppercase">Supergrupo 5</span>
                    <h3 class="font-display font-bold text-sm text-white">Opisthokonta</h3>
                    <p class="text-[10px] text-slate-400">Flagelo posterior. Ej: Coanoflagelados.</p>
                </button>
            </div>

            <div id="clade-detail-box" class="bg-slate-900 p-4 rounded-2xl border border-slate-800 flex items-center justify-between gap-4">
                <div class="space-y-1">
                    <h4 id="clade-title" class="font-display font-bold text-base text-bio-400">Selecciona un supergrupo arriba</h4>
                    <p id="clade-desc" class="text-xs text-slate-300">Aprende sobre la biodiversidad celular y las relaciones evolutivas del Reino Protista.</p>
                </div>
                <div id="clade-badge" class="hidden sm:block text-2xl bg-slate-950 p-3 rounded-xl border border-slate-800">
                    🧬
                </div>
            </div>
        </section>

        <section class="bg-slate-950 p-6 rounded-3xl border-2 border-slate-800 shadow-2xl space-y-6">
            <div class="flex flex-col sm:flex-row sm:items-center justify-between gap-2 border-b border-slate-800 pb-3">
                <div>
                    <span class="text-amber-400 font-bold text-xs uppercase tracking-wider">📸 Experimento 3</span>
                    <h2 class="font-display font-bold text-xl text-white">Muestrario de Muestras del Alumno</h2>
                </div>
                <span id="sample-count" class="text-xs font-bold text-bio-400">0 Muestras registradas</span>
            </div>

            <div class="grid grid-cols-1 lg:grid-cols-12 gap-6">
                <form onsubmit="addSample(event)" class="lg:col-span-5 bg-slate-900 p-5 rounded-2xl border border-slate-800 space-y-3">
                    <h3 class="font-bold text-sm text-white border-b border-slate-800 pb-2">Añadir Muestra al Informe</h3>

                    <div>
                        <label class="block text-[11px] font-bold text-slate-300 mb-1">Nombre / Organismo *</label>
                        <input type="text" id="sample-name" required placeholder="Ej: Paramecio / Alga verde" class="w-full px-3 py-2 bg-slate-950 rounded-xl border border-slate-700 text-xs text-white focus:outline-none focus:border-bio-400">
                    </div>

                    <div>
                        <label class="block text-[11px] font-bold text-slate-300 mb-1">Aumento de Lente *</label>
                        <select id="sample-zoom" required class="w-full px-3 py-2 bg-slate-950 rounded-xl border border-slate-700 text-xs text-white focus:outline-none focus:border-bio-400">
                            <option value="100x">100x (Panorama)</option>
                            <option value="400x">400x (Detalle medio)</option>
                            <option value="1000x">1000x (Inmersión en aceite)</option>
                        </select>
                    </div>

                    <div>
                        <label class="block text-[11px] font-bold text-slate-300 mb-1">Foto o Dibujo de la Muestra *</label>
                        <input type="file" id="sample-file" accept="image/*" onchange="loadSampleImage(event)" class="text-xs text-slate-400 w-full file:mr-2 file:py-1 file:px-3 file:rounded-xl file:border-0 file:bg-bio-500 file:text-slate-950 file:font-bold">
                    </div>

                    <button type="submit" class="w-full py-2.5 bg-bio-500 text-slate-950 font-display font-bold text-xs rounded-xl shadow-md hover:bg-bio-400 transition-all">
                        <i class="fa-solid fa-plus"></i> Guardar Muestra en el Registro
                    </button>
                </form>

                <div id="samples-container" class="lg:col-span-7 grid grid-cols-1 sm:grid-cols-2 gap-4">
                    <div class="col-span-full py-10 text-center bg-slate-900 rounded-2xl border border-slate-800">
                        <i class="fa-solid fa-camera text-3xl text-slate-700 mb-2"></i>
                        <p class="text-xs text-slate-400">Aún no has subido fotos. Toma capturas con tu teléfono o adjúntalas aquí.</p>
                    </div>
                </div>
            </div>
        </section>

    </main>

    <script>
        // State management
        let score = 0;
        let samplesList = [];
        let currentImageBase64 = '';
        let currentLocoKey = 'flagella';

        // Simplified Experiment 1 Data
        const locoData = {
            flagella: {
                title: "Flagelo (Ejemplo: Euglena / Trypanosoma)",
                badge: "Movimiento en Látigo",
                desc: "Filamento largo que rota o ondea para impulsar a la célula a través del agua.",
                question: "¿Cuál de estos protistas se desplaza mediante un flagelo largo?",
                options: [
                    { text: "Euglena", correct: true },
                    { text: "Ameba proteus", correct: false },
                    { text: "Paramecio", correct: false }
                ]
            },
            cilia: {
                title: "Cilios (Ejemplo: Paramecio)",
                badge: "Movimiento Sincronizado",
                desc: "Cientos de pestañas cortas que baten en conjunto como remos para nadar velozmente.",
                question: "¿Qué estructura usan los Paramecios para remar de forma coordinada?",
                options: [
                    { text: "Cilios microscópicos", correct: true },
                    { text: "Seudópodos de gel", correct: false },
                    { text: "Pared Celular dura", correct: false }
                ]
            },
            pseudopod: {
                title: "Seudópodos (Ejemplo: Ameba)",
                badge: "Pies Falsos / Fagocitosis",
                desc: "Extensiones del citoplasma que fluyen para arrastrarse y envolver presas.",
                question: "¿Cómo se llama la extensión de citoplasma que permite a las amebas moverse y comer?",
                options: [
                    { text: "Seudópodo (Pie falso)", correct: true },
                    { text: "Cloroplasto", correct: false },
                    { text: "Espora", correct: false }
                ]
            }
        };

        function selectLocomotion(key) {
            currentLocoKey = key;
            ['flagella', 'cilia', 'pseudopod'].forEach(k => {
                const btn = document.getElementById(`btn-${k}`);
                if (k === key) {
                    btn.className = 'retro-btn bg-bio-500 text-slate-950 p-3 rounded-2xl flex flex-col items-center gap-1';
                } else {
                    btn.className = 'retro-btn bg-slate-900 text-white p-3 rounded-2xl flex flex-col items-center gap-1';
                }
            });

            const data = locoData[key];
            document.getElementById('loco-title').textContent = data.title;
            document.getElementById('loco-badge').textContent = data.badge;
            document.getElementById('loco-desc').textContent = data.desc;
            document.getElementById('exp1-question').textContent = data.question;

            const optionsBox = document.getElementById('exp1-options');
            optionsBox.innerHTML = '';
            data.options.forEach(opt => {
                const btn = document.createElement('button');
                btn.className = 'retro-btn bg-slate-800 hover:bg-bio-500 hover:text-slate-950 text-white p-2.5 rounded-xl text-xs font-bold text-left transition-all';
                btn.textContent = opt.text;
                btn.onclick = () => answerExp1(opt.correct);
                optionsBox.appendChild(btn);
            });

            document.getElementById('exp1-feedback').className = 'hidden';
        }

        function answerExp1(isCorrect) {
            const fb = document.getElementById('exp1-feedback');
            fb.classList.remove('hidden', 'bg-bio-500/20', 'bg-red-500/20', 'text-bio-400', 'text-red-400');

            if (isCorrect) {
                score += 25;
                document.getElementById('user-score').textContent = score;
                fb.classList.add('bg-bio-500/20', 'text-bio-400');
                fb.textContent = '🎉 ¡Correcto! Identificaste la estructura de locomoción (+25 Pts).';
                document.getElementById('exp1-status').textContent = 'Completado';
                document.getElementById('exp1-status').className = 'text-xs bg-bio-500 text-slate-950 font-bold px-2.5 py-0.5 rounded-md';
            } else {
                fb.classList.add('bg-red-500/20', 'text-red-400');
                fb.textContent = '❌ Respuesta incorrecta. Prueba seleccionando otra opción.';
            }
        }

        // Cladogram info database
        const clades = {
            excavata: {
                title: "Supergrupo Excavata",
                desc: "Incluye organismos unicelulares con surcos de alimentación ventrales característicos. Muchos tienen flagelos modificados y mitocondrias atípicas (ej. Euglenozoos).",
                badge: "🏊‍♂️"
            },
            sar: {
                title: "Supergrupo SAR (Stramenopila, Alveolata, Rhizaria)",
                desc: "Un clado gigantesco y diverso. Incluye algas doradas/pardas, diatomeas de pared de sílice, dinoflagelados causantes de marea roja y ciliados como el Paramecio.",
                badge: "🌾"
            },
            amoebozoa: {
                title: "Clado Amoebozoa",
                desc: "Protistas ameboides que se desplazan emitiendo seudópodos lobulados o con forma de dedos. Incluye amebas de vida libre y mohos mucilaginosos.",
                badge: "🦠"
            },
            archaeplastida: {
                title: "Supergrupo Archaeplastida",
                desc: "Surgieron por endosimbiosis primaria con una cianobacteria. Comprende algas rojas (Rhodophyta), algas verdes (Chlorophyta) y el Reino Vegetal.",
                badge: "🍃"
            },
            opisthokonta: {
                title: "Supergrupo Opisthokonta",
                desc: "Organismos caracterizados por poseer células con un único flagelo posterior. Este grupo emparenta a los protistas Coanoflagelados con los Hongos y Animales.",
                badge: "🍄"
            }
        };

        function showCladeInfo(key) {
            const clade = clades[key];
            if (clade) {
                document.getElementById('clade-title').textContent = clade.title;
                document.getElementById('clade-desc').textContent = clade.desc;
                const badge = document.getElementById('clade-badge');
                badge.textContent = clade.badge;
                badge.classList.remove('hidden');
            }
        }

        // Image loading and samples
        function loadSampleImage(e) {
            const file = e.target.files[0];
            if (file) {
                const reader = new FileReader();
                reader.onload = function(evt) {
                    currentImageBase64 = evt.target.result;
                };
                reader.readAsDataURL(file);
            }
        }

        function addSample(e) {
            e.preventDefault();
            const name = document.getElementById('sample-name').value;
            const zoom = document.getElementById('sample-zoom').value;

            if (!currentImageBase64) {
                alert("Por favor selecciona un archivo de imagen.");
                return;
            }

            samplesList.push({ name, zoom, img: currentImageBase64 });
            renderSamples();

            document.getElementById('sample-name').value = '';
            currentImageBase64 = '';
        }

        function renderSamples() {
            const container = document.getElementById('samples-container');
            document.getElementById('sample-count').textContent = `${samplesList.length} Muestras registradas`;

            if (samplesList.length === 0) return;

            container.innerHTML = '';
            samplesList.forEach((s, idx) => {
                const card = document.createElement('div');
                card.className = 'retro-card rounded-2xl overflow-hidden p-3 text-slate-900 space-y-2';
                card.innerHTML = `
                    <img src="${s.img}" class="w-full h-32 object-cover rounded-xl border border-slate-300">
                    <div class="flex items-center justify-between font-bold text-xs">
                        <span>#${idx + 1} ${s.name}</span>
                        <span class="bg-bio-500 text-slate-950 px-2 py-0.5 rounded-md text-[10px]">${s.zoom}</span>
                    </div>
                `;
                container.appendChild(card);
            });
        }

        function copySummary() {
            const studentName = document.getElementById('student-name').value || 'Alumno no especificado';
            let summary = `🧬 INFORME DE LABORATORIO: REINO PROTISTA\n`;
            summary += `👤 Alumno/Equipo: ${studentName}\n`;
            summary += `⭐ Puntaje Obtenido: ${score} pts\n`;
            summary += `🔬 Muestras Registradas: ${samplesList.length}\n`;
            if (samplesList.length > 0) {
                summary += `📋 Detalle de Muestras:\n`;
                samplesList.forEach((s, idx) => {
                    summary += `  ${idx + 1}. ${s.name} (Aumento: ${s.zoom})\n`;
                });
            }

            const dummy = document.createElement("textarea");
            document.body.appendChild(dummy);
            dummy.value = summary;
            dummy.select();
            document.execCommand("copy");
            document.body.removeChild(dummy);

            alert("¡Resumen de laboratorio copiado al portapapeles con éxito!");
        }

        function downloadJsonReport() {
            const studentName = document.getElementById('student-name').value || 'Alumno';
            const data = {
                alumno: studentName,
                puntaje: score,
                fecha: new Date().toLocaleDateString(),
                muestras: samplesList
            };

            const dataStr = "data:text/json;charset=utf-8," + encodeURIComponent(JSON.stringify(data, null, 2));
            const downloadAnchor = document.createElement('a');
            downloadAnchor.setAttribute("href", dataStr);
            downloadAnchor.setAttribute("download", `Informe_Protistas_${studentName.replace(/\s+/g, '_')}.json`);
            document.body.appendChild(downloadAnchor);
            downloadAnchor.click();
            downloadAnchor.remove();
        }

        window.onload = () => {
            selectLocomotion('flagella');
        };
    </script>
</body>
</html>
