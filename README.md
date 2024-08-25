 <!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Dépôt Mobile Money</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f9;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
        }
        .deposit-container {
            background-color: #fff;
            padding: 30px;
            border-radius: 10px;
            box-shadow: 0 0 15px rgba(0, 0, 0, 0.1);
            width: 350px;
            text-align: center;
        }
        .deposit-container input,
        .deposit-container button {
            padding: 10px;
            margin: 10px 0;
            width: 100%;
        }
        .deposit-container button {
            background-color: #ff8200;
            border: none;
            color: #fff;
            cursor: pointer;
            font-size: 16px;
        }
    </style>
</head>
<body>
    <div class="deposit-container">
        <h2>Dépôt Mobile Money</h2>
        <form id="depositForm">
            <input type="text" id="phoneNumber" placeholder="Numéro de Téléphone" required><br>
            <input type="number" id="amount" placeholder="Montant à déposer (CFA)" required><br>
            <button type="button" onclick="submitPayment()">Payer avec Mobile Money</button>
        </form>
    </div>

    <script>
        function submitPayment() {
            var phoneNumber = document.getElementById('phoneNumber').value;
            var amount = document.getElementById('amount').value;

            if (!phoneNumber || !amount) {
                alert('Veuillez entrer toutes les informations.');
                return;
            }

            // Requête pour envoyer les données à votre serveur backend
            fetch('https://votre-backend-url/api/paiement', {
                method: 'POST',
                headers: {
                    'Content-Type': 'application/json'
                },
                body: JSON.stringify({
                    identifiant: 'LIONEL SONGFACK',
                    numero: phoneNumber,
                    montant: amount
                })
            })
            .then(response => response.json())
            .then(data => {
                if (data.success) {
                    alert('Paiement réussi. Merci pour votre dépôt.');
                } else {
                    alert('Échec du paiement. Veuillez réessayer.');
                }
            })
            .catch(error => {
                console.error('Erreur:', error);
                alert('Une erreur est survenue. Veuillez réessayer plus tard.');
            });
        }
    </script>
</body>
</html>
