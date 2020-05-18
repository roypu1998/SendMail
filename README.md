# SendMail

Hello everybody this repository for Java app to sending mail.
Before you using in this application you need change your email access 
settings at low security levels to make the program work.

Explain the program :

In the first step, we open a MAVEN file and add the Gmail API to it.
In the second stage we will create a class send emails.
In the third step we will add all javax.mail and java Swing imports.
Next we will start to create java swing variables and then define them in the constructor and create a main frame in a separate function.
In the frame, we want to add a menu bar that contains file and about menus when the file can allow the user to exit the app and about allow the user to get another frame containing the program key details.

After we arrange in the main frame all our variables including the arrangement of the panels and then our buttons allow us to do different actions.
We'll deal with the send button and put in the 'addActionListner' function to get user input (sender's email and password, recipient's mail, name, and of course the message) and also use 'javaxMail's' API and we can send the message via the entered email
