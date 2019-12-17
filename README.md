# Bypass WordPress Upload Restriction with Polyglots

In this article I will bypass the Wordpress 5.3.1 Upload restrictions by using polymorphic files.

As PoC we will use a DOCX + JAR polyglot file available at: https://github.com/Polydet/polyglot-database/blob/master/files/DOCX%2BJAR.docx

![1](https://ciber.sejalivre.org/WP/1.png)

I downloaded the file with wget as below:

![1](https://ciber.sejalivre.org/WP/2.png)

Because it is a polymorphic Java and Microsoft Office file, I will run it first with Java, as follows:

![1](https://ciber.sejalivre.org/WP/3.png)


Its content is a simple "Hello World" in Java.

We will now open the polymorphic with MS Word to analyze its content:

![1](https://ciber.sejalivre.org/WP/4.png)

![1](https://ciber.sejalivre.org/WP/5.png)


This done, I will create a copy of the polymorphic, saving it as a JAR file to send it to our WordPress 5.3.1.

![1](https://ciber.sejalivre.org/WP/6.png)

![1](https://ciber.sejalivre.org/WP/7.png)


As expected, WordPress identifies the file as being prohibited under its security policies and does not allow upload.

![1](https://ciber.sejalivre.org/WP/8.png)


However, when uploading the .DOCX file WordPress does not validate its content and allows upload:

![1](https://ciber.sejalivre.org/WP/9.png)


In this scenario, an attacker could take advantage of the lack of validation of the file upload restriction in WordPress 5.3.1 to host malicious DOCX files (eg camouflaged in resumes). The victim, upon receiving by other means a spreadsheet containing a macro or even a PowerShell script, would execute malicious DOCX content.

![1](https://ciber.sejalivre.org/WP/11.png)

![1](https://ciber.sejalivre.org/WP/10.png)

This is the file hosted on WordPress 5.3.1: https://sejalivre.org/poc/wp-content/uploads/2019/12/DOCXJAR.docx

