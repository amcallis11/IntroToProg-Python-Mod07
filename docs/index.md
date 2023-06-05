## Python Code Guide

### Importing Modules
```python
import pickle
```
The code begins by importing the `pickle` module, which will allow us to save more complex data structures like lists and dictionaries to a binary file. Binary files are not readable by humans, and they are more efficient at storing and transferring data than text files. 

### Initializing Variables
The code adds starting values for several variables to maintain consistency in the code, prevent naming errors later in the code, and keep the code organized.
```python
file = "Client_fees.dat"  # File name for storing client data
choice = None  # User menu choice
dicRow = {}  # Dictionary row
lstTable = []  # List of dictionary rows
```
The code initializes several variables:
- `file`: Represents the file name for storing client data.
- `choice`: Holds the user's menu choice.
- `dicRow`: Represents a dictionary row.
- `lstTable`: Stores a list of dictionary rows.

### Getting User Data
```python
while True:
    client = input("Who is the client? ").strip()
    media = input("What is the media type? ").strip()
    
    while True:
        try:
            fee = float(input("What is the fee ($Total Dollars)? "))
            break
        except ValueError:
            print("Oops. Please enter a valid fee as a number.")

    dicRow = {"ClientName": client, "MediaType": media, "Fee": fee}
    lstTable.append(dicRow)
    
    choice = input("Do you want to enter data for another client? (yes/no): ").lower().strip()
    if choice != "yes":
        break
```
The code enters a loop to get user data for the dictionary. It repeatedly prompts the user for client information:
1. The user is asked to provide the client's name and media type.
2. Inside a nested loop, the code attempts to convert the user's input for the fee into a floating-point number.
3. To handle potential errors when converting the user's input to a float, a try-except block is used.
4. If the conversion succeeds, the fee is stored in the `fee` variable.
5. If a `ValueError` is raised during the conversion, indicating that the user entered an invalid fee, the except block is executed.
6. The loop continues until the user enters a valid fee, at which point it breaks out of the inner loop and proceeds to store the client's information.
7. To add multiple rows of data, the user is asked if they want to continue or finish entering data. If the user chooses not to enter more data, the loop breaks.

### Writing Data to a File
```python
objFile = open(file, "wb")
pickle.dump(lstTable, objFile)
objFile.close()
```
The code opens the file in write mode using the open() function and the "wb" mode (binary write). It then uses pickle.dump() to write the list of dictionary rows (lstTable) to the file in a .dat file. Finally, the file is closed using the close() method.

### Reading Data from a File
```python
objFile = open(file, "rb")
objFileData = pickle.load(objFile)
objFile.close()
```
The code opens the file specified earlier in read mode using the open() function and the "rb" mode (binary read). It uses pickle.load() to read the contents of the file and load them into the variable objFileData. The file is then closed using the close() method.

### Printing the Read Data
```python
print(objFileData)
```
The code prints the contents of `objFileData`, which represents the data read from the file.

We're done!


