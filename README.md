<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>جمعية النور أولاد بن علال - نظام فواتير الماء</title>
<style>
:root {
  --gold: #ffd700;
  --dark-bg: rgba(0, 0, 0, 0.7);
  --card-bg: rgba(30, 30, 30, 0.9);
}
body {
  margin: 0;
  font-family: 'Segoe UI', sans-serif;
  background: url('WhatsApp Image 2025-10-11 at 17.54.02.jpeg') no-repeat center center fixed;
  background-size: cover;
  color: white;
  overflow-x: hidden;
  position: relative;
}

/* إضاءة ذهبية متحركة مثل موجة ماء */
body::before, body::after {
  content: "";
  position: fixed;
  top: 0; left: 0;
  width: 100%; height: 100%;
  z-index: -1;
  opacity: 0.2;
  pointer-events: none;
}
body::before {
  background: radial-gradient(circle at 20% 30%, rgba(255,215,0,0.25), transparent 70%),
              radial-gradient(circle at 80% 70%, rgba(0,191,255,0.15), transparent 70%);
  animation: waterLights 60s linear infinite;
}
body::after {
  background: radial-gradient(circle at 50% 50%, rgba(255,255,255,0.1), transparent 70%);
  animation: waterGlow 50s linear infinite;
}
@keyframes waterLights {
  0%   { background-position: 10% 20%, 70% 80%; }
  50%  { background-position: 80% 40%, 30% 90%; }
  100% { background-position: 10% 20%, 70% 80%; }
}
@keyframes waterGlow {
  0%   { opacity: 0.15; transform: scale(1); }
  50%  { opacity: 0.35; transform: scale(1.05); }
  100% { opacity: 0.15; transform: scale(1); }
}

.overlay {
  background-color: var(--dark-bg);
  min-height: 100vh;
  padding: 20px;
  backdrop-filter: blur(3px);
}

.card {
  background-color: var(--card-bg);
  padding: 20px;
  border-radius: 15px;
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.6);
  margin-bottom: 20px;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}
.card:hover {
  transform: translateY(-5px);
  box-shadow: 0 12px 30px rgba(0,0,0,0.8);
}

h1, h2, h3, p {
  transition: transform 0.3s ease, color 0.3s ease;
}
h1:hover, h2:hover, h3:hover, p:hover {
  transform: translateY(-3px) scale(1.02);
  color: #ffd700;
}

button {
  background: linear-gradient(45deg, var(--gold), #e6c200);
  border: none;
  border-radius: 10px;
  padding: 10px 20px;
  margin: 5px;
  font-weight: bold;
  cursor: pointer;
  transition: transform 0.3s, box-shadow 0.3s, background 0.3s;
}
button:hover { 
  transform: scale(1.1) translateY(-2px);
  box-shadow: 0 6px 15px rgba(0,0,0,0.5);
  background: linear-gradient(45deg, #ffe45c, #ffcc00);
}

.page { display: none; }
.page.active { display: block; }

/* الفواتير */
.month-item {
  background: #007bff;
  color: white;
  border-radius: 10px;
  padding: 10px;
  margin: 6px 0;
  display: flex;
  justify-content: space-between;
  align-items: center;
  transition: all 0.4s ease;
  position: relative;
  overflow: hidden;
}
.month-item::before {
  content: '';
  position: absolute;
  top: -50%;
  left: -50%;
  width: 200%;
  height: 200%;
  background: radial-gradient(circle, rgba(255,255,255,0.2) 10%, transparent 70%);
  transform: rotate(45deg) scale(0);
  transition: transform 0.6s ease, opacity 0.6s ease;
  pointer-events: none;
}
.month-item:hover::before {
  transform: rotate(45deg) scale(1);
  opacity: 0.4;
}
.month-item:hover {
  transform: translateX(3px) scale(1.03);
  box-shadow: 0 8px 20px rgba(255, 255, 255, 0.2);
}
.month-item.paid {
  background: linear-gradient(45deg, #28a745, #34d058);
  color: white;
  border: 2px solid #1e7e34;
  animation: pulse 1s ease-in-out infinite alternate;
}
.month-item.paid:hover::before {
  background: radial-gradient(circle, rgba(40,167,69,0.2) 10%, transparent 70%);
}
@keyframes pulse {
  from { transform: scale(1); opacity: 0.95; }
  to { transform: scale(1.03); opacity: 1; }
}

.controls { display: flex; gap: 5px; }
.remove-month, .edit-month, .print-month, .toggle-paid {
  border: none;
  border-radius: 6px;
  padding: 5px 8px;
  cursor: pointer;
}
.remove-month { background: red; color: white; }
.edit-month { background: orange; color: white; }
.print-month { background: green; color: white; }
.toggle-paid { background: #444; color: #fff; transition: all 0.3s ease; }
.toggle-paid.paid-toggle { animation: glow 1s ease-in-out infinite alternate; }
@keyframes glow {
  from { box-shadow: 0 0 5px #28a745; }
  to { box-shadow: 0 0 15px #28a745; }
}

.welcome-text {
  font-size: 1.2rem;
  color: var(--gold);
  text-shadow: 1px 1px 3px black;
  animation: fadeIn 2s ease;
}
@keyframes fadeIn {
  from { opacity: 0; transform: translateY(10px); }
  to { opacity: 1; transform: translateY(0); }
}
</style>
</head>
<body onload="playWelcomeSound()">

<!-- الأصوات -->
<audio id="welcomeSound" src="https://cdn.pixabay.com/download/audio/2022/03/15/audio_50ed5a00e3.mp3?filename=water-drop-1-189787.mp3"></audio>
<audio id="soundAdd" src="https://cdn.pixabay.com/download/audio/2022/03/15/audio_50ed5a00e3.mp3?filename=water-drop-1-189787.mp3"></audio>
<audio id="soundPaid" src="https://cdn.pixabay.com/download/audio/2021/09/23/audio_5b5c9b0f3a.mp3?filename=success-1-6297.mp3"></audio>
<audio id="soundRemove" src="https://cdn.pixabay.com/download/audio/2022/03/15/audio_6a7c2f1bb6.mp3?filename=water-drip-20776.mp3"></audio>

<div class="overlay">
  <div class="card" style="text-align:center;">
    <img src="logo.jpg" alt="شعار الجمعية" style="width:120px;border-radius:15px;">
    <h1>💧 جمعية النور أولاد بن علال للتنمية و التعاون مرس الحجر</h1>
    <p class="welcome-text">مرحبًا بكم في نظام إدارة فواتير جمعية النور أولاد بن علال للتنمية والتعاون مرس الحجر</p>
    <button onclick="showPage('login')">تسجيل الدخول</button>
    <button onclick="showPage('home')">الرئيسية</button>
  </div>

  <div id="home" class="page active card" style="text-align:center;">
    <h2>🌿 نظام فواتير المياه العصري</h2>
    <p class="welcome-text">مرحبًا بكم في منصة جمعية النور لإدارة فواتير الماء بطريقة حديثة وسهلة</p>
  </div>

  <div id="login" class="page card">
    <h2>تسجيل الدخول</h2>
    <select id="userType">
      <option value="customer">مشترك</option>
      <option value="admin">مدير</option>
    </select>
    <input type="password" id="password" placeholder="كلمة المرور أو كود المشترك">
    <button onclick="login()">دخول</button>
  </div>

  <div id="admin-dashboard" class="page">
    <div class="card">
      <h2>لوحة تحكم المدير</h2>
      <button onclick="logout()">🚪 خروج</button>
      <button onclick="exportToExcel()">💾 تصدير Excel</button>
    </div>
    <div class="card">
      <h3>➕ إضافة مشترك جديد</h3>
      <input type="text" id="newCustomerName" placeholder="اسم المشترك">
      <input type="text" id="newCustomerCode" placeholder="كود المشترك">
      <button onclick="addCustomer()">إضافة</button>
    </div>
    <div class="card">
      <h3>📋 قائمة المشتركين</h3>
      <div id="customerList"></div>
    </div>
    <div class="card">
      <h3>📊 إدارة فواتير المشترك</h3>
      <select id="selectedCustomer" onchange="renderMonths()">
        <option value="">اختر مشترك</option>
      </select>
      <input type="number" id="monthConsumption" placeholder="الاستهلاك بالمتر³">
      <button onclick="addMonth()">إضافة فاتورة</button>
      <div id="monthList"></div>
    </div>
  </div>

  <div id="customer-dashboard" class="page card">
    <h2>مرحبًا <span id="customerNameDisplay"></span></h2>
    <button onclick="logout()">🚪 خروج</button>
    <h3>💵 فواتيرك</h3>
    <div id="customerMonths"></div>
  </div>
</div>

<script src="https://cdn.jsdelivr.net/npm/xlsx/dist/xlsx.full.min.js"></script>
<script>
let adminPassword = "236263";
let customers = JSON.parse(localStorage.getItem("customersData") || "[]");

function playSound(id){
  const s = document.getElementById(id);
  s.currentTime = 0;
  s.volume = 0.4;
  s.play().catch(()=>{});
}
function playWelcomeSound(){ playSound('welcomeSound'); }

function showPage(id){ document.querySelectorAll('.page').forEach(p=>p.classList.remove('active')); document.getElementById(id).classList.add('active'); }
function login(){
  let type = userType.value, pass = password.value.trim();
  if(type==="admin"){
    if(pass===adminPassword){ showPage('admin-dashboard'); renderCustomers(); }
    else alert("كلمة مرور المدير غير صحيحة");
  } else {
    let user = customers.find(c=>c.code===pass);
    if(user){ showPage('customer-dashboard'); customerNameDisplay.innerText=user.name; renderCustomerMonths(user); }
    else alert("كود المشترك غير صحيح");
  }
}
function logout(){ showPage('login'); }

function addCustomer(){
  let name=newCustomerName.value.trim(), code=newCustomerCode.value.trim();
  if(!name||!code) return alert("أدخل الاسم والكود");
  customers.push({name,code,months:[]});
  saveData(); newCustomerName.value=''; newCustomerCode.value='';
  renderCustomers(); alert("✅ تمت إضافة المشترك بنجاح");
}
function renderCustomers(){
  customerList.innerHTML=''; selectedCustomer.innerHTML='<option value="">اختر مشترك</option>';
  customers.forEach((c,i)=>{
    customerList.innerHTML+=`<p>${i+1}. ${c.name} <button onclick="removeCustomer(${i})" style="background:red;color:#fff">حذف</button></p>`;
    selectedCustomer.innerHTML+=`<option value="${i}">${c.name}</option>`;
  });
}
function removeCustomer(i){ if(confirm("هل تريد حذف هذا المشترك؟")){ customers.splice(i,1); saveData(); renderCustomers(); monthList.innerHTML=''; playSound('soundRemove'); } }

function addMonth(){
  let idx=selectedCustomer.value, cons=parseFloat(monthConsumption.value);
  if(idx===""||!cons) return alert("اختر مشترك وأدخل استهلاك صالح");
  customers[idx].months.push({consumption:cons, paid:false}); 
  saveData(); monthConsumption.value=''; renderMonths();
  playSound('soundAdd');
}
function renderMonths(){
  let idx=selectedCustomer.value; monthList.innerHTML='';
  if(idx==="") return;
  customers[idx].months.forEach((m,i)=>{
    let amount=m.consumption*3;
    let paidClass=m.paid?"paid":"";
    let paidText=m.paid?"✅ مدفوعة":"❌ غير مدفوعة";
    monthList.innerHTML+=`<div class="month-item ${paidClass}"><span>شهر ${i+1}: ${m.consumption} م³ = ${amount} درهم (${paidText})</span>
      <div class="controls">
        <button class="edit-month" onclick="editMonth(${idx},${i})">✏️</button>
        <button class="print-month" onclick="printInvoice(${idx},${i})">🖨️</button>
        <button class="remove-month" onclick="removeMonth(${idx},${i})">×</button>
        <button class="toggle-paid ${m.paid?'paid-toggle':''}" onclick="togglePaid(${idx},${i})">💰</button>
      </div></div>`;
  });
}
function togglePaid(c,m){ customers[c].months[m].paid=!customers[c].months[m].paid; saveData(); renderMonths(); playSound('soundPaid'); }
function removeMonth(c,m){ if(confirm("هل تريد حذف هذه الفاتورة؟")){ customers[c].months.splice(m,1); saveData(); renderMonths(); playSound('soundRemove'); } }
function editMonth(c,m){
  let newCons=prompt("أدخل القيمة الجديدة:", customers[c].months[m].consumption);
  if(newCons && !isNaN(newCons)){ customers[c].months[m].consumption=parseFloat(newCons); saveData(); renderMonths(); alert("تم التعديل بنجاح"); }
}
function renderCustomerMonths(user){
  customerMonths.innerHTML='';
  if(user.months.length===0){ customerMonths.innerHTML='<p>لا توجد فواتير بعد.</p>'; return; }
  user.months.forEach((m,i)=>{ 
    let cls=m.paid?"paid":""; 
    customerMonths.innerHTML+=`<div class="month-item ${cls}">شهر ${i+1}: ${m.consumption} م³ = ${m.consumption*3} درهم ${m.paid?"(مدفوعة)":"(غير مدفوعة)"}</div>`; 
  });
}
function printInvoice(c,m){
  let cust=customers[c], inv=cust.months[m], amt=inv.consumption*3;
  let w=window.open('', '', 'width=600,height=700');
  w.document.write(`<html dir="rtl"><body style="text-align:center;font-family:Tahoma;">
  <img src="logo.jpg" style="width:100px"><h2>جمعية النور أولاد بن علال للتنمية و التعاون مرس الحجر</h2>
  <h3>فاتورة الماء الشهرية</h3><hr>
  <p><b>الاسم:</b> ${cust.name}</p><p><b>الكود:</b> ${cust.code}</p>
  <p><b>الشهر:</b> ${m+1}</p><p><b>الاستهلاك:</b> ${inv.consumption} م³</p>
  <p><b>المبلغ:</b> ${amt} درهم</p>
  <p><b>الحالة:</b> ${inv.paid ? "مدفوعة ✅" : "غير مدفوعة ❌"}</p>
  <hr><p>تاريخ الطباعة: ${new Date().toLocaleDateString('ar-MA')}</p></body></html>`);
  w.print();
}
function exportToExcel(){
  if(customers.length===0) return alert("لا توجد بيانات");
  let rows=[["الاسم","الكود","الشهر","الاستهلاك","المبلغ","الحالة"]];
  customers.forEach(c=>{ c.months.length?c.months.forEach((m,i)=>rows.push([c.name,c.code,"شهر "+(i+1),m.consumption,m.consumption*3,m.paid?"مدفوعة":"غير مدفوعة"])):rows.push([c.name,c.code,"-","-","-","-"]); });
  let wb=XLSX.utils.book_new(); let ws=XLSX.utils.aoa_to_sheet(rows); XLSX.utils.book_append_sheet(wb,ws,"فواتير");
  XLSX.writeFile(wb,`فواتير_${new Date().toISOString().slice(0,10)}.xlsx`);
  alert("✅ تم تصدير الملف بنجاح!");
}

function saveData(){ localStorage.setItem("customersData", JSON.stringify(customers)); }
</script>
</body>
</html>
