# Lab 8 - 202001465

## Jaykumar Navadiya
## 21 April, 2023
## JUnit testing

### Goal of the lab: Goal: The goal of this lab is to learn how to use JUnit to write unit tests for Java programs.


1. Create a new Eclipse project, and within the project create a package.
2. Created a class in the package - class name - Boa and junit test case file - BoaTest

```java
package lab8_202001465;

//represents a boa constrictor
public class Boa {
	private String name;
	private int length; // the length of the boa, in feet
	private String favoriteFood;

	public Boa(String name, int length, String favoriteFood) {
		this.name = name;
		this.length = length;
		this.favoriteFood = favoriteFood;
	}

	//returns true if this boa constrictor is healthy
	public boolean isHealthy() {
		return this.favoriteFood.equals("granola bars");
	}

	//returns true if the length of this boa constrictor is
	//less than the given cage length
	public boolean fitsInCage(int cageLength) {
		return this.length < cageLength;
	}
}
```

3. Created junit test case for class Boa - BoaTest and for test method stubs, select both isHealthy() and fitsInCage(int).

See the screenshot given below to see the tasks done till now:

![s1](https://user-images.githubusercontent.com/67496808/233610831-93079ced-4c1c-46f0-897f-6c97926c7fb9.png)


### Creating a JUnit Test case 
![s2](https://user-images.githubusercontent.com/67496808/233610859-7b4fb116-947c-49ab-b42f-8abd87852a38.png)


4. Method annotated with @Before will be run before each test executes.

```java
package lab8_202001465;

import static org.junit.Assert.*;

import org.junit.Before;
import org.junit.Test;

public class BoaTest {
	
	private Boa jen;
	private Boa ken;

	@Before
	public void setUp() throws Exception {
		//initialization
		jen = new Boa("Jennifer", 2, "grapes");
		ken = new Boa ("Kenneth", 3, "granola bars");
	}
}
```

5. Added private fields for jen and ken in the Boa class.

```java
private Boa jen;
private Boa ken;
```

- The BoaTest class now includes private fields for jen and ken, which are initialized in the setUp method. The testIsHealthy and testFitsInCage methods have also been modified to use these Boa objects for testing.

- It's important to note that the setUp method will be run before each test method, ensuring that any alterations made to the Boa objects during a test won't impact the objects used in other tests.

6. The code has been updated to include additional test cases. These methods are marked with the @Test annotation, indicating that they will be executed by the testing framework. It's important to note that the order in which the tests are run cannot be guaranteed.

```java
package lab8_202001465;

import static org.junit.Assert.*;

import org.junit.Before;
import org.junit.Test;

public class BoaTest {
	
	private Boa jen;
	private Boa ken;

	@Before
	public void setUp() throws Exception {
		//initialization
		jen = new Boa("Jennifer", 2, "grapes");
		ken = new Boa ("Kenneth", 3, "granola bars");
	}
	
	@Test 
	public void testIsHealthy() {
		//testing isHealthy for 2 objects
		assertEquals(false,jen.isHealthy());
		assertEquals(true,ken.isHealthy());
	}
	
	@Test 
	public void testFitsInCage() {
		//testing isHealthy for 2 objects		
		assertEquals(false,jen.fitsInCage(1)); // less than the size of cage
		assertEquals(false,jen.fitsInCage(2)); // equal to the size of cage		
		assertEquals(true,jen.fitsInCage(3)); // greater than the size of cage
	}
}
```

- The newly added test cases involve testing the functionality of two methods in the Boa class. In the first test case, we instantiate two Boa objects with distinct preferred foods, and verify that the isHealthy method returns false for the first object and true for the second object.

- In the second test case, we assess the fitsInCage method by generating three Boa objects with differing lengths, and evaluating whether they are able to fit in cages of varying lengths.

7. Running the two test cases - isHealthy() and fitsInCage()

![s3](https://user-images.githubusercontent.com/67496808/233610922-fd3264b8-a557-47e3-b5d8-99131e2dfc1b.png)


8. Adding a new method to the Boa class

```java
package lab8_202001465;

public class Boa {
	private String name;
	private int length; // the length of the boa, in feet
	private String favoriteFood;
	
	public Boa (String name, int length, String favoriteFood){
		this.name = name;
		this.length = length;
		this.favoriteFood = favoriteFood;
	}
	// returns true if this boa constrictor is healthy
	public boolean isHealthy(){
		return this.favoriteFood.equals("granola bars");
	}
	
	// returns true if the length of this boa constrictor is
	// less than the given cage length
	public boolean fitsInCage(int cageLength){
		return this.length < cageLength;
	}
	public int lengthInInches()
	{
		int LengthInInches=this.length*12;
		return LengthInInches;
	}
	
}
```

9. Adding test cases for new methods
```java
@Test
	public void testlengthInInches()
	{
		assertEquals(24,jen.lengthInInches());
		assertEquals(36,ken.lengthInInches());
	}
```

After running output:

Successful run:

![s5](https://user-images.githubusercontent.com/67496808/233610953-20ef4b25-49c0-4a88-b5b8-7bc14622d5e8.png)


Unsuccessful run:

![s4](https://user-images.githubusercontent.com/67496808/233610989-d8b21c1a-2a5d-4f5d-a7e9-a5d63e202331.png)






