import { useState, useEffect, useRef, useCallback } from "react";

// ── BRAND ────────────────────────────────────────────────────────────────────
const Y = "#FBBA00", YD = "#E5A800", K = "#1A1A1A";
const ZN = { terraza:"Terraza", salon:"Salón", barra:"Barra", bano:"Baño" };
const ZI = { terraza:"🌿", salon:"🛋", barra:"☕", bano:"🚿" };
const ZC = { terraza:"#D4FAD4", salon:"#DBEAFE", barra:"#FEF3C7", bano:"#E0E7FF" };
const ZA = { terraza:"#059669", salon:"#1D4ED8", barra:"#D97706", bano:"#6D28D9" };
const DS = ["lun","mar","mié","jue","vie","sáb","dom"];
const DF = ["Lunes","Martes","Miércoles","Jueves","Viernes","Sábado","Domingo"];
const BDL = { D:"Diaria", S:"Semanal", N:"Noche" };

// ── DEFAULT TASKS ─────────────────────────────────────────────────────────────
const DEFAULT_TASKS = [
  {id:"d1",z:"terraza",n:"Limpieza mesas y sillas",t:"D",sh:"m"},
  {id:"d2",z:"salon",n:"Farolillos",t:"D",sh:"m"},
  {id:"d3",z:"salon",n:"Círculos negros mesas",t:"D",sh:"m"},
  {id:"d4",z:"salon",n:"Organización bancos de bebida",t:"D",sh:"m"},
  {id:"n1",z:"barra",n:"Limpieza grifo y cafetera",t:"N",sh:"n"},
  {id:"n2",z:"bano",n:"Baños (repaso noche)",t:"N",sh:"n"},
  {id:"n3",z:"salon",n:"Repaso rápido sala",t:"N",sh:"n"},
  {id:"s01",z:"salon",n:"Sofás a fondo",t:"S",sh:"m",d:"lun"},
  {id:"s02",z:"salon",n:"Galidón a fondo (menús, cubiertos)",t:"S",sh:"m",d:"lun"},
  {id:"s03",z:"salon",n:"Limpiar entrada local",t:"S",sh:"m",d:"lun"},
  {id:"s04",z:"salon",n:"Mover mesas y sillas",t:"S",sh:"m",d:"mar"},
  {id:"s05",z:"salon",n:"Paredes de salón",t:"S",sh:"m",d:"mar"},
  {id:"s06",z:"terraza",n:"Barrer y fregar terraza",t:"S",sh:"m",d:"mié"},
  {id:"s07",z:"barra",n:"Cámaras de bebidas (agua, cerveza, refrescos)",t:"S",sh:"m",d:"mié"},
  {id:"s08",z:"barra",n:"Puertas y rieles cámaras",t:"S",sh:"m",d:"mié"},
  {id:"s09",z:"salon",n:"Cristaleras a fondo",t:"S",sh:"m",d:"jue"},
  {id:"s10",z:"barra",n:"Limpieza de copas y estanterías",t:"S",sh:"m",d:"jue"},
  {id:"s11",z:"barra",n:"Zona cafetera y organizador de cápsulas",t:"S",sh:"m",d:"jue"},
  {id:"s12",z:"salon",n:"Aire acondicionado (rejillas)",t:"S",sh:"m",d:"vie"},
  {id:"s13",z:"barra",n:"Mover cajas y limpieza a fondo",t:"S",sh:"m",d:"vie"},
  {id:"s14",z:"barra",n:"Congelador a fondo",t:"S",sh:"m",d:"vie"},
  {id:"s15",z:"barra",n:"Barra a fondo (agua y jabón)",t:"S",sh:"m",d:"vie"},
  {id:"s16",z:"terraza",n:"Pie sombrilla",t:"S",sh:"m",d:"sáb"},
  {id:"s17",z:"barra",n:"Zona TPV a fondo",t:"S",sh:"m",d:"sáb"},
  {id:"s18",z:"bano",n:"Zona pila y productos de limpieza",t:"S",sh:"m",d:"sáb"},
  {id:"s19",z:"salon",n:"Sillas a fondo",t:"S",sh:"m",d:"dom"},
  {id:"s20",z:"salon",n:"Lámparas y bombillas",t:"S",sh:"m",d:"dom"},
  {id:"s21",z:"bano",n:"Lavavajillas a fondo",t:"S",sh:"m",d:"dom"},
  {id:"s22",z:"bano",n:"WC a fondo (lejía y mistol)",t:"S",sh:"m",d:"dom"},
  {id:"s23",z:"bano",n:"Paredes y cristales (baño)",t:"S",sh:"m",d:"dom"},
];

const DEFAULT_TEAM = [
  {id:"u1",name:"Encargado/a",hours:40,libre:["lun","mar"],bg:Y,fg:K,init:"YO"},
  {id:"u2",name:"Compañero/a",hours:40,libre:["mié","jue"],bg:K,fg:Y,init:"C2"},
  {id:"u3",name:"Refuerzo",hours:20,libre:["lun","mar","mié","jue","vie"],bg:"#E8E8E3",fg:"#6B6B67",init:"C3"},
];

// ── HISTORY GENERATION ────────────────────────────────────────────────────────
function genHistory() {
  const h = {};
  const now = new Date();
  const dayRates = [0.68,0.72,0.81,0.83,0.85,0.91,0.89];
  const dayTotals = [7,9,12,12,14,11,13];
  for (let i = 29; i >= 0; i--) {
    const d = new Date(now); d.setDate(now.getDate() - i);
    const dow = d.getDay() === 0 ? 6 : d.getDay() - 1;
    const base = dayRates[dow];
    const noise = (Math.random() - 0.5) * 0.22;
    const rate = Math.max(0.35, Math.min(1, base + noise));
    const total = dayTotals[dow];
    const dateStr = d.toISOString().split("T")[0];
    h[dateStr] = {
      done: Math.round(total * rate), total,
      rate: Math.round(rate * 100),
      byZone: {
        terraza: Math.round(Math.max(45,Math.min(100,74+(Math.random()-.5)*40))),
        salon:   Math.round(Math.max(45,Math.min(100,77+(Math.random()-.5)*38))),
        barra:   Math.round(Math.max(35,Math.min(100,63+(Math.random()-.5)*44))),
        bano:    Math.round(Math.max(50,Math.min(100,81+(Math.random()-.5)*32))),
      }
    };
  }
  return h;
}

// ── STORAGE ───────────────────────────────────────────────────────────────────
const SK = "circoclean_react_v1";
function loadST() {
  try {
    const s = JSON.parse(localStorage.getItem(SK));
    if (s) return { done: s.done||{}, history: s.history||genHistory(), customTasks: s.customTasks||[], removedIds: s.removedIds||[], modifiedTasks: s.modifiedTasks||{}, team: s.team||null };
  } catch(e) {}
  return { done:{}, history:genHistory(), customTasks:[], removedIds:[], modifiedTasks:{}, team:null };
}
function saveST(st) {
  try { localStorage.setItem(SK, JSON.stringify(st)); } catch(e) {}
}

// ── HELPERS ───────────────────────────────────────────────────────────────────
function todayStr() { return new Date().toDateString(); }
function dow() { const d = new Date().getDay(); return d===0?6:d-1; }
function todayDia() { return DS[dow()]; }
function nowHHMM() { return new Date().toLocaleTimeString("es-ES",{hour:"2-digit",minute:"2-digit"}); }
function fmtDate() {
  const now = new Date();
  return {
    day:["Domingo","Lunes","Martes","Miércoles","Jueves","Viernes","Sábado"][now.getDay()],
    date:`${now.getDate()} de ${["enero","feb.","mar.","abr.","mayo","jun.","jul.","ago.","sep.","oct.","nov.","dic."][now.getMonth()]}`
  };
}

// ── MINI BAR CHART (no dep) ───────────────────────────────────────────────────
function MiniBar({ data, labels, colors, height=120 }) {
  const max = Math.max(...data, 1);
  return (
    <div style={{display:"flex",alignItems:"flex-end",gap:6,height,paddingTop:8}}>
      {data.map((v,i)=>(
        <div key={i} style={{flex:1,display:"flex",flexDirection:"column",alignItems:"center",gap:3}}>
          <span style={{fontSize:9,color:"#A8A8A2",fontWeight:700}}>{v}%</span>
          <div style={{width:"100%",height:(v/max)*(height-24),background:colors?colors[i]:Y,borderRadius:"4px 4px 0 0",transition:"height .4s",minHeight:3}}/>
          <span style={{fontSize:9,color:"#A8A8A2",fontWeight:700,textAlign:"center",lineHeight:1}}>{labels[i]}</span>
        </div>
      ))}
    </div>
  );
}

function LineChart({ data, labels, height=140 }) {
  if (!data.length) return null;
  const max = Math.max(...data, 1), min = Math.min(...data, 0);
  const range = max - min || 1;
  const w = 100, h = height - 24;
  const pts = data.map((v,i) => {
    const x = (i / (data.length-1)) * w;
    const y = h - ((v - min) / range) * h;
    return `${x},${y}`;
  }).join(" ");
  const area = `0,${h} ${pts} ${w},${h}`;
  return (
    <div style={{position:"relative",height,paddingBottom:20}}>
      <svg viewBox={`0 0 100 ${h}`} preserveAspectRatio="none" style={{position:"absolute",inset:0,width:"100%",height:"100%"}}>
        <defs>
          <linearGradient id="lg" x1="0" y1="0" x2="0" y2="1">
            <stop offset="0%" stopColor={Y} stopOpacity=".3"/>
            <stop offset="100%" stopColor={Y} stopOpacity="0"/>
          </linearGradient>
        </defs>
        <polygon points={area} fill="url(#lg)"/>
        <polyline points={pts} fill="none" stroke={Y} strokeWidth="1.5" strokeLinecap="round" strokeLinejoin="round"/>
      </svg>
      <div style={{position:"absolute",bottom:0,left:0,right:0,display:"flex",justifyContent:"space-between"}}>
        {labels.filter((_,i)=>i%Math.ceil(labels.length/6)===0).map((l,i)=>(
          <span key={i} style={{fontSize:9,color:"#A8A8A2"}}>{l}</span>
        ))}
      </div>
    </div>
  );
}

// ── COMPONENTS ────────────────────────────────────────────────────────────────
function Drip() {
  return (
    <svg width="68" height="9" viewBox="0 0 68 9" fill="none">
      <rect x="0" y="0" width="68" height="2.5" rx="1.25" fill={Y}/>
      <path d="M13 2 C13 2 13.2 5.5 12 7.2 C11.4 8.1 10.5 8.8 12 8.8 C13.5 8.8 12.8 8.1 12.2 7.2 C11 5.5 13 2 13 2Z" fill={Y}/>
      <path d="M34 2 C34 2 34.3 5.8 33 7.5 C32.3 8.4 31.3 9 33 9 C34.7 9 33.9 8.4 33.2 7.5 C31.9 5.8 34 2 34 2Z" fill={Y}/>
      <path d="M55 2 C55 2 55.2 5 54 6.5 C53.4 7.3 52.6 7.9 54 7.9 C55.4 7.9 54.8 7.3 54.2 6.5 C53 5 55 2 55 2Z" fill={Y}/>
    </svg>
  );
}

function Badge({ type }) {
  const styles = {
    D:{background:"#FEF3C7",color:"#92400E"},
    S:{background:"#DBEAFE",color:"#1E40AF"},
    N:{background:"#EDE9FE",color:"#5B21B6"},
  };
  return <span style={{fontSize:10,fontWeight:700,padding:"3px 8px",borderRadius:20,...(styles[type]||styles.D)}}>{BDL[type]}</span>;
}

function TaskCard({ task, onTap, done:isDone, interactive=true }) {
  return (
    <div onClick={interactive?onTap:undefined} style={{
      background: isDone?"#FFF9E1":"#fff",
      border: `1.5px solid ${isDone?"#FFE082":"#E8E8E3"}`,
      borderRadius:16, padding:"12px 14px", marginBottom:6,
      display:"flex", alignItems:"center", gap:12,
      cursor: interactive?"pointer":"default",
      boxShadow:"0 1px 2px rgba(0,0,0,.05)",
      transition:"transform .12s",
      minHeight:58,
      userSelect:"none",
    }}
    onMouseDown={e=>interactive&&(e.currentTarget.style.transform="scale(.984)")}
    onMouseUp={e=>interactive&&(e.currentTarget.style.transform="")}
    onMouseLeave={e=>interactive&&(e.currentTarget.style.transform="")}
    >
      <div style={{
        width:26,height:26,borderRadius:"50%",flexShrink:0,
        display:"flex",alignItems:"center",justifyContent:"center",
        background: isDone?"#16A34A":"#fff",
        border: `2px solid ${isDone?"#16A34A":"#D4D4CE"}`,
        transition:"all .2s",
      }}>
        {isDone && <svg width="13" height="13" viewBox="0 0 13 13" fill="none" stroke="#fff" strokeWidth="2.5" strokeLinecap="round" strokeLinejoin="round"><polyline points="2,6.5 5.5,10 11,3"/></svg>}
      </div>
      <div style={{flex:1,minWidth:0}}>
        <div style={{fontSize:14,fontWeight:500,color:isDone?"#6B6B67":K,textDecoration:isDone?"line-through":"none",lineHeight:1.3}}>{task.n}</div>
        <div style={{fontSize:11,color:"#A8A8A2",marginTop:2,fontWeight:500}}>{ZN[task.z]}</div>
      </div>
      <Badge type={task.t}/>
    </div>
  );
}

function SectionHdr({ label }) {
  return (
    <div style={{display:"flex",alignItems:"center",gap:8,margin:"14px 0 7px"}}>
      <span style={{fontSize:10,fontWeight:800,textTransform:"uppercase",letterSpacing:".1em",color:"#A8A8A2",whiteSpace:"nowrap"}}>{label}</span>
      <div style={{flex:1,height:1,background:"#E8E8E3"}}/>
    </div>
  );
}

function ProgBar({ done, total }) {
  const pct = total ? Math.round(done/total*100) : 0;
  return (
    <div style={{height:42,background:"#fff",borderBottom:"1px solid #E8E8E3",display:"flex",alignItems:"center",gap:10,padding:"0 16px",flexShrink:0}}>
      <span style={{fontSize:12,fontWeight:700,color:"#6B6B67",whiteSpace:"nowrap"}}>{done} / {total}</span>
      <div style={{flex:1,height:7,background:"#E8E8E3",borderRadius:4,overflow:"hidden"}}>
        <div style={{height:"100%",background:pct===100?"#16A34A":Y,borderRadius:4,width:pct+"%",transition:"width .5s cubic-bezier(.4,0,.2,1)"}}/>
      </div>
      <span style={{fontSize:12,fontWeight:700,minWidth:32,textAlign:"right"}}>{pct}%</span>
    </div>
  );
}

function ZoneTabs({ active, counts, onChange }) {
  const tabs = [{z:"all",lbl:"Todas"},{z:"terraza",lbl:"Terraza"},{z:"salon",lbl:"Salón"},{z:"barra",lbl:"Barra"},{z:"bano",lbl:"Baño"}];
  return (
    <div style={{height:44,background:"#fff",borderBottom:"1px solid #E8E8E3",display:"flex",alignItems:"stretch",padding:"0 12px",flexShrink:0,overflowX:"auto"}}>
      {tabs.map(({z,lbl})=>(
        <button key={z} onClick={()=>onChange(z)} style={{
          fontFamily:"inherit",fontSize:13,fontWeight:600,padding:"0 13px",
          border:"none",background:"transparent",color:active===z?K:"#6B6B67",cursor:"pointer",
          whiteSpace:"nowrap",borderBottom:`2.5px solid ${active===z?Y:"transparent"}`,
          transition:"all .15s",display:"flex",alignItems:"center",gap:4,
        }}>
          {lbl}
          <span style={{
            display:"inline-flex",alignItems:"center",justifyContent:"center",
            width:17,height:17,borderRadius:"50%",fontSize:10,fontWeight:700,
            background:active===z?Y:"#E8E8E3",color:active===z?K:"#6B6B67",
            transition:"all .15s",
          }}>{counts[z]||0}</span>
        </button>
      ))}
    </div>
  );
}

// ── HOY VIEW ──────────────────────────────────────────────────────────────────
function ViewHoy({ allTasks, shift, zona, done, onTap, onZona }) {
  const today = todayDia();
  const todayT = allTasks.filter(t => {
    if(t.sh!==shift) return false;
    if(t.t==="D"||t.t==="N") return true;
    if(t.t==="S") return t.d===today;
    return false;
  });
  const filtered = zona==="all" ? todayT : todayT.filter(t=>t.z===zona);
  const nd = todayT.filter(t=>done[`${todayStr()}_${t.id}`]).length;
  const counts = { all: todayT.length };
  ["terraza","salon","barra","bano"].forEach(z=>counts[z]=todayT.filter(t=>t.z===z).length);

  return (
    <div style={{display:"flex",flexDirection:"column",flex:1,overflow:"hidden"}}>
      <ProgBar done={nd} total={todayT.length}/>
      <ZoneTabs active={zona} counts={counts} onChange={onZona}/>
      <div style={{flex:1,overflowY:"auto",padding:"14px 16px 18px"}}>
        {zona==="all" && (
          <>
            <div style={{display:"grid",gridTemplateColumns:"1fr 1fr 1fr",gap:8,marginBottom:12}}>
              {[{v:nd,l:"completadas",c:"#16A34A"},{v:todayT.length-nd,l:"pendientes",c:K},{v:`${todayT.length?Math.round(nd/todayT.length*100):0}%`,l:"progreso",c:YD}].map(({v,l,c},i)=>(
                <div key={i} style={{background:"#fff",border:"1px solid #E8E8E3",borderRadius:16,padding:"11px 13px",boxShadow:"0 1px 2px rgba(0,0,0,.05)"}}>
                  <div style={{fontSize:26,fontWeight:800,color:c,lineHeight:1}}>{v}</div>
                  <div style={{fontSize:11,color:"#6B6B67",marginTop:2,fontWeight:500}}>{l}</div>
                </div>
              ))}
            </div>
            <div style={{display:"grid",gridTemplateColumns:"1fr 1fr",gap:8,marginBottom:14}}>
              {["terraza","salon","barra","bano"].map(z=>{
                const zt=todayT.filter(t=>t.z===z);
                const zd=zt.filter(t=>done[`${todayStr()}_${t.id}`]).length;
                const zp=zt.length?Math.round(zd/zt.length*100):0;
                const allDone=zp===100&&zt.length>0;
                return (
                  <div key={z} onClick={()=>onZona(z)} style={{
                    background:allDone?"#F0FDF4":"#fff",
                    border:`1.5px solid ${allDone?"#BBF7D0":zp>0?"#FFE082":"#E8E8E3"}`,
                    borderRadius:16,padding:"12px 13px",cursor:"pointer",
                    boxShadow:"0 1px 2px rgba(0,0,0,.05)",transition:"all .15s",
                  }}>
                    <div style={{fontSize:13,fontWeight:700,marginBottom:2,display:"flex",alignItems:"center",gap:5}}>
                      <div style={{width:22,height:22,borderRadius:6,background:ZC[z],color:ZA[z],display:"flex",alignItems:"center",justifyContent:"center",fontSize:11}}>{ZI[z]}</div>
                      {ZN[z]}
                    </div>
                    <div style={{fontSize:24,fontWeight:800,color:allDone?"#16A34A":K,lineHeight:1,margin:"3px 0 2px"}}>{zp}%</div>
                    <div style={{fontSize:11,color:"#6B6B67"}}>{zd} de {zt.length} tareas</div>
                    <div style={{height:4,background:"#E8E8E3",borderRadius:2,marginTop:8,overflow:"hidden"}}>
                      <div style={{width:zp+"%",height:"100%",background:allDone?"#16A34A":Y,borderRadius:2,transition:"width .4s"}}/>
                    </div>
                  </div>
                );
              })}
            </div>
          </>
        )}
        {["D","N"].some(t=>filtered.find(f=>f.t===t)) && (
          <><SectionHdr label={shift==="m"?"☀ Apertura · tareas diarias":"☾ Cierre · repaso noche"}/>{filtered.filter(t=>t.t==="D"||t.t==="N").map(t=><TaskCard key={t.id} task={t} done={!!done[`${todayStr()}_${t.id}`]} onTap={()=>onTap(t.id)}/>)}</>
        )}
        {filtered.some(t=>t.t==="S") && (
          <><SectionHdr label={`📋 Semanal asignada · ${today}`}/>{filtered.filter(t=>t.t==="S").map(t=><TaskCard key={t.id} task={t} done={!!done[`${todayStr()}_${t.id}`]} onTap={()=>onTap(t.id)}/>)}</>
        )}
        {!filtered.length && <div style={{textAlign:"center",padding:32}}><div style={{fontSize:36,marginBottom:8}}>✅</div><div style={{fontSize:13,fontWeight:600,color:"#A8A8A2"}}>Sin tareas para este turno</div></div>}
      </div>
    </div>
  );
}

// ── SEMANA VIEW ───────────────────────────────────────────────────────────────
function ViewSemana({ allTasks }) {
  const [selDay, setSelDay] = useState(dow());
  const today = dow();
  const now = new Date();
  const ws = new Date(now); ws.setDate(now.getDate()-today);
  return (
    <div style={{display:"flex",flexDirection:"column",flex:1,overflow:"hidden"}}>
      <div style={{background:"#fff",borderBottom:"1px solid #E8E8E3",padding:"10px 12px",display:"grid",gridTemplateColumns:"repeat(7,1fr)",gap:3,flexShrink:0}}>
        {DS.map((d,i)=>{
          const dt=new Date(ws); dt.setDate(ws.getDate()+i);
          const ns=allTasks.filter(t=>t.t==="S"&&t.d===d).length;
          const isToday=i===today, isSel=i===selDay;
          return (
            <div key={d} onClick={()=>setSelDay(i)} style={{textAlign:"center",cursor:"pointer"}}>
              <div style={{fontSize:9,fontWeight:800,textTransform:"uppercase",letterSpacing:".06em",color:"#A8A8A2",marginBottom:3}}>{d}</div>
              <div style={{width:32,height:32,borderRadius:"50%",margin:"0 auto 2px",display:"flex",alignItems:"center",justifyContent:"center",fontSize:12,fontWeight:700,
                background:isToday?K:isSel?"#FFF9E1":"transparent",
                border:`1.5px solid ${isToday?"transparent":isSel?Y:"transparent"}`,
                color:isToday?"#fff":K,transition:"all .15s",
              }}>{dt.getDate()}</div>
              <div style={{fontSize:9,color:"#A8A8A2",fontWeight:600}}>{ns}s</div>
              <div style={{width:5,height:5,borderRadius:"50%",background:ns>0?Y:"#E8E8E3",margin:"2px auto 0"}}/>
            </div>
          );
        })}
      </div>
      <div style={{flex:1,overflowY:"auto",padding:"14px 16px"}}>
        {(() => {
          const dia=DS[selDay];
          const sem=allTasks.filter(t=>t.t==="S"&&t.d===dia);
          const daily=allTasks.filter(t=>t.t==="D");
          return <>
            {sem.length ? <><SectionHdr label={`${DF[selDay]} · ${sem.length} tarea${sem.length!==1?"s":""} semanales`}/>{sem.map(t=><TaskCard key={t.id} task={t} done={false} interactive={false}/>)}</> : <div style={{textAlign:"center",padding:24}}><div style={{fontSize:30,marginBottom:6}}>📋</div><div style={{fontSize:13,fontWeight:600,color:"#A8A8A2"}}>Sin semanales el {DS[selDay]}</div></div>}
            <SectionHdr label="Tareas diarias · siempre"/>
            {daily.map(t=><div key={t.id} style={{opacity:.6}}><TaskCard task={t} done={false} interactive={false}/></div>)}
          </>;
        })()}
      </div>
    </div>
  );
}

// ── AI VIEW ───────────────────────────────────────────────────────────────────
function ViewIA({ allTasks }) {
  const [msgs, setMsgs] = useState([]);
  const [input, setInput] = useState("");
  const [loading, setLoading] = useState(false);
  const [pending, setPending] = useState({});
  const [aiHistory, setAiHistory] = useState([]);
  const [taskState, setTaskState] = useState(loadST());
  const bottomRef = useRef(null);

  useEffect(()=>{ bottomRef.current?.scrollIntoView({behavior:"smooth"}); },[msgs,loading]);

  const sysPrompt = useCallback(()=>{
    const tasks = allTasks.map(t=>({id:t.id,zona:t.z,nombre:t.n,tipo:t.t,turno:t.sh,dia:t.d||"-"}));
    return `Eres el asistente de limpieza de CIRCOCLEAN, restaurante Circo (Sevilla). Interpretas mensajes de empleados en español.

ZONAS: terraza, salon, barra, bano
TIPOS: D=diaria, S=semanal, N=noche
TURNOS: m=mañana, n=noche
DÍAS (solo S): lun, mar, mié, jue, vie, sáb, dom

TAREAS ACTUALES: ${JSON.stringify(tasks)}

Responde SOLO con JSON válido. Sin texto fuera del JSON.
{"action":"add|remove|modify|query|none","taskData":{"z":"zona","n":"nombre","t":"D|S|N","sh":"m|n","d":"dia_si_S"},"targetId":"id_si_remove_o_modify","message":"respuesta breve en español max 60 palabras","preview":"resumen corto de la acción"}`;
  },[allTasks]);

  async function send() {
    const msg = input.trim(); if(!msg||loading) return;
    setInput("");
    setMsgs(m=>[...m,{role:"user",text:msg,time:nowHHMM()}]);
    const newHist=[...aiHistory,{role:"user",content:msg}];
    setAiHistory(newHist);
    setLoading(true);
    try {
      const resp = await fetch("https://api.anthropic.com/v1/messages",{
        method:"POST",headers:{"Content-Type":"application/json"},
        body:JSON.stringify({model:"claude-sonnet-4-20250514",max_tokens:800,system:sysPrompt(),messages:newHist.slice(-12)})
      });
      const data = await resp.json();
      const raw = data.content?.[0]?.text||"{}";
      setAiHistory(h=>[...h,{role:"assistant",content:raw}]);
      let parsed;
      try { const m=raw.match(/\{[\s\S]*\}/); parsed=m?JSON.parse(m[0]):{action:"none",message:raw}; } catch(e){parsed={action:"none",message:raw};}
      if(parsed.action&&parsed.action!=="none"&&parsed.action!=="query"){
        const pid="p"+Date.now();
        setPending(p=>({...p,[pid]:parsed}));
        setMsgs(m=>[...m,{role:"ai",text:parsed.message,time:nowHHMM(),pid,preview:parsed.preview}]);
      } else {
        setMsgs(m=>[...m,{role:"ai",text:parsed.message||raw,time:nowHHMM()}]);
      }
    } catch(e) {
      setMsgs(m=>[...m,{role:"ai",text:"⚠ Error de conexión. Comprueba la red.",time:nowHHMM()}]);
    }
    setLoading(false);
  }

  function confirmAction(pid) {
    const p = pending[pid]; if(!p) return;
    const st = loadST();
    if(p.action==="add") { st.customTasks.push({...p.taskData,id:"ct"+Date.now()}); }
    else if(p.action==="remove") { if(!st.removedIds.includes(p.targetId)) st.removedIds.push(p.targetId); st.customTasks=st.customTasks.filter(t=>t.id!==p.targetId); }
    else if(p.action==="modify") {
      const isCustom=st.customTasks.find(t=>t.id===p.targetId);
      if(isCustom){const idx=st.customTasks.findIndex(t=>t.id===p.targetId);st.customTasks[idx]={...st.customTasks[idx],...p.taskData};}
      else{st.modifiedTasks[p.targetId]={...(st.modifiedTasks[p.targetId]||{}),...p.taskData};}
    }
    saveST(st);
    setPending(prev=>{const n={...prev};delete n[pid];return n;});
    setMsgs(m=>m.map(msg=>msg.pid===pid?{...msg,confirmed:true}:msg));
  }
  function cancelAction(pid) {
    setPending(prev=>{const n={...prev};delete n[pid];return n;});
    setMsgs(m=>m.map(msg=>msg.pid===pid?{...msg,cancelled:true}:msg));
  }

  const suggestions=["Añade limpiar el almacén los jueves a barra","Quita el pie sombrilla del sistema","Cambia cristaleras al lunes","¿Cuántas tareas hay en barra?"];

  return (
    <div style={{display:"flex",flexDirection:"column",flex:1,overflow:"hidden"}}>
      <div style={{padding:"10px 16px",background:"#fff",borderBottom:"1px solid #E8E8E3",display:"flex",alignItems:"center",gap:10,flexShrink:0}}>
        <div style={{width:36,height:36,borderRadius:"50%",background:K,display:"flex",alignItems:"center",justifyContent:"center",flexShrink:0}}>
          <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="#fff" strokeWidth="1.8" strokeLinecap="round" strokeLinejoin="round"><path d="M12 2a2 2 0 0 1 2 2c0 .74-.4 1.39-1 1.73V7h1a7 7 0 0 1 7 7h1a1 1 0 0 1 1 1v3a1 1 0 0 1-1 1h-1v1a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-1H2a1 1 0 0 1-1-1v-3a1 1 0 0 1 1-1h1a7 7 0 0 1 7-7h1V5.73c-.6-.34-1-.99-1-1.73a2 2 0 0 1 2-2"/><circle cx="9" cy="14" r="1" fill="#fff" stroke="none"/><circle cx="15" cy="14" r="1" fill="#fff" stroke="none"/></svg>
        </div>
        <div>
          <div style={{fontSize:14,fontWeight:700}}>Asistente CIRCOCLEAN</div>
          <div style={{fontSize:11,color:"#6B6B67"}}>Gestiona tareas con lenguaje natural</div>
        </div>
        <div style={{width:8,height:8,borderRadius:"50%",background:loading?"#F59E0B":"#16A34A",marginLeft:"auto",flexShrink:0,transition:"background .3s"}}/>
      </div>

      <div style={{flex:1,overflowY:"auto",padding:"14px 14px",display:"flex",flexDirection:"column",gap:10}}>
        {msgs.length===0 && (
          <div style={{display:"flex",flexDirection:"column",alignItems:"center",justifyContent:"center",flex:1,padding:"20px 16px",textAlign:"center"}}>
            <div style={{width:56,height:56,borderRadius:"50%",background:"#FFF9E1",display:"flex",alignItems:"center",justifyContent:"center",marginBottom:12}}>
              <svg width="26" height="26" viewBox="0 0 24 24" fill="none" stroke={YD} strokeWidth="1.8" strokeLinecap="round" strokeLinejoin="round"><path d="M12 2a2 2 0 0 1 2 2c0 .74-.4 1.39-1 1.73V7h1a7 7 0 0 1 7 7h1a1 1 0 0 1 1 1v3a1 1 0 0 1-1 1h-1v1a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-1H2a1 1 0 0 1-1-1v-3a1 1 0 0 1 1-1h1a7 7 0 0 1 7-7h1V5.73c-.6-.34-1-.99-1-1.73a2 2 0 0 1 2-2"/><circle cx="9" cy="14" r="1"/><circle cx="15" cy="14" r="1"/></svg>
            </div>
            <h3 style={{fontSize:15,fontWeight:700,marginBottom:6}}>Hola, soy tu asistente</h3>
            <p style={{fontSize:13,color:"#6B6B67",lineHeight:1.5,maxWidth:260}}>Puedo añadir, quitar o modificar tareas. Prueba con:</p>
            <div style={{display:"flex",flexWrap:"wrap",gap:7,justifyContent:"center",marginTop:14}}>
              {suggestions.map((s,i)=>(
                <button key={i} onClick={()=>setInput(s)} style={{background:"#fff",border:"1px solid #E8E8E3",borderRadius:20,padding:"7px 13px",fontSize:12,color:"#6B6B67",cursor:"pointer",fontFamily:"inherit",fontWeight:500,transition:"all .15s"}}>{s.length>28?s.slice(0,28)+"…":s}</button>
              ))}
            </div>
          </div>
        )}

        {msgs.map((m,i)=>(
          <div key={i} style={{display:"flex",flexDirection:"column",maxWidth:"85%",alignSelf:m.role==="user"?"flex-end":"flex-start",alignItems:m.role==="user"?"flex-end":"flex-start"}}>
            <div style={{
              padding:"10px 13px",borderRadius:16,fontSize:14,lineHeight:1.5,
              ...(m.role==="user"
                ?{background:K,color:"#fff",borderRadius:"16px 16px 4px 16px"}
                :{background:"#fff",color:K,border:"1px solid #E8E8E3",borderRadius:"4px 16px 16px 16px",boxShadow:"0 1px 2px rgba(0,0,0,.05)"})
            }}>{m.text}</div>
            {m.pid && !m.confirmed && !m.cancelled && (
              <div style={{background:"#fff",border:`1.5px solid ${Y}`,borderRadius:12,padding:"11px 13px",marginTop:6,maxWidth:300}}>
                <div style={{fontSize:10,fontWeight:800,textTransform:"uppercase",letterSpacing:".08em",color:YD,marginBottom:4}}>✨ Acción propuesta</div>
                <div style={{fontSize:12,color:"#6B6B67",marginBottom:8,lineHeight:1.4}}>{m.preview}</div>
                <div style={{display:"flex",gap:8}}>
                  <button onClick={()=>confirmAction(m.pid)} style={{flex:1,padding:8,background:Y,color:K,border:"none",borderRadius:8,fontFamily:"inherit",fontSize:13,fontWeight:700,cursor:"pointer"}}>✓ Confirmar</button>
                  <button onClick={()=>cancelAction(m.pid)} style={{flex:1,padding:8,background:"transparent",color:"#6B6B67",border:"1px solid #E8E8E3",borderRadius:8,fontFamily:"inherit",fontSize:13,fontWeight:600,cursor:"pointer"}}>Cancelar</button>
                </div>
              </div>
            )}
            {m.confirmed && <div style={{fontSize:11,color:"#16A34A",fontWeight:600,marginTop:4,padding:"0 4px"}}>✓ Cambio aplicado</div>}
            {m.cancelled && <div style={{fontSize:11,color:"#A8A8A2",marginTop:4,padding:"0 4px"}}>Cancelado</div>}
            <div style={{fontSize:10,color:"#A8A8A2",marginTop:3,padding:"0 4px"}}>{m.time}</div>
          </div>
        ))}

        {loading && (
          <div style={{display:"flex",flexDirection:"column",alignSelf:"flex-start"}}>
            <div style={{padding:"12px 16px",background:"#fff",border:"1px solid #E8E8E3",borderRadius:"4px 16px 16px 16px",boxShadow:"0 1px 2px rgba(0,0,0,.05)"}}>
              <div style={{display:"flex",gap:4,alignItems:"center"}}>
                {[0,1,2].map(i=><div key={i} style={{width:7,height:7,borderRadius:"50%",background:"#D4D4CE",animation:`bounce .8s ${i*.15}s ease infinite`}}/>)}
              </div>
            </div>
          </div>
        )}
        <div ref={bottomRef}/>
      </div>

      <div style={{background:"#fff",borderTop:"1px solid #E8E8E3",padding:"10px 14px",display:"flex",gap:8,alignItems:"center",flexShrink:0}}>
        <input value={input} onChange={e=>setInput(e.target.value)} onKeyDown={e=>e.key==="Enter"&&send()}
          placeholder="Escribe un mensaje…" style={{flex:1,background:"#F5F5F2",border:"1px solid #E8E8E3",borderRadius:24,padding:"10px 16px",fontFamily:"inherit",fontSize:14,outline:"none"}}/>
        <button onClick={send} disabled={loading} style={{width:40,height:40,borderRadius:"50%",background:loading?"#E8E8E3":Y,border:"none",cursor:loading?"not-allowed":"pointer",display:"flex",alignItems:"center",justifyContent:"center",flexShrink:0,transition:"all .15s"}}>
          <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke={loading?"#A8A8A2":K} strokeWidth="2" strokeLinecap="round" strokeLinejoin="round"><line x1="22" y1="2" x2="11" y2="13"/><polygon points="22 2 15 22 11 13 2 9 22 2"/></svg>
        </button>
      </div>
      <style>{`@keyframes bounce{0%,80%,100%{transform:scale(1);opacity:.5}40%{transform:scale(1.3);opacity:1}}`}</style>
    </div>
  );
}

// ── ADMIN VIEW ────────────────────────────────────────────────────────────────
function ViewAdmin({ allTasks, st, setST }) {
  const [tab, setTab] = useState("tareas");
  const [zFilter, setZFilter] = useState("all");
  const [modal, setModal] = useState(null); // {mode:"add"|"edit", task?}
  const [form, setForm] = useState({z:"terraza",n:"",t:"D",sh:"m",d:"lun"});

  const tabs = [{k:"tareas",l:"📋 Tareas"},{k:"equipo",l:"👥 Equipo"},{k:"reportes",l:"📊 Reportes"},{k:"whatsapp",l:"💬 WhatsApp"}];

  function openAdd() { setForm({z:"terraza",n:"",t:"D",sh:"m",d:"lun"}); setModal({mode:"add"}); }
  function openEdit(task) { setForm({z:task.z,n:task.n,t:task.t,sh:task.sh,d:task.d||"lun"}); setModal({mode:"edit",id:task.id}); }
  function saveTask() {
    if(!form.n.trim()) return;
    const newST = {...st};
    if(modal.mode==="add") {
      newST.customTasks=[...newST.customTasks,{...form,id:"ct"+Date.now()}];
    } else {
      const isCustom=newST.customTasks.find(t=>t.id===modal.id);
      if(isCustom){newST.customTasks=newST.customTasks.map(t=>t.id===modal.id?{...t,...form}:t);}
      else{newST.modifiedTasks={...newST.modifiedTasks,[modal.id]:{...(newST.modifiedTasks[modal.id]||{}),...form}};}
    }
    saveST(newST); setST(newST); setModal(null);
  }
  function deleteTask(id) {
    if(!window.confirm("¿Eliminar esta tarea?")) return;
    const newST={...st};
    if(newST.customTasks.some(t=>t.id===id)) newST.customTasks=newST.customTasks.filter(t=>t.id!==id);
    else if(!newST.removedIds.includes(id)) newST.removedIds=[...newST.removedIds,id];
    saveST(newST); setST(newST);
  }
  function saveTeam(team) {
    const newST={...st,team};saveST(newST);setST(newST);
  }

  return (
    <div style={{display:"flex",flexDirection:"column",flex:1,overflow:"hidden"}}>
      <div style={{display:"flex",background:"#fff",borderBottom:"1px solid #E8E8E3",flexShrink:0}}>
        {tabs.map(({k,l})=>(
          <button key={k} onClick={()=>setTab(k)} style={{flex:1,fontFamily:"inherit",fontSize:11,fontWeight:700,padding:"12px 4px",border:"none",background:"transparent",color:tab===k?K:"#6B6B67",cursor:"pointer",borderBottom:`2.5px solid ${tab===k?Y:"transparent"}`,transition:"all .15s",letterSpacing:".02em"}}>{l}</button>
        ))}
      </div>

      <div style={{flex:1,overflowY:"auto",padding:"14px 16px 80px",position:"relative"}}>
        {tab==="tareas" && (
          <>
            <div style={{display:"flex",gap:6,marginBottom:12,flexWrap:"wrap"}}>
              {["all","terraza","salon","barra","bano"].map(z=>(
                <button key={z} onClick={()=>setZFilter(z)} style={{fontFamily:"inherit",fontSize:12,fontWeight:600,padding:"6px 12px",borderRadius:20,border:`1px solid ${zFilter===z?"transparent":"#E8E8E3"}`,background:zFilter===z?K:"transparent",color:zFilter===z?"#fff":"#6B6B67",cursor:"pointer",transition:"all .15s"}}>{z==="all"?"Todas":ZN[z]}</button>
              ))}
            </div>
            {[{k:"D",l:"☀ Diarias"},{k:"S",l:"📋 Semanales"},{k:"N",l:"☾ Noche"}].map(({k,l})=>{
              const tasks=(zFilter==="all"?allTasks:allTasks.filter(t=>t.z===zFilter)).filter(t=>t.t===k);
              if(!tasks.length) return null;
              return (
                <div key={k}>
                  <SectionHdr label={l}/>
                  {tasks.map(t=>(
                    <div key={t.id} style={{background:"#fff",border:"1px solid #E8E8E3",borderRadius:12,padding:"11px 13px",marginBottom:6,display:"flex",alignItems:"center",gap:10,boxShadow:"0 1px 2px rgba(0,0,0,.04)"}}>
                      <div style={{flex:1,minWidth:0}}>
                        <div style={{fontSize:13,fontWeight:600}}>{t.n}</div>
                        <div style={{fontSize:11,color:"#A8A8A2",marginTop:2}}>{ZN[t.z]}{t.d?" · "+t.d:""}{st.customTasks.some(c=>c.id===t.id)?" · Personalizada":""}</div>
                      </div>
                      <div style={{display:"flex",gap:6,flexShrink:0}}>
                        <button onClick={()=>openEdit(t)} style={{width:32,height:32,borderRadius:8,border:"1px solid #E8E8E3",background:"transparent",cursor:"pointer",display:"flex",alignItems:"center",justifyContent:"center",color:"#6B6B67"}}>
                          <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" strokeWidth="1.8" strokeLinecap="round" strokeLinejoin="round"><path d="M11 4H4a2 2 0 0 0-2 2v14a2 2 0 0 0 2 2h14a2 2 0 0 0 2-2v-7"/><path d="M18.5 2.5a2.121 2.121 0 0 1 3 3L12 15l-4 1 1-4 9.5-9.5z"/></svg>
                        </button>
                        <button onClick={()=>deleteTask(t.id)} style={{width:32,height:32,borderRadius:8,border:"1px solid #E8E8E3",background:"transparent",cursor:"pointer",display:"flex",alignItems:"center",justifyContent:"center",color:"#A8A8A2"}}>
                          <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" strokeWidth="1.8" strokeLinecap="round" strokeLinejoin="round"><polyline points="3 6 5 6 21 6"/><path d="M19 6l-1 14a2 2 0 0 1-2 2H8a2 2 0 0 1-2-2L5 6"/><path d="M10 11v6"/><path d="M14 11v6"/><path d="M9 6V4h6v2"/></svg>
                        </button>
                      </div>
                    </div>
                  ))}
                </div>
              );
            })}
            <button onClick={openAdd} style={{position:"absolute",bottom:16,right:16,width:52,height:52,borderRadius:"50%",background:Y,border:"none",cursor:"pointer",display:"flex",alignItems:"center",justifyContent:"center",boxShadow:`0 4px 16px rgba(251,186,0,.4)`,transition:"all .18s"}}>
              <svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke={K} strokeWidth="2.5" strokeLinecap="round"><line x1="12" y1="5" x2="12" y2="19"/><line x1="5" y1="12" x2="19" y2="12"/></svg>
            </button>
          </>
        )}

        {tab==="equipo" && <TeamTab team={st.team||DEFAULT_TEAM.map(t=>({...t}))} onSave={saveTeam}/>}
        {tab==="reportes" && <ReportesTab history={st.history||{}}/>}
        {tab==="whatsapp" && <WATab allTasks={allTasks} st={st} setST={setST}/>}
      </div>

      {modal && (
        <div onClick={e=>e.target===e.currentTarget&&setModal(null)} style={{position:"absolute",inset:0,background:"rgba(0,0,0,.5)",display:"flex",alignItems:"flex-end",zIndex:100}}>
          <div style={{background:"#fff",borderRadius:"24px 24px 0 0",width:"100%",maxHeight:"90%",overflow:"hidden",display:"flex",flexDirection:"column"}}>
            <div style={{display:"flex",alignItems:"center",justifyContent:"space-between",padding:"16px 18px",borderBottom:"1px solid #E8E8E3",flexShrink:0}}>
              <span style={{fontSize:16,fontWeight:700}}>{modal.mode==="add"?"Nueva tarea":"Editar tarea"}</span>
              <button onClick={()=>setModal(null)} style={{width:32,height:32,borderRadius:"50%",border:"1px solid #E8E8E3",background:"transparent",cursor:"pointer",fontSize:18,color:"#6B6B67",display:"flex",alignItems:"center",justifyContent:"center"}}>×</button>
            </div>
            <div style={{overflowY:"auto",padding:"16px 18px",flex:1}}>
              {[
                {id:"n",label:"Nombre",type:"text",placeholder:"Ej: Limpiar almacén"},
              ].map(f=>(
                <div key={f.id} style={{marginBottom:14}}>
                  <label style={{display:"block",fontSize:11,fontWeight:700,textTransform:"uppercase",letterSpacing:".08em",color:"#A8A8A2",marginBottom:5}}>{f.label}</label>
                  <input value={form[f.id]} onChange={e=>setForm(p=>({...p,[f.id]:e.target.value}))} placeholder={f.placeholder} style={{width:"100%",fontFamily:"inherit",fontSize:14,padding:"10px 12px",border:`1.5px solid ${form[f.id]?"#E8E8E3":"#FCA5A5"}`,borderRadius:12,background:"#F5F5F2",outline:"none"}}/>
                </div>
              ))}
              {[
                {id:"z",label:"Zona",opts:Object.entries(ZN).map(([k,v])=>({v:k,l:v}))},
                {id:"t",label:"Tipo",opts:[{v:"D",l:"Diaria (cada apertura)"},{v:"S",l:"Semanal (día concreto)"},{v:"N",l:"Noche (cierre)"}]},
                {id:"sh",label:"Turno",opts:[{v:"m",l:"Mañana / Apertura"},{v:"n",l:"Noche / Cierre"}]},
              ].map(f=>(
                <div key={f.id} style={{marginBottom:14}}>
                  <label style={{display:"block",fontSize:11,fontWeight:700,textTransform:"uppercase",letterSpacing:".08em",color:"#A8A8A2",marginBottom:5}}>{f.label}</label>
                  <select value={form[f.id]} onChange={e=>setForm(p=>({...p,[f.id]:e.target.value}))} style={{width:"100%",fontFamily:"inherit",fontSize:14,padding:"10px 12px",border:"1.5px solid #E8E8E3",borderRadius:12,background:"#F5F5F2",outline:"none"}}>
                    {f.opts.map(o=><option key={o.v} value={o.v}>{o.l}</option>)}
                  </select>
                </div>
              ))}
              {form.t==="S" && (
                <div style={{marginBottom:14}}>
                  <label style={{display:"block",fontSize:11,fontWeight:700,textTransform:"uppercase",letterSpacing:".08em",color:"#A8A8A2",marginBottom:5}}>Día asignado</label>
                  <select value={form.d} onChange={e=>setForm(p=>({...p,d:e.target.value}))} style={{width:"100%",fontFamily:"inherit",fontSize:14,padding:"10px 12px",border:"1.5px solid #E8E8E3",borderRadius:12,background:"#F5F5F2",outline:"none"}}>
                    {DS.map(d=><option key={d} value={d}>{d}</option>)}
                  </select>
                </div>
              )}
            </div>
            <div style={{padding:"12px 18px",borderTop:"1px solid #E8E8E3",flexShrink:0}}>
              <button onClick={saveTask} style={{width:"100%",padding:13,background:Y,color:K,border:"none",borderRadius:16,fontFamily:"inherit",fontSize:15,fontWeight:700,cursor:"pointer"}}>Guardar</button>
            </div>
          </div>
        </div>
      )}
    </div>
  );
}

function TeamTab({ team, onSave }) {
  const [local, setLocal] = useState(team.map(t=>({...t})));
  function update(i,k,v){setLocal(l=>l.map((m,j)=>j===i?{...m,[k]:v}:m))}
  return (
    <div>
      <SectionHdr label="Equipo de sala"/>
      {local.map((m,i)=>(
        <div key={m.id} style={{background:"#fff",border:"1.5px solid #E8E8E3",borderRadius:20,padding:14,marginBottom:8,boxShadow:"0 1px 2px rgba(0,0,0,.04)"}}>
          <div style={{display:"flex",alignItems:"center",gap:12,marginBottom:12}}>
            <div style={{width:44,height:44,borderRadius:"50%",background:m.bg,color:m.fg,display:"flex",alignItems:"center",justifyContent:"center",fontSize:13,fontWeight:800,flexShrink:0}}>{m.init}</div>
            <input value={m.name} onChange={e=>update(i,"name",e.target.value)} style={{flex:1,fontFamily:"inherit",fontSize:15,fontWeight:700,background:"transparent",border:"none",borderBottom:"1.5px solid #E8E8E3",padding:"2px 0",outline:"none"}}/>
          </div>
          <div style={{display:"grid",gridTemplateColumns:"1fr 1fr",gap:8}}>
            {[{k:"hours",l:"Horas/semana",type:"number"},{k:"libre",l:"Días libranza (sep. por coma)",type:"text",val:m.libre.join(", "),onChange:v=>update(i,"libre",v.split(",").map(s=>s.trim()).filter(Boolean))}].map(f=>(
              <div key={f.k}>
                <label style={{display:"block",fontSize:10,fontWeight:700,textTransform:"uppercase",letterSpacing:".08em",color:"#A8A8A2",marginBottom:3}}>{f.l}</label>
                <input type={f.type||"text"} value={f.val!==undefined?f.val:m[f.k]} onChange={e=>f.onChange?f.onChange(e.target.value):update(i,f.k,e.target.value)} style={{width:"100%",fontFamily:"inherit",fontSize:13,padding:"7px 10px",border:"1px solid #E8E8E3",borderRadius:8,background:"#F5F5F2",outline:"none"}}/>
              </div>
            ))}
          </div>
          <button onClick={()=>onSave(local)} style={{marginTop:10,width:"100%",padding:9,background:K,color:"#fff",border:"none",borderRadius:12,fontFamily:"inherit",fontSize:13,fontWeight:700,cursor:"pointer"}}>Guardar cambios</button>
        </div>
      ))}
      <SectionHdr label="Cobertura diaria"/>
      <div style={{background:"#fff",border:"1px solid #E8E8E3",borderRadius:16,padding:"4px 14px",boxShadow:"0 1px 2px rgba(0,0,0,.04)"}}>
        {DS.map(d=>{
          const n=local.filter(m=>!m.libre.includes(d)).length;
          const col=n===0?"#E8E8E3":n===local.length?"#16A34A":Y;
          return (
            <div key={d} style={{display:"flex",alignItems:"center",gap:12,padding:"8px 0",borderBottom:"1px solid #E8E8E3"}}>
              <span style={{fontSize:13,fontWeight:700,minWidth:32}}>{d}</span>
              <div style={{flex:1,height:7,background:"#E8E8E3",borderRadius:4,overflow:"hidden"}}>
                <div style={{width:`${Math.round(n/local.length*100)}%`,height:"100%",background:col,borderRadius:4,transition:"width .4s"}}/>
              </div>
              <span style={{fontSize:11,color:"#6B6B67",minWidth:72,textAlign:"right"}}>{n} / {local.length} pers.</span>
            </div>
          );
        })}
      </div>
    </div>
  );
}

function ReportesTab({ history }) {
  const hist = Object.entries(history).sort(([a],[b])=>a.localeCompare(b)).slice(-30);
  const rates = hist.map(([,v])=>v.rate);
  const avg = rates.length ? Math.round(rates.reduce((a,b)=>a+b,0)/rates.length) : 0;
  const maxR = Math.max(...rates,0);
  const maxDay = hist[rates.indexOf(maxR)]?.[0]||"-";
  const maxFmt = maxDay!=="-" ? new Date(maxDay).toLocaleDateString("es-ES",{day:"numeric",month:"short"}) : "-";
  const zoneAvgs = {};
  ["terraza","salon","barra","bano"].forEach(z=>{
    const vals=hist.map(([,v])=>v.byZone?.[z]||0);
    zoneAvgs[z]=vals.length?Math.round(vals.reduce((a,b)=>a+b,0)/vals.length):0;
  });
  const worstZ = Object.entries(zoneAvgs).sort(([,a],[,b])=>a-b)[0];
  const streak = (()=>{let s=0;for(const[,v]of[...hist].reverse()){if(v.rate>=75)s++;else break}return s;})();
  const dowAvgs = DS.map((_,i)=>{
    const vals=hist.filter(([d])=>{const dw=new Date(d).getDay()===0?6:new Date(d).getDay()-1;return dw===i;}).map(([,v])=>v.rate);
    return vals.length?Math.round(vals.reduce((a,b)=>a+b,0)/vals.length):0;
  });
  const lineLabels = hist.map(([d])=>new Date(d).toLocaleDateString("es-ES",{day:"numeric",month:"short"}));

  return (
    <div>
      <div style={{display:"grid",gridTemplateColumns:"1fr 1fr",gap:8,marginBottom:14}}>
        {[{v:`${avg}%`,l:"Media mensual",s:"completado por turno",c:YD},{v:`${maxR}%`,l:"Mejor día",s:maxFmt,c:"#16A34A"},{v:`${worstZ?zoneAvgs[worstZ[0]]:0}%`,l:"Zona crítica",s:worstZ?ZN[worstZ[0]]:"-",c:"#DC2626"},{v:streak,l:"Racha actual",s:"días seguidos >75%",c:K}].map(({v,l,s,c},i)=>(
          <div key={i} style={{background:"#fff",border:"1px solid #E8E8E3",borderRadius:16,padding:"12px 13px",boxShadow:"0 1px 2px rgba(0,0,0,.04)"}}>
            <div style={{fontSize:26,fontWeight:800,color:c,lineHeight:1}}>{v}</div>
            <div style={{fontSize:11,color:"#6B6B67",marginTop:2,fontWeight:500}}>{l}</div>
            <div style={{fontSize:10,color:"#A8A8A2",marginTop:1}}>{s}</div>
          </div>
        ))}
      </div>

      <div style={{background:"#fff",border:"1px solid #E8E8E3",borderRadius:16,padding:14,boxShadow:"0 1px 2px rgba(0,0,0,.04)",marginBottom:10}}>
        <div style={{fontSize:12,fontWeight:700,marginBottom:10}}>📈 Completado diario · últimos 30 días</div>
        <LineChart data={rates} labels={lineLabels} height={150}/>
      </div>

      <div style={{display:"grid",gridTemplateColumns:"1fr 1fr",gap:10}}>
        <div style={{background:"#fff",border:"1px solid #E8E8E3",borderRadius:16,padding:14,boxShadow:"0 1px 2px rgba(0,0,0,.04)"}}>
          <div style={{fontSize:12,fontWeight:700,marginBottom:4}}>Por zona</div>
          <MiniBar data={["terraza","salon","barra","bano"].map(z=>zoneAvgs[z]||0)} labels={["terraza","salon","barra","bano"].map(z=>ZN[z].slice(0,4))} colors={["terraza","salon","barra","bano"].map(z=>ZA[z])} height={120}/>
        </div>
        <div style={{background:"#fff",border:"1px solid #E8E8E3",borderRadius:16,padding:14,boxShadow:"0 1px 2px rgba(0,0,0,.04)"}}>
          <div style={{fontSize:12,fontWeight:700,marginBottom:4}}>Por día semana</div>
          <MiniBar data={dowAvgs} labels={DS} colors={dowAvgs.map(v=>v>=80?"#16A34A":v>=65?Y:"#D97706")} height={120}/>
        </div>
      </div>

      <SectionHdr label="Desglose por zona (media mensual)"/>
      <div style={{background:"#fff",border:"1px solid #E8E8E3",borderRadius:16,padding:"4px 14px",boxShadow:"0 1px 2px rgba(0,0,0,.04)"}}>
        {Object.entries(zoneAvgs).sort(([,a],[,b])=>b-a).map(([z,pct])=>(
          <div key={z} style={{display:"flex",alignItems:"center",gap:10,padding:"8px 0",borderBottom:"1px solid #E8E8E3"}}>
            <span style={{fontSize:13,fontWeight:700,minWidth:60}}>{ZN[z]}</span>
            <div style={{flex:1,height:8,background:"#E8E8E3",borderRadius:4,overflow:"hidden"}}><div style={{width:pct+"%",height:"100%",background:ZA[z],borderRadius:4}}/></div>
            <span style={{fontSize:13,fontWeight:700,minWidth:36,textAlign:"right"}}>{pct}%</span>
          </div>
        ))}
      </div>
      <div style={{height:20}}/>
    </div>
  );
}

function WATab({ allTasks, st, setST }) {
  const shift = "m";
  const today = todayDia();
  const all = allTasks.filter(t=>{ if(t.sh!==shift)return false; if(t.t==="D"||t.t==="N")return true; if(t.t==="S")return t.d===today; return false; });
  const nd = all.filter(t=>st.done[`${todayStr()}_${t.id}`]);
  const pend = all.filter(t=>!st.done[`${todayStr()}_${t.id}`]);
  const pct = all.length?Math.round(nd.length/all.length*100):0;
  const fecha = new Date().toLocaleDateString("es-ES",{weekday:"long",day:"numeric",month:"long"});
  const byZona={};nd.forEach(t=>{if(!byZona[t.z])byZona[t.z]=[];byZona[t.z].push(t.n)});
  const doneText=Object.entries(byZona).map(([z,ts])=>`  ${ZN[z]}:\n${ts.map(n=>`    ✓ ${n}`).join("\n")}`).join("\n")||"  — Ninguna completada aún";
  const pendText=pend.length?pend.map(t=>`  • ${ZN[t.z]}: ${t.n}`).join("\n"):"  — Todo completado 🎉";
  const diario=`🧹 *CIRCOCLEAN · LIMPIEZA DIARIA*\n📅 ${fecha}\n🕐 Turno: Mañana (Apertura)\n\n✅ *Completadas (${nd.length}/${all.length}) · ${pct}%*\n${doneText}\n\n⏳ *Pendientes (${pend.length}):*\n${pendText}${pct===100?"\n\n🌟 ¡Turno completado al 100%!":""}`.trim();
  const semanal=`📋 *CIRCOCLEAN · PLAN SEMANAL*\n\n🗓 Distribución:\n  Lun (1p): Sofás, Galidón, Entrada\n  Mar (1p): Mesas/sillas, Paredes\n  Mié (2p): Terraza, Cámaras, Rieles\n  Jue (2p): Cristaleras, Copas, Cafetera\n  Vie (2p): Aire, Cajas, Congelador, Barra\n  Sáb (3p): Sombrilla, TPV, Zona pila\n  Dom (3p): Sillas, Lámparas, WC, Lavavajillas\n\n✅ Diarias: ${allTasks.filter(t=>t.t==="D").length} fijas · ☾ Noche: ${allTasks.filter(t=>t.t==="N").length} · 📋 Semanales: ${allTasks.filter(t=>t.t==="S").length}`;

  function copy(txt){navigator.clipboard.writeText(txt).catch(()=>{})}
  function reset(){
    const now=todayStr();const newDone={...st.done};
    Object.keys(newDone).forEach(k=>{if(k.startsWith(now))delete newDone[k]});
    const newST={...st,done:newDone};saveST(newST);setST(newST);
  }

  return (
    <div>
      <SectionHdr label="Reporte diario · WhatsApp"/>
      <div style={{background:"#fff",border:"1.5px solid #E8E8E3",borderRadius:16,padding:14,fontFamily:"'Courier New',monospace",fontSize:12,lineHeight:1.7,whiteSpace:"pre-wrap",wordBreak:"break-word",boxShadow:"0 1px 2px rgba(0,0,0,.04)"}}>{diario}</div>
      <div style={{display:"flex",gap:8,marginTop:10}}>
        <button onClick={()=>copy(diario)} style={{flex:1,padding:12,background:Y,color:K,border:"none",borderRadius:12,fontFamily:"inherit",fontSize:13,fontWeight:700,cursor:"pointer"}}>📋 Copiar para WhatsApp</button>
        <button onClick={reset} style={{padding:"12px 16px",background:"#F5F5F2",color:K,border:"1.5px solid #E8E8E3",borderRadius:12,fontFamily:"inherit",fontSize:13,fontWeight:600,cursor:"pointer"}}>↺ Reset</button>
      </div>
      <div style={{height:1,background:"#E8E8E3",margin:"16px 0"}}/>
      <SectionHdr label="Resumen semanal"/>
      <div style={{background:"#fff",border:"1.5px solid #E8E8E3",borderRadius:16,padding:14,fontFamily:"'Courier New',monospace",fontSize:12,lineHeight:1.7,whiteSpace:"pre-wrap",wordBreak:"break-word",boxShadow:"0 1px 2px rgba(0,0,0,.04)"}}>{semanal}</div>
      <button onClick={()=>copy(semanal)} style={{width:"100%",marginTop:10,padding:12,background:"#F5F5F2",color:K,border:"1.5px solid #E8E8E3",borderRadius:12,fontFamily:"inherit",fontSize:13,fontWeight:700,cursor:"pointer"}}>📋 Copiar resumen</button>
      <div style={{height:20}}/>
    </div>
  );
}

// ── BOTTOM NAV ────────────────────────────────────────────────────────────────
function BottomNav({ view, onNav, hasAIActivity }) {
  const items = [
    {k:"hoy",l:"HOY",icon:<svg className="ni" viewBox="0 0 24 24" fill="none" stroke="currentColor" strokeWidth="1.8" strokeLinecap="round" strokeLinejoin="round"><rect x="3" y="4" width="18" height="18" rx="2"/><line x1="16" y1="2" x2="16" y2="6"/><line x1="8" y1="2" x2="8" y2="6"/><line x1="3" y1="10" x2="21" y2="10"/><line x1="8" y1="14" x2="8.01" y2="14" strokeWidth="2.5"/><line x1="12" y1="14" x2="12.01" y2="14" strokeWidth="2.5"/><line x1="16" y1="14" x2="16.01" y2="14" strokeWidth="2.5"/></svg>},
    {k:"semana",l:"SEMANA",icon:<svg className="ni" viewBox="0 0 24 24" fill="none" stroke="currentColor" strokeWidth="1.8" strokeLinecap="round" strokeLinejoin="round"><rect x="3" y="4" width="18" height="18" rx="2"/><line x1="16" y1="2" x2="16" y2="6"/><line x1="8" y1="2" x2="8" y2="6"/><line x1="3" y1="10" x2="21" y2="10"/><polyline points="9 16 11 18 15 14"/></svg>},
    {k:"ia",l:"IA",icon:<svg className="ni" viewBox="0 0 24 24" fill="none" stroke="currentColor" strokeWidth="1.8" strokeLinecap="round" strokeLinejoin="round"><path d="M12 2a2 2 0 0 1 2 2c0 .74-.4 1.39-1 1.73V7h1a7 7 0 0 1 7 7h1a1 1 0 0 1 1 1v3a1 1 0 0 1-1 1h-1v1a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-1H2a1 1 0 0 1-1-1v-3a1 1 0 0 1 1-1h1a7 7 0 0 1 7-7h1V5.73c-.6-.34-1-.99-1-1.73a2 2 0 0 1 2-2"/><circle cx="9" cy="14" r="1"/><circle cx="15" cy="14" r="1"/></svg>},
    {k:"admin",l:"ADMIN",icon:<svg className="ni" viewBox="0 0 24 24" fill="none" stroke="currentColor" strokeWidth="1.8" strokeLinecap="round" strokeLinejoin="round"><path d="M12.22 2h-.44a2 2 0 0 0-2 2v.18a2 2 0 0 1-1 1.73l-.43.25a2 2 0 0 1-2 0l-.15-.08a2 2 0 0 0-2.73.73l-.22.38a2 2 0 0 0 .73 2.73l.15.1a2 2 0 0 1 1 1.72v.51a2 2 0 0 1-1 1.74l-.15.09a2 2 0 0 0-.73 2.73l.22.38a2 2 0 0 0 2.73.73l.15-.08a2 2 0 0 1 2 0l.43.25a2 2 0 0 1 1 1.73V20a2 2 0 0 0 2 2h.44a2 2 0 0 0 2-2v-.18a2 2 0 0 1 1-1.73l.43-.25a2 2 0 0 1 2 0l.15.08a2 2 0 0 0 2.73-.73l.22-.39a2 2 0 0 0-.73-2.73l-.15-.08a2 2 0 0 1-1-1.74v-.5a2 2 0 0 1 1-1.74l.15-.09a2 2 0 0 0 .73-2.73l-.22-.38a2 2 0 0 0-2.73-.73l-.15.08a2 2 0 0 1-2 0l-.43-.25a2 2 0 0 1-1-1.73V4a2 2 0 0 0-2-2z"/><circle cx="12" cy="12" r="3"/></svg>},
  ];
  return (
    <nav style={{height:62,background:"#fff",borderTop:"1px solid #E8E8E3",display:"flex",flexShrink:0}}>
      <style>{`.ni{width:21px;height:21px}`}</style>
      {items.map(({k,l,icon})=>(
        <button key={k} onClick={()=>onNav(k)} style={{flex:1,display:"flex",flexDirection:"column",alignItems:"center",justifyContent:"center",gap:2,cursor:"pointer",border:"none",background:"transparent",fontFamily:"inherit",color:view===k?K:"#A8A8A2",fontSize:10,fontWeight:700,transition:"color .15s",position:"relative",letterSpacing:".02em"}}>
          <div style={{width:21,height:21,color:view===k?K:"#A8A8A2"}}>{icon}</div>
          {l}
          {view===k && <div style={{position:"absolute",top:0,left:"25%",right:"25%",height:2,background:Y,borderRadius:"0 0 2px 2px"}}/>}
          {k==="ia"&&hasAIActivity&&view!=="ia" && <div style={{position:"absolute",top:6,right:"calc(25% - 4px)",width:7,height:7,borderRadius:"50%",background:Y,border:"2px solid #fff"}}/>}
        </button>
      ))}
    </nav>
  );
}

// ── TOAST ─────────────────────────────────────────────────────────────────────
function Toast({ msg }) {
  return msg ? (
    <div style={{position:"absolute",bottom:76,left:"50%",transform:"translateX(-50%)",background:K,color:"#fff",padding:"10px 20px",borderRadius:24,fontSize:13,fontWeight:600,whiteSpace:"nowrap",zIndex:1000,pointerEvents:"none",boxShadow:"0 4px 16px rgba(0,0,0,.2)"}}>
      {msg}
    </div>
  ) : null;
}

// ── ROOT APP ──────────────────────────────────────────────────────────────────
export default function App() {
  const [view, setView] = useState("hoy");
  const [shift, setShift] = useState(()=>new Date().getHours()>=19||new Date().getHours()<6?"n":"m");
  const [zona, setZona] = useState("all");
  const [st, setST] = useState(loadST);
  const [toastMsg, setToastMsg] = useState("");
  const [hasAI, setHasAI] = useState(false);
  const toastTimer = useRef(null);
  const {day,date} = fmtDate();

  function getAllTasks() {
    const base = DEFAULT_TASKS.filter(t=>!st.removedIds.includes(t.id)).map(t=>st.modifiedTasks[t.id]?{...t,...st.modifiedTasks[t.id]}:t);
    return [...base,...st.customTasks];
  }
  const allTasks = getAllTasks();

  function toast(msg) {
    setToastMsg(msg);
    clearTimeout(toastTimer.current);
    toastTimer.current = setTimeout(()=>setToastMsg(""),2400);
  }

  function tapTask(id) {
    const k = `${todayStr()}_${id}`;
    const newDone = {...st.done};
    if(newDone[k]) delete newDone[k]; else newDone[k]=true;
    const all = allTasks.filter(t=>{
      if(t.sh!==shift)return false;
      if(t.t==="D"||t.t==="N")return true;
      if(t.t==="S")return t.d===todayDia();
      return false;
    });
    const nd = all.filter(t=>newDone[`${todayStr()}_${t.id}`]).length;
    const newST = {...st,done:newDone};
    saveST(newST); setST(newST);
    if(nd===all.length&&all.length>0) toast("🎉 ¡Todo completado!");
    else toast(newDone[k]?"✓ Tarea completada":"Tarea desmarcada");
  }

  function handleNav(v) {
    setView(v);
    if(v==="ia") setHasAI(false);
  }

  return (
    <div style={{display:"flex",flexDirection:"column",height:"100%",background:"#F5F5F2",fontFamily:"'Plus Jakarta Sans',-apple-system,sans-serif",WebkitFontSmoothing:"antialiased",position:"relative",overflow:"hidden"}}>
      <style>{`@import url('https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@400;500;600;700;800&display=swap');*{box-sizing:border-box;margin:0;padding:0;-webkit-tap-highlight-color:transparent}`}</style>

      {/* HEADER */}
      <header style={{height:60,background:"#fff",borderBottom:"1px solid #E8E8E3",display:"flex",alignItems:"center",gap:12,padding:"0 16px",flexShrink:0,zIndex:10}}>
        <div style={{display:"flex",flexDirection:"column",alignItems:"flex-start",gap:0,lineHeight:1}}>
          <div style={{fontWeight:800,fontSize:17,letterSpacing:"-.5px",lineHeight:1}}>CIRCO<span style={{color:"#A8A8A2",fontWeight:600}}>CLEAN</span></div>
          <div style={{marginTop:3,opacity:.9}}><Drip/></div>
        </div>
        <div style={{flex:1,textAlign:"center"}}>
          <div style={{fontSize:14,fontWeight:700}}>{day}</div>
          <div style={{fontSize:11,color:"#6B6B67",marginTop:1}}>{date}</div>
        </div>
        <div style={{display:"flex",background:"#F5F5F2",border:"1px solid #E8E8E3",borderRadius:8,padding:3,gap:2}}>
          {[{k:"m",l:"Mañana",icon:<svg width="12" height="12" viewBox="0 0 24 24" fill="none" stroke="currentColor" strokeWidth="1.8" strokeLinecap="round"><circle cx="12" cy="12" r="4"/><line x1="12" y1="2" x2="12" y2="4"/><line x1="12" y1="20" x2="12" y2="22"/><line x1="4.22" y1="4.22" x2="5.64" y2="5.64"/><line x1="18.36" y1="18.36" x2="19.78" y2="19.78"/><line x1="2" y1="12" x2="4" y2="12"/><line x1="20" y1="12" x2="22" y2="12"/></svg>},{k:"n",l:"Noche",icon:<svg width="12" height="12" viewBox="0 0 24 24" fill="none" stroke="currentColor" strokeWidth="1.8" strokeLinecap="round"><path d="M21 12.79A9 9 0 1 1 11.21 3 7 7 0 0 0 21 12.79z"/></svg>}].map(({k,l,icon})=>(
            <button key={k} onClick={()=>setShift(k)} style={{fontFamily:"inherit",fontSize:11,fontWeight:700,padding:"5px 11px",border:"none",borderRadius:6,cursor:"pointer",transition:"all .18s",background:shift===k?(k==="n"?"#312E81":K):"transparent",color:shift===k?"#fff":"#6B6B67",display:"flex",alignItems:"center",gap:4,whiteSpace:"nowrap"}}>
              {icon}{l}
            </button>
          ))}
        </div>
      </header>

      {/* VIEWS */}
      {view==="hoy" && <ViewHoy allTasks={allTasks} shift={shift} zona={zona} done={st.done} onTap={tapTask} onZona={setZona}/>}
      {view==="semana" && <ViewSemana allTasks={allTasks}/>}
      {view==="ia" && <ViewIA allTasks={allTasks}/>}
      {view==="admin" && <ViewAdmin allTasks={allTasks} st={st} setST={setST}/>}

      <BottomNav view={view} onNav={handleNav} hasAIActivity={hasAI}/>
      <Toast msg={toastMsg}/>
    </div>
  );
}
