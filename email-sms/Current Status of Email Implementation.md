# Current Status of Email Implementation

Original Author: Josh Rimell
Updated by: Robert Brown - Summer 2026

> **Updated 2026:** The original version of this document referenced Gmail's "Less Secure Apps" setting, which Google removed entirely in 2024. Those sections have been corrected to use App Passwords. All other content is unchanged. For a full step-by-step walkthrough in a web app, see "Sending email on a C# Web Application.pdf" in this repo.

**Question: Can C# send an email using a Gmail account**

Yes, C# can be used to send emails through your Gmail account using the System.Net.Mail namespace. However, Gmail requires additional configuration before it will accept sign-ins from an application sending email programmatically.

Here's a basic example of how you can send an email using C# and Gmail's SMTP server.

Remember to replace "yourgmail@gmail.com" with your Gmail address and the password with an **App Password** (not your normal account password). Also, adjust the recipient's email address accordingly.

Gmail will reject your normal account password when signing in from an application. You must generate an App Password instead:

1. Enable 2-Step Verification on the Google account (required before App Passwords are available).
2. Go to myaccount.google.com → Security → App Passwords (searching "app passwords" in the settings search bar is the fastest way to find it).
3. Create one and use the generated 16-character password as your SMTP password.

See Google's official instructions: https://support.google.com/mail/answer/185833

Alternatively, you can use OAuth authentication for a more robust method suited to production applications.

For security reasons, avoid hardcoding sensitive information like passwords in your code. Consider using secure methods, such as environment variables or configuration files, to store and access sensitive data. Note that `appsettings.json` is usually committed to git — .NET user secrets (`dotnet user-secrets`) or environment variables are safer places for the App Password. Never commit an App Password to the repository.

Before using this code in a production environment, it's advisable to thoroughly test it and ensure that it complies with Google's security requirements and best practices.

## Template Code For Sending Emails from Gmail's Server

```csharp
using System;
using System.Net;
using System.Net.Mail;

class Program
{
    static void Main()
    {
        // Gmail credentials (replace with your Gmail address and an App Password)
        string senderEmail = "sender@gmail.com";
        string senderPassword = "YOUR_APP_PASSWORD"; // 16-char App Password, NOT your account password

        // Recipient's email address
        string recipientEmail = "recipient@gmail.com";

        // Create and configure the SMTP client
        SmtpClient smtpClient = new SmtpClient("smtp.gmail.com", 587);
        smtpClient.EnableSsl = true;
        smtpClient.UseDefaultCredentials = false;
        smtpClient.Credentials = new NetworkCredential(senderEmail, senderPassword);

        // Create the email message
        MailMessage mail = new MailMessage(senderEmail, recipientEmail);
        mail.Subject = "Test Email";
        mail.Body = "This is a test email sent from C#.";

        try
        {
            // Send the email
            smtpClient.Send(mail);
            Console.WriteLine("Test email sent successfully.");
        }
        catch (Exception ex)
        {
            Console.WriteLine("Failed to send test email. Error: " + ex.Message);
        }
    }
}
```

## Explanation of "Functions.cs"

*(Can be found under Services → Functions.cs — this section describes the ScavengerHunt project's implementation and is kept for historical reference.)*

This code is part of a system responsible for sending emails, specifically using Gmail's SMTP server, while keeping sensitive information like email passwords secure by using Google Secret Manager for storing and retrieving them. It demonstrates best practices for handling sensitive information and leveraging external services for secure credential storage.

The SMTP server for Gmail is a free SMTP server that anyone across the globe can use. It allows you to manage email transactions from your Gmail account via email clients or web applications. Email clients are user-end mail applications. Some of the most popular ones are Thunderbird, Outlook, and Mac Mail.

This code is C# class named Functions, which serves as a part of a larger application or service. Here's a breakdown of what the code does:

**Constructor with Configuration Injection:** The Functions class has a constructor that accepts an IConfiguration parameter injected through dependency injection. This allows it to access configuration settings from different sources, such as appsettings.json or environment variables.

**SendEmail Method:** This method (SendEmail) is responsible for sending an email using Gmail's SMTP server. It takes the recipient's email address, email subject, and email body as parameters.

It sets the environment variable GOOGLE_APPLICATION_CREDENTIALS to point to a JSON file (scrum-bums-042e94718ef6.json) containing Google Cloud credentials. This file is used for authentication purposes when interacting with Google services.

Retrieves email settings (EmailFrom) and password from the configuration using `_configuration.GetValue<string>("EmailSettings:EmailFrom")`. The email sender's address is obtained from the configuration, and the email password is retrieved using the Google Secret Manager API, to keep the password secure and not hardcoded in the code.

Configures an SMTP client (SmtpClient) to send emails through Gmail's SMTP server using SSL. It uses the retrieved email address and password for authentication.

Creates a MailMessage object with the provided recipient email, subject, and body.

Attempts to send the email using the configured SMTP client (client.Send(message)), catching any exceptions that might occur during the sending process.

**GetSecretAsync Method:** This method retrieves the email password from Google Secret Manager using the provided secretId. It makes an asynchronous call to Secret Manager, gets the latest secret version, and extracts the password data.

It initializes a SecretManagerServiceClient and retrieves the latest version of the specified secret (etsuscavengerhuntemail) from Secret Manager. The retrieved secret is the email password.

It decodes the retrieved password data from bytes to a string (passwordBytes.ToStringUtf8()) and returns it.
