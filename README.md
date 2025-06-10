ody {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
  font-size: 16px;
  line-height: 1.5;
  color: #1c1c1c;
  background-color: #f3f2ef;
}

h1, h2, h3 {
  font-weight: 600;
}

a {
  color: #0a66c2;
  text-decoration: none;
}

.profile-container {
  max-width: 700px;
  margin: 10px auto;
  background: white;
  border-radius: 10px;
  overflow: hidden;
  box-shadow: 0 0 10px rgba(0,0,0,0.1);
  position: relative;
}

.header-bg {
  height: 200px;
  background-image: url('bg.png');
  background-size: cover;
  background-position: center;
}

.profile-photo-wrapper {
  position: absolute;
  top: 130px;
  left: 30px;
  width: 120px;
  height: 120px;
  border-radius: 50%;
  overflow: hidden;
  border: 4px solid white;
  box-shadow: 0 0 6px rgba(0,0,0,0.2);
}

.profile-photo-wrapper img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.header-text {
  margin-top: 40px;
  padding: 30px 30px 10px 30px;
}

.header-text h1 {
  margin: 0;
  font-size: 24px;
}

.header-text .subtitle {
  color: #666;
  margin: 5px 0;
}

.header-text a {
  color: #0073b1;
  text-decoration: none;
}

.action-buttons {
  padding: 0 30px 20px 30px;
}

.action-buttons button {
  background-color: #0a66c2;
  color: white;
  border: none;
  padding: 8px 12px;
  border-radius: 5px;
  margin-right: 10px;
  cursor: pointer;
}

.content-card {
  margin: 0 30px 20px 30px;
  padding: 20px;
  background: #fafafa;
  border-radius: 10px;
}

.content-card h2, .content-card h3 {
  margin-top: 0;
}

.content-card ul {
  padding-left: 20px;
} 
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>afwanda rizqi</title>
  <link rel="stylesheet" href="style.css" />
</head>
<body>
  <div class="profile-container">
  <div class="header-bg"></div>

  <div class="profile-photo-wrapper">
    <img src="profile.png" alt="profile" class="profile-photo" />
  </div>

  <div class="header-text">
    <h1>afwanda rizqi</h1>
    <p class="subtitle">He/Him • Web Developer</p>
    <p>Jakarta, Indonesia • <a href="https://afwanda.rizqi.com">afwanda rizqi.com</a></p>
    <p><strong>afwanda Langit Solusi</strong> — Universitas ipwija</p>
  </div>

  <div class="action-buttons">
    <button>Open to work</button>
    <button>Add profile section</button>
    <button>Enhance profile</button>
  </div>

  <div id="content"  >


  </div>



  <div class="content-card">
    <h3>Sosial Media <small></small></h3>
    <ul>
      <li><strong>linkedin :</strong> http://linkedin.com/in/sismadi </li>
      <li><strong>credly :</strong> https://www.credly.com/users/wawan-sismadi</li>
    </ul>
  </div>
</div>


<script type="module">
// Import Supabase client dari CDN
import { createClient } from 'https://cdn.jsdelivr.net/npm/@supabase/supabase-js/+esm'


const SUPABASE_URL = 'https://zligkbkrxqqbetnwykrq.supabase.co'
const SUPABASE_ANON_KEY = 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6InpsaWdrYmtyeHFxYmV0bnd5a3JxIiwicm9sZSI6ImFub24iLCJpYXQiOjE3NDkyNjM2ODUsImV4cCI6MjA2NDgzOTY4NX0.kDK8_c6qCKKRax4HbHwEbAMwTavhDRWdgqkDtjWWYD8'
etoibznogpudrbwkuikq

const supabase = createClient(SUPABASE_URL, SUPABASE_ANON_KEY)

// Elemen DOM
// const addBtn = document.getElementById('addBtn')
// const dataBody = document.getElementById('dataBody')
// const crudForm = document.getElementById('crudForm')
// const recordIdInput = document.getElementById('recordId')
// const nameInput = document.getElementById('nameInput')
// const emailInput = document.getElementById('emailInput')
// const deleteBtn = document.getElementById('deleteBtn')
// const cancelBtn = document.getElementById('cancelBtn')

const content = document.getElementById('content')

// Fungsi load data ke tabel
async function loadData() {
  const { data, error } = await supabase.from('web').select('*').order('id')
  if (error) {
    alert('Error loading data: ' + error.message)
    return
  }
  content.innerHTML = ''
  let  out=``;
  data.forEach(row => {

    out+=`

    <div class="content-card">
    <h2>${row.judul}</h2>
    <p>${row.isi}
</p>

  </div>
  `

  })
  content.innerHTML = out


}

 // Load data saat halaman siap
window.addEventListener('DOMContentLoaded', loadData)

</script>



</body>
</html>
