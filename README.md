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
            background-color: #f8f9fa;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            padding: 20px;
        }

        .form-container {
            background: white;
            padding: 24px;
            border-radius: 8px;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
            width: 100%;
            max-width: 600px;
        }

        h2 {
            text-align: center;
            margin-bottom: 20px;
            font-size: 22px;
            color: #202124;
        }

        .form-group {
            margin-bottom: 16px;
        }

        label {
            font-size: 14px;
            font-weight: 600;
            display: block;
            margin-bottom: 5px;
            color: #5f6368;
        }

        input, select {
            width: 100%;
            padding: 12px;
            font-size: 14px;
            border: 1px solid #dadce0;
            border-radius: 4px;
            background-color: #fff;
        }

        .form-group button {
            background-color: #1a73e8;
            color: white;
            border: none;
            padding: 12px;
            border-radius: 4px;
            font-size: 16px;
            width: 100%;
            cursor: pointer;
            font-weight: 600;
        }

        .form-group button:hover {
            background-color: #1765c1;
        }

        .loading {
            background-color: #d1d1d1;
            cursor: not-allowed;
        }

        .loading-message {
            text-align: center;
            margin-top: 20px;
            font-size: 16px;
            color: #1a73e8;
            font-weight: 600;
        }
    </style>
    <script>
        let isSubmitting = false;

        function enviarFormulario(event) {
            event.preventDefault();

            // Impede o envio múltiplo
            if (isSubmitting) {
                return;
            }

            isSubmitting = true;

            // Desabilitar o botão e mostrar que o envio está em andamento
            const button = event.target.querySelector("button[type='submit']");
            const loadingMessage = document.getElementById("loadingMessage");

            button.disabled = true;
            button.classList.add("loading");
            button.textContent = "Enviando...";

            loadingMessage.style.display = "block"; // Mostrar mensagem de envio

            var form = document.getElementById("formulario");
            var formData = new FormData(form);

            // Enviar os dados do formulário via fetch
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
            })
            .finally(() => {
                // Reabilitar o botão após 5 segundos ou após resposta
                setTimeout(() => {
                    button.disabled = false;
                    button.classList.remove("loading");
                    button.textContent = "Enviar";
                    isSubmitting = false;
                    loadingMessage.style.display = "none"; // Esconder mensagem após envio
                }, 1000);  // Ajuste o tempo conforme necessário
            });
        }
    </script>
</head>
<body>
    <div class="form-container" id="formContainer">
        <h2>Divergências em Notas Fiscais</h2>
        <form id="formulario" onsubmit="enviarFormulario(event)">
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

            <div class="form-group">
                <label>Transportadora</label>
                <select name="transportadora" id="transportadora" required>
                    <option value="BRASPRESS">BRASPRESS</option>
                    <option value="OUTROS">OUTROS</option>
                </select>
            </div>

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

        <!-- Mensagem de "Enviando..." -->
        <div id="loadingMessage" class="loading-message" style="display: none;">
            Enviando... Por favor, aguarde.
        </div>
    </div>
</body>
</html>
