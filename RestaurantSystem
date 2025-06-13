import java.util.*;
class RestaurantSystem {
    static Scanner sc = new Scanner(System.in);
    static Map<Integer, String> menu = new HashMap<>();
    static Map<Integer, Double> prices = new HashMap<>();
    static List<String> orders = new ArrayList<>();
	static List<String> customercart = new ArrayList<>();
    static List<String> reservations = new ArrayList<>();
    static double totalRevenue = 0;
    static boolean loginAsAdmin() {
        System.out.print("Enter admin password: ");
        return sc.nextLine().equals("admin123");
    }
    static {
		menu.put(1, "Tea");
		menu.put(2, "coffee");
        menu.put(3, "Pizza(4 pieces)");
        menu.put(4, "Burger");
		menu.put(5, "pizza(6 pieces)");
		menu.put(6, "sandwich(2 pieces)");
        menu.put(7, "french fries");
		menu.put(8, "coke");
		menu.put(9, "icecream");
		menu.put(10, "water bottel");
        prices.put(1, 50.0);
        prices.put(2, 100.0);
        prices.put(3, 250.0);
		prices.put(4, 200.0);
		prices.put(5, 400.0);
		prices.put(6, 150.0);
		prices.put(7, 150.0);
		prices.put(8, 50.0);
		prices.put(9, 180.0);
		prices.put(10, 30.0);
    }
    static void customerPortal() {
		double customerTotal=0.0;
		customercart.clear();
		boolean isBilled=false;
        while (true) {
            System.out.println("\nCustomer Menu");
            System.out.println("1. View Menu\n2. Place Order\n3. Reserve Table\n4. Viewcart\n5. GenerateBill\n6. Exit");
            int choice = sc.nextInt();
            sc.nextLine();
            switch (choice) {
                case 1: viewMenu(); break;
                case 2: customerTotal += placeOrder(); break;
                case 3: reserveTable(); break;
				case 4: Viewcart(); break;
				case 5: generateBill(customerTotal);
				        isBilled=true;
						break;
				case 6:if(!isBilled){
					System.out.println("please generate the bill before exiting");
				}
				else{
					return;
				}
				break;
                default: System.out.println("Invalid choice.");
            }
        }
    }
    static void viewMenu() {
        System.out.println("\n--- Menu ---");
        for (int id : menu.keySet())
            System.out.println(id + ". " + menu.get(id) + " - ₹" + prices.get(id));
    }
    static double placeOrder() {
        viewMenu();
        System.out.print("Enter item number to order: ");
        int item = sc.nextInt();
        sc.nextLine();
        if (menu.containsKey(item)) {
            orders.add(menu.get(item));
			double price=prices.get(item);
            totalRevenue += price;
            System.out.println("Order placed: " + menu.get(item));
        } else {
            System.out.println("Invalid item.");
        }
		return 0.0;
    }
    static void reserveTable() {
        System.out.print("Enter your name for reservation: ");
        String name = sc.nextLine();
        reservations.add(name);
        System.out.println("Table reserved for " + name);
    }
	static void Viewcart(){
		System.out.println("Orders: " + orders);
		
	}
	static void generateBill(double customerTotal){
		System.out.println("\n Final Bill");
		if(orders.isEmpty()){
			System.out.println("N0 items ordered.");
			return;
		}
		    double calculatedTotal = 0.0;

    System.out.printf("%-20s %10s\n", "Item", "Price");
    System.out.println("-------------------------------");

    for (String item : orders) {
        for (Map.Entry<Integer, String> entry : menu.entrySet()) {
            if (entry.getValue().equals(item)) {
                double price = prices.get(entry.getKey());
                System.out.printf("%-20s %10.2f\n", item, price);
                calculatedTotal += price;
            }
        }
    }

    System.out.println("-------------------------------");
    System.out.printf("%-20s %10.2f\n", "Total Amount", calculatedTotal);
    System.out.println("Thank you for visiting!");
}
    static void adminPortal() {
        if (loginAsAdmin()) {
            System.out.println("Access Denied.");
            return;
        }
        while (true) {
            System.out.println("\n--- Admin Dashboard ---");
            System.out.println("1. View Orders\n2. View Reservations\n3. Update Menu\n4. View Revenue\n5. Exit");
            int choice = sc.nextInt();
            sc.nextLine();
            switch (choice) {
                case 1: System.out.println("Orders: " + orders); break;
                case 2: System.out.println("Reservations: " + reservations); break;
                case 3: updateMenu(); break;
                case 4: System.out.println("Total Revenue: ₹" + totalRevenue); break;
                case 5: return;
                default: System.out.println("Invalid choice.");
            }
        }
    }
    static void updateMenu() {
        System.out.print("Enter new item name: ");
        String name = sc.nextLine();
        System.out.print("Enter price: ");
        double price = sc.nextDouble();
        int newId = menu.size() + 1;
        menu.put(newId, name);
        prices.put(newId, price);
        System.out.println("Menu updated.");
    }
    public static void main(String[] args) {
        while (true) {
            System.out.println("\nWelcome to Restaurant System");
            System.out.println("1. Customer\n2. Admin\n3. Exit");
            int role = sc.nextInt();
            sc.nextLine();
            if (role == 1) customerPortal();
            else if (role == 2) adminPortal();
            else break;
        }
    }
}
