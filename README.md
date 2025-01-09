# signup-and-login-page
java script
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>

    <script src="https://cdn.jsdelivr.net/npm/sweetalert2@11"></script>
</head>

<body>

    username:<input type="text" placeholder="enter username" id="username" />
    email:<input type="email" placeholder="enter email" id="email" />
    password:<input type="password" placeholder="enter password" id="password" />
    <button onclick="signup()">signup</button>

    <script>
        let signup = () => {
            let usernamevalue = document.getElementById("username").value
            let emailvalue = document.getElementById("email").value
            let passwordvalue = document.getElementById("password").value

            let userdata = {
                "username": usernamevalue,
                "email": emailvalue,
                "password": passwordvalue
            }
            let alreadyusers = JSON.parse(localStorage.getItem("signup")) || []

            let existuser = alreadyusers.filter(user => user.email == emailvalue)
            let groot = existuser[0]

            if (!groot) {
                Swal.fire({
                    title: "Signup Sucesss..",
                    icon: "success"
                });
                alreadyusers.push(userdata)
                localStorage.setItem("signup", JSON.stringify(alreadyusers))

            }
            else {
                Swal.fire({
                    icon: "error",
                    title: "Already Uses!...",
                });
            }



        };
    </script>

</body>

</html>

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    
    <!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>login page </title>
</head>
<script src="https://cdn.jsdelivr.net/npm/sweetalert2@11"></script>
<body>
    email:<input type="email" placeholder="enter email" id="email"/>
    password:<input type="password" placeholder="enter password" id="password"/>
    <button onclick="login()">login</button>


    <script>
        let login=()=>{
            let emailvalue=document.getElementById("email").value 
            let passwordvalue=document.getElementById("password").value 

            let users=JSON.parse(localStorage.getItem("signup"))
            let existdata=users.filter(user=> user.email==emailvalue)
            let validdata=existdata[0]

            if (!validdata) {
                let timerInterval;
Swal.fire({
  title: "email is wrounge",
  html: "I will close in <b></b> milliseconds.",
  timer: 2000,
  timerProgressBar: true,
  didOpen: () => {
    Swal.showLoading();
    const timer = Swal.getPopup().querySelector("b");
    timerInterval = setInterval(() => {
      timer.textContent = `${Swal.getTimerLeft()}`;
    }, 100);
  },
  willClose: () => {
    clearInterval(timerInterval);
  }
}).then((result) => {
  /* Read more about handling dismissals below */
  if (result.dismiss === Swal.DismissReason.timer) {
    console.log("I was closed by the timer");
  }
});
                
            }else if(validdata.email==emailvalue && validdata.password==passwordvalue){
                Swal.fire({
                    title: "Login Sucesss..",
                    icon: "success"
                });
            }else if(validdata.password==""){
                Swal.fire("enter the password");
            }else if(validdata.email!=emailvalue){
                Swal.fire({
  title: "wrounge email",
  showClass: {
    popup: `
      animate__animated
      animate__fadeInUp
      animate__faster
    `
  },
  hideClass: {
    popup: `
      animate__animated
      animate__fadeOutDown
      animate__faster
    `
  }
});
            }else if(validdata.password!=passwordvalue){
                Swal.fire({
  title: "wrounge password",
  showClass: {
    popup: `
      animate__animated
      animate__fadeInUp
      animate__faster
    `
  },
  hideClass: {
    popup: `
      animate__animated
      animate__fadeOutDown
      animate__faster
    `
  }
});
            }else{
                alert("invalid details")
            }


        }
       
    </script>
    


</body>
</html>
