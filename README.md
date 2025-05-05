<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Interactive Web Bundle (Embedded JS)</title>
    <style>
        /* Paste the CSS from the previous response here */
        body {
            font-family: sans-serif;
            line-height: 1.6;
            margin: 20px;
        }

        h1, h2 {
            color: #333;
        }

        section {
            margin-bottom: 40px;
            padding: 20px;
            border: 1px solid #eee;
            border-radius: 8px;
        }

        button {
            padding: 10px 15px;
            background-color: #007bff;
            color: white;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            margin-right: 10px;
        }

        button:hover {
            background-color: #0056b3;
        }

        /* Event Handling Styles */
        #hoverText {
            color: #555;
            transition: color 0.3s ease;
        }

        #hoverText:hover {
            color: red;
        }

        /* Interactive Elements Styles */
        .button-container {
            margin-bottom: 20px;
        }

        .gallery-container {
            margin-bottom: 20px;
        }

        .gallery-container img {
            display: block;
            margin-bottom: 10px;
        }

        .tabs-container {
            margin-bottom: 20px;
        }

        .tabs button {
            background-color: #ddd;
            color: #333;
            border-bottom: 2px solid transparent;
        }

        .tabs button.active {
            background-color: #eee;
            border-bottom-color: #007bff;
        }

        .tab-content {
            display: none;
            padding: 15px;
            border: 1px solid #ddd;
            border-top: none;
        }

        .tab-content.active {
            display: block;
        }

        .accordion-item {
            border: 1px solid #ddd;
            margin-bottom: 5px;
        }

        .accordion-header {
            width: 100%;
            text-align: left;
            background-color: #f9f9f9;
            padding: 10px;
            border: none;
            cursor: pointer;
            font-weight: bold;
        }

        .accordion-content {
            display: none;
            padding: 10px;
            border-top: 1px solid #eee;
        }

        .accordion-content.active {
            display: block;
        }

        .animation-example {
            margin-top: 20px;
        }

        #animatedBox {
            width: 50px;
            height: 50px;
            background-color: orange;
            position: relative; /* Needed for animation */
            transition: transform 0.5s ease-in-out; /* Animation for transformation */
        }

        #animatedBox.moved {
            transform: translateX(100px); /* Move the box */
        }


        /* Form Validation Styles */
        .form-group {
            margin-bottom: 15px;
        }

        .form-group label {
            display: block;
            margin-bottom: 5px;
            font-weight: bold;
        }

        .form-group input {
            width: 100%;
            padding: 8px;
            border: 1px solid #ccc;
            border-radius: 4px;
            box-sizing: border-box; /* Include padding in width */
        }

        .error-message {
            color: red;
            font-size: 0.9em;
            display: none; /* Hide by default */
        }

        .form-group input:invalid:not(:placeholder-shown) {
            border-color: red;
        }

        .form-group input:valid:not(:placeholder-shown) {
            border-color: green;
        }
    </style>
</head>
<body>

    <h1>Interactive Web Features (Embedded JS)</h1>

    <!-- Section 1: Event Handling -->
    <section id="event-handling">
        <h2>Event Handling</h2>
        <!-- Button click: Using the onclick attribute -->
        <button onclick="alert('Button clicked!')">Click Me!</button>
        <!-- Hover effects: Handled by CSS -->
        <p id="hoverText">Hover over me!</p>
        <p>Press a key on your keyboard.</p>
        <p id="keypressOutput"></p>
        <!-- Bonus: Secret action for a double-click or long press -->
        <button id="secretButton">Double Click/Long Press Me!</button>
        <p id="secretMessage"></p>
    </section>

    <hr>

    <!-- Section 2: Interactive Elements -->
    <section id="interactive-elements">
        <h2>Interactive Elements</h2>

        <div class="button-container">
            <!-- Button that changes text or color: Using the onclick attribute and a dedicated function -->
            <button id="changeButton" onclick="changeButtonTextAndColor()">Change My Text/Color</button>
        </div>

        <div class="gallery-container">
            <h3>Image Gallery</h3>
            <img id="galleryImage" src="image1.jpg" alt="Image 1" width="300">
            <!-- Image gallery buttons: Using onclick attributes -->
            <button onclick="prevImage()">Previous</button>
            <button onclick="nextImage()">Next</button>
        </div>

        <div class="tabs-container">
            <h3>Tabs</h3>
            <div class="tabs">
                <!-- Tab buttons: Using onclick attributes and passing the tab ID -->
                <button class="tab-button active" onclick="openTab(event, 'tab1')">Tab 1</button>
                <button class="tab-button" onclick="openTab(event, 'tab2')">Tab 2</button>
                <button class="tab-button" onclick="openTab(event, 'tab3')">Tab 3</button>
            </div>
            <div id="tab1" class="tab-content active">Content for Tab 1</div>
            <div id="tab2" class="tab-content">Content for Tab 2</div>
            <div id="tab3" class="tab-content">Content for Tab 3</div>
        </div>

        <div class="accordion-container">
            <h3>Accordion</h3>
            <div class="accordion-item">
                <!-- Accordion headers: Using onclick attributes -->
                <button class="accordion-header" onclick="toggleAccordion(this)">Section 1</button>
                <div class="accordion-content">Content for Section 1</div>
            </div>
            <div class="accordion-item">
                <button class="accordion-header" onclick="toggleAccordion(this)">Section 2</button>
                <div class="accordion-content">Content for Section 2</div>
            </div>
            <div class="accordion-item">
                <button class="accordion-header" onclick="toggleAccordion(this)">Section 3</button>
                <div class="accordion-content">Content for Section 3</div>
            </div>
        </div>

        <div class="animation-example">
            <h3>Animation Example</h3>
            <!-- Animation box: Using onclick attribute -->
            <div id="animatedBox" onclick="toggleAnimation()"></div>
        </div>

    </section>

    <hr>

    <!-- Section 3: Form Validation -->
    <section id="form-validation">
        <h2>Form Validation</h2>
        <!-- Form: Using the onsubmit attribute to call a validation function -->
        <form id="myForm" onsubmit="return validateForm(event)">
            <div class="form-group">
                <label for="name">Name:</label>
                <!-- Real-time feedback: Using the oninput attribute -->
                <input type="text" id="name" required oninput="validateName()">
                <span class="error-message" id="nameError"></span>
            </div>

            <div class="form-group">
                <label for="email">Email:</label>
                <!-- Real-time feedback: Using the oninput attribute -->
                <input type="email" id="email" required oninput="validateEmail()">
                <span class="error-message" id="emailError"></span>
            </div>

            <div class="form-group">
                <label for="password">Password:</label>
                <!-- Real-time feedback: Using the oninput attribute -->
                <input type="password" id="password" required minlength="8" oninput="validatePassword()">
                <span class="error-message" id="passwordError"></span>
            </div>

            <button type="submit">Submit</button>
        </form>
    </section>

    <script>
        // This is where we'll put our JavaScript functions

        // 1. Event Handling 🎈

        // Keypress Detection (Needs to be attached to the document)
        document.addEventListener('keypress', (event) => {
            const keypressOutput = document.getElementById('keypressOutput');
            keypressOutput.textContent = `You pressed: ${event.key}`;
        });

        // Bonus: Secret action for a double-click or long press
        const secretButton = document.getElementById('secretButton');
        const secretMessage = document.getElementById('secretMessage'); 
        let clickTimer;
        let isLongPress = false;

        secretButton.addEventListener('mousedown', () => {
            isLongPress = false;
            clickTimer = setTimeout(() => {
                isLongPress = true;
                secretMessage.textContent = 'Secret Long Press Action Activated!';
            }, 500); // 500ms for long press
        });

        secretButton.addEventListener('mouseup', () => {
            clearTimeout(clickTimer);
            if (!isLongPress) {
                // This is a regular click or double click
            }
        });

        secretButton.addEventListener('dblclick', () => {
            secretMessage.textContent = 'Secret Double Click Action Activated!';
        });


        // 2. Interactive Elements 🎮

        // Button that changes text or color
        let isChanged = false;
        function changeButtonTextAndColor() {
            const changeButton = document.getElementById('changeButton');
            if (isChanged) {
                changeButton.textContent = 'Change My Text/Color';
                changeButton.style.backgroundColor = '#007bff';
                isChanged = false;
            } else {
                changeButton.textContent = 'Changed!';
                changeButton.style.backgroundColor = 'green';
                isChanged = true;
            }
        }

        // Image gallery or slideshow
        const galleryImage = document.getElementById('galleryImage');
        const images = ['image1.jpg', 'image2.jpg', 'image3.jpg']; // Replace with your image paths
        let currentImageIndex = 0;

        function updateGalleryImage() {
            galleryImage.src = images[currentImageIndex];
        }

        function prevImage() {
            currentImageIndex--;
            if (currentImageIndex < 0) {
                currentImageIndex = images.length - 1; // Loop back to the last image
            }
            updateGalleryImage();
        }

        function nextImage() {
            currentImageIndex++;
            if (currentImageIndex >= images.length) {
                currentImageIndex = 0; // Loop back to the first image
            }
            updateGalleryImage();
        }

        // Tabs
        function openTab(event, tabId) {
            const tabButtons = document.querySelectorAll('.tab-button');
            const tabContents = document.querySelectorAll('.tab-content');

            // Remove active class from all buttons and content
            tabButtons.forEach(btn => btn.classList.remove('active'));
            tabContents.forEach(content => content.classList.remove('active'));

            // Add active class to the clicked button and corresponding content
            document.getElementById(tabId).classList.add('active');
            event.currentTarget.classList.add('active'); // event.currentTarget is the clicked button
        }

        // Accordion
        function toggleAccordion(header) {
            const accordionContent = header.nextElementSibling; // Get the next sibling element (the content)

            // Toggle the active class on the content
            accordionContent.classList.toggle('active');

            // Optional: Close other open accordion sections
            const accordionHeaders = document.querySelectorAll('.accordion-header');
            accordionHeaders.forEach(otherHeader => {
                if (otherHeader !== header) {
                    otherHeader.nextElementSibling.classList.remove('active');
                }
            });
        }

        // Bonus: Add some animation using JS or CSS ✨
        function toggleAnimation() {
            const animatedBox = document.getElementById('animatedBox');
            animatedBox.classList.toggle('moved'); // Add or remove the 'moved' class
        }


        // 3. Form Validation 📋✅

        function validateForm(event) {
            // Prevent the form from submitting by default
            event.preventDefault();

            // Perform validation
            const isNameValid = validateName();
            const isEmailValid = validateEmail();
            const isPasswordValid = validatePassword();

            // If all fields are valid, you can submit the form (or do something else)
            if (isNameValid && isEmailValid && isPasswordValid) {
                alert('Form submitted successfully!');
                // Here you would typically send the form data to a server
                // event.target.submit(); // Uncomment this to actually submit the form
                return true; // Allow form submission if valid (if you uncomment the submit line)
            } else {
                alert('Please fix the errors in the form.');
                return false; // Prevent form submission if invalid
            }
        }

        function validateName() {
            const nameInput = document.getElementById('name');
            const nameError = document.getElementById('nameError');
            if (nameInput.value.trim() === '') {
                nameError.textContent = 'Name is required.';
                nameError.style.display = 'block';
                return false;
            } else {
                nameError.textContent = '';
                nameError.style.display = 'none';
                return true;
            }
        }

        function validateEmail() {
            const emailInput = document.getElementById('email');
            const emailError = document.getElementById('emailError');
            // Basic email format validation using a regular expression
            const emailPattern = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
            if (emailInput.value.trim() === '') {
                emailError.textContent = 'Email is required.';
                emailError.style.display = 'block';
                return false;
            } else if (!emailPattern.test(emailInput.value)) {
                emailError.textContent = 'Please enter a valid email address.';
                emailError.style.display = 'block';
                return false;
            } else {
                emailError.textContent = '';
                emailError.style.display = 'none';
                return true;
            }
        }

        function validatePassword() {
            const passwordInput = document.getElementById('password');
            const passwordError = document.getElementById('passwordError');
            if (passwordInput.value.trim() === '') {
                passwordError.textContent = 'Password is required.';
                passwordError.style.display = 'block';
                return false;
            } else if (passwordInput.value.length < 8) {
                passwordError.textContent = 'Password must be at least 8 characters long.';
                passwordError.style.display = 'block';
                return false;
            } else {
                passwordError.textContent = '';
                passwordError.style.display = 'none';
                return true;
            }
        }

    </script>

</body>
