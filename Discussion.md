# **Log Extraction from Large Files - Discussion**

## **Solutions Considered**

### **1. Loading the Entire File into Memory (Inefficient) 🚫**
- One approach is to load the **entire log file** into memory and then filter lines that match the given date.  
- **Why it was rejected?**  
  - This method is **not feasible for a 1TB file** as it requires an enormous amount of RAM.  
  - High memory usage leads to **performance issues and potential crashes**.  

### **2. Line-by-Line Processing (Efficient & Chosen) ✅**
- Read the log file **line by line** and write matching logs to the output file.  
- **Why this approach?**  
  - Works efficiently for very large files.  
  - Requires **minimal memory usage**.  
  - Since logs are **evenly distributed across dates**, scanning line by line is manageable.  

### **3. Using an Index for Faster Retrieval (Advanced)**
- If performance is a concern, we can preprocess the log file and create an **index** (mapping dates to byte offsets).  
- **Pros:**  
  - Instant access to logs of a particular date without scanning the entire file.  
- **Cons:**  
  - Requires a **preprocessing step** to create the index before searching.  

---

## **Final Solution Summary**
- We **chose the line-by-line processing** approach because:  
  ✅ It **scales well** for a 1TB file.  
  ✅ It **does not require high RAM usage**.  
  ✅ It is **straightforward and easy to implement**.  
- The script reads the log file line by line, checks if a line starts with the given date, and writes matching entries to an output file.  

---

## **Steps to Run the Solution**

### **Prerequisites**
- Ensure you have **Python 3+** installed.  
- The log file (`logs_2024.log`) should be in the same directory as the script.  

### **Execution Steps**
1. **Clone the Repository**
   ```bash
   git clone https://github.com/aroraaaa/tech-campus-recruitment-2025.git
   cd tech-campus-recruitment-2025
2. **Run the Python Script**

    ```bash
    python src/solution.py
3. **Enter the Date when Prompted**
    ```bash
    Enter the date (YYYY-MM-DD): 2024-12-01
4. **Output File Location**
Logs for the given date will be saved inside the output/ directory:
    ```bash
    output/output_2024-12-01.txt
