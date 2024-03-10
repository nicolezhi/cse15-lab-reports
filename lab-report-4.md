# **Lab Report 4, Week 7**
***
## Steps 4-9
**Below is a screenshot of me logging into ieng6.**
My input was: `ssh nzhi@ieng6.ucsd.edu <enter>`

<img width="479" alt="Screenshot 2024-02-27 at 9 09 16 PM" src="https://github.com/nicolezhi/cse15-lab-reports/assets/112342454/ee941ac5-b48f-47bf-80d9-adf419388f9f">

***

**Below is a screnshot of me cloning the github repository using the ssh URL.** 
My input was: `git clone git@github.com:ucsd-cse15l-s23/lab7.git new_directory <enter>`

<img width="479" alt="Screenshot 2024-02-27 at 9 43 15 PM" src="https://github.com/nicolezhi/cse15-lab-reports/assets/112342454/52ca24e9-68eb-48bf-b52a-69cdb766d1f6">

***

**Below is a screenshot of me running the tests in `ListExamplesTests.java`.** 
My input was: `<up> javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java <enter>` and `<up><up> java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests <enter>`. The `javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java` command was 1 up in the search history, so I pressed the up arrow key once to access it. The `java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests` key was 2 up in the search history, so I pressed the up arrow key twice to access it.

<img width="452" alt="Screenshot 2024-02-27 at 10 12 54 PM" src="https://github.com/nicolezhi/cse15-lab-reports/assets/112342454/5ef54b4d-37ab-4a41-9108-1afe3f703dfd">

***


**I fixed the code by changing `index1 += 1` to `index2 += 1` in line 43 of the merge method. Additionally, I edited the filter method in line 15 by changing `result.add(0, s);` to `result.add(s);` so that the elements get added to the end of the list, not the beginning.`**

<img width="629" alt="Screenshot 2024-03-09 at 11 43 50 PM" src="https://github.com/nicolezhi/cse15-lab-reports/assets/112342454/543615d9-93b0-4424-9200-6c2d25c228ce">

***

**After running the two tests with the edited code, they now pass. Below is a screenshot of the passing tests.**

<img width="643" alt="Screenshot 2024-03-10 at 12 03 32 AM" src="https://github.com/nicolezhi/cse15-lab-reports/assets/112342454/32ff117b-9826-45d2-9b4d-e0373c31ec3f">
