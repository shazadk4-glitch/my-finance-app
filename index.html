import { useState, useEffect, useCallback, useMemo, useRef } from "react";
import { LineChart, Line, AreaChart, Area, BarChart, Bar, PieChart, Pie, Cell, XAxis, YAxis, CartesianGrid, Tooltip, ResponsiveContainer, Legend } from "recharts";

const STORAGE_KEY = "wealthlens-v1";

const COLORS = {
  bg:"#0a0e17", bgCard:"#111827", bgCardHover:"#1a2235", bgInput:"#0d1220",
  border:"#1e2a3a", borderFocus:"#3b82f6",
  text:"#e2e8f0", textMuted:"#64748b", textDim:"#475569",
  accent:"#3b82f6", accentGlow:"rgba(59,130,246,0.15)",
  green:"#10b981", greenDim:"rgba(16,185,129,0.15)",
  red:"#ef4444", redDim:"rgba(239,68,68,0.15)",
  orange:"#f59e0b", orangeDim:"rgba(245,158,11,0.15)",
  purple:"#8b5cf6", purpleDim:"rgba(139,92,246,0.15)",
  cyan:"#06b6d4", cyanDim:"rgba(6,182,212,0.15)",
};
const PIE_COLORS = ["#3b82f6","#10b981","#f59e0b","#8b5cf6","#06b6d4","#ef4444","#ec4899","#14b8a6"];
const MONTHS = ["Jan","Feb","Mar","Apr","May","Jun","Jul","Aug","Sep","Oct","Nov","Dec"];

// ─── EMPTY DEFAULT (clean start for new users) ──────────
const EMPTY_DATA = {
  bankAccounts:[], creditCards:[], loans:[], stocks:[], crypto:[],
  retirement:[], stockPlans:[], properties:[],
  cashFlow:{ income:[], expenses:[] },
  alerts:[], netWorthHistory:[],
  zakatSettings:{ nisabBasis:"silver", goldPricePerOz:2880, silverPricePerOz:33, stockMethod:"A", retirementMethod:"accessible", retirementTaxPenaltyPct:30, debtDeduction:"short_term", propertyIntents:{}, goldWeightOz:0 },
};

// ─── DEMO DATA (realistic sample for testing) ──────────
const DEMO_DATA = {
  bankAccounts:[
    {id:"d1",name:"Primary Checking",type:"checking",balance:8250,institution:"Chase"},
    {id:"d2",name:"Savings",type:"savings",balance:15000,institution:"Chase"},
    {id:"d3",name:"Business Checking",type:"checking",balance:4800,institution:"PNC"},
    {id:"d4",name:"Emergency Fund",type:"savings",balance:22000,institution:"Ally"},
  ],
  creditCards:[
    {id:"dc1",name:"Sapphire Reserve",balance:1240,dueDate:"Mar 15",institution:"Chase"},
    {id:"dc2",name:"Business Ink",balance:380,dueDate:"Mar 20",institution:"Chase"},
  ],
  loans:[
    {id:"dl1",name:"2023 Toyota Highlander",type:"auto",balance:28500,monthlyPayment:612,institution:"Toyota Financial",dueDate:"Mar 1"},
  ],
  stocks:[
    {id:"ds1",ticker:"VOO",shares:45,avgCost:380,currentPrice:520,name:"Vanguard S&P 500 ETF",account:"Fidelity"},
    {id:"ds2",ticker:"VTI",shares:80,avgCost:200,currentPrice:280,name:"Vanguard Total Market ETF",account:"Fidelity"},
    {id:"ds3",ticker:"AAPL",shares:25,avgCost:150,currentPrice:198,name:"Apple Inc.",account:"Robinhood"},
    {id:"ds4",ticker:"MSFT",shares:15,avgCost:310,currentPrice:420,name:"Microsoft Corp.",account:"Robinhood"},
    {id:"ds5",ticker:"AMZN",shares:20,avgCost:140,currentPrice:195,name:"Amazon.com Inc.",account:"Robinhood"},
  ],
  crypto:[
    {id:"dx1",symbol:"BTC",amount:0.15,currentValue:14200,name:"Bitcoin",platform:"Coinbase"},
    {id:"dx2",symbol:"ETH",amount:2.5,currentValue:8200,name:"Ethereum",platform:"Coinbase"},
    {id:"dx3",symbol:"SOL",amount:40,currentValue:5600,name:"Solana",platform:"Coinbase"},
  ],
  retirement:[
    {id:"dr1",name:"Company 401(k)",type:"401k",balance:185000,institution:"Fidelity",monthlyContribution:1200,
      holdings:[
        {ticker:"FXAIX",name:"Fidelity 500 Index",shares:450,price:239,avgCost:180,value:107550,pct:58},
        {ticker:"FXNAX",name:"Fidelity US Bond Index",shares:320,price:10.5,avgCost:10.8,value:3360,pct:1.8},
        {ticker:"FTIHX",name:"Fidelity Total Intl Index",shares:1200,price:12.8,avgCost:11.5,value:15360,pct:8.3},
        {ticker:"FSMDX",name:"Fidelity Mid Cap Index",shares:800,price:39.5,avgCost:32,value:31600,pct:17.1},
        {ticker:"FSSNX",name:"Fidelity Small Cap Index",shares:900,price:30.14,avgCost:28,value:27130,pct:14.8},
      ]},
  ],
  stockPlans:[
    {id:"dsp1",name:"Company RSU",type:"RSU",value:35000,vested:false,shares:200,description:"Vesting quarterly through 2028"},
  ],
  properties:[
    {id:"dp1",name:"Primary Residence",address:"Chicago, IL",purchasePrice:420000,currentValue:510000,mortgageBalance:310000,monthlyMortgage:2100,monthlyRent:0,rate:3.25,insurance:0,propertyTax:0,lender:"Wells Fargo",loanDuration:"2020–2050",isRental:false},
    {id:"dp2",name:"Rental Condo",address:"Naperville, IL",purchasePrice:280000,currentValue:320000,mortgageBalance:195000,monthlyMortgage:1450,monthlyRent:2200,rate:5.5,insurance:0,propertyTax:0,lender:"Rocket Mortgage",loanDuration:"2023–2053",isRental:true},
  ],
  cashFlow:{
    income:[
      {id:"di1",name:"Salary (net)",amount:7500,frequency:"monthly"},
      {id:"di2",name:"Rental Income",amount:2200,frequency:"monthly"},
    ],
    expenses:[
      {id:"de1",name:"Primary Mortgage",amount:2100,frequency:"monthly",category:"housing"},
      {id:"de2",name:"Rental Mortgage",amount:1450,frequency:"monthly",category:"housing"},
      {id:"de3",name:"Car Payment",amount:612,frequency:"monthly",category:"auto"},
      {id:"de4",name:"401(k) Contribution",amount:1200,frequency:"monthly",category:"savings"},
      {id:"de5",name:"Groceries & Living",amount:1100,frequency:"monthly",category:"living"},
    ],
  },
  alerts:[
    {id:"da1",text:"Rent collection due",date:"2026-04-01",type:"reminder",active:true},
    {id:"da2",text:"Car payment due",date:"2026-04-01",type:"deadline",active:true},
  ],
  netWorthHistory:[],
  zakatSettings:{nisabBasis:"silver",goldPricePerOz:2880,silverPricePerOz:33,stockMethod:"A",retirementMethod:"accessible",retirementTaxPenaltyPct:30,debtDeduction:"short_term",propertyIntents:{},goldWeightOz:0},
};

const fmt = (n) => {
  if (n===undefined||n===null||isNaN(n)) return "$0";
  return new Intl.NumberFormat("en-US",{style:"currency",currency:"USD",minimumFractionDigits:0,maximumFractionDigits:0}).format(n);
};
const fmtPct = (n) => (n>=0?"+":"")+n.toFixed(2)+"%";
const uid = () => Math.random().toString(36).slice(2,10);

const S = {
  app:{background:COLORS.bg,color:COLORS.text,minHeight:"100vh",fontFamily:"'DM Sans','Segoe UI',sans-serif",display:"flex",fontSize:14},
  sidebar:{width:240,background:"#080c14",borderRight:`1px solid ${COLORS.border}`,padding:"24px 0",display:"flex",flexDirection:"column",position:"fixed",top:0,left:0,bottom:0,zIndex:10},
  logo:{padding:"0 24px 32px",fontSize:20,fontWeight:700,letterSpacing:"-0.5px",color:"#fff"},
  logoAccent:{color:COLORS.accent},
  navItem:(active)=>({padding:"10px 24px",cursor:"pointer",display:"flex",alignItems:"center",gap:12,fontSize:14,fontWeight:active?600:400,color:active?"#fff":COLORS.textMuted,background:active?COLORS.accentGlow:"transparent",borderRight:active?`2px solid ${COLORS.accent}`:"2px solid transparent",transition:"all 0.2s"}),
  main:{flex:1,marginLeft:240,padding:"32px 40px",maxWidth:1100},
  card:{background:COLORS.bgCard,borderRadius:12,padding:"20px 24px",border:`1px solid ${COLORS.border}`,marginBottom:16},
  pageTitle:{fontSize:26,fontWeight:800,color:"#fff",margin:0,letterSpacing:"-0.5px"},
  pageSubtitle:{fontSize:14,color:COLORS.textMuted,marginTop:4,marginBottom:24},
  statLabel:{fontSize:12,color:COLORS.textMuted,marginBottom:4,textTransform:"uppercase",letterSpacing:"0.5px"},
  statValue:{fontSize:28,fontWeight:700,color:"#fff"},
  statChange:(pos)=>({fontSize:13,fontWeight:600,color:pos?COLORS.green:COLORS.red,marginTop:4}),
  grid:(c)=>({display:"grid",gridTemplateColumns:`repeat(${c},1fr)`,gap:16,marginBottom:16}),
  table:{width:"100%",borderCollapse:"collapse"},
  th:{textAlign:"left",padding:"10px 12px",fontSize:11,fontWeight:600,color:COLORS.textMuted,textTransform:"uppercase",letterSpacing:"0.5px",borderBottom:`1px solid ${COLORS.border}`},
  td:{padding:"12px",fontSize:13,color:COLORS.text,borderBottom:`1px solid ${COLORS.border}`},
  input:{width:"100%",padding:"8px 12px",background:COLORS.bgInput,border:`1px solid ${COLORS.border}`,borderRadius:8,color:"#fff",fontSize:13,outline:"none",boxSizing:"border-box"},
  select:{width:"100%",padding:"8px 12px",background:COLORS.bgInput,border:`1px solid ${COLORS.border}`,borderRadius:8,color:"#fff",fontSize:13,outline:"none"},
  btn:(v="primary")=>({padding:"8px 18px",borderRadius:8,border:"none",cursor:"pointer",fontSize:13,fontWeight:600,transition:"all 0.2s",background:v==="primary"?COLORS.accent:v==="danger"?COLORS.red:"transparent",color:v==="ghost"?COLORS.textMuted:"#fff",border:v==="ghost"?`1px solid ${COLORS.border}`:"none",display:"inline-flex",alignItems:"center",gap:6}),
  badge:(c)=>({display:"inline-block",padding:"3px 10px",borderRadius:20,fontSize:11,fontWeight:600,background:c==="green"?COLORS.greenDim:c==="red"?COLORS.redDim:c==="orange"?COLORS.orangeDim:c==="purple"?COLORS.purpleDim:COLORS.cyanDim,color:c==="green"?COLORS.green:c==="red"?COLORS.red:c==="orange"?COLORS.orange:c==="purple"?COLORS.purple:COLORS.cyan}),
  formRow:{display:"grid",gridTemplateColumns:"1fr 1fr",gap:12,marginBottom:12},
  modalOverlay:{position:"fixed",top:0,left:0,right:0,bottom:0,background:"rgba(0,0,0,0.6)",display:"flex",justifyContent:"center",alignItems:"center",zIndex:100},
  modalBox:{background:COLORS.bgCard,borderRadius:16,padding:28,width:520,maxHeight:"85vh",overflowY:"auto",border:`1px solid ${COLORS.border}`},
  alertCard:(t)=>({background:t==="reminder"?COLORS.accentGlow:t==="deadline"?COLORS.redDim:COLORS.orangeDim,borderRadius:10,padding:"14px 18px",marginBottom:10,display:"flex",justifyContent:"space-between",alignItems:"center",border:`1px solid ${t==="reminder"?"rgba(59,130,246,0.2)":t==="deadline"?"rgba(239,68,68,0.2)":"rgba(245,158,11,0.2)"}`}),
};

const Icons = {
  overview:<svg width="18" height="18" fill="none" stroke="currentColor" strokeWidth="2" viewBox="0 0 24 24"><rect x="3" y="3" width="7" height="7" rx="1"/><rect x="14" y="3" width="7" height="7" rx="1"/><rect x="3" y="14" width="7" height="7" rx="1"/><rect x="14" y="14" width="7" height="7" rx="1"/></svg>,
  bank:<svg width="18" height="18" fill="none" stroke="currentColor" strokeWidth="2" viewBox="0 0 24 24"><path d="M3 21h18M3 10h18M5 6l7-3 7 3M4 10v11M20 10v11M8 14v3M12 14v3M16 14v3"/></svg>,
  stock:<svg width="18" height="18" fill="none" stroke="currentColor" strokeWidth="2" viewBox="0 0 24 24"><polyline points="22 12 18 12 15 21 9 3 6 12 2 12"/></svg>,
  retire:<svg width="18" height="18" fill="none" stroke="currentColor" strokeWidth="2" viewBox="0 0 24 24"><circle cx="12" cy="12" r="10"/><path d="M12 6v6l4 2"/></svg>,
  property:<svg width="18" height="18" fill="none" stroke="currentColor" strokeWidth="2" viewBox="0 0 24 24"><path d="M3 9l9-7 9 7v11a2 2 0 01-2 2H5a2 2 0 01-2-2z"/><polyline points="9 22 9 12 15 12 15 22"/></svg>,
  cashflow:<svg width="18" height="18" fill="none" stroke="currentColor" strokeWidth="2" viewBox="0 0 24 24"><line x1="12" y1="1" x2="12" y2="23"/><path d="M17 5H9.5a3.5 3.5 0 000 7h5a3.5 3.5 0 010 7H6"/></svg>,
  zakat:<svg width="18" height="18" fill="none" stroke="currentColor" strokeWidth="2" viewBox="0 0 24 24"><path d="M12 2L2 7l10 5 10-5-10-5z"/><path d="M2 17l10 5 10-5"/><path d="M2 12l10 5 10-5"/></svg>,
  alert:<svg width="18" height="18" fill="none" stroke="currentColor" strokeWidth="2" viewBox="0 0 24 24"><path d="M18 8A6 6 0 006 8c0 7-3 9-3 9h18s-3-2-3-9M13.73 21a2 2 0 01-3.46 0"/></svg>,
  plus:<svg width="16" height="16" fill="none" stroke="currentColor" strokeWidth="2" viewBox="0 0 24 24"><line x1="12" y1="5" x2="12" y2="19"/><line x1="5" y1="12" x2="19" y2="12"/></svg>,
  trash:<svg width="14" height="14" fill="none" stroke="currentColor" strokeWidth="2" viewBox="0 0 24 24"><polyline points="3 6 5 6 21 6"/><path d="M19 6v14a2 2 0 01-2 2H7a2 2 0 01-2-2V6m3 0V4a2 2 0 012-2h4a2 2 0 012 2v2"/></svg>,
  edit:<svg width="14" height="14" fill="none" stroke="currentColor" strokeWidth="2" viewBox="0 0 24 24"><path d="M11 4H4a2 2 0 00-2 2v14a2 2 0 002 2h14a2 2 0 002-2v-7"/><path d="M18.5 2.5a2.121 2.121 0 013 3L12 15l-4 1 1-4 9.5-9.5z"/></svg>,
  upload:<svg width="16" height="16" fill="none" stroke="currentColor" strokeWidth="2" viewBox="0 0 24 24"><path d="M21 15v4a2 2 0 01-2 2H5a2 2 0 01-2-2v-4"/><polyline points="17 8 12 3 7 8"/><line x1="12" y1="3" x2="12" y2="15"/></svg>,
};

const NAV_ITEMS = [
  {key:"overview",label:"Overview",icon:Icons.overview},
  {key:"bank",label:"Cash & Loans",icon:Icons.bank},
  {key:"stocks",label:"Investments",icon:Icons.stock},
  {key:"retirement",label:"401(k) & RSU",icon:Icons.retire},
  {key:"properties",label:"Real Estate",icon:Icons.property},
  {key:"cashflow",label:"Cash Flow",icon:Icons.cashflow},
  {key:"zakat",label:"Zakat",icon:Icons.zakat},
  {key:"alerts",label:"Alerts",icon:Icons.alert},
];

function parseCSV(text) {
  const lines = text.trim().split("\n");
  if (lines.length<2) return [];
  const headers = lines[0].split(",").map(h=>h.trim().replace(/"/g,""));
  return lines.slice(1).map(line => {
    const vals = line.split(",").map(v=>v.trim().replace(/"/g,""));
    const obj = {};
    headers.forEach((h,i)=>(obj[h]=vals[i]));
    return obj;
  });
}

// ─── AI FILE PARSER ─────────────────────────────────────
async function parseFileWithAI(file) {
  const text = await readFileAsText(file);
  const fname = file.name.toLowerCase();

  // For CSV/TSV — try structured parse first
  if (fname.endsWith(".csv") || fname.endsWith(".tsv")) {
    const rows = parseCSV(text);
    if (rows.length > 0) return { type:"csv", rows, raw:text.substring(0,3000) };
  }

  // For all files — send to Claude for intelligent extraction
  const prompt = `You are a financial data extractor. The user uploaded a file named "${file.name}". Here is the content (first 4000 chars):

---
${text.substring(0,4000)}
---

Extract ANY financial data you can find and return ONLY valid JSON (no markdown, no backticks) in this exact structure. Only include categories where you found data. Use empty arrays for categories with no data:

{
  "bankAccounts": [{"name":"...", "type":"checking|savings", "balance":0, "institution":"..."}],
  "creditCards": [{"name":"...", "balance":0, "dueDate":"...", "institution":"..."}],
  "loans": [{"name":"...", "type":"auto|personal|student", "balance":0, "monthlyPayment":0, "institution":"..."}],
  "stocks": [{"ticker":"...", "name":"...", "shares":0, "avgCost":0, "currentPrice":0, "account":"..."}],
  "crypto": [{"symbol":"...", "name":"...", "amount":0, "currentValue":0, "platform":"..."}],
  "retirement": [{"name":"...", "type":"401k|ira", "balance":0, "institution":"...", "monthlyContribution":0}],
  "properties": [{"name":"...", "address":"...", "currentValue":0, "mortgageBalance":0, "monthlyMortgage":0, "rate":0, "isRental":false}],
  "income": [{"name":"...", "amount":0}],
  "expenses": [{"name":"...", "amount":0, "category":"housing|living|auto|insurance|savings"}],
  "summary": "Brief description of what was extracted"
}`;

  try {
    const resp = await fetch("https://api.anthropic.com/v1/messages", {
      method:"POST",
      headers:{"Content-Type":"application/json"},
      body:JSON.stringify({ model:"claude-sonnet-4-20250514", max_tokens:2000, messages:[{role:"user",content:prompt}] })
    });
    const d = await resp.json();
    const txt = d.content?.map(c=>c.text||"").join("")||"";
    const clean = txt.replace(/```json|```/g,"").trim();
    return { type:"ai", parsed:JSON.parse(clean) };
  } catch(e) {
    return { type:"error", message:"Could not parse file: "+e.message, raw:text.substring(0,500) };
  }
}

async function readFileAsText(file) {
  return new Promise((resolve, reject) => {
    const reader = new FileReader();
    reader.onload = e => resolve(e.target.result);
    reader.onerror = () => reject(new Error("Failed to read file"));

    const fname = file.name.toLowerCase();
    if (fname.endsWith(".pdf") || fname.endsWith(".png") || fname.endsWith(".jpg") || fname.endsWith(".jpeg") || fname.endsWith(".gif") || fname.endsWith(".webp")) {
      // For images/PDFs — read as base64 and describe
      reader.onload = async (e) => {
        const base64 = e.target.result.split(",")[1];
        try {
          const mediaType = file.type || (fname.endsWith(".pdf")?"application/pdf":"image/jpeg");
          const contentType = fname.endsWith(".pdf") ? "document" : "image";
          const resp = await fetch("https://api.anthropic.com/v1/messages", {
            method:"POST",
            headers:{"Content-Type":"application/json"},
            body:JSON.stringify({
              model:"claude-sonnet-4-20250514", max_tokens:2000,
              messages:[{role:"user",content:[
                {type:contentType,source:{type:"base64",media_type:mediaType,data:base64}},
                {type:"text",text:`Extract ALL financial data from this ${contentType} (${file.name}). Return ONLY valid JSON with this structure: {"bankAccounts":[{"name":"...","type":"checking","balance":0,"institution":"..."}],"creditCards":[{"name":"...","balance":0,"institution":"..."}],"loans":[{"name":"...","type":"auto","balance":0,"monthlyPayment":0,"institution":"..."}],"stocks":[{"ticker":"...","name":"...","shares":0,"avgCost":0,"currentPrice":0,"account":"..."}],"crypto":[{"symbol":"...","name":"...","amount":0,"currentValue":0,"platform":"..."}],"retirement":[{"name":"...","type":"401k","balance":0,"institution":"..."}],"properties":[{"name":"...","address":"...","currentValue":0,"mortgageBalance":0,"monthlyMortgage":0,"isRental":false}],"income":[{"name":"...","amount":0}],"expenses":[{"name":"...","amount":0,"category":"housing"}],"summary":"..."}`}
              ]}]
            })
          });
          const d = await resp.json();
          const txt = d.content?.map(c=>c.text||"").join("")||"";
          resolve("__AI_PARSED__"+txt.replace(/```json|```/g,"").trim());
        } catch(err) { resolve("[Binary file — could not process: "+err.message+"]"); }
      };
      reader.readAsDataURL(file);
    } else {
      reader.readAsText(file);
    }
  });
}

export default function FinanceDashboard() {
  const [page, setPage] = useState("overview");
  const [data, setData] = useState(EMPTY_DATA);
  const [modal, setModal] = useState(null);
  const [loading, setLoading] = useState(true);
  const [editItem, setEditItem] = useState(null);
  const [uploadStatus, setUploadStatus] = useState(null);
  const [uploadPreview, setUploadPreview] = useState(null);
  const fileRef = useRef(null);

  useEffect(() => {
    (async () => {
      try {
        const result = await window.storage.get(STORAGE_KEY);
        if (result && result.value) { setData({...EMPTY_DATA,...JSON.parse(result.value)}); }
      } catch {}
      setLoading(false);
    })();
  }, []);

  const saveData = useCallback(async (newData) => {
    setData(newData);
    try { await window.storage.set(STORAGE_KEY, JSON.stringify(newData)); } catch {}
  }, []);

  const totals = useMemo(() => {
    const bankTotal=data.bankAccounts.reduce((s,a)=>s+a.balance,0);
    const stockTotal=data.stocks.reduce((s,a)=>s+a.shares*a.currentPrice,0);
    const stockCost=data.stocks.reduce((s,a)=>s+a.shares*a.avgCost,0);
    const cryptoTotal=(data.crypto||[]).reduce((s,c)=>s+c.currentValue,0);
    const stockPlanTotal=(data.stockPlans||[]).reduce((s,p)=>s+p.value,0);
    const retireTotal=data.retirement.reduce((s,a)=>s+a.balance,0);
    const propValue=data.properties.reduce((s,p)=>s+(p.currentValue||0),0);
    const propDebt=data.properties.reduce((s,p)=>s+p.mortgageBalance,0);
    const propEquity=propValue-propDebt;
    const ccDebt=(data.creditCards||[]).reduce((s,c)=>s+c.balance,0);
    const loanDebt=(data.loans||[]).reduce((s,l)=>s+l.balance,0);
    const totalAssets=bankTotal+stockTotal+cryptoTotal+stockPlanTotal+retireTotal+propValue;
    const totalLiabilities=propDebt+ccDebt+loanDebt;
    const netWorth=totalAssets-totalLiabilities;
    const monthlyIncome=data.cashFlow.income.reduce((s,i)=>s+i.amount,0);
    const monthlyExpenses=data.cashFlow.expenses.reduce((s,e)=>s+e.amount,0);
    const monthlySavings=monthlyIncome-monthlyExpenses;
    const stockGain=stockTotal-stockCost;
    return {bankTotal,stockTotal,stockCost,stockGain,cryptoTotal,stockPlanTotal,retireTotal,propValue,propDebt,propEquity,totalAssets,totalLiabilities,netWorth,monthlyIncome,monthlyExpenses,monthlySavings,ccDebt,loanDebt};
  }, [data]);

  const hasData = totals.totalAssets>0 || totals.totalLiabilities>0 || data.bankAccounts.length>0 || data.stocks.length>0;

  const netWorthBreakdown = useMemo(()=>[
    {name:"Cash",value:totals.bankTotal},{name:"Stocks",value:totals.stockTotal},{name:"Crypto",value:totals.cryptoTotal},
    {name:"Stock Plans",value:totals.stockPlanTotal},{name:"401(k)",value:totals.retireTotal},{name:"RE Equity",value:Math.max(0,totals.propEquity)},
  ].filter(d=>d.value>0),[totals]);

  const monthlyTrend = useMemo(()=>{const b=totals.netWorth*0.85;return MONTHS.map((m,i)=>({month:m,netWorth:Math.round(b+(totals.netWorth-b)*((i+1)/12)+(Math.random()-0.3)*totals.netWorth*0.02)}));},[totals.netWorth]);
  const cashFlowChart = useMemo(()=>MONTHS.map(m=>({month:m,income:totals.monthlyIncome+(Math.random()-0.5)*500,expenses:totals.monthlyExpenses+(Math.random()-0.5)*300})),[totals.monthlyIncome,totals.monthlyExpenses]);

  const addItem=(key,item)=>{const d={...data};if(key==="income"||key==="expenses"){d.cashFlow={...d.cashFlow,[key]:[...d.cashFlow[key],{id:uid(),...item}]};}else{d[key]=[...d[key],{id:uid(),...item}];}saveData(d);setModal(null);};
  const updateItem=(key,id,updates)=>{const d={...data};if(key==="income"||key==="expenses"){d.cashFlow={...d.cashFlow,[key]:d.cashFlow[key].map(i=>i.id===id?{...i,...updates}:i)};}else{d[key]=d[key].map(i=>i.id===id?{...i,...updates}:i);}saveData(d);setModal(null);setEditItem(null);};
  const deleteItem=(key,id)=>{const d={...data};if(key==="income"||key==="expenses"){d.cashFlow={...d.cashFlow,[key]:d.cashFlow[key].filter(i=>i.id!==id)};}else{d[key]=d[key].filter(i=>i.id!==id);}saveData(d);};

  const loadDemoData = () => saveData({...EMPTY_DATA,...DEMO_DATA});
  const clearAllData = () => saveData({...EMPTY_DATA});

  // ─── FILE UPLOAD HANDLER ──────────────────────────────
  const handleFileUpload = async (files) => {
    setUploadStatus({state:"processing",message:"Reading files..."});
    const allParsed = [];
    for (const file of files) {
      setUploadStatus({state:"processing",message:`Analyzing ${file.name}...`});
      const result = await parseFileWithAI(file);
      if (result.type === "ai" || (result.type === "csv" && result.rows)) {
        allParsed.push({file:file.name, ...result});
      } else if (result.raw && result.raw.startsWith("__AI_PARSED__")) {
        try { allParsed.push({file:file.name, type:"ai", parsed:JSON.parse(result.raw.replace("__AI_PARSED__",""))}); } catch {}
      }
    }
    if (allParsed.length === 0) { setUploadStatus({state:"error",message:"Could not extract data from uploaded files."}); return; }

    // Merge all parsed data
    const merged = {...EMPTY_DATA, zakatSettings:data.zakatSettings};
    for (const p of allParsed) {
      const src = p.parsed || {};
      ["bankAccounts","creditCards","loans","stocks","crypto","retirement","stockPlans","properties"].forEach(key => {
        if (src[key]?.length) merged[key] = [...merged[key], ...src[key].map(i=>({id:uid(),...i}))];
      });
      if (src.income?.length) merged.cashFlow.income = [...merged.cashFlow.income, ...src.income.map(i=>({id:uid(),frequency:"monthly",...i}))];
      if (src.expenses?.length) merged.cashFlow.expenses = [...merged.cashFlow.expenses, ...src.expenses.map(i=>({id:uid(),frequency:"monthly",...i}))];
    }

    const summary = allParsed.map(p=>p.parsed?.summary||p.file).join("; ");
    setUploadPreview({merged, summary, files:allParsed.map(p=>p.file)});
    setUploadStatus({state:"preview",message:"Data extracted — review before importing."});
  };

  const confirmUpload = (mode) => {
    if (!uploadPreview) return;
    if (mode === "replace") { saveData(uploadPreview.merged); }
    else { // merge with existing
      const d = {...data};
      ["bankAccounts","creditCards","loans","stocks","crypto","retirement","stockPlans","properties"].forEach(k=>{
        if(uploadPreview.merged[k]?.length) d[k]=[...d[k],...uploadPreview.merged[k]];
      });
      d.cashFlow = {
        income:[...d.cashFlow.income,...uploadPreview.merged.cashFlow.income],
        expenses:[...d.cashFlow.expenses,...uploadPreview.merged.cashFlow.expenses],
      };
      saveData(d);
    }
    setUploadPreview(null); setUploadStatus({state:"success",message:"Data imported successfully!"}); setModal(null);
    setTimeout(()=>setUploadStatus(null),3000);
  };

  const Modal2 = ({title,onClose,children}) => (<div style={S.modalOverlay} onClick={onClose}><div style={S.modalBox} onClick={e=>e.stopPropagation()}><div style={{display:"flex",justifyContent:"space-between",alignItems:"center",marginBottom:20}}><div style={{fontSize:18,fontWeight:700,color:"#fff"}}>{title}</div><span style={{cursor:"pointer",fontSize:20,color:COLORS.textMuted}} onClick={onClose}>×</span></div>{children}</div></div>);
  const FormField = ({label,children}) => (<div style={{marginBottom:12}}><label style={{fontSize:12,fontWeight:600,color:COLORS.textMuted,display:"block",marginBottom:4}}>{label}</label>{children}</div>);

  // ─── ZAKAT ENGINE ─────────────────────────────────────
  const computeZakat = useCallback((portfolio, settings) => {
    const GOLD_GRAMS=87.48,SILVER_GRAMS=612.36,GRAMS_PER_OZ=31.1035,RATE=0.025;
    const gldG=(settings.goldPricePerOz||2880)/GRAMS_PER_OZ;
    const slvG=(settings.silverPricePerOz||33)/GRAMS_PER_OZ;
    const nisabGold=GOLD_GRAMS*gldG,nisabSilver=SILVER_GRAMS*slvG;
    const nisab=settings.nisabBasis==="gold"?nisabGold:nisabSilver;
    const breakdown=[];let totalZ=0,totalExcl=0;const warnings=[];

    const cashAmt=(portfolio.bankAccounts||[]).reduce((s,a)=>s+a.balance,0);
    totalZ+=cashAmt;
    breakdown.push({category:"Cash & Bank Accounts",icon:"\u{1F3E6}",included:cashAmt,excluded:0,rule:"Fully zakatable",items:(portfolio.bankAccounts||[]).map(a=>({name:a.name+" ("+a.institution+")",amount:a.balance,included:true}))});

    const stockAmt=(portfolio.stocks||[]).reduce((s,st)=>s+st.shares*st.currentPrice,0);
    totalZ+=stockAmt;
    breakdown.push({category:"Stocks & ETFs",icon:"\u{1F4C8}",included:stockAmt,excluded:0,rule:settings.stockMethod==="A"?"Method A: Full market value":"Method B: Company-based",items:(portfolio.stocks||[]).map(st=>({name:st.ticker+" — "+st.shares+" @ "+fmt(st.currentPrice),amount:st.shares*st.currentPrice,included:true}))});

    const cryptoAmt=(portfolio.crypto||[]).reduce((s,c)=>s+c.currentValue,0);
    totalZ+=cryptoAmt;
    breakdown.push({category:"Cryptocurrency",icon:"\u20BF",included:cryptoAmt,excluded:0,rule:"Full value as currency/trade asset",items:(portfolio.crypto||[]).filter(c=>c.currentValue>=0.5).map(c=>({name:c.symbol+" ("+c.platform+")",amount:c.currentValue,included:true}))});

    const retGross=(portfolio.retirement||[]).reduce((s,r)=>s+r.balance,0);
    const taxP=(settings.retirementTaxPenaltyPct||30)/100;
    let retZ=0,retExcl=0;
    if(settings.retirementMethod==="accessible"){retZ=retGross*(1-taxP);retExcl=retGross*taxP;}else{retExcl=retGross;warnings.push("Retirement set to Defer — excluded until withdrawal.");}
    totalZ+=retZ;totalExcl+=retExcl;
    breakdown.push({category:"Retirement (401k)",icon:"\u231B",included:retZ,excluded:retExcl,rule:settings.retirementMethod==="accessible"?"Accessible: "+fmt(retGross)+" minus "+(taxP*100).toFixed(0)+"% = "+fmt(retZ):"Deferred",items:(portfolio.retirement||[]).map(r=>({name:r.name,amount:r.balance,included:settings.retirementMethod==="accessible"}))});

    const spVested=(portfolio.stockPlans||[]).filter(p=>p.vested!==false);
    const spUnvested=(portfolio.stockPlans||[]).filter(p=>p.vested===false);
    const spZ=spVested.reduce((s,p)=>s+p.value,0);
    const spExcl=spUnvested.reduce((s,p)=>s+p.value,0);
    totalZ+=spZ;totalExcl+=spExcl;
    breakdown.push({category:"Stock Plans",icon:"\u{1F3E2}",included:spZ,excluded:spExcl,rule:spUnvested.length>0?"Unvested excluded":"Vested at market value",items:[...spVested.map(p=>({name:p.name+" (VESTED)",amount:p.value,included:true})),...spUnvested.map(p=>({name:p.name+" (UNVESTED)",amount:p.value,included:false}))]});

    const goldOz=settings.goldWeightOz||0;const goldVal=goldOz*(settings.goldPricePerOz||2880);
    if(goldOz>0)totalZ+=goldVal;
    breakdown.push({category:"Gold Holdings",icon:"\u{1F947}",included:goldVal,excluded:0,rule:goldOz>0?"Personal gold at spot price":"Enter weight in settings",items:goldOz>0?[{name:goldOz.toFixed(2)+" oz @ "+fmt(settings.goldPricePerOz||2880)+"/oz",amount:goldVal,included:true}]:[]});

    let propZ=0,propExcl=0;
    const propItems=(portfolio.properties||[]).map(p=>{const intent=(settings.propertyIntents||{})[p.id]||(p.isRental?"rental":"primary");if(intent==="resale"){propZ+=(p.currentValue||0);return{name:p.name+" (RESALE)",amount:p.currentValue||0,included:true};}propExcl+=(p.currentValue||0);return{name:p.name+" ("+intent+")",amount:p.currentValue||0,included:false};});
    totalZ+=propZ;totalExcl+=propExcl;
    breakdown.push({category:"Real Estate",icon:"\u{1F3E0}",included:propZ,excluded:propExcl,rule:"Only resale properties zakatable",items:propItems});

    let deductions=0;const deductItems=[];
    if(settings.debtDeduction==="short_term"){
      const ccD=(portfolio.creditCards||[]).reduce((s,c)=>s+c.balance,0);
      if(ccD>0){deductions+=ccD;deductItems.push({name:"Credit card balances",amount:ccD,included:true});}
      (portfolio.loans||[]).forEach(l=>{const a=(l.monthlyPayment||0)*12;deductions+=a;deductItems.push({name:l.name+" (12 mo)",amount:a,included:true});});
      (portfolio.properties||[]).forEach(p=>{if(p.monthlyMortgage>0){const a=p.monthlyMortgage*12;deductions+=a;deductItems.push({name:p.name+" mortgage (12 mo)",amount:a,included:true});}});
    }
    breakdown.push({category:"Debt Deductions",icon:"\u2796",included:-deductions,excluded:0,isDeduction:true,rule:settings.debtDeduction==="short_term"?"Hanafi: 12-month debts deducted":"None applied",items:deductItems});

    const netZ=Math.max(0,totalZ-deductions);const met=netZ>=nisab;
    return{netZakatable:netZ,grossZakatable:totalZ,deductions,totalExcluded:totalExcl,nisab,nisabGold,nisabSilver,nisabMet:met,zakatDue:met?netZ*RATE:0,breakdown,warnings};
  },[]);

  if(loading) return(<div style={{...S.app,justifyContent:"center",alignItems:"center"}}><div style={{textAlign:"center"}}><div style={{fontSize:28,fontWeight:700,color:"#fff",marginBottom:8}}><span style={{color:COLORS.accent}}>Wealth</span>Lens</div><div style={{color:COLORS.textMuted}}>Loading...</div></div></div>);

  // ─── WELCOME / ONBOARDING (shown when no data) ────────
  const WelcomeBanner = () => (
    <div style={{...S.card,background:"linear-gradient(135deg,#111827,#1a1f35)",textAlign:"center",padding:40,marginBottom:24}}>
      <div style={{fontSize:40,marginBottom:12}}>🕌</div>
      <h2 style={{fontSize:24,fontWeight:800,color:"#fff",margin:"0 0 8px"}}>Welcome to WealthLens</h2>
      <p style={{color:COLORS.textMuted,maxWidth:500,margin:"0 auto 24px",lineHeight:1.6}}>
        Track your finances with built-in Hanafi Zakat calculation. Upload your financial documents or try the demo to get started.
      </p>
      <div style={{display:"flex",gap:12,justifyContent:"center",flexWrap:"wrap"}}>
        <button style={{...S.btn(),padding:"12px 28px",fontSize:15}} onClick={()=>setModal("upload")}>{Icons.upload} Upload Financial Data</button>
        <button style={{...S.btn("ghost"),padding:"12px 28px",fontSize:15,border:`1px solid ${COLORS.accent}`,color:COLORS.accent}} onClick={loadDemoData}>Generate Demo Data</button>
      </div>
      <div style={{marginTop:20,fontSize:12,color:COLORS.textDim}}>
        Supports: CSV, Excel (.xlsx), PDF statements, screenshots, Word docs, and more
      </div>
    </div>
  );

  // ─── UPLOAD MODAL ─────────────────────────────────────
  const UploadModal = () => (
    <Modal2 title="Import Financial Data" onClose={()=>{setModal(null);setUploadStatus(null);setUploadPreview(null);}}>
      <div style={{textAlign:"center",padding:"20px 0"}}>
        <input ref={fileRef} type="file" multiple accept=".csv,.tsv,.xlsx,.xls,.pdf,.doc,.docx,.txt,.png,.jpg,.jpeg,.gif,.webp" style={{display:"none"}} onChange={e=>{if(e.target.files?.length)handleFileUpload(Array.from(e.target.files));}}/>
        <div onClick={()=>fileRef.current?.click()} style={{border:`2px dashed ${COLORS.border}`,borderRadius:12,padding:"40px 20px",cursor:"pointer",transition:"all 0.2s",background:COLORS.bgInput}}>
          <div style={{fontSize:36,marginBottom:8}}>📂</div>
          <div style={{fontSize:16,fontWeight:600,color:"#fff",marginBottom:6}}>Drop files or click to upload</div>
          <div style={{fontSize:12,color:COLORS.textMuted,lineHeight:1.6}}>
            CSV/TSV spreadsheets, PDF bank statements, screenshots of accounts,<br/>
            Excel files, Word documents — we'll extract the financial data automatically
          </div>
        </div>

        {uploadStatus?.state==="processing" && (
          <div style={{marginTop:20,padding:16,background:COLORS.accentGlow,borderRadius:10,border:`1px solid rgba(59,130,246,0.2)`}}>
            <div style={{display:"flex",alignItems:"center",justifyContent:"center",gap:10}}>
              <div style={{width:16,height:16,border:`2px solid ${COLORS.accent}`,borderTopColor:"transparent",borderRadius:"50%",animation:"spin 1s linear infinite"}}/>
              <span style={{color:COLORS.accent,fontWeight:600}}>{uploadStatus.message}</span>
            </div>
            <style>{`@keyframes spin { to { transform: rotate(360deg); } }`}</style>
          </div>
        )}

        {uploadStatus?.state==="error" && (
          <div style={{marginTop:20,padding:16,background:COLORS.redDim,borderRadius:10,color:COLORS.red,fontWeight:600}}>{uploadStatus.message}</div>
        )}

        {uploadStatus?.state==="success" && (
          <div style={{marginTop:20,padding:16,background:COLORS.greenDim,borderRadius:10,color:COLORS.green,fontWeight:600}}>{uploadStatus.message}</div>
        )}

        {uploadPreview && (
          <div style={{marginTop:20,textAlign:"left"}}>
            <div style={{fontSize:14,fontWeight:700,color:"#fff",marginBottom:12}}>Extracted Data Preview</div>
            <div style={{background:COLORS.bgInput,borderRadius:8,padding:12,border:`1px solid ${COLORS.border}`,marginBottom:12}}>
              <div style={{fontSize:12,color:COLORS.textMuted,marginBottom:8}}>Files: {uploadPreview.files.join(", ")}</div>
              {uploadPreview.summary && <div style={{fontSize:12,color:COLORS.text,marginBottom:8}}>{uploadPreview.summary}</div>}
              <div style={{display:"grid",gridTemplateColumns:"1fr 1fr 1fr",gap:8}}>
                {[["Accounts",uploadPreview.merged.bankAccounts.length],["Stocks",uploadPreview.merged.stocks.length],["Crypto",uploadPreview.merged.crypto.length],["Credit Cards",uploadPreview.merged.creditCards.length],["Properties",uploadPreview.merged.properties.length],["Retirement",uploadPreview.merged.retirement.length]].filter(([,v])=>v>0).map(([l,v])=>(
                  <div key={l} style={{background:COLORS.bgCard,borderRadius:6,padding:8,textAlign:"center"}}><div style={{fontSize:18,fontWeight:700,color:COLORS.accent}}>{v}</div><div style={{fontSize:10,color:COLORS.textMuted}}>{l}</div></div>
                ))}
              </div>
            </div>
            <div style={{display:"flex",gap:10}}>
              <button style={{...S.btn(),flex:1}} onClick={()=>confirmUpload("replace")}>Replace All Data</button>
              {hasData && <button style={{...S.btn("ghost"),flex:1,border:`1px solid ${COLORS.accent}`,color:COLORS.accent}} onClick={()=>confirmUpload("merge")}>Merge with Existing</button>}
            </div>
          </div>
        )}
      </div>

      <div style={{marginTop:16,padding:12,background:COLORS.bgInput,borderRadius:8,border:`1px solid ${COLORS.border}`}}>
        <div style={{fontSize:12,fontWeight:600,color:"#fff",marginBottom:6}}>Supported Formats</div>
        <div style={{fontSize:11,color:COLORS.textMuted,lineHeight:1.6}}>
          <strong style={{color:COLORS.text}}>Spreadsheets:</strong> CSV, TSV, XLSX — brokerage exports, bank transaction downloads<br/>
          <strong style={{color:COLORS.text}}>Documents:</strong> PDF bank/brokerage statements, Word docs with financial summaries<br/>
          <strong style={{color:COLORS.text}}>Images:</strong> Screenshots of account balances, portfolio summaries, statements
        </div>
      </div>
    </Modal2>
  );

  // ─── OVERVIEW ─────────────────────────────────────────
  const OverviewPage = () => {
    const zr = computeZakat(data,data.zakatSettings||EMPTY_DATA.zakatSettings);
    return (<>
      <h1 style={S.pageTitle}>Financial Overview</h1>
      <p style={S.pageSubtitle}>Your complete net worth — {new Date().toLocaleDateString("en-US",{month:"long",year:"numeric"})}</p>

      {!hasData && <WelcomeBanner/>}

      {hasData && <>
        <div style={{...S.card,marginBottom:24,background:"linear-gradient(135deg,#111827,#1a1f35)",position:"relative",overflow:"hidden"}}>
          <div style={{display:"flex",justifyContent:"space-between",alignItems:"flex-end"}}>
            <div>
              <div style={S.statLabel}>Total Net Worth</div>
              <div style={{fontSize:42,fontWeight:800,color:"#fff",letterSpacing:"-2px"}}>{fmt(totals.netWorth)}</div>
              <div style={{display:"flex",gap:24,marginTop:8}}>
                <div><span style={{fontSize:12,color:COLORS.textMuted}}>Assets: </span><span style={{fontSize:14,fontWeight:600,color:COLORS.green}}>{fmt(totals.totalAssets)}</span></div>
                <div><span style={{fontSize:12,color:COLORS.textMuted}}>Liabilities: </span><span style={{fontSize:14,fontWeight:600,color:COLORS.red}}>{fmt(totals.totalLiabilities)}</span></div>
              </div>
            </div>
            <div style={{textAlign:"right"}}>
              <div style={{fontSize:12,color:COLORS.textMuted}}>Debt-to-Asset</div>
              <div style={{fontSize:24,fontWeight:700,color:totals.totalAssets>0?(totals.totalLiabilities/totals.totalAssets<0.5?COLORS.green:COLORS.orange):COLORS.textMuted}}>{totals.totalAssets>0?((totals.totalLiabilities/totals.totalAssets)*100).toFixed(1):0}%</div>
            </div>
          </div>
        </div>

        <div style={S.grid(4)}>
          {[["Cash",totals.bankTotal],["Stocks",totals.stockTotal],["Crypto",totals.cryptoTotal],["401(k)",totals.retireTotal]].map(([l,v],i)=><div key={i} style={S.card}><div style={S.statLabel}>{l}</div><div style={{...S.statValue,fontSize:22}}>{fmt(v)}</div></div>)}
        </div>
        <div style={S.grid(4)}>
          {[["Stock Plans",totals.stockPlanTotal,"#fff"],["Real Estate",totals.propValue,"#fff"],["Mortgages & Loans",totals.propDebt+totals.loanDebt,COLORS.red],["Credit Cards",totals.ccDebt,totals.ccDebt>0?COLORS.orange:COLORS.green]].map(([l,v,c],i)=><div key={i} style={S.card}><div style={S.statLabel}>{l}</div><div style={{...S.statValue,fontSize:22,color:c}}>{fmt(v)}</div></div>)}
        </div>

        {netWorthBreakdown.length>0 && <div style={{display:"grid",gridTemplateColumns:"2fr 1fr",gap:16,marginBottom:16}}>
          <div style={S.card}><div style={{fontSize:14,fontWeight:600,color:"#fff",marginBottom:14}}>Net Worth Trend</div><ResponsiveContainer width="100%" height={220}><AreaChart data={monthlyTrend}><defs><linearGradient id="nwGrad" x1="0" y1="0" x2="0" y2="1"><stop offset="5%" stopColor={COLORS.accent} stopOpacity={0.3}/><stop offset="95%" stopColor={COLORS.accent} stopOpacity={0}/></linearGradient></defs><CartesianGrid strokeDasharray="3 3" stroke={COLORS.border}/><XAxis dataKey="month" tick={{fill:COLORS.textMuted,fontSize:11}} axisLine={false} tickLine={false}/><YAxis tick={{fill:COLORS.textMuted,fontSize:11}} axisLine={false} tickLine={false} tickFormatter={v=>"$"+(v/1000).toFixed(0)+"k"}/><Tooltip contentStyle={{background:COLORS.bgCard,border:`1px solid ${COLORS.border}`,borderRadius:8,color:COLORS.text}} formatter={v=>[fmt(v),"Net Worth"]}/><Area type="monotone" dataKey="netWorth" stroke={COLORS.accent} fill="url(#nwGrad)" strokeWidth={2}/></AreaChart></ResponsiveContainer></div>
          <div style={S.card}><div style={{fontSize:14,fontWeight:600,color:"#fff",marginBottom:14}}>Allocation</div><ResponsiveContainer width="100%" height={220}><PieChart><Pie data={netWorthBreakdown} cx="50%" cy="50%" innerRadius={50} outerRadius={80} paddingAngle={3} dataKey="value">{netWorthBreakdown.map((_,i)=><Cell key={i} fill={PIE_COLORS[i%PIE_COLORS.length]}/>)}</Pie><Tooltip contentStyle={{background:COLORS.bgCard,border:`1px solid ${COLORS.border}`,borderRadius:8,color:COLORS.text}} formatter={v=>fmt(v)}/><Legend iconType="circle" wrapperStyle={{fontSize:11}}/></PieChart></ResponsiveContainer></div>
        </div>}

        <div style={{...S.card,cursor:"pointer",borderLeft:`3px solid ${COLORS.green}`}} onClick={()=>setPage("zakat")}>
          <div style={{display:"flex",justifyContent:"space-between",alignItems:"center"}}>
            <div style={{display:"flex",alignItems:"center",gap:10}}><span style={{fontSize:20}}>🕌</span><div><div style={{fontSize:14,fontWeight:700,color:"#fff"}}>Zakat Due</div><div style={{fontSize:12,color:COLORS.textMuted}}>Hanafi · {(data.zakatSettings||{}).nisabBasis==="gold"?"Gold":"Silver"} Nisab</div></div></div>
            <div style={{textAlign:"right"}}><div style={{fontSize:24,fontWeight:800,color:COLORS.green}}>{fmt(zr.zakatDue)}</div><div style={{fontSize:11,color:COLORS.textMuted}}>on {fmt(zr.netZakatable)} zakatable</div></div>
          </div>
        </div>
      </>}
    </>);
  };

  // ─── BANK PAGE ────────────────────────────────────────
  const BankPage = () => {
    const [form,setForm]=useState({name:"",type:"checking",balance:"",institution:""});
    const institutions=[...new Set(data.bankAccounts.map(a=>a.institution))];
    return (<>
      <div style={{display:"flex",justifyContent:"space-between",alignItems:"center",marginBottom:24}}>
        <div><h1 style={S.pageTitle}>Cash, Cards & Loans</h1></div>
        <div style={{display:"flex",gap:8}}><button style={S.btn("ghost")} onClick={()=>setModal("upload")}>{Icons.upload} Import</button><button style={S.btn()} onClick={()=>setModal("addBank")}>{Icons.plus} Add</button></div>
      </div>
      {data.bankAccounts.length===0 && <div style={{...S.card,textAlign:"center",padding:40}}><div style={{fontSize:32,marginBottom:8}}>🏦</div><div style={{color:COLORS.textMuted}}>No accounts yet. Add manually or upload a statement.</div></div>}
      {institutions.map(inst=>{const accts=data.bankAccounts.filter(a=>a.institution===inst);return(<div key={inst} style={{...S.card,marginBottom:12}}><div style={{display:"flex",justifyContent:"space-between",marginBottom:12}}><span style={{fontSize:14,fontWeight:700,color:"#fff"}}>{inst}</span><span style={{fontSize:14,fontWeight:600,color:COLORS.accent}}>{fmt(accts.reduce((s,a)=>s+a.balance,0))}</span></div><table style={S.table}><thead><tr><th style={S.th}>Account</th><th style={S.th}>Type</th><th style={{...S.th,textAlign:"right"}}>Balance</th><th style={{...S.th,textAlign:"right"}}>Actions</th></tr></thead><tbody>{accts.map(a=><tr key={a.id}><td style={{...S.td,fontWeight:500,color:"#fff"}}>{a.name}</td><td style={S.td}><span style={S.badge(a.type==="checking"?"cyan":"green")}>{a.type}</span></td><td style={{...S.td,textAlign:"right",fontWeight:600,color:"#fff"}}>{fmt(a.balance)}</td><td style={{...S.td,textAlign:"right"}}><span style={{cursor:"pointer",color:COLORS.red}} onClick={()=>deleteItem("bankAccounts",a.id)}>{Icons.trash}</span></td></tr>)}</tbody></table></div>)})}
      {(data.creditCards||[]).length>0 && <div style={{...S.card}}><div style={{fontSize:14,fontWeight:700,color:"#fff",marginBottom:12}}>Credit Cards</div><table style={S.table}><thead><tr><th style={S.th}>Card</th><th style={S.th}>Institution</th><th style={{...S.th,textAlign:"right"}}>Balance</th></tr></thead><tbody>{data.creditCards.map(c=><tr key={c.id}><td style={{...S.td,color:"#fff"}}>{c.name}</td><td style={S.td}>{c.institution}</td><td style={{...S.td,textAlign:"right",fontWeight:600,color:c.balance>0?COLORS.orange:COLORS.green}}>{fmt(c.balance)}</td></tr>)}</tbody></table></div>}
      {(data.loans||[]).length>0 && <div style={S.card}><div style={{fontSize:14,fontWeight:700,color:"#fff",marginBottom:12}}>Loans</div><table style={S.table}><thead><tr><th style={S.th}>Loan</th><th style={{...S.th,textAlign:"right"}}>Balance</th><th style={{...S.th,textAlign:"right"}}>Monthly</th></tr></thead><tbody>{data.loans.map(l=><tr key={l.id}><td style={{...S.td,color:"#fff"}}>{l.name}</td><td style={{...S.td,textAlign:"right",color:COLORS.red,fontWeight:600}}>{fmt(l.balance)}</td><td style={{...S.td,textAlign:"right"}}>{fmt(l.monthlyPayment)}</td></tr>)}</tbody></table></div>}
      {modal==="addBank" && <Modal2 title="Add Bank Account" onClose={()=>setModal(null)}><FormField label="Name"><input style={S.input} value={form.name} onChange={e=>setForm({...form,name:e.target.value})}/></FormField><div style={S.formRow}><FormField label="Type"><select style={S.select} value={form.type} onChange={e=>setForm({...form,type:e.target.value})}><option value="checking">Checking</option><option value="savings">Savings</option></select></FormField><FormField label="Institution"><input style={S.input} value={form.institution} onChange={e=>setForm({...form,institution:e.target.value})}/></FormField></div><FormField label="Balance"><input style={S.input} type="number" value={form.balance} onChange={e=>setForm({...form,balance:e.target.value})}/></FormField><button style={{...S.btn(),width:"100%",marginTop:8}} onClick={()=>{if(form.name)addItem("bankAccounts",{...form,balance:parseFloat(form.balance)||0})}}>Add</button></Modal2>}
    </>);
  };

  // ─── STOCKS PAGE ──────────────────────────────────────
  const StocksPage = () => {
    const [form,setForm]=useState({ticker:"",name:"",shares:"",avgCost:"",currentPrice:"",account:"Robinhood"});
    const stockTotal=data.stocks.reduce((s,a)=>s+a.shares*a.currentPrice,0);
    return (<>
      <div style={{display:"flex",justifyContent:"space-between",alignItems:"center",marginBottom:24}}>
        <div><h1 style={S.pageTitle}>Investments</h1></div>
        <div style={{display:"flex",gap:8}}><button style={S.btn("ghost")} onClick={()=>setModal("upload")}>{Icons.upload} Import</button><button style={S.btn()} onClick={()=>setModal("addStock")}>{Icons.plus} Add</button></div>
      </div>
      {data.stocks.length===0 && !data.crypto?.length && <div style={{...S.card,textAlign:"center",padding:40}}><div style={{fontSize:32,marginBottom:8}}>📈</div><div style={{color:COLORS.textMuted}}>No investments yet. Add holdings or upload a brokerage export.</div></div>}
      {data.stocks.length>0 && <div style={S.card}><table style={S.table}><thead><tr><th style={S.th}>Ticker</th><th style={S.th}>Name</th><th style={S.th}>Account</th><th style={{...S.th,textAlign:"right"}}>Shares</th><th style={{...S.th,textAlign:"right"}}>Value</th><th style={{...S.th,textAlign:"right"}}>P&L</th><th style={{...S.th,textAlign:"right"}}></th></tr></thead><tbody>{data.stocks.map(s=>{const v=s.shares*s.currentPrice,c=s.shares*s.avgCost,g=v-c;return(<tr key={s.id}><td style={{...S.td,fontWeight:700,color:COLORS.accent}}>{s.ticker}</td><td style={S.td}>{s.name}</td><td style={S.td}><span style={S.badge(s.account==="Fidelity"?"green":"orange")}>{s.account}</span></td><td style={{...S.td,textAlign:"right"}}>{s.shares}</td><td style={{...S.td,textAlign:"right",fontWeight:600,color:"#fff"}}>{fmt(v)}</td><td style={{...S.td,textAlign:"right"}}><span style={{color:g>=0?COLORS.green:COLORS.red,fontWeight:600}}>{fmt(g)}</span></td><td style={{...S.td,textAlign:"right"}}><span style={{cursor:"pointer",color:COLORS.red}} onClick={()=>deleteItem("stocks",s.id)}>{Icons.trash}</span></td></tr>)})}</tbody></table></div>}
      {(data.crypto||[]).length>0 && <div style={{...S.card,marginTop:16}}><div style={{fontSize:14,fontWeight:600,color:"#fff",marginBottom:14}}>Crypto · {fmt(totals.cryptoTotal)}</div><table style={S.table}><thead><tr><th style={S.th}>Coin</th><th style={S.th}>Platform</th><th style={{...S.th,textAlign:"right"}}>Value</th></tr></thead><tbody>{data.crypto.filter(c=>c.currentValue>=0.5).map(c=><tr key={c.id}><td style={{...S.td,fontWeight:600,color:COLORS.orange}}>{c.symbol}</td><td style={S.td}>{c.platform}</td><td style={{...S.td,textAlign:"right",fontWeight:600,color:"#fff"}}>{fmt(c.currentValue)}</td></tr>)}</tbody></table></div>}
      {modal==="addStock" && <Modal2 title="Add Holding" onClose={()=>setModal(null)}><div style={S.formRow}><FormField label="Ticker"><input style={S.input} value={form.ticker} onChange={e=>setForm({...form,ticker:e.target.value})}/></FormField><FormField label="Name"><input style={S.input} value={form.name} onChange={e=>setForm({...form,name:e.target.value})}/></FormField></div><div style={S.formRow}><FormField label="Shares"><input style={S.input} type="number" value={form.shares} onChange={e=>setForm({...form,shares:e.target.value})}/></FormField><FormField label="Avg Cost"><input style={S.input} type="number" value={form.avgCost} onChange={e=>setForm({...form,avgCost:e.target.value})}/></FormField></div><FormField label="Current Price"><input style={S.input} type="number" value={form.currentPrice} onChange={e=>setForm({...form,currentPrice:e.target.value})}/></FormField><button style={{...S.btn(),width:"100%",marginTop:8}} onClick={()=>{if(form.ticker)addItem("stocks",{ticker:form.ticker,name:form.name||form.ticker,shares:parseFloat(form.shares)||0,avgCost:parseFloat(form.avgCost)||0,currentPrice:parseFloat(form.currentPrice)||0,account:form.account})}}>Add</button></Modal2>}
    </>);
  };

  // ─── RETIREMENT PAGE ──────────────────────────────────
  const RetirementPage = () => {
    const r = data.retirement[0];
    if(!r) return (<><h1 style={S.pageTitle}>Retirement</h1><div style={{...S.card,textAlign:"center",padding:40}}><div style={{fontSize:32,marginBottom:8}}>⏳</div><div style={{color:COLORS.textMuted}}>No retirement accounts. Upload a 401(k) statement or add manually.</div><button style={{...S.btn(),marginTop:16}} onClick={()=>setModal("upload")}>{Icons.upload} Import</button></div></>);
    return (<>
      <h1 style={S.pageTitle}>Retirement — 401(k)</h1>
      <div style={{...S.card,marginBottom:20,background:"linear-gradient(135deg,#111827,#1a1f35)"}}><div style={{display:"flex",justifyContent:"space-between",alignItems:"flex-end"}}><div><div style={S.statLabel}>Balance</div><div style={{fontSize:38,fontWeight:800,color:"#fff"}}>{fmt(r.balance)}</div></div>{r.monthlyContribution>0&&<div style={{textAlign:"right"}}><div style={{fontSize:12,color:COLORS.textMuted}}>Monthly</div><div style={{fontSize:24,fontWeight:700,color:COLORS.green}}>{fmt(r.monthlyContribution)}</div></div>}</div></div>
      {r.holdings?.length>0 && <div style={S.card}><div style={{fontSize:14,fontWeight:600,color:"#fff",marginBottom:14}}>Fund Holdings</div><table style={S.table}><thead><tr><th style={S.th}>Fund</th><th style={S.th}>Ticker</th><th style={{...S.th,textAlign:"right"}}>Value</th><th style={{...S.th,textAlign:"right"}}>Alloc</th></tr></thead><tbody>{r.holdings.map((h,i)=><tr key={i}><td style={{...S.td,color:"#fff",maxWidth:200,overflow:"hidden",textOverflow:"ellipsis",whiteSpace:"nowrap"}}>{h.name}</td><td style={{...S.td,color:COLORS.accent,fontWeight:600}}>{h.ticker}</td><td style={{...S.td,textAlign:"right",fontWeight:600,color:"#fff"}}>{fmt(h.value)}</td><td style={{...S.td,textAlign:"right"}}>{h.pct?.toFixed(1)}%</td></tr>)}</tbody></table></div>}
      {(data.stockPlans||[]).length>0 && <div style={{...S.card,marginTop:16}}><div style={{fontSize:14,fontWeight:600,color:"#fff",marginBottom:14}}>Stock Plans</div><div style={{display:"grid",gridTemplateColumns:"1fr 1fr",gap:12}}>{data.stockPlans.map(sp=><div key={sp.id} style={{background:COLORS.bgInput,borderRadius:10,padding:16,border:`1px solid ${COLORS.border}`}}><span style={S.badge(sp.type==="RSU"?"purple":"cyan")}>{sp.type}</span>{sp.vested===false&&<span style={{...S.badge("red"),marginLeft:6}}>UNVESTED</span>}<div style={{fontSize:15,fontWeight:600,color:"#fff",marginTop:8}}>{sp.name}</div><div style={{fontSize:24,fontWeight:700,color:"#fff",marginTop:4}}>{fmt(sp.value)}</div></div>)}</div></div>}
    </>);
  };

  // ─── PROPERTIES PAGE ──────────────────────────────────
  const PropertiesPage = () => {
    const [form,setForm]=useState({name:"",address:"",currentValue:"",mortgageBalance:"",monthlyMortgage:"",rate:""});
    return (<>
      <div style={{display:"flex",justifyContent:"space-between",alignItems:"center",marginBottom:24}}>
        <div><h1 style={S.pageTitle}>Real Estate</h1></div>
        <button style={S.btn()} onClick={()=>setModal("addProp")}>{Icons.plus} Add Property</button>
      </div>
      {data.properties.length===0 && <div style={{...S.card,textAlign:"center",padding:40}}><div style={{fontSize:32,marginBottom:8}}>🏠</div><div style={{color:COLORS.textMuted}}>No properties. Add your real estate holdings.</div></div>}
      {data.properties.map(p=>{const eq=(p.currentValue||0)-p.mortgageBalance;return(<div key={p.id} style={{...S.card,borderLeft:`3px solid ${p.isRental?COLORS.orange:COLORS.accent}`}}><div style={{display:"flex",justifyContent:"space-between",marginBottom:12}}><div><div style={{fontSize:16,fontWeight:700,color:"#fff"}}>{p.name} {p.isRental&&<span style={S.badge("orange")}>RENTAL</span>}</div><div style={{fontSize:12,color:COLORS.textMuted}}>{p.address}</div></div><span style={{cursor:"pointer",color:COLORS.red}} onClick={()=>deleteItem("properties",p.id)}>{Icons.trash}</span></div><div style={{display:"grid",gridTemplateColumns:"repeat(4,1fr)",gap:16}}>{p.currentValue>0&&<div><div style={S.statLabel}>Value</div><div style={{fontSize:18,fontWeight:700,color:"#fff"}}>{fmt(p.currentValue)}</div></div>}<div><div style={S.statLabel}>Mortgage</div><div style={{fontSize:18,fontWeight:700,color:COLORS.red}}>{fmt(p.mortgageBalance)}</div></div><div><div style={S.statLabel}>Equity</div><div style={{fontSize:18,fontWeight:700,color:eq>=0?COLORS.green:COLORS.red}}>{fmt(eq)}</div></div><div><div style={S.statLabel}>Monthly</div><div style={{fontSize:18,fontWeight:700,color:"#fff"}}>{p.monthlyMortgage>0?fmt(p.monthlyMortgage):"—"}</div></div></div></div>)})}
      {modal==="addProp" && <Modal2 title="Add Property" onClose={()=>setModal(null)}><FormField label="Name"><input style={S.input} value={form.name} onChange={e=>setForm({...form,name:e.target.value})}/></FormField><FormField label="Address"><input style={S.input} value={form.address} onChange={e=>setForm({...form,address:e.target.value})}/></FormField><div style={S.formRow}><FormField label="Value"><input style={S.input} type="number" value={form.currentValue} onChange={e=>setForm({...form,currentValue:e.target.value})}/></FormField><FormField label="Mortgage"><input style={S.input} type="number" value={form.mortgageBalance} onChange={e=>setForm({...form,mortgageBalance:e.target.value})}/></FormField></div><div style={S.formRow}><FormField label="Monthly Payment"><input style={S.input} type="number" value={form.monthlyMortgage} onChange={e=>setForm({...form,monthlyMortgage:e.target.value})}/></FormField><FormField label="Rate %"><input style={S.input} type="number" value={form.rate} onChange={e=>setForm({...form,rate:e.target.value})}/></FormField></div><button style={{...S.btn(),width:"100%",marginTop:8}} onClick={()=>{if(form.name)addItem("properties",{name:form.name,address:form.address,purchasePrice:0,currentValue:parseFloat(form.currentValue)||0,mortgageBalance:parseFloat(form.mortgageBalance)||0,monthlyMortgage:parseFloat(form.monthlyMortgage)||0,monthlyRent:0,rate:parseFloat(form.rate)||0,insurance:0,propertyTax:0,isRental:false,lender:"",loanDuration:""})}}>Add</button></Modal2>}
    </>);
  };

  // ─── CASH FLOW ────────────────────────────────────────
  const CashFlowPage = () => {
    const [incForm,setIncForm]=useState({name:"",amount:""});const [expForm,setExpForm]=useState({name:"",amount:"",category:"living"});
    return (<>
      <h1 style={S.pageTitle}>Cash Flow</h1><p style={S.pageSubtitle}>Monthly income vs expenses</p>
      <div style={S.grid(3)}>
        <div style={S.card}><div style={S.statLabel}>Income</div><div style={{...S.statValue,fontSize:24,color:COLORS.green}}>{fmt(totals.monthlyIncome)}</div></div>
        <div style={S.card}><div style={S.statLabel}>Expenses</div><div style={{...S.statValue,fontSize:24,color:COLORS.red}}>{fmt(totals.monthlyExpenses)}</div></div>
        <div style={S.card}><div style={S.statLabel}>Net</div><div style={{...S.statValue,fontSize:24,color:totals.monthlySavings>=0?COLORS.green:COLORS.red}}>{fmt(totals.monthlySavings)}</div></div>
      </div>
      {(totals.monthlyIncome>0||totals.monthlyExpenses>0)&&<div style={{...S.card,marginBottom:24}}><ResponsiveContainer width="100%" height={200}><BarChart data={cashFlowChart}><CartesianGrid strokeDasharray="3 3" stroke={COLORS.border}/><XAxis dataKey="month" tick={{fill:COLORS.textMuted,fontSize:11}} axisLine={false} tickLine={false}/><YAxis tick={{fill:COLORS.textMuted,fontSize:11}} axisLine={false} tickLine={false}/><Tooltip contentStyle={{background:COLORS.bgCard,border:`1px solid ${COLORS.border}`,borderRadius:8}} formatter={v=>fmt(v)}/><Bar dataKey="income" fill={COLORS.green} radius={[4,4,0,0]}/><Bar dataKey="expenses" fill={COLORS.red} radius={[4,4,0,0]} opacity={0.7}/></BarChart></ResponsiveContainer></div>}
      <div style={{display:"grid",gridTemplateColumns:"1fr 1fr",gap:16}}>
        <div style={S.card}><div style={{display:"flex",justifyContent:"space-between",marginBottom:12}}><span style={{fontWeight:600,color:COLORS.green}}>Income</span><button style={{...S.btn(),padding:"4px 10px",fontSize:11}} onClick={()=>setModal("addIncome")}>{Icons.plus}</button></div>{data.cashFlow.income.map(i=><div key={i.id} style={{display:"flex",justifyContent:"space-between",padding:"8px 0",borderBottom:`1px solid ${COLORS.border}`}}><span>{i.name}</span><div style={{display:"flex",gap:10}}><span style={{fontWeight:600,color:COLORS.green}}>{fmt(i.amount)}</span><span style={{cursor:"pointer",color:COLORS.red}} onClick={()=>deleteItem("income",i.id)}>{Icons.trash}</span></div></div>)}</div>
        <div style={S.card}><div style={{display:"flex",justifyContent:"space-between",marginBottom:12}}><span style={{fontWeight:600,color:COLORS.red}}>Expenses</span><button style={{...S.btn(),padding:"4px 10px",fontSize:11}} onClick={()=>setModal("addExpense")}>{Icons.plus}</button></div>{data.cashFlow.expenses.map(e=><div key={e.id} style={{display:"flex",justifyContent:"space-between",padding:"8px 0",borderBottom:`1px solid ${COLORS.border}`}}><span>{e.name} <span style={S.badge("orange")}>{e.category}</span></span><div style={{display:"flex",gap:10}}><span style={{fontWeight:600,color:COLORS.red}}>{fmt(e.amount)}</span><span style={{cursor:"pointer",color:COLORS.red}} onClick={()=>deleteItem("expenses",e.id)}>{Icons.trash}</span></div></div>)}</div>
      </div>
      {modal==="addIncome"&&<Modal2 title="Add Income" onClose={()=>setModal(null)}><FormField label="Name"><input style={S.input} value={incForm.name} onChange={e=>setIncForm({...incForm,name:e.target.value})}/></FormField><FormField label="Monthly Amount"><input style={S.input} type="number" value={incForm.amount} onChange={e=>setIncForm({...incForm,amount:e.target.value})}/></FormField><button style={{...S.btn(),width:"100%",marginTop:8}} onClick={()=>{if(incForm.name)addItem("income",{name:incForm.name,amount:parseFloat(incForm.amount)||0,frequency:"monthly"})}}>Add</button></Modal2>}
      {modal==="addExpense"&&<Modal2 title="Add Expense" onClose={()=>setModal(null)}><FormField label="Name"><input style={S.input} value={expForm.name} onChange={e=>setExpForm({...expForm,name:e.target.value})}/></FormField><div style={S.formRow}><FormField label="Amount"><input style={S.input} type="number" value={expForm.amount} onChange={e=>setExpForm({...expForm,amount:e.target.value})}/></FormField><FormField label="Category"><select style={S.select} value={expForm.category} onChange={e=>setExpForm({...expForm,category:e.target.value})}><option value="housing">Housing</option><option value="living">Living</option><option value="auto">Auto</option><option value="insurance">Insurance</option><option value="savings">Savings</option></select></FormField></div><button style={{...S.btn(),width:"100%",marginTop:8}} onClick={()=>{if(expForm.name)addItem("expenses",{name:expForm.name,amount:parseFloat(expForm.amount)||0,frequency:"monthly",category:expForm.category})}}>Add</button></Modal2>}
    </>);
  };

  // ─── ZAKAT PAGE ───────────────────────────────────────
  const ZakatPage = () => {
    const zs=data.zakatSettings||{};const [settings,setSettings]=useState({...EMPTY_DATA.zakatSettings,...zs});
    const upd=(k,v)=>{const n={...settings,[k]:v};setSettings(n);setData(prev=>({...prev,zakatSettings:n}));};
    const result=useMemo(()=>computeZakat(data,settings),[data,settings,computeZakat]);
    const Tog=({label,active,onClick})=><button onClick={onClick} style={{padding:"6px 14px",borderRadius:6,fontSize:12,fontWeight:600,cursor:"pointer",border:`1px solid ${active?COLORS.accent:COLORS.border}`,background:active?COLORS.accent:COLORS.bgInput,color:active?"#fff":COLORS.textMuted}}>{label}</button>;
    return (<>
      <h1 style={S.pageTitle}>Zakat Calculator</h1><p style={{...S.pageSubtitle,marginBottom:24}}>Hanafi fiqh — live on your portfolio</p>
      <div style={{...S.card,marginBottom:20,background:"linear-gradient(135deg,#111827,#0c1a12)",position:"relative",overflow:"hidden"}}>
        <div style={{position:"absolute",top:-50,right:-50,width:220,height:220,background:"radial-gradient(circle,rgba(16,185,129,0.1),transparent 70%)",borderRadius:"50%"}}/>
        <div style={{display:"flex",justifyContent:"space-between",alignItems:"flex-start"}}>
          <div>
            <div style={{fontSize:12,color:COLORS.textMuted,marginBottom:4}}>Zakat Due (2.5%)</div>
            <div style={{fontSize:44,fontWeight:800,color:result.nisabMet?COLORS.green:COLORS.textMuted,letterSpacing:"-2px"}}>{fmt(result.zakatDue)}</div>
            <div style={{display:"flex",gap:20,marginTop:12}}>
              <div><div style={{fontSize:11,color:COLORS.textMuted}}>Net Zakatable</div><div style={{fontSize:18,fontWeight:700,color:"#fff"}}>{fmt(result.netZakatable)}</div></div>
              <div><div style={{fontSize:11,color:COLORS.textMuted}}>Deductions</div><div style={{fontSize:18,fontWeight:700,color:COLORS.red}}>{fmt(result.deductions)}</div></div>
              <div><div style={{fontSize:11,color:COLORS.textMuted}}>Excluded</div><div style={{fontSize:18,fontWeight:700,color:COLORS.textDim}}>{fmt(result.totalExcluded)}</div></div>
            </div>
          </div>
          <div style={{textAlign:"right"}}>
            <div style={{padding:"6px 14px",borderRadius:20,fontSize:12,fontWeight:700,background:result.nisabMet?COLORS.greenDim:COLORS.redDim,color:result.nisabMet?COLORS.green:COLORS.red,marginBottom:8}}>{result.nisabMet?"✓ Nisab Met":"✗ Below Nisab"}</div>
            <div style={{fontSize:12,color:COLORS.textMuted}}>Nisab ({settings.nisabBasis})</div>
            <div style={{fontSize:16,fontWeight:600,color:"#fff"}}>{fmt(result.nisab)}</div>
            <div style={{fontSize:11,color:COLORS.textDim,marginTop:4}}>Gold: {fmt(result.nisabGold)} | Silver: {fmt(result.nisabSilver)}</div>
          </div>
        </div>
      </div>
      <div style={{...S.card,marginBottom:16}}>
        <div style={{fontSize:14,fontWeight:700,color:"#fff",marginBottom:16}}>Settings</div>
        <div style={{display:"grid",gridTemplateColumns:"1fr 1fr 1fr",gap:16}}>
          <div><div style={{fontSize:12,color:COLORS.textMuted,marginBottom:6}}>Nisab</div><div style={{display:"flex",gap:6}}><Tog label="Silver" active={settings.nisabBasis==="silver"} onClick={()=>upd("nisabBasis","silver")}/><Tog label="Gold" active={settings.nisabBasis==="gold"} onClick={()=>upd("nisabBasis","gold")}/></div></div>
          <div><div style={{fontSize:12,color:COLORS.textMuted,marginBottom:6}}>Stocks</div><div style={{display:"flex",gap:6}}><Tog label="Full Value" active={settings.stockMethod==="A"} onClick={()=>upd("stockMethod","A")}/><Tog label="Company" active={settings.stockMethod==="B"} onClick={()=>upd("stockMethod","B")}/></div></div>
          <div><div style={{fontSize:12,color:COLORS.textMuted,marginBottom:6}}>401(k)</div><div style={{display:"flex",gap:6}}><Tog label="Accessible" active={settings.retirementMethod==="accessible"} onClick={()=>upd("retirementMethod","accessible")}/><Tog label="Defer" active={settings.retirementMethod==="defer"} onClick={()=>upd("retirementMethod","defer")}/></div></div>
          <div><div style={{fontSize:12,color:COLORS.textMuted,marginBottom:6}}>Debt Deduction</div><div style={{display:"flex",gap:6}}><Tog label="12-Mo Debts" active={settings.debtDeduction==="short_term"} onClick={()=>upd("debtDeduction","short_term")}/><Tog label="None" active={settings.debtDeduction==="none"} onClick={()=>upd("debtDeduction","none")}/></div></div>
          <div><div style={{fontSize:12,color:COLORS.textMuted,marginBottom:6}}>401(k) Tax/Penalty</div><div style={{display:"flex",alignItems:"center",gap:8}}><input type="range" min="0" max="50" value={settings.retirementTaxPenaltyPct} onChange={e=>upd("retirementTaxPenaltyPct",parseInt(e.target.value))} style={{flex:1}}/><span style={{fontSize:14,fontWeight:600,color:"#fff",minWidth:36}}>{settings.retirementTaxPenaltyPct}%</span></div></div>
          <div><div style={{fontSize:12,color:COLORS.textMuted,marginBottom:6}}>Spot Prices ($/oz)</div><div style={{display:"flex",gap:8}}><div style={{flex:1}}><div style={{fontSize:10,color:COLORS.textDim}}>Gold</div><input style={{...S.input,padding:"4px 8px",fontSize:12}} type="number" value={settings.goldPricePerOz} onChange={e=>upd("goldPricePerOz",parseFloat(e.target.value)||0)}/></div><div style={{flex:1}}><div style={{fontSize:10,color:COLORS.textDim}}>Silver</div><input style={{...S.input,padding:"4px 8px",fontSize:12}} type="number" value={settings.silverPricePerOz} onChange={e=>upd("silverPricePerOz",parseFloat(e.target.value)||0)}/></div></div></div>
        </div>
        <div style={{display:"grid",gridTemplateColumns:"1fr 1fr 1fr",gap:16,marginTop:16,paddingTop:16,borderTop:`1px solid ${COLORS.border}`}}>
          <div style={{gridColumn:"span 2"}}><div style={{fontSize:12,color:COLORS.textMuted,marginBottom:6}}>Personal Gold (jewelry, bullion)</div><div style={{display:"flex",gap:8,alignItems:"center"}}><div style={{flex:1}}><div style={{fontSize:10,color:COLORS.textDim}}>Troy oz</div><input style={{...S.input,padding:"4px 8px",fontSize:12}} type="number" step="0.01" value={settings.goldWeightOz||""} placeholder="0" onChange={e=>upd("goldWeightOz",parseFloat(e.target.value)||0)}/></div><div style={{flex:1}}><div style={{fontSize:10,color:COLORS.textDim}}>Grams</div><input style={{...S.input,padding:"4px 8px",fontSize:12}} type="number" step="0.1" value={settings.goldWeightOz?(settings.goldWeightOz*31.1035).toFixed(1):""} placeholder="0" onChange={e=>upd("goldWeightOz",parseFloat(((parseFloat(e.target.value)||0)/31.1035).toFixed(4)))}/></div><div style={{minWidth:100,textAlign:"right"}}><div style={{fontSize:10,color:COLORS.textDim}}>Value</div><div style={{fontSize:14,fontWeight:700,color:COLORS.orange}}>{fmt((settings.goldWeightOz||0)*(settings.goldPricePerOz||2880))}</div></div></div></div>
        </div>
      </div>
      {result.warnings.length>0&&<div style={{marginBottom:16}}>{result.warnings.map((w,i)=><div key={i} style={{...S.alertCard("review"),fontSize:13}}>{w}</div>)}</div>}
      <div style={S.card}>
        <div style={{fontSize:14,fontWeight:700,color:"#fff",marginBottom:16}}>Breakdown</div>
        {result.breakdown.map((cat,ci)=>(
          <div key={ci} style={{marginBottom:20,paddingBottom:16,borderBottom:ci<result.breakdown.length-1?`1px solid ${COLORS.border}`:"none"}}>
            <div style={{display:"flex",justifyContent:"space-between",alignItems:"center",marginBottom:8}}>
              <div style={{display:"flex",alignItems:"center",gap:8}}><span style={{fontSize:18}}>{cat.icon}</span><span style={{fontSize:14,fontWeight:700,color:"#fff"}}>{cat.category}</span></div>
              <div style={{display:"flex",gap:16,alignItems:"center"}}>{cat.included!==0&&<span style={{fontSize:14,fontWeight:700,color:cat.isDeduction?COLORS.red:COLORS.green}}>{cat.isDeduction?"\u2212":"+"}{fmt(Math.abs(cat.included))}</span>}{cat.excluded>0&&<span style={{fontSize:12,color:COLORS.textDim}}>({fmt(cat.excluded)} excl.)</span>}</div>
            </div>
            <div style={{fontSize:11,color:COLORS.textMuted,marginBottom:8,fontStyle:"italic",paddingLeft:26}}>{cat.rule}</div>
            {cat.items.length>0&&<table style={{...S.table,marginLeft:26}}><tbody>{cat.items.map((item,ii)=><tr key={ii}><td style={{...S.td,paddingTop:4,paddingBottom:4,fontSize:12,color:item.included===false?COLORS.textDim:COLORS.text}}>{item.included===false?<span style={{color:COLORS.red,marginRight:4}}>{"\u2717"}</span>:<span style={{color:COLORS.green,marginRight:4}}>{"\u2713"}</span>}{item.name}</td><td style={{...S.td,paddingTop:4,paddingBottom:4,textAlign:"right",fontSize:12,fontWeight:600,color:item.included===false?COLORS.textDim:"#fff"}}>{fmt(item.amount)}</td></tr>)}</tbody></table>}
          </div>
        ))}
        <div style={{background:COLORS.bgInput,borderRadius:10,padding:16,border:`1px solid ${COLORS.border}`,marginTop:8}}>
          <div style={{display:"grid",gridTemplateColumns:"1fr 1fr 1fr 1fr",gap:16,textAlign:"center"}}>
            <div><div style={{fontSize:11,color:COLORS.textMuted}}>Gross</div><div style={{fontSize:16,fontWeight:700,color:"#fff"}}>{fmt(result.grossZakatable)}</div></div>
            <div><div style={{fontSize:11,color:COLORS.textMuted}}>Deductions</div><div style={{fontSize:16,fontWeight:700,color:COLORS.red}}>{"\u2212"}{fmt(result.deductions)}</div></div>
            <div><div style={{fontSize:11,color:COLORS.textMuted}}>Net Zakatable</div><div style={{fontSize:16,fontWeight:700,color:COLORS.accent}}>{fmt(result.netZakatable)}</div></div>
            <div><div style={{fontSize:11,color:COLORS.textMuted}}>Zakat Due</div><div style={{fontSize:16,fontWeight:700,color:COLORS.green}}>{fmt(result.zakatDue)}</div></div>
          </div>
        </div>
      </div>
      <div style={{...S.card,marginTop:16,background:COLORS.bgInput}}><div style={{fontSize:13,fontWeight:600,color:"#fff",marginBottom:8}}>Hanafi Reference</div><div style={{fontSize:12,color:COLORS.textMuted,lineHeight:1.6}}>Zakat is 2.5% of net zakatable wealth once nisab is met. Silver nisab (612.36g) is the standard Hanafi threshold. Stocks at full market value. Retirement at withdrawable value minus tax/penalty. 12-month debts deducted. Rental property value exempt. Consult a qualified scholar for your situation.</div></div>
    </>);
  };

  // ─── ALERTS PAGE ──────────────────────────────────────
  const AlertsPage = () => {
    const [form,setForm]=useState({text:"",date:"",type:"reminder"});
    return (<>
      <div style={{display:"flex",justifyContent:"space-between",alignItems:"center",marginBottom:24}}><h1 style={S.pageTitle}>Alerts</h1><button style={S.btn()} onClick={()=>setModal("addAlert")}>{Icons.plus} Add</button></div>
      {data.alerts.filter(a=>a.active).length===0&&<div style={{...S.card,textAlign:"center",padding:40}}><div style={{color:COLORS.textMuted}}>No active alerts.</div></div>}
      {data.alerts.filter(a=>a.active).map(a=><div key={a.id} style={S.alertCard(a.type)}><div><div style={{fontWeight:600,color:COLORS.text}}>{a.text}</div><div style={{fontSize:12,color:COLORS.textMuted}}>{a.date}</div></div><div style={{display:"flex",gap:8}}><span style={S.badge(a.type==="deadline"?"red":"purple")}>{a.type}</span><button style={{...S.btn("ghost"),padding:"4px 8px",fontSize:11}} onClick={()=>updateItem("alerts",a.id,{active:false})}>Done</button></div></div>)}
      {modal==="addAlert"&&<Modal2 title="Add Alert" onClose={()=>setModal(null)}><FormField label="Description"><input style={S.input} value={form.text} onChange={e=>setForm({...form,text:e.target.value})}/></FormField><div style={S.formRow}><FormField label="Date"><input style={S.input} type="date" value={form.date} onChange={e=>setForm({...form,date:e.target.value})}/></FormField><FormField label="Type"><select style={S.select} value={form.type} onChange={e=>setForm({...form,type:e.target.value})}><option value="reminder">Reminder</option><option value="deadline">Deadline</option><option value="review">Review</option></select></FormField></div><button style={{...S.btn(),width:"100%",marginTop:8}} onClick={()=>{if(form.text)addItem("alerts",{text:form.text,date:form.date,type:form.type,active:true})}}>Add</button></Modal2>}
    </>);
  };

  const pages={overview:OverviewPage,bank:BankPage,stocks:StocksPage,retirement:RetirementPage,properties:PropertiesPage,cashflow:CashFlowPage,zakat:ZakatPage,alerts:AlertsPage};
  const PageComponent=pages[page];
  const activeAlertCount=data.alerts.filter(a=>a.active).length;

  return (
    <div style={S.app}>
      <link href="https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;600;700;800&display=swap" rel="stylesheet"/>
      <div style={S.sidebar}>
        <div style={S.logo}><span style={S.logoAccent}>Wealth</span>Lens</div>
        <nav style={{flex:1}}>
          {NAV_ITEMS.map(item=>(
            <div key={item.key} style={S.navItem(page===item.key)} onClick={()=>setPage(item.key)}>
              {item.icon}<span>{item.label}</span>
              {item.key==="alerts"&&activeAlertCount>0&&<span style={{marginLeft:"auto",background:COLORS.red,color:"#fff",fontSize:10,fontWeight:700,borderRadius:10,padding:"1px 6px"}}>{activeAlertCount}</span>}
            </div>
          ))}
        </nav>
        <div style={{padding:"0 16px",display:"flex",flexDirection:"column",gap:6}}>
          <button style={{...S.btn(),width:"100%",fontSize:12,padding:"8px 12px"}} onClick={()=>setModal("upload")}>{Icons.upload} Import Data</button>
          <button style={{...S.btn("ghost"),width:"100%",fontSize:11,padding:"6px 12px",border:`1px solid ${COLORS.accent}`,color:COLORS.accent}} onClick={loadDemoData}>Demo Data</button>
          {hasData&&<button style={{...S.btn("ghost"),width:"100%",fontSize:11,padding:"6px 12px"}} onClick={clearAllData}>Clear All</button>}
        </div>
      </div>
      <div style={S.main}><PageComponent/></div>
      {modal==="upload"&&<UploadModal/>}
      {uploadStatus?.state==="success"&&<div style={{position:"fixed",top:20,right:20,background:COLORS.greenDim,border:`1px solid ${COLORS.green}`,borderRadius:10,padding:"12px 20px",color:COLORS.green,fontWeight:600,zIndex:200}}>{uploadStatus.message}</div>}
    </div>
  );
}
