# deletenode-recursively
#include<iostream>
using namespace std;
class node {
public:
	int data;
	node* next;

	node(int data) {
		this->data = data;
		next = NULL;
	}

};
node* takeinput();
void print(node* head);
node* deleterecurse(node* head, int i);
int main()
{
	node* head = takeinput();
	print(head);
	int i, data;
	cin >> i;
	head = deleterecurse(head, i);
	print(head);
}
node* takeinput()
{
	int data;
	cin >> data;
	node* head = NULL;
	node* tail = NULL;
	while (data != -1)
	{
		node* newnode = new node(data);
		if (head == NULL)
		{
			head = newnode;
			tail = newnode;

		}
		else
		{
			tail->next = newnode;
			tail = tail->next;
		}
		cin >> data;
	}
	return head;
}
void print(node* head)
{
	node* temp = head;
	while (temp != NULL)
	{
		cout << temp->data<<" ";
		temp = temp->next;
	}
}

node* deleterecurse(node* head, int i)
{
	if (head == 0)
	{
		return NULL;
	}
	if (i == 0) //ye apna 0th element wala case hogya
	{
		node* temp = head;
		head = temp->next;
		delete temp;
		return head;
	}
	if (i == 1)
	{
		node* temp = head->next;
		head->next = temp->next;
		temp->next = NULL;
		delete temp;
		return head;

	}
	node* x = deleterecurse(head->next, i - 1);
	return head;
}
