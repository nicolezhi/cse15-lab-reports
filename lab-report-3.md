# **Week 3 Lab Report**
***
## Part 1: Bugs
There is a bug in the `filter` method in `ListExamples`. 

A failure-inducing input for the buggy program, as a JUnit test and any associated code (write it as a code block in Markdown)

The bug: reverses the order of the elements in the list in the line: `result.add(0, s)`
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
