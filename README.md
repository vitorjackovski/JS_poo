# JS_poo

<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Lista de Tarefas</title>
    <link rel="stylesheet" href="./style.css">
</head>
<body>
    <header>
        <h1>Lista de Tarefas</h1>
        <nav>
            <!-- Links de navegação corrigidos com as âncoras -->
            <a href="#inicio">Inicio</a>
            <a href="#tarefas">Tarefas</a>
            <a href="#contato">Contato</a>
        </nav>
    </header>

    <div id="inicio" class="container">
        <h1>Adicionar nova Tarefa</h1>
        <div>
            <input type="text" id="tarefaInput" placeholder="Digite uma tarefa">
            <button onclick="adicionarTarefa()">Adicionar</button>
        </div>

        <ul id="listaTarefas"></ul>
    </div>

    <footer id="contato">
        <p>&copy; 2025 SENAI. Todos os direitos reservados.</p>
    </footer>

    <script>
        let tarefas = [];

        function adicionarTarefa() {
            const input = document.getElementById('tarefaInput');
            const tarefa = input.value.trim();
            if (tarefa) {
                tarefas.push(tarefa);
                input.value = '';
                atualizarLista();
            }
        }

        function removerTarefa(index) {
            tarefas.splice(index, 1);
            atualizarLista();
        }

        function atualizarLista() {
            const lista = document.getElementById('listaTarefas');
            lista.innerHTML = '';
            tarefas.forEach((tarefa, index) => {
                const li = document.createElement('li');
                li.innerHTML = `${tarefa} <button onclick="removerTarefa(${index})">Remover</button>`;
                lista.appendChild(li);
            });
        }
    </script>
</body>
</html>

# Style 

    body {
            font-family: Arial, sans-serif;
            text-align: center;
            margin: 0;
            padding: 0;
            background-color: #D7C9AF; /* Cor de fundo mais clara */
            color: #282119; /* Cor escura para o texto */
            line-height: 1.6;
            display: flex;
            flex-direction: column;
            min-height: 100vh; /* Garante que o corpo ocupe toda a altura da tela */
        }

        /* Cabeçalho */
        header {
            background-color: #65371F; /* Cor de fundo do header */
            padding: 20px 0;
        }

        header h1 {
            font-size: 2.5rem;
            color: #D7C9AF; /* Cor de texto clara no header */
            margin: 0;
        }

        nav {
            display: flex;
            justify-content: center;
            gap: 20px; /* Espaço entre os links */
            margin-top: 15px;
        }

        nav a {
            color: #C37338; /* Cor dos links */
            text-decoration: none;
            font-size: 1rem;
            transition: color 0.3s ease;
        }

        nav a:hover {
            color: #9F4D27; /* Cor ao passar o mouse nos links */
        }

        /* Container principal */
        .container {
            max-width: 600px;
            width: 100%;
            margin: 85px auto;
            padding: 40px;
            border-radius: 10px;
            background-color: #65371F; /* Cor de fundo do container */
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
            flex-grow: 1; /* Isso faz o container crescer e empurrar o footer para baixo */
        }

        .container h1 {
            color: #D7C9AF; /* Cor clara para o título */
            margin-bottom: 20px;
        }

        /* Estilo do input e botões */
        input[type="text"] {
            padding: 12px;
            width: calc(100% - 140px);
            font-size: 1rem;
            border: 1px solid #746049;
            border-radius: 5px;
            margin-right: 10px;
            margin-bottom: 20px;
            background-color: #D7C9AF;
        }

        button {
            padding: 12px;
            font-size: 1rem;
            cursor: pointer;
            background-color: #9F4D27; /* Cor de fundo do botão */
            color: #D7C9AF;
            border: none;
            border-radius: 5px;
            transition: background-color 0.3s ease;
        }

        button:hover {
            background-color: #C37338; /* Cor ao passar o mouse no botão */
        }

        /* Estilo da lista de tarefas */
        ul {
            list-style-type: none;
            padding: 0;
            margin-top: 20px;
        }

        li {
            padding: 12px;
            background-color: #D7C9AF; /* Cor de fundo das tarefas */
            margin-bottom: 10px;
            border-radius: 5px;
            color: #282119;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        li button {
            background-color: #9F4D27; /* Cor de fundo do botão dentro da tarefa */
            padding: 8px 12px;
            font-size: 0.9rem;
            border-radius: 5px;
            color: #D7C9AF; /* Cor das letras das tarefas */
            cursor: pointer;
            transition: background-color 0.3s ease;
        }

        li button:hover {
            background-color: #C37338; /* Cor ao passar o mouse no botão dentro da tarefa */
        }

        /* Estilo do rodapé */
        footer {
            background-color: #65371F;
            padding: 20px 0;
            text-align: center;
            color: #D7C9AF;
            font-size: 0.9rem;
        }
