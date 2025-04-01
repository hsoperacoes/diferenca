<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Cadastro de Divergências em Notas Fiscais</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f9;
            display: flex;
            justify-content: center;
            align-items: flex-start;
            min-height: 100vh;
            overflow-y: auto;
            padding: 20px;
        }

        .form-container {
            background: white;
            padding: 30px;
            border-radius: 8px;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
            width: 100%;
            max-width: 800px;  /* Largura aumentada */
            display: none;
        }

        h2 {
            text-align: center;
            margin-bottom: 20px;
            font-size: 24px;
            color: #4CAF50;
        }

        .form-group {
            margin-bottom: 20px;
        }

        label {
            font-size: 14px;
            font-weight: bold;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        input, select {
            width: 100%;
            padding: 10px;
            font-size: 14px;
            border: 1px solid #ddd;
            border-radius: 5px;
            margin-top: 5px;
        }

        .form-group button {
            background-color: #4CAF50;
            color: white;
            border: none;
            padding: 12px;
            border-radius: 5px;
            font-size: 16px;
            width: 100%;
            cursor: pointer;
        }

        .form-group button:hover {
            background-color: #45a049;
        }

        .login-container {
            background: white;
            padding: 30px;
            border-radius: 8px;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
            width: 100%;
            max-width: 500px;
            text-align: center;
        }

        .login-container input {
            margin-bottom: 15px;
        }
    </style>
</head>
<body>
    <!-- Tela de Login -->
    <div class="login-container" id="loginContainer">
        <h2>Login</h2>
        <form id="loginForm">
            <div class="form-group">
                <label for="username">Usuário</label>
                <input type="text" id="username" name="username" required>
            </div>
            <div class="form-group">
                <label for="password">Senha</label>
                <input type="password" id="password" name="password" required>
            </div>
            <div class="form-group">
                <button type="submit">Entrar</button>
            </div>
        </form>
    </div>

    <!-- Formulário de Cadastro de Divergências (escondido inicialmente) -->
    <div class="form-container" id="formContainer">
        <h2>Divergências em Notas Fiscais</h2>
        <form action="https://formspree.io/f/{your_form_id}" method="POST">
            <div class="form-group">
                <label>Filial</label>
                <select name="filial" required>
                    <option value="">Selecione uma filial</option>  <!-- Removi a preseleção -->
                    <option value="ARTUR">ARTUR</option>
                    <option value="FLORIANO">FLORIANO</option>
                    <option value="JOTA">JOTA</option>
                    <option value="MODA">MODA</option>
                    <option value="PONTO">PONTO</option>
                </select>
            </div>

            <div class="form-group">
                <label>Transportadora</label>
                <select name="transportadora" id="transportadora" required>
                    <option value="BRASPRESS">BRASPRESS</option>
                    <option value="OUTROS">OUTROS</option>
                </select>
            </div>

            <!-- Campo de texto para o nome da transportadora "OUTROS" -->
            <div class="form-group" id="outrosTransportadora" style="display: none;">
                <label for="outraTransportadora">Qual é a Transportadora?</label>
                <input type="text" id="outraTransportadora" name="outraTransportadora">
            </div>

            <div class="form-group">
                <label for="dataRecebimento">Data de Recebimento</label>
                <input type="date" id="dataRecebimento" name="dataRecebimento" required>
            </div>

            <div class="form-group">
                <label for="notaFiscal">Número da Nota Fiscal</label>
                <input type="text" id="notaFiscal" name="notaFiscal" required>
            </div>

            <div class="form-group">
                <label for="serieNota">Série da Nota Fiscal</label>
                <input type="text" id="serieNota" name="serieNota" required>
            </div>

            <div class="form-group">
                <label for="referencia">Referência</label>
                <input type="text" id="referencia" name="referencia" maxlength="4" required>
            </div>

            <div class="form-group">
                <label for="cor">Cor</label>
                <input type="text" id="cor" name="cor" maxlength="6" required>
            </div>

            <div class="form-group">
                <label for="tamanho">Tamanho</label>
                <input type="text" id="tamanho" name="tamanho" required>
            </div>

            <div class="form-group">
                <label for="quantidade">Quantidade</label>
                <input type="number" id="quantidade" name="quantidade" required>
            </div>

            <div class="form-group">
                <label>Divergência</label>
                <select name="divergencia" required>
                    <option value="">Selecione uma opção</option>
                    <option value="MERCADORIA PASSANDO">MERCADORIA PASSANDO</option>
                    <option value="MERCADORIA FALTANDO">MERCADORIA FALTANDO</option>
                </select>
            </div>

            <div class="form-group">
                <button type="submit">Enviar</button>
            </div>
        </form>
    </div>

    <script>
        // Exibir o campo de transportadora "OUTROS" quando selecionado
        document.getElementById('transportadora').addEventListener('change', function() {
            const outrosField = document.getElementById('outrosTransportadora');
            if (this.value === 'OUTROS') {
                outrosField.style.display = 'block';  // Exibe o campo
            } else {
                outrosField.style.display = 'none';  // Esconde o campo
            }
        });

        // Defina os usuários e senhas permitidos
        const users = [
            { username: 'admin', password: 'senha123' },
            { username: 'a', password: 'hering0277' },
            { username: 'f', password: 'hering0277' },
            { username: 'j', password: 'hering0277' },
            { username: 'm', password: 'hering0277' },
            { username: 'p', password: 'hering0277' }
        ];

        // Função para verificar o login
        function checkLogin() {
            if (localStorage.getItem('loggedIn') === 'true') {
                document.querySelector('.login-container').style.display = 'none';
                document.querySelector('.form-container').style.display = 'block';
            } else {
                document.querySelector('.login-container').style.display = 'block';
                document.querySelector('.form-container').style.display = 'none';
            }
        }

        // Validação do login
        document.getElementById('loginForm').addEventListener('submit', function(event) {
            event.preventDefault();

            const username = document.getElementById('username').value;
            const password = document.getElementById('password').value;

            // Verificar se as credenciais correspondem a algum usuário da lista
            const user = users.find(u => u.username === username && u.password === password);

            if (user) {
                // Login bem-sucedido
                localStorage.setItem('loggedIn', 'true');  // Salva no localStorage que o usuário está logado
                resetIdleTimer();  // Reinicia o timer de inatividade
                checkLogin();  // Atualiza a interface
            } else {
                alert('Usuário ou senha incorretos!');
            }
        });

        // Função para monitorar inatividade
        let idleTimeout;

        function resetIdleTimer() {
            // Limpar qualquer timeout anterior
            clearTimeout(idleTimeout);

            // Definir novo timeout de 10 minutos (600000ms)
            idleTimeout = setTimeout(() => {
                alert("Você foi deslogado por inatividade!");
                localStorage.setItem('loggedIn', 'false');
                checkLogin();
            }, 600000);  // 10 minutos
        }

        // Monitorar atividade do usuário (movimento do mouse, pressionamento de tecla, etc.)
        window.addEventListener('mousemove', resetIdleTimer);
        window.addEventListener('keydown', resetIdleTimer);
        window.addEventListener('click', resetIdleTimer);

        // Verifica o login no início
        checkLogin();
    </script>
</body>
</html>
