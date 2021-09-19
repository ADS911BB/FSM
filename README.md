
<?php 
      
    
      include('db_connect/data_conn.php');

      $ID_Number = $psw = '';
      $errors= array('ID_Number' => '','psw'=>'');

     

        //Construct a query
          if ($_POST) {
            # code...
        
          $ID_Number =mysqli_real_escape_string($conn, $_POST['ID_Number']);
          $psw =mysqli_real_escape_string($conn, $_POST['psw']);

      $sql = "SELECT id_number,psw FROM sign_db WHERE id_number='$ID_Number' AND psw='$psw'";

      $results = mysqli_query($conn, $sql);

      if( mysqli_num_rows($results) == 1 ){

        session_start();
        $_SESSION['cloud']='true';

       header("location: /PheSite/output_site/resultpage.php");


      }else{
          
          $errors['psw'] = " <p>ID or Password is incorrect</>";


       }
  












}//end check



 ?>










<!DOCTYPE html>
<html>
<title>Pheunimaid.com</title>
<meta charset="UTF-8">
<meta name="Pheunimaid" content="This is an academic website of Physical and health education,University of Maiduguri">
<meta name="academic" content="updates,news,results">
<meta http-equiv="author" content="ADAM SALEH">
<meta http-equiv="content-language" content="en-us"> 
<meta name="viewport" content="width=device-width, initial-scale=1">
<link rel="stylesheet" href="https://www.w3schools.com/w3css/4/w3.css">
<link rel="stylesheet" href="https://www.w3schools.com/lib/w3-theme-black.css">
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css">











<style type="text/css">

body
{
  background-color: lightblue;
}

  /* Bordered form */
form {
  border: 3px solid #f1f1f1;
}

/* Full-width inputs */
input[type=text], input[type=password] {
  width: 100%;
  padding: 12px 20px;
  margin: 8px 0;
  display: inline-block;
  border: 1px solid #ccc;
  box-sizing: border-box;
  border-radius:15px;
}
input[type=text]:focus, input[type=password]:focus 
{
   background-color: #ddd;
   outline: none;
}

input[type=checkbox] {
  float: right;
}

/* Set a style for all buttons */
button {
  background-color: #04AA6D;
  color: white;
  padding: 14px 20px;
  margin: 8px 0;
  border: none;
  cursor: pointer;
  width: 100%;
  border-radius:15px;
}


/* Add a hover effect for buttons */
button:hover {
  opacity: 0.8;
}

/* Extra style for the cancel button (red) */
.cancelbtn {
  width: auto;
  padding: 10px 18px;
  background-color: #f44336;
}


/* Add padding to containers */
.container {
  padding: 10px;
  box-shadow: 2px 0px 8px 2px rgba(0, 0, 0, 0.2);
}

/* The "Forgot password" text */
span.psw {
  float: right;
  padding-top: 16px;
}

/* Change styles for span and cancel button on extra small screens */
@media screen and (max-width: 300px) {
  span.psw {
    display: block;
    float: none;
  }
  
}
/* The Modal (background) */
.modal {
  display: none; /* Hidden by default */
  position: fixed; /* Stay in place */
  z-index: 1; /* Sit on top */
  left: 0;
  top: 0;
  width: 100%; /* Full width */
  height: 100%; /* Full height */
  overflow: auto; /* Enable scroll if needed */
  background-color: rgb(0,0,0); /* Fallback color */
  background-color: rgba(0,0,0,0.4); /* Black w/ opacity */
  margin-top: 60px;
}

/* Modal Content/Box */
.modal-content {
  background-color: #fefefe;
  margin: 10% auto 15% auto; /* 15% from the top and centered */
  border:none;
  max-width: 300px;/* Could be more or less, depending on screen size */
  background:linear-gradient(lightblue,white);
  max-width: 300px;

}

/* The Close Button */
.close {
  /* Position it in the top right corner outside of the modal */
  position: absolute;
  right: 25px;
  top: 0;
  color: #000;
  font-size: 35px;
  font-weight: bold;
}

/* Close button on hover */
.close:hover,
.close:focus {
  color: red;
  cursor: pointer;
}

/* Add Zoom Animation */
.animate {
  -webkit-animation: animatezoom 0.6s;
  animation: animatezoom 0.6s
}

@-webkit-keyframes animatezoom {
  from {-webkit-transform: scale(0)}
  to {-webkit-transform: scale(1)}
}

@keyframes animatezoom {
  from {transform: scale(0)}
  to {transform: scale(1)}
}
a
{
  color: white;
  list-style-type: none;
}
.forgotpass
{
  color: blue;
}
@media screen and (max-width: 300px){
  span.psw {
    display: block;
    float: none;
  }
}


/* The Modal (background) */
.box {
  display: none; /* Hidden by default */
  position: fixed; /* Stay in place */
  z-index: 1; /* Sit on top */
  padding-top: 100px; /* Location of the box */
  left: 0;
  top: 0;
  width: 100%; /* Full width */
  height: 100%; /* Full height */
  overflow: auto; /* Enable scroll if needed */
  background-color: inherit; /* Fallback color */
  background-color: inherit; /* Black w/ opacity */
}

/* Modal Content */
.box-content {
  background-color:rgb(255,166,166);
  
  
  margin: auto;
  padding: 20px;
  border: 2px solid red;
  width: 55%;
  border-radius: 10px;
}

/* The Close Button */
.close {
  color: #aaaaaa;
  float: right;
  font-size: 28px;
  font-weight: bold;
}

.close:hover,
.close:focus {
  color: #000;
  text-decoration: none;
  cursor: pointer;
}

.box-content, p 
{
  text-align: center;
  font-family: helvetica;
  font-size: 15px;
  color: red;
  font-style: italic;
}
</style>


<body>

<!-- Trigger/Open The Modal -->





<!-- The Modal -->
<div id="myBox" class="box">
  <p id=myBtn><?php echo  $errors['psw']  ?></p>

  <!-- Modal content -->
  <div class="box-content">
    <span class="close">&times;</span>
   

  
  </div>

</div>

<script>
// Get the modal
var box = document.getElementById("myBox");

// Get the button that opens the modal
var btn = document.getElementById("myBtn");

// Get the <span> element that closes the modal
var span = document.getElementsByClassName("close")[0];

// When the user clicks the button, open the modal 
btn.onclick = function() {
  box.style.display = "block";
}

// When the user clicks on <span> (x), close the modal
span.onclick = function() {
  box.style.display = "none";
}

// When the user clicks anywhere outside of the modal, close it
window.onclick = function(event) {
  if (event.target == box) {
    box.style.display = "none";
  }
}
</script>


  <!-- Modal Content -->
  <form class="modal-content animate" action=" " method="POST">
    <p style="  text-align: center;font-family: helvetica;font-size: 15px;color: red;font-style: italic;"> <?php echo $errors['psw']; ?></p>
    
   
    <div class="container">
      <div class="container">
      <center><img src="Napherlogo.JPG"style="width:35%; border-radius: 15%; box-shadow: 5px 5px 2px 2px grey;" class="logo"></center>
    </div>
    <br>
      <i class="fa fa-id-card" aria-hidden="true"></i>
      <label for="id_number"><b>ID Number</b></label>
      <input type="text" placeholder=" 17/04/04/0000" name="ID_Number" value="<?php echo htmlspecialchars($ID_Number) ?>" >
     <!--  <div class="text-red"><?php //echo $errors['ID_Number']; ?></div> -->            
      <br>

      <i class="fa fa-lock" aria-hidden="true"></i>
      <label for="psw"><b>Password</b></label>
      <input type="password" placeholder="Password" id="myInput" name="psw" value="<?php echo htmlspecialchars($psw) ?>" >
      <!-- <div class="text-red"><?php //echo $errors['psw']; ?></div> -->
            <span style="float: right;">show pass</span><input type="checkbox" onclick="myFunction()">
      <script>
function myFunction() {
  var x = document.getElementById("myInput");
  if (x.type === "password") {
    x.type = "text";
  } else {
    x.type = "password";
  }
}
</script>
<br>
<br>


      <button type="submit">LOGIN</button>
      <a href="/PheSite/changes_input_site/forgotpass.php" class="forgotpass">Forgot password</a>
    </div>

    <div class="container" style="background-color:#f1f1f1">
      <a href="/PheSite/first_page/firstpage.php"><button type="button" onclick="document.getElementById('id01').style.display='none'" class="cancelbtn">Cancel</button></a>
       <a href="/PheSite/input_site/sign.php"><button type="button" style="float: right; background-color: blue;" class="cancelbtn">Sign In</button></a>
    
    </div>
  </form>
</div>
<script>

// When the user clicks anywhere outside of the modal, close it
window.onclick = function(event) {
  if (event.target == modal) {
    modal.style.display = "none";
  }
}
</script>

</body>
</html>
