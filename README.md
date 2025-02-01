# Linked_list
#include<stdio.h>
   #include<stdlib.h
   struct Node
   {
          int data;
          struct Node *next;
  };
 
  struct Node* create_node(int data);
  void insert_begin(struct Node** head, int data);
 void insert_end(struct Node** head, int data);
  void delete_node(struct Node** head, int key);
  void traversal_list(struct Node* head);
  int main()
  {
          struct Node* head = NULL;
          insert_begin(&head,10);
          insert_begin(&head, 20);
          insert_end(&head, 30);
          printf("Linked list after insertion: ");
         traversal_list(head);
          delete_node(&head,20);
          printf("Linked list after deletion: ");
          traversal_list(head);
          return 0;
  }
struct Node* create_node(int data)
  {
         struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
          if(!newNode)
          {
                printf("Memory allocation failed.\n");
                 exit(1);
         }
          newNode->data = data;
         newNode->next = NULL;
          return newNode;
  }

  void insert_begin(struct Node** head,int data)
  {
          struct Node* newNode = create_node(data);
          if(*head == NULL)
          {
                  *head = newNode;
                  return;
         }
          struct Node* temp = *head;
         while(temp->next != NULL)
          {
                  temp=temp->next;
         }
         temp->next = newNode;
  }
void insert_end(struct Node** head, int data)
  {
          struct Node* newNode = create_node(data);
          if(*head == NULL)
          {
                  *head = newNode;
                  return;
          }
          struct Node* temp = *head;
          while(temp->next != NULL)
          {
                  temp = temp->next;
          }
          temp->next = newNode;
  }
void delete_node(struct Node** head,int key)
  {
          struct Node* temp = *head;
          struct Node* prev = NULL;
         if(temp != NULL && temp->data == key)
          {
                 *head = temp->next;
                  free(temp);
                  return;
          }
         while(temp != NULL && temp->data != key)
          {
                  prev = temp;
                 temp = temp->next;
         }
          if(temp == NULL)
          {
                 printf("Key not found in the list.\n");
                 return;
          }
          prev->next = temp->next;
          free(temp);
 }
 void traversal_list(struct Node* head)
{
        struct Node* temp = head;
         while(temp != NULL)
         {
                 printf("%d ->",temp->data);
                 temp = temp->next;
         }
         printf("NULL\n");
 }

