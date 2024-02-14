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
<img width="682" alt="Screenshot 2024-02-13 at 11 05 27 PM" src="https://github.com/nicolezhi/cse15-lab-reports/assets/112342454/da5ae317-7ad4-4826-b12e-ba7db80e5d98">

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
less -N ./technical/biomed/1468-6708-3-.txt`
```
This is the output of the first few lines of the text file:
```
      5         Introduction
      6         Older adults are frequently counseled to lose weight,
      7         even though there is little evidence that overweight is
      8         associated with increased mortality in those over age 65.
      9         Six large controlled population-based studies of
     10         non-smoking older adults have investigated the association
```
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
**The command `+G` shows the lines at the bottom of the text file.**
This is the input:
```
less +G ./technical/biomed/1471-213X-1-1.txt
```

The result shows the text file scrolled to the bottom. This is the last line in the file.:
```
a SPOT digital camera (Diagnostic Instruments Inc.).
```
This is another input:
```
less +G ./technical/plos/journal.pbio.0020043.txt
```
This is the last line in the text file, which is scrolled to the bottom.
```
planet and why, in the meantime, we should take a close look at scale insects.
```
**The command `+<line-number>` shows the text file at the given line number.**
This is an input:
```
less -N +150 ./technical/biomed/1471-213.1-3.txt
```
In the output, it scrolls exactly to line 150.
```
 150           several cells thick and extended from the anterior edge
```
This is another input:
```
less -N +65 ./technical/plos/journal.pbio.0020064.txt
```
In the output, the text file shows the line at line 65.
```
 65         and, subsequently, a whole family of T2Rs’, says Zuker.
```
**The `:n` and `:p` commands are used to switch between two text files (next or previous).**
This is the input:
```
less ./technical/biomed/1468-6708-3-1.txt ./technical/biomed/1468-6708-3-3.txt
```
One text file is shown at a time. I can use `:n` to go to the next file and `:p` to go to the previous. When I use :n, it shows the next text file (here are the first 3 lines of the text file). It also says this at the bottom: `./technical/biomed/1468-6708-3-3.txt (file 2 of 2)`.
```
The problem
Three published [ 1 2 3 ] and one recently presented [ 4
] randomized placebo-controlled clinical trial have
```

This is another intput.
```
less ./technical/plos/0020040.txt ./technical/plos/0020042.txt
```
This is the output of the first 3 lines of the first text file when I use `:p`. It also says this at the bottom: `less ./technical/plos/0020040.txt (file 1 of 2)`.
```
Stuttering, with its characteristic disruption in verbal fluency, has been known for
centuries; earliest descriptions probably date back to the Biblical Moses' “slowness of
speech and tongue” and his related avoidance behavior (Exodus 4, 10–13). Stuttering occurs
```
