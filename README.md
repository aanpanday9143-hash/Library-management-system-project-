# Library-management-system-project-
include <stdio.h>
#include <string.h>
#define MAX_BOOKS 100
typedef struct {
 int id;
 char title[100];
 char author[100];
 int available; /* 1 = available, 0 = issued */
} Book;
Book books[MAX_BOOKS];
int bookCount = 0;
/* Linear search: O(n) */
int findBook(int id) {
 for (int i = 0; i < bookCount; i++) {
 if (books[i].id == id) return i;
 }
 return -1;
}
void addBook(void) {
 if (bookCount >= MAX_BOOKS) {
 printf("Library is full.\\n");
 return;
 }
 Book b;
 printf("Enter book ID: ");
 if (scanf("%d", &b.id) != 1) return;
 if (findBook(b.id) != -1) {
 printf("A book with this ID already exists.\\n");
 return;
 }
 printf("Enter title (one word): ");
 scanf("%99s", b.title);
 printf("Enter author (one word): ");
 scanf("%99s", b.author);
 b.available = 1;
 books[bookCount++] = b;
 printf("Book added successfully.\\n");
void displayBooks(void) {
 if (bookCount == 0) {
 printf("No books in the library.\\n");
 return;
 }
 printf("\\nID\\tTitle\\tAuthor\\tStatus\\n");
 for (int i = 0; i < bookCount; i++) {
 printf("%d\\t%s\\t%s\\t%s\\n",
 books[i].id, books[i].title, books[i].author,
 books[i].available ? "Available" : "Issued");
 }
}
void searchBook(void) {
 int id;
 printf("Enter book ID to search: ");
 if (scanf("%d", &id) != 1) return;
 int index = findBook(id);
 if (index == -1) {
 printf("Book not found.\\n");
 } else {
 printf("Found: ID=%d, Title=%s, Author=%s, Status=%s\\n",
 books[index].id, books[index].title, books[index].author,
 books[index].available ? "Available" : "Issued");
 }
}
void issueBook(void) {
 int id;
 printf("Enter book ID to issue: ");
 if (scanf("%d", &id) != 1) return;
 int index = findBook(id);
 if (index == -1) {
 printf("Book not found.\\n");
 } else if (!books[index].available) {
 printf("This book is already issued.\\n");
 } else {
 books[index].available = 0;
 printf("Book issued successfully.\\n");
 }
}
void returnBook(void) {
 int id;
 printf("Enter book ID to return: ");
 if (scanf("%d", &id) != 1) return;
 int index = findBook(id);
 if (index == -1) {
 printf("Book not found.\\n");
 } else if (books[index].available) {
 printf("This book was not issued.\\n");
 } else {
 books[index].available = 1;
 printf("Book returned successfully.\\n");
 }
}
int main(void) {
 int choice;
 do {
 printf("\\n===== LIBRARY MANAGEMENT SYSTEM =====\\n");
 printf("1. Add book\\n");
 printf("2. Display all books\\n");
 printf("3. Search book by ID\\n");
 printf("4. Issue book\\n");
 printf("5. Return book\\n");
 printf("0. Exit\\n");
 printf("Enter choice: ");
 if (scanf("%d", &choice) != 1) {
 printf("Invalid input. Exiting.\\n");
 break;
 }
 switch (choice) {
 case 1: addBook(); break;
 case 2: displayBooks(); break;
 case 3: searchBook(); break;
 case 4: issueBook(); break;
 case 5: returnBook(); break;
 case 0: printf("Thank you for using the system.\\n"); break;
 default: printf("Invalid choice. Try again.\\n");
 }
 } while (choice != 0);
 return 0;
