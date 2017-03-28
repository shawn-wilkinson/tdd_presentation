## Test Driven Development
#### Introduction & Application
---
#####What am I talking about?<br>
<div style="text-align: left">
-(Briefly) What is TDD and why do we do it?<br>
-The hardest part: getting started<br>
-Tips and best practices<br>
-Discussion: how do we move forward?
</div>
---
###What Is TDD?

####More than "writing tests first"...<br>
TDD is continual testing, coding, design and documentation.
+++
####In a nutshell:
  1. Write a test.
  2. Run all tests. The test should fail.
  3. Write the minimum amount of code to pass the test.
  4. Run all tests. They should pass.
  5. Refactor your code - optional.
  
+++
![Image-Absolute](https://s3.amazonaws.com/media-p.slid.es/uploads/jlopezmo/images/587930/tdd-circle-of-life.png)
+++
####Uncle Bob's Three Laws of TDD:<br>
1. You can't write any production code until you have first written a failing unit test.<br>
2. You can't write more of a unit test than is sufficient to fail, and not compiling is failing.<br>
3. You can't write more production code than is sufficient to pass the currently failing unit test<br>
[Credit to Robert C. Martin](http://programmer.97things.oreilly.com/wiki/index.php/Uncle_Bob)
---
####Why Do We Use TDD?
1. Code is written to specification.

2. Tests serve as documentation for the intention behind the subject.

3. We can push up with confidence.
+++
####Why Do We Use TDD?
4. Tests promote refactoring and more maintainable code.

5. Will you *really* get around to writing those tests later?
---
####The Hard Part
#####Testing functionality that doesn't exist yet
![Image-Relative](http://media1.iterated-reality.com/2015/03/ChickenOrEgg.jpg)
+++
#####The Basic Steps:
1. Inputs and Outputs
2. Function Signature
3. Decide on one aspect of functionality
4. Implement Tests
5. Implement Code

[Code Utopia](https://codeutopia.net/blog/2016/10/10/5-step-method-to-make-test-driven-development-and-unit-testing-easy/)
+++
#####Example Problem:
####Build a function that determines if a username has valid formatting.<br>
-Length?<br>
-Special Characters?<br>
-Duplication?<br>
+++
#####1. Inputs and Outputs<br>
Input: username<br>
Output: boolean<br>
#####2. Function Signature<br>
I think it will look something like this:
```Java 
Public Boolean isValidUsername(String username){
  ...code things go here...
}
```
+++
#####3. Isolate one aspect of functionality
Behavior: Blank usernames are considered invalid.
#####4.Implement Tests
```Java
  @Test
  public void isValidUsername_blankUsername_returnsFalse{
    Boolean isValid = isValidUsername("");
    assertThat(isValid).isEqualTo(false);
  }
```
+++
#####5. Implement Code
```Java
Public boolean isValidUsername(String username){
  return !username.isEmpty();
}
```
+++
######Let's add more...
#####3b. Isolate one aspect of functionality<br>
Behavior: Usernames under six characters are considered invalid.
+++
#####4b.Implement Tests
```Java
  @Test
  public void isValidUsername_overSixChars_returnsTrue{
    Boolean isValid = isValidUsername("Savy");
    assertThat(isValid).isEqualTo(false);
  }
```
+++
#####4b cont...
```Java
  @Test
  public void isValidUsername_overSixChars_returnsTrue{
    Boolean isValid = isValidUsername("eaglescout1776");
    assertThat(isValid).isEqualTo(true);
  }
```
+++
#####4b cont...
```Java
  @Test
  public void isValidUsername_sixChars_returnsTrue{
    Boolean isValid = isValidUsername("Oberon");
    assertThat(isValid).isEqualTo(true);
  }
```
+++
#####5b. Implement Code
```Java
Public boolean isValidUsername(String username){
  return username.length() > = 6;
}
```
---
####Testing Best Practices:
  1. Test the behavior.
  
  2. Design from the outside in. Design based on need.
  
  3. If you can't come up with a succinct test name, the the subject method might need to be broken down.
+++
####Testing Best Practices:
  4. As few assertions as possible to capture the behavior.
  
  5. Extract repetitive or distracting code to setup/helpers.
  
  6. Why a test passes should be obvious.
+++
####Testing Best Practices:
  7. Expressive code is better than DRY code.
  
  8. Never skimp on refactoring. TDD without refactoring is a mess.
---
####TDD can be hard. How do we get better?
  - How do we practice TDD as a team?<br>
  - What do we do well?<br>
  - What are opportunites for improvement? (Action Items!)
---
####Resources:


