# School-work-1
<?php
// Pizza prices
$margheritaPrice = 8.50;
$pepperoniPrice = 9.50;
$veggiePrice = 9.00;
// Default quantities
$qtyMargherita = 0;
$qtyPepperoni = 0;
$qtyVeggie = 0;
$total = 0;
$orderPlaced = false;
// Check if the form was submitted
if ($_SERVER["REQUEST_METHOD"] === "GET" && isset($_GET["margherita"])) {
$qtyMargherita = max(0, (int) $_GET["margherita"]);
$qtyPepperoni = max(0, (int) $_GET["pepperoni"]);
$qtyVeggie = max(0, (int) $_GET["veggie"]);
// Calculate individual totals
$margheritaTotal = $qtyMargherita * $margheritaPrice;
$pepperoniTotal = $qtyPepperoni * $pepperoniPrice;
$veggieTotal = $qtyVeggie * $veggiePrice;
// Calculate overall total
$total = $margheritaTotal + $pepperoniTotal + $veggieTotal;
$orderPlaced = true;
}
?>
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Pizza Order</title>
</head>
<body>
<h2>Place Your Pizza Order</h2>
<form method="GET" action="pizza_order.php">
<label>
</label>
<input
type="number"
name="margherita"
min="0"
Number of Margherita pizzas (€8.50 each):
value="<?php echo $qtyMargherita; ?>"
>
<br><br>
<label>
</label>
<input
type="number"
name="pepperoni"
min="0"
Number of Pepperoni pizzas (€9.50 each):
value="<?php echo $qtyPepperoni; ?>"
>
<br><br>
<label>
</label>
<input
type="number"
name="veggie"
min="0"
Number of Veggie pizzas (€9.00 each):
value="<?php echo $qtyVeggie; ?>"
>
<br><br>
<input type="submit" value="Calculate My Order">
</form>
<?php if ($orderPlaced): ?>
<hr>
<h3>Your Pizza Order Summary:</h3>
<p>
Margherita × <?php echo $qtyMargherita; ?>
= €<?php echo number_format($margheritaTotal, 2); ?>
</p>
<p>
Pepperoni × <?php echo $qtyPepperoni; ?>
= €<?php echo number_format($pepperoniTotal, 2); ?>
</p>
<p>
Veggie × <?php echo $qtyVeggie; ?>
= €<?php echo number_format($veggieTotal, 2); ?>
</p>
<hr>
<p>
<strong>
</strong>
Total to pay: €<?php echo number_format($total, 2); ?>
</p>
<?php if ($total > 20): ?>
<p style="color: green; font-weight: bold;">
Wow! Big order — you get a free drink!
</p>
<?php else: ?>
<p style="color: blue;">
Thank you for your order!
</p>
<?php endif; ?>
<?php endif; ?>
</body>
</html
