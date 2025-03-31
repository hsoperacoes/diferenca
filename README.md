<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Divergências em Notas Fiscais</title>
    <style>
        body {
            font-family: 'Roboto', sans-serif;
            background-color: #f7f7f7;
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
        }

        .form-container {
            background-color: white;
            border-radius: 8px;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
            width: 100%;
            max-width: 800px;
            padding: 30px;
            box-sizing: border-box;
        }

        .form-header {
            font-size: 24px;
            font-weight: 500;
            color: #333;
            margin-bottom: 30px;
            text-align: center;
        }

        .form-group {
            margin-bottom: 20px;
        }

        .form-group label {
            font-size: 14px;
            color: #333;
            margin-bottom: 10px;
            display: block;
        }

        .form-group input,
        .form-group select,
        .form-group textarea {
            width: 100%;
            padding: 12px;
            font-size: 14px;
            border: 1px solid #ddd;
            border-radius: 4px;
            margin-top: 5px;
            box-sizing: border-box;
            background-color: #f9f9f9;
        }

        .form-group input:focus,
        .form-group select:focus,
        .form-group textarea:focus {
            outline: none;
            border-color: #4CAF50;
        }

        .form-group input[type="submit"] {
            background-color: #4CAF50;
            color: white;
            border: none;
            font-size: 16px;
            padding: 12px;
            border-radius: 4px;
            cursor: pointer;
            width: 100%;
            margin-top: 10px;
            transition: background-color 0.3s;
        }

        .form-group input[type="submit"]:hover {
            background-color: #45a049;
        }

        .form-group input[type="date"] {
            background-color: #fff;
        }

        .form-group #outrosTransportadora {
            display: none;
        }

    </style>
</head>
<body>

    <div class="form-container">
        <h1 class="form-header">Divergências em Notas Fiscais</h1>

        <form>

            <!-- Filial -->
            <div class="form-group">
                <label>Filial</label>
                <select id="filial" name="filial" required>
                    <option value="">Selecione uma Filial</option>
                    <option value="ARTUR">ARTUR</option>
                    <option value="FLORIANO">FLORIANO</option>
                    <option value="JOTA">JOTA</option>
                    <option value="MODA">MODA</option>
                    <option value="PONTO">PONTO</option>
                </select>
            </div>

            <!-- Transportadora -->
            <div class="form-group">
                <label>Transportadora</label>
                <select id="transportadora" name="transportadora" required>
                    <option value="BRASPRESS">BRASPRESS</option>
                    <option value="OUTROS">OUTROS</option>
                </select>
            </div>

            <!-- Campo de Transportadora "Outros" -->
            <div class="form-group" id="outrosTransportadora">
                <label for="outraTransportadora">Qual é a Transportadora?</label>
                <input type="text" id="outraTransportadora" name="outraTransportadora">
            </div>

            <!-- Data de Recebimento -->
            <div class="form-group">
                <label for="dataRecebimento">Data de Recebimento</label>
                <input type="date" id="dataRecebimento" name="dataRecebimento" required>
            </div>

            <!-- Nota Fiscal -->
            <div class="form-group">
                <label for="notaFiscal">Nota Fiscal</label>
                <input type="text" id="notaFiscal" name="notaFiscal" required>
                <small>Não é necessário incluir os 0 à esquerda</small>
            </div>

            <!-- Série da Nota Fiscal -->
            <div class="form-group">
                <label for="serieNotaFiscal">Série da Nota Fiscal</label>
                <input type="text" id="serieNotaFiscal" name="serieNotaFiscal" required>
            </div>

            <!-- Referência (Limite de 4 caracteres) -->
            <div class="form-group">
                <label for="referencia">Referência (Máximo de 4 caracteres)</label>
                <input type="text" id="referencia" name="referencia" maxlength="4" required>
            </div>

            <!-- Cor -->
            <div class="form-group">
                <label for="cor">Cor</label>
                <input type="text" id="cor" name="cor" required>
            </div>

            <!-- Tamanho -->
            <div class="form-group">
                <label for="tamanho">Tamanho</label>
                <input type="text" id="tamanho" name="tamanho" required>
            </div>

            <!-- Quantidade -->
            <div class="form-group">
                <label for="quantidade">Quantidade</label>
                <input type="number" id="quantidade" name="quantidade" required>
            </div>

            <!-- Divergência -->
            <div class="form-group">
                <label>Divergência</label>
                <select name="divergencia" id="divergencia">
                    <option value="mercadoriaPassando">Mercadoria Passando</option>
                    <option value="mercadoriaFaltando">Mercadoria Faltando</option>
                </select>
            </div>

            <!-- Botão de Enviar -->
            <div class="form-group">
                <input type="submit" value="Enviar">
            </div>
        </form>
    </div>

    <script>
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
