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
