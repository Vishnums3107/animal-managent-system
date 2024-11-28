# animal-managent-system
Creating an animal management system in C involves designing a program that can handle various animal-related data, such as storing information about different animals, adding new animals, listing animals, and possibly managing their details.
#include <stdio.h>
#include <string.h>

#define MAX_ANIMALS 100
#define MAX_NAME_LEN 50
#define MAX_SPECIES_LEN 30

// Define a struct for Animal
typedef struct {
    char name[MAX_NAME_LEN];
    char species[MAX_SPECIES_LEN];
    int age;
} Animal;

// Declare a global array of Animal objects
Animal animals[MAX_ANIMALS];
int numAnimals = 0;

// Function to add an animal
void addAnimal() {
    if (numAnimals < MAX_ANIMALS) {
        printf("Enter animal's name: ");
        scanf(" %[^\n]", animals[numAnimals].name);  // Read string with spaces
        printf("Enter animal's species: ");
        scanf(" %[^\n]", animals[numAnimals].species);
        printf("Enter animal's age: ");
        scanf("%d", &animals[numAnimals].age);
        numAnimals++;
        printf("Animal added successfully!\n\n");
    } else {
        printf("Error: Animal database is full!\n\n");
    }
}

// Function to list all animals
void listAnimals() {
    if (numAnimals == 0) {
        printf("No animals in the system!\n\n");
    } else {
        printf("Listing all animals:\n");
        for (int i = 0; i < numAnimals; i++) {
            printf("Animal %d\n", i + 1);
            printf("Name: %s\n", animals[i].name);
            printf("Species: %s\n", animals[i].species);
            printf("Age: %d\n\n", animals[i].age);
        }
    }
}

// Function to search for an animal by name
void searchAnimal() {
    char searchName[MAX_NAME_LEN];
    printf("Enter the animal name to search: ");
    scanf(" %[^\n]", searchName);

    int found = 0;
    for (int i = 0; i < numAnimals; i++) {
        if (strcmp(animals[i].name, searchName) == 0) {
            printf("Animal found!\n");
            printf("Name: %s\n", animals[i].name);
            printf("Species: %s\n", animals[i].species);
            printf("Age: %d\n\n", animals[i].age);
            found = 1;
            break;
        }
    }
    if (!found) {
        printf("Animal with name %s not found.\n\n", searchName);
    }
}

// Function to display the menu
void displayMenu() {
    printf("===== Animal Management System =====\n");
    printf("1. Add animal\n");
    printf("2. List all animals\n");
    printf("3. Search for an animal\n");
    printf("4. Exit\n");
    printf("Enter your choice: ");
}

int main() {
    int choice;

    // Run the program until the user chooses to exit
    while (1) {
        displayMenu();
        scanf("%d", &choice);

        switch (choice) {
            case 1:
                addAnimal();
                break;
            case 2:
                listAnimals();
                break;
            case 3:
                searchAnimal();
                break;
            case 4:
                printf("Exiting the system. Goodbye!\n");
                return 0;
            default:
                printf("Invalid choice! Please try again.\n\n");
        }
    }

    return 0;
}
