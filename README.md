# SpringBoot-applications
Spring boot crud operation

<!DOCTYPE html>
<html>
<head>
    <title>User Details</title>
    <script>
        function sendOTP() {
            var mobileNumber = document.getElementById("mobileNumber").value;
            var email = document.getElementById("email").value;

            var xhr = new XMLHttpRequest();
            xhr.open("POST", "/sendOTP", true);
            xhr.setRequestHeader("Content-type", "application/x-www-form-urlencoded");
            xhr.onreadystatechange = function () {
                if (xhr.readyState == 4 && xhr.status == 200) {
                    alert(xhr.responseText);
                }
            };
            xhr.send("mobileNumber=" + mobileNumber + "&email=" + email);
        }

        function verifyOTP() {
            var mobileOTP = document.getElementById("mobileOTP").value;
            var emailOTP = document.getElementById("emailOTP").value;

            var xhr = new XMLHttpRequest();
            xhr.open("POST", "/verifyOTP", true);
            xhr.setRequestHeader("Content-type", "application/x-www-form-urlencoded");
            xhr.onreadystatechange = function () {
                if (xhr.readyState == 4 && xhr.status == 200) {
                    if (xhr.responseText == "OTP verified successfully") {
                        document.getElementById("userDetailsForm").submit();
                    } else {
                        alert("Invalid OTP");
                    }
                }
            };
            xhr.send("mobileOTP=" + mobileOTP + "&emailOTP=" + emailOTP);
        }
    </script>
</head>
<body>
    <form id="userDetailsForm" action="SubmitDetails" method="post">
        First Name: <input type="text" name="firstName"><br>
        Middle Name: <input type="text" name="middleName"><br>
        Last Name: <input type="text" name="lastName"><br>
        Mobile Number: <input type="text" id="mobileNumber" name="mobileNumber"><br>
        Email Id: <input type="text" id="email" name="email"><br>
        Branch: <input type="text" name="branch"><br>
        Pincode: <input type="text" name="pincode"><br>
        Mobile OTP: <input type="text" id="mobileOTP" name="mobileOTP"><br>
        Email Id OTP: <input type="text" id="emailOTP" name="emailOTP"><br>
        <button type="button" onclick="sendOTP()">Send OTP</button>
        <button type="button" onclick="verifyOTP()">Submit</button>
    </form>
</body>
</html>
