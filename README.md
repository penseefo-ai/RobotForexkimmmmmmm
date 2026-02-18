<!DOCTYPE html>
<html lang="th">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>FX Robot Hub — EA & Robot Forex Library</title>
<link href="https://fonts.googleapis.com/css2?family=Rajdhani:wght@400;500;600;700&family=Sarabun:wght@300;400;500&family=Share+Tech+Mono&display=swap" rel="stylesheet">
<style>
:root {
  --bg:#f5f7fa; --bg2:#ffffff; --bg3:#eef1f6;
  --card:#ffffff; --card-hover:#f0f5ff;
  --border:#dde3ef; --border-glow:#6b9fff;
  --accent:#3b82f6; --accent2:#10b981;
  --text:#1e293b; --text-muted:#94a3b8; --text-dim:#475569;
  --gold:#d97706; --red:#ef4444; --green:#10b981;
}
*{margin:0;padding:0;box-sizing:border-box}
body{background:var(--bg);color:var(--text);font-family:'Sarabun',sans-serif;min-height:100vh;overflow-x:hidden}
body::before{content:'';position:fixed;inset:0;background-image:radial-gradient(circle,#c7d4e8 1px,transparent 1px);background-size:28px 28px;pointer-events:none;z-index:0;opacity:0.4}

/* HEADER */
header{position:sticky;top:0;z-index:100;background:rgba(255,255,255,0.93);backdrop-filter:blur(20px);border-bottom:1px solid var(--border);padding:0 2rem;box-shadow:0 1px 8px rgba(0,0,0,0.06)}
.header-inner{max-width:1400px;margin:0 auto;display:flex;align-items:center;justify-content:space-between;height:64px;gap:1.5rem}
.logo{display:flex;align-items:center;gap:0.6rem;text-decoration:none}
.logo-icon{width:36px;height:36px;background:linear-gradient(135deg,#3b82f6,#6366f1);border-radius:8px;display:flex;align-items:center;justify-content:center;font-family:'Share Tech Mono',monospace;font-size:14px;font-weight:bold;color:#fff;box-shadow:0 2px 12px rgba(59,130,246,0.35)}
.logo-text{font-family:'Rajdhani',sans-serif;font-size:1.4rem;font-weight:700;color:var(--text);letter-spacing:1px}
.logo-text span{color:var(--accent)}
nav{display:flex;align-items:center;gap:0.25rem}
nav a{color:var(--text-muted);text-decoration:none;font-size:0.9rem;padding:0.4rem 0.9rem;border-radius:6px;transition:all 0.2s;font-family:'Rajdhani',sans-serif;font-weight:600;letter-spacing:0.5px}
nav a:hover,nav a.active{color:var(--accent);background:rgba(59,130,246,0.08)}
.btn-upload{background:linear-gradient(135deg,#3b82f6,#6366f1);color:#fff;border:none;padding:0.45rem 1.1rem;border-radius:8px;font-family:'Rajdhani',sans-serif;font-size:0.9rem;font-weight:700;cursor:pointer;letter-spacing:0.5px;transition:all 0.2s;display:flex;align-items:center;gap:0.4rem;box-shadow:0 2px 12px rgba(59,130,246,0.35)}
.btn-upload:hover{transform:translateY(-1px);box-shadow:0 4px 20px rgba(59,130,246,0.45)}

/* HERO */
.hero{position:relative;z-index:1;padding:4rem 2rem 3rem;text-align:center;overflow:hidden}
.hero::before{content:'';position:absolute;top:-100px;left:50%;transform:translateX(-50%);width:600px;height:300px;background:radial-gradient(ellipse,rgba(59,130,246,0.08) 0%,transparent 70%);pointer-events:none}
.hero-badge{display:inline-flex;align-items:center;gap:0.5rem;background:rgba(59,130,246,0.08);border:1px solid rgba(59,130,246,0.2);border-radius:20px;padding:0.3rem 0.9rem;font-size:0.8rem;color:var(--accent);font-family:'Share Tech Mono',monospace;margin-bottom:1.25rem;animation:fadeIn 0.6s ease}
.hero-badge::before{content:'';width:6px;height:6px;background:var(--accent2);border-radius:50%;box-shadow:0 0 8px var(--accent2);animation:blink 1.5s infinite}
@keyframes blink{0%,100%{opacity:1}50%{opacity:0.3}}
@keyframes fadeIn{from{opacity:0;transform:translateY(12px)}to{opacity:1;transform:translateY(0)}}
.hero h1{font-family:'Rajdhani',sans-serif;font-size:clamp(2rem,5vw,3.5rem);font-weight:700;line-height:1.1;margin-bottom:1rem;animation:fadeIn 0.7s ease 0.1s both}
.hero h1 .hl{background:linear-gradient(90deg,#3b82f6,#6366f1);-webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text}
.hero p{color:var(--text-dim);font-size:1.05rem;max-width:560px;margin:0 auto 2rem;line-height:1.7;animation:fadeIn 0.7s ease 0.2s both}
.stats-row{display:flex;justify-content:center;gap:2.5rem;animation:fadeIn 0.7s ease 0.3s both}
.stat{text-align:center}
.stat-num{font-family:'Share Tech Mono',monospace;font-size:1.5rem;color:var(--accent);display:block}
.stat-label{font-size:0.8rem;color:var(--text-muted);margin-top:0.2rem}

/* TOOLBAR */
.toolbar{position:relative;z-index:1;max-width:1400px;margin:0 auto;padding:0 2rem 2rem;display:flex;align-items:center;gap:1rem;flex-wrap:wrap}
.search-box{flex:1;min-width:200px;position:relative}
.search-box input{width:100%;background:var(--card);border:1px solid var(--border);color:var(--text);padding:0.65rem 1rem 0.65rem 2.5rem;border-radius:10px;font-size:0.9rem;font-family:'Sarabun',sans-serif;outline:none;transition:border-color 0.2s,box-shadow 0.2s}
.search-box input:focus{border-color:var(--accent);box-shadow:0 0 0 3px rgba(59,130,246,0.12)}
.search-box input::placeholder{color:var(--text-muted)}
.search-icon{position:absolute;left:0.8rem;top:50%;transform:translateY(-50%);color:var(--text-muted);font-size:0.9rem}
.filter-tabs{display:flex;gap:0.4rem;flex-wrap:wrap}
.filter-tab{background:var(--card);border:1px solid var(--border);color:var(--text-muted);padding:0.5rem 1rem;border-radius:8px;font-family:'Rajdhani',sans-serif;font-weight:600;font-size:0.85rem;cursor:pointer;transition:all 0.2s;letter-spacing:0.5px}
.filter-tab:hover{color:var(--text);border-color:var(--border-glow)}
.filter-tab.active{background:rgba(59,130,246,0.1);border-color:var(--accent);color:var(--accent)}
.sort-select{background:var(--card);border:1px solid var(--border);color:var(--text);padding:0.6rem 1rem;border-radius:8px;font-size:0.85rem;font-family:'Sarabun',sans-serif;cursor:pointer;outline:none}

/* GRID */
.grid-section{position:relative;z-index:1;max-width:1400px;margin:0 auto;padding:0 2rem 4rem}
.section-header{display:flex;align-items:center;gap:1rem;margin-bottom:1.5rem}
.section-title{font-family:'Rajdhani',sans-serif;font-size:1.1rem;font-weight:700;color:var(--text-dim);letter-spacing:1px;text-transform:uppercase}
.section-line{flex:1;height:1px;background:linear-gradient(90deg,var(--border),transparent)}
.count-badge{font-family:'Share Tech Mono',monospace;font-size:0.8rem;color:var(--text-muted);background:var(--bg3);border:1px solid var(--border);padding:0.2rem 0.6rem;border-radius:20px}
.ea-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(280px,1fr));gap:1.25rem}

/* EA CARD */
.ea-card{background:var(--card);border:1px solid var(--border);border-radius:14px;overflow:hidden;cursor:pointer;box-shadow:0 1px 4px rgba(0,0,0,0.06),0 2px 12px rgba(0,0,0,0.04);transition:all 0.25s;animation:cardIn 0.5s ease both;position:relative}
@keyframes cardIn{from{opacity:0;transform:translateY(16px)}to{opacity:1;transform:translateY(0)}}
.ea-card:hover{border-color:var(--border-glow);background:var(--card-hover);transform:translateY(-3px);box-shadow:0 6px 28px rgba(0,0,0,0.09),0 0 0 1px rgba(59,130,246,0.1)}
.card-badge{position:absolute;top:0.65rem;left:0.65rem;z-index:2;font-family:'Share Tech Mono',monospace;font-size:0.65rem;padding:0.2rem 0.5rem;border-radius:5px;font-weight:bold;letter-spacing:0.5px}
.badge-free{background:rgba(16,185,129,0.12);color:#059669;border:1px solid rgba(16,185,129,0.3)}
.badge-premium{background:rgba(217,119,6,0.1);color:#b45309;border:1px solid rgba(217,119,6,0.3)}
.badge-new{background:rgba(59,130,246,0.1);color:var(--accent);border:1px solid rgba(59,130,246,0.3)}
.badge-hot{background:rgba(239,68,68,0.08);color:#dc2626;border:1px solid rgba(239,68,68,0.25)}
.card-preview{width:100%;height:160px;background:#f0f5ff;position:relative;overflow:hidden;display:flex;align-items:flex-end}
.chart-svg{width:100%;height:100%;position:absolute;inset:0}
.chart-overlay{position:absolute;inset:0;background:linear-gradient(180deg,transparent 50%,#fff 100%)}
.preview-stats{position:absolute;top:0.6rem;right:0.65rem;display:flex;flex-direction:column;align-items:flex-end;gap:0.25rem}
.profit-pct{font-family:'Share Tech Mono',monospace;font-size:1rem;font-weight:bold}
.profit-pos{color:#059669}
.profit-neg{color:var(--red)}
.profit-label{font-size:0.65rem;color:#475569;background:rgba(255,255,255,0.9);padding:0.1rem 0.35rem;border-radius:4px}
.card-body{padding:1rem;background:#fff}
.card-header-row{display:flex;align-items:flex-start;justify-content:space-between;gap:0.5rem;margin-bottom:0.5rem}
.ea-name{font-family:'Rajdhani',sans-serif;font-size:1rem;font-weight:700;color:var(--text);line-height:1.2;letter-spacing:0.3px}
.ea-version{font-family:'Share Tech Mono',monospace;font-size:0.65rem;color:var(--text-muted);background:var(--bg3);padding:0.15rem 0.4rem;border-radius:4px;flex-shrink:0;margin-top:0.1rem}
.ea-pair{display:flex;gap:0.35rem;flex-wrap:wrap;margin-bottom:0.6rem}
.pair-tag{font-family:'Share Tech Mono',monospace;font-size:0.65rem;color:var(--accent);background:rgba(59,130,246,0.08);border:1px solid rgba(59,130,246,0.2);padding:0.15rem 0.4rem;border-radius:4px}
.ea-desc{font-size:0.82rem;color:var(--text-muted);line-height:1.55;margin-bottom:0.75rem;display:-webkit-box;-webkit-line-clamp:2;-webkit-box-orient:vertical;overflow:hidden}
.mini-stats{display:grid;grid-template-columns:repeat(3,1fr);gap:0.4rem;margin-bottom:0.85rem}
.mini-stat{background:var(--bg3);border:1px solid var(--border);border-radius:8px;padding:0.4rem 0.3rem;text-align:center}
.mini-stat-val{font-family:'Share Tech Mono',monospace;font-size:0.75rem;font-weight:bold;display:block}
.mini-stat-key{font-size:0.62rem;color:var(--text-muted);margin-top:0.1rem;display:block}
.green{color:#059669}.gold{color:var(--gold)}.red{color:var(--red)}.cyan{color:var(--accent)}
.card-footer{display:flex;align-items:center;gap:0.5rem}
.btn-download{flex:1;background:linear-gradient(135deg,rgba(59,130,246,0.1),rgba(99,102,241,0.1));border:1px solid rgba(59,130,246,0.3);color:var(--accent);padding:0.55rem 0;border-radius:8px;font-family:'Rajdhani',sans-serif;font-weight:700;font-size:0.85rem;cursor:pointer;transition:all 0.2s;letter-spacing:0.5px;display:flex;align-items:center;justify-content:center;gap:0.4rem}
.btn-download:hover{background:linear-gradient(135deg,rgba(59,130,246,0.18),rgba(99,102,241,0.18));box-shadow:0 2px 12px rgba(59,130,246,0.2)}
.btn-detail{background:var(--bg3);border:1px solid var(--border);color:var(--text-muted);padding:0.55rem 0.7rem;border-radius:8px;font-size:0.85rem;cursor:pointer;transition:all 0.2s}
.btn-detail:hover{border-color:var(--border-glow);color:var(--text)}
.download-count{font-size:0.7rem;color:var(--text-muted);display:flex;align-items:center;gap:0.2rem;white-space:nowrap}

/* MODAL */
.modal-overlay{position:fixed;inset:0;background:rgba(15,23,42,0.5);backdrop-filter:blur(6px);z-index:200;display:flex;align-items:center;justify-content:center;padding:1rem;opacity:0;pointer-events:none;transition:opacity 0.25s}
.modal-overlay.open{opacity:1;pointer-events:all}
.modal{background:var(--bg2);border:1px solid var(--border);border-radius:18px;width:100%;max-width:700px;max-height:90vh;overflow-y:auto;transform:translateY(20px);transition:transform 0.25s;box-shadow:0 24px 80px rgba(0,0,0,0.15)}
.modal-overlay.open .modal{transform:translateY(0)}
.modal-header{padding:1.5rem 1.5rem 1rem;border-bottom:1px solid var(--border);display:flex;align-items:flex-start;justify-content:space-between;gap:1rem}
.modal-title{font-family:'Rajdhani',sans-serif;font-size:1.5rem;font-weight:700;color:var(--text)}
.modal-close{background:var(--bg3);border:1px solid var(--border);color:var(--text-muted);width:34px;height:34px;border-radius:8px;cursor:pointer;display:flex;align-items:center;justify-content:center;font-size:1.1rem;flex-shrink:0;transition:all 0.2s}
.modal-close:hover{color:var(--text);border-color:var(--border-glow)}
.modal-body{padding:1.5rem}
.modal-chart{width:100%;height:200px;background:var(--bg3);border:1px solid var(--border);border-radius:10px;margin-bottom:1.5rem;overflow:hidden;position:relative}
.modal-stats-grid{display:grid;grid-template-columns:repeat(4,1fr);gap:0.75rem;margin-bottom:1.5rem}
.modal-stat{background:var(--bg3);border:1px solid var(--border);border-radius:10px;padding:0.75rem;text-align:center}
.modal-stat-val{font-family:'Share Tech Mono',monospace;font-size:1.1rem;font-weight:bold;display:block;margin-bottom:0.25rem}
.modal-stat-key{font-size:0.72rem;color:var(--text-muted)}
.modal-section-title{font-family:'Rajdhani',sans-serif;font-size:0.85rem;font-weight:700;color:var(--text-muted);text-transform:uppercase;letter-spacing:1.5px;margin-bottom:0.6rem}
.modal-desc{font-size:0.9rem;color:var(--text-dim);line-height:1.7;margin-bottom:1.5rem}
.feature-list{list-style:none;display:grid;grid-template-columns:1fr 1fr;gap:0.4rem;margin-bottom:1.5rem}
.feature-list li{font-size:0.85rem;color:var(--text-dim);display:flex;align-items:center;gap:0.5rem}
.feature-list li::before{content:'▸';color:var(--accent);font-size:0.75rem}
.spec-table{width:100%;border-collapse:collapse;margin-bottom:1.5rem;font-size:0.85rem}
.spec-table td{padding:0.5rem 0.75rem;border-bottom:1px solid var(--border)}
.spec-table td:first-child{color:var(--text-muted);width:140px;font-size:0.8rem}
.spec-table td:last-child{color:var(--text-dim);font-family:'Share Tech Mono',monospace;font-size:0.8rem}
.modal-actions{display:flex;gap:0.75rem}
.btn-modal-download{flex:1;background:linear-gradient(135deg,#3b82f6,#6366f1);color:#fff;border:none;padding:0.75rem;border-radius:10px;font-family:'Rajdhani',sans-serif;font-weight:700;font-size:1rem;cursor:pointer;transition:all 0.2s;letter-spacing:0.5px;display:flex;align-items:center;justify-content:center;gap:0.5rem;box-shadow:0 4px 16px rgba(59,130,246,0.35)}
.btn-modal-download:hover{transform:translateY(-1px);box-shadow:0 6px 24px rgba(59,130,246,0.45)}
.btn-modal-fav{background:var(--bg3);border:1px solid var(--border);color:var(--text-muted);padding:0.75rem 1.25rem;border-radius:10px;cursor:pointer;font-size:1.1rem;transition:all 0.2s}
.btn-modal-fav:hover{border-color:var(--gold);color:var(--gold)}

/* UPLOAD MODAL */
.upload-modal-content{padding:1.5rem}
.upload-zone{border:2px dashed var(--border);border-radius:12px;padding:2.5rem;text-align:center;cursor:pointer;transition:all 0.2s;margin-bottom:1.25rem;background:rgba(59,130,246,0.03)}
.upload-zone:hover{border-color:var(--accent);background:rgba(59,130,246,0.07)}
.upload-icon{font-size:2.5rem;margin-bottom:0.75rem;display:block}
.upload-zone p{color:var(--text-muted);font-size:0.9rem}
.upload-zone strong{color:var(--accent)}
.form-group{margin-bottom:1rem}
.form-label{display:block;font-size:0.82rem;color:var(--text-muted);margin-bottom:0.4rem;font-family:'Rajdhani',sans-serif;font-weight:600;letter-spacing:0.5px;text-transform:uppercase}
.form-input{width:100%;background:var(--bg3);border:1px solid var(--border);color:var(--text);padding:0.65rem 0.9rem;border-radius:8px;font-size:0.9rem;font-family:'Sarabun',sans-serif;outline:none;transition:border-color 0.2s}
.form-input:focus{border-color:var(--accent)}
.form-input::placeholder{color:var(--text-muted)}
.form-row{display:grid;grid-template-columns:1fr 1fr;gap:0.75rem}
textarea.form-input{resize:vertical;min-height:90px}

/* TOAST */
.toast{position:fixed;bottom:2rem;right:6rem;background:var(--bg2);border:1px solid rgba(59,130,246,0.3);color:var(--text);padding:0.85rem 1.2rem;border-radius:10px;font-size:0.9rem;z-index:500;transform:translateY(80px);opacity:0;transition:all 0.3s;display:flex;align-items:center;gap:0.6rem;box-shadow:0 8px 32px rgba(0,0,0,0.12);max-width:320px}
.toast.show{transform:translateY(0);opacity:1}

/* SCROLLBAR */
::-webkit-scrollbar{width:6px}
::-webkit-scrollbar-track{background:#f1f5f9}
::-webkit-scrollbar-thumb{background:#cbd5e1;border-radius:3px}
::-webkit-scrollbar-thumb:hover{background:#94a3b8}

/* FOOTER */
footer{position:relative;z-index:1;border-top:1px solid var(--border);padding:2rem;text-align:center;color:var(--text-muted);font-size:0.82rem}
footer span{color:var(--accent)}

/* CHAT WIDGET */
.chat-bubble{position:fixed;bottom:2rem;right:2rem;z-index:300;width:58px;height:58px;background:linear-gradient(135deg,#3b82f6,#6366f1);border-radius:50%;border:none;cursor:pointer;box-shadow:0 4px 20px rgba(59,130,246,0.45);display:flex;align-items:center;justify-content:center;font-size:1.4rem;transition:all 0.25s}
.chat-bubble:hover{transform:scale(1.1);box-shadow:0 6px 28px rgba(59,130,246,0.6)}
.notif-dot{position:absolute;top:3px;right:3px;width:12px;height:12px;background:#22c55e;border-radius:50%;border:2px solid #fff;animation:ndot 2s infinite}
@keyframes ndot{0%,100%{transform:scale(1)}50%{transform:scale(1.35)}}
.chat-window{position:fixed;bottom:5.5rem;right:2rem;z-index:300;width:370px;background:#fff;border:1px solid #dde3ef;border-radius:20px;box-shadow:0 12px 60px rgba(0,0,0,0.14);display:flex;flex-direction:column;overflow:hidden;transform-origin:bottom right;transform:scale(0.85) translateY(20px);opacity:0;pointer-events:none;transition:all 0.25s cubic-bezier(0.34,1.56,0.64,1)}
.chat-window.open{transform:scale(1) translateY(0);opacity:1;pointer-events:all}
.chat-head{background:linear-gradient(135deg,#3b82f6,#6366f1);padding:1rem 1.1rem;display:flex;align-items:center;gap:0.75rem;flex-shrink:0}
.chat-ava-h{width:38px;height:38px;background:rgba(255,255,255,0.2);border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:1.2rem;flex-shrink:0}
.chat-head-info{flex:1}
.chat-head-name{font-family:'Rajdhani',sans-serif;font-weight:700;font-size:0.95rem;color:#fff}
.chat-head-status{font-size:0.72rem;color:rgba(255,255,255,0.8);display:flex;align-items:center;gap:0.35rem;margin-top:0.1rem}
.sdot{width:6px;height:6px;background:#4ade80;border-radius:50%;animation:ndot 2s infinite}
.chat-closebtn{background:rgba(255,255,255,0.15);border:none;color:#fff;width:30px;height:30px;border-radius:8px;cursor:pointer;font-size:0.9rem;display:flex;align-items:center;justify-content:center;transition:background 0.2s}
.chat-closebtn:hover{background:rgba(255,255,255,0.28)}
.chat-messages{flex:1;overflow-y:auto;padding:1rem;display:flex;flex-direction:column;gap:0.75rem;background:#f8faff;max-height:330px}
.cmsg{display:flex;gap:0.5rem;align-items:flex-end;animation:cmsgIn 0.25s ease both}
@keyframes cmsgIn{from{opacity:0;transform:translateY(8px)}to{opacity:1;transform:translateY(0)}}
.cmsg.user{flex-direction:row-reverse}
.cmsg-ava{width:28px;height:28px;border-radius:50%;background:linear-gradient(135deg,#3b82f6,#6366f1);display:flex;align-items:center;justify-content:center;font-size:0.75rem;color:#fff;flex-shrink:0}
.cmsg-bubble{max-width:82%;padding:0.6rem 0.85rem;border-radius:14px;font-size:0.85rem;line-height:1.6;font-family:'Sarabun',sans-serif}
.cmsg.ai .cmsg-bubble{background:#fff;color:#1e293b;border:1px solid #e2e8f0;border-bottom-left-radius:4px;box-shadow:0 1px 4px rgba(0,0,0,0.06)}
.cmsg.user .cmsg-bubble{background:linear-gradient(135deg,#3b82f6,#6366f1);color:#fff;border-bottom-right-radius:4px}
.typing-wrap{display:flex;gap:0.5rem;align-items:flex-end}
.typing-bubble{background:#fff;border:1px solid #e2e8f0;border-radius:14px;border-bottom-left-radius:4px;padding:0.65rem 0.9rem;display:flex;gap:4px;align-items:center}
.tdot{width:7px;height:7px;background:#94a3b8;border-radius:50%;animation:tbounce 1.2s infinite}
.tdot:nth-child(2){animation-delay:0.2s}.tdot:nth-child(3){animation-delay:0.4s}
@keyframes tbounce{0%,60%,100%{transform:translateY(0)}30%{transform:translateY(-6px)}}
.quick-qs{padding:0.5rem 1rem;display:flex;flex-wrap:wrap;gap:0.4rem;border-top:1px solid #eef1f6;background:#fff;flex-shrink:0}
.quick-q{font-size:0.72rem;background:#f0f5ff;border:1px solid #c7d9ff;color:#3b82f6;padding:0.3rem 0.65rem;border-radius:20px;cursor:pointer;font-family:'Sarabun',sans-serif;transition:all 0.15s;white-space:nowrap}
.quick-q:hover{background:#dbeafe;border-color:#3b82f6}
.chat-input-row{padding:0.75rem 1rem;display:flex;gap:0.5rem;border-top:1px solid #eef1f6;background:#fff;flex-shrink:0}
.chat-input{flex:1;background:#f8faff;border:1px solid #dde3ef;color:#1e293b;padding:0.6rem 0.85rem;border-radius:10px;font-size:0.85rem;font-family:'Sarabun',sans-serif;outline:none;transition:border-color 0.2s}
.chat-input:focus{border-color:#3b82f6}
.chat-input::placeholder{color:#94a3b8}
.chat-send{background:linear-gradient(135deg,#3b82f6,#6366f1);border:none;color:#fff;width:38px;height:38px;border-radius:10px;cursor:pointer;font-size:1rem;display:flex;align-items:center;justify-content:center;flex-shrink:0;transition:all 0.2s;box-shadow:0 2px 8px rgba(59,130,246,0.35)}
.chat-send:hover{transform:scale(1.08)}
.chat-send:disabled{opacity:0.5;cursor:not-allowed;transform:none}

@media(max-width:768px){nav{display:none}.modal-stats-grid{grid-template-columns:repeat(2,1fr)}.feature-list{grid-template-columns:1fr}.form-row{grid-template-columns:1fr}.chat-window{width:calc(100vw - 2rem);right:1rem}}
</style>
</head>
<body>

<!-- HEADER -->
<header>
  <div class="header-inner">
    <a class="logo" href="#">
      <div class="logo-icon">FX</div>
      <span class="logo-text">Robot<span>Hub</span></span>
    </a>
    <nav>
      <a href="#" class="active">🏠 หน้าหลัก</a>
      <a href="#">📊 Backtest</a>
      <a href="#">📚 คู่มือ</a>
      <a href="#">🏆 อันดับ</a>
      <a href="#">💬 ชุมชน</a>
    </nav>
    <button class="btn-upload" onclick="openUploadModal()">⬆ อัพโหลด EA</button>
  </div>
</header>

<!-- HERO -->
<section class="hero">
  <div class="hero-badge">● LIVE — อัพเดทล่าสุด</div>
  <h1>คลังรวม <span class="hl">EA & Robot</span><br>Forex ที่ใหญ่ที่สุด</h1>
  <p>ดาวน์โหลด Expert Advisor และ Trading Robot ฟรี พร้อม Backtest จริง คู่มือครบ และสถิติโปร่งใส</p>
  <div class="stats-row">
    <div class="stat"><span class="stat-num">248</span><div class="stat-label">EA ทั้งหมด</div></div>
    <div class="stat"><span class="stat-num">12.4K</span><div class="stat-label">ดาวน์โหลด</div></div>
    <div class="stat"><span class="stat-num">18</span><div class="stat-label">Strategy</div></div>
    <div class="stat"><span class="stat-num">Free</span><div class="stat-label">100% ฟรี</div></div>
  </div>
</section>

<!-- TOOLBAR -->
<div class="toolbar">
  <div class="search-box">
    <span class="search-icon">🔍</span>
    <input type="text" placeholder="ค้นหา EA, คู่สกุลเงิน, กลยุทธ์..." id="searchInput" oninput="filterCards()">
  </div>
  <div class="filter-tabs">
    <button class="filter-tab active" onclick="setFilter(this,'all')">ทั้งหมด</button>
    <button class="filter-tab" onclick="setFilter(this,'scalping')">Scalping</button>
    <button class="filter-tab" onclick="setFilter(this,'trend')">Trend</button>
    <button class="filter-tab" onclick="setFilter(this,'grid')">Grid</button>
    <button class="filter-tab" onclick="setFilter(this,'martingale')">Martingale</button>
    <button class="filter-tab" onclick="setFilter(this,'hedging')">Hedging</button>
    <button class="filter-tab" onclick="setFilter(this,'news')">News</button>
  </div>
  <select class="sort-select" onchange="sortCards(this.value)">
    <option value="newest">ใหม่ล่าสุด</option>
    <option value="popular">ยอดนิยม</option>
    <option value="profit">กำไรสูงสุด</option>
    <option value="drawdown">DD ต่ำสุด</option>
  </select>
</div>

<!-- GRID -->
<section class="grid-section">
  <div class="section-header">
    <span class="section-title">EA Library</span>
    <div class="section-line"></div>
    <span class="count-badge" id="countBadge">แสดง 12 จาก 248</span>
  </div>
  <div class="ea-grid" id="eaGrid"></div>
</section>

<footer><p>© 2025 <span>FX Robot Hub</span> — แบ่งปันความรู้ Forex Robot เพื่อชุมชน Trader ไทย</p></footer>

<!-- DETAIL MODAL -->
<div class="modal-overlay" id="detailModal" onclick="if(event.target===this)closeModal('detailModal')">
  <div class="modal">
    <div class="modal-header">
      <div>
        <div class="modal-title" id="modalTitle">EA Name</div>
        <div style="font-size:0.8rem;color:var(--text-muted);margin-top:0.3rem" id="modalMeta">-</div>
      </div>
      <button class="modal-close" onclick="closeModal('detailModal')">✕</button>
    </div>
    <div class="modal-body">
      <div class="modal-chart" id="modalChart"></div>
      <div class="modal-stats-grid" id="modalStats"></div>
      <div class="modal-section-title">📋 คำอธิบาย</div>
      <div class="modal-desc" id="modalDesc"></div>
      <div class="modal-section-title">✅ คุณสมบัติ</div>
      <ul class="feature-list" id="modalFeatures"></ul>
      <div class="modal-section-title">⚙️ ข้อมูลจำเพาะ</div>
      <table class="spec-table" id="modalSpecs"></table>
      <div class="modal-actions">
        <button class="btn-modal-download" onclick="downloadEA()">⬇ ดาวน์โหลด EA ฟรี</button>
        <button class="btn-modal-fav" title="บันทึก">★</button>
      </div>
    </div>
  </div>
</div>

<!-- UPLOAD MODAL -->
<div class="modal-overlay" id="uploadModal" onclick="if(event.target===this)closeModal('uploadModal')">
  <div class="modal">
    <div class="modal-header">
      <div class="modal-title">⬆ อัพโหลด EA ใหม่</div>
      <button class="modal-close" onclick="closeModal('uploadModal')">✕</button>
    </div>
    <div class="upload-modal-content">
      <div class="upload-zone" onclick="document.getElementById('eaFile').click()">
        <span class="upload-icon">📁</span>
        <p><strong>คลิกเพื่อเลือกไฟล์ EA</strong> หรือลากวางที่นี่</p>
        <p style="margin-top:0.4rem;font-size:0.8rem">รองรับ .ex4, .ex5, .mq4, .mq5, .zip</p>
        <input type="file" id="eaFile" style="display:none" accept=".ex4,.ex5,.mq4,.mq5,.zip">
      </div>
      <div class="form-group">
        <label class="form-label">ชื่อ EA *</label>
        <input class="form-input" type="text" placeholder="เช่น TrendMaster Pro v2.1">
      </div>
      <div class="form-row">
        <div class="form-group">
          <label class="form-label">กลยุทธ์</label>
          <select class="form-input"><option>Scalping</option><option>Trend Following</option><option>Grid</option><option>Martingale</option><option>Hedging</option><option>News Trading</option></select>
        </div>
        <div class="form-group">
          <label class="form-label">คู่สกุลเงิน</label>
          <input class="form-input" type="text" placeholder="EURUSD, GBPUSD, ...">
        </div>
      </div>
      <div class="form-row">
        <div class="form-group">
          <label class="form-label">กำไรรวม (%)</label>
          <input class="form-input" type="number" placeholder="เช่น 345.6">
        </div>
        <div class="form-group">
          <label class="form-label">Max Drawdown (%)</label>
          <input class="form-input" type="number" placeholder="เช่น 12.4">
        </div>
      </div>
      <div class="form-group">
        <label class="form-label">คำอธิบาย</label>
        <textarea class="form-input" placeholder="อธิบายวิธีทำงาน กลยุทธ์ เงื่อนไขการใช้งาน..."></textarea>
      </div>
      <div class="form-group">
        <label class="form-label">อัพโหลดภาพ Backtest</label>
        <input class="form-input" type="file" accept="image/*" style="padding:0.5rem">
      </div>
      <div class="modal-actions" style="margin-top:0.5rem">
        <button class="btn-modal-download" onclick="submitUpload()">✅ อัพโหลด EA</button>
      </div>
    </div>
  </div>
</div>

<!-- TOAST -->
<div class="toast" id="toast"><span id="toastMsg">ดาวน์โหลดสำเร็จ</span></div>

<!-- CHAT BUBBLE -->
<button class="chat-bubble" onclick="toggleChat()" id="chatBubble" title="ถาม AI">
  🤖<span class="notif-dot"></span>
</button>

<!-- CHAT WINDOW -->
<div class="chat-window" id="chatWindow">
  <div class="chat-head">
    <div class="chat-ava-h">🤖</div>
    <div class="chat-head-info">
      <div class="chat-head-name">FX Robot Assistant</div>
      <div class="chat-head-status"><span class="sdot"></span>พร้อมตอบเรื่อง EA ทุกตัว</div>
    </div>
    <button class="chat-closebtn" onclick="toggleChat()">✕</button>
  </div>
  <div class="chat-messages" id="chatMessages"></div>
  <div class="quick-qs" id="quickQs">
    <button class="quick-q" onclick="sendQuick('EA ตัวไหนเหมาะกับมือใหม่?')">🌱 มือใหม่</button>
    <button class="quick-q" onclick="sendQuick('EA สำหรับ Gold มีอะไรบ้าง?')">🥇 EA Gold</button>
    <button class="quick-q" onclick="sendQuick('EA ตัวไหน Drawdown ต่ำสุด?')">📉 DD ต่ำสุด</button>
    <button class="quick-q" onclick="sendQuick('วิธีติดตั้ง EA ใน MT4?')">⚙️ วิธีติดตั้ง</button>
    <button class="quick-q" onclick="sendQuick('EA Scalping ที่ดีที่สุดคืออะไร?')">⚡ Scalping</button>
  </div>
  <div class="chat-input-row">
    <input class="chat-input" id="chatInput" type="text" placeholder="ถามเกี่ยวกับ EA...">
    <button class="chat-send" id="chatSendBtn" onclick="sendChat()">➤</button>
  </div>
</div>

<script>
// ════════════════════════
// DATA
// ════════════════════════
var eaData = [
  {id:1,name:'TrendMaster Pro',version:'v2.3',badge:'hot',pairs:['EURUSD','GBPUSD'],strategy:'trend',profit:'+348%',dd:'11.2',wr:'67',pf:'2.14',trades:'1842',color:'#16a34a',desc:'EA ตามเทรนด์อัจฉริยะที่ใช้ EMA cross และ ATR filter กรองสัญญาณหลอก ทำงานได้ดีในตลาดที่มีทิศทางชัดเจน',tf:'H1',platform:'MT4/MT5',downloads:3241,year:'2024',features:['Multi-timeframe analysis','ATR Trailing Stop','News Filter อัตโนมัติ','Risk Management ครบ','ไม่ใช้ Martingale','Dashboard แสดงผล'],specs:{Timeframe:'H1','Min. Deposit':'$500','Lot Size':'ปรับได้','Max Spread':'2 pip',Broker:'All ECN'}},
  {id:2,name:'ScalpKing Ultra',version:'v1.8',badge:'free',pairs:['EURUSD'],strategy:'scalping',profit:'+192%',dd:'8.7',wr:'73',pf:'1.87',trades:'5621',color:'#2563eb',desc:'สแคลปปิ้ง EA ความเร็วสูง เปิด-ปิดออเดอร์ภายในไม่กี่นาที เหมาะกับบัญชีที่มี spread ต่ำ',tf:'M5',platform:'MT4',downloads:5882,year:'2024',features:['Ultra-fast execution','Spread filter','Session filter','Multiple pairs','Low drawdown','ข่าว filter'],specs:{Timeframe:'M5','Min. Deposit':'$200','Lot Size':'0.01 min','Max Spread':'1 pip',Broker:'ECN/STP'}},
  {id:3,name:'GridSurfer X',version:'v3.1',badge:'new',pairs:['XAUUSD'],strategy:'grid',profit:'+621%',dd:'34.1',wr:'82',pf:'3.21',trades:'3108',color:'#d97706',desc:'Grid trading EA สำหรับ Gold โดยเฉพาะ ระยะ Grid ปรับตามความผันผวน มี hard stop loss ป้องกันความเสี่ยง',tf:'M15',platform:'MT5',downloads:1920,year:'2025',features:['Dynamic grid spacing','Hard stop loss','Gold optimized','Auto lot sizing','Drawdown limit','ปรับ grid อัตโนมัติ'],specs:{Timeframe:'M15','Min. Deposit':'$1000','Lot Size':'Auto','Max Spread':'3 pip',Symbol:'XAUUSD'}},
  {id:4,name:'NewsHunter Elite',version:'v2.0',badge:'premium',pairs:['EURUSD','USDJPY','GBPUSD'],strategy:'news',profit:'+156%',dd:'5.3',wr:'61',pf:'2.45',trades:'412',color:'#7c3aed',desc:'ซื้อขายก่อน-หลังข่าวสำคัญ ดึงปฏิทินเศรษฐกิจอัตโนมัติ วางออเดอร์ straddle ก่อนข่าว 2 นาที',tf:'M1',platform:'MT4/MT5',downloads:887,year:'2025',features:['ดึงข่าวอัตโนมัติ','Straddle strategy','Slippage protection','Auto time zone','เลือกระดับข่าวได้','OCO orders'],specs:{Timeframe:'M1','Min. Deposit':'$300','Min. Lot':'0.01',Broker:'Low Slippage'}},
  {id:5,name:'MeanRevert AI',version:'v1.2',badge:'new',pairs:['EURUSD','GBPJPY'],strategy:'trend',profit:'+234%',dd:'15.8',wr:'64',pf:'1.92',trades:'2341',color:'#db2777',desc:'ใช้ AI ตรวจจับจุด overbought/oversold ผ่าน Z-Score และ Bollinger Band ซื้อเมื่อราคาออกห่าง mean มากเกิน',tf:'H4',platform:'MT5',downloads:1456,year:'2025',features:['AI signal detection','Z-Score filter','Bollinger Bands','Dynamic SL/TP','Pair correlation','Kelly sizing'],specs:{Timeframe:'H4','Min. Deposit':'$500','Lot Size':'Auto','Max Spread':'2 pip',Model:'Neural Net'}},
  {id:6,name:'HedgeShield FX',version:'v4.2',badge:'free',pairs:['EURUSD','GBPUSD','EURGBP'],strategy:'hedging',profit:'+97%',dd:'3.2',wr:'89',pf:'4.12',trades:'678',color:'#0d9488',desc:'Hedging EA ที่ป้องกันความเสี่ยงด้วยการเปิดออเดอร์สวนทางในคู่สกุลที่ correlated กัน ลด DD ได้มากถึง 70%',tf:'D1',platform:'MT4',downloads:2103,year:'2023',features:['Auto correlation detection','Smart hedging','Low risk profile','Multi-pair','Equity protection','Manual override'],specs:{Timeframe:'D1','Min. Deposit':'$1000',Pairs:'3+','DD Target':'<5%',Style:'Conservative'}},
  {id:7,name:'BreakoutSniper',version:'v1.5',badge:'hot',pairs:['EURUSD','GBPUSD','USDJPY'],strategy:'trend',profit:'+287%',dd:'18.4',wr:'58',pf:'2.01',trades:'921',color:'#ea580c',desc:'ล่าเหยื่อ breakout จาก London และ NY session เปิดออเดอร์เมื่อราคาทะลุ high/low ของ pre-session',tf:'M30',platform:'MT4/MT5',downloads:2897,year:'2024',features:['Session breakout','False breakout filter','ATR stop loss','Session selector','Partial close','Push notification'],specs:{Timeframe:'M30','Min. Deposit':'$500',Sessions:'London/NY','Max Spread':'1.5 pip',Filter:'Momentum'}},
  {id:8,name:'SafeGrid Nano',version:'v2.7',badge:'free',pairs:['EURUSD'],strategy:'grid',profit:'+445%',dd:'29.6',wr:'91',pf:'2.88',trades:'8821',color:'#2563eb',desc:'Grid EA สำหรับผู้เริ่มต้น ตั้งค่าน้อย ทำงานอัตโนมัติ มี max grid level ป้องกันไม่ให้ margin หมด',tf:'M1',platform:'MT4',downloads:7341,year:'2023',features:['ตั้งค่าง่าย','Max level limit','Compounding option','Smart recovery','Live stats panel','Email alerts'],specs:{Timeframe:'M1','Min. Deposit':'$500','Grid Size':'10 pip','Max Level':'10',Recovery:'Auto'}},
  {id:9,name:'PinbarHunter',version:'v1.1',badge:'new',pairs:['XAUUSD','EURUSD'],strategy:'trend',profit:'+178%',dd:'9.4',wr:'62',pf:'1.78',trades:'534',color:'#9333ea',desc:'ตรวจจับรูปแบบแท่งเทียน Pinbar และ Engulfing ใน timeframe สูง เข้า trade เฉพาะจุด high probability',tf:'H4',platform:'MT5',downloads:623,year:'2025',features:['Pattern recognition','HTF confirmation','Risk/Reward 1:2','Candle filter','Support/Resistance','Low trade frequency'],specs:{Timeframe:'H4/D1','Min. Deposit':'$300',Patterns:'Pinbar,Engulf','RR Ratio':'1:2+',Frequency:'Low'}},
  {id:10,name:'Martini Recovery',version:'v3.0',badge:'hot',pairs:['GBPUSD','GBPJPY'],strategy:'martingale',profit:'+892%',dd:'47.3',wr:'96',pf:'5.12',trades:'4421',color:'#dc2626',desc:'Martingale strategy พร้อม recovery mode อัจฉริยะ มี max lot limit และ equity stop เพื่อควบคุมความเสี่ยง ระวัง: ความเสี่ยงสูง',tf:'M15',platform:'MT4',downloads:4112,year:'2024',features:['Smart martingale','Equity stop loss','Max lot control','Recovery algo','Win rate tracking','Risk warning'],specs:{Timeframe:'M15','Min. Deposit':'$2000',Risk:'HIGH','Max Lot':'2.00',Style:'Aggressive'}},
  {id:11,name:'ICT Killzone Bot',version:'v1.0',badge:'new',pairs:['EURUSD','GBPUSD','NAS100'],strategy:'trend',profit:'+201%',dd:'12.1',wr:'55',pf:'2.33',trades:'287',color:'#0d9488',desc:'EA ที่สร้างตามแนวคิด ICT เข้า trade ใน Killzone sessions ใช้ Liquidity sweep และ FVG เป็นเงื่อนไขหลัก',tf:'M5',platform:'MT5',downloads:1847,year:'2025',features:['ICT methodology','Killzone sessions','FVG detection','Liquidity sweep','OB levels','Swing analysis'],specs:{Timeframe:'M5',Concept:'ICT',Sessions:'London/NY AM','Min. Deposit':'$500'}},
  {id:12,name:'MACD Divergence EA',version:'v2.2',badge:'free',pairs:['EURUSD','USDJPY','USDCHF'],strategy:'trend',profit:'+134%',dd:'7.6',wr:'60',pf:'1.65',trades:'1203',color:'#3b82f6',desc:'ตรวจจับ Hidden และ Regular Divergence บน MACD แล้วเข้า trade ตาม setup ที่แม่นยำ กรองด้วย RSI และ Volume',tf:'H1',platform:'MT4/MT5',downloads:3021,year:'2023',features:['Regular divergence','Hidden divergence','RSI filter','Volume confirm','Multiple TF','Auto SL/TP'],specs:{Timeframe:'H1',Indicator:'MACD + RSI','Min. Deposit':'$300','Max Spread':'2 pip',Filter:'Volume'}}
];

var currentEA = null;
var activeFilter = 'all';
var activeSearch = '';
var activeSort = 'newest';

// ════════════════════════
// CHART
// ════════════════════════
function generateChart(color, positive, w, h, area) {
  var pts = [];
  var y = h * 0.6;
  var steps = Math.floor(w / 8);
  for (var i = 0; i <= steps; i++) {
    y += (Math.random() - (positive ? 0.38 : 0.62)) * 14;
    y = Math.max(h * 0.08, Math.min(h * 0.92, y));
    pts.push({x: (i / steps) * w, y: y});
  }
  var pathD = pts.map(function(p,i){ return (i===0?'M':'L')+' '+p.x.toFixed(1)+' '+p.y.toFixed(1); }).join(' ');
  var areaD = pathD + ' L '+w+' '+h+' L 0 '+h+' Z';
  var gid = 'cg'+color.replace('#','');
  return '<svg class="chart-svg" viewBox="0 0 '+w+' '+h+'" preserveAspectRatio="none">'
    +'<defs><linearGradient id="'+gid+'" x1="0" y1="0" x2="0" y2="1">'
    +'<stop offset="0%" stop-color="'+color+'" stop-opacity="0.2"/>'
    +'<stop offset="100%" stop-color="'+color+'" stop-opacity="0"/>'
    +'</linearGradient></defs>'
    +(area ? '<path d="'+areaD+'" fill="url(#'+gid+')" />' : '')
    +'<path d="'+pathD+'" fill="none" stroke="'+color+'" stroke-width="2" stroke-linecap="round"/>'
    +'</svg>';
}

// ════════════════════════
// RENDER CARDS
// ════════════════════════
function renderCards() {
  var grid = document.getElementById('eaGrid');
  var filtered = eaData.filter(function(ea) {
    var mf = activeFilter === 'all' || ea.strategy === activeFilter;
    var q = activeSearch.toLowerCase();
    var ms = !q || ea.name.toLowerCase().indexOf(q) > -1 || ea.pairs.join(' ').toLowerCase().indexOf(q) > -1 || ea.desc.toLowerCase().indexOf(q) > -1;
    return mf && ms;
  });
  if (activeSort === 'profit') filtered.sort(function(a,b){ return parseFloat(b.profit)-parseFloat(a.profit); });
  else if (activeSort === 'popular') filtered.sort(function(a,b){ return b.downloads-a.downloads; });
  else if (activeSort === 'drawdown') filtered.sort(function(a,b){ return parseFloat(a.dd)-parseFloat(b.dd); });

  document.getElementById('countBadge').textContent = 'แสดง '+filtered.length+' จาก '+eaData.length;
  var badgeLabels = {free:'FREE', premium:'PREMIUM', new:'NEW', hot:'🔥 HOT'};

  grid.innerHTML = filtered.map(function(ea, idx) {
    var isPos = ea.profit.charAt(0) !== '-';
    var chart = generateChart(ea.color, isPos, 280, 160, true);
    var pairs = ea.pairs.map(function(p){ return '<span class="pair-tag">'+p+'</span>'; }).join('');
    return '<div class="ea-card" onclick="openDetail('+ea.id+')" style="animation-delay:'+(idx*0.05)+'s">'
      +'<span class="card-badge badge-'+ea.badge+'">'+badgeLabels[ea.badge]+'</span>'
      +'<div class="card-preview">'+chart
      +'<div class="chart-overlay"></div>'
      +'<div class="preview-stats">'
      +'<div class="profit-pct '+(isPos?'profit-pos':'profit-neg')+'">'+ea.profit+'</div>'
      +'<div class="profit-label">Total Profit</div>'
      +'</div></div>'
      +'<div class="card-body">'
      +'<div class="card-header-row"><div class="ea-name">'+ea.name+'</div><div class="ea-version">'+ea.version+'</div></div>'
      +'<div class="ea-pair">'+pairs+'<span class="pair-tag" style="color:var(--text-muted);border-color:var(--border)">'+ea.strategy.toUpperCase()+'</span></div>'
      +'<div class="ea-desc">'+ea.desc+'</div>'
      +'<div class="mini-stats">'
      +'<div class="mini-stat"><span class="mini-stat-val '+(isPos?'green':'red')+'">'+ea.profit+'</span><span class="mini-stat-key">กำไร</span></div>'
      +'<div class="mini-stat"><span class="mini-stat-val gold">'+ea.dd+'%</span><span class="mini-stat-key">Max DD</span></div>'
      +'<div class="mini-stat"><span class="mini-stat-val cyan">'+ea.wr+'%</span><span class="mini-stat-key">Win Rate</span></div>'
      +'</div>'
      +'<div class="card-footer">'
      +'<button class="btn-download" onclick="event.stopPropagation();downloadEA('+ea.id+')">⬇ ดาวน์โหลด</button>'
      +'<button class="btn-detail" onclick="event.stopPropagation();openDetail('+ea.id+')" title="รายละเอียด">📄</button>'
      +'<div class="download-count">⬇ '+ea.downloads.toLocaleString()+'</div>'
      +'</div></div></div>';
  }).join('');
}

// ════════════════════════
// DETAIL MODAL
// ════════════════════════
function openDetail(id) {
  currentEA = null;
  for (var i=0;i<eaData.length;i++){ if(eaData[i].id===id){ currentEA=eaData[i]; break; } }
  if (!currentEA) return;
  var ea = currentEA;
  document.getElementById('modalTitle').textContent = ea.name + ' ' + ea.version;
  document.getElementById('modalMeta').innerHTML = ea.pairs.join(', ') + ' &nbsp;·&nbsp; ' + ea.tf + ' &nbsp;·&nbsp; ' + ea.platform + ' &nbsp;·&nbsp; ⬇ ' + ea.downloads.toLocaleString();
  var isPos = ea.profit.charAt(0) !== '-';
  var mc = document.getElementById('modalChart');
  mc.innerHTML = generateChart(ea.color, isPos, 660, 200, true);
  var stats = [
    {val:ea.profit, key:'Total Profit', cls:isPos?'green':'red'},
    {val:ea.dd+'%', key:'Max Drawdown', cls:'gold'},
    {val:ea.wr+'%', key:'Win Rate', cls:'cyan'},
    {val:ea.pf, key:'Profit Factor', cls:'green'},
    {val:ea.trades, key:'Total Trades', cls:''},
    {val:ea.tf, key:'Timeframe', cls:'cyan'},
    {val:ea.platform, key:'Platform', cls:''},
    {val:ea.year, key:'ปีที่เผยแพร่', cls:''}
  ];
  document.getElementById('modalStats').innerHTML = stats.map(function(s){
    return '<div class="modal-stat"><span class="modal-stat-val '+s.cls+'">'+s.val+'</span><div class="modal-stat-key">'+s.key+'</div></div>';
  }).join('');
  document.getElementById('modalDesc').textContent = ea.desc;
  document.getElementById('modalFeatures').innerHTML = ea.features.map(function(f){ return '<li>'+f+'</li>'; }).join('');
  document.getElementById('modalSpecs').innerHTML = Object.keys(ea.specs).map(function(k){
    return '<tr><td>'+k+'</td><td>'+ea.specs[k]+'</td></tr>';
  }).join('');
  document.getElementById('detailModal').classList.add('open');
}

function downloadEA(id) {
  var ea = id ? eaData.find(function(e){ return e.id===id; }) : currentEA;
  if (!ea) return;
  ea.downloads++;
  showToast('✅ กำลังดาวน์โหลด "'+ea.name+'"...');
  renderCards();
}

// ════════════════════════
// UPLOAD
// ════════════════════════
function openUploadModal() { document.getElementById('uploadModal').classList.add('open'); }
function submitUpload() { closeModal('uploadModal'); showToast('🚀 อัพโหลด EA สำเร็จ! กำลังรอตรวจสอบ...'); }

// ════════════════════════
// HELPERS
// ════════════════════════
function closeModal(id) { document.getElementById(id).classList.remove('open'); }
function setFilter(btn, val) {
  document.querySelectorAll('.filter-tab').forEach(function(b){ b.classList.remove('active'); });
  btn.classList.add('active');
  activeFilter = val;
  renderCards();
}
function filterCards() { activeSearch = document.getElementById('searchInput').value; renderCards(); }
function sortCards(val) { activeSort = val; renderCards(); }
function showToast(msg) {
  var t = document.getElementById('toast');
  document.getElementById('toastMsg').textContent = msg;
  t.classList.add('show');
  setTimeout(function(){ t.classList.remove('show'); }, 3000);
}
document.addEventListener('keydown', function(e){ if(e.key==='Escape'){ closeModal('detailModal'); closeModal('uploadModal'); } });

// ════════════════════════
// AI CHAT
// ════════════════════════
var chatOpen = false;
var chatBusy = false;
var chatHist = [];

function buildSysPrompt() {
  var kb = eaData.map(function(ea){
    return '['+ea.name+' '+ea.version+'] กลยุทธ์:'+ea.strategy
      +' | คู่:'+ea.pairs.join(',')
      +' | กำไร:'+ea.profit
      +' | DD:'+ea.dd+'%'
      +' | WR:'+ea.wr+'%'
      +' | TF:'+ea.tf
      +' | '+ea.platform
      +' | ดาวน์โหลด:'+ea.downloads
      +' | '+ea.desc;
  }).join('\n');
  return 'คุณเป็น AI ผู้ช่วยของ FX Robot Hub คลัง EA Forex\n\nข้อมูล EA ในเว็บ:\n'+kb+'\n\nกฎ: ตอบภาษาไทย กระชับ เป็นมิตร ตอบไม่เกิน 150 คำ ใช้ emoji ช่วยอ่าน แนะนำ EA จากข้อมูลข้างบน';
}

function toggleChat() {
  chatOpen = !chatOpen;
  document.getElementById('chatWindow').classList.toggle('open', chatOpen);
  if (chatOpen && chatHist.length === 0) {
    setTimeout(function(){ addChatMsg('ai', 'สวัสดีครับ! 👋 ผมคือ AI ผู้ช่วยของ FX Robot Hub\n\nถามเรื่อง EA ได้เลยครับ เช่น แนะนำ EA ตามสไตล์การเทรด, เปรียบเทียบ EA หรือวิธีติดตั้ง 🤖'); }, 400);
    setTimeout(function(){ document.getElementById('chatInput').focus(); }, 300);
  }
}

function addChatMsg(role, text) {
  var box = document.getElementById('chatMessages');
  var d = document.createElement('div');
  d.className = 'cmsg '+role;
  var ava = role==='ai'
    ? '<div class="cmsg-ava">🤖</div>'
    : '<div class="cmsg-ava" style="background:linear-gradient(135deg,#10b981,#059669)">👤</div>';
  var bub = '<div class="cmsg-bubble">'+text.replace(/\n/g,'<br>')+'</div>';
  d.innerHTML = role==='ai' ? ava+bub : bub+ava;
  box.appendChild(d);
  box.scrollTop = box.scrollHeight;
}

function showTypingIndicator() {
  var box = document.getElementById('chatMessages');
  var d = document.createElement('div');
  d.className='typing-wrap'; d.id='typingWrap';
  d.innerHTML='<div class="cmsg-ava">🤖</div><div class="typing-bubble"><div class="tdot"></div><div class="tdot"></div><div class="tdot"></div></div>';
  box.appendChild(d); box.scrollTop=box.scrollHeight;
}
function hideTypingIndicator() { var el=document.getElementById('typingWrap'); if(el)el.remove(); }

function sendQuick(text) {
  document.getElementById('quickQs').style.display='none';
  document.getElementById('chatInput').value=text;
  sendChat();
}

document.getElementById('chatInput').addEventListener('keydown', function(e){
  if(e.key==='Enter'){ e.preventDefault(); sendChat(); }
});

async function sendChat() {
  var inp = document.getElementById('chatInput');
  var btn = document.getElementById('chatSendBtn');
  var text = inp.value.trim();
  if (!text || chatBusy) return;
  inp.value = '';
  addChatMsg('user', text);
  chatHist.push({role:'user', content:text});
  chatBusy = true; btn.disabled = true;
  showTypingIndicator();
  try {
    var res = await fetch('https://api.anthropic.com/v1/messages', {
      method:'POST',
      headers:{'Content-Type':'application/json'},
      body:JSON.stringify({
        model:'claude-sonnet-4-20250514',
        max_tokens:1000,
        system:buildSysPrompt(),
        messages:chatHist
      })
    });
    var data = await res.json();
    var reply = (data.content && data.content[0] && data.content[0].text) ? data.content[0].text : 'ขออภัยครับ เกิดข้อผิดพลาด';
    hideTypingIndicator();
    addChatMsg('ai', reply);
    chatHist.push({role:'assistant', content:reply});
    if (chatHist.length > 20) chatHist = chatHist.slice(-20);
  } catch(e) {
    hideTypingIndicator();
    addChatMsg('ai', '⚠️ ขออภัยครับ ไม่สามารถเชื่อมต่อได้ กรุณาลองใหม่');
  }
  chatBusy = false; btn.disabled = false; inp.focus();
}

// INIT
renderCards();
</script>
</body>
</html>
