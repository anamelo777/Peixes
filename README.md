# Peixes
Vendo Peixes a partir de 40 reais o quilo.
# fish_shop.py

class FishShop:
    def __init__(self):
        self.fish_inventory = {
            "Salmão": 40,
            "Truta": 45,
            "Atum": 50,
            "Tilápia": 42
        }
        self.cart = {}

    def show_fish_inventory(self):
        print("\n--- Estoque de Peixes ---")
        for fish, price in self.fish_inventory.items():
            print(f"{fish}: R${price}/kg")

    def add_to_cart(self, fish, quantity):
        if fish in self.fish_inventory:
            if fish not in self.cart:
                self.cart[fish] = 0
            self.cart[fish] += quantity
            print(f"Adicionado {quantity} kg de {fish} ao carrinho.")
        else:
            print("Peixe não disponível.")

    def calculate_total(self):
        total = 0
        for fish, quantity in self.cart.items():
            total += self.fish_inventory[fish] * quantity
        return total

    def checkout(self):
        total = self.calculate_total()
        print("\n--- Resumo do Pedido ---")
        for fish, quantity in self.cart.items():
            print(f"{fish}: {quantity} kg")
        print(f"Total: R${total:.2f}")

def main():
    shop = FishShop()
    print("Bem-vindo à Loja de Peixes!")

    while True:
        shop.show_fish_inventory()
        
        choice = input("\nDeseja adicionar algum peixe ao carrinho? (sim/não): ").lower()
        if choice == "sim":
            fish = input("Escolha o peixe (nome): ").capitalize()
            quantity = float(input(f"Quantos kg de {fish} deseja comprar? "))
            shop.add_to_cart(fish, quantity)
        else:
            break
    
    shop.checkout()

if __name__ == "__main__":
    main()
