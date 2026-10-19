<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Plataformas Educacionais - Dashboard</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        .gradient-bg {
            background: linear-gradient(135deg, #0f172a 0%, #1e1b4b 50%, #0f172a 100%);
        }
        .card-hover {
            transition: all 0.3s ease;
        }
        .card-hover:hover {
            transform: translateY(-4px);
            box-shadow: 0 12px 24px -10px rgba(99, 102, 241, 0.3);
        }
    </style>
</head>
<body class="gradient-bg text-slate-100 min-h-screen flex flex-col font-sans">

    <!-- Header -->
    <header class="border-b border-slate-800 bg-slate-900/50 backdrop-blur-md sticky top-0 z-50">
        <div class="max-w-6xl mx-auto px-4 py-4 flex flex-col sm:flex-row justify-between items-center gap-4">
            <div class="flex items-center space-x-3">
                <div class="p-2 bg-indigo-600 rounded-lg shadow-lg shadow-indigo-500/30">
                    <i class="fa-solid fa-wand-magic-sparkles text-xl text-white"></i>
                </div>
                <div>
                    <h1 class="text-xl font-bold bg-clip-text text-transparent bg-gradient-to-r from-indigo-400 to-purple-400">
                        Script Maestro Hub
                    </h1>
                    <p class="text-xs text-slate-400">Automação & Auxílio para Plataformas Educacionais</p>
                </div>
            </div>
            <div class="flex items-center gap-2 bg-slate-800/80 px-3 py-1.5 rounded-full border border-slate-700 text-xs">
                <span class="w-2 h-2 rounded-full bg-emerald-500 animate-pulse"></span>
                <span class="text-slate-300 font-medium">Modelo: Llama-3.3-70b (Groq)</span>
            </div>
        </div>
    </header>

    <!-- Main Content -->
    <main class="max-w-6xl mx-auto px-4 py-8 flex-1 w-full space-y-8">
        
        <!-- Configuração de API Key -->
        <section class="bg-slate-900/80 border border-slate-800 rounded-2xl p-6 shadow-xl backdrop-blur-sm">
            <div class="flex flex-col md:flex-row md:items-center justify-between gap-4">
                <div class="space-y-1">
                    <h2 class="text-lg font-semibold flex items-center gap-2 text-indigo-300">
                        <i class="fa-solid fa-key text-indigo-400"></i> Chave de API Groq (Opcional)
                    </h2>
                    <p class="text-sm text-slate-400">
                        O sistema usa uma chave padrão. Se ela atingir o limite, digite a sua chave própria abaixo para atualizar todos os scripts automaticamente.
                    </p>
                </div>
                <div class="flex items-center gap-2 w-full md:w-auto">
                    <div class="relative w-full md:w-80">
                        <input type="password" id="customApiKey" placeholder="gsk_..." 
                               class="w-full bg-slate-950 border border-slate-700 rounded-xl px-4 py-2 text-sm text-slate-200 focus:outline-none focus:border-indigo-500 transition-colors pr-10">
                        <button onclick="toggleKeyVisibility()" class="absolute right-3 top-1/2 -translate-y-1/2 text-slate-400 hover:text-slate-200">
                            <i class="fa-solid fa-eye text-xs" id="eyeIcon"></i>
                        </button>
                    </div>
                    <button onclick="saveApiKey()" class="bg-indigo-600 hover:bg-indigo-500 text-white px-4 py-2 rounded-xl text-sm font-medium transition-all shadow-lg shadow-indigo-600/20 shrink-0">
                        Salvar Key
                    </button>
                    <button onclick="clearApiKey()" title="Restaurar chave padrão" class="bg-slate-800 hover:bg-slate-700 text-slate-300 px-3 py-2 rounded-xl text-sm transition-all border border-slate-700 shrink-0">
                        <i class="fa-solid fa-rotate-left"></i>
                    </button>
                </div>
            </div>
            <div id="apiStatus" class="mt-3 text-xs hidden"></div>
        </section>

        <!-- Instruções -->
        <section class="bg-indigo-950/30 border border-indigo-900/50 rounded-2xl p-6">
            <h3 class="text-sm font-semibold text-indigo-300 uppercase tracking-wider mb-3 flex items-center gap-2">
                <i class="fa-solid fa-circle-info"></i> Como usar os Bookmarklets
            </h3>
            <ol class="grid grid-cols-1 md:grid-cols-3 gap-4 text-xs text-slate-300">
                <li class="flex items-start gap-2 bg-slate-900/50 p-3 rounded-lg border border-slate-800">
                    <span class="bg-indigo-500/20 text-indigo-400 rounded-full w-5 h-5 flex items-center justify-center shrink-0 font-bold">1</span>
                    <span>Arraste o botão do script desejado para a sua <strong>Barra de Favoritos</strong> do navegador.</span>
                </li>
                <li class="flex items-start gap-2 bg-slate-900/50 p-3 rounded-lg border border-slate-800">
                    <span class="bg-indigo-500/20 text-indigo-400 rounded-full w-5 h-5 flex items-center justify-center shrink-0 font-bold">2</span>
                    <span>Abra a atividade na plataforma educacional correspondente.</span>
                </li>
                <li class="flex items-start gap-2 bg-slate-900/50 p-3 rounded-lg border border-slate-800">
                    <span class="bg-indigo-500/20 text-indigo-400 rounded-full w-5 h-5 flex items-center justify-center shrink-0 font-bold">3</span>
                    <span>Clique no favorito salvo para executar a automação instantaneamente.</span>
                </li>
            </ol>
        </section>

        <!-- Grid de Plataformas -->
        <section class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">

            <!-- Quizizz -->
            <div class="bg-slate-900/80 border border-slate-800 rounded-2xl p-6 card-hover flex flex-col justify-between">
                <div>
                    <div class="flex items-center justify-between mb-4">
                        <div class="p-3 bg-purple-500/10 text-purple-400 rounded-xl border border-purple-500/20">
                            <i class="fa-solid fa-gamepad text-2xl"></i>
                        </div>
                        <span class="text-xs bg-purple-500/10 text-purple-300 border border-purple-500/20 px-2 py-1 rounded-full font-medium">V2 Maestro</span>
                    </div>
                    <h3 class="text-lg font-bold text-slate-100 mb-1">Quizizz Solver</h3>
                    <p class="text-xs text-slate-400 mb-4">Desbloqueia a interface, desativa restrições de tela e resolve questões via IA Groq em tempo real.</p>
                </div>
                <div class="space-y-2">
                    <a id="link-quizizz" href="#" class="block w-full py-2.5 px-4 bg-purple-600 hover:bg-purple-500 text-white text-center font-semibold text-sm rounded-xl transition-all shadow-lg shadow-purple-600/20 cursor-grab active:cursor-grabbing">
                        <i class="fa-solid fa-bookmark mr-2"></i> Arraste para os Favoritos
                    </a>
                    <button onclick="copyToClipboard('link-quizizz')" class="w-full py-2 text-xs text-slate-400 hover:text-slate-200 transition-colors">
                        <i class="fa-solid fa-copy mr-1"></i> Copiar Código
                    </button>
                </div>
            </div>

            <!-- Khan Academy -->
            <div class="bg-slate-900/80 border border-slate-800 rounded-2xl p-6 card-hover flex flex-col justify-between">
                <div>
                    <div class="flex items-center justify-between mb-4">
                        <div class="p-3 bg-emerald-500/10 text-emerald-400 rounded-xl border border-emerald-500/20">
                            <i class="fa-solid fa-graduation-cap text-2xl"></i>
                        </div>
                        <span class="text-xs bg-emerald-500/10 text-emerald-300 border border-emerald-500/20 px-2 py-1 rounded-full font-medium">Auto Helper</span>
                    </div>
                    <h3 class="text-lg font-bold text-slate-100 mb-1">Khan Academy</h3>
                    <p class="text-xs text-slate-400 mb-4">Extrai enunciados e alternativas e utiliza a Groq para marcar a resposta certa.</p>
                </div>
                <div class="space-y-2">
                    <a id="link-khan" href="#" class="block w-full py-2.5 px-4 bg-emerald-600 hover:bg-emerald-500 text-white text-center font-semibold text-sm rounded-xl transition-all shadow-lg shadow-emerald-600/20 cursor-grab active:cursor-grabbing">
                        <i class="fa-solid fa-bookmark mr-2"></i> Arraste para os Favoritos
                    </a>
                    <button onclick="copyToClipboard('link-khan')" class="w-full py-2 text-xs text-slate-400 hover:text-slate-200 transition-colors">
                        <i class="fa-solid fa-copy mr-1"></i> Copiar Código
                    </button>
                </div>
            </div>

            <!-- Inglês High -->
            <div class="bg-slate-900/80 border border-slate-800 rounded-2xl p-6 card-hover flex flex-col justify-between">
                <div>
                    <div class="flex items-center justify-between mb-4">
                        <div class="p-3 bg-blue-500/10 text-blue-400 rounded-xl border border-blue-500/20">
                            <i class="fa-solid fa-language text-2xl"></i>
                        </div>
                        <span class="text-xs bg-blue-500/10 text-blue-300 border border-blue-500/20 px-2 py-1 rounded-full font-medium">Assistente</span>
                    </div>
                    <h3 class="text-lg font-bold text-slate-100 mb-1">Inglês High</h3>
                    <p class="text-xs text-slate-400 mb-4">Identifica atividades de gramática, frases e vocabulário destacando as respostas corretas.</p>
                </div>
                <div class="space-y-2">
                    <a id="link-ingles" href="#" class="block w-full py-2.5 px-4 bg-blue-600 hover:bg-blue-500 text-white text-center font-semibold text-sm rounded-xl transition-all shadow-lg shadow-blue-600/20 cursor-grab active:cursor-grabbing">
                        <i class="fa-solid fa-bookmark mr-2"></i> Arraste para os Favoritos
                    </a>
                    <button onclick="copyToClipboard('link-ingles')" class="w-full py-2 text-xs text-slate-400 hover:text-slate-200 transition-colors">
                        <i class="fa-solid fa-copy mr-1"></i> Copiar Código
                    </button>
                </div>
            </div>

            <!-- Leia Paraná -->
            <div class="bg-slate-900/80 border border-slate-800 rounded-2xl p-6 card-hover flex flex-col justify-between">
                <div>
                    <div class="flex items-center justify-between mb-4">
                        <div class="p-3 bg-amber-500/10 text-amber-400 rounded-xl border border-amber-500/20">
                            <i class="fa-solid fa-book-open text-2xl"></i>
                        </div>
                        <span class="text-xs bg-amber-500/10 text-amber-300 border border-amber-500/20 px-2 py-1 rounded-full font-medium">Leitura & Quiz</span>
                    </div>
                    <h3 class="text-lg font-bold text-slate-100 mb-1">Leia Paraná</h3>
                    <p class="text-xs text-slate-400 mb-4">Responde os questionários das leituras com base no contexto do livro e da questão.</p>
                </div>
                <div class="space-y-2">
                    <a id="link-leia" href="#" class="block w-full py-2.5 px-4 bg-amber-600 hover:bg-amber-500 text-white text-center font-semibold text-sm rounded-xl transition-all shadow-lg shadow-amber-600/20 cursor-grab active:cursor-grabbing">
                        <i class="fa-solid fa-bookmark mr-2"></i> Arraste para os Favoritos
                    </a>
                    <button onclick="copyToClipboard('link-leia')" class="w-full py-2 text-xs text-slate-400 hover:text-slate-200 transition-colors">
                        <i class="fa-solid fa-copy mr-1"></i> Copiar Código
                    </button>
                </div>
            </div>

            <!-- Google Classroom -->
            <div class="bg-slate-900/80 border border-slate-800 rounded-2xl p-6 card-hover flex flex-col justify-between">
                <div>
                    <div class="flex items-center justify-between mb-4">
                        <div class="p-3 bg-rose-500/10 text-rose-400 rounded-xl border border-rose-500/20">
                            <i class="fa-solid fa-chalkboard-user text-2xl"></i>
                        </div>
                        <span class="text-xs bg-rose-500/10 text-rose-300 border border-rose-500/20 px-2 py-1 rounded-full font-medium">Classroom Helper</span>
                    </div>
                    <h3 class="text-lg font-bold text-slate-100 mb-1">Google Classroom</h3>
                    <p class="text-xs text-slate-400 mb-4">Ajuda na resolução de formulários e tarefas integradas ao Classroom.</p>
                </div>
                <div class="space-y-2">
                    <a id="link-classroom" href="#" class="block w-full py-2.5 px-4 bg-rose-600 hover:bg-rose-500 text-white text-center font-semibold text-sm rounded-xl transition-all shadow-lg shadow-rose-600/20 cursor-grab active:cursor-grabbing">
                        <i class="fa-solid fa-bookmark mr-2"></i> Arraste para os Favoritos
                    </a>
                    <button onclick="copyToClipboard('link-classroom')" class="w-full py-2 text-xs text-slate-400 hover:text-slate-200 transition-colors">
                        <i class="fa-solid fa-copy mr-1"></i> Copiar Código
                    </button>
                </div>
            </div>

        </section>
    </main>

    <!-- Footer -->
    <footer class="border-t border-slate-800 py-6 text-center text-xs text-slate-500">
        <p>Desenvolvido para fins educacionais &bull; Powered by Groq AI</p>
    </footer>

    <!-- Lógica JavaScript & Construtor de Bookmarklets -->
    <script>
        function getDefaultApiKey() {
            try {
                return atob("Z3NrX2ptTzhKeHc4TDQyN3AweXZyUkd3V0dkeWIzeGFyNmFiUXA="); 
            } catch(e) {
                return "";
            }
        }

        function getActiveApiKey() {
            const savedKey = localStorage.getItem("groq_custom_api_key");
            if (savedKey && savedKey.trim() !== "") {
                return savedKey.trim();
            }
            return getDefaultApiKey();
        }

        function saveApiKey() {
            const input = document.getElementById("customApiKey");
            const key = input.value.trim();
            if (key) {
                localStorage.setItem("groq_custom_api_key", key);
                showStatus("Chave salva com sucesso e aplicada aos bookmarklets!", "success");
            } else {
                localStorage.removeItem("groq_custom_api_key");
                showStatus("Chave removida. Utilizando chave padrão.", "info");
            }
            buildBookmarklets();
        }

        function clearApiKey() {
            localStorage.removeItem("groq_custom_api_key");
            document.getElementById("customApiKey").value = "";
            showStatus("Voltou para a chave padrão.", "info");
            buildBookmarklets();
        }

        function toggleKeyVisibility() {
            const input = document.getElementById("customApiKey");
            const icon = document.getElementById("eyeIcon");
            if (input.type === "password") {
                input.type = "text";
                icon.classList.remove("fa-eye");
                icon.classList.add("fa-eye-slash");
            } else {
                input.type = "password";
                icon.classList.remove("fa-eye-slash");
                icon.classList.add("fa-eye");
            }
        }

        function showStatus(msg, type) {
            const status = document.getElementById("apiStatus");
            status.textContent = msg;
            status.classList.remove("hidden", "text-emerald-400", "text-amber-400");
            if (type === "success") status.classList.add("text-emerald-400");
            else status.classList.add("text-amber-400");
            setTimeout(() => status.classList.add("hidden"), 4000);
        }

        // Função geradora de scripts para Bookmarklet
        function buildBookmarklets() {
            const apiKey = getActiveApiKey();

            // SCRIPT MAESTRO QUIZIZZ V2
            const quizizzCode = `javascript:(function(){
                console.log("Iniciando Script Maestro V2 no Quizizz...");
                try {
                    document.oncontextmenu = null;
                    document.onselectstart = null;
                    document.ondragstart = null;
                    document.onkeydown = null;
                    if (window.jQuery) {
                        jQuery(document).unbind();
                        jQuery(window).unbind();
                    }
                    const overlayEls = document.querySelectorAll('.blocker, .modal-backdrop, [class*="overlay"]');
                    overlayEls.forEach(el => el.remove());
                    document.body.style.overflow = 'auto';
                    document.body.style.userSelect = 'auto';
                } catch(e) { console.error("Erro no desbloqueio:", e); }

                const apiKey = "${apiKey}";
                if(!apiKey){ alert("Nenhuma API Key da Groq foi configurada!"); return; }

                const questionEl = document.querySelector('[data-test-id="question-container"], .question-text, .query-text');
                const optionEls = document.querySelectorAll('[data-test-id*="option"], .option-text, .option');

                if(!questionEl || optionEls.length === 0){
                    alert("Não foi possível encontrar a pergunta/opções na página.");
                    return;
                }

                const questionText = questionEl.innerText.trim();
                let optionsText = [];
                optionEls.forEach((opt, idx) => {
                    optionsText.push((idx + 1) + ") " + opt.innerText.trim());
                });

                const prompt = "Pergunta: " + questionText + "\\nOpções:\\n" + optionsText.join("\\n") + "\\nResponda APENAS com o número e o texto exato da opção correta.";

                fetch("https://api.groq.com/openai/v1/chat/completions", {
                    method: "POST",
                    headers: {
                        "Authorization": "Bearer " + apiKey,
                        "Content-Type": "application/json"
                    },
                    body: JSON.stringify({
                        model: "llama-3.3-70b-versatile",
                        messages: [{ role: "user", content: prompt }]
                    })
                })
                .then(r => r.json())
                .then(data => {
                    const ans = data.choices[0].message.content;
                    alert("Resposta sugerida Groq:\\n\\n" + ans);
                })
                .catch(err => {
                    alert("Erro ao consultar a API da Groq: " + err.message);
                });
            })();`;

            // SCRIPT KHAN ACADEMY
            const khanCode = `javascript:(function(){
                const apiKey = "${apiKey}";
                if(!apiKey){ alert("Configure a API Key da Groq!"); return; }
                const q = document.querySelector('[data-test-id="problem-statement"]')?.innerText || document.body.innerText.substring(0, 500);
                alert("Analisando Khan Academy com Groq...");
                fetch("https://api.groq.com/openai/v1/chat/completions", {
                    method: "POST",
                    headers: { "Authorization": "Bearer " + apiKey, "Content-Type": "application/json" },
                    body: JSON.stringify({
                        model: "llama-3.3-70b-versatile",
                        messages: [{ role: "user", content: "Resolva de forma direta: " + q }]
                    })
                }).then(r=>r.json()).then(d=>alert("Resposta Groq:\\n"+d.choices[0].message.content)).catch(e=>alert(e.message));
            })();`;

            // SCRIPT INGLÊS HIGH
            const inglesCode = `javascript:(function(){
                const apiKey = "${apiKey}";
                if(!apiKey){ alert("Configure a API Key!"); return; }
                const text = document.body.innerText.substring(0, 1000);
                fetch("https://api.groq.com/openai/v1/chat/completions", {
                    method: "POST",
                    headers: { "Authorization": "Bearer " + apiKey, "Content-Type": "application/json" },
                    body: JSON.stringify({
                        model: "llama-3.3-70b-versatile",
                        messages: [{ role: "user", content: "Ajude na seguinte atividade de inglês fornecendo a resposta correta diretamente:\\n" + text }]
                    })
                }).then(r=>r.json()).then(d=>alert("Resposta Groq:\\n"+d.choices[0].message.content)).catch(e=>alert(e.message));
            })();`;

            // SCRIPT LEIA PARANÁ
            const leiaCode = `javascript:(function(){
                const apiKey = "${apiKey}";
                if(!apiKey){ alert("Configure a API Key!"); return; }
                const text = document.body.innerText.substring(0, 1000);
                fetch("https://api.groq.com/openai/v1/chat/completions", {
                    method: "POST",
                    headers: { "Authorization": "Bearer " + apiKey, "Content-Type": "application/json" },
                    body: JSON.stringify({
                        model: "llama-3.3-70b-versatile",
                        messages: [{ role: "user", content: "Responda à questão do livro:\\n" + text }]
                    })
                }).then(r=>r.json()).then(d=>alert("Resposta Groq:\\n"+d.choices[0].message.content)).catch(e=>alert(e.message));
            })();`;

            // SCRIPT CLASSROOM
            const classroomCode = `javascript:(function(){
                const apiKey = "${apiKey}";
                if(!apiKey){ alert("Configure a API Key!"); return; }
                const text = document.body.innerText.substring(0, 1000);
                fetch("https://api.groq.com/openai/v1/chat/completions", {
                    method: "POST",
                    headers: { "Authorization": "Bearer " + apiKey, "Content-Type": "application/json" },
                    body: JSON.stringify({
                        model: "llama-3.3-70b-versatile",
                        messages: [{ role: "user", content: "Forneça a resposta para esta tarefa:\\n" + text }]
                    })
                }).then(r=>r.json()).then(d=>alert("Resposta Groq:\\n"+d.choices[0].message.content)).catch(e=>alert(e.message));
            })();`;

            // Atualiza os elementos A no DOM
            document.getElementById("link-quizizz").href = quizizzCode;
            document.getElementById("link-khan").href = khanCode;
            document.getElementById("link-ingles").href = inglesCode;
            document.getElementById("link-leia").href = leiaCode;
            document.getElementById("link-classroom").href = classroomCode;
        }

        // Função de cópia corrigida sem decodeURIComponent para evitar erros de URI malformada
        function copyToClipboard(elementId) {
            const link = document.getElementById(elementId);
            if (!link || !link.href) return;
            navigator.clipboard.writeText(link.href).then(() => {
                alert("Código do Bookmarklet copiado para a área de transferência!");
            }).catch(err => {
                console.error("Erro ao copiar: ", err);
            });
        }

        // Inicialização na carga da página
        window.addEventListener("DOMContentLoaded", () => {
            const savedKey = localStorage.getItem("groq_custom_api_key");
            if (savedKey) {
                document.getElementById("customApiKey").value = savedKey;
            }
            buildBookmarklets();
        });
    </script>
</body>
</html>