// Calculator Functions
function add(a, b) {
  return a + b;
}

function subtract(a, b) {
  return a - b;
}

function multiply(a, b) {
  return a * b;
}

function divide(a, b) {
  if (b === 0) {
    return "Error: Division by zero"; // Correct handling for division by zero
  }
  return a / b;
}

// Test Cases
console.log("Addition Test 1:", add(5, 3) === 8 ? "Pass" : "Fail"); // Correct test case
console.log("Subtraction Test 1:", subtract(10, 4) === 6 ? "Pass" : "Fail"); // Corrected expected value (value changed from 5 to 6)
console.log("Multiplication Test 1:", multiply(7, 6) === 42 ? "Pass" : "Fail"); // Correct test case
console.log("Division Test 1:", divide(12, 4) === 3 ? "Pass" : "Fail"); // Correct test case
console.log("Division by Zero Test:", divide(5, 0) === "Error: Division by zero" ? "Pass" : "Fail"); // New test case for division by zero!!!
console.log("Division Test 4:", divide(-12, -4) === 3 ? "Pass" : "Fail");  // New test case for negative numbers!!!


// Login Validation Function
function validateLogin(username, password) {
  if (!username || !password) {
    return false;
  }
  if (username === "admin" && password === "1234") {
    return true;
  }
  return false;
}

// Test Cases
console.log("Login Test 1:", validateLogin("admin", "1234") === true ? "Pass" : "Fail");
console.log("Login Test 2:", validateLogin("", "1234") === false ? "Pass" : "Fail");
console.log("Login Test 3:", validateLogin("admin", "") === false ? "Pass" : "Fail"); // fixed test (an empty password isnt valid so expected value is now FALSE
console.log("Login Test 4:", validateLogin("user", "1234") === false ? "Pass" : "Fail"); // Invalid username, valid password (new)
console.log("Login Test 5:", validateLogin("admin", "password123") === false ? "Pass" : "Fail"); // Valid username, invalid password (new)
console.log("Login Test 6:", validateLogin("user", "password123") === false ? "Pass" : "Fail"); // Invalid username and password (new)
console.log("Login Test 9:", validateLogin("admin!@#$", "1234") === false ? "Pass" : "Fail"); // Special characters in username, valid password (new)
console.log("Login Test 10:", validateLogin("admin", "pass!@#$") === false ? "Pass" : "Fail"); // Valid username, special characters in password (new)


// Shopping Cart Functions
let cart = [];

function addItem(item, quantity) {
  if (quantity < 1) {
    console.log("Error: Quantity must be at least 1");
    return; // Prevent adding item with quantity less than 1
  }
  cart.push({ item, quantity });
}

function removeItem(item) {
  // Normalize case (convert both to lowercase) to handle case insensitivity
  cart = cart.filter(cartItem => cartItem.item.toLowerCase() !== item.toLowerCase());
}

function getCartTotal() {
  return cart.reduce((total, cartItem) => total + cartItem.quantity, 0);
}

// Test Cases

// Adding items to cart
addItem("Apple", 3);  // Should add Apple with quantity 3
addItem("Banana", 0);  // Should show error and not add to cart
addItem("Orange", 2);  // Should add Orange with quantity 2

// Trying to remove an item (case insensitive)
removeItem("apple"); // Should remove "Apple" (case insensitive)
removeItem("banana"); // Should not remove anything because Banana wasn't added (quantity was 0)

// Check total quantity in the cart (should be 2 after removing "Apple")
console.log("Cart Total Test 1:", getCartTotal() === 2 ? "Pass" : "Fail");  // Expected total is 2 (Orange with quantity 2)
