# Implement-a-Simple-Contact-Management-System
Implement a Simple Contact Management System
#include <stdio.h>
#include <string.h>
#include <stdlib.h>

// Define a structure to represent a contact
struct Contact {
    char name[100];
    char phone[20];
    char email[100];
};

// Function to add a new contact
void addContact(struct Contact *contacts, int *contactCount) {
    if (*contactCount < 100) {
        printf("Enter contact details:\n");
        printf("Name: ");
        scanf(" %[^\n]", contacts[*contactCount].name);
        printf("Phone: ");
        scanf(" %[^\n]", contacts[*contactCount].phone);
        printf("Email: ");
        scanf(" %[^\n]", contacts[*contactCount].email);
        (*contactCount)++;
        printf("Contact added successfully!\n");
    } else {
        printf("Contact list is full. Delete some contacts to make space.\n");
    }
}

// Function to display the contact list
void viewContacts(struct Contact *contacts, int contactCount) {
    printf("Contact List:\n");
    for (int i = 0; i < contactCount; i++) {
        printf("%d. Name: %s, Phone: %s, Email: %s\n", i + 1, contacts[i].name, contacts[i].phone, contacts[i].email);
    }
}

// Function to edit a contact
void editContact(struct Contact *contacts, int contactCount) {
    int contactIndex;
    printf("Enter the index of the contact you want to edit: ");
    scanf("%d", &contactIndex);
    if (contactIndex >= 1 && contactIndex <= contactCount) {
        printf("Enter new contact details:\n");
        printf("Name: ");
        scanf(" %[^\n]", contacts[contactIndex - 1].name);
        printf("Phone: ");
        scanf(" %[^\n]", contacts[contactIndex - 1].phone);
        printf("Email: ");
        scanf(" %[^\n]", contacts[contactIndex - 1].email);
        printf("Contact edited successfully!\n");
    } else {
        printf("Invalid contact index.\n");
    }
}

// Function to delete a contact
void deleteContact(struct Contact *contacts, int *contactCount) {
    int contactIndex;
    printf("Enter the index of the contact you want to delete: ");
    scanf("%d", &contactIndex);
    if (contactIndex >= 1 && contactIndex <= *contactCount) {
        for (int i = contactIndex - 1; i < *contactCount - 1; i++) {
            contacts[i] = contacts[i + 1];
        }
        (*contactCount)--;
        printf("Contact deleted successfully!\n");
    } else {
        printf("Invalid contact index.\n");
    }
}

int main() {
    struct Contact contacts[100];
    int contactCount = 0;
    int choice;

    while (1) {
        printf("\nContact Management System\n");
        printf("1. Add a new contact\n");
        printf("2. View contact list\n");
        printf("3. Edit a contact\n");
        printf("4. Delete a contact\n");
        printf("5. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch (choice) {
            case 1:
                addContact(contacts, &contactCount);
                break;
            case 2:
                viewContacts(contacts, contactCount);
                break;
            case 3:
                editContact(contacts, contactCount);
                break;
            case 4:
                deleteContact(contacts, &contactCount);
                break;
            case 5:
                exit(0);
            default:
                printf("Invalid choice. Please try again.\n");
        }
    }

    return 0;
}











