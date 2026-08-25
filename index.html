<?php
// Organizador visual de mesas e invitados.
// Guarda los datos en el navegador mediante localStorage.
// Si luego quieres conectarlo a MariaDB/MySQL, podemos sustituir esta capa por PHP + BD.
?>
<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Organizador de Mesas</title>
<style>
*{box-sizing:border-box}
body{margin:0;font-family:Arial,sans-serif;background:#f4f5f7;color:#222}
header{background:#fff;padding:18px 24px;border-bottom:1px solid #ddd;display:flex;justify-content:space-between;align-items:center;gap:15px;position:sticky;top:0;z-index:20}
h1{margin:0;font-size:24px}
button{border:0;border-radius:8px;padding:10px 14px;cursor:pointer;font-weight:700}
.primary{background:#222;color:#fff}.secondary{background:#e9eaed;color:#222}
.layout{display:grid;grid-template-columns:1fr 330px;gap:18px;padding:18px;min-height:calc(100vh - 75px)}
.panel,.stage{background:#fff;border:1px solid #ddd;border-radius:14px}
.stage{position:relative;overflow:auto;min-height:650px;padding:20px}
.toolbar{display:flex;gap:8px;flex-wrap:wrap;margin-bottom:15px}
#canvas{position:relative;min-width:900px;min-height:590px}

.seat{
 position:absolute;z-index:5;min-width:34px;height:34px;border-radius:50%;
 border:2px solid #777;background:#fff;color:#222;font-weight:700;
 padding:3px 7px;cursor:pointer;box-shadow:0 3px 8px #0002;
 white-space:nowrap;font-size:11px;
}
.empty-seat{font-size:24px;line-height:25px;padding:0}
.seat:hover{transform:translate(-50%,-50%) scale(1.08)!important}
.special-seat{background:#d6ad42;border-color:#b48b21;color:#fff}
.table{overflow:visible}

.table{
 position:absolute;width:180px;min-height:180px;border-radius:50%;
 background:#dce1e7;border:4px solid #777;
 display:flex;flex-direction:column;align-items:center;justify-content:center;
 padding:24px 12px 12px;box-shadow:0 5px 14px #0001;user-select:none;
}
.table.special{background:#dff3df;border-color:#269447}
.table h3{margin:0 0 5px;font-size:18px}
.table .capacity{font-size:12px;color:#555;margin-bottom:7px}
.add{width:38px;height:38px;border-radius:50%;background:#222;color:#fff;font-size:25px;line-height:25px;padding:0}
.guest-list{display:flex;flex-wrap:wrap;gap:5px;justify-content:center;max-width:160px}
.guest-chip{background:#fff;border:1px solid #ccc;border-radius:12px;padding:4px 7px;font-size:11px}
.guest-chip.special{background:#d6ad42;color:#fff;border-color:#b48b21}
.side{padding:16px}
.section{padding-bottom:18px;margin-bottom:18px;border-bottom:1px solid #ddd}
.section h2{font-size:17px;margin:0 0 12px}
input,select{width:100%;padding:10px;border:1px solid #ccc;border-radius:8px;margin:5px 0 8px}
.row{display:flex;gap:7px}.row>*{flex:1}
.guest{display:flex;align-items:center;justify-content:space-between;gap:8px;padding:9px;border:1px solid #ddd;border-radius:9px;margin:6px 0;background:#fafafa}
.guest.special{border-left:5px solid #c49a2e;background:#fffaf0}
.guest small{display:block;color:#777}
.guest-actions button{padding:5px 8px;font-size:11px}
.empty{color:#777;text-align:center;padding:20px}
.legend span{display:inline-block;padding:6px 9px;border-radius:7px;margin:3px;font-size:12px}
.legend .green{background:#dff3df;border:1px solid #269447}
.legend .gold{background:#d6ad42;color:white}
.table-controls{position:absolute;top:8px;right:8px;display:flex;gap:4px}
.table-controls button{padding:3px 7px;background:#fff;border:1px solid #bbb;font-size:11px}
.resize{position:absolute;right:8px;bottom:8px;width:15px;height:15px;border-right:3px solid #777;border-bottom:3px solid #777;cursor:nwse-resize}
.drag-hint{font-size:12px;color:#777;margin:0 0 10px}
</style>
</head>
<body>
<header>
  <h1>Organizador de Mesas</h1>
  <div>
    <button class="primary" onclick="addTable()">＋ Añadir mesa</button>
    <button class="secondary" onclick="addGuest()">＋ Añadir invitado</button>
  </div>
</header>

<div class="layout">
  <main class="stage">
    <div class="toolbar">
      <button class="secondary" onclick="addTable(true)">＋ Mesa especial</button>
      <button class="secondary" onclick="clearAll()">Limpiar todo</button>
    </div>
    <p class="drag-hint">Arrastra las mesas para acomodarlas. Cada + del borde representa un asiento. Haz clic en + para elegir un invitado. Usa la esquina inferior derecha para cambiar el tamaño.</p>
    <div id="canvas"></div>
  </main>

  <aside class="panel side">
    <div class="section">
      <h2>Crear / editar invitado</h2>
      <input id="guestName" placeholder="Nombre del invitado">
      <label><input id="guestSpecial" type="checkbox" style="width:auto"> Invitado especial</label>
      <button class="primary" style="width:100%" onclick="addGuest()">Guardar invitado</button>
    </div>

    <div class="section">
      <h2>Invitados</h2>
      <div id="guests"></div>
    </div>

    <div class="section legend">
      <h2>Referencia</h2>
      <span class="green">Mesa especial</span>
      <span class="gold">Invitado especial</span>
    </div>
  </aside>
</div>

<script>
const KEY='organizador_mesas_v1';
let state=JSON.parse(localStorage.getItem(KEY)||'null') || {
  nextTable:1,nextGuest:1,
  tables:[],guests:[]
};

function save(){localStorage.setItem(KEY,JSON.stringify(state));render()}
function addTable(special=false){
  const n=state.nextTable++;
  state.tables.push({id:'t'+n,name:'Mesa '+n,capacity:8,special,x:40+(n%4)*210,y:40+Math.floor((n-1)/4)*220,size:180});
  save();
}
function addGuest(){
  const input=document.getElementById('guestName');
  const name=input.value.trim();
  if(!name){alert('Escribe el nombre del invitado.');input.focus();return}
  const special=document.getElementById('guestSpecial').checked;
  state.guests.push({id:'g'+state.nextGuest++,name,special,tableId:null});
  input.value='';document.getElementById('guestSpecial').checked=false;save();
}
function removeGuest(id){state.guests=state.guests.filter(g=>g.id!==id);save()}
function removeTable(id){
  const t=state.tables.find(t=>t.id===id);
  if(t && state.guests.some(g=>g.tableId===id)){
    if(!confirm('Esta mesa tiene invitados. ¿Quieres eliminarla? Los invitados quedarán sin mesa.')) return;
  }
  state.guests.forEach(g=>{if(g.tableId===id){g.tableId=null;g.seatIndex=null}});
  state.tables=state.tables.filter(t=>t.id!==id);save();
}
function assignGuest(id,tableId,seatIndex=null){
  const table=state.tables.find(t=>t.id===tableId);
  const guest=state.guests.find(g=>g.id===id);
  if(!guest||!table)return;

  if(guest.tableId===tableId){
    guest.tableId=null;
    guest.seatIndex=null;
  }else{
    const occupied=state.guests.some(g=>g.tableId===tableId && g.seatIndex===seatIndex);
    if(seatIndex!==null && occupied){alert('Ese asiento ya está ocupado.');return}
    if(state.guests.filter(g=>g.tableId===tableId).length>=table.capacity){
      alert('Esta mesa ya alcanzó su capacidad.');
      return;
    }
    guest.tableId=tableId;
    guest.seatIndex=seatIndex;
  }
  save();
}
function changeCapacity(id,delta){
  const t=state.tables.find(t=>t.id===id);
  if(!t)return;
  const occupied=state.guests.filter(g=>g.tableId===id).length;
  if(delta<0 && t.capacity<=occupied){
    alert('No puedes reducir la capacidad por debajo de los invitados sentados.');
    return;
  }
  t.capacity=Math.max(occupied,Math.min(60,t.capacity+delta));
  save();
}
function toggleSpecial(id){
  const t=state.tables.find(t=>t.id===id); if(t){t.special=!t.special;save()}
}
function updateTableName(id,name){
  const t=state.tables.find(t=>t.id===id);if(t){t.name=name.trim()||t.name;save()}
}
function updateSize(id,delta){
  const t=state.tables.find(t=>t.id===id);if(!t)return;
  t.size=Math.max(140,Math.min(420,t.size+delta));
  save();
}
function clearAll(){
  if(confirm('¿Eliminar todas las mesas e invitados?')){state={nextTable:1,nextGuest:1,tables:[],guests:[]};save()}
}

function render(){
  const canvas=document.getElementById('canvas');
  canvas.innerHTML='';
  state.tables.forEach(t=>{
    const el=document.createElement('div');
    el.className='table '+(t.special?'special':'');
    el.style.left=t.x+'px';el.style.top=t.y+'px';
    el.style.width=t.size+'px';el.style.height=t.size+'px';

    const assigned=state.guests.filter(g=>g.tableId===t.id);
    const seats=[];
    for(let i=0;i<t.capacity;i++){
      const guest=assigned[i];
      const angle=(i/t.capacity)*Math.PI*2-Math.PI/2;
      const radius=t.size/2+28;
      const x=Math.cos(angle)*radius;
      const y=Math.sin(angle)*radius;
      seats.push({guest,angle,x,y,index:i});
    }

    el.innerHTML=`
      <div class="table-controls">
        <button onclick="toggleSpecial('${t.id}')">${t.special?'Normal':'Especial'}</button>
        <button onclick="removeTable('${t.id}')">×</button>
      </div>
      <input value="${escapeHtml(t.name)}" onchange="updateTableName('${t.id}',this.value)"
        style="width:110px;text-align:center;border:0;background:transparent;font-weight:700;font-size:18px">
      <div class="capacity">${assigned.length}/${t.capacity} invitados</div>
      <div style="margin-top:8px">
        <button style="padding:3px 8px;font-size:11px" onclick="changeCapacity('${t.id}',-1)">− asiento</button>
        <button style="padding:3px 8px;font-size:11px" onclick="changeCapacity('${t.id}',1)">+ asiento</button>
      </div>
      <div class="resize" title="Agrandar mesa" onmousedown="startResize(event,'${t.id}')"></div>
    `;

    // Seats are outside the table but positioned relative to it.
    seats.forEach(s=>{
      const seat=document.createElement('button');
      seat.className='seat '+(s.guest?(s.guest.special?'occupied special-seat':'occupied'):'empty-seat');
      seat.title=s.guest ? `Asiento ${s.index+1}: ${s.guest.name}` : `Asiento ${s.index+1}: asignar invitado`;
      seat.style.left=`calc(50% + ${s.x}px)`;
      seat.style.top=`calc(50% + ${s.y}px)`;
      seat.style.transform='translate(-50%,-50%)';
      seat.innerHTML=s.guest ? escapeHtml(s.guest.name) : '+';
      seat.onclick=(e)=>{
        e.stopPropagation();
        if(s.guest) openSeatMenu(s.guest.id,t.id);
        else openAssignSeat(t.id,s.index);
      };
      el.appendChild(seat);
    });

    makeDraggable(el,t);
    canvas.appendChild(el);
  });
  renderGuests();
}

function openAssignSeat(tableId,seatIndex){
  const table=state.tables.find(t=>t.id===tableId);
  if(!table)return;

  const available=state.guests.filter(g=>g.tableId===null);
  if(!available.length){
    alert('No hay invitados disponibles. Primero añade invitados o libera un asiento.');
    return;
  }

  const list=available.map((g,i)=>`${i+1}. ${g.name}${g.special?' ★':''}`).join('\n');
  const answer=prompt(
    `Selecciona el invitado para el asiento ${seatIndex+1} de ${table.name}.\n\n${list}\n\nEscribe el número:`
  );

  if(answer===null)return;
  const index=parseInt(answer,10)-1;
  if(index<0 || index>=available.length){
    alert('Selección inválida.');
    return;
  }

  const guest=available[index];
  guest.tableId=tableId;
  guest.seatIndex=seatIndex;
  save();
}

function openSeatMenu(guestId,tableId){
  const guest=state.guests.find(g=>g.id===guestId);
  if(!guest)return;

  const action=confirm(
    `${guest.name} está sentado en ${state.tables.find(t=>t.id===tableId)?.name || 'esta mesa'}.\n\n` +
    `Aceptar = quitarlo de la mesa\nCancelar = mantenerlo`
  );

  if(action){
    guest.tableId=null;
    guest.seatIndex=null;
    save();
  }
}

function renderGuests(){
  const box=document.getElementById('guests');
  if(!state.guests.length){box.innerHTML='<div class="empty">No hay invitados.</div>';return}
  box.innerHTML=state.guests.map(g=>{
    const table=state.tables.find(t=>t.id===g.tableId);
    return `<div class="guest ${g.special?'special':''}">
      <div><b>${escapeHtml(g.name)}</b><small>${table?escapeHtml(table.name):'Sin mesa'}</small></div>
      <div class="guest-actions">
        <button onclick="openAssignForGuest('${g.id}')">Mesa</button>
        <button onclick="removeGuest('${g.id}')">×</button>
      </div>
    </div>`
  }).join('');
}
function openAssign(tableId){
  // Compatibilidad con la versión anterior: busca el primer asiento libre.
  const table=state.tables.find(t=>t.id===tableId);
  if(!table)return;
  const used=state.guests.filter(g=>g.tableId===tableId).map(g=>g.seatIndex);
  const seat=[...Array(table.capacity).keys()].find(i=>!used.includes(i));
  if(seat===undefined){alert('No hay asientos libres en esta mesa.');return}
  openAssignSeat(tableId,seat);
}

function openAssignForGuest(guestId){
  if(!state.tables.length){alert('Primero añade una mesa.');return}
  const guest=state.guests.find(g=>g.id===guestId);
  if(!guest)return;

  const options=state.tables.map((t,i)=>{
    const occupied=state.guests.filter(g=>g.tableId===t.id).length;
    return `${i+1}. ${t.name} (${occupied}/${t.capacity})`;
  }).join('\n');

  const answer=prompt('Selecciona la mesa:\n\n'+options+'\n\nEscribe el número:');
  if(answer===null)return;
  const ti=parseInt(answer,10)-1;
  if(ti<0||ti>=state.tables.length){alert('Selección inválida.');return}

  const table=state.tables[ti];
  const used=state.guests.filter(g=>g.tableId===table.id).map(g=>g.seatIndex);
  const seat=[...Array(table.capacity).keys()].find(i=>!used.includes(i));
  if(seat===undefined){alert('Esta mesa no tiene asientos libres.');return}

  // Un invitado solo puede estar en una mesa.
  guest.tableId=table.id;
  guest.seatIndex=seat;
  save();
}

function makeDraggable(el,t){
  let sx,sy,ox,oy,drag=false;
  el.addEventListener('mousedown',e=>{
    if(e.target.tagName==='BUTTON'||e.target.tagName==='INPUT'||e.target.classList.contains('resize'))return;
    drag=true;sx=e.clientX;sy=e.clientY;ox=t.x;oy=t.y;e.preventDefault();
  });
  window.addEventListener('mousemove',e=>{
    if(!drag)return;
    t.x=Math.max(0,ox+e.clientX-sx);t.y=Math.max(0,oy+e.clientY-sy);
    el.style.left=t.x+'px';el.style.top=t.y+'px';
  });
  window.addEventListener('mouseup',()=>{if(drag){drag=false;save()}});
}
function startResize(e,id){
  e.stopPropagation();e.preventDefault();
  const t=state.tables.find(t=>t.id===id);if(!t)return;
  const startX=e.clientX,startSize=t.size;
  function move(ev){t.size=Math.max(140,Math.min(420,startSize+(ev.clientX-startX)));render()}
  function up(){window.removeEventListener('mousemove',move);window.removeEventListener('mouseup',up);save()}
  window.addEventListener('mousemove',move);window.addEventListener('mouseup',up);
}
function escapeHtml(s){return String(s).replace(/[&<>"']/g,m=>({'&':'&amp;','<':'&lt;','>':'&gt;','"':'&quot;',"'":'&#039;'}[m]))}
render();
</script>
</body>
</html>
