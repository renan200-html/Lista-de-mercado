<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Minha Lista de Mercado</title>
    <style>
        /* CSS - Estilização e Responsividade */
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: #f4f4f9;
            display: flex;
            justify-content: center;
            padding: 20px;
        }

        .container {
            background: white;
            width: 100%;
            max-width: 400px;
            padding: 20px;
            border-radius: 12px;
            box-shadow: 0 4px 10px rgba(0,0,0,0.1);
        }

        h2 { text-align: center; color: #333; }

        .input-group {
            display: flex;
            gap: 10px;
            margin-bottom: 20px;
        }

        input {
            flex: 1;
            padding: 12px;
            border: 1px solid #ddd;
            border-radius: 6px;
            outline: none;
        }

        button#add-btn {
            padding: 12px;
            background-color: #28a745;
            color: white;
            border: none;
            border-radius: 6px;
            cursor: pointer;
            font-weight: bold;
        }

        ul {
            list-style: none;
            padding: 0;
        }

        li {
            background: #fff;
            border-bottom: 1px solid #eee;
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 10px 5px;
        }

        .remove-btn {
            background-color: #dc3545;
            color: white;
            border: none;
            padding: 5px 10px;
            border-radius: 4px;
            cursor: pointer;
            font-size: 12px;
        }

        /* Ajuste para Celular */
        @media (max-width: 480px) {
            body { padding: 10px; }
            .container { border-radius: 0; height: 100vh; max-width: 100%; }
        }
    </style>
</head>
<body>

<div class="container">
    <h2>Lista de Mercado 🛒</h2>
    
    <div class="input-group">
        <input type="text" id="item-input" placeholder="Ex: Arroz, Feijão...">
        <button id="add-btn">Add</button>
    </div>

    <ul id="shopping-list">
        </ul>
</div>

<script>
    // JavaScript - Lógica de funcionamento
    const input = document.getElementById('item-input');
    const btn = document.getElementById('add-btn');
    const list = document.getElementById('shopping-list');

    function addItem() {
        const text = input.value.trim();
        
        if (text !== "") {
            const li = document.createElement('li');
            li.innerHTML = `
                <span>${text}</span>
                <button class="remove-btn" onclick="this.parentElement.remove()">Remover</button>
            `;
            list.appendChild(li);
            input.value = ""; // Limpa o campo
            input.focus();
        }
    }

    // Adiciona ao clicar no botão
    btn.addEventListener('click', addItem);

    // Adiciona ao apertar "Enter"
    input.addEventListener('keypress', (e) => {
        if (e.key === 'Enter') addItem();
    });
</script>

</body>
</html>
