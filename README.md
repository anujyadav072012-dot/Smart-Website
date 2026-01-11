<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Smart Web</title>
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<style>
body{
  margin:0;
  font-family: Arial, sans-serif;
  background:linear-gradient(to right,#74ebd5,#acb6e5);
}
#login{
  max-width:320px;
  margin:100px auto;
  background:white;
  padding:20px;
  border-radius:10px;
  box-shadow:0 0 10px #000;
}
header{
  background:#2c3e50;
  color:white;
  padding:15px;
  text-align:center;
}
nav{
  background:#34495e;
  text-align:center;
  padding:10px;
}
nav a{
  color:white;
  margin:8px;
  text-decoration:none;
  font-weight:bold;
}
section{
  display:none;
  padding:20px;
  background:white;
  margin:10px;
  border-radius:10px;
}
button{
  background:#3498db;
  color:white;
  border:none;
  padding:8px;
  width:100%;
  border-radius:5px;
}
input, textarea{
  width:100%;
  padding:8px;
  margin:5px 0;
}
.post{
  background:#ecf0f1;
  padding:10px;
  margin:10px 0;
  border-radius:5px;
}
</style>
</head>

<body>

<!-- LOGIN -->
<div id="login">
  <h2>Sign In – Smart Web</h2>
  <input id="user" placeholder="Username">
  <input id="pass" type="password" placeholder="Password">
  <button onclick="login()">Login</button>
  <p id="error" style="color:red;"></p>
</div>

<!-- WEBSITE -->
<div id="site" style="display:none;">

<header>
  <h1>Smart Web</h1>
  <p>Learn • Create • Grow</p>
</header>

<nav>
  <a onclick="show('home')">Home</a>
  <a onclick="show('about')">About Us</a>
  <a onclick="show('video')">Video</a>
  <a onclick="show('photo')">Photo</a>
  <a onclick="show('privacy')">Privacy</a>
</nav>

<section id="home">
  <h2>Home</h2>

  <!-- ADMIN POST -->
  <div id="admin">
    <h3>Add New Post</h3>
    <textarea id="postText" placeholder="Write your post..."></textarea>
    <button onclick="addPost()">Post</button>
  </div>

  <div id="posts"></div>
</section>

<section id="about">
  <h2>About Us</h2>
  <p>Smart Web ek educational website hai jo learning ke liye banayi gayi hai.</p>
</section>

<section id="video">
  <h2>Videos</h2>
  <iframe width="100%" height="200"
  src="https://www.youtube.com/embed/dQw4w9WgXcQ"></iframe>
</section>

<section id="photo">
  <h2>Photos</h2>
  <img src="https://via.placeholder.com/300" width="100%">
</section>

<section id="privacy">
  <h2>Privacy Policy</h2>
  <p>Hum users ki privacy ka poora dhyan rakhte hain.</p>
</section>

</div>

<script>
// 🔐 CHANGE LOGIN DETAILS HERE
const ADMIN_USER = "admin";
const ADMIN_PASS = "1234";

function login(){
  let u = user.value;
  let p = pass.value;
  if(u===ADMIN_USER && p===ADMIN_PASS){
    login.style.display="none";
    site.style.display="block";
    show('home');
  } else {
    error.innerText="Wrong username or password";
  }
}

function show(id){
  document.querySelectorAll("section").forEach(s=>s.style.display="none");
  document.getElementById(id).style.display="block";
}

function addPost(){
  let text = postText.value;
  if(text==="") return;
  let div = document.createElement("div");
  div.className="post";
  div.innerText=text;
  posts.prepend(div);
  postText.value="";
}
</script>

</body>
</html>
