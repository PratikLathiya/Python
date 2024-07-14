# Library Management - Python Mini Project
### Creat a library class
### display a book
### lend book - (who owns the book if not present)
### add book
### return book

### pm = Library(listofbooks, library_name)

### dictionary (books-nameofperson)

### create a main function and run an infinite while loop asking
### users for their input

class Library:
    def __init__(self, list, name):
        self.booklist = list
        self.name = name
        self.lenddict = {}

    def displaybooks(self):
        print(f"we have following books in our library: {self.name}")
        for book in self.booklist:
            print(book)

    def lendbook(self, user, book):
        if book not in self.lenddict.keys():
            self.lenddict.update({book:user})
            print("Lender-Book database has been updated. You can take the book now")
        else:
            print(f"Book is already being used by {self.lenddict[book]}")

    def addbook(self, book):
        self.booklist.append(book)
        print("Book has been added to the book list")
    
    def returnbook(self, book):
        self.lenddict.pop(book)
    
if __name__ == '__main__':
    pm = Library(['Python', 'Rich Daddy Poor Daddy', 'Harry Potter', 'C++ Basics', 'Algorithms by CLRS'], "codewithpratik")

    while(True):
        print(f"Welcome to the {pm.name} library. Enter your choiceto continue")
        print(f"1. Display Books")
        print(f"2. Lend a Book")
        print(f"3. Add a Book")
        print(f"4. Return a Book")
        user_choice = input()
        if user_choice not in ['1', '2', '3', '4']:
            print("Please enter a valid option")
            continue

        else:
            user_choice = int(user_choice)
        
        if user_choice == 1:
            pm.displaybooks()

        elif user_choice == 2:
            book = input("Enter the name of book you want to lend: ")
            user = input("Enter your name: ")
            pm.lendbook(user, book)

        elif user_choice == 3:
            book = input("Enter the name of book you want to add: ")
            pm.addbook(book)

        elif user_choice == 4:
            book = input("Enter the name of book you want to return: ")
            pm.returnbook(book)

        else:
            print("Not a valid option")

        print("Press q to quit and c to continue")
        user_choice2 = ""
        while(user_choice2 != "c" and user_choice2 != "q"):
            user_choice2 = input()
            if user_choice2 == "q":
                exit()
            elif user_choice2 == "c":
                continue 
### correction __init__, __main__, __name_
