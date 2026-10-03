
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Salami Lateef Oriyomi — IT & Service Delivery Leadership</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@400;500;600;700&family=IBM+Plex+Sans:wght@400;500;600&family=IBM+Plex+Mono:wght@400;500&display=swap" rel="stylesheet">
<style>
  :root{
    --bg: #0A0F1C;
    --panel: #111A2E;
    --panel-hi: #16213B;
    --line: #24314F;
    --text: #E7ECF6;
    --text-dim: #8D99B3;
    --signal: #29E0B0;
    --signal-dim: #1A8F73;
    --alert: #FF7A54;
    --amber: #FFC259;
    --font-display: 'Space Grotesk', sans-serif;
    --font-body: 'IBM Plex Sans', sans-serif;
    --font-mono: 'IBM Plex Mono', monospace;
  }
  *{ box-sizing:border-box; margin:0; padding:0; }
  html{ scroll-behavior:smooth; }
  body{
    background: var(--bg);
    color: var(--text);
    font-family: var(--font-body);
    line-height:1.6;
    -webkit-font-smoothing:antialiased;
  }
  body::before{
    content:"";
    position:fixed; inset:0;
    background-image:
      linear-gradient(var(--line) 1px, transparent 1px),
      linear-gradient(90deg, var(--line) 1px, transparent 1px);
    background-size: 48px 48px;
    opacity:0.08;
    pointer-events:none;
    z-index:0;
  }
  .wrap{ max-width: 900px; margin:0 auto; padding: 0 28px 80px; position:relative; z-index:1; }

  /* ---------- HERO / STATUS HEADER ---------- */
  header.hero{
    padding: 56px 0 40px;
    border-bottom: 1px solid var(--line);
  }
  .status-row{
    display:flex; align-items:center; gap:10px;
    font-family: var(--font-mono);
    font-size: 12px;
    letter-spacing: 0.12em;
    color: var(--signal);
    text-transform: uppercase;
    margin-bottom: 22px;
  }
  .dot{
    width:8px; height:8px; border-radius:50%;
    background: var(--signal);
    box-shadow: 0 0 0 0 rgba(41,224,176,0.6);
    animation: pulse-dot 2s infinite;
  }
  @keyframes pulse-dot{
    0%{ box-shadow: 0 0 0 0 rgba(41,224,176,0.5); }
    70%{ box-shadow: 0 0 0 8px rgba(41,224,176,0); }
    100%{ box-shadow: 0 0 0 0 rgba(41,224,176,0); }
  }
  h1.name{
    font-family: var(--font-display);
    font-weight: 700;
    font-size: clamp(34px, 6vw, 56px);
    letter-spacing: -0.02em;
    line-height: 1.05;
    opacity:0;
    transform: translateY(14px);
    animation: rise 0.7s ease-out forwards 0.15s;
  }
  .role{
    font-family: var(--font-display);
    font-weight: 500;
    font-size: clamp(15px, 2.4vw, 19px);
    color: var(--signal);
    margin-top: 10px;
    opacity:0;
    transform: translateY(14px);
    animation: rise 0.7s ease-out forwards 0.3s;
  }
  .contact-line{
    margin-top: 20px;
    display:flex; flex-wrap:wrap; gap: 6px 18px;
    font-family: var(--font-mono);
    font-size: 12.5px;
    color: var(--text-dim);
    opacity:0;
    transform: translateY(14px);
    animation: rise 0.7s ease-out forwards 0.45s;
  }
  .contact-line a{ color: var(--text-dim); text-decoration:none; border-bottom:1px dotted var(--line); }
  .contact-line a:hover{ color: var(--signal); border-color: var(--signal); }
  @keyframes rise{ to{ opacity:1; transform: translateY(0); } }

  /* ---------- SECTION SCAFFOLD ---------- */
  section{ padding: 44px 0; border-bottom: 1px solid var(--line); }
  section:last-of-type{ border-bottom:none; }
  .sec-head{
    display:flex; align-items:baseline; gap:14px;
    margin-bottom: 26px;
  }
  .sec-tag{
    font-family: var(--font-mono);
    font-size: 11px;
    color: var(--text-dim);
    letter-spacing: 0.1em;
  }
  .sec-title{
    font-family: var(--font-display);
    font-weight: 600;
    font-size: 22px;
    letter-spacing: -0.01em;
  }
  .sec-rule{ flex:1; height:1px; background: var(--line); }

  .reveal{
    opacity:0; transform: translateY(20px);
    transition: opacity 0.6s ease, transform 0.6s ease;
  }
  .reveal.visible{ opacity:1; transform: translateY(0); }

  /* ---------- PROFILE ---------- */
  .profile p{ color: var(--text); font-size: 15.5px; max-width: 74ch; }
  .profile strong{ color: var(--signal); font-weight:600; }

  /* ---------- COMPETENCY SIGNAL BARS ---------- */
  .comp-grid{
    display:grid; grid-template-columns: repeat(auto-fit, minmax(230px,1fr));
    gap: 14px 28px;
  }
  .comp-item{ font-size: 13.5px; }
  .comp-name{ display:flex; justify-content:space-between; margin-bottom:6px; color: var(--text); }
  .comp-name span.lvl{ font-family: var(--font-mono); color: var(--text-dim); font-size:11px; }
  .comp-bar{
    height: 5px; background: var(--panel-hi); border-radius: 3px; overflow:hidden;
    border: 1px solid var(--line);
  }
  .comp-fill{
    height: 100%;
    background: linear-gradient(90deg, var(--signal-dim), var(--signal));
    width: 0%;
    border-radius: 3px;
    transition: width 1.1s cubic-bezier(.2,.8,.2,1);
  }
  .comp-item.visible .comp-fill{ width: var(--fill); }

  /* ---------- EXPERIENCE TIMELINE (NETWORK TRACE) ---------- */
  .trace{ position:relative; padding-left: 30px; }
  .trace::before{
    content:"";
    position:absolute; left:6px; top:6px; bottom:6px; width:1px;
    background: linear-gradient(var(--signal), var(--line) 60%, transparent);
  }
  .node{
    position:relative;
    padding-bottom: 40px;
  }
  .node:last-child{ padding-bottom:0; }
  .node::before{
    content:"";
    position:absolute; left:-30px; top:5px;
    width:13px; height:13px; border-radius:50%;
    background: var(--bg);
    border: 2px solid var(--signal);
  }
  .node.visible::before{
    animation: node-pulse 1.6s ease-out 1;
  }
  @keyframes node-pulse{
    0%{ box-shadow: 0 0 0 0 rgba(41,224,176,0.55); }
    100%{ box-shadow: 0 0 0 12px rgba(41,224,176,0); }
  }
  .node-head{
    display:flex; flex-wrap:wrap; justify-content:space-between; align-items:baseline; gap:8px;
    margin-bottom: 4px;
  }
  .node-role{ font-family: var(--font-display); font-weight:600; font-size: 17px; }
  .node-org{ color: var(--signal); font-size: 13.5px; font-weight:500; }
  .node-date{
    font-family: var(--font-mono); font-size: 11.5px; color: var(--text-dim);
    white-space:nowrap;
  }
  .node ul{ margin-top: 10px; padding-left: 18px; }
  .node li{ font-size: 14px; color: var(--text-dim); margin-bottom: 7px; }
  .node li::marker{ color: var(--signal); }
  .node li strong{ color: var(--text); font-weight:600; }

  /* ---------- PROJECTS ---------- */
  .proj-grid{ display:grid; grid-template-columns: repeat(auto-fit,minmax(260px,1fr)); gap:16px; }
  .proj-card{
    background: var(--panel);
    border: 1px solid var(--line);
    border-radius: 8px;
    padding: 18px 20px;
    transition: transform 0.25s ease, border-color 0.25s ease, box-shadow 0.25s ease;
  }
  .proj-card:hover{
    transform: translateY(-3px);
    border-color: var(--signal-dim);
    box-shadow: 0 10px 30px -14px rgba(41,224,176,0.35);
  }
  .proj-title{ font-family: var(--font-display); font-weight:600; font-size:15px; margin-bottom:6px; }
  .proj-year{ font-family: var(--font-mono); color: var(--signal); font-size:11px; }
  .proj-card p{ font-size: 13.5px; color: var(--text-dim); margin-top:8px; }

  /* ---------- EDU / CERTS ---------- */
  .cred-grid{ display:grid; grid-template-columns: 1fr 1fr; gap: 34px; }
  @media (max-width: 620px){ .cred-grid{ grid-template-columns: 1fr; } }
  .cred-grid h3{
    font-family: var(--font-mono); font-size:11px; letter-spacing:0.1em;
    color: var(--text-dim); text-transform:uppercase; margin-bottom:14px;
  }
  .cred-grid ul{ list-style:none; }
  .cred-grid li{
    font-size: 14px; padding: 9px 0; border-bottom: 1px dashed var(--line);
    display:flex; align-items:center; gap:10px;
  }
  .cred-grid li:last-child{ border-bottom:none; }
  .cred-grid li::before{ content:"▸"; color: var(--signal); font-size:11px; }

  /* ---------- PUBLICATIONS ---------- */
  .pub{ font-size:14px; color: var(--text-dim); margin-bottom:10px; padding-left:18px; position:relative; }
  .pub::before{ content:"“"; position:absolute; left:0; color:var(--signal); font-family:var(--font-display); }

  /* ---------- REFEREES ---------- */
  .ref-grid{ display:grid; grid-template-columns: repeat(auto-fit,minmax(230px,1fr)); gap:16px; }
  .ref-card{
    background: var(--panel);
    border:1px solid var(--line);
    border-radius:8px;
    padding:16px 18px;
  }
  .ref-name{ font-family: var(--font-display); font-weight:600; font-size:14.5px; }
  .ref-title{ font-size:12.5px; color: var(--signal); margin-top:2px; }
  .ref-org{ font-size:12.5px; color: var(--text-dim); margin-top:2px; }
  .ref-contact{ font-family: var(--font-mono); font-size:11px; color: var(--text-dim); margin-top:10px; word-break:break-word; }

  footer{
    text-align:center; padding: 40px 0 10px; font-family: var(--font-mono);
    font-size: 11px; color: var(--text-dim); letter-spacing:0.08em;
  }

  @media print{
    body::before{ display:none; }
    .reveal{ opacity:1 !important; transform:none !important; }
    .comp-fill{ width: var(--fill) !important; }
  }

  @media (prefers-reduced-motion: reduce){
    *{ animation: none !important; transition: none !important; }
    .reveal{ opacity:1; transform:none; }
    .comp-fill{ width: var(--fill) !important; }
  }
</style>
</head>
<body>

<div class="wrap">

  <header class="hero">
    <div class="status-row"><span class="dot"></span> System status: operational — 10 years uptime</div>
    <h1 class="name">Salami Lateef Oriyomi</h1>
    <div class="role">IT &amp; Service Delivery Leadership — Infrastructure · Governance · Telecom</div>
    <div class="contact-line">
      <span>4, Olaniyan Close, Igbo Oluwo Estate, Ikorodu, Lagos, Nigeria</span>
      <a href="tel:+2347031709743">+234 703 170 9743</a>
      <a href="tel:+2348028513367">+234 802 851 3367</a>
      <a href="mailto:slatheiph@gmail.com">slatheiph@gmail.com</a>
    </div>
  </header>

  <section class="profile reveal">
    <div class="sec-head"><span class="sec-tag">// 00</span><span class="sec-title">Executive Profile</span><span class="sec-rule"></span></div>
    <p>Results-driven technology leader with a decade of progressive experience across <strong>telecommunications and enterprise IT</strong> — spanning infrastructure engineering, service delivery, and IT governance. Proven record of aligning technology strategy with business objectives: optimizing infrastructure for efficiency and cost reduction, championing enterprise-wide cybersecurity, and embedding <strong>ITIL and PRINCE2</strong> governance frameworks across multi-country operations. Combines deep operational credibility (NOC, infrastructure, vendor and change management) with growing exposure to modern DevOps practices, including containerization with <strong>Docker and Kubernetes</strong>, to support infrastructure modernization. Positioned to lead technology strategy, infrastructure governance, and digital transformation at Head of Technology level.</p>
  </section>

  <section class="reveal">
    <div class="sec-head"><span class="sec-tag">// 01</span><span class="sec-title">Core Competencies</span><span class="sec-rule"></span></div>
    <div class="comp-grid">
      <div class="comp-item" style="--fill:95%"><div class="comp-name"><span>IT Strategy &amp; Technology Leadership</span></div><div class="comp-bar"><div class="comp-fill"></div></div></div>
      <div class="comp-item" style="--fill:92%"><div class="comp-name"><span>Infrastructure &amp; Asset Lifecycle Mgmt</span></div><div class="comp-bar"><div class="comp-fill"></div></div></div>
      <div class="comp-item" style="--fill:96%"><div class="comp-name"><span>ITIL v3 Service Management</span></div><div class="comp-bar"><div class="comp-fill"></div></div></div>
      <div class="comp-item" style="--fill:90%"><div class="comp-name"><span>PRINCE2 Project &amp; Change Governance</span></div><div class="comp-bar"><div class="comp-fill"></div></div></div>
      <div class="comp-item" style="--fill:94%"><div class="comp-name"><span>IT Change Advisory Board (CAB) Leadership</span></div><div class="comp-bar"><div class="comp-fill"></div></div></div>
      <div class="comp-item" style="--fill:88%"><div class="comp-name"><span>Vendor &amp; SLA / OLA Management</span></div><div class="comp-bar"><div class="comp-fill"></div></div></div>
      <div class="comp-item" style="--fill:85%"><div class="comp-name"><span>Enterprise Cybersecurity (Security+)</span></div><div class="comp-bar"><div class="comp-fill"></div></div></div>
      <div class="comp-item" style="--fill:55%"><div class="comp-name"><span>DevOps Fundamentals — Docker &amp; Kubernetes</span></div><div class="comp-bar"><div class="comp-fill"></div></div></div>
      <div class="comp-item" style="--fill:87%"><div class="comp-name"><span>Disaster Recovery &amp; Business Continuity</span></div><div class="comp-bar"><div class="comp-fill"></div></div></div>
      <div class="comp-item" style="--fill:93%"><div class="comp-name"><span>Telecom Network Ops (NOC, LTE, Transmission)</span></div><div class="comp-bar"><div class="comp-fill"></div></div></div>
    </div>
  </section>

  <section class="reveal">
    <div class="sec-head"><span class="sec-tag">// 02</span><span class="sec-title">Professional Experience</span><span class="sec-rule"></span></div>
    <div class="trace">

      <div class="node">
        <div class="node-head">
          <div><div class="node-role">Senior ICT Engineer / IT Client Manager — West Africa</div><div class="node-org">L M Ericsson Nigeria</div></div>
          <div class="node-date">Nov 2017 – Present</div>
        </div>
        <ul>
          <li>Lead full lifecycle management of <strong>IT infrastructure</strong> (servers, network, hardware) across a multi-country region, aligning asset strategy with ITIL best practice.</li>
          <li>Chair the <strong>IT Change Advisory Board (CAB)</strong> with sole authorization responsibility, evaluating all changes for risk, financial viability, and operational impact.</li>
          <li>Govern third-party IT service delivery, holding vendors accountable to <strong>SLAs</strong> for uptime, performance, and maintainability; negotiate warranty and support agreements.</li>
          <li>Develop and enforce configuration management processes, reducing configuration drift and improving system stability.</li>
          <li>Driving infrastructure modernization by introducing <strong>Docker and Kubernetes</strong> concepts into infrastructure planning, building foundational DevOps capability.</li>
          <li>Control IT asset stock end-to-end (procurement, cascade, refresh, decommissioning) to maximize ROI and minimize TCO.</li>
        </ul>
      </div>

      <div class="node">
        <div class="node-head">
          <div><div class="node-role">System Administrator &amp; Support Specialist</div><div class="node-org">HP (Excis HPE Service Account)</div></div>
          <div class="node-date">Sept 2016 – Nov 2017</div>
        </div>
        <ul>
          <li>Delivered <strong>Tier 2/3</strong> onsite and remote technical support, resolving critical incidents impacting internet availability and core business functions.</li>
          <li>Built strong client relationships through high-value technical consultation, improving customer satisfaction and trust.</li>
        </ul>
      </div>

      <div class="node">
        <div class="node-head">
          <div><div class="node-role">NOC Engineer — Incident &amp; Network Operations Management</div><div class="node-org">L M Ericsson Nigeria</div></div>
          <div class="node-date">Apr 2014 – Jul 2016</div>
        </div>
        <ul>
          <li>Directed end-to-end lifecycle of Ericsson's IT infrastructure estate — procurement, configuration, upgrades, decommissioning.</li>
          <li>Governed IT service delivery for Ericsson Nigeria and external partners, holding vendors to SLAs for availability, reliability, performance.</li>
          <li>Managed and coordinated <strong>incident resolution</strong> within SLA/OLA, maintaining stakeholder communication and accurate failure reporting.</li>
          <li>Spearheaded IT change management, performing risk and impact analysis for seamless transitions.</li>
          <li>Tracked all IT assets for 100% warranty and maintenance coverage, safeguarding disaster recovery readiness.</li>
          <li>Coordinated escalation across Field Support, Switch, Transmission, LAN/WAN, Satellite, Fibre, and Systems Support teams.</li>
        </ul>
      </div>

      <div class="node">
        <div class="node-head">
          <div><div class="node-role">Telecom Engineer / Field Support Engineer</div><div class="node-org">HP Service Center (Sechaba, HP Partner)</div></div>
          <div class="node-date">Jan 2013 – Mar 2014</div>
        </div>
        <ul>
          <li>Led migration of IT infrastructure from Ericsson's old office to a new location, including server configuration, backup, and data restoration.</li>
          <li>Managed the company's <strong>Storage Area Network (SAN)</strong>, plus network, security, and endpoint infrastructure.</li>
          <li>Installed and integrated 2G/3G systems (DUG, DUW), configured ASC/RET/TMA, supported TCU/SIU integration; diagnosed and cleared site alarms.</li>
          <li>Configured and provisioned Aviat transmission systems (WTM6000, TR6500 Long Haul Radios); remote monitoring via One TM/One FM.</li>
          <li>Contributed to the FY13/FY14 <strong>MTN Nigeria</strong> project, managing cut-over transitions (2P/6P to 20P Magazine) including E1 mapping and onsite supervision.</li>
        </ul>
      </div>

    </div>
  </section>

  <section class="reveal">
    <div class="sec-head"><span class="sec-tag">// 03</span><span class="sec-title">Key Projects</span><span class="sec-rule"></span></div>
    <div class="proj-grid">
      <div class="proj-card"><div class="proj-year">Lagos, 2019</div><div class="proj-title">MWP Re-Imaging (Windows)</div><p>Re-imaged and deployed 500+ workstations at LM Ericsson Nigeria, migrating from MWP II to MWP-C/MWP-M.</p></div>
      <div class="proj-card"><div class="proj-year">Lagos, 2017</div><div class="proj-title">Ericsson Site Relocation</div><p>Managed decommissioning and re-commissioning of IT infrastructure between Ericsson Nigeria offices, including all technical amendments.</p></div>
      <div class="proj-card"><div class="proj-year">2014</div><div class="proj-title">Asset Swap &amp; Re-Imaging</div><p>Upgraded HP hardware fleet (8460p/8470p → 9470m/9480m) for 270 Ericsson users; re-imaged 300+ workstations from MWP I to MWP II.</p></div>
      <div class="proj-card"><div class="proj-year">2013</div><div class="proj-title">Infrastructure Upgrade &amp; Decommission</div><p>Co-managed office relocation decommissioning/re-commissioning; deployed 500 HP Field Support units for MTN Nigeria; upgraded 300 users to Windows 7.</p></div>
    </div>
  </section>

  <section class="reveal">
    <div class="sec-head"><span class="sec-tag">// 04</span><span class="sec-title">Education &amp; Certifications</span><span class="sec-rule"></span></div>
    <div class="cred-grid">
      <div>
        <h3>Education</h3>
        <ul>
          <li>MBA, Business Analysis &amp; Strategy — Caleb University, Lagos</li>
          <li>B.Sc. Computer Science — Lagos State University, Ojo, Lagos</li>
        </ul>
        <h3 style="margin-top:22px">Publications</h3>
        <div class="pub">Multilevel Security in Distributed Database — written journal, 2012</div>
        <div class="pub">Cybersecurity for Everyone: Threat Actor Oil Rigs — course paper</div>
      </div>
      <div>
        <h3>Certifications</h3>
        <ul>
          <li>CompTIA Security+ Certified</li>
          <li>ITIL v3 Certified — IT Service Management</li>
          <li>PRINCE2 Foundation &amp; Practitioner Certified</li>
          <li>LTE L14 Operations, Configuration &amp; Troubleshooting — Ericsson Academy</li>
          <li>Cybersecurity for Everyone — University of Maryland</li>
          <li>Information Systems Audit, Control &amp; Assurance — HKUST</li>
          <li>VCE Certified Professional Associate</li>
          <li>Linux and Linux System Administration Certified</li>
          <li>IBM AI Developer (in-view)</li>
        </ul>
      </div>
    </div>
  </section>

  <section class="reveal">
    <div class="sec-head"><span class="sec-tag">// 05</span><span class="sec-title">Referees</span><span class="sec-rule"></span></div>
    <div class="ref-grid">
      <div class="ref-card">
        <div class="ref-name">Mr Yinka Atunda</div>
        <div class="ref-title">Head of IT Department</div>
        <div class="ref-org">ATC (American Tower Company), Lagos, Nigeria</div>
        <div class="ref-contact">atandasteve@yahoo.com<br>0808 718 5387</div>
      </div>
      <div class="ref-card">
        <div class="ref-name">Mr Temitayo Idowu</div>
        <div class="ref-title">Senior Vice President, Operations</div>
        <div class="ref-org">New Jersey, United States</div>
        <div class="ref-contact">idowu.temitayo@gmail.com<br>0812 998 9292</div>
      </div>
      <div class="ref-card">
        <div class="ref-name">Mr Peter Olusoji Ogundele</div>
        <div class="ref-title">Country Manager</div>
        <div class="ref-org">L M Ericsson Nigeria Limited</div>
        <div class="ref-contact">peter.olusoji.ogundele@ericsson.com<br>+234 802 222 1374</div>
      </div>
    </div>
  </section>

  <footer>Last synced — 2026</footer>

</div>

<script>
  const revealEls = document.querySelectorAll('.reveal, .node, .comp-item');
  const io = new IntersectionObserver((entries) => {
    entries.forEach(e => {
      if(e.isIntersecting){
        e.target.classList.add('visible');
        io.unobserve(e.target);
      }
    });
  }, { threshold: 0.15 });
  revealEls.forEach(el => io.observe(el));
</script>

</body>
</html>
