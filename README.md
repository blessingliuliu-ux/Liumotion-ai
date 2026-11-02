
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>LiuMotion AI</title>
<style>
*{box-sizing:border-box}
body{
 margin:0;
 font-family:Arial,sans-serif;
 background:#10101c;
 color:white;
}
header{
 padding:20px;
 background:#19192a;
 display:flex;
 justify-content:space-between;
 align-items:center;
 border-bottom:1px solid #303047;
}
.logo{font-size:23px;font-weight:bold;color:#bd83ff}
.logo span{color:white}
main{max-width:700px;margin:auto;padding:22px}
h1{font-size:29px;margin-bottom:8px}
.subtitle{color:#aaa;line-height:1.5}
.tabs{display:flex;gap:10px;margin:25px 0}
.tab{
 flex:1;padding:13px 8px;border:1px solid #444;
 border-radius:10px;background:#202033;color:white;
 font-weight:bold;
}
.tab.active{background:#813fe0;border-color:#813fe0}
.panel{
 background:#1b1b2c;padding:18px;
 border:1px solid #35354b;border-radius:15px;
}
label{display:block;margin:17px 0 9px;font-weight:bold}
textarea,input[type=text]{
 width:100%;padding:14px;border-radius:9px;
 border:1px solid #45455b;background:#10101c;
 color:white;font-size:15px;
}
textarea{height:115px;resize:vertical}
.upload{
 border:2px dashed #6e55a0;border-radius:12px;
 padding:25px;text-align:center;margin-top:12px;
 color:#ccc;
}
.upload input{max-width:100%;margin-top:15px}
#preview{display:none;width:100%;margin-top:15px;border-radius:10px}
.generate{
 width:100%;padding:16px;margin-top:22px;
 border:0;border-radius:10px;background:#a45cff;
 color:white;font-size:17px;font-weight:bold;
}
.note{font-size:12px;color:#aaa;line-height:1.6;margin-top:15px}
footer{text-align:center;color:#777;padding:30px}
.hidden{display:none}
</style>
</head>
<body>
<header>
 <div class="logo">LiuMotion <span>AI</span></div>
 <div>✨ AI Studio</div>
</header>

<main>
 <h1>Create amazing videos with AI</h1>
 <p class="subtitle">Turn your imagination and pictures into amazing videos.</p>

 <div class="tabs">
  <button class="tab active" id="textTab" onclick="showMode('text')">Text to Video</button>
  <button class="tab" id="photoTab" onclick="showMode('photo')">Photo to Video</button>
 </div>

 <section class="panel">
  <div id="textMode">
   <label>Describe the video you want</label>
   <textarea id="prompt" placeholder="Example: A beautiful young girl walking through a magical forest, cinematic lighting, realistic 4K..."></textarea>
  </div>

  <div id="photoMode" class="hidden">
   <label>Upload your picture</label>
   <div class="upload">
    Choose a picture from your phone
    <input type="file" id="photo" accept="image/*" onchange="previewPhoto(event)">
    <img id="preview" alt="Your selected picture">
   </div>
   <label>Describe how you want the picture to move</label>
   <textarea id="photoPrompt" placeholder="Example: Make the person smile and slowly turn towards the camera..."></textarea>
  </div>

  <label>Video style</label>
  <select id="style" style="width:100%;padding:13px;border-radius:9px;background:#10101c;color:white">
   <option>Realistic</option>
   <option>Cartoon</option>
   <option>Cinematic</option>
   <option>Anime</option>
  </select>

  <button class="generate" onclick="startCreation()">✨ Create AI Video</button>
  <p class="note" id="message">Your video-generation service will be connected in the next development step. This is currently the website interface.</p>
 </section>
</main>

<footer>© 2026 LiuMotion AI · Create without limits</footer>

<script>
let mode="text";

function showMode(selected){
 mode=selected;
 document.getElementById("textMode").classList.toggle("hidden",mode!=="text");
 document.getElementById("photoMode").classList.toggle("hidden",mode!=="photo");
 document.getElementById("textTab").classList.toggle("active",mode==="text");
 document.getElementById("photoTab").classList.toggle("active",mode==="photo");
}

function previewPhoto(event){
 const file=event.target.files[0];
 if(!file)return;
 const image=document.getElementById("preview");
 image.src=URL.createObjectURL(file);
 image.style.display="block";
}

function startCreation(){
 const prompt=mode==="text"
 ?document.getElementById("prompt").value.trim()
 :document.getElementById("photoPrompt").value.trim();
 const photo=document.getElementById("photo").files[0];

 if(!prompt){
  alert("Please describe the video you want.");
  return;
 }
 if(mode==="photo"&&!photo){
  alert("Please upload a picture first.");
  return;
 }
 alert("Great! Your request is ready. We will connect the AI video-generation engine in the next step.");
}
</script>
</body>
</html>
