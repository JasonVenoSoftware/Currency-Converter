# Currency-Converter

# Summarize the project and what problem it was solving.
This program scrapes a website called x-rates.com, acquires the current exchange rates between the U.S. Dollar and other common currencies, and allows the user to calculate the exact worth of their U.S. money in other currencies.  

# What did you do particularly well?
This project did a simple web scrape using urllib3 and BeautifulSoup, which was short and efficient.  It also used tkinter to display clean, simplistic date for the user.  

# Where could you enhance your code?  How would these improvements make your code more efficient, secure, and so on?
I could allow the user to choose a starting currency and an ending currency, so the user could convert from Euros to USD, or Yens to Pesos.  

# Which pieces of the code did you find the most challenging to write, and how did you overcome this?  What tools or resources are you adding to your support network?
This was my first web scraping project, so the majority of the time spent was learning how to use urllib3 and BeautifulSoup, as well as how to traverse the HTML file of the website.  After I figured out how to acquire the exchange rates (which was thanks mostly to a Youtube channel called Tech With Tim), it was easy to give the user the desired capabilities with the tkinter program.  

# What skills from this project will be particularly transferable to other projects or course work?
The most valuable thing I learned during this project was how to traverse an HTML file.  Though this only required me to learn the very basics of how an HTML file works, it still stands as a great foundation to future work with websites, whether that be creating them or scraping them.  

# How did you make this program maintainable, readable, and adaptable?
This was a very simple program, consisting of just two functions and some web scraping/tkinter code.  The functions were short, which makes it easy to read them and understand what they do.  It would be extremely easy to add more currency options, by simply scraping more exchange rates and adding more buttons to the tkinter program.  
