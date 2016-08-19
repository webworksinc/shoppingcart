
Usage

$cart = new shoppingCart();

//using session variables
if (isset($_SESSION['cart'])) {
    $cart = $_SESSION['cart'];
} else {
    $cart = new ShoppingCart();
}


$w1 = new Item('W139', 'Some Widget', 23.45);
$w2 = new Item('W384', 'Another Widget', 12.39);
$w3 = new Item('W55', 'Cheap Widget', 5.00);


$cart->addItem($w1);
$cart->addItem($w2);
$cart->addItem($w3);
$cart->updateItem($w2, 4);
$cart->updateItem($w1, 1);
$cart->deleteItem($w3);



echo '<h2>Cart Contents (' . count($cart) . ' items)</h2>';
if (!$cart->isEmpty()) {
    foreach ($cart as $arr) {
        $item = $arr['item'];
        printf('<p><strong>%s</strong>: %d @ $%0.2f each.<p>', $item->getName(), $arr['qty'], $item->getPrice());
    }
}