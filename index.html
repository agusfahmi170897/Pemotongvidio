<!doctype html><html lang="id"><head><meta charset="utf-8"><meta name="viewport" content="width=device-width,initial-scale=1,viewport-fit=cover"><title>Pemotong Video Otomatis</title>
<style>
:root{--bg:#fff;--fg:#1a1a1a;--mu:#666;--cd:#f4f4f2;--ac:#c2410c;--bt:#fff;--bd:#ddd;box-sizing:border-box;padding-top:env(safe-area-inset-top,0px);padding-bottom:env(safe-area-inset-bottom,0px)}
@media(prefers-color-scheme:dark){:root:not([data-theme="light"]){--bg:#161616;--fg:#eee;--mu:#999;--cd:#222;--ac:#fb923c;--bt:#111;--bd:#333;color-scheme:dark}}
:root[data-theme="dark"]{--bg:#161616;--fg:#eee;--mu:#999;--cd:#222;--ac:#fb923c;--bt:#111;--bd:#333;color-scheme:dark}
html{scroll-padding-top:env(safe-area-inset-top,0px)}
body{margin:0;background:var(--bg);color:var(--fg);font:16px/1.5 system-ui,sans-serif}
main{max-width:640px;margin:0 auto;padding:20px 16px}
h1{font-size:1.4rem;margin:0 0 8px}
.mu{color:var(--mu);font-size:.9rem}
.drop{display:block;border:2px dashed var(--bd);border-radius:12px;padding:22px 12px;text-align:center;cursor:pointer;margin:16px 0 8px;background:var(--cd)}
.drop input{display:none}
.row{display:flex;gap:8px;margin:16px 0 12px}
select,input[type=number]{font:inherit;padding:10px;border:1px solid var(--bd);border-radius:10px;background:var(--cd);color:var(--fg);min-width:0}
select{flex:1}input[type=number]{width:90px}
button{font:inherit;border:0;border-radius:10px;padding:10px 16px;cursor:pointer}
.b{background:var(--ac);color:var(--bt)}.b:disabled{opacity:.4}
.s{background:var(--cd);color:var(--fg);border:1px solid var(--bd)}
#go,#all{width:100%}
#st{margin:12px 0}
.r{display:flex;gap:8px;align-items:center;background:var(--cd);border-radius:12px;padding:10px 12px;margin-top:8px}
.r div{flex:1;min-width:0}
#all{margin-top:12px}
</style></head><body><main>
<h1>✂️ Pemotong Video Otomatis</h1>
<p class="mu">Potong video panjang atau film jadi beberapa part sekaligus. Diproses langsung di perangkatmu (tanpa upload) dan tanpa konversi ulang, jadi cepat dan kualitas tetap. Format: MP4 / MOV / M4V.</p>
<label class="drop"><input id="f" type="file" accept="video/*"><span id="fn">Pilih video…</span></label>
<div id="info" class="mu"></div>
<div class="row"><select id="m"><option value="d">Durasi per part (menit)</option><option value="n">Jumlah part</option></select><input id="v" type="number" value="10" min="1" step="any"></div>
<button id="go" class="b" disabled>Potong otomatis</button>
<div id="st" class="mu"></div><div id="out"></div>
<button id="all" class="b" hidden>Simpan semua</button>
<p class="mu">Pemotongan dilakukan di titik keyframe, jadi durasi tiap part bisa meleset beberapa detik dari target.</p>
</main>
<script>
const $=i=>document.getElementById(i);
let file,root,d,u,tr,V,mts,tot,BASE,BIG,MD,PSc,parts=[];
const s4=t=>Uint8Array.from(t,c=>c.charCodeAt(0)),ty=o=>String.fromCharCode(...u.subarray(o,o+4)),raw=k=>u.subarray(k.s,k.e);
const w32=a=>{const o=new Uint8Array(a.length*4),v=new DataView(o.buffer);for(let i=0;i<a.length;i++)v.setUint32(i*4,a[i]);return o};
const box=(t,...p)=>{let n=8;for(const x of p)n+=x.length;const o=new Uint8Array(n);new DataView(o.buffer).setUint32(0,n);o.set(s4(t),4);let q=8;for(const x of p){o.set(x,q);q+=x.length}return o};
const fmt=s=>{s=Math.round(s);const h=s/3600|0,m=s%3600/60|0,x=s%60;return(h?h+':'+String(m).padStart(2,'0'):m)+':'+String(x).padStart(2,'0')};
const rle=(a,s,e)=>{const r=[];for(let i=s,j;i<e;i=j){j=i;while(j<e&&a[j]==a[i])j++;r.push(j-i,a[i])}return r};
function kids(s,e){const r=[];while(s+8<=e){let z=d.getUint32(s),h=8;if(z==1){z=d.getUint32(s+8)*4294967296+d.getUint32(s+12);h=16}else if(!z)z=e-s;if(z<h)break;r.push({t:ty(s+4),s,e:s+z,b:s+h});s+=z}return r}
const kid=(p,t)=>kids(p.b,p.e).find(k=>k.t==t);
function ptrak(k){
 const md=kid(k,'mdia'),mh=kid(md,'mdhd'),st=kid(kid(md,'minf'),'stbl');if(!st)return;const g=t=>kid(st,t);
 const T={k,vide:ty(kid(md,'hdlr').b+8)=='vide',ts:d.getUint32(mh.b+(d.getUint8(mh.b)?20:12))};
 let z=g('stsz');const n=d.getUint32(z.b+8),cs=d.getUint32(z.b+4);T.n=n;
 T.size=new Uint32Array(n);for(let i=0;i<n;i++)T.size[i]=cs||d.getUint32(z.b+12+4*i);
 let p=g('stts').b+4,ne=d.getUint32(p),i=0;p+=4;T.dur=new Uint32Array(n);
 for(let e=0;e<ne;e++,p+=8){let c=d.getUint32(p);const v=d.getUint32(p+4);while(c--&&i<n)T.dur[i++]=v}
 T.dts=new Float64Array(n+1);for(let j=0;j<n;j++)T.dts[j+1]=T.dts[j]+T.dur[j];
 if(z=g('ctts')){T.cv=d.getUint8(z.b);T.cts=new Int32Array(n);p=z.b+4;ne=d.getUint32(p);p+=4;i=0;for(let e=0;e<ne;e++,p+=8){let c=d.getUint32(p);const v=d.getInt32(p+4);while(c--&&i<n)T.cts[i++]=v}}
 T.sync=new Uint8Array(n);if(z=g('stss')){T.hs=1;ne=d.getUint32(z.b+4);for(let e=0;e<ne;e++){const x=d.getUint32(z.b+8+4*e)-1;if(x<n)T.sync[x]=1}}else T.sync.fill(1);
 const co=g('stco'),c6=g('co64'),sc=g('stsc'),nc=d.getUint32((co||c6).b+4),cf=c=>co?d.getUint32(co.b+8+4*c):d.getUint32(c6.b+8+8*c)*4294967296+d.getUint32(c6.b+12+8*c);
 T.off=new Float64Array(n);ne=d.getUint32(sc.b+4);let si=0;
 for(let e=0;e<ne;e++){const q=sc.b+8+12*e,f=d.getUint32(q),spc=d.getUint32(q+4),l=e+1<ne?d.getUint32(q+12):nc+1;for(let c=f;c<l;c++){let o=cf(c-1);for(let j=0;j<spc&&si<n;j++){T.off[si]=o;o+=T.size[si++]}}}
 return T}
async function load(f){
 let o=0,mv,hl;const sz=f.size;
 while(o<sz-7){const h=new DataView(await f.slice(o,o+16).arrayBuffer());let z=h.getUint32(0),l=8;const t=String.fromCharCode(h.getUint8(4),h.getUint8(5),h.getUint8(6),h.getUint8(7));
  if(z==1){z=h.getUint32(8)*4294967296+h.getUint32(12);l=16}else if(!z)z=sz-o;if(z<l)break;
  if(t=='moov'){mv=await f.slice(o,o+z).arrayBuffer();hl=l}if(t=='moof')throw 0;o+=z}
 if(!mv)throw 0;
 u=new Uint8Array(mv);d=new DataView(mv);root={t:'moov',s:0,e:mv.byteLength,b:hl};
 const mh=kid(root,'mvhd');mts=d.getUint32(mh.b+(d.getUint8(mh.b)?20:12));
 tr=kids(root.b,root.e).filter(k=>k.t=='trak').map(ptrak).filter(Boolean);
 V=tr.find(t=>t.vide)||tr[0];if(!V||!V.n)throw 0;tot=V.dts[V.n]/V.ts;file=f}
function plan(P){
 const vd=V.dts,vs=V.ts,n=V.n,sy=[];for(let i=0;i<n;i++)if(V.sync[i])sy.push(i);
 const c=[0];
 for(let k=1;;k++){const t=k*P*vs;if(t>=vd[n])break;let l=0,h=sy.length;while(l<h){const m=(l+h)>>1;vd[sy[m]]<t?l=m+1:h=m}if(l>=sy.length)break;if(sy[l]>c[c.length-1])c.push(sy[l])}
 c.push(n);return c}
const lo=(T,t)=>{let l=0,h=T.n;const x=t*T.ts-.5;while(l<h){const m=(l+h)>>1;T.dts[m]<x?l=m+1:h=m}return l};
const slices=(c,j)=>tr.map(T=>T==V?{T,a:c[j],b:c[j+1]}:{T,a:j?lo(T,V.dts[c[j]]/V.ts):0,b:j==c.length-2?T.n:lo(T,V.dts[c[j+1]]/V.ts)}).filter(s=>s.b>s.a);
function hd(k,v){const r=raw(k).slice(),dv=new DataView(r.buffer),ver=r[8],p=k.t=='tkhd'?(ver?36:28):(ver?32:24);v=Math.round(v);if(ver){dv.setUint32(p,Math.floor(v/4294967296));dv.setUint32(p+4,v)}else dv.setUint32(p,v);return r}
function stbl(k,S){
 const T=S.T,{a,b}=S,n=b-a,g=t=>kid(k,t),o=[raw(g('stsd'))];
 let r=rle(T.dur,a,b);o.push(box('stts',w32([0,r.length/2]),w32(r)));
 if(T.cts){r=rle(T.cts,a,b);o.push(box('ctts',w32([T.cv*16777216,r.length/2]),w32(r)))}
 if(T.hs){const s=[];for(let i=a;i<b;i++)if(T.sync[i])s.push(i-a+1);o.push(box('stss',w32([0,s.length]),w32(s)))}
 o.push(box('stsc',w32([0,1,1,1,1])));
 let z=new Uint8Array(12+4*n),v=new DataView(z.buffer);v.setUint32(8,n);for(let i=0;i<n;i++)v.setUint32(12+4*i,T.size[a+i]);o.push(box('stsz',z));
 z=new Uint8Array(8+(BIG?8:4)*n);v=new DataView(z.buffer);v.setUint32(4,n);
 for(let i=0;i<n;i++){const x=BASE+S.no[i];if(BIG){v.setUint32(8+8*i,Math.floor(x/4294967296));v.setUint32(12+8*i,x)}else v.setUint32(8+4*i,x)}
 o.push(box(BIG?'co64':'stco',z));return box('stbl',...o)}
function rb(k,S){const t=k.t;
 if(t=='edts')return null;
 if(t=='mvhd')return hd(k,MD);
 if(t=='tkhd')return hd(k,S.td);
 if(t=='mdhd')return hd(k,S.md);
 if(t=='stbl')return stbl(k,S);
 if(t=='moov')return box(t,...kids(k.b,k.e).map(c=>{if(c.t!='trak')return rb(c);const x=PSc.find(s=>s.T.k.s==c.s);return x&&rb(c,x)}).filter(Boolean));
 if(t=='trak'||t=='mdia'||t=='minf')return box(t,...kids(k.b,k.e).map(c=>rb(c,S)).filter(Boolean));
 return raw(k)}
function layout(PS){const L=[];for(const s of PS){s.no=new Float64Array(s.b-s.a);for(let i=s.a;i<s.b;i++)L.push([s.T.off[i],s.T.size[i],s,i-s.a])}
 L.sort((x,y)=>x[0]-y[0]);const runs=[];let pos=0,c;
 for(const[o,z,s,i]of L){if(c&&c.e==o)c.e+=z;else runs.push(c={s:o,e:o+z});s.no[i]=pos;pos+=z}return{runs,pos}}
function mkPart(PS){
 const{runs,pos}=layout(PS);
 for(const s of PS){s.md=s.T.dts[s.b]-s.T.dts[s.a];s.td=Math.round(s.md/s.T.ts*mts)}
 MD=Math.max(...PS.map(s=>s.td));BIG=pos>4e9;PSc=PS;
 const ft=box('ftyp',s4('isom'),w32([512]),s4('isomiso2mp41')),mh=new Uint8Array(pos+8>4294967295?16:8),dv=new DataView(mh.buffer);
 if(mh.length==16){dv.setUint32(0,1);dv.setUint32(8,Math.floor((pos+16)/4294967296));dv.setUint32(12,pos+16)}else dv.setUint32(0,pos+8);
 mh.set(s4('mdat'),4);
 BASE=0;let mv=rb(root);BASE=ft.length+mv.length+mh.length;mv=rb(root);
 return new Blob([ft,mv,mh,...runs.map(r=>file.slice(r.s,r.e))],{type:'video/mp4'})}
async function save(n,b){
 try{const c=await window.claude?.use?.('downloads');if(c){await c.save({filename:n,data:b});return}}catch(e){if(e&&e.code=='declined')return}
 const a=document.createElement('a');a.href=URL.createObjectURL(b);a.download=n;a.click()}
function add(j,nm,b,t0,t1){
 const r=document.createElement('div');r.className='r';
 r.innerHTML=`<div><b>Part ${j+1}</b><br><span class="mu">${fmt(t0)}–${fmt(t1)} · ${(b.size/1e6).toFixed(1)} MB</span></div>`;
 const p=document.createElement('button');p.textContent='Putar';p.className='s';
 p.onclick=()=>{const vd=document.createElement('video');vd.controls=true;vd.playsInline=true;vd.src=URL.createObjectURL(b);vd.style.cssText='width:100%;margin-top:8px;border-radius:10px';r.after(vd);vd.play().catch(()=>{});p.remove()};
 const s=document.createElement('button');s.textContent='Simpan';s.className='b';s.onclick=()=>save(nm,b);
 r.append(p,s);$('out').append(r)}
$('m').onchange=()=>$('v').value=$('m').value=='d'?10:5;
$('f').onchange=async e=>{
 const f=e.target.files[0];if(!f)return;
 $('go').disabled=true;$('out').innerHTML='';$('all').hidden=true;$('fn').textContent=f.name;$('info').textContent='';$('st').textContent='Membaca video…';
 try{await load(f);$('info').textContent=`Durasi ${fmt(tot)} · ${(f.size/1e6).toFixed(0)} MB`;$('st').textContent='';$('go').disabled=false}
 catch(x){$('st').textContent='Video ini belum bisa dibaca. Pakai MP4/MOV/M4V (bukan MKV/AVI atau MP4 fragmented). Film MKV bisa di-remux dulu ke MP4 tanpa re-encode.'}};
$('go').onclick=async()=>{
 const m=$('m').value,v=+$('v').value;if(!(v>0))return;
 const P=Math.max(1,m=='d'?v*60:tot/Math.min(Math.round(v)||1,500));
 $('go').disabled=true;$('out').innerHTML='';$('all').hidden=true;parts=[];
 try{
  const c=plan(P),N=c.length-1;
  for(let j=0;j<N;j++){
   $('st').textContent=`Membuat part ${j+1}/${N}…`;await new Promise(r=>setTimeout(r));
   const b=mkPart(slices(c,j)),nm=file.name.replace(/\.[^.]+$/,'')+'_part'+String(j+1).padStart(2,'0')+'.mp4';
   parts.push([nm,b]);add(j,nm,b,V.dts[c[j]]/V.ts,V.dts[c[j+1]]/V.ts)}
  $('st').textContent=`Selesai: ${N} part.`;$('all').hidden=false}
 catch(x){$('st').textContent='Gagal memotong video ini: '+(x&&x.message||'struktur file tidak didukung')}
 $('go').disabled=false};
$('all').onclick=async()=>{for(const[n,b]of parts)await save(n,b)};
</script></body></html>
