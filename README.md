<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>PAN Number Finder</title>
    <style>
        /* Animation */
        @keyframes buttonAnimation {
            0% {
                transform: scale(1);
            }
            50% {
                transform: scale(1.1);
            }
            100% {
                transform: scale(1);
            }
        }

        .button-container {
            display: flex;
            flex-wrap: wrap;
            justify-content: space-around;
            margin-top: 20px;
        }

        .button {
            margin: 10px;
            padding: 10px 20px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            font-size: 16px;
            font-weight: bold;
            animation-duration: 1s;
            animation-iteration-count: infinite;
        }

        .find-button {
            background-color: #FF5733; /* Orange */
            color: white;
            animation-name: buttonAnimation;
        }

        .download-nsdl-button {
            background-color: #4CAF50; /* Green */
            color: white;
            animation-name: buttonAnimation;
        }

        .download-uti-button {
            background-color: #008CBA; /* Blue */
            color: white;
            animation-name: buttonAnimation;
        }

        .apply-nsdl-button {
            background-color: #FFC300; /* Yellow */
            color: white;
            animation-name: buttonAnimation;
        }

        .apply-uti-button {
            background-color: #800080; /* Purple */
            color: white;
            animation-name: buttonAnimation;
        }

        .free-apply-button {
            background-color: #FF5733; /* Orange */
            color: white;
            animation-name: buttonAnimation;
        }

        .upi-button {
            background-color: #008CBA; /* Blue */
            color: white;
            animation-name: buttonAnimation;
        }

        .note {
            font-weight: normal;
            color: #333;
            margin-top: 10px;
        }

        .menu-icon {
            position: absolute;
            top: 10px;
            right: 10px;
            cursor: pointer;
        }

        .menu-icon::before,
        .menu-icon::after {
            content: '';
            display: block;
            width: 20px;
            height: 3px;
            background-color: #333;
        }

        .menu-icon::before {
            margin-bottom: 5px;
        }

        .menu-icon::after {
            margin-top: 5px;
        }

        /* Hide the buttons initially */
        .hidden {
            display: none;
        }

        /* Fullscreen image */
        .fullscreen-image {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-image: url('https://i.postimg.cc/sDc1ZZ3d/20240509-181353.jpg');
            background-size: cover;
            background-position: center;
            display: none;
            z-index: 9999;
        }
    </style>
</head>
<body>
    <div class="fullscreen-image" id="fullscreenImage"></div>
    <div class="container">
        <div class="menu-icon" onclick="toggleMenu()"></div>
        <h2>PAN Number Finder</h2>
        <div class="form-group">
            <label for="aadharNumber">Enter Aadhar Number:</label>
            <input type="text" id="aadharNumber" placeholder="Enter Aadhar number...">
        </div>
        <button class="button find-button" onclick="openWhatsApp()">Find PAN Number</button>
        <div id="can you find my pan number"></div>

        <div class="button-container">
            <!-- NSDL PAN card PDF download button -->
            <button class="button download-nsdl-button" onclick="downloadNSDLPAN()">Download NSDL PAN Card PDF</button>

            <!-- UTI PAN card PDF download button -->
            <button class="button download-uti-button" onclick="downloadUtilityPAN()">Download UTI PAN Card PDF</button>

            <!-- Apply for new e-PAN card through NSDL -->
            <button class="button apply-nsdl-button" onclick="applyNSDLePAN()">Apply New e-PAN (NSDL)</button>

            <!-- Apply for new e-PAN card through UTI -->
            <button class="button apply-uti-button" onclick="applyUTIePAN()">Apply New e-PAN (UTI)</button>

            <!-- Free PAN card apply button -->
            <button class="button free-apply-button" onclick="applyFreePAN()">Apply Free PAN Card</button>

            <!-- NSDL PAN card apply button -->
            <button class="button apply-nsdl-button" onclick="applyNSDLPAN()">Apply NSDL PAN Card</button>

            <!-- UTI PAN card apply button -->
            <button class="button apply-uti-button" onclick="applyUtilityPAN()">Apply UTI PAN Card</button>

            <!-- New UPI app use without debit card button -->
            <button class="button upi-button" onclick="useUPIApp()">Use New UPI App without Debit Card</button>

            <!-- Button to show when three dots are clicked -->
            <button id="pan-server-button" class="button hidden" onclick="openPanServerForm()">PAN Number Find Server 2</button>

            <!-- Customer Support button -->
            <button id="customer-support-button" class="button hidden" onclick="redirectToCustomerSupport()">Customer Support</button>
        </div>

        <div class="note">Note: This PAN Finder app is only in beta version.</div>
        <div class="note">Note: Sign up in the new UPI app and get a ₹5 bonus for sending a minimum of ₹101. Also, get ₹10 for each referral.</div>
    </div>
    
    <script>
        // Show the fullscreen image for 3 seconds
        document.addEventListener('DOMContentLoaded', function() {
            var fullscreenImage = document.getElementById('fullscreenImage');
            fullscreenImage.style.display = 'block';
            setTimeout(function() {
                fullscreenImage.style.display = 'none';
            }, 3000);
        });

        function toggleMenu() {
            var panServerButton = document.getElementById('pan-server-button');
            var customerSupportButton = document.getElementById('customer-support-button');
            
            // Toggle visibility of the buttons
            panServerButton.classList.toggle('hidden');
            customerSupportButton.classList.toggle('hidden');
        }

        function openPanServerForm() {
            window.open('https://docs.google.com/forms/d/e/1FAIpQLSdqHMsVXsDsAOX5YnuNM8OIOcT5AwACjz9X8OcRqC6AN9p9zQ/viewform?usp=sf_link');
        }

        function redirectToCustomerSupport() {
            window.location.href = 'mailto:pannumberfinderofficial@gmail.com';
        }

        // JavaScript functions for button actions
        function openWhatsApp() {
            window.open('https://wa.me/916262348349/?text=Can%20you%20find%20my%20PAN%20number%3F');
        }

        function downloadNSDLPAN() {
            window.open('https://www.onlineservices.nsdl.com/paam/requestAndDownloadEPAN.html');
        }

        function downloadUtilityPAN() {
            window.open('https://www.pan.utiitsl.com/PAN_ONLINE/ePANCard');
        }

        function applyNSDLePAN() {
            window.open('https://tin.tin.nsdl.com/pan2');
        }

        function applyUTIePAN() {
            window.open('https://www.utiitsl.com/');
        }

        function applyFreePAN() {
            window.open('https://www.incometax.gov.in/iec/foportal/');
        }

        function applyNSDLPAN() {
            window.open('https://tin.tin.nsdl.com/pan2');
        }

        function applyUtilityPAN() {
            window.open('https://www.utiitsl.com/');
        }

        function useUPIApp() {
            window.open('https://tinyurl.com/myjbmb86?refCode=NTC0NT');
        }
    </script>
</body>
</html>
