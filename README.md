<!DOCTYPE html>
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
            max-width: 800px;
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
    </style>
</head>
<body>
    <div class="form-container">
        <h2>Divergências em Notas Fiscais</h2>
        <form id="divergenciaForm">
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
                <label for="dataRecebimento">Data de Recebimento</label>
                <input type="date" id="dataRecebimento" name="dataRecebimento" required>
            </div>

            <div class="form-group">
                <label for="notaFiscal">Número da Nota Fiscal</label>
                <input type="text" id="notaFiscal" name="notaFiscal" required>
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
        document.querySelector("#divergenciaForm").addEventListener("submit", function (event) {
            event.preventDefault();
            const form = event.target;
            const formData = new FormData(form);

            fetch("https://script.google.com/macros/s/YOUR_SCRIPT_ID/exec", {
                method: "POST",
                body: formData
            })
            .then(response => response.json())
            .then(data => {
                if (data.result === "success") {
                    alert("Dados enviados com sucesso!");
                    form.reset();
                } else {
                    alert("Erro ao enviar os dados.");
                }
            })
            .catch(error => {
                console.error("Erro:", error);
                alert("Erro na conexão com o servidor.");
            });
        });
    </script>
</body>
</html>
