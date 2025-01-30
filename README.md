# FILE-HANDLING-UTILITY

**COMPANY**:CODE IT SOLUTIONS

**NAME**:DHIVYA K.R

**INTERN ID**:CODHC153

**DOMAIN**:JAVA PROGRAMMING 

**BATCH DURATION**:December 25th, 2024 to February 10th, 2025.

**MENTOR NAME**:NEELA SANTHOSH KUMAR 

**DESCRIPTION**:

# **Java File Handling Utility: Implementation and Explanation**  

## **Introduction**  
The objective of this project was to create a **Java program** that efficiently performs fundamental file operations, including **reading, writing, and modifying text files**. Java provides powerful built-in classes in the `java.io` package to handle file operations, ensuring seamless interaction with external text files.  

This program performs the following steps:  
1. **Write to a file** – Stores a message in a text file.  
2. **Read from the file** – Displays the file's content.  
3. **Modify the file** – Replaces specific words in the text file.  
4. **Read the updated file** – Confirms successful modification.  
5. **Interactive step** – Allows the user to append new content dynamically.  

---

## **Understanding the Code Implementation**  

### **1. Writing to a File**  
The `writeToFile` method uses `FileWriter` to write data into a text file.  
- The constructor parameter `true` enables **appending** to the file instead of overwriting it.  
- A `try-with-resources` block ensures that the file is properly closed after writing, preventing memory leaks.  
- An error-handling mechanism using `IOException` ensures robustness.  

```java
public static void writeToFile(String fileName, String content) {
    try (FileWriter writer = new FileWriter(fileName, true)) {
        writer.write(content);
        System.out.println("Successfully wrote to the file: " + fileName);
    } catch (IOException e) {
        System.err.println("An error occurred while writing to the file.");
        e.printStackTrace();
    }
}
```  

### **2. Reading from a File**  
The `readFromFile` method uses `BufferedReader` for efficient line-by-line reading.  
- It opens the file using `FileReader`.  
- A `while` loop reads each line until the end of the file (`null`).  
- The content is displayed in the console for verification.  

```java
public static void readFromFile(String fileName) {
    try (BufferedReader reader = new BufferedReader(new FileReader(fileName))) {
        String line;
        System.out.println("Reading from file: " + fileName);
        while ((line = reader.readLine()) != null) {
            System.out.println(line);
        }
    } catch (IOException e) {
        System.err.println("An error occurred while reading the file.");
        e.printStackTrace();
    }
}
```  

### **3. Modifying File Content**  
The `modifyFile` method searches for a specific word in the file and replaces it with new text.  
- A `StringBuilder` temporarily stores the modified content.  
- It reads and updates each line, then rewrites the modified content into the file.  

```java
public static void modifyFile(String fileName, String targetWord, String replacement) {
    File file = new File(fileName);
    StringBuilder content = new StringBuilder();

    try (BufferedReader reader = new BufferedReader(new FileReader(file))) {
        String line;
        while ((line = reader.readLine()) != null) {
            content.append(line.replace(targetWord, replacement)).append(System.lineSeparator());
        }
    } catch (IOException e) {
        System.err.println("An error occurred while reading the file for modification.");
        e.printStackTrace();
        return;
    }

    try (FileWriter writer = new FileWriter(file)) {
        writer.write(content.toString());
        System.out.println("Successfully modified the file: " + fileName);
    } catch (IOException e) {
        System.err.println("An error occurred while writing the modified content to the file.");
        e.printStackTrace();
    }
}
```  

### **4. Interactive File Modification**  
To make the program dynamic, a **user input step** was introduced. Using `Scanner`, the user can enter additional text, which is appended to the file.  
- The `try-with-resources` ensures `Scanner` is properly closed.  
- The newly entered text is written using `writeToFile()`, followed by reading the file again to confirm changes.  

```java
try (Scanner scanner = new Scanner(System.in)) {
    System.out.println("Enter additional text to append to the file:");
    String additionalText = scanner.nextLine();
    writeToFile(fileName, additionalText + "\n");
    System.out.println("Updated File Content:");
    readFromFile(fileName);
}
```

---

## **Testing and Validation**  
The program was tested under different scenarios to ensure correctness:  
1. **Writing and reading a file** – Verified that the written content was correctly saved and displayed.  
2. **Appending content** – Ensured that new text was added without deleting previous data.  
3. **Modifying content** – Checked whether the program accurately replaced targeted words in the file.  
4. **Handling non-existent files** – The error-handling mechanism worked correctly, preventing crashes.  

---

## **Challenges and Improvements**  
### **Challenges Faced**  
- **Handling large files**: Buffered reading and writing were used to optimize performance.  
- **Preventing accidental overwriting**: `FileWriter` with `true` ensured data persistence.  
- **Managing user input efficiently**: The `Scanner` class was closed properly to avoid resource leaks.  

### **Future Improvements**  
- **GUI-based implementation**: A user-friendly graphical interface using Java Swing.  
- **Enhanced search and replace**: Regular expressions for advanced text modifications.  
- **Logging and error handling**: Writing errors and operations to a log file for debugging.  

---

## **Conclusion**  
This Java file handling utility efficiently demonstrates **reading, writing, appending, and modifying text files**. It leverages **BufferedReader, FileWriter, and Scanner** to interact with files dynamically while ensuring proper resource management. The interactive approach makes it useful for various real-world applications such as **configuration file handling, data logging, and text processing**.  

This project successfully meets the requirements and serves as a **robust foundation for advanced file operations in Java.** 🚀

**OUTPUT**:
![Image](https://github.com/user-attachments/assets/69f28691-4594-4977-a001-7418a3f0e501)
