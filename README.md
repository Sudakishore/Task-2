# Task-2
class InventoryManager:
    def __init__(self):
        self.inventory = {}

   def add_product(self):
        product_id = input("Enter product ID: ")
        if product_id in self.inventory:
            print("Product ID already exists!")
            return
        
  product_name = input("Enter product name: ")
        quantity = int(input("Enter product quantity: "))
        price = float(input("Enter product price: "))
        
  self.inventory[product_id] = {
            'name': product_name,
            'quantity': quantity,
            'price': price
        }
        print("Product added successfully!\n")

  def edit_product(self):
        product_id = input("Enter product ID to edit: ")
        if product_id not in self.inventory:
            print("Product ID not found!")
            return
        
   print("Leave the field blank if you do not wish to change it.")
        
  product_name = input("Enter new product name (current: {}): ".format(self.inventory[product_id]['name']))
        if product_name:
            self.inventory[product_id]['name'] = product_name
        
  try:
            quantity = input("Enter new product quantity (current: {}): ".format(self.inventory[product_id]['quantity']))
            if quantity:
                self.inventory[product_id]['quantity'] = int(quantity)
            
   price = input("Enter new product price (current: {}): ".format(self.inventory[product_id]['price']))
            if price:
                self.inventory[product_id]['price'] = float(price)
            
  print("Product updated successfully!\n")
        except ValueError:
            print("Invalid input. Product not updated.\n")

   def delete_product(self):
        product_id = input("Enter product ID to delete: ")
        if product_id in self.inventory:
            del self.inventory[product_id]
            print("Product deleted successfully!\n")
        else:
            print("Product ID not found!\n")

  def view_inventory(self):
        if not self.inventory:
            print("Inventory is empty.\n")
            return
        
   print("Current Inventory:")
        for product_id, details in self.inventory.items():
            print(f"ID: {product_id}, Name: {details['name']}, Quantity: {details['quantity']}, Price: ${details['price']}")
        print()

  def low_stock_alert(self, threshold=10):
        print(f"Products with quantity less than {threshold}:")
        for product_id, details in self.inventory.items():
            if details['quantity'] < threshold:
                print(f"ID: {product_id}, Name: {details['name']}, Quantity: {details['quantity']}")
        print()

  def sales_summary(self):
        total_sales_value = 0
        for product_id, details in self.inventory.items():
            total_sales_value += details['price'] * details['quantity']
        
   print(f"Total value of inventory: ${total_sales_value}\n")

def main():
    inventory_manager = InventoryManager()

  while True:
        print("1. Add Product")
        print("2. Edit Product")
        print("3. Delete Product")
        print("4. View Inventory")
        print("5. Low Stock Alert")
        print("6. Sales Summary")
        print("7. Exit")

  choice = input("Choose an option: ")

  if choice == '1':
            inventory_manager.add_product()
        elif choice == '2':
            inventory_manager.edit_product()
        elif choice == '3':
            inventory_manager.delete_product()
        elif choice == '4':
            inventory_manager.view_inventory()
        elif choice == '5':
            threshold = int(input("Enter the low stock threshold: "))
            inventory_manager.low_stock_alert(threshold)
        elif choice == '6':
            inventory_manager.sales_summary()
        elif choice == '7':
            print("Exiting program.")
            break
        else:
            print("Invalid choice, please try again.\n")

if __name__ == "__main__":
    main()
