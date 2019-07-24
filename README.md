# Assignment4
using System;
using System.Text;
using System.Text.RegularExpressions;
using System.Threading;
using NUnit.Framework;
using OpenQA.Selenium;
using OpenQA.Selenium.Firefox;
using OpenQA.Selenium.Support.UI;

namespace SeleniumTests
{
    [TestFixture]
    public class AutomobileMissingfieldAllfieldMandatory
    {
        private IWebDriver driver;
        private StringBuilder verificationErrors;
        private string baseURL;
        private bool acceptNextAlert = true;

        [SetUp]
        public void SetupTest()
        {
            driver = new FirefoxDriver();
            baseURL = "http://localhost/web.html/";
            verificationErrors = new StringBuilder();
        }

        [TearDown]
        public void TeardownTest()
        {
            try
            {
                driver.Quit();
            }
            catch (Exception)
            {
                // Ignore errors if unable to close the browser
            }
            Assert.AreEqual("", verificationErrors.ToString());
        }

        [Test]
        public void Automobile_ActualMissingfield_ExpectedAllfieldMandatory()
        {
            driver.Navigate().GoToUrl("http://localhost/web.html");
            driver.FindElement(By.XPath("(.//*[normalize-space(text()) and normalize-space(.)='Vehicle Year'])[1]/following::input[2]")).Click();
            driver.FindElement(By.Name("name")).Clear();
            driver.FindElement(By.Name("name")).SendKeys("Desley");
            driver.FindElement(By.Name("Address")).Clear();
            driver.FindElement(By.Name("Address")).SendKeys("7778 nutcracker street");
            driver.FindElement(By.Name("City")).Clear();
            driver.FindElement(By.Name("City")).SendKeys("Toronto");
            driver.FindElement(By.Name("Phone")).Clear();
            driver.FindElement(By.Name("Phone")).SendKeys("226-897-5546");
            driver.FindElement(By.Name("email")).Clear();
            driver.FindElement(By.Name("email")).SendKeys("desley778@gmail.com");
            driver.FindElement(By.Name("Make")).Clear();
            driver.FindElement(By.Name("Make")).SendKeys("Honda");
            driver.FindElement(By.Name("Model")).Clear();
            driver.FindElement(By.Name("Model")).SendKeys("Accord");
            driver.FindElement(By.Name("Year")).Clear();
            driver.FindElement(By.Name("Year")).SendKeys("2019");
            driver.FindElement(By.XPath("(.//*[normalize-space(text()) and normalize-space(.)='Vehicle Year'])[1]/following::input[2]")).Click();
            Assert.AreEqual("Desley", driver.FindElement(By.XPath("/html/body/table/tbody/tr/td[1]")).Text);
            Assert.AreEqual("7778 nutcracker street", driver.FindElement(By.XPath("/html/body/table/tbody/tr/td[2]")).Text);
            Assert.AreEqual("Toronto", driver.FindElement(By.XPath("/html/body/table/tbody/tr/td[3]")).Text);
            Assert.AreEqual("226-897-5546", driver.FindElement(By.XPath("/html/body/table/tbody/tr/td[4]")).Text);
            Assert.AreEqual("desley778@gmail.com", driver.FindElement(By.XPath("/html/body/table/tbody/tr/td[5]")).Text);
            Assert.AreEqual("Honda", driver.FindElement(By.XPath("/html/body/table/tbody/tr/td[6]")).Text);
            Assert.AreEqual("Accord", driver.FindElement(By.XPath("/html/body/table/tbody/tr/td[7]")).Text);
            Assert.AreEqual("2019", driver.FindElement(By.XPath("/html/body/table/tbody/tr/td[8]")).Text);
            Assert.AreEqual("http://www.jdpower.com/cars/2019/Honda/Accord", driver.FindElement(By.XPath("/html/body/table/tbody/tr/td[9]/a")).Text);
            driver.FindElement(By.LinkText("http://www.jdpower.com/cars/2019/Honda/Accord")).Click();
        }
        [Test]
        public void Automobile_ActualInvalidvehicleentry_ExpectedPage404found()
        {
            driver.Navigate().GoToUrl("http://localhost/web.html");
            driver.FindElement(By.Name("name")).Clear();
            driver.FindElement(By.Name("name")).SendKeys("Wilson");
            driver.FindElement(By.Name("Address")).Clear();
            driver.FindElement(By.Name("Address")).SendKeys("45 coronation drive");
            driver.FindElement(By.Name("City")).Clear();
            driver.FindElement(By.Name("City")).SendKeys("Oakville");
            driver.FindElement(By.Name("Phone")).Clear();
            driver.FindElement(By.Name("Phone")).SendKeys("745-885-7877");
            driver.FindElement(By.Name("email")).Clear();
            driver.FindElement(By.Name("email")).SendKeys("wilson89@gmail.com");
            driver.FindElement(By.Name("Make")).Clear();
            driver.FindElement(By.Name("Make")).SendKeys("honda");
            driver.FindElement(By.Name("Model")).Clear();
            driver.FindElement(By.Name("Model")).SendKeys("fusion");
            driver.FindElement(By.Name("Year")).Clear();
            driver.FindElement(By.Name("Year")).SendKeys("2018");
            driver.FindElement(By.XPath("(.//*[normalize-space(text()) and normalize-space(.)='Vehicle Year'])[1]/following::input[2]")).Click();
            driver.FindElement(By.LinkText("http://www.jdpower.com/cars/2018/honda/fusion")).Click();
            Assert.AreEqual("404 - NOT FOUND", driver.FindElement(By.XPath("/html/body/div[3]/section/div/main/div[1]/div[1]/h1")).Text);
        }
        
        [Test]
        public void Automobile_ActualValidinputs_ExpectDirectToRespectiveJdpowerpage()
        {
            driver.Navigate().GoToUrl("http://localhost/web.html");
            driver.FindElement(By.Name("name")).Clear();
            driver.FindElement(By.Name("name")).SendKeys("Freddy");
            driver.FindElement(By.Name("Address")).Clear();
            driver.FindElement(By.Name("Address")).SendKeys("45 bresley drive");
            driver.FindElement(By.Name("City")).Clear();
            driver.FindElement(By.Name("City")).SendKeys("kitchener");
            driver.FindElement(By.Name("Phone")).Clear();
            driver.FindElement(By.Name("Phone")).SendKeys("519-474-8888");
            driver.FindElement(By.Name("email")).Clear();
            driver.FindElement(By.Name("email")).SendKeys("freddy90@gmail.com");
            driver.FindElement(By.Name("Make")).Clear();
            driver.FindElement(By.Name("Make")).SendKeys("Honda");
            driver.FindElement(By.Name("Model")).Clear();
            driver.FindElement(By.Name("Model")).SendKeys("civic");
            driver.FindElement(By.Name("Year")).Clear();
            driver.FindElement(By.Name("Year")).SendKeys("2019");
            driver.FindElement(By.XPath("(.//*[normalize-space(text()) and normalize-space(.)='Vehicle Year'])[1]/following::input[2]")).Click();
            Assert.AreEqual("Freddy", driver.FindElement(By.XPath("/html/body/table/tbody/tr/td[1]")).Text);
            Assert.AreEqual("45 bresley drive", driver.FindElement(By.XPath("/html/body/table/tbody/tr/td[2]")).Text);
            Assert.AreEqual("519-474-8888", driver.FindElement(By.XPath("/html/body/table/tbody/tr/td[4]")).Text);
            Assert.AreEqual("freddy90@gmail.com", driver.FindElement(By.XPath("/html/body/table/tbody/tr/td[5]")).Text);
            Assert.AreEqual("Honda", driver.FindElement(By.XPath("/html/body/table/tbody/tr/td[6]")).Text);
            Assert.AreEqual("civic", driver.FindElement(By.XPath("/html/body/table/tbody/tr/td[7]")).Text);
            Assert.AreEqual("2019", driver.FindElement(By.XPath("/html/body/table/tbody/tr/td[8]")).Text);
            Assert.AreEqual("http://www.jdpower.com/cars/2019/Honda/civic", driver.FindElement(By.XPath("/html/body/table/tbody/tr/td[9]/a")).Text);
            driver.FindElement(By.LinkText("http://www.jdpower.com/cars/2019/Honda/civic")).Click();
        }

 [Test]
        public void Automobile_ActualInvalidfiemailYearEntry_ExpectedDetectinvalidEmailandyearEntryTest()
        {
            driver.Navigate().GoToUrl("http://localhost/web.html");
            driver.FindElement(By.Name("name")).Clear();
            driver.FindElement(By.Name("name")).SendKeys("Thomas");
            driver.FindElement(By.Name("Address")).Clear();
            driver.FindElement(By.Name("Address")).SendKeys("333 brock avenue");
            driver.FindElement(By.Name("City")).Clear();
            driver.FindElement(By.Name("City")).SendKeys("Toronto");
            driver.FindElement(By.Name("Phone")).Clear();
            driver.FindElement(By.Name("Phone")).SendKeys("778-554-7454");
            driver.FindElement(By.Name("Make")).Clear();
            driver.FindElement(By.Name("Make")).SendKeys("mercedes benz");
            driver.FindElement(By.Name("Model")).Clear();
            driver.FindElement(By.Name("Model")).SendKeys("a class");
            driver.FindElement(By.XPath("(.//*[normalize-space(text()) and normalize-space(.)='Vehicle Year'])[1]/following::input[2]")).Click();
            driver.FindElement(By.Name("email")).Clear();
            driver.FindElement(By.Name("email")).SendKeys("thomas222@gmail.com");
            driver.FindElement(By.XPath("(.//*[normalize-space(text()) and normalize-space(.)='Vehicle Year'])[1]/following::input[2]")).Click();
            driver.FindElement(By.Name("Year")).Clear();
            driver.FindElement(By.Name("Year")).SendKeys("2019");
            driver.FindElement(By.XPath("(.//*[normalize-space(text()) and normalize-space(.)='Vehicle Year'])[1]/following::input[2]")).Click();
            Assert.AreEqual("thomas222@gmail.com", driver.FindElement(By.XPath("/html/body/table/tbody/tr/td[5]")).Text);
            Assert.AreEqual("2019", driver.FindElement(By.XPath("/html/body/table/tbody/tr/td[8]")).Text);
            driver.FindElement(By.LinkText("http://www.jdpower.com/cars/2019/mercedes-benz/a-class")).Click();
        }
        [Test]
        public void Automobile_ActualInvalidphonenumber_ExpectedDetectInvalidphonenumber()
        {
            driver.Navigate().GoToUrl("http://localhost/web.html");
            driver.FindElement(By.Name("name")).Clear();
            driver.FindElement(By.Name("name")).SendKeys("Dijo");
            driver.FindElement(By.Name("Address")).Clear();
            driver.FindElement(By.Name("Address")).SendKeys("111 vilson street");
            driver.FindElement(By.Name("City")).Clear();
            driver.FindElement(By.Name("City")).SendKeys("Cambridge");
            driver.FindElement(By.Name("Phone")).Clear();
            driver.FindElement(By.Name("Phone")).SendKeys("2264547845");
            driver.FindElement(By.Name("email")).Clear();
            driver.FindElement(By.Name("email")).SendKeys("dijo111@gmail.com");
            driver.FindElement(By.Name("Make")).Clear();
            driver.FindElement(By.Name("Make")).SendKeys("ford");
            driver.FindElement(By.Name("Model")).Clear();
            driver.FindElement(By.Name("Model")).SendKeys("fusion");
            driver.FindElement(By.Name("Year")).Clear();
            driver.FindElement(By.Name("Year")).SendKeys("2019");
            driver.FindElement(By.XPath("(.//*[normalize-space(text()) and normalize-space(.)='Vehicle Year'])[1]/following::input[2]")).Click();
            driver.FindElement(By.Name("Phone")).Clear();
            driver.FindElement(By.Name("Phone")).SendKeys("22645478452");
            driver.FindElement(By.XPath("(.//*[normalize-space(text()) and normalize-space(.)='Vehicle Year'])[1]/following::input[2]")).Click();
            driver.FindElement(By.Name("Phone")).Clear();
            driver.FindElement(By.Name("Phone")).SendKeys("226-454-7845");
            driver.FindElement(By.XPath("(.//*[normalize-space(text()) and normalize-space(.)='Vehicle Year'])[1]/following::input[2]")).Click();
            Assert.AreEqual("226-454-7845", driver.FindElement(By.XPath("/html/body/table/tbody/tr/td[4]")).Text);
            driver.FindElement(By.LinkText("http://www.jdpower.com/cars/2019/ford/fusion")).Click();
        }
        private bool IsElementPresent(By by)
        {
            try
            {
                driver.FindElement(by);
                return true;
            }
            catch (NoSuchElementException)
            {
                return false;
            }
        }

        private bool IsAlertPresent()
        {
            try
            {
                driver.SwitchTo().Alert();
                return true;
            }
            catch (NoAlertPresentException)
            {
                return false;
            }
        }

        private string CloseAlertAndGetItsText()
        {
            try
            {
                IAlert alert = driver.SwitchTo().Alert();
                string alertText = alert.Text;
                if (acceptNextAlert)
                {
                    alert.Accept();
                }
                else
                {
                    alert.Dismiss();
                }
                return alertText;
            }
            finally
            {
                acceptNextAlert = true;
            }
        }
    }
}
