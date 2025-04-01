<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Cadastro de Divergências em Notas Fiscais</title>
    <style>
        /* Estilos CSS mantidos */
    </style>
</head>
<body>
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

    <div class="form-container" id="formContainer">
        <h2>Divergências em Notas Fiscais</h2>
        <form id="divergenciaForm">
            <div class="form-group">
                <label>Filial</label>
                <select name="filial" required>
                    <option value="ARTUR">ARTUR</option>
                    <option value="FLORIANO">FLORIANO</option>
                    <option value="JOTA">JOTA</option>
                    <option value="MODA">MODA</option>
                    <option value="PONTO">PONTO</option>
                </select>
            </div>
            <div class="form-group">
                <label>Transportadora</label>
                <select name="transportadora" required>
                    <option value="BRASPRESS">BRASPRESS</option>
                    <option value="OUTROS">OUTROS</option>
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
                <label for="serieNota">Série da Nota Fiscal</label>
                <input type="text" id="serieNota" name="serieNota" required>
            </div>
            <div class="form-group">
                <label for="referencia">Referência</label>
                <input type="text" id="referencia" name="referencia" required>
            </div>
            <div class="form-group">
                <label for="cor">Cor</label>
                <input type="text" id="cor" name="cor" required>
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
        document.getElementById('divergenciaForm').addEventListener('submit', function(event) {
            event.preventDefault();
            const formData = new FormData(this);
            fetch('https://script.google.com/macros/s/YOUR_DEPLOYED_SCRIPT_URL/exec', {
                method: 'POST',
                body: formData
            })
            .then(response => response.json())
            .then(data => {
                alert('Dados enviados com sucesso!');
                document.getElementById('divergenciaForm').reset();
            })
            .catch(error => {
                alert('Erro ao enviar os dados!');
                console.error('Erro:', error);
            });
        });
    </script>
</body>
</html>
