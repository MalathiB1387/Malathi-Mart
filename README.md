# Malathi-LifeBridge-mart
AI-powered smart marketplace for customers and local stores
import java.util.ArrayList;
import java.util.Scanner;

public class Item {

    static Scanner sc = new Scanner(System.in);

    static ArrayList<String> names = new ArrayList<>();
    static ArrayList<Double> prices = new ArrayList<>();
    static ArrayList<String> stores = new ArrayList<>();
    static ArrayList<Integer> cart = new ArrayList<>();

    public static void main(String[] args) {

        addProducts();

        int choice;

        System.out.println("==========================================");
        System.out.println("           LIFEBRIDGE MART");
        System.out.println("   Smart Essential Shopping Platform");
        System.out.println("==========================================");

        do {
            System.out.println("\n------------- MAIN MENU -------------");
            System.out.println("1. View Products");
            System.out.println("2. Search Product");
            System.out.println("3. Nearby Stores");
            System.out.println("4. AI Recommendations");
            System.out.println("5. Add to Cart");
            System.out.println("6. View Cart");
            System.out.println("7. Place Order");
            System.out.println("8. Track Order");
            System.out.println("9. Exit");

            System.out.print("Enter choice: ");
            choice = sc.nextInt();
            sc.nextLine();

            switch (choice) {

                case 1:
                    viewProducts();
                    break;

                case 2:
                    searchProduct();
                    break;

                case 3:
                    nearbyStores();
                    break;

                case 4:
                    recommendations();
                    break;

                case 5:
                    addToCart();
                    break;

                case 6:
                    viewCart();
                    break;

                case 7:
                    placeOrder();
                    break;

                case 8:
                    trackOrder();
                    break;

                case 9:
                    System.out.println("\nThank you for using LifeBridge Mart!");
                    break;

                default:
                    System.out.println("Invalid choice!");
            }

        } while (choice != 9);
    }

    // Add sample products
    static void addProducts() {

        names.add("Rice 5kg");
        prices.add(350.0);
        stores.add("Green Mart");

        names.add("Milk 1L");
        prices.add(60.0);
        stores.add("Sakthi Store");

        names.add("Bread");
        prices.add(45.0);
        stores.add("City Mart");

        names.add("Tomato 1kg");
        prices.add(50.0);
        stores.add("Green Mart");

        names.add("Soap");
        prices.add(40.0);
        stores.add("Sakthi Store");

        names.add("Cooking Oil 1L");
        prices.add(150.0);
        stores.add("City Mart");

        names.add("Biscuits");
        prices.add(30.0);
        stores.add("Green Mart");

        names.add("Shampoo");
        prices.add(120.0);
        stores.add("Sakthi Store");
    }

    // View products
    static void viewProducts() {

        System.out.println("\n------------- PRODUCTS -------------");

        for (int i = 0; i < names.size(); i++) {

            System.out.println(
                (i + 1) + ". " +
                names.get(i) +
                " | Rs." + prices.get(i) +
                " | " + stores.get(i)
            );
        }
    }

    // Search product
    static void searchProduct() {

        System.out.print("\nEnter product name: ");
        String search = sc.nextLine().toLowerCase();

        boolean found = false;

        for (int i = 0; i < names.size(); i++) {

            if (names.get(i).toLowerCase().contains(search)) {

                System.out.println(
                    names.get(i) +
                    " | Rs." + prices.get(i) +
                    " | " + stores.get(i)
                );

                found = true;
            }
        }

        if (!found) {
            System.out.println("Product not found.");
        }
    }

    // Nearby stores
    static void nearbyStores() {

        System.out.println("\n--------- NEARBY STORES ---------");

        System.out.println("1. Green Mart   - 0.4 km");
        System.out.println("2. Sakthi Store - 0.8 km");
        System.out.println("3. City Mart    - 1.2 km");
        System.out.println("4. Fresh Store  - 1.5 km");
    }

    // AI recommendation
    static void recommendations() {

        System.out.println("\n====== AI RECOMMENDATIONS ======");

        System.out.println("Based on popular shopping patterns:");

        System.out.println("1. Rice 5kg       - Rs.350");
        System.out.println("2. Milk 1L        - Rs.60");
        System.out.println("3. Cooking Oil    - Rs.150");
        System.out.println("4. Biscuits       - Rs.30");

        System.out.println("\nAI Suggestion:");
        System.out.println("Milk + Bread can be a useful combination.");
    }

    // Add to cart
    static void addToCart() {

        viewProducts();

        System.out.print("\nEnter product number: ");
        int product = sc.nextInt();

        if (product >= 1 && product <= names.size()) {

            cart.add(product - 1);

            System.out.println(
                names.get(product - 1) +
                " added to cart successfully!"
            );

        } else {

            System.out.println("Invalid product number.");
        }
    }

    // View cart
    static void viewCart() {

        System.out.println("\n------------- YOUR CART -------------");

        if (cart.isEmpty()) {

            System.out.println("Cart is empty.");
            return;
        }

        double total = 0;

        for (int index : cart) {

            System.out.println(
                names.get(index) +
                " - Rs." + prices.get(index)
            );

            total += prices.get(index);
        }

        System.out.println("-------------------------------------");
        System.out.println("Total Amount: Rs." + total);
    }

    // Place order
    static void placeOrder() {

        if (cart.isEmpty()) {

            System.out.println("\nYour cart is empty.");
            return;
        }

        double total = 0;

        for (int index : cart) {
            total += prices.get(index);
        }

        System.out.println("\n========== ORDER CONFIRMED ==========");
        System.out.println("Order ID: LB1001");
        System.out.println("Total Amount: Rs." + total);
        System.out.println("Status: Order Placed");
        System.out.println("Estimated Delivery: 30-45 minutes");
        System.out.println("=====================================");

        cart.clear();
    }

    // Track order
    static void trackOrder() {

        System.out.println("\n========== ORDER TRACKING ==========");

        System.out.println("Order ID: LB1001");
        System.out.println("1. Order Placed       ✓");
        System.out.println("2. Store Confirmed    ✓");
        System.out.println("3. Preparing Order    ✓");
        System.out.println("4. Out for Delivery   →");
        System.out.println("5. Delivered          Pending");

        System.out.println("====================================");
    }
}
