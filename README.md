<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Black Ink Studio</title>

<script src="https://cdnjs.cloudflare.com/ajax/libs/qrcodejs/1.0.0/qrcode.min.js"></script>

<style>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: Arial, sans-serif;
}

body {
    background: #0a0a0a;
    color: white;
    overflow-x: hidden;
}

/* HERO */
.hero {
    height: 100vh;
    background: url('https://images.unsplash.com/photo-1617042375876-a13e36732a04') center/cover;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    text-align: center;
    position: relative;
}

.hero::after {
    content: "";
    position: absolute;
    width: 100%;
    height: 100%;
    background: rgba(0,0,0,0.6);
}

.hero h1 {
    font-size: 70px;
    z-index: 2;
    letter-spacing: 5px;
}

.hero p {
    z-index: 2;
    opacity: 0.8;
}

/* NAV */
nav {
    position: fixed;
    top: 0;
    width: 100%;
    background: rgba(0,0,0,0.8);
    padding: 15px;
    text-align: center;
    z-index: 1000;
}

nav a {
    color: white;
    margin: 0 15px;
    text-decoration: none;
    transition: 0.3s;
}

nav a:hover {
    color: crimson;
}

/* SECTIONS */
section {
    padding: 80px 10%;
}

/* GALLERY */
.filters {
    text-align: center;
    margin-bottom: 20px;
}

.filters button {
    background: none;
    border: 1px solid white;
    color: white;
    padding: 8px 15px;
    margin: 5px;
    cursor: pointer;
    transition: 0.3s;
}

.filters button:hover {
    background: crimson;
}

.gallery {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: 15px;
}

.gallery img {
    width: 100%;
    height: 300px;
    object-fit: cover;
    cursor: pointer;
    transition: 0.4s;
    border-radius: 10px;
}

.gallery img:hover {
    transform: scale(1.05);
}

/* MODAL */
.modal {
    display: none;
    position: fixed;
    top:0;
    left:0;
    width:100%;
    height:100%;
    background: rgba(0,0,0,0.9);
    justify-content: center;
    align-items: center;
    z-index: 2000;
}

.modal img {
    max-width: 80%;
    max-height: 80%;
}

/* CARD */
.card {
    background: #141414;
    padding: 20px;
    border-radius: 10px;
    max-width: 400px;
}

/* FORM */
form input, form textarea {
    width: 100%;
    margin: 10px 0;
    padding: 10px;
    background: #111;
    border: 1px solid #333;
    color: white;
}

form button {
    background: crimson;
    padding: 10px 15px;
    border: none;
    color: white;
    cursor: pointer;
}

/* FOOTER */
footer {
    text-align: center;
    padding: 20px;
    background: #111;
}
</style>
</head>

<body>

<!-- NAV -->
<nav>
    <a href="#about">About</a>
    <a href="#works">Works</a>
    <a href="#booking">Booking</a>
    <a href="#contact">Contact</a>
</nav>

<!-- HERO -->
<div class="hero">
    <h1>BLACK INK</h1>
    <p>Elite Tattoo Studio • Custom Ink • Realism • Japanese • Minimal</p>
</div>

<!-- ABOUT -->
<section id="about">
    <h2>About the Artist</h2>
    <p>
        Black Ink Studio specializes in high-end tattoo artistry. Every design is custom-crafted to tell a story,
        blending precision, creativity, and deep artistic expression.
    </p>
</section>

<!-- WORKS -->
<section id="works">
    <h2>Portfolio</h2>

    <div class="filters">
        <button onclick="filter('all')">All</button>
        <button onclick="filter('realism')">Realism</button>
        <button onclick="filter('japanese')">Japanese</button>
        <button onclick="filter('minimal')">Minimal</button>
    </div>

    <div class="gallery">
        <img src="https://images.unsplash.com/photo-1542728928-1413d1894ed1" class="realism" onclick="openModal(this)">
        <img src="https://images.unsplash.com/photo-1604881991720-f91add269bed" class="japanese" onclick="openModal(this)">
        <img src="https://images.unsplash.com/photo-1617050318658-7f1c1a6f0f34" class="minimal" onclick="openModal(this)">
        <img src="https://images.unsplash.com/photo-1590246814883-57c5f7b3c6a7" class="realism" onclick="openModal(this)">
    </div>
</section>

<!-- BOOKING -->
<section id="booking">
    <h2>Book a Session</h2>

    <form action="https://formspree.io/f/mnjldyqb" method="POST">
  <input type="text" name="name" placeholder="Full Name" required>
  <input type="email" name="email" placeholder="Email" required>
  <input type="text" name="idea" placeholder="Tattoo Idea">
  <textarea name="message" placeholder="Describe your tattoo..." rows="5"></textarea>

  <button type="submit">Send Request</button>
</form>
</section>

<!-- CONTACT -->
<section id="contact">
    <h2>Calling Card</h2>

    <div class="card">
        <h3>Artist: Juan Dela Cruz</h3>
        <p>📍 Manila, Philippines</p>
        <p>📞 +63 900 000 0000</p>
        <p>✉️ inkstudio@email.com</p>

        <h4>Socials</h4>
        <p>Instagram | Facebook | TikTok</p>

        <h4>QR Code</h4>
        <div id="qrcode"></div>
    </div>
</section>

<footer>
    © 2026 Black Ink Studio
</footer>

<!-- MODAL -->
<div class="modal" id="modal" onclick="closeModal()">
    <img id="modalImg">
</div>

<script>
// QR CODE
new QRCode(document.getElementById("qrcode"), {
    text: window.location.href,
    width: 150,
    height: 150
});

// MODAL
function openModal(img){
    document.getElementById("modal").style.display = "flex";
    document.getElementById("modalImg").src = img.src;
}

function closeModal(){
    document.getElementById("modal").style.display = "none";
}

// FILTER
function filter(category){
    let images = document.querySelectorAll(".gallery img");

    images.forEach(img => {
        if(category === "all"){
            img.style.display = "block";
        } else {
            img.style.display = img.classList.contains(category) ? "block" : "none";
        }
    });
}

// FORM
function submitForm(e){
    e.preventDefault();
    alert("Your tattoo request has been sent!");
}
</script>

</body>
</html>
