# Task 01: Write Test Cases for a Simple Calculator Application

Create detailed test cases in Markdown format for a calculator that performs add, subtract, multiply, and divide operations. Focus on valid inputs (e.g., positive and negative numbers, decimals, BODMAS) and invalid inputs (e.g., non-numeric characters, division by zero). Each test case should include the following elements:
- Test Case ID
- Test Description
- Preconditions
- Test Steps
- Expected Results

## Test Cases

### Test Case 1: Adding any positive integers
**Test Case ID:** TC_001  
**Test Description:** The First Test will be some test for Bonus 1.  
**Preconditions:** Calculator application should be opened successfully.  
**Test Steps:**
1. Type "5" into the calculator display.
2. Press the "+" button.
3. On the calculator display, input "3".
4. Press the "=" button.  
**Expected Result:** The display on the calculator should read "8".

---

### Test Case 2: Addition of Negative Integers
**Test Case ID:** TC_002  
**Test Description:** Perform addition between two negative integers.  
**Preconditions:** Calculator application launches properly.  
**Test Steps:**
1. Write "-5" on the calculator screen.
2. Press the "+" button.
3. On the calculator display, input "-3".
4. Press the "=" button.  
**Expected Result:** Display on the calculator should show “-8”.

---

### Test Case 3: Add Decimal Numbers
**Test Case ID:** TC_003  
**Test Description:** Take as input two decimal numbers, compute their sum and print it.  
**Preconditions:** Calculator Application is opened successfully.  
**Test Steps:**
1. On the calculator screen, input "2.5".
2. Press the "+" button.
3. Enter “1.75” on the calculator screen.
4. Press the "=" button.  
**Expected Result:** The output of the calculator display should be: "4.25".

---

### Test Case 4: Subtracting Positive Integers
**Test Case ID:** TC_004  
**Test Description:** Subtract two positive integers.  
**Preconditions:** Calculator application opened.  
**Test Steps:**
1. On the calculator display, enter "8".
2. Press the "-" button.
3. Display "3" on the calculator.
4. Press the "=" button.  
**Expected Result:** The calculator display should be "5".

---

### Test Case 5: Subtracting Negative Integers
**Test Case ID:** TC_005  
**Test Description:** Subtract two negative integers.  
**Preconditions:** Calculator application opened.  
**Test Steps:**
1. On the calculator display, enter "8".
2. Press the "-" button.
3. Display "-3" on the calculator.
4. Press the "=" button.  
**Expected Result:** The calculator display should be "11".

---

### Test Case 6: Multiplying Integers
**Test Case ID:** TC_006  
**Test Description:** Multiply two integers.  
**Preconditions:** Calculator application opened.  
**Test Steps:**
1. On the calculator display, enter "5".
2. Press the "x" button.
3. Display "-3" on the calculator.
4. Press the "=" button.  
**Expected Result:** The calculator display should be "-15".

---

### Test Case 7: Division of Integers
**Test Case ID:** TC_007  
**Test Description:** Divide two integers.  
**Preconditions:** Calculator application opened.  
**Test Steps:**
1. On the calculator display, enter "10".
2. Press the "/" button.
3. Display "2" on the calculator.
4. Press the "=" button.  
**Expected Result:** The calculator display should be "5".

---

### Test Case 8: Division by Zero
**Test Case ID:** TC_008  
**Test Description:** Divide a number by zero.  
**Preconditions:** Calculator application opened.  
**Test Steps:**
1. Input "5" on the calculator display.
2. Press the "/" button.
3. Input "0" on the calculator display.
4. Press the "=" button.  
**Expected Result:** The calculator display should show an error message (e.g., "Error", "Division by zero").

---

### Test Case 9: Non-Numeric Input
**Test Case ID:** TC_009  
**Test Description:** Enter a non-numeric character as input.  
**Preconditions:** Calculator application opened.  
**Test Steps:**
1. Input "5" on the calculator display.
2. Press the "+" button.
3. Input "a" (or any non-numeric character) on the calculator display.
4. Press the "=" button.  
**Expected Result:** The calculator display should show an error message (e.g., "Error", "Invalid input").

---

### Test Case 10: BODMAS Operation
**Test Case ID:** TC_010  
**Test Description:** Test the order of operations (BODMAS).  
**Preconditions:** Calculator application opened.  
**Test Steps:**
1. Input "2" on the calculator display.
2. Press the "x" button.
3. Input "3" on the calculator display.
4. Press the "+" button.
5. Input "4" on the calculator display.
6. Press the "=" button.  
**Expected Result:** The calculator display should show "10" (2 * 3 = 6, 6 + 4 = 10).
