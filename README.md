import csv

class Item:
    def __init__(self, name, price, stock):
        self.name = name
        self.price = price
        self.stock = stock

    def __str__(self):
        return f"{self.name} - Price: {self.price}, Stock: {self.stock}"

class Inventory:
    def __init__(self):
        self.items = {}

    def add_item(self, name, price, stock):
        if name in self.items:
            self.items[name].stock += stock
        else:
            self.items[name] = Item(name, price, stock)
        print(f"Added {stock} of {name} to inventory.")

    def remove_item(self, name, stock):
        if name in self.items:
            if self.items[name].stock >= stock:
                self.items[name].stock -= stock
                print(f"Removed {stock} of {name} from inventory.")
                if self.items[name].stock == 0:
                    del self.items[name]
            else:
                print(f"Not enough stock to remove {stock} of {name}.")
        else:
            print(f"{name} not found in inventory.")

    def check_low_stock(self, threshold):
        low_stock_items = [item for item in self.items.values() if item.stock < threshold]
        return low_stock_items

    def total_inventory_value(self):
        total_value = sum(item.price * item.stock for item in self.items.values())
        return total_value

    def record_sale(self, name, stock):
        if name in self.items:
            if self.items[name].stock >= stock:
                self.items[name].stock -= stock
                print(f"Sold {stock} of {name}.")
                if self.items[name].stock == 0:
                    del self.items[name]
            else:
                print(f"Not enough stock to sell {stock} of {name}.")
        else:
            print(f"{name} not found in inventory.")

    def export_inventory(self, filename):
        with open(filename, mode='w', newline='') as file:
            writer = csv.writer(file)
            writer.writerow(['Name', 'Price', 'Stock'])
            for item in self.items.values():
                writer.writerow([item.name, item.price, item.stock])
        print(f"Inventory exported to {filename}.")


if __name__ == "__main__":
    inventory = Inventory()

    # Menambah item
    inventory.add_item("Laptop", 1000, 10)
    inventory.add_item("Mouse", 20, 50)
    inventory.add_item("Keyboard", 30, 20)

    # Mengurangi stok
    inventory.remove_item("Mouse", 5)

    # Peringatan stok rendah
    low_stock_items = inventory.check_low_stock(10)
    if low_stock_items:
        print("Low stock items:")
        for item in low_stock_items:
            print(item)

    # Menghitung total nilai barang
    total_value = inventory.total_inventory_value()
    print(f"Total inventory value: {total_value}")

    # Mencatat laporan penjualan
    inventory.record_sale("Laptop", 2)

    # Mengekspor data inventaris
    inventory.export_inventory("inventory.csv")
import csv

class Item:
    def __init__(self, name, price, stock):
        self.name = name
        self.price = price
        self.stock = stock

    def __str__(self):
        return f"{self.name} - Price: {self.price}, Stock: {self.stock}"

class Inventory:
    def __init__(self):
        self.items = {}

    def add_item(self, name, price, stock):
        if name in self.items:
            self.items[name].stock += stock
        else:
            self.items[name] = Item(name, price, stock)
        print(f"Added {stock} of {name} to inventory.")

    def remove_item(self, name, stock):
        if name in self.items:
            if self.items[name].stock >= stock:
                self.items[name].stock -= stock
                print(f"Removed {stock} of {name} from inventory.")
                if self.items[name].stock == 0:
                    del self.items[name]
            else:
                print(f"Not enough stock to remove {stock} of {name}.")
        else:
            print(f"{name} not found in inventory.")

    def check_low_stock(self, threshold):
        low_stock_items = [item for item in self.items.values() if item.stock < threshold]
        return low_stock_items

    def total_inventory_value(self):
        total_value = sum(item.price * item.stock for item in self.items.values())
        return total_value

    def record_sale(self, name, stock):
        if name in self.items:
            if self.items[name].stock >= stock:
                self.items[name].stock -= stock
                print(f"Sold {stock} of {name}.")
                if self.items[name].stock == 0:
                    del self.items[name]
            else:
                print(f"Not enough stock to sell {stock} of {name}.")
        else:
            print(f"{name} not found in inventory.")

    def export_inventory(self, filename):
        with open(filename, mode='w', newline='') as file:
            writer = csv.writer(file)
            writer.writerow(['Name', 'Price', 'Stock'])
            for item in self.items.values():
                writer.writerow([item.name, item.price, item.stock])
        print(f"Inventory exported to {filename}.")


if __name__ == "__main__":
    inventory = Inventory()

    # Menambah item
    inventory.add_item("Laptop", 1000, 10)
    inventory.add_item("Mouse", 20, 50)
    inventory.add_item("Keyboard", 30, 20)

    # Mengurangi stok
    inventory.remove_item("Mouse", 5)

    # Peringatan stok rendah
    low_stock_items = inventory.check_low_stock(10)
    if low_stock_items:
        print("Low stock items:")
        for item in low_stock_items:
            print(item)

    # Menghitung total nilai barang
    total_value = inventory.total_inventory_value()
    print(f"Total inventory value: {total_value}")

    # Mencatat laporan penjualan
    inventory.record_sale("Laptop", 2)

    # Mengekspor data inventaris
    inventory.export_inventory("inventory.csv")
