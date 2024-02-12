# **Week 3 Lab Report**
***
## Part 1: Bugs
There is a bug in the `filter` method in `ListExamples`. The line: `result.add(0, s)` reverses the order of the elements in the list.

Below is a failure-inducing input for the buggy program, as a JUnit test and associated code.
```
public class ListTest {
  @Test
  public void testFilter() {
    class Checker implements StringChecker {
      public boolean StringChecker(String s) {
        return s.contains(s:" ");
      }
    StringChecker sc = new Checker();
    
    }

    List<String> input = new ArrayList<String>();
    input.add("red");
    input.add("yellow");
    input.add("blue");

    List<String> output = new ArrayList<String>();
    output.add("red");
    output.add("yellow");

    List<String> result = ListTest.filter(input, sc);
    List<String> expected = ["red", "yellow"];

    assertEquals(expected, result);
  }

  
}
```

Below is an input that doesn't induce a failure, as a JUnit test and associated code.
```
code here
```

Below is the symptom, as the output of running the tests (screenshot of running JUnit with at least the two inputs above)

Below is the bug, as the before-and-after code change required to fix it (as two code blocks in Markdown)
```
code here
```
Description of why the fix addresses the issue.
***
## Part 2: Researching Commands
