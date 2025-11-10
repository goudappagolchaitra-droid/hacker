class Village:
    def __init__(self, name, location_x, location_y, population=0):
        """
        Initializes a Village object.

        Args:
            name (str): The name of the village.
            location_x (int): The X-coordinate of the village's location.
            location_y (int): The Y-coordinate of the village's location.
            population (int): The initial population of the village.
        """
        self.name = name
        self.location = (location_x, location_y)
        self.population = population
        self.buildings = []  # To store buildings within the village
        self.resources = {}  # To store resources available in the village

    def add_population(self, number):
        """Adds to the village's population."""
        self.population += number
        print(f"{number} people moved to {self.name}. New population: {self.population}")

    def remove_population(self, number):
        """Removes from the village's population."""
        if self.population >= number:
            self.population -= number
            print(f"{number} people left {self.name}. New population: {self.population}")
        else:
            print(f"Cannot remove {number} people; only {self.population} remain in {self.name}.")

    def add_building(self, building_name):
        """Adds a building to the village."""
        self.buildings.append(building_name)
        print(f"A new {building_name} was built in {self.name}.")

    def gather_resource(self, resource_type, quantity):
        """Gathers a specified resource."""
        self.resources[resource_type] = self.resources.get(resource_type, 0) + quantity
        print(f"{quantity} units of {resource_type} gathered in {self.name}.")

    def __str__(self):
        """Returns a string representation of the Village object."""
        return (f"Village: {self.name}\n"
                f"Location: {self.location}\n"
                f"Population: {self.population}\n"
                f"Buildings: {', '.join(self.buildings) if self.buildings else 'None'}\n"
                f"Resources: {self.resources}")

# Example Usage:
if __name__ == "__main__":
    village1 = Village("Greenville", 10, 20, 100)
    print(village1)

    village1.add_population(50)
    village1.add_building("Town Hall")
    village1.add_building("Farm")
    village1.gather_resource("Wood", 200)
    village1.gather_resource("Food", 500)
    print("\nAfter updates:")
    print(village1)

    village1.remove_population(20)
    print("\nAfter population decrease:")
    print(village1)
