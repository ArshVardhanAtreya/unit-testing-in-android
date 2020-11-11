# Android Unit Testing and Test Driven Development

##  Testing:
-   Ensuring that “the thing” does what it’s supposed to do

### Unit Testing:
-   Ensuring that a class does what it’s supposed to do
-   INPUTS of UNIT TESTING: Method calls with predefined arguments
-   OUTPUT of UNIT TESTING: Assert expected behavior

#### JUnit:
-    Unit testing framework for Java. For example: JUnit4, JUnit5

#### Naming of the unit tests:
-    When properly named unit test fails, you can investigate and fix the issue without reading unrelated source code
-    Naming conventions: `<unitOfWork>_<stateUnderTest>_<expectedBehavior>`

#### How to choose test cases:
-    100% line coverage is necessary, but not sufficient to ensure good coverage of SUT functionality
-    Identify different groups of input combinations corresponding to different states
-    Write at least one test case for representative of each group
-    Write test cases for boundary conditions between different groups of inputs

#### Test Doubles
-    Used to substitute external unit’s dependencies in tests
-    Three main types: fake, stub and mock
     1. Fake is a functional implementation optimized for tests
     2. Stub return predefined data and can have programmable behavior
     3. Mock records interactions during test & recorded interactions can be inspected

#### Why to avoid static methods in code
-    Hidden dependencies
-    Can’t be substituted with test doubles
-    Singletons should be avoided at all costs

#### Mockito Fundamentals
-    Easily create stubs and mocks
-    Powerful and versatile
-    Not trivially simple with Mockito – fall back to manual test doubles

-    Objects Vs Data Structure
-    Objects:
     1. Expose behavior
     2. Hide internal implementation details
     3. Should be injected into other objects
     4. Need to be unit tested explicitly
     5. Eligible to be substituted with test doubles

-    Data Structures:
     1. Expose data
     2. Should not have behavior
     3. Can be instantiated by other objects and data structures
     4. Unit tests for objects test data structures implicitly
     5. No need to substitute with test doubles

#### TDD Fundamentals
-    All tests up-front:
     1. Create an empty class for SUT
     2. Write all the required tests
        -You can expand SUT’s public API to make the tests compile
        -You can’t write internal implementation of SUT
     3.  Write the internal implementation of the SUT
     4. Run the tests
     5. Debug until all tests pass

#### TDD Rules by Uncle Bob
-    Uncle Bob has given the following three rules:
     1. You are not allowed to write any production code unless it is to make a failing unit test pass
     2. You are not allowed to write any more of a unit test than is sufficient to fail; and compilation failures are failures
     3. You are not allowed to write any more production code than is sufficient to pass the one failing unit test

#### Synchronous execution:
-    All effects of method call happen before the method returns
-    Return value contains flow execution result

#### Asynchronous execution (Using Observers):
-    Method call can have effects after the method returns
-    Flow execution result will be known after the method returns

#### To keep classes unit testable (in Android Development):
-    Don’t use Android static APIs
-    Don’t instantiate any Android specific classes
-    Mock all Android dependencies (including data structures)
