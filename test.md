To send an email purely from the frontend without a backend server, you can use a service like EmailJS, which allows you to send emails directly from JavaScript running in the browser. Here’s how you can set it up in a single HTML file:

### Step-by-Step Guide

1. **Sign up for EmailJS** and get your service ID, template ID, and user ID.
2. **Create a new email template** in EmailJS if you haven't already.

### HTML and JavaScript in One File





font-family: Inria Serif !important;





```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Send Email Example</title>
    <script src="https://cdn.emailjs.com/dist/email.min.js"></script>
    <script>
      document.addEventListener("DOMContentLoaded", (event) => {
        // Initialize EmailJS with your user ID
        emailjs.init("YOUR_USER_ID");

        // Add event listener to the form
        document
          .getElementById("contact-form")
          .addEventListener("submit", function (event) {
            event.preventDefault(); // Prevent the default form submission

            // Get service and template IDs from EmailJS
            const serviceID = "YOUR_SERVICE_ID";
            const templateID = "YOUR_TEMPLATE_ID";

            // Get form values
            const templateParams = {
              name: document.getElementById("name").value,
              email: document.getElementById("email").value,
              message: document.getElementById("message").value,
            };

            // Send the email using EmailJS
            emailjs.send(serviceID, templateID, templateParams).then(
              (response) => {
                alert(
                  "Email sent successfully! " +
                    response.status +
                    " " +
                    response.text
                );
              },
              (error) => {
                alert("Failed to send email. " + error);
              }
            );
          });
      });
    </script>
  </head>
  <body>
    <form id="contact-form">
      <label for="name">Name:</label>
      <input type="text" id="name" name="name" required /><br /><br />

      <label for="email">Email:</label>
      <input type="email" id="email" name="email" required /><br /><br />

      <label for="message">Message:</label>
      <textarea id="message" name="message" required></textarea><br /><br />

      <button type="submit">Send Email</button>
    </form>
    <form action="/action_page.php">
      <label for="cars">Choose a car:</label>
      <select name="cars" id="cars">
        <option value="volvo">Volvo</option>
        <option value="saab">Saab</option>
        <option value="opel">Opel</option>
        <option value="audi">Audi</option>
      </select>
      <br /><br />
      <input type="submit" value="Submit" />
    </form>
  </body>
</html>
```

### Instructions

1. **Replace `YOUR_USER_ID`, `YOUR_SERVICE_ID`, and `YOUR_TEMPLATE_ID`** in the JavaScript section with the appropriate values from your EmailJS account.
2. **Open the HTML file in a browser** to use the form. When you submit the form, it will send an email using the EmailJS service.

This setup allows you to send an email directly from the frontend using only HTML and JavaScript with the help of EmailJS.

    <!-- <form action="https://formsubmit.co/dasarghyaslg11@gmail.com" method="POST">
        <input type="text" name="name" required>
        <input type="email" name="email" required>
        <button type="submit">Send</button>
    </form> -->
