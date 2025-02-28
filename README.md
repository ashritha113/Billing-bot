# Billing-bot
#The Billing Website is a fast and efficient system designed for medical shops to manage transactions seamlessly.
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Billing System</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background: #000;
            color: white;
            margin: 0;
            display: flex;
            height: 100vh;
            justify-content: center;
            align-items: center;
        }
        .container {
            width: 100%;
            max-width: 500px;
            background: #111;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 5px 15px rgba(255, 255, 255, 0.2);
            text-align: center;
        }
        .container h2 {
            color: white;
        }
        .billing-form input {
            width: 100%;
            padding: 10px;
            margin: 10px 0;
            border: 1px solid white;
            border-radius: 5px;
            background: #222;
            color: white;
        }
        .billing-form button {
            width: 100%;
            padding: 10px;
            background: white;
            color: black;
            border: none;
            border-radius: 5px;
            font-size: 16px;
            cursor: pointer;
        }
        .billing-form button:hover {
            background: #ddd;
        }
        .stats {
            margin-top: 20px;
            background: #222;
            padding: 10px;
            border-radius: 10px;
        }
        .history {
            margin-top: 20px;
            background: #333;
            padding: 10px;
            border-radius: 10px;
            text-align: left;
            max-height: 200px;
            overflow-y: auto;
        }
    </style>
</head>
<body>
    <div class="container">
        <h2>Billing System</h2>
        <div class="billing-form">
            <input type="text" id="customer-name" placeholder="Customer Name">
            <input type="text" id="mobile-number" placeholder="Mobile Number">
            <input type="text" id="items" placeholder="Purchased Items">
            <input type="number" id="total-amount" placeholder="Total Amount">
            <button onclick="processBilling()">Submit</button>
        </div>
        <div class="stats">
            <h3>Sales Summary</h3>
            <p><strong>Customers Served:</strong> <span id="customer-count">0</span></p>
            <p><strong>Total Sales:</strong> ₹<span id="total-sales">0</span></p>
        </div>
        <div class="history">
            <h3>Billing History</h3>
            <ul id="history-list"></ul>
        </div>
    </div>

    <script>
        let customerCount = 0;
        let totalSales = 0;

        function processBilling() {
            let name = document.getElementById("customer-name").value;
            let mobile = document.getElementById("mobile-number").value;
            let items = document.getElementById("items").value;
            let amount = parseFloat(document.getElementById("total-amount").value);

            if (name && mobile && items && !isNaN(amount) && amount > 0) {
                customerCount++;
                totalSales += amount;
                document.getElementById("customer-count").innerText = customerCount;
                document.getElementById("total-sales").innerText = totalSales;
                
                let historyList = document.getElementById("history-list");
                let entry = document.createElement("li");
                entry.innerText = `Name: ${name}, Mobile: ${mobile}, Items: ${items}, Amount: ₹${amount}`;
                historyList.prepend(entry);
                
                clearForm();
            } else {
                alert("Please enter valid details.");
            }
        }

        function clearForm() {
            document.getElementById("customer-name").value = "";
            document.getElementById("mobile-number").value = "";
            document.getElementById("items").value = "";
            document.getElementById("total-amount").value = "";
        }
    </script>
</body>
</html>
