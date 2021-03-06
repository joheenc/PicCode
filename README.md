# PicCode

This project was created at DevFest 2019 at Columbia University by Alexander Wang, Ursula Ott, Joheen Chakraborty, and Michael Jan.

### Project Overview
Whiteboarding/coding by hand/reading code in the form of physical text (via textbook or otherwise) is a common practice among programmers/CS students. It would then be helpful to convert code in the form of literal text to a more usable form.

PicCode would enable anyone to take a picture of code and then text the picture to the phone number, (562) 374-7298. Then, they would receive a return text that either contains the output of the code or any errors in the code. This is extremely useful as all of it can be done via only a phone, and whiteboarding often results in buggy code that is hard to verify without compiling. It allows for flexibility and portability in coding, as one can quickly verify any handwritten code by simply taking a picture. As of now, PicCode only works for code in C.

### Description
We set up the entire program on the Google cloud platform so the app is always running without needing to be hosted by a local machine. A python/flask/ngrok program was used to receive the image from Twilio and to send the response back to the user (also via Twilio). The Google Vision cloud API's Optical Character Recognition tool was utilized to help with the physical text to code translation. Within the Google cloud virtual machine, we wrote a shell script that would compile the programs, determine any errors/outputs, correct for some simple common errors, and then send it back to Twilio via the aforementioned python program. This works for multiple mediums, including printer paper, lined paper, blackboards, and whiteboards.

### Examples

<img src="./img/test1.jpg" height=500/> 
<img src="./img/test2.jpg" height=500/> 
<img src="./img/test3.jpg" height=500/> 
<img src="./img/test4.jpg" height=500/> 
Example of error feedback to help debug.
<img src="./img/test5.jpg" height=500/> 
<img src="./img/test6.jpg" width=650/> 

### Future Direction
-Expand the possible code to more than just C. First steps would probably be Python and Java, which are among the most popular programming languages today.

-Look at ways to improve the accuracy of the machine learning text to code algorithm. Currently, we've coded some basic algorithms that correct simple compiler mistakes (missing semicolons for example). But the Google Cloud OCR tool is trained on English grammar and vocabulary, which is less accurate than training a model on code from the ground up. There are also a number of research papers (ex. https://arxiv.org/pdf/1801.10467.pdf) that use deep learning text investigating to correct code for syntax errors after the fact, and, given a dataset of programs, we'd be able to  better train our own text recognition machine learning model.

-Allow texting of parameters along with the image of the code

### Technologies Used
Google Cloud -  Google Vision cloud API's Optical Character Recognition tool to turn the image of the handwritten code into text; Compute Engine to hold our scripts, compile & run the code, and other backend
                
Twilio API - Allows user to text MMS to a number and have it saved on Google Cloud Platform, Allows the number to text back to the user with the output (or error message), as processed on GCP
             
Python w/ Flask - scripts, server

ngrok
