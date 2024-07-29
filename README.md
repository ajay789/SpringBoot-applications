a:-

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
