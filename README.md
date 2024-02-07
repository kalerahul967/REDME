# REDME

import org.junit.After;
import org.junit.Before;
import org.junit.Test;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;
import static org.junit.Assert.assertTrue;

public class EntrataTests {

    private WebDriver driver;

    @Before
    public void setUp() {
        // Set up WebDriver
        System.setProperty("webdriver.chrome.driver", "path/to/chromedriver");
        driver = new ChromeDriver();
    }

    @Test
    public void testHomePageTitle() {
        // Test if homepage title is correct
        driver.get("https://www.entrata.com/");
        String expectedTitle = "Entrata | Multifamily Property Management Software";
        String actualTitle = driver.getTitle();
        assertTrue(actualTitle.contains(expectedTitle));
    }

    @Test
    public void testNavigationToSolutionsPage() {
        // Test navigation to solutions page
        driver.get("https://www.entrata.com/");
        driver.findElement(By.linkText("Solutions")).click();
        String expectedUrl = "https://www.entrata.com/solutions";
        String actualUrl = driver.getCurrentUrl();
        assertTrue(actualUrl.contains(expectedUrl));
    }

    // Add more tests as needed

    @After
    public void tearDown() {
        // Quit WebDriver after each test
        if (driver != null) {
            driver.quit();
        }
    }
}
