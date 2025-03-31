<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Cadastro de Divergências em Notas Fiscais</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f9;
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: flex-start;
            min-height: 100vh;
            overflow-y: auto;
        }
        .form-container {
            background: white;
            padding: 30px;
            border-radius: 8px;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
            width: 100%;
            max-width: 800px;
            box-sizing: border-box;
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
            display: block;
            font-size: 14px;
            margin-bottom: 8px;
            font-weight: bold;
        }
        input, select {
            width: 100%;
            padding: 10px;
            font-size: 14px;
            border: 1px solid #ddd;
            border-radius: 5px;
        }
        input[type="date"] {
            cursor: pointer;
        }
        select {
            cursor: pointer;
        }
        .note {
            font-size: 12px;
            color: #777;
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
        #outrosTransportadora {
            display: none;
        }
    </style>
</head>
<body>
    <div class="form-container">
        <h2>Divergências em Notas Fiscais</h2>
        <form action="https://formspree.io/f/{your_form_id}" method="POST">
            
            <!-- Campo Filial -->
            <div class="form-group">
                <label for="filial">Filial</label>
                <select id="filial" name="filial" required>
                    <option value="">Selecione uma Filial</option>
                    <option value="ARTUR">ARTUR</option>
                    <option value="FLORIANO">FLORIANO</option>
                    <option value="JOTA">JOTA</option>
                    <option value="MODA">MODA</option>
                    <option value="PONTO">PONTO</option>
                </select>
            </div>

            <!-- Campo Transportadora -->
            <div class="form-group">
                <label for="transportadora">Transportadora</label>
                <select id="transportadora" name="transportadora" required>
                    <option value="BRASPRESS">BRASPRESS</option>
                    <option value="OUTROS">OUTROS</option>
                </select>
            </div>

            <!-- Campo para escrever Transportadora se "OUTROS" for selecionado -->
            <div class="form-group" id="outrosTransportadora">
                <label for="outraTransportadora">Qual é a Transportadora?</label>
                <input type="text" id="outraTransportadora" name="outraTransportadora">
            </div>

            <!-- Campo Data de Recebimento -->
            <div class="form-group">
                <label for="dataRecebimento">Data de Recebimento</label>
                <input type="date" id="dataRecebimento" name="dataRecebimento" required>
            </div>

            <!-- Campo Nota Fiscal -->
            <div class="form-group">
                <label for="notaFiscal">Número da Nota Fiscal</label>
                <input type="text" id="notaFiscal" name="notaFiscal" required>
                <small class="note">Não é necessário incluir os 0 à esquerda do número da NF.</small>
            </div>

            <!-- Campo Série da Nota Fiscal -->
            <div class="form-group">
                <label for="serieNota">Série da Nota Fiscal</label>
                <input type="text" id="serieNota" name="serieNota" required>
            </div>

            <!-- Campo Referência -->
            <div class="form-group">
                <label for="referencia">Referência</label>
                <input type="text" id="referencia" name="referencia" maxlength="4" required>
            </div>

            <!-- Campo Cor -->
            <div class="form-group">
                <label for="cor">Cor</label>
                <input type="text" id="cor" name="cor" required>
            </div>

            <!-- Campo Tamanho -->
            <div class="form-group">
                <label for="tamanho">Tamanho</label>
                <input type="text" id="tamanho" name="tamanho" required>
            </div>

            <!-- Campo Quantidade -->
            <div class="form-group">
                <label for="quantidade">Quantidade</label>
                <input type="number" id="quantidade" name="quantidade" required>
            </div>

            <!-- Campo Divergência -->
            <div class="form-group">
                <label>Divergência</label>
                <select name="divergencia" required>
                    <option value="MERCADORIA PASSANDO">MERCADORIA PASSANDO</option>
                    <option value="MERCADORIA FALTANDO">MERCADORIA FALTANDO</option>
                </select>
            </div>

            <!-- Botão Enviar -->
            <div class="form-group">
                <button type="submit">Enviar</button>
            </div>
        </form>
    </div>

    <script>
        // Mostrar campo para a transportadora "OUTROS"
        document.getElementById('transportadora').addEventListener('change', function() {
            const outrosField = document.getElementById('outrosTransportadora');
            if (this.value === 'OUTROS') {
                outrosField.style.display = 'block';
            } else {
                outrosField.style.display = 'none';
            }
        });
    </script>
</body>
</html>
