<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Form Submission</title>
</head>
<body>

    <h1>Contact Form</h1>

    <form id="contactForm">
        <label for="name">Name:</label>
        <input type="text" id="name" name="name" required><br>

        <label for="email">Email:</label>
        <input type="email" id="email" name="email" required><br>

        <label for="message">Message:</label>
        <textarea id="message" name="message" rows="4" required></textarea><br>

        <button type="button" onclick="submitForm()">Submit</button>
    </form>

    <script>
        function submitForm() {
            // Get form data
            const name = document.getElementById('name').value;
            const email = document.getElementById('email').value;
            const message = document.getElementById('message').value;

            // Prepare data for the API
            const formData = {
                name: name,
                email: email,
                message: message
            };

            // Send data to the API (replace 'API_ENDPOINT' with your actual API endpoint)
            fetch('API_ENDPOINT', {
                method: 'POST',
                headers: {
                    'Content-Type': 'application/json',
                },
                body: JSON.stringify(formData),
            })
            .then(response => {
                if (response.ok) {
                    // Show success notification
                    alert('Submission successful!');
                } else {
                    // Show error notification
                    alert('Submission failed. Please try again.');
                }
            })
            .catch(error => {
                console.error('Error during form submission:', error);
                // Show error notification
                alert('An error occurred. Please try again.');
            });
        }
    </script>

</body>
</html>
