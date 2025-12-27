# Design Recipes for Python
Recipes that I've learned from systematic design courses from The University of British Columbia and wanted to convert them from BSL to Python.

## Functions Design Recipe

1. **What and why, dummy**
   - **What kind of data are we dealing with?**
     
     Before you can solve a problem, you must know what the inputs and outputs look like. If you are building a "Search" bar, the "What" is a String. If you are building a "Calculator," the "What" is a Number. In Python: We use Type Hints.
     ```python
     # input:int -> output:int
     def main(input:int) -> int:
     ```
    - **Why does this function exist?**
  
    You should be able to explain the function's goal in one simple sentence. If you can't explain it in English (or your native language), you will never be able to explain it in Python. In Python: we use docstrings
     ```python
     def double_integers(input:int) -> int:
         """Doubles any integer value.
     
         Args:
             input(int): Integer to double

         Returns:
             int: Double initial integer value
         """
     ```
    - **Dummy working example**

    The "Dummy" is a version of the function that is intentionally wrong but syntactically correct. If the function is supposed to return a number, you just return 0.
     ```python
     def double_integers(input:int) -> int:
         """Doubles any integer value.
     
         Args:
             input(int): Integer to double

         Returns:
             int: Double initial integer value
         """

         return 0
     ```
  2. **Define examples**
  
  You will often need examples, to help you better understand the function or to properly test the function. In Python, we use the assert keyword to write our examples. Think of assert as a "truth checker": if the statement after it is True, nothing happens. If it is False, the program crashes and tells you exactly what went wrong.
  ```python
      assert double_integers(2) == 4
      assert double_integers(0) == 0
      assert double_integers(-5) == -10
  ```

  ```python
     def double_integers(input:int) -> int:
         """Doubles any integer value.
     
         Args:
             input(int): Integer to double

         Returns:
             int: Double initial integer value
         """

         return 0

      assert double_integers(2) == 4
      assert double_integers(0) == 0
      assert double_integers(-5) == -10
  ```
  3. **Template and Inventory**
  
  The template is a comment that lists the "inventory" of what you have to work with. This is good to do because as your data gets more complex (like a List or a Class), the template reminds you of all the pieces you are allowed to use. For example, if you have a `Player` object, your template would remind you that you have `p.name` and `p.score` available.
  ```python
    def double_integers(input:int) -> int:
         """Doubles any integer value.
     
         Args:
             input(int): Integer to double

         Returns:
             int: Double initial integer value
         """

         return (... input)  # <--- template of inventory

      assert double_integers(2) == 4
      assert double_integers(0) == 0
      assert double_integers(-5) == -10
  ```

   4. **Code function body**
  
  Now complete the function body by filling in the template.
   
  ```python
     def double_integers(input:int) -> int:
         """Doubles any integer value.
     
         Args:
             input(int): Integer to double

         Returns:
             int: Double initial integer value
         """
          
         return 2*input

      assert double_integers(2) == 4
      assert double_integers(0) == 0
      assert double_integers(-5) == -10
  ```

  5. **Testing**
     
  Run your script. If you followed the "run early, run often" approach, your What/Why/Dummy and Template steps should have already cleared out syntax errors. Now, you are just fixing the logic until your assert statements stop crashing the program. Once the function is logic-perfect, you'll notice that having 10 assert lines in the middle of your script makes it look messy. In professional Python, we move those examples into a **Unit Test**.


  
## Data Design 
The key element of data design is a data definition. The Data Definition is just a translation guide between your brain and the computer.

**Information (Real World)**: You think about things like "a car's speed," "a user’s name," or "a bank balance."

**Data (Computer World)**: The computer only sees int, str, or float.

A **Data Definition** is the rule that says: "In this program, when you see the number 6, it represents 6 meters per second." Without this rule, the number 6 is just a meaningless piece of data.

A complete data definition consists of five parts that ensure everyone understands what the data is and how to use it:

1. **Structure Definition**

