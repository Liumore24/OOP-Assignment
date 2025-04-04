# OOP-Assignment

# Base class representing a generic Smartphone
class Smartphone:
    def __init__(self, brand, model, battery, storage, ram, media_density):
        self.brand = brand
        self.model = model
        # Using name mangling to simulate private attributes
        self.__battery = battery       # in mAh
        self.__storage = storage       # in GB
        self.__ram = ram               # in GB
        self.media_density = media_density  # e.g., for camera quality or display metric

    def display_specs(self):
        """Display the smartphone's specifications."""
        print(f"Smartphone Specs for {self.brand} {self.model}:")
        print(f"  Battery: {self.__battery} mAh")
        print(f"  Storage: {self.__storage} GB")
        print(f"  RAM: {self.__ram} GB")
        print(f"  Media Density: {self.media_density}")

    def update_battery(self, new_battery):
        """Update the battery capacity (e.g., after a battery upgrade)."""
        self.__battery = new_battery

# Subclass representing the specific Doogee V Max Pro
class DoogeeVMaxPro(Smartphone):
    def __init__(self, battery, storage, ram, media_density):
        # Initialize the Doogee V Max Pro with fixed brand/model values
        super().__init__("Doogee", "V Max Pro", battery, storage, ram, media_density)
    
    def battery_status(self):
        """
        Example method that might check battery health.
        Note: Using the mangled attribute name to access the private battery value.
        """
        # Accessing private variable from the parent class using _ClassName__variable
        if self._Smartphone__battery >= 22000:
            print("Battery is in excellent condition!")
        else:
            print("Battery might need some maintenance.")

# Create an instance of the DoogeeVMaxPro with the given specs:
# Battery: 22000 mAh, Storage: 512 GB, RAM: 12 GB, Media Density: 7800
my_phone = DoogeeVMaxPro(22000, 512, 12, 7800)
my_phone.display_specs()
my_phone.battery_status()

Polymorphism Challenge – Animal Movement
# Base class representing a generic Animal
class Animal:
    def move(self):
        # This method is intended to be overridden by subclasses
        raise NotImplementedError("Subclasses must implement this method")

# A Dog class that moves by running
class Dog(Animal):
    def move(self):
        print("Dog is running on four legs. 🐕‍🦺")

# A Bird class that moves by flying
class Bird(Animal):
    def move(self):
        print("Bird is flying gracefully in the sky. 🕊️")

# Testing polymorphism: both animals have a move() method that behaves differently.
animals = [Dog(), Bird()]
for animal in animals:
    animal.move()
