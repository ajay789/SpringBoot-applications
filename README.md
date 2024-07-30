<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>
<!DOCTYPE html>
<html>
<head>
    <title>User Details</title>
    <script>
        function sendOTP() {
            var form = document.getElementById("userDetailsForm");
            form.action = "/sendOTP";
            form.submit();
        }

        function verifyOTP() {
            var form = document.getElementById("userDetailsForm");
            form.action = "/verifyOTP";
            form.submit();
        }
    </script>
</head>
<body>
    <h2>User Details</h2>
    <form id="userDetailsForm" method="post">
        First Name: <input type="text" name="firstName"><br>
        Middle Name: <input type="text" name="middleName"><br>
        Last Name: <input type="text" name="lastName"><br>
        Mobile Number: <input type="text" name="mobileNumber"><br>
        Email Id: <input type="text" name="email"><br>
        Branch: <input type="text" name="branch"><br>
        Pincode: <input type="text" name="pincode"><br>
        Mobile OTP: <input type="text" name="mobileOTP"><br>
        Email Id OTP: <input type="text" name="emailOTP"><br>
        <button type="button" onclick="sendOTP()">Send OTP</button>
        <button type="button" onclick="verifyOTP()">Submit</button>
    </form>
    <c:if test="${not empty message}">
        <p>${message}</p>
    </c:if>
</body>
</html>
