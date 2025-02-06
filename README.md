import random

class Pet:
    def __init__(self, name, species):
        self.name = name
        self.species = species.lower()
        self.hunger = 50  # 0 - сыт, 100 - голоден
        self.energy = 50  # 0 - устал, 100 - бодр
        self.happiness = 50  # 0 - несчастлив, 100 - счастлив

    def eat(self):
        self.hunger = max(0, self.hunger - random.randint(10, 30))
        self.energy = min(100, self.energy + 10)
        print(f"{self.name} поел(а) и теперь сытый! Голод: {self.hunger}, Энергия: {self.energy}")

    def sleep(self):
        self.energy = min(100, self.energy + random.randint(20, 40))
        self.hunger = min(100, self.hunger + 10)
        print(f"{self.name} поспал(а) и теперь отдохнул(а)! Энергия: {self.energy}, Голод: {self.hunger}")

    def play(self):
        if self.energy > 20 and self.hunger < 80:
            self.happiness = min(100, self.happiness + random.randint(10, 20))
            self.energy = max(0, self.energy - 15)
            self.hunger = min(100, self.hunger + 10)
            print(f"{self.name} поиграл(а) и доволен! Счастье: {self.happiness}, Энергия: {self.energy}, Голод: {self.hunger}")
        else:
            print(f"{self.name} слишком устал(а) или голоден(а) для игры.")

    def status(self):
        print(f"{self.name} ({self.species.capitalize()}):\n  Счастье: {self.happiness}\n  Голод: {self.hunger}\n  Энергия: {self.energy}")

# Пример использования
pet = Pet("Барсик", "кот")
pet.status()
pet.eat()
pet.play()
pet.sleep()
pet.status()
