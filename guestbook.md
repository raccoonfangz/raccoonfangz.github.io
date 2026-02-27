---
layout: default
title: "Guestbook"
permalink: /guestbook/
---

<hr>

<p id="sayhi-text">
  Say hi, share a quote or your critique, I love both!
</p>

<style>
html:not([data-theme="dark"]) #sayhi-text {
  color: #222 !important;
  text-align: center;
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, system-ui, Arial;
  margin-top: 1rem;
  font-size: 1.1rem;
}

#guestbook-embed {
  max-width: 650px;
  margin: 0.8rem auto;
  border-radius: 8px;
  display: block;
  box-shadow: 0 6px 20px rgba(0,0,0,0.04);
}
</style>

<iframe class="guestbook-frame" 
  title="Guestbook" 
  loading="lazy"
  style="width:100%;height:760px;border:0;border-radius:8px;display:block;margin:0.8rem auto;box-shadow:0 6px 20px rgba(0,0,0,0.04);"
  srcdoc='<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<title>Guestbook</title>
<style>
:root{
  --font-main: system-ui,-apple-system,BlinkMacSystemFont,"Segoe UI",sans-serif;
  --font-secondary: var(--font-main);
  --bg-light:#ffffff;
  --text-light:#111111;
  --border-light:#e6e6e6;
  --meta-light:#6f6f6f;
}
html,body{height:100%;margin:0;background:var(--bg-light);color:var(--text-light);font-family:var(--font-main);}
.wrap{max-width:650px;margin:12px auto;padding:16px;box-sizing:border-box;font-family:var(--font-main);}
form{display:flex;flex-direction:column;gap:0.9rem;font-family:var(--font-secondary);}
input,textarea{padding:.7rem .9rem;border-radius:8px;border:1px solid var(--border-light);background:var(--bg-light);color:var(--text-light);font-size:1rem;width:100%;box-sizing:border-box;}
textarea{min-height:108px;resize:vertical;}
button{padding:.55rem 1rem;border-radius:8px;border:0;background:#111;color:#fff;cursor:pointer;font-family:var(--font-secondary);}
.meta{font-size:.85rem;color:var(--meta-light);text-align:right;margin-top:8px;}
hr{border:0;border-top:1px solid var(--border-light);margin:14px 0;}
h3{font-size:1.02rem;margin:8px 0 12px;color:var(--text-light); font-family: var(--font-secondary);}
#guestbooks___guestbook-messages-container{display:flex;flex-direction:column;gap:1rem;color:var(--text-light);font-family:var(--font-secondary);}
::placeholder{color:#9a9a9a;opacity:1;}
body, body * { background-repeat: no-repeat !important; }
</style>
</head>
<body>
<div class="wrap">
<script async src="https://guestbooks.meadow.cafe/resources/js/embed_script/1001/script.js"></script>

<div id="guestbooks___guestbook-form-container">
  <form id="guestbooks___guestbook-form" action="https://guestbooks.meadow.cafe/guestbook/1001/submit" method="post" autocomplete="on">
    <input type="text" id="name" name="name" placeholder="Your name" required>
    <input type="url" id="website" name="website" placeholder="Website (optional)">
    <div id="guestbooks___challenge-answer-container"></div>
    <textarea id="text" name="text" placeholder="Leave your message..." required></textarea>
    <button type="submit">Sign Guestbook</button>
    <div id="guestbooks___error-message" style="color:#b00;font-size:.9rem"></div>
  </form>
</div>

<div id="guestbooks___guestbook-made-with" class="meta">Powered by <a href="https://guestbooks.meadow.cafe" target="_blank" rel="noopener noreferrer">Guestbooks</a></div>
<hr>
<h3>Messages</h3>
<div id="guestbooks___guestbook-messages-container"></div>
</div>

<script>
setTimeout(function(){
  var c=document.getElementById("guestbooks___guestbook-messages-container");
  if(c && !c.children.length){
    c.innerHTML = "<p style=\"color:var(--meta-light);font-size:.95rem;font-family:var(--font-secondary);\">Guestbook failed to load. Try refreshing the page.</p>";
  }
},2200);
</script>
</body>
</html>'
></iframe>
