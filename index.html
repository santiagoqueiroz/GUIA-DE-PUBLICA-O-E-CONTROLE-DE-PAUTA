import { useState } from "react";

const WEEKDAYS = ["Dom", "Seg", "Ter", "Qua", "Qui", "Sex", "Sáb"];

const MONTHS_PT = [
  "Janeiro", "Fevereiro", "Março", "Abril", "Maio", "Junho",
  "Julho", "Agosto", "Setembro", "Outubro", "Novembro", "Dezembro"
];

// ========== FERIADOS ==========
function getFixedHolidays(year) {
  return [
    [year, 0, 1],   // Confraternização Universal
    [year, 3, 21],  // Tiradentes
    [year, 4, 1],   // Dia do Trabalho
    [year, 5, 15],  // Aniversário do Acre
    [year, 8, 5],   // Dia da Amazônia
    [year, 8, 7],   // Independência do Brasil
    [year, 9, 12],  // Nossa Senhora Aparecida
    [year, 10, 2],  // Finados
    [year, 10, 15], // Proclamação da República
    [year, 10, 17], // Tratado de Petrópolis
    [year, 10, 20], // Consciência Negra
    [year, 11, 8],  // Dia da Justiça
    [year, 11, 25], // Natal
  ];
}

function getEaster(year) {
  const a = year % 19;
  const b = Math.floor(year / 100);
  const c = year % 100;
  const d = Math.floor(b / 4);
  const e = b % 4;
  const f = Math.floor((b + 8) / 25);
  const g = Math.floor((b - f + 1) / 3);
  const h = (19 * a + b - d - g + 15) % 30;
  const i = Math.floor(c / 4);
  const k = c % 4;
  const l = (32 + 2 * e + 2 * i - h - k) % 7;
  const m = Math.floor((a + 11 * h + 22 * l) / 451);
  const month = Math.floor((h + l - 7 * m + 114) / 31) - 1;
  const day = ((h + l - 7 * m + 114) % 31) + 1;
  return new Date(year, month, day);
}

function getMovableHolidays(year) {
  const easter = getEaster(year);
  const e = easter.getTime();
  const day = 86400000;
  return [
    new Date(e - 48 * day),
    new Date(e - 47 * day),
    new Date(e - 2 * day),
    new Date(e),
    new Date(e + 60 * day),
  ].map(d => [d.getFullYear(), d.getMonth(), d.getDate()]);
}

function getAllHolidays(year) {
  const years = [year - 1, year, year + 1];
  const all = [];
  years.forEach(y => {
    all.push(...getFixedHolidays(y));
    all.push(...getMovableHolidays(y));
  });
  return all;
}

function isHoliday(year, month, day, holidays) {
  return holidays.some(h => h[0] === year && h[1] === month && h[2] === day);
}

function isWeekend(year, month, day) {
  const d = new Date(year, month, day).getDay();
  return d === 0 || d === 6;
}

function isBusinessDay(year, month, day, holidays) {
  return !isWeekend(year, month, day) && !isHoliday(year, month, day, holidays);
}

function addBusinessDays(date, count, direction, holidays) {
  let d = new Date(date);
  let remaining = Math.abs(count);
  const dir = direction < 0 ? -1 : 1;
  while (remaining > 0) {
    d.setDate(d.getDate() + dir);
    if (isBusinessDay(d.getFullYear(), d.getMonth(), d.getDate(), holidays)) {
      remaining--;
    }
  }
  return d;
}

function sameDay(d1, y, m, d) {
  return d1.getFullYear() === y && d1.getMonth() === m && d1.getDate() === d;
}

function formatDate(d) {
  const dias = ["Domingo","Segunda-feira","Terça-feira","Quarta-feira","Quinta-feira","Sexta-feira","Sábado"];
  return `${dias[d.getDay()]}, ${String(d.getDate()).padStart(2,'0')}/${String(d.getMonth()+1).padStart(2,'0')}/${d.getFullYear()}`;
}

function formatShort(d) {
  return `${String(d.getDate()).padStart(2,'0')}/${String(d.getMonth()+1).padStart(2,'0')}`;
}

function getHolidayName(year, month, day) {
  const names = {
    "0-1": "Confraternização Universal", "3-21": "Tiradentes", "4-1": "Dia do Trabalho",
    "5-15": "Aniversário do Acre", "8-5": "Dia da Amazônia", "8-7": "Independência do Brasil",
    "9-12": "N. Sra. Aparecida", "10-2": "Finados", "10-15": "Proclamação da República",
    "10-17": "Tratado de Petrópolis", "10-20": "Consciência Negra", "11-8": "Dia da Justiça", "11-25": "Natal",
  };
  const key = `${month}-${day}`;
  if (names[key]) return names[key];
  const easter = getEaster(year);
  const e = easter.getTime();
  const dTime = new Date(year, month, day).getTime();
  const dayMs = 86400000;
  const diff = Math.round((dTime - e) / dayMs);
  if (diff === -48) return "Seg. Carnaval";
  if (diff === -47) return "Terça Carnaval";
  if (diff === -2) return "Sexta-feira Santa";
  if (diff === 0) return "Páscoa";
  if (diff === 60) return "Corpus Christi";
  return "Feriado";
}

// ========== TIMELINE CALC ==========
function calcTimeline(sessionDate, holidays) {
  const sd = new Date(sessionDate);
  const prazoFim = addBusinessDays(sd, 1, -1, holidays);
  const prazoInicio = addBusinessDays(prazoFim, 4, -1, holidays);
  const publicacaoConsiderada = addBusinessDays(prazoInicio, 1, -1, holidays);
  const disponibilizacao = addBusinessDays(publicacaoConsiderada, 1, -1, holidays);
  const envioPublicacao = addBusinessDays(disponibilizacao, 1, -1, holidays);
  const verificacao48h = addBusinessDays(sd, 2, -1, holidays);
  return { sessionDate: sd, envioPublicacao, disponibilizacao, publicacaoConsiderada, prazoInicio, prazoFim, verificacao48h };
}

const LEGEND = [
  { key: "envio", color: "#E67E22", label: "Envio p/ Publicação" },
  { key: "disp", color: "#9B59B6", label: "Disponibilização DJe" },
  { key: "pub", color: "#2980B9", label: "Publicação Considerada" },
  { key: "prazo", color: "#27AE60", label: "Prazo 5 Dias Úteis" },
  { key: "verif", color: "#C0392B", label: "Verificação 48h (Art. 8º, II)" },
  { key: "sessao", color: "#F0C040", label: "Sessão de Julgamento" },
  { key: "feriado", color: "#FF6B9D", label: "Feriado" },
];

export default function App() {
  const today = new Date();
  const [year, setYear] = useState(today.getFullYear());
  const [month, setMonth] = useState(today.getMonth());
  const [selectedDay, setSelectedDay] = useState(null);
  const [timeline, setTimeline] = useState(null);

  const holidays = getAllHolidays(year);
  const daysInMonth = new Date(year, month + 1, 0).getDate();
  const firstDay = new Date(year, month, 1).getDay();

  const handleDayClick = (day) => {
    if (!isBusinessDay(year, month, day, holidays)) return;
    setSelectedDay(day);
    setTimeline(calcTimeline(new Date(year, month, day), holidays));
  };

  const prevMonth = () => {
    if (month === 0) { setMonth(11); setYear(y => y - 1); } else setMonth(m => m - 1);
    setSelectedDay(null); setTimeline(null);
  };
  const nextMonth = () => {
    if (month === 11) { setMonth(0); setYear(y => y + 1); } else setMonth(m => m + 1);
    setSelectedDay(null); setTimeline(null);
  };

  function getDayFlags(day) {
    if (!timeline) return {};
    const f = {};
    if (sameDay(timeline.envioPublicacao, year, month, day)) f.envio = true;
    if (sameDay(timeline.disponibilizacao, year, month, day)) f.disp = true;
    if (sameDay(timeline.publicacaoConsiderada, year, month, day)) f.pub = true;
    if (sameDay(timeline.verificacao48h, year, month, day)) f.verif = true;
    if (sameDay(timeline.sessionDate, year, month, day)) f.sessao = true;
    const thisDate = new Date(year, month, day);
    if (thisDate >= timeline.prazoInicio && thisDate <= timeline.prazoFim && isBusinessDay(year, month, day, holidays)) f.prazo = true;
    return f;
  }

  function getDayStyle(day) {
    const f = getDayFlags(day);
    const we = isWeekend(year, month, day);
    const hol = isHoliday(year, month, day, holidays);
    if (f.sessao) return { bg: "linear-gradient(135deg,#1A1A2E,#2C3E50)", text: "#F0C040", border: "2px solid #F0C040" };
    if (f.verif) return { bg: "#C0392B", text: "#FFF", border: "2px solid #922B21" };
    if (f.envio) return { bg: "#E67E22", text: "#FFF", border: "2px solid #CA6F1E" };
    if (f.disp) return { bg: "#9B59B6", text: "#FFF", border: "2px solid #7D3C98" };
    if (f.pub) return { bg: "#2980B9", text: "#FFF", border: "2px solid #1F618D" };
    if (f.prazo) return { bg: "#27AE60", text: "#FFF", border: "2px solid #1E8449" };
    if (hol && !we) return { bg: "linear-gradient(135deg,#FF6B9D22,#FF6B9D11)", text: "#FF6B9D", border: "2px solid #FF6B9D55" };
    if (we) return { bg: "#1A1F2E", text: "#445", border: "2px solid transparent" };
    if (selectedDay === day) return { bg: "#D5F5E3", text: "#1A1A2E", border: "2px solid #27AE60" };
    return { bg: "rgba(255,255,255,0.06)", text: "#CDD", border: "2px solid rgba(255,255,255,0.08)" };
  }

  const weeks = [];
  let cw = new Array(firstDay).fill(null);
  for (let d = 1; d <= daysInMonth; d++) {
    cw.push(d);
    if (cw.length === 7) { weeks.push(cw); cw = []; }
  }
  if (cw.length > 0) { while (cw.length < 7) cw.push(null); weeks.push(cw); }

  return (
    <div style={{ minHeight:"100vh", background:"linear-gradient(165deg,#0F1923 0%,#1A2744 40%,#1E3A5F 100%)", fontFamily:"'Segoe UI','Helvetica Neue',sans-serif", padding:"24px 16px", color:"#E8E8E8" }}>
      
      {/* Header */}
      <div style={{ textAlign:"center", marginBottom:24 }}>
        <div style={{ display:"inline-block", background:"rgba(255,255,255,0.06)", backdropFilter:"blur(12px)", borderRadius:16, padding:"18px 32px", border:"1px solid rgba(255,255,255,0.1)" }}>
          <h1 style={{ fontSize:18, fontWeight:700, margin:0, letterSpacing:"0.5px", color:"#F0C040" }}>⚖️ GUIA DE PUBLICAÇÃO E CONTROLE DE PAUTA</h1>
          <p style={{ margin:"6px 0 0", fontSize:11, color:"#8A9BB0", letterSpacing:"1.5px", textTransform:"uppercase" }}>Julgamento Eletrônico — Órgãos Fracionários — TJAC</p>
          <p style={{ margin:"4px 0 0", fontSize:10, color:"#667788" }}>Contagem exclusiva em dias úteis • Feriados nacionais e estaduais (AC) incluídos</p>
        </div>
      </div>

      {/* Instruction */}
      <div style={{ maxWidth:820, margin:"0 auto 18px", background:"rgba(255,255,255,0.04)", borderRadius:12, padding:"12px 18px", border:"1px solid rgba(255,255,255,0.08)", fontSize:12.5, color:"#9AB", textAlign:"center", lineHeight:1.6 }}>
        Selecione um <strong style={{ color:"#F0C040" }}>dia útil</strong> para definir a data da sessão. Fins de semana e feriados são <strong style={{ color:"#FF6B9D" }}>automaticamente excluídos</strong> de toda a contagem.
      </div>

      {/* Calendar */}
      <div style={{ maxWidth:820, margin:"0 auto 20px", background:"rgba(255,255,255,0.05)", borderRadius:16, padding:22, border:"1px solid rgba(255,255,255,0.1)" }}>
        <div style={{ display:"flex", justifyContent:"space-between", alignItems:"center", marginBottom:18 }}>
          <button onClick={prevMonth} style={{ background:"rgba(255,255,255,0.1)", border:"none", color:"#FFF", borderRadius:8, padding:"8px 16px", cursor:"pointer", fontSize:16, fontWeight:600 }}>◀</button>
          <h2 style={{ margin:0, fontSize:20, fontWeight:700, color:"#FFF", letterSpacing:1 }}>{MONTHS_PT[month]} {year}</h2>
          <button onClick={nextMonth} style={{ background:"rgba(255,255,255,0.1)", border:"none", color:"#FFF", borderRadius:8, padding:"8px 16px", cursor:"pointer", fontSize:16, fontWeight:600 }}>▶</button>
        </div>

        <div style={{ display:"grid", gridTemplateColumns:"repeat(7,1fr)", gap:4, marginBottom:6 }}>
          {WEEKDAYS.map((wd,i) => (
            <div key={i} style={{ textAlign:"center", fontSize:11, fontWeight:700, color:(i===0||i===6)?"#E74C3C":"#8899AA", letterSpacing:1, textTransform:"uppercase", padding:"6px 0" }}>{wd}</div>
          ))}
        </div>

        {weeks.map((week,wi) => (
          <div key={wi} style={{ display:"grid", gridTemplateColumns:"repeat(7,1fr)", gap:4, marginBottom:4 }}>
            {week.map((day,di) => {
              if (!day) return <div key={di} />;
              const st = getDayStyle(day);
              const we = isWeekend(year,month,day);
              const hol = isHoliday(year,month,day,holidays);
              const biz = isBusinessDay(year,month,day,holidays);
              const flags = getDayFlags(day);
              const hasEv = Object.keys(flags).length > 0;
              let tip = "";
              if (hol && !we) tip = getHolidayName(year,month,day);
              else if (we) tip = "Fim de semana";
              else if (!hasEv) tip = "Clique para definir como sessão";

              return (
                <div key={di} title={tip} onClick={() => handleDayClick(day)} style={{
                  background:st.bg, color:st.text, border:st.border, borderRadius:10, padding:"8px 4px",
                  textAlign:"center", fontSize:14, fontWeight:hasEv?700:biz?500:400,
                  cursor:biz?"pointer":"default", transition:"all 0.2s",
                  position:"relative", minHeight:48, display:"flex", flexDirection:"column",
                  alignItems:"center", justifyContent:"center",
                  opacity:(!biz && !hasEv)?0.45:1, boxShadow:hasEv?"0 2px 10px rgba(0,0,0,0.35)":"none",
                }}>
                  {day}
                  {(hol && !we) && <span style={{ fontSize:7, marginTop:1, color:"#FF6B9D", letterSpacing:0.3 }}>FERIADO</span>}
                  {we && <span style={{ fontSize:7, marginTop:1, color:"#556" }}>{new Date(year,month,day).getDay()===0?"DOM":"SÁB"}</span>}
                  {hasEv && (
                    <div style={{ display:"flex", gap:2, marginTop:2, flexWrap:"wrap", justifyContent:"center" }}>
                      {flags.envio && <span style={{ width:5, height:5, borderRadius:"50%", background:"#E67E22" }} />}
                      {flags.disp && <span style={{ width:5, height:5, borderRadius:"50%", background:"#9B59B6" }} />}
                      {flags.pub && <span style={{ width:5, height:5, borderRadius:"50%", background:"#2980B9" }} />}
                      {flags.prazo && <span style={{ width:5, height:5, borderRadius:"50%", background:"#27AE60" }} />}
                      {flags.verif && <span style={{ width:5, height:5, borderRadius:"50%", background:"#C0392B" }} />}
                      {flags.sessao && <span style={{ width:5, height:5, borderRadius:"50%", background:"#F0C040" }} />}
                    </div>
                  )}
                </div>
              );
            })}
          </div>
        ))}
      </div>

      {/* Legend */}
      <div style={{ maxWidth:820, margin:"0 auto 20px", display:"flex", flexWrap:"wrap", gap:8, justifyContent:"center" }}>
        {LEGEND.map(l => (
          <div key={l.key} style={{ display:"flex", alignItems:"center", gap:6, background:"rgba(255,255,255,0.05)", borderRadius:8, padding:"5px 10px", border:"1px solid rgba(255,255,255,0.08)", fontSize:10.5, color:"#BCC" }}>
            <span style={{ width:10, height:10, borderRadius:3, background:l.color, flexShrink:0 }} />
            {l.label}
          </div>
        ))}
      </div>

      {/* Timeline */}
      {timeline && (
        <div style={{ maxWidth:820, margin:"0 auto", background:"rgba(255,255,255,0.05)", borderRadius:16, padding:24, border:"1px solid rgba(255,255,255,0.1)" }}>
          <h3 style={{ margin:"0 0 6px", fontSize:17, fontWeight:700, color:"#F0C040", textAlign:"center" }}>📅 Linha do Tempo Completa</h3>
          <p style={{ margin:"0 0 20px", fontSize:12, color:"#8A9BB0", textAlign:"center" }}>Sessão: {formatDate(timeline.sessionDate)} • Todos os marcos em dias úteis</p>

          <div style={{ position:"relative", paddingLeft:28 }}>
            <div style={{ position:"absolute", left:12, top:8, bottom:8, width:2, background:"rgba(255,255,255,0.12)", borderRadius:2 }} />

            {[
              { color:"#E67E22", icon:"📤", title:"Envio para Publicação", date:timeline.envioPublicacao,
                desc:"A Coordenadoria do órgão fracionário envia a pauta para publicação no DJe. Marco em dia útil." },
              { color:"#9B59B6", icon:"📰", title:"Disponibilização no DJe", date:timeline.disponibilizacao,
                desc:"A pauta é disponibilizada no DJe em dia útil. A publicação será considerada efetivada no próximo dia útil." },
              { color:"#2980B9", icon:"📋", title:"Publicação Considerada", date:timeline.publicacaoConsiderada,
                desc:"Publicação considerada efetivada (1º dia útil após a disponibilização). O prazo de 5 dias úteis inicia no dia útil seguinte." },
              { color:"#27AE60", icon:"⏳", title:"Prazo de 5 Dias Úteis", date:timeline.prazoInicio,
                subtitle:`${formatShort(timeline.prazoInicio)} → ${formatShort(timeline.prazoFim)}`,
                desc:"Prazo mínimo de 5 dias úteis entre a publicação e a sessão (Res. CNJ 591/2024). Fins de semana e feriados NÃO são contados. Partes podem se manifestar nos autos." },
              { color:"#C0392B", icon:"🔍", title:"Verificação 48h Úteis — Retirada de Pauta", date:timeline.verificacao48h,
                desc:"Até 2 dias úteis antes da sessão, o Coordenador verifica processos com pedido de retirada de pauta (art. 8º, II, Res. 591/2024 CNJ)." },
              { color:"#F0C040", icon:"⚖️", title:"Sessão de Julgamento Eletrônico", date:timeline.sessionDate, highlight:true,
                desc:"Início da sessão de julgamento eletrônico do órgão fracionário." },
            ].map((item,i) => (
              <div key={i} style={{ position:"relative", marginBottom:18, paddingLeft:20 }}>
                <div style={{ position:"absolute", left:-20, top:6, width:14, height:14, borderRadius:"50%", background:item.color, border:"3px solid rgba(255,255,255,0.15)", boxShadow:`0 0 10px ${item.color}55` }} />
                <div style={{
                  background:item.highlight?"linear-gradient(135deg,rgba(240,192,64,0.12),rgba(240,192,64,0.03))":"rgba(255,255,255,0.03)",
                  borderRadius:12, padding:"12px 16px",
                  border:item.highlight?"1px solid rgba(240,192,64,0.25)":"1px solid rgba(255,255,255,0.06)",
                }}>
                  <div style={{ display:"flex", justifyContent:"space-between", alignItems:"center", marginBottom:5, flexWrap:"wrap", gap:6 }}>
                    <span style={{ fontSize:13.5, fontWeight:700, color:item.highlight?"#F0C040":"#FFF" }}>{item.icon} {item.title}</span>
                    <div style={{ display:"flex", gap:6, alignItems:"center" }}>
                      {item.subtitle && <span style={{ fontSize:11, fontWeight:600, color:item.color, background:`${item.color}22`, padding:"2px 8px", borderRadius:5 }}>{item.subtitle}</span>}
                      <span style={{ fontSize:11, fontWeight:700, background:item.color, color:item.color==="#F0C040"?"#1A1A2E":"#FFF", padding:"3px 10px", borderRadius:6 }}>{formatShort(item.date)}</span>
                    </div>
                  </div>
                  <p style={{ margin:0, fontSize:12, color:"#8A9BB0", lineHeight:1.6 }}>{item.desc}</p>
                </div>
              </div>
            ))}
          </div>

          {/* Warning */}
          <div style={{ marginTop:18, background:"rgba(192,57,43,0.1)", border:"1px solid rgba(192,57,43,0.25)", borderRadius:12, padding:"12px 16px" }}>
            <p style={{ margin:0, fontSize:12, color:"#E8BCBC", lineHeight:1.7 }}>
              <strong style={{ color:"#E74C3C" }}>⚠️ Art. 8º, II, Resolução n.º 591/2024 — CNJ:</strong>{" "}
              O Coordenador do órgão fracionário deve verificar, até <strong>2 dias úteis antes da sessão</strong> ({formatDate(timeline.verificacao48h)}), os processos com pedido de retirada de pauta.
            </p>
          </div>

          {/* Info */}
          <div style={{ marginTop:12, background:"rgba(39,174,96,0.08)", border:"1px solid rgba(39,174,96,0.2)", borderRadius:12, padding:"12px 16px" }}>
            <p style={{ margin:0, fontSize:11.5, color:"#A3D9B1", lineHeight:1.6 }}>
              <strong style={{ color:"#27AE60" }}>ℹ️ Observação:</strong>{" "}
              Toda a contagem é realizada exclusivamente em <strong>dias úteis</strong>. Sábados, domingos e feriados nacionais/estaduais (AC) são desconsiderados em todas as etapas do fluxo.
            </p>
          </div>
        </div>
      )}

      <div style={{ maxWidth:820, margin:"20px auto 0", textAlign:"center", fontSize:9.5, color:"#445566", letterSpacing:0.5, lineHeight:1.6 }}>
        Tribunal de Justiça do Estado do Acre — Segunda Câmara Cível — Coordenadoria<br/>
        Res. CNJ n.º 591/2024 • Contagem em dias úteis (Art. 219 do CPC)
      </div>
    </div>
  );
}
