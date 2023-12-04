# dobby
--------------------String Operation----------------------------------------------------------------------------------------------------------------------------------
import java.util.*;
class stringoperations
{
    public static void main(String args[])
    {
        Scanner S= new Scanner(System.in);
        System.out.println("Enter 2 Strings: ");
        String a= S.next();
        String b= S.next();
        String c= a+" "+b;
// 1. Concat
        System.out.println(c);

// 2. Compare
        if(a==b)
        {
            System.out.println("Both Strings are equal and same");
        }
        else
        {
            System.out.println("Both are different");
        }
// 3. Length
        int x= c.length();
        System.out.println("Length of String is: "+x);
// 4. Reverse
        char ch[]= c.toCharArray();
        char rev[]= new char[x];
        int d=0;
        for(int i=x-1;i>=0;i--)
        {
            rev[d] = ch[i];
            d++;
        }
        System.out.print("Reverse String is: ");
        System.out.println(rev);
// 5. Copy
        String e= c;
        System.out.print("Copy of original string: "+e);
    }
}

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

-----------------------------------------sparse matrix simple and fast transpose----------------------------------------------------------------------------------------------
import java.util.Scanner;

class SparseMatrix {
    private int[][] matrix;
    private int numRows;
    private int numCols;
    private int numNonZeroElements;

    public SparseMatrix(int numRows, int numCols) {
        this.numRows = numRows;
        this.numCols = numCols;
        matrix = new int[numRows][numCols];
        numNonZeroElements = 0;
    }

    public void readMatrix() {
        Scanner scanner = new Scanner(System.in);
        System.out.println("Enter the elements of the matrix:");
        for (int i = 0; i < numRows; i++) {
            for (int j = 0; j < numCols; j++) {
                matrix[i][j] = scanner.nextInt();
                if (matrix[i][j] != 0) {
                    numNonZeroElements++;
                }
            }
        }
    }

    public void displaySparseMatrix() {
        System.out.println("Sparse Matrix:");
        System.out.println("Row\tColumn\tValue");
        for (int i = 0; i < numRows; i++) {
            for (int j = 0; j < numCols; j++) {
                if (matrix[i][j] != 0) {
                    System.out.println(i + "\t" + j + "\t" + matrix[i][j]);
                }
            }
        }
    }

    public SparseMatrix simpleTranspose() {
        SparseMatrix transposedMatrix = new SparseMatrix(numCols, numRows);

        for (int i = 0; i < numRows; i++) {
            for (int j = 0; j < numCols; j++) {
                if (matrix[i][j] != 0) {
                    transposedMatrix.matrix[j][i] = matrix[i][j];
                }
            }
        }

        return transposedMatrix;
    }

    public SparseMatrix fastTranspose() {
        SparseMatrix transposedMatrix = new SparseMatrix(numCols, numRows);
        int[] rowTerms = new int[numCols];
        int[] startingPosition = new int[numCols];

        for (int i = 0; i < numRows; i++) {
            for (int j = 0; j < numCols; j++) {
                if (matrix[i][j] != 0) {
                    rowTerms[j]++;
                }
            }
        }

        startingPosition[0] = 0;
        for (int i = 1; i < numCols; i++) {
            startingPosition[i] = startingPosition[i - 1] + rowTerms[i - 1];
        }

        for (int i = 0; i < numRows; i++) {
            for (int j = 0; j < numCols; j++) {
                if (matrix[i][j] != 0) {
                    int pos = startingPosition[j]++;
                    transposedMatrix.matrix[j][pos] = matrix[i][j];
                }
            }
        }

        return transposedMatrix;
    }
}

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter the number of rows: ");
        int numRows = scanner.nextInt();
        System.out.print("Enter the number of columns: ");
        int numCols = scanner.nextInt();

        SparseMatrix matrix = new SparseMatrix(numRows, numCols);
        matrix.readMatrix();

        System.out.println("Original Matrix:");
        matrix.displaySparseMatrix();

        SparseMatrix simpleTransposedMatrix = matrix.simpleTranspose();
        System.out.println("\nSimple Transpose:");
        simpleTransposedMatrix.displaySparseMatrix();

        SparseMatrix fastTransposedMatrix = matrix.fastTranspose();
        System.out.println("\nFast Transpose:");
        fastTransposedMatrix.displaySparseMatrix();
    }
}
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
-------------------------------------------------------------------BUBBLE SORT----------------------------------------------------------------------------------------
import java.util.*;
import java.lang.*;
class Bubble
{
    public static void main (String[] args)
    {
        Scanner sc=new Scanner(System.in);
        int[] arr=new int[8];
        int[] arr1=new int[8];
        int a=0,b=0;
        System.out.println("Enter the eight numbers that are to be arranged :");
        for(int i=0;i<8;i++)
        {
            arr[i]=sc.nextInt();
        }
        for(int i=0;i<8;i++)
        {
            for(int j=0;j<7;j++)
            {
                if(arr[j]>arr[j+1])
                {
                    a=arr[j];
                    b=arr[j+1];
                    arr[j]=b;
                    arr[j+1]=a;
                }
            }
        }
        System.out.print("Sorted Array :");
        for(int i=0;i<8;i++)
        {
            System.out.print(arr[i]+" ");
        }
        sc.close();
    }
}
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------
-------------------------------------------------------------------------QUICK SORT----------------------------------------------------------------------------------------
public class QuickSort {

    static void quickSort(int[] arr, int low, int high) {
        if (low < high) {
            int partitionIndex = partition(arr, low, high);

            // Display pass-by-pass output
            System.out.print("Pass: ");
            displayArray(arr);

            quickSort(arr, low, partitionIndex - 1);
            quickSort(arr, partitionIndex + 1, high);
        }
    }

    static int partition(int[] arr, int low, int high) {
        int pivot = arr[high];
        int i = low - 1;

        for (int j = low; j < high; j++) {
            if (arr[j] <= pivot) {
                i++;

                // Swap arr[i] and arr[j]
                int temp = arr[i];
                arr[i] = arr[j];
                arr[j] = temp;
            }
        }

        // Swap arr[i+1] and arr[high] (pivot)
        int temp = arr[i + 1];
        arr[i + 1] = arr[high];
        arr[high] = temp;

        return i + 1;
    }

    // Display array elements
    static void displayArray(int[] data) {
        for (int i = 0; i < data.length; i++) {
            System.out.print(data[i]);
            if (i < data.length - 1) {
                System.out.print(" ");
            }
        }
        System.out.println();
    }

    public static void main(String[] args) {
        // Example data
        int[] data = {64, 34, 25, 12, 22, 11, 90};

        // Sorting using quick sort
        quickSort(data, 0, data.length - 1);
    }
}
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------
-------------------------------------------------------------------------LINEAR SEARCH----------------------------------------------------------------------------------------
import java.util.Scanner;

public class LinearSearch {
    public static int linearSearch(int[] arr, int key) {
        for (int i = 0; i < arr.length; i++) {
            if (arr[i] == key) {
                return i; // Return the index if the key is found
            }
        }
        return -1; // Return -1 if the key is not found
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        // Get the size of the array from the user
        System.out.print("Enter the size of the array: ");
        int size = scanner.nextInt();

        // Create an array with the specified size
        int[] arr = new int[size];

        // Get array elements from the user
        System.out.println("Enter the elements of the array:");
        for (int i = 0; i < size; i++) {
            arr[i] = scanner.nextInt();
        }

        // Get the key to search for
        System.out.print("Enter the element to search for: ");
        int key = scanner.nextInt();

        // Perform linear search
        int result = linearSearch(arr, key);

        // Display the result
        if (result != -1) {
            System.out.println("Element " + key + " found at index " + result);
        } else {
            System.out.println("Element " + key + " not found in the array");
        }

        // Close the scanner
        scanner.close();
    }
}
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------
-------------------------------------------------------------------------SELECTION SORT AND BINARY SEARCH----------------------------------------------------------------------------------------
import java.util.Scanner;

public class UserDefinedSelectionSortAndBinarySearch {

    // Selection sort method
    static void selectionSort(int[] data) {
        int n = data.length;
        for (int i = 0; i < n - 1; i++) {
            int minIndex = i;
            for (int j = i + 1; j < n; j++) {
                if (data[j] < data[minIndex]) {
                    minIndex = j;
                }
            }
            // Swap the found minimum element with the first element
            int temp = data[minIndex];
            data[minIndex] = data[i];
            data[i] = temp;

            // Display pass-by-pass output
            System.out.print("Pass " + (i + 1) + ": ");
            displayArray(data);
        }
    }

    // Binary search method
    static int binarySearch(int[] data, int target) {
        int low = 0, high = data.length - 1;

        while (low <= high) {
            int mid = (low + high) / 2;

            if (data[mid] == target) {
                return mid; // Element found, return its index
            } else if (data[mid] < target) {
                low = mid + 1;
            } else {
                high = mid - 1;
            }
        }

        return -1; // Element not found
    }

    // Display array elements
    static void displayArray(int[] data) {
        for (int i = 0; i < data.length; i++) {
            System.out.print(data[i]);
            if (i < data.length - 1) {
                System.out.print(" ");
            }
        }
        System.out.println();
    }

    public static void main(String[] args) {
        // Allowing the user to input their own array
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter the size of the array: ");
        int size = scanner.nextInt();

        int[] data = new int[size];
        System.out.println("Enter the elements of the array:");
        for (int i = 0; i < size; i++) {
            data[i] = scanner.nextInt();
        }

        // Sorting using selection sort
        selectionSort(data.clone()); // Displaying pass-by-pass output

        // Example target to search
        System.out.print("Enter the element to search: ");
        int target = scanner.nextInt();

        // Using binary search on the sorted data
        int result = binarySearch(data, target);

        if (result != -1) {
            System.out.println("Element " + target + " found at index " + result);
        } else {
            System.out.println("Element " + target + " not found");
        }

        scanner.close();
    }
}
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------SINGLY LINKED LIST EMP------------------------------------------------------------------------------------------------
import java.util.Scanner;

class Node {
    int emp_id;
    String emp_name;
    String emp_position;
    Node next;

    public Node(int emp_id, String emp_name, String emp_position) {
        this.emp_id = emp_id;
        this.emp_name = emp_name;
        this.emp_position = emp_position;
        this.next = null;
    }
}

class LinkedList {
    Node head;

    // Function to insert a new employee at the end of the linked list
    public void insert(int emp_id, String emp_name, String emp_position) {
        Node newEmployee = new Node(emp_id, emp_name, emp_position);
        if (head == null) {
            head = newEmployee;
        } else {
            Node current = head;
            while (current.next != null) {
                current = current.next;
            }
            current.next = newEmployee;
        }
    }

    // Function to delete an employee by emp_id
    public void delete(int emp_id) {
        if (head == null) {
            System.out.println("List is empty. Deletion failed.");
            return;
        }

        if (head.emp_id == emp_id) {
            head = head.next;
            return;
        }

        Node current = head;
        while (current.next != null && current.next.emp_id != emp_id) {
            current = current.next;
        }

        if (current.next == null) {
            System.out.println("Employee not found.");
        } else {
            current.next = current.next.next;
        }
    }

    // Function to search for an employee by emp_id
    public Node search(int emp_id) {
        Node current = head;
        while (current != null) {
            if (current.emp_id == emp_id) {
                return current;
            }
            current = current.next;
        }
        return null;
    }

    // Function to modify employee details by emp_id
    public void modify(int emp_id, String new_name, String new_position) {
        Node employee = search(emp_id);
        if (employee != null) {
            employee.emp_name = new_name;
            employee.emp_position = new_position;
        } else {
            System.out.println("Employee not found.");
        }
    }

    // Function to display the linked list
    public void display() {
        Node current = head;
        while (current != null) {
            System.out.println("Employee ID: " + current.emp_id +
                    ", Employee Name: " + current.emp_name +
                    ", Employee Position: " + current.emp_position);
            current = current.next;
        }
    }
}

class Main {
    public static void main(String[] args) {
        LinkedList employeeList = new LinkedList();
        Scanner x = new Scanner(System.in);

        System.out.print("Enter the number of employees: ");
        int ren = x.nextInt();
        x.nextLine(); // Consume newline

        // Taking user-defined inputs for employee data
        for (int i = 1; i <= ren; i++) {
            System.out.print("Enter employee ID for employee " + i + ": ");
            int emp_id = x.nextInt();
            x.nextLine(); // Consume newline
            System.out.print("Enter employee name for employee " + i + ": ");
            String emp_name = x.nextLine();
            System.out.print("Enter employee position for employee " + i + ": ");
            String emp_position = x.nextLine();

            // Inserting the employee into the linked list
            employeeList.insert(emp_id, emp_name, emp_position);
        }

        // Display the list
        System.out.println("\nEmployee List:");
        employeeList.display();

        // Menu-driven program
        int choice;
        do {
            System.out.println("\nMenu:");
            System.out.println("1. Insert Employee");
            System.out.println("2. Delete Employee");
            System.out.println("3. Search Employee");
            System.out.println("4. Modify Employee Details");
            System.out.println("5. Display Employees");
            System.out.println("6. Exit");
            System.out.print("Enter your choice: ");
            choice = x.nextInt();
            x.nextLine(); // Consume newline

            switch (choice) {
                case 1:
                    System.out.print("Enter employee ID: ");
                    int emp_id = x.nextInt();
                    x.nextLine(); // Consume newline
                    System.out.print("Enter employee name: ");
                    String emp_name = x.nextLine();
                    System.out.print("Enter employee position: ");
                    String emp_position = x.nextLine();
                    employeeList.insert(emp_id, emp_name, emp_position);
                    break;
                case 2:
                    System.out.print("Enter employee ID to delete: ");
                    emp_id = x.nextInt();
                    employeeList.delete(emp_id);
                    break;
                case 3:
                    System.out.print("Enter employee ID to search: ");
                    emp_id = x.nextInt();
                    Node foundEmployee = employeeList.search(emp_id);
                    if (foundEmployee != null) {
                        System.out.println("Employee found: ID - " + foundEmployee.emp_id +
                                ", Name - " + foundEmployee.emp_name +
                                ", Position - " + foundEmployee.emp_position);
                    } else {
                        System.out.println("Employee not found.");
                    }
                    break;
                case 4:
                    System.out.print("Enter employee ID to modify: ");
                    emp_id = x.nextInt();
                    x.nextLine(); // Consume newline
                    System.out.print("Enter new employee name: ");
                    emp_name = x.nextLine();
                    System.out.print("Enter new employee position: ");
                    emp_position = x.nextLine();
                    employeeList.modify(emp_id, emp_name, emp_position);
                    break;
                case 5:
                    System.out.println("Employee List:");
                    employeeList.display();
                    break;
                case 6:
                    System.out.println("Exiting program. Goodbye!");
                    break;
                default:
                    System.out.println("Invalid choice. Please try again.");
            }
        } while (choice != 6);

        x.close();
    }
}
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------
------------------------------------------STACK AS LINKED LIST-----------------------------------------------------------------------------------------------------------


---------------------------------------------------------------------------------------------------------------------------------------------------------------------------
------------------------------------------QUEUE AS LINKED LIST-----------------------------------------------------------------------------------------------------------
