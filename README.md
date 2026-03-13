class Node:
    def __init__(self, data):
        self.data = data
        self.next = None

class Stack:
    def __init__(self):
        self.top = None

    def push(self, data):
        newnode = Node(data)
        newnode.next = self.top
        self.top = newnode

    def pop(self):
        if self.top == None:
            print("No pages to go back")
            return None
        temp = self.top
        self.top = self.top.next
        return temp.data

    def display(self):
        if self.top == None:
            print("Stack empty")
        else:
            temp = self.top
            print("Browser History:")
            while temp:
                print(temp.data)
                temp = temp.next

stack = Stack()
current_page = None

while True:
    print("\n1.Visit Page")
    print("2.Back")
    print("3.Display History")
    print("4.Exit")

    ch = int(raw_input("Enter choice: "))

    if ch == 1:
        page = raw_input("Enter page URL: ")
        if current_page:
            stack.push(current_page)
        current_page = page
        print("Current Page:", current_page)

    elif ch == 2:
        prev = stack.pop()
        if prev:
            current_page = prev
            print("Went back to:", current_page)

    elif ch == 3:
        stack.display()

    elif ch == 4:
        break# Stack-and-queue
output:
1.Visit Page
2.Back
3.Display History
4.Exit
Enter choice: 1
Enter page URL: google.com
Current Page: google.com

Enter choice: 1
Enter page URL: youtube.com
Current Page: youtube.com

Enter choice: 2
Went back to: google.com

Enter choice: 3
Browser History:
