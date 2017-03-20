## Test Driven Development
#### Introduction & Application
---
###What Is TDD?
####More than "writing tests first"...
+++
TDD is continual testing, coding, design and documentation.
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
Why Do We Use TDD?
TDD is continual testing, coding, design and documentation.
---
####Testing Best Practices:
+++
  #####Test the behavior.
+++
  #####As few assertions as possible to capture the behavior.
+++
  #####Extract repetitive or distracting code to setup/helpers.
```Java
// Java Code Block
@Test
public void completeMeritBadge_completedAndScoutMasterSet {
  Scout scout = new Scout();
  ScoutMaster scoutMaster = new ScoutMaster();
  MeritBadge meritBadge = MeritBadge.builder().name("Knots").build();
  doReturn(scoutMaster).when(mockBadgeService).getSupervisingScoutMaster();

  subject.completeMeritBadge(scout, meritBadge);

  assertThat(meritBadge.completed()).isTrue();
  assertThat(meritBadge.supervisingScoutMaster()).isEqualTo(scoutMaster);
}
```
+++
  #####Why a test passes should be obvious.
  ```Java
  // Java Code Block
  @Test
  public void completeMeritBadge_completedAndScoutMasterSet {
    Scout scout = new Scout();
    ScoutMaster scoutMaster = new ScoutMaster();
    MeritBadge meritBadge = MeritBadge.builder().name("Knots").build();
    doReturn(scoutMaster).when(mockBadgeService).getSupervisingScoutMaster();

    subject.completeMeritBadge(scout, meritBadge);

    assertThat(meritBadge.completed()).isTrue();
    assertThat(meritBadge.supervisingScoutMaster()).isEqualTo(scoutMaster);
  }
  ```
+++
  #####Expressive code is better than DRY code.
+++
  #####If you can't come up with a succinct test name, the the subject method might need to be broken down.
+++
  #####Never skimp on refactoring. TDD without refactoring is a mess.
+++
  #####Design from the outside in. Design based on need.
---

