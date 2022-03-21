
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
<div>
    <div>
        <h1>Day end Sheet</h1>
        <h4>Please enter values in all columns, If no value plese enter 0 (zero), do not leave any column empty  </h4>
    </div>
    <table border=1 style="width:100%">
        <tr>
            <th><label for="membership">Choose a membership type:</label></th>
            <th>
                <select name="membership" id="membership" onchange="clear()">
                    <option value="sel">Select</option>
                    <option value="mem">Member</option>
                    <option value="non">Non Member</option>
                </select>
            </th>
        </tr>
        <tr>
            <th>Gross Food Sales</th>
            <th><input type="text" id="fsale" name="TextBox1"></th>
        </tr>
        <tr>
            <th>Gross Non Food Sales</th>
            <th><input type="text" id="nfsale" name="TextBox2"></th>
        <tr>
        <tr>
            <th>Food Stamp Tookens</th>
            <th><input type="text" id="fstamp" name="TextBox2"></th>
        <tr>
        <tr>
            <th>DUFB Vouchers</th>
            <th><input type="text" id="dvoucher" name="TextBox2"></th>
        <tr>
        <tr>
            <th>Coupons</th>
            <th><input type="text" id="coupons" name="TextBox2"></th>
        <tr>
        <tr>
            <th>Tokens</th>
            <th><input type="text" id="tokens" name="TextBox2"></th>
        <tr>
       </table>
<br><br>
    <input type="button" name="clickbtn" value="Calculate Fee" onclick="add_number()">
    <br><br>
        <table border =1 style="width:100%">
        <tr>
            <th>Food Tax 2.25%</th>
            <th><input type="text" id="ftax" name="TextBox2" readonly></th>
        <tr>
        <tr>
            <th>Non Food Tax 7.55%</th>
            <th><input type="text" id="nftax" name="TextBox2" readonly></th>
        <tr>
        <tr>
            <th>Market fee</th>
            <th><input type="text" id="mfee" name="TextBox2" readonly></th>
        <tr>
        <tr>
            <th>Total to pay</th>
            <th><input type="text" id="total" name="TextBox3" readonly></th>
        </tr>
    </table>
</body>
	<script type="text/javascript">
           function add_number() {
                console.log("inside function");
                var fsale = parseInt(document.getElementById("fsale").value);
                var nfsale = parseInt(document.getElementById("nfsale").value);
                var fstamp = parseInt(document.getElementById("fstamp").value);
                var dufvouchers = parseInt(document.getElementById("dvoucher").value);
                var coupons = parseInt(document.getElementById("coupons").value);
                var tokens = parseInt(document.getElementById("tokens").value);
		        var e = document.getElementById("membership");
                var memType = e.options[e.selectedIndex].value;

                var ftax = (fsale - fstamp - dufvouchers) * 0.0225;
                var nftax = nfsale * 0.0755;
                var totalSale = (fsale - ftax) + (nfsale - nftax);
                var mfee;
                var total;
                if(memType == "mem"){
                   mfee = totalSale * 0.05;
                }else if (memType == "non"){
                console.log("in non mem block");
                   mfee = (totalSale * 0.10) + 10;
                 }

                 total = (mfee + ftax + nftax) - (fstamp + dufvouchers + coupons + tokens);

                document.getElementById("ftax").value = ftax.toFixed(2);
                document.getElementById("nftax").value = nftax.toFixed(2);;
                document.getElementById("mfee").value = mfee.toFixed(2);;
                document.getElementById("total").value = total.toFixed(2);;
            }
    </script>
</html>
