#include <stdio.h>
#include <stdlib.h>
#include <string.h>

#define MAX_SEATS 10

int seats[MAX_SEATS] = {0}; // 0 = Available, 1 = Booked

char *movies[] = {"1. Avengers: Endgame", "2. Inception", "3. The Dark Knight", "4. Interstellar"};
char *timings[] = {"10:00 AM", "1:00 PM", "4:00 PM", "7:00 PM"};

typedef struct Node {
    int ticket_id;
    char movie_name[50];
    char timing[20];
    int seat_number;
    struct Node* next;
} Node;

typedef struct Queue {
    Node* front;
    Node* rear;
    int size;
} Queue;

void initQueue(Queue* q);
int isFull(Queue* q);
int isEmpty(Queue* q);
void bookTicket(Queue* q, int ticket_id);
void cancelTicket(Queue* q, int ticket_id);
void viewBookings(Queue* q);
void viewAvailableSeats();

void initQueue(Queue* q) {
    q->front = q->rear = NULL;
    q->size = 0;
}

int isFull(Queue* q) {
    return q->size >= MAX_SEATS;
}

int isEmpty(Queue* q) {
    return q->size == 0;
}

void bookTicket(Queue* q, int ticket_id) {
    if (isFull(q)) {
        printf("All seats are booked!\n");
        return;
    }
    int movie_choice, time_choice, seat_choice;
    printf("Available Movies:\n");
    for (int i = 0; i < 4; i++) {
        printf("%s\n", movies[i]);
    }
    printf("Select Movie (1-4): ");
    scanf("%d", &movie_choice);
    getchar();
    if (movie_choice < 1 || movie_choice > 4) {
        printf("Invalid selection!\n");
        return;
    }

    printf("Available Timings:\n");
    for (int i = 0; i < 4; i++) {
        printf("%d. %s\n", i + 1, timings[i]);
    }
    printf("Select Timing (1-4): ");
    scanf("%d", &time_choice);
    getchar();
    if (time_choice < 1 || time_choice > 4) {
        printf("Invalid selection!\n");
        return;
    }

    viewAvailableSeats();
    printf("Select Seat Number: ");
    scanf("%d", &seat_choice);
    getchar();
    if (seat_choice < 1 || seat_choice > MAX_SEATS || seats[seat_choice - 1] == 1) {
        printf("Invalid or already booked seat!\n");
        return;
    }
    
    seats[seat_choice - 1] = 1;
    Node* newNode = (Node*)malloc(sizeof(Node));
    newNode->ticket_id = ticket_id;
    strcpy(newNode->movie_name, movies[movie_choice - 1]);
    strcpy(newNode->timing, timings[time_choice - 1]);
    newNode->seat_number = seat_choice;
    newNode->next = NULL;

    if (isEmpty(q)) {
        q->front = q->rear = newNode;
    } else {
        q->rear->next = newNode;
        q->rear = newNode;
    }
    q->size++;
    printf("\n===================================\n");
    printf("         BOOKING RECEIPT\n");
    printf("===================================\n");
    printf("Ticket ID   : %d\n", ticket_id);
    printf("Movie       : %s\n", newNode->movie_name);
    printf("Timing      : %s\n", newNode->timing);
    printf("Seat Number : %d\n", newNode->seat_number);
    printf("===================================\n");
    printf("Please check your receipt before leaving!\n");
}

void cancelTicket(Queue* q, int ticket_id) {
    if (isEmpty(q)) {
        printf("No bookings available to cancel!\n");
        return;
    }
    Node *temp = q->front, *prev = NULL;
    while (temp != NULL && temp->ticket_id != ticket_id) {
        prev = temp;
        temp = temp->next;
    }
    if (temp == NULL) {
        printf("Invalid Ticket ID!\n");
        return;
    }
    
    if (prev == NULL) {
        q->front = temp->next;
    } else {
        prev->next = temp->next;
    }
    if (temp == q->rear) {
        q->rear = prev;
    }
    seats[temp->seat_number - 1] = 0;
    free(temp);
    q->size--;
    printf("Ticket Canceled Successfully!\n");
}

void viewBookings(Queue* q) {
    if (isEmpty(q)) {
        printf("No bookings available!\n");
        return;
    }
    printf("\nCurrent Bookings:\n");
    Node* temp = q->front;
    while (temp != NULL) {
        printf("Ticket ID: %d | Movie: %s | Timing: %s | Seat: %d\n", temp->ticket_id, temp->movie_name, temp->timing, temp->seat_number);
        temp = temp->next;
    }
}

void viewAvailableSeats() {
    printf("Available Seats: ");
    for (int i = 0; i < MAX_SEATS; i++) {
        if (seats[i] == 0) {
            printf("%d ", i + 1);
        }
    }
    printf("\n");
}

int main() {
    Queue ticketQueue;
    initQueue(&ticketQueue);
    int choice, id = 1, ticket_id;

    printf("======================================\n");
    printf("        WELCOME TO MOVIE BOOKING\n");
    printf("======================================\n");
    
    do {
        printf("\nTicket Booking System\n");
        printf("1. Book Ticket\n");
        printf("2. Cancel Ticket\n");
        printf("3. View Bookings\n");
        printf("4. View Available Seats\n");
        printf("5. Exit\n");
        printf("Enter choice: ");
        scanf("%d", &choice);
        getchar();
        switch (choice) {
            case 1:
                bookTicket(&ticketQueue, id++);
                break;
            case 2:
                printf("Enter Ticket ID to cancel: ");
                scanf("%d", &ticket_id);
                getchar();
                cancelTicket(&ticketQueue, ticket_id);
                break;
            case 3:
                viewBookings(&ticketQueue);
                break;
            case 4:
                viewAvailableSeats();
                break;
            case 5:
                printf("Exiting...\n");
                break;
            default:
                printf("Invalid choice!\n");
        }
    } while (choice != 5);
    
    return 0;
}
