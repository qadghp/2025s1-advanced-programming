# C++ Coding Challenge: Inventory Management System using C++ Containers


## Objective
The goal of this lab is to provide hands-on experience using C++ containers (`std::vector`, `std::set`, `std::stack`, `std::queue`, and `std::map`). Students will implement an inventory management system for a small store where they will use different data structures to store and manage products, track orders, and maintain logs.

---

## **Scenario**
You have been hired by a small store to develop a simple inventory management system. The store keeps track of its products, processes customer orders, and maintains a history of returned items. Your task is to implement the system using C++ containers.

---

## **Task 1: Managing Products with `std::map`**
- Use `std::map<std::string, int>` to store products in the inventory. The key is the product name, and the value is the quantity available.
- Implement functions to:
  - Add a new product to the inventory.
  - Update the quantity of an existing product.
  - Display all available products.

```cpp
#include <iostream>
#include <map>

void displayInventory(const std::map<std::string, int>& inventory) {
    std::cout << "Current Inventory:\n";
    for (const auto& item : inventory) {
        std::cout << item.first << ": " << item.second << " in stock\n";
    }
    std::cout << std::endl;
}

int main() {
    std::map<std::string, int> inventory;

    // Adding products
    inventory["Laptop"] = 5;
    inventory["Mouse"] = 20;
    inventory["Keyboard"] = 10;

    displayInventory(inventory);

    return 0;
}
```

---

## **Task 2: Tracking Unique Products with `std::set`**
- Use `std::set<std::string>` to store unique product categories.
- Implement functions to:
  - Add a new category.
  - Display all categories.

```cpp
#include <iostream>
#include <set>

int main() {
    std::set<std::string> productCategories;

    // Adding categories
    productCategories.insert("Electronics");
    productCategories.insert("Accessories");
    productCategories.insert("Peripherals");

    std::cout << "Product Categories:\n";
    for (const auto& category : productCategories) {
        std::cout << "- " << category << "\n";
    }

    return 0;
}
```

---

## **Task 3: Processing Orders with `std::queue`**
- Use `std::queue<std::string>` to manage customer orders (FIFO processing).
- Implement functions to:
  - Add a new order.
  - Process an order (remove from the queue).

```cpp
#include <iostream>
#include <queue>

int main() {
    std::queue<std::string> orders;

    // Adding orders
    orders.push("Order#1: Laptop");
    orders.push("Order#2: Mouse");
    orders.push("Order#3: Keyboard");

    // Processing orders
    while (!orders.empty()) {
        std::cout << "Processing " << orders.front() << std::endl;
        orders.pop();
    }

    return 0;
}
```

---

## **Task 4: Handling Restocks with `std::stack`**
- Use `std::stack<std::pair<std::string, int>>` to manage restocked items (LIFO processing).
- Implement functions to:
  - Add a restock batch.
  - Process a restock batch.

```cpp
#include <iostream>
#include <stack>

int main() {
    std::stack<std::pair<std::string, int>> restocks;

    // Adding restock batches
    restocks.push({"Mouse", 10});
    restocks.push({"Laptop", 2});
    restocks.push({"Keyboard", 5});

    // Processing restocks
    while (!restocks.empty()) {
        auto item = restocks.top();
        std::cout << "Restocking " << item.second << " units of " << item.first << std::endl;
        restocks.pop();
    }

    return 0;
}
```

---

## **Task 5: Storing Customer Purchases with `std::vector`**
- Use `std::vector<std::string>` to keep track of items a customer purchases.
- Implement functions to:
  - Add items to a customer’s cart.
  - Display the items in the cart.

```cpp
#include <iostream>
#include <vector>

int main() {
    std::vector<std::string> customerCart;

    // Adding items to cart
    customerCart.push_back("Laptop");
    customerCart.push_back("Mouse");
    customerCart.push_back("Keyboard");

    std::cout << "Items in customer cart:\n";
    for (const auto& item : customerCart) {
        std::cout << "- " << item << "\n";
    }

    return 0;
}
```

---

## **Final Challenge (Bonus Task)**
- Combine all tasks into a **single program** where users can:
  - Add products to inventory (`std::map`).
  - Categorize products (`std::set`).
  - Process orders (`std::queue`).
  - Manage restocks (`std::stack`).
  - Simulate a shopping cart (`std::vector`).

This final implementation will solidify students' understanding of C++ containers in a real-world scenario.

---

## **Lab Submission**
- Students should implement all five tasks and submit their final integrated program.
- Encourage students to experiment by adding error handling and extending functionality.

Would you like to modify the scenario or add additional requirements?

