# DS-16
DS code
#include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node *left, *right;
};

struct Node* createNode(int data) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = data;
    newNode->left = newNode->right = NULL;
    return newNode;
}

struct Node* insert(struct Node* root, int data) {
    if (root == NULL) return createNode(data);
    if (data < root->data)
        root->left = insert(root->left, data);
    else if (data > root->data)
        root->right = insert(root->right, data);
    return root;
}

struct Node* findMin(struct Node* root) {
    if (root == NULL) return NULL;
    while (root->left) root = root->left;
    return root;
}

struct Node* findMax(struct Node* root) {
    if (root == NULL) return NULL;
    while (root->right) root = root->right;
    return root;
}

int main() {
    struct Node* root = NULL;
    int n, val;
    printf("Enter number of nodes: ");
    scanf("%d", &n);
    for (int i = 0; i < n; i++) {
        printf("Enter value: ");
        scanf("%d", &val);
        root = insert(root, val);
    }
    struct Node* minNode = findMin(root);
    struct Node* maxNode = findMax(root);
    if (minNode) printf("Minimum element: %d\n", minNode->data);
    if (maxNode) printf("Maximum element: %d\n", maxNode->data);
    return 0;
}
