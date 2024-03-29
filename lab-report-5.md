# **Lab Report 5, Week 9**
***
## Part 1: Edstem Conversation About Debugging

**EdStem post from a student regarding a question about debugging the ListExamples program.**

"Hello,

My program is giving me an error that the merge method is not working in `testMerge2`. I am not sure what I'm doing wrong. Below is my code and output."

<img width="685" alt="Screenshot 2024-03-11 at 3 46 37 PM" src="https://github.com/nicolezhi/cse15-lab-reports/assets/112342454/1ba938b9-dd66-4714-9935-f7de60498e9b">

<img width="571" alt="Screenshot 2024-03-11 at 3 43 27 PM" src="https://github.com/nicolezhi/cse15-lab-reports/assets/112342454/e9ec6799-93f0-462e-8d9c-dc3c0b5e3b92">

***

**Edstem reply from a TA asking a leading question to help the student debug their code.**

"Hello,

You are correct that the merge method is not working. Have you tried looking to see if you are adding an element from the correct list? Remember that `index1` corresponds to `list1` and `index2` corresponds to `list2`."

***

**Student's output after debugging code based on TA's suggestion.**

<img width="563" alt="Screenshot 2024-03-11 at 3 05 11 PM" src="https://github.com/nicolezhi/cse15-lab-reports/assets/112342454/c45eec1d-130c-4faf-97cb-aefd2ce770b5">

The bug was located in line 30. Instead of adding `index1` from `list1`, the student was incorrectly adding `index1` from `list2`. The if statement is comparing if `index1` in `list1` is less than `index2` in `list2`, and if so, the program should add `index1` from `list1` in the resulting merged list.

***

### Setup information

**File setup:**

`ListExamples.java` file, `ListExamplesTests.java` file, `StringChecker.class` file, `ListExamples.class` file, `ListExamplesTests.class` file, `test.sh` file, and `lib` folder containing `hamcrest-core-1.3.jar` and junit-4.13.2.jar` files. These are all within the same home directory. 

**Contents of `ListExamples.java` file before fixing bug:**
```
import java.util.ArrayList;
import java.util.List;

interface StringChecker { boolean checkString(String s); }

class ListExamples {

  // Returns a new list that has all the elements of the input list for which
  // the StringChecker returns true, and not the elements that return false, in
  // the same order they appeared in the input list;
  static List<String> filter(List<String> list, StringChecker sc) {
    List<String> result = new ArrayList<>();
    for(String s: list) {
      if(sc.checkString(s)) {
        result.add(s);
      }
    }
    return result;
  }

  // Takes two sorted list of strings (so "a" appears before "b" and so on),
  // and return a new list that has all the strings in both list in sorted order.
  static List<String> merge(List<String> list1, List<String> list2) {
    List<String> result = new ArrayList<>();
    int index1 = 0, index2 = 0;
    while(index1 < list1.size() && index2 < list2.size()) {
      if(list1.get(index1).compareTo(list2.get(index2)) < 0) {
        // fix this line below
        result.add(list1.get(index2));
        index2 += 1;
      }
      else {
        result.add(list2.get(index2));
        index2 += 1;
      }
    }
    while(index1 < list1.size()) {
      result.add(list1.get(index1));
      index1 += 1;
    }
    while(index2 < list2.size()) {
      result.add(list2.get(index2));
      // change index1 below to index2 to fix test
      index2 += 1;
    }
    return result;
  }
}
```

**Command line to compile and run:**

`javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java`

`java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests`

**What to edit to fix the bug:**

In line 30, edit `result.add(list1.get(index2));` to `result.add(list1.get(index1));`.

Below is the correct code after fixing the bug:
```
import java.util.ArrayList;
import java.util.List;

interface StringChecker { boolean checkString(String s); }

class ListExamples {

  // Returns a new list that has all the elements of the input list for which
  // the StringChecker returns true, and not the elements that return false, in
  // the same order they appeared in the input list;
  static List<String> filter(List<String> list, StringChecker sc) {
    List<String> result = new ArrayList<>();
    for(String s: list) {
      if(sc.checkString(s)) {
        // fix to result.add(s);
        result.add(s);
      }
    }
    return result;
  }

  // Takes two sorted list of strings (so "a" appears before "b" and so on),
  // and return a new list that has all the strings in both list in sorted order.
  static List<String> merge(List<String> list1, List<String> list2) {
    List<String> result = new ArrayList<>();
    int index1 = 0, index2 = 0;
    while(index1 < list1.size() && index2 < list2.size()) {
      if(list1.get(index1).compareTo(list2.get(index2)) < 0) {
        // fix this line below
        result.add(list1.get(index1));
        index1 += 1;
      }
      else {
        result.add(list2.get(index2));
        index2 += 1;
      }
    }
    while(index1 < list1.size()) {
      result.add(list1.get(index1));
      index1 += 1;
    }
    while(index2 < list2.size()) {
      result.add(list2.get(index2));
      // change index1 below to index2 to fix test
      index2 += 1;
    }
    return result;
  }
}
```

***

## Part 2: Reflection

Something cool I learned from labs the second half of this quarter is being able to use `vim` to edit code from the terminal. I enjoyed learning about the different commands involved to edit the code files. I also found this really useful for any future coding projects that I do!
