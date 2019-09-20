## Assignment 2 - Selenium

1. Install Selenium-library (https://www.seleniumhq.org/download/) into your IDE.
2. Run following scenario with help of code below.
3. Create doc-report with some screens.

### Scenario

1. Open Firefox browser.
2. Maximize the browser window.
3. Navigate to “https://ssau.ru/english”.
4. Write a method to print PASS if the title of the page matches with “Samara University” else FAIL. (If you are familiar with testng or junit use assert statement like assert.assertequals(actual, expected) to give a verdict of pass or fail.
5. Navigate to Facebook page (https://www.facebook.com)
6. Navigate back to Samara University website.
7. Print the URL of the current page.
8. Navigate forward.
9. Reload the page.
10. Close the Browser.

### Helpful code

```
package assignments;
 
import java.util.concurrent.TimeUnit;
 
import org.openqa.selenium.firefox.FirefoxDriver;
 
public class Assignment1 {
 
	// Creating an instance of Firefox Browser
	FirefoxDriver driver;
	String ssauUrl = "https://ssau.ru/english";
	String facebookUrl = "https://www.facebook.com";
 
	public void invokeBrowser() {
 
		System.setProperty("webdriver.gecko.driver",
				"C:\\Users\\User\\workspace\\libs\\geckodriver-v0.20.1-win64\\geckodriver.exe");
		driver = new FirefoxDriver();
 
		driver.manage().window().maximize();
 
		driver.manage().timeouts().pageLoadTimeout(20, TimeUnit.SECONDS);
 
		driver.get(ssauUrl);
 
		String titleOfThePage = driver.getTitle();
 
		if (titleOfThePage.equals("Samara University")) {
			System.out.println("Test case PASS");
		} else {
			System.out.println("Test case FAIL");
		}
 
	}
 
	public void navigateCommands() {
		driver.navigate().to(facebookUrl);
 
		String currentUrl = driver.getCurrentUrl();
 
		System.out.println("Current URL :: " + currentUrl);
		driver.navigate().back();
 
		driver.navigate().refresh();
 
		driver.navigate().refresh();
	}
 
	public static void main(String[] args) {
		Assignment1 assignment = new Assignment1();
 
		assignment.invokeBrowser();
 
	}
 
}
```