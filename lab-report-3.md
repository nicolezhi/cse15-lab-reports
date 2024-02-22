# **Week 3 Lab Report**
***
## Part 1: Bugs
There is a bug in the `filter` method in `ListExamples`. The line: `result.add(0, s)` reverses the order of the elements in the list.

**Below is a failure-inducing input for the buggy program, as a JUnit test and associated code.**
```
public class ListTest {
  @Test
  public void testFilter() {
    class Checker implements StringChecker {
      public boolean checkString(String s) {
        return s.contains(" ");
      }
    StringChecker sc = new Checker();
    }
    List<String> input = new ArrayList<String>();
    input.add("red");
    input.add("yellow");
    input.add("blue");

    List<String> result = ListTest.filter(input, sc);
    List<String> expected = Arrays.asList("red", "yellow");

    assertEquals(expected, result);
  }
}
```

**Below is an input that doesn't induce a failure, as a JUnit test and associated code.**
```
public class ListTest {
  @Test
  public void testFilter() {
    class Checker implements StringChecker {
      public boolean checkString(String s) {
        return s.contains(" ");
      }
    StringChecker sc = new Checker();
    }
    List<String> input = new ArrayList<String>();
    input.add("red");
    input.add("yellow");
    input.add("blue");

    List<String> expected = Arrays.asList("blue");

    List<String> result = ListTest.filter(input, sc);

    assertEquals(expected, result);
  }
}
```

**Below is the symptom, as the output of running the tests (screenshot of running JUnit with at least the two inputs above).**
<img width="754" alt="lab3-screenshot1" src="https://github.com/nicolezhi/cse15-lab-reports/assets/112342454/095ddaab-686d-43b5-8c48-0494b70d05e0">


**Below is the bug `result.add(0, s)`, as the before code.**
```
 static List<String> filter(List<String> list, StringChecker sc) {
    List<String> result = new ArrayList<>();
    for(String s: list) {
      if(sc.checkString(s)) {
        result.add(0, s);
      }
    }
    return result;
  }
```
**Below is the code after the bug is fixed. The code was changed from `result.add(0, s)` to `result.add(s)`.**

```
static List<String> filter(List<String> list, StringChecker sc) {
    List<String> result = new ArrayList<>();
    for(String s: list) {
      if(sc.checkString(s)) {
        result.add(s);
      }
    }
    return result;
  }
```

**Description of why the fix addresses the issue.**
Before, the code would add the next element in the array at the index 0, resulting in the array list elements being backwards. When taking out the index 0 specification, the code will add the element at the end of the array list, so that they are in order.

***
## Part 2: Researching Commands

**The command line option `-N` shows the line numbers for a text file in `./technical/biomed`.**
This is the input:
```
less -N ./technical/biomed/1468-6708-3-3.txt
```
This is the output of the first few lines of the text file:
```
      5         The problem
      6         Three published [ 1 2 3 ] and one recently presented [ 4
      7         ] randomized placebo-controlled clinical trial have
      8         unequivocally demonstrated that 3-Hydroxy-3-methylgluatryl
      9         coenzyme A (HMG CoA) reductase inhibitors (statins) reduce
     10         the morbidity and mortality associated with coronary
```
Below is a screenshot of the first few lines of the text file output. The -N is useful because it shows the line number after each line so you can see how many lines are in the text file total and reference certain line numbers.

<img width="755" alt="Screenshot 2024-02-22 at 1 17 15 PM" src="https://github.com/nicolezhi/cse15-lab-reports/assets/112342454/7cd09804-9096-4481-810c-3bdad7ece466">

In another example using a text file in the `plos` directory, this is the input:
```
less -N ./technical/plos/journal.pbio.0020001.txt
```
This is the output: 
```
      6         Kofi Annan, the Secretary-General of the United Nations, recently called atten      6 tion to
      7         the clear inequalities in science between developing and developed countries a      7 nd to the
      8         challenges of building bridges across these gaps that should bring the United       8 Nations and
      9         the world scientific community closer to each other (Annan 2003). Mr. Annan st      9 ressed the
     10         importance of reducing the inequalities in science between developed and devel     10 oping
```
Below is a screenshot of what the output code looks like.
<img width="755" alt="Screenshot 2024-02-22 at 1 19 45 PM" src="https://github.com/nicolezhi/cse15-lab-reports/assets/112342454/c565c07f-6be0-47ba-8cb6-e88cb5dc18e2">

The -N is useful in these examples because it shows the line number next to each line, so you know how many lines there are total in the text file and how to reference a specific line by its line number.

***

**The command `+G` shows the lines at the bottom of the text file.**
This is the input:
```
less +G ./technical/biomed/1471-213X-1-1.txt
```

The result shows the text file scrolled to the bottom. This is the last line in the file.:
```
a SPOT digital camera (Diagnostic Instruments Inc.).
```
Below is a screenshot of the output code.
<img width="755" alt="Screenshot 2024-02-22 at 1 24 38 PM" src="https://github.com/nicolezhi/cse15-lab-reports/assets/112342454/f9a34f81-8b15-4bd6-b685-a0a9817ef839">

This command is useful because there are so many lines in the specified file, and scrolling it to the bottom of the text file helps you get to the end of the text easily.

This is another input:
```
less +G ./technical/plos/journal.pbio.0020043.txt
```
This is the last line in the text file, which is scrolled to the bottom.
```
planet and why, in the meantime, we should take a close look at scale insects.
```
Below is a screenshot of the output code.
<img width="755" alt="Screenshot 2024-02-22 at 1 25 24 PM" src="https://github.com/nicolezhi/cse15-lab-reports/assets/112342454/bb531d7f-8485-4f4f-b3bf-5003dad8d8c9">

Again, using this command to scroll to the bottom of the text file helps you get to/reference the end of the text easily.

***

**The command `+<line-number>` shows the text file at the given line number.**
This is an input:
```
less -N +150 ./technical/biomed/1471-213X-1-3.txt
```
In the output, it scrolls exactly to line 150.
```
 150           several cells thick and extended from the anterior edge
```
Below is a screenshot of the output code, scrolled to line 150.

<img width="755" alt="Screenshot 2024-02-22 at 1 27 57 PM" src="https://github.com/nicolezhi/cse15-lab-reports/assets/112342454/8ecc51e7-910e-42a6-80c3-95006b0f3f0d">

This command is extremely helpful when you want to reference a certain line in the text file, since many text files are large and have hundreds or thousands of lines of text.

This is another input:
```
less -N +65 ./technical/plos/journal.pbio.0020064.txt
```
In the output, the text file shows the line at line 65.
```
 65         and, subsequently, a whole family of T2Rs’, says Zuker.
```
Below is a screenshot of the output code at line 65.
<img width="755" alt="Screenshot 2024-02-22 at 1 29 29 PM" src="https://github.com/nicolezhi/cse15-lab-reports/assets/112342454/0f9d9ed8-30e8-4ebf-ad3f-5489850a66c2">

In this example, the `<+line number>` command was helpful in taking me directly to line 65 when searching for a specific line in the text file.

***

**The `-S` command is used to disable line wrapping when displayed in the terminal.**
This is the input:
```
less -S ./technical/biomed/1468-6708-3-1.txt ./technical/biomed/1468-6708-3-3.txt
```
In the output in the terminal, the lines do not go all the way to the end of the page as there is a larger margin. Below is a screenshot of the output code.

<img width="494" alt="Screenshot 2024-02-22 at 1 44 43 PM" src="https://github.com/nicolezhi/cse15-lab-reports/assets/112342454/498c27f3-e65c-4b1d-b5ff-f26cd5c8b4ba">

This `-S` command is useful because it makes it easier to read the text in the terminal, instead of the words going off the page.

This is another intput.
```
less -S ./technical/plos/journal.pbio.0020040.txt
```
Below is the output. As you can see, the `-S` command moves text onto the next line so that it does not wrap around the page. This makes it easy to read every word in the line of the text file.

<img width="494" alt="Screenshot 2024-02-22 at 1 45 01 PM" src="https://github.com/nicolezhi/cse15-lab-reports/assets/112342454/a5c8beb2-d856-4467-816f-de36f0dcfa30">

***

## Works Cited

I used ChatGPT to give me a list of command line options for this lab. The prompts I gave ChatGPT were: "less command in line options" and "how to use less -S".

**The first output it gave me was:**

"The less command is a terminal pager program that allows you to view text files in a scrollable and interactive way. Here are some commonly used command-line options for the less command:

Basic Usage:

Copy code
less filename
Opens the specified file in less for viewing.

Navigation:

Spacebar or Page Down: Move forward one screen.
b or Page Up: Move backward one screen.
↑ and ↓ arrow keys: Move line by line.
g: Go to the beginning of the file.
G: Go to the end of the file.
q: Quit less.
Search:

/pattern: Search forward for a pattern.
?pattern: Search backward for a pattern.
n: Move to the next occurrence of the search pattern.
N: Move to the previous occurrence of the search pattern.
File Information:

=: Display the current line number and total number of lines.
:f: Display the current file name and status.
Marking Text:

v: Open the current file in the default text editor (configured by the $VISUAL or $EDITOR environment variable).
Other Options:

-N: Display line numbers.
-i: Ignore case when searching.
-S: Disable line wrapping.
-F: Quit if the entire file can be displayed on one screen.
Example:

bash
Copy code
less -i -N myfile.txt
These are just a few examples of the many options available with the less command. You can access more options and details by checking the manual page using man less in the terminal."

**The next output it gave me was:**

The -S option in the less command is used to disable line wrapping. When you use less -S, it prevents long lines from wrapping onto the next line, making it easier to read lines that extend beyond the width of your terminal. Here's an example of how to use less -S:

bash
Copy code
less -S filename
Replace filename with the name of the file you want to view. Once you've opened the file with less -S, you can navigate through the file using the arrow keys, spacebar, and other navigation commands as mentioned earlier.

If you want to use less -S with other options, you can combine them. For example:

bash
Copy code
less -S -i myfile.txt
This would open the file myfile.txt in less, disable line wrapping (-S), and ignore case when searching (-i). Adjust the options based on your preferences and needs."
