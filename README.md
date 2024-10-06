#include <stdio.h>
#include <stdlib.h>
#include <string.h>

#define MAX_CONTACTS 100

// Structure to store contact details
typedef struct {
    char name[50];
    char phone[15];
    char email[50];
} Contact;

// Global array to store contacts
Contact contacts[MAX_CONTACTS];
int contactCount = 0;

// Function to add a new contact
void addContact() {
    if (contactCount < MAX_CONTACTS) {
        printf("Enter Name: ");
        scanf("%s", contacts[contactCount].name);
        printf("Enter Phone: ");
        scanf("%s", contacts[contactCount].phone);
        printf("Enter Email: ");
        scanf("%s", contacts[contactCount].email);
        contactCount++;
        printf("Contact added successfully!\n");
    } else {
        printf("Contact list is full!\n");
    }
}

// Function to display all contacts
void displayContacts() {
    if (contactCount == 0) {
        printf("No contacts available.\n");
        return;
    }
    printf("\nContacts List:\n");
    for (int i = 0; i < contactCount; i++) {
        printf("Name: %s\n", contacts[i].name);
        printf("Phone: %s\n", contacts[i].phone);
        printf("Email: %s\n", contacts[i].email);
        printf("------------------------\n");
    }
}

// Function to search for a contact by name
void searchContact() {
    char name[50];
    printf("Enter name to search: ");
    scanf("%s", name);
    int found = 0;
    for (int i = 0; i < contactCount; i++) {
        if (strcmp(contacts[i].name, name) == 0) {
            printf("Contact Found:\n");
            printf("Name: %s\n", contacts[i].name);
            printf("Phone: %s\n", contacts[i].phone);
            printf("Email: %s\n", contacts[i].email);
            found = 1;
            break;
        }
    }
    if (!found) {
        printf("Contact not found.\n");
    }
}

// Function to update contact details by name
void updateContact() {
    char name[50];
    printf("Enter the name of the contact to update: ");
    scanf("%s", name);
    int found = 0;
    for (int i = 0; i < contactCount; i++) {
        if (strcmp(contacts[i].name, name) == 0) {
            printf("Updating contact:\n");
            printf("Enter new phone: ");
            scanf("%s", contacts[i].phone);
            printf("Enter new email: ");
            scanf("%s", contacts[i].email);
            printf("Contact updated successfully!\n");
            found = 1;
            break;
        }
    }
    if (!found) {
        printf("Contact not found.\n");
    }
}

// Function to delete a contact by name
void deleteContact() {
    char name[50];
    printf("Enter the name of the contact to delete: ");
    scanf("%s", name);
    int found = 0;
    for (int i = 0; i < contactCount; i++) {
        if (strcmp(contacts[i].name, name) == 0) {
            found = 1;
            for (int j = i; j < contactCount - 1; j++) {
                contacts[j] = contacts[j + 1];
            }
            contactCount--;
            printf("Contact deleted successfully!\n");
            break;
        }
    }
    if (!found) {
        printf("Contact not found.\n");
    }
}

// Main menu function
void menu() {
    int choice;
    do {
        printf("\n***** CONTACT MANAGEMENT SYSTEM *****\n");
        printf("1. Add Contact\n");
        printf("2. Display Contacts\n");
        printf("3. Search Contact\n");
        printf("4. Update Contact\n");
        printf("5. Delete Contact\n");
        printf("6. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch (choice) {
            case 1:
                addContact();
                break;
            case 2:
                displayContacts();
                break;
            case 3:
                searchContact();
                break;
            case 4:
                updateContact();
                break;
            case 5:
                deleteContact();
                break;
            case 6:
                printf("Exited...\n");
                break;
            default:
                printf("Invalid choice! Try again.\n");
        }
    } while (choice != 6);
}

int main() {
    menu();
    return 0;
}
