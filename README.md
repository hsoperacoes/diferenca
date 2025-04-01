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
            position: relative;
        }

        .form-container {
            background: white;
            padding: 30px;
            border-radius: 8px;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
            width: 95%;
            max-width: 1200px;
            margin-bottom: 80px;
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

        /* Estilo do logo */
        .logo-hering {
            position: fixed;
            bottom: 20px;
            right: 20px;
            width: 180px;
            height: auto;
            z-index: 100;
        }

        @media (max-width: 768px) {
            .logo-hering {
                width: 120px;
            }
        }
    </style>
    <script>
        function enviarFormulario(event) {
            event.preventDefault();
            
            var form = document.getElementById("formulario");
            var formData = new FormData(form);
            
            fetch("https://script.google.com/macros/s/AKfycbw5xq6i5Qoc0s3f-ZaQ6FCZdsjXrC_my8d0tmgr756hWZQqT9Olu9DjsGOYwTlvnBQA/exec", {
                method: "POST",
                body: formData
            })
            .then(response => response.json())
            .then(data => {
                alert("SUA DIVERGÊNCIA FOI ENVIADA COM SUCESSO, AGRADECEMOS SEU APOIO");
                form.reset();
            })
            .catch(error => {
                alert("Erro ao enviar o formulário. Tente novamente.");
            });
        }

        // Mostrar campo de transportadora quando selecionar "OUTROS"
        document.addEventListener('DOMContentLoaded', function() {
            document.getElementById('transportadora').addEventListener('change', function() {
                const outrosField = document.getElementById('outrosTransportadora');
                outrosField.style.display = this.value === 'OUTROS' ? 'block' : 'none';
            });
        });
    </script>
</head>
<body>
    <div class="form-container" id="formContainer">
        <h2>Divergências em Notas Fiscais</h2>
        <form id="formulario" onsubmit="enviarFormulario(event)">
            <!-- Seus campos de formulário aqui -->
            <div class="form-group">
                <label>Filial</label>
                <select name="filial" required>
                    <option value="">Selecione uma filial</option>
                    <option value="ARTUR">ARTUR</option>
                    <option value="FLORIANO">FLORIANO</option>
                    <option value="JOTA">JOTA</option>
                    <option value="MODA">MODA</option>
                    <option value="PONTO">PONTO</option>
                </select>
            </div>

            <!-- Demais campos do formulário -->
            
            <div class="form-group">
                <button type="submit">Enviar</button>
            </div>
        </form>
    </div>

    <!-- Logo Hering funcional -->
    <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/7/7e/Hering_logo.svg/1200px-Hering_logo.svg.png" 
         alt="Logo Hering" 
         class="logo-hering">
</body>
</html>
