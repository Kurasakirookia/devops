#3 Webpage.java

package org.test;

import org.testng.annotations.AfterTest;
import org.testng.annotations.BeforeTest;
import org.testng.annotations.Test;
import org.testng.Assert;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;




public class WebPageTest {

    static WebDriver driver;

    @BeforeTest
    public void  openBrowser()throws InterruptedException{
        System.setProperty("webdriver.chrome.driver","C:\\chromedriver-win64\\chromedriver.exe");
        driver=new ChromeDriver();
        driver.manage().window().maximize();
        Thread.sleep(1000);
        driver.get("https://jssateb.ac.in");
    }
        @Test
        public void titleValidationTest() {
            String actualTitle=driver.getTitle();
            String expected="JSSATEB";
            Assert.assertEquals(actualTitle,expected);
            Assert.assertTrue(actualTitle.contains("JSSATEB"),"title should contain jssateb");

        }

        @AfterTest
        public void closeBrowser() throws InterruptedException{
            Thread.sleep(1000);
            driver.quit();
        }

    }

#bild Gradle 
plugins {
    id 'application'
    id 'java'
}

group 'com.example'
version '1.0-SNAPSHOT'

repositories {
    mavenCentral()
}

dependencies {
    testImplementation 'org.junit.jupiter:junit-jupiter-api:5.8.1'
    testRuntimeOnly 'org.junit.jupiter:junit-jupiter-engine:5.8.1'
    // https://mvnrepository.com/artifact/org.seleniumhq.selenium/selenium-java
    implementation 'org.seleniumhq.selenium:selenium-java:2.41.0'
    // https://mvnrepository.com/artifact/org.squashtest.tm/spock-test-dependencies
    // https://mvnrepository.com/artifact/org.testng/testng
    testImplementation 'org.testng:testng:7.4.0'
}
test {
    useJUnitPlatform()
}
test{
    useTestNG()
}
application{
    mainClass='com.example.Main'
}

jar{
    manifest{
        attributes 'Main-Class':'com.example.Main'
    }
}







#2 pom.xml

<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.example</groupId>
    <artifactId>demo</artifactId>
    <version>1.0-SNAPSHOT</version>
    <!-- https://mvnrepository.com/artifact/org.seleniumhq.selenium/selenium-java -->
    <dependencies>
        <dependency>
            <groupId>org.seleniumhq.selenium</groupId>
            <artifactId>selenium-java</artifactId>
            <version>4.28.1</version>
        </dependency>

        <dependency>
            <groupId>org.openjfx</groupId>
            <artifactId>javafx-controls</artifactId>
            <version>20</version>
        </dependency>
        <dependency>
            <groupId>org.openjfx</groupId>
            <artifactId>javafx-fxml</artifactId>
            <version>20</version>
        </dependency>


    </dependencies>


    <properties>
        <maven.compiler.source>19</maven.compiler.source>
        <maven.compiler.target>19</maven.compiler.target>
        <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
    </properties>

</project>


# login tets


import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;



public class LoginTest {
    public static void main(String[] args)throws InterruptedException {
        WebDriver driver = new ChromeDriver();
        driver.get("https://www.saucedemo.com");
        driver.manage().window().maximize();

        driver.findElement(By.id("user-name")).sendKeys("standard-user");
        Thread.sleep(2000);
        driver.findElement(By.id("password")).sendKeys("secret-sauce");
        Thread.sleep(2000);
        driver.findElement(By.id("login-button")).click();
        Thread.sleep(2000);
        driver.quit();


    }
}
