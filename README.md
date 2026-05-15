# factor-digielectronic-
طراحی فاکتور با کد HTML
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>Invoice v1 - Navy Clean Style</title>
<style>
    body {
        font-family: Arial, sans-serif;
        background: #f5f7fb;
        margin: 0;
        padding: 20px;
    }
    .invoice-box {
        max-width: 900px;
        margin: auto;
        background: #fff;
        padding: 30px;
        border-radius: 12px;
        box-shadow: 0 10px 25px rgba(0,0,0,0.08);
    }
    .header {
        display: flex;
        justify-content: space-between;
        align-items: center;
        border-bottom: 3px solid #0b1f3a;
        padding-bottom: 15px;
    }
    .brand {
        font-size: 24px;
        font-weight: bold;
        color: #0b1f3a;
    }
    .meta {
        text-align: right;
        font-size: 14px;
        color: #555;
    }
    .client {
        margin-top: 20px;
        font-size: 15px;
        color: #333;
    }
    table {
        width: 100%;
        border-collapse: collapse;
        margin-top: 20px;
    }
    table th {
        background: #0b1f3a;
        color: #fff;
        padding: 10px;
        font-size: 14px;
    }
    table td {
        border-bottom: 1px solid #eee;
        padding: 10px;
        font-size: 14px;
    }
    .right {
        text-align: right;
    }
    .total {
        margin-top: 20px;
        text-align: right;
        font-size: 16px;
        font-weight: bold;
        color: #0b1f3a;
    }
    .footer {
        margin-top: 30px;
        font-size: 12px;
        color: #777;
        border-top: 1px solid #eee;
        padding-top: 10px;
        text-align: center;
    }
    .accent {
        color: #f28c28;
    }
</style>
</head>
<body>
<div class="invoice-box">

    <div class="header">
        <div class="brand">
            DigiElectronic <span class="accent">Invoice</span>
        </div>
        <div class="meta">
            <div>Invoice No: 001</div>
            <div>Date: 2026-05-13</div>
        </div>
    </div>

    <div class="client">
        <strong>Bill To:</strong> _______________________<br/>
        Address: _________________________________
    </div>

    <table id="invoiceTable">
        <thead>
            <tr>
                <th>#</th>
                <th>Description</th>
                <th class="right">Qty</th>
                <th class="right">Unit Price</th>
                <th class="right">Total</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>1</td>
                <td><input type="text" value="SWIT S-1093H LUXURY Monitor 9\"" style="width:100%; border:none; background:transparent;"></td>
                <td class="right"><input type="number" value="1" class="qty" oninput="calc()"></td>
                <td class="right"><input type="number" value="850" class="price" oninput="calc()"></td>
                <td class="right rowTotal">850</td>
            </tr>
            <tr>
                <td>2</td>
                <td>Videohub Smart Control Pro</td>
                <td class="right"><input type="number" value="1" class="qty" oninput="calc()"></td>
                <td class="right"><input type="number" value="995" class="price" oninput="calc()"></td>
                <td class="right rowTotal">995</td>
            </tr>
            <tr>
                <td>3</td>
                <td><input type="text" value="Master Control Unit" style="width:100%; border:none; background:transparent;"></td>
                <td class="right"><input type="number" value="1" class="qty" oninput="calc()"></td>
                <td class="right"><input type="number" value="975" class="price" oninput="calc()"></td>
                <td class="right rowTotal">975</td>
            </tr>
        </tbody>
    </table>

    <div class="total" id="grandTotal">
        Grand Total: 2820
    </div>

    <div style="margin-top:20px; text-align:right;">
        <button onclick="addRow()" style="padding:10px 18px; border:none; border-radius:8px; background:#f28c28; color:white; cursor:pointer; margin-right:10px;">
            + Add Item
        </button>

        <button onclick="window.print()" style="padding:10px 18px; border:none; border-radius:8px; background:#0b1f3a; color:white; cursor:pointer;">
            Print / Save PDF
        </button>
    </div>

<script>
function addRow(){
    let table = document.querySelector("#invoiceTable tbody");
    let rowCount = table.rows.length + 1;

    let row = table.insertRow();

    row.innerHTML = `
        <td>${rowCount}</td>
        <td><input type="text" value="New Equipment" style="width:100%; border:none; background:transparent;"></td>
        <td class="right"><input type="number" value="1" class="qty" oninput="calc()"></td>
        <td class="right"><input type="number" value="0" class="price" oninput="calc()"></td>
        <td class="right rowTotal">0</td>
    `;

    calc();
}

function calc(){
    let rows = document.querySelectorAll("#invoiceTable tbody tr");
    let grand = 0;

    rows.forEach(r => {
        let qty = r.querySelector(".qty").value;
        let price = r.querySelector(".price").value;
        let total = qty * price;
        r.querySelector(".rowTotal").innerText = total;
        grand += total;
    });

    document.getElementById("grandTotal").innerText = "Grand Total: " + grand;
}
calc();
</script>

    <div class="footer">
        DigiElectronic | Professional Broadcast & Studio Equipment
    </div>

</div>
</body>
</html>
تا اینجا درست کار نمیکنه
