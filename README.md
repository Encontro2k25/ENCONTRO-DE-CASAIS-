<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Encontro de Casais</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background: #e0f7fa;
            margin: 0;
            padding: 0;
            text-align: center;
            color: #004d40;
        }
        .header {
            background-color: #00796b;
            padding: 20px 0;
            color: white;
        }
        .header h1 {
            font-size: 2.5em;
            margin: 0;
        }
        .container {
            width: 80%;
            margin: auto;
            background: #ffffff;
            padding: 30px;
            border-radius: 15px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
            margin-top: -50px;
            z-index: 10;
            position: relative;
        }
        h2 {
            color: #004d40;
        }
        p {
            font-size: 1.2em;
        }
        button {
            background-color: #00796b;
            color: white;
            padding: 12px 30px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            font-size: 1.1em;
        }
        button:hover {
            background-color: #004d40;
        }
        .whatsapp-btn {
            background-color: #25D366;
            color: white;
            padding: 12px 30px;
            border-radius: 5px;
            text-decoration: none;
            font-size: 1.1em;
            margin-top: 20px;
        }
        .whatsapp-btn:hover {
            background-color: #128C7E;
        }
        input, textarea {
            width: 80%;
            padding: 12px;
            margin: 10px 0;
            font-size: 1em;
            border: 1px solid #ccc;
            border-radius: 5px;
        }
        .footer {
            background-color: #00796b;
            color: white;
            padding: 10px 0;
            margin-top: 30px;
        }
        .footer p {
            margin: 0;
        }
    </style>
    <!-- EmailJS Script -->
    <script type="text/javascript" src="https://cdn.emailjs.com/dist/email.min.js"></script>
    <script type="text/javascript">
        (function(){
            emailjs.init("your_user_id_here"); // Substitua com seu user ID do EmailJS
        })();
    </script>
</head>
<body>

    <!-- Cabeçalho -->
    <div class="header">
        <h1>Encontro de Casais - Igreja ADMP Morumbi</h1>
    </div>

    <!-- Conteúdo -->
    <div class="container">
        <h2>Informações do Evento</h2>
        <p><strong>Data:</strong> 28 de Junho de 2025 | <strong>Horário:</strong> 19:30 | <strong>Local:</strong> Igreja ADMP Morumbi, R. Tamanduás, 253 - Morumbi, Uberlândia</p>
        <p><strong>Valor:</strong> R$ 75,00 por pessoa<br>O valor total por casal (2 pessoas) será R$ 150,00.</p>
        <p><strong>Realize o pagamento via Pix:</strong></p>
        <a href="https://nubank.com.br/cobrar/17bxj0/67e8045b-dc79-44f6-bca4-ae4a889fb676" target="_blank">
            <button>Efetuar Pagamento via Pix</button>
        </a>
        <p style="color: red;"><strong>Não será permitida a entrada de crianças.</strong></p>
        <p><strong>Para parcelamento, entre em contato pelo WhatsApp:</strong></p>
        <a class="whatsapp-btn" href="https://wa.me/5534988356552" target="_blank">Falar no WhatsApp</a>

        <h2>Inscrição</h2>
        <form id="inscricaoForm">
            <input type="text" id="nome" placeholder="Nome do casal" required>
            <input type="email" id="email" placeholder="E-mail" required>
            <input type="tel" id="whatsapp" placeholder="WhatsApp (com DDD)" required>
            <textarea id="mensagem" placeholder="Mensagem (opcional)"></textarea>
            <button type="submit">Confirmar Inscrição</button>
        </form>
    </div>

    <!-- Rodapé -->
    <div class="footer">
        <p>Todos os direitos reservados &copy; 2025 Igreja ADMP Morumbi</p>
    </div>

    <script>
        document.getElementById('inscricaoForm').addEventListener('submit', function(event) {
            event.preventDefault();
            let nome = document.getElementById('nome').value;
            let email = document.getElementById('email').value;
            let whatsapp = document.getElementById('whatsapp').value;
            let mensagem = document.getElementById('mensagem').value;

            // Envia os dados para o e-mail com o ingresso
            emailjs.send("service_id", "template_id", {
                from_name: nome,
                from_email: email,
                whatsapp: whatsapp,
                message: mensagem,
                ingresso: `
                    Ingresso para o Encontro de Casais:
                    Nome: ${nome}
                    Data do Evento: 28 de Junho de 2025
                    Local: Igreja ADMP Morumbi
                    Valor: R$ 150,00
                    Confirmação: Confirmada
                `
            }).then(function(response) {
                console.log('Sucesso!', response);
                alert('Inscrição confirmada! Seu ingresso será enviado por e-mail.');
            }, function(error) {
                console.log('Erro:', error);
                alert('Houve um erro ao enviar a inscrição. Tente novamente.');
            });
        });
    </script>
</body>
</html>
