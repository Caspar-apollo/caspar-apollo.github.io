<html lang="de">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<title>Bad und Anstrich Musterstraße</title>
<style>
:root{
  --ink:#1a1a1a; --accent:#e83a50; --bg:#efedea; --paper:#ffffff;
  --border:#e0ddd8; --rule:#e8e6e2; --muted:#888888; --subtle:#555555;
  --tint:#f5f4f0; --warn-bg:#fff5f6; --bubble:#f2f0ed; --shell:#e6e3df;
}
@media (prefers-color-scheme: dark){
  :root:not([data-theme="light"]){
    --ink:#f2f0ed; --accent:#ff5f74; --bg:#121110; --paper:#1e1d1c;
    --border:#37342f; --rule:#312e2a; --muted:#9a948c; --subtle:#b8b2a9;
    --tint:#262421; --warn-bg:#2b1b1e; --bubble:#272522; --shell:#1a1918;
  }
}
:root[data-theme="dark"]{
  --ink:#f2f0ed; --accent:#ff5f74; --bg:#121110; --paper:#1e1d1c;
  --border:#37342f; --rule:#312e2a; --muted:#9a948c; --subtle:#b8b2a9;
  --tint:#262421; --warn-bg:#2b1b1e; --bubble:#272522; --shell:#1a1918;
}
*{box-sizing:border-box}
body{
  font-family:'Segoe UI', system-ui, -apple-system, sans-serif;
  background:var(--bg); color:var(--ink);
  line-height:1.6; font-size:0.95rem; margin:0; padding:1.5rem 1rem 3rem;
  -webkit-font-smoothing:antialiased;
}
.note{max-width:760px; margin:0 auto .9rem; font-size:.72rem; font-weight:700;
  letter-spacing:.12em; text-transform:uppercase; color:var(--muted); padding:0 .25rem}

/* Chat */
.chat{max-width:760px; margin:0 auto; background:var(--shell);
  border:1px solid var(--border); border-radius:10px; padding:1.25rem 1.25rem 0;
  display:flex; flex-direction:column; gap:.9rem}
.msg{max-width:86%; font-size:.9rem}
.msg.me{align-self:flex-end; background:var(--bubble); border:1px solid var(--border);
  border-radius:12px 12px 3px 12px; padding:.6rem .9rem; color:var(--subtle)}
.msg.bot{align-self:flex-start; color:var(--subtle); padding:0 .2rem}
.composer{border-top:1px solid var(--border); margin:.5rem -1.25rem 0; padding:.85rem 1.25rem;
  display:flex; align-items:center; gap:.6rem; color:var(--muted); font-size:.85rem}
.composer .field{flex:1; background:var(--paper); border:1px solid var(--border);
  border-radius:16px; padding:.5rem .9rem}

/* Widget */
.widget{background:var(--paper); border:1px solid var(--ink); border-radius:6px; overflow:hidden}
.w-head{padding:1.4rem 1.6rem 1.2rem; border-bottom:2px solid var(--ink)}
.eyebrow{font-size:.68rem; font-weight:700; letter-spacing:.14em; text-transform:uppercase; color:var(--accent); margin-bottom:.4rem}
.w-head h1{font-size:1.35rem; font-weight:700; margin:0 0 .25rem; letter-spacing:-.01em; text-wrap:balance}
.w-head .addr{font-size:.82rem; color:var(--muted)}
.w-body{padding:1.4rem 1.6rem}
h2{font-size:.68rem; font-weight:700; letter-spacing:.12em; text-transform:uppercase;
  color:var(--muted); border-bottom:1px solid var(--rule); padding-bottom:.3rem; margin:1.7rem 0 .8rem}
h2:first-child{margin-top:0}
p{margin:0 0 .75rem}
.lead{font-size:1rem; max-width:58ch}

/* Räume */
.rooms{display:flex; flex-direction:column; border:1px solid var(--rule); border-radius:3px; overflow:hidden}
.rw{display:grid; grid-template-columns:1.4rem 1fr auto; gap:.85rem; align-items:center;
  padding:.62rem .9rem; border-bottom:1px solid var(--rule); cursor:pointer; background:none;
  border-left:none; border-right:none; border-top:none; width:100%; text-align:left; font:inherit; color:inherit}
.rw:last-child{border-bottom:none}
.rw:nth-child(odd){background:var(--tint)}
.rw:focus-visible{outline:2px solid var(--accent); outline-offset:-2px}
.box{width:1.05rem; height:1.05rem; border:1.5px solid var(--ink); border-radius:2px;
  display:grid; place-items:center; font-size:.72rem; color:var(--paper); background:var(--ink)}
.rw[aria-pressed="false"] .box{background:transparent; color:transparent; border-color:var(--muted)}
.rw[aria-pressed="false"]{opacity:.5}
.rn{font-weight:600; font-size:.9rem}
.rn span{display:block; font-weight:400; font-size:.76rem; color:var(--muted); line-height:1.45; margin-top:.1rem}
.re{font-variant-numeric:tabular-nums; font-weight:600; white-space:nowrap; font-size:.92rem}
.hint{font-size:.76rem; color:var(--muted); margin-top:.5rem}

/* Kalender */
.cal{border:1px solid var(--rule); border-radius:3px; padding:.9rem 1rem}
.cal-top{display:flex; justify-content:space-between; align-items:baseline; margin-bottom:.7rem}
.cal-top .m{font-weight:700; font-size:.92rem}
.cal-top .legend{font-size:.72rem; color:var(--muted)}
.grid{display:grid; grid-template-columns:repeat(7,1fr); gap:.2rem}
.dow{font-size:.68rem; color:var(--muted); text-align:center; padding-bottom:.25rem; font-weight:700; letter-spacing:.06em}
.day{aspect-ratio:1; display:grid; place-items:center; border-radius:3px; font-size:.82rem;
  border:1px solid transparent; background:none; font-family:inherit; color:var(--muted); font-variant-numeric:tabular-nums}
.day.free{background:var(--tint); color:var(--ink); cursor:pointer; border-color:var(--rule)}
.day.free:hover{border-color:var(--ink)}
.day.free:focus-visible{outline:2px solid var(--accent); outline-offset:1px}
.day.sel{background:var(--ink); color:var(--paper); border-color:var(--ink); font-weight:700}
.day.span{background:var(--warn-bg); border-color:var(--accent); color:var(--ink)}
.day.out{opacity:.35}
.cal-out{display:flex; justify-content:space-between; gap:1rem; flex-wrap:wrap;
  margin-top:.8rem; padding-top:.7rem; border-top:1px solid var(--rule); font-size:.85rem}
.cal-out b{display:block; font-size:.95rem}
.cal-out .lbl{font-size:.7rem; letter-spacing:.1em; text-transform:uppercase; color:var(--muted)}

/* Preis + CTA */
.total{display:flex; justify-content:space-between; align-items:flex-end; gap:1rem;
  border-top:1px solid var(--ink); padding-top:1rem; margin-top:1.6rem}
.total .lbl{font-size:.78rem; color:var(--subtle)}
.total .big{font-size:2.1rem; font-weight:700; font-variant-numeric:tabular-nums; letter-spacing:-.02em; line-height:1.1}
.total .vat{font-size:.76rem; color:var(--muted); text-align:right}
.cta{display:block; width:100%; margin-top:1rem; background:var(--accent); color:#fff;
  border:none; border-radius:4px; padding:.85rem 1rem; font-size:1rem; font-weight:600; font-family:inherit; cursor:pointer}
.cta:hover{filter:brightness(.94)}
.cta:focus-visible{outline:2px solid var(--ink); outline-offset:2px}
.cta[disabled]{background:var(--muted); cursor:not-allowed}
.sub-cta{font-size:.76rem; color:var(--muted); text-align:center; margin-top:.5rem}
.done{display:none; border:1px solid var(--accent); background:var(--warn-bg);
  border-radius:4px; padding:1rem 1.1rem; margin-top:1rem; font-size:.9rem}
.done.on{display:block}
.done b{display:block; margin-bottom:.2rem}

/* Enthalten / Nicht enthalten */
.scope{display:grid; grid-template-columns:1fr 1fr; gap:1rem}
@media (max-width:600px){ .scope{grid-template-columns:1fr} .msg{max-width:96%} }
.panel{border-radius:4px; overflow:hidden; display:flex; flex-direction:column}
.panel.in{border:1px solid var(--ink)}
.panel.out{border:1px dashed var(--border)}
.panel-head{display:flex; align-items:center; gap:.45rem; padding:.5rem .85rem;
  font-size:.74rem; font-weight:700; letter-spacing:.06em; text-transform:uppercase}
.panel.in .panel-head{background:var(--ink); color:var(--paper)}
.panel.out .panel-head{background:var(--tint); color:var(--muted)}
.mark{width:1.05rem; height:1.05rem; border-radius:50%; display:grid; place-items:center;
  font-size:.7rem; font-weight:700; flex:none}
.panel.in .mark{background:var(--paper); color:var(--ink)}
.panel.out .mark{background:var(--muted); color:var(--tint)}
.panel ul{list-style:none; margin:0; padding:.7rem .85rem; display:flex; flex-direction:column; gap:.42rem}
.panel li{font-size:.85rem; padding-left:1.15rem; position:relative; line-height:1.5}
.panel.in li::before{content:"✓"; position:absolute; left:0; top:0; font-weight:700; color:var(--ink)}
.panel.out li::before{content:"–"; position:absolute; left:.1rem; top:0; font-weight:700; color:var(--muted)}
.panel.out li{color:var(--subtle)}

.callout{border-left:3px solid var(--ink); background:var(--tint); padding:.8rem 1rem; border-radius:0 3px 3px 0; font-size:.88rem}
.callout.accent{border-left-color:var(--accent); background:var(--warn-bg)}
.callout p:last-child{margin-bottom:0}
.callout .t{font-weight:700; display:block; margin-bottom:.15rem}
.assume{font-size:.88rem}
.assume dt{font-weight:600; margin-top:.5rem}
.assume dd{margin:0; color:var(--subtle)}
.phases{display:flex; flex-wrap:wrap; gap:.4rem; font-size:.76rem; color:var(--subtle); margin-top:.7rem}
.ph{background:var(--tint); border:1px solid var(--rule); border-radius:3px; padding:.28rem .55rem}
.ph b{font-weight:700; color:var(--ink)}
@media (prefers-reduced-motion:reduce){*{transition:none!important}}
</style>
</head>
<body>

<div class="note">Mockup · Kundenangebot im Chat · Wohnung 44 m²</div>

<div class="chat">

  <div class="msg me">Hier sind Fotos und der Grundriss. Das Bad soll komplett neu, alle Wände und Decken gestrichen werden, Türen und Zargen mit. Elektrik und Sanitär bitte einmal durchsehen. Der Boden bleibt, die Küche auch.</div>
  <div class="msg bot">Danke. Ich komme auf 44 m² in fünf Räumen, Bad 2,9 m², rund 115 m² streichbare Wandfläche, fünf Türen mit Zarge. Die Wände sind glatt gestrichen, keine Tapete — das spart Untergrundarbeit. Zwei Fragen zum Bad: Dusche oder Wanne, und soll die Dusche eine Abtrennung bekommen?</div>
  <div class="msg me">Dusche, 80 × 80. Mit Glastür, keine Wanne.</div>
  <div class="msg bot">Gut — mit Abtrennung bleibt die hohe Abdichtungsklasse auf die Duschzone begrenzt, das spart rund 200 €. Hier ist Ihr Festpreis:</div>

  <div class="widget">
    <div class="w-head">
      <div class="eyebrow">Festpreis-Angebot · gültig 14 Tage</div>
      <h1>Neues Bad, frisch gestrichene Wohnung</h1>
      <div class="addr">Musterstraße 14, 2. OG links · 44 m² · Angebot 2026-0147</div>
    </div>

    <div class="w-body">
      <p class="lead">Wir bauen Ihr Bad vollständig neu — vom Rückbau über die Abdichtung nach
        DIN 18534 bis zu Fliesen, Wand-WC, Waschtisch und Dusche. Alle Wände und Decken der Wohnung
        werden gestrichen, Türblätter und Zargen lackiert. Elektro- und Sanitärinstallation prüfen
        wir und messen die Anlage nach Norm durch. Boden und Küche bleiben und werden geschützt.</p>

      <h2>Räume</h2>
      <div class="rooms" id="rooms">
        <button class="rw" type="button" aria-pressed="true" data-eur="13578.21" data-core="1">
          <span class="box">✓</span>
          <span class="rn">Bad
            <span>2,9 m² · komplett neu: Rückbau, Vorwand, Abdichtung, 19,4 m² Wand- und 2,9 m² Bodenfliesen,
              Wand-WC spülrandlos, Waschtisch, Dusche 80 × 80 mit Gleittür, alle Armaturen, Elektro im Feuchtraum</span></span>
          <span class="re">13.578,21 €</span>
        </button>
        <button class="rw" type="button" aria-pressed="true" data-eur="2094.40">
          <span class="box">✓</span>
          <span class="rn">Schlafzimmer
            <span>13,5 m² · Wände, Decke, Zierprofile, 2 Fensterleibungen, 1 Zarge · Steckdosen und Schalter geprüft</span></span>
          <span class="re">2.094,40 €</span>
        </button>
        <button class="rw" type="button" aria-pressed="true" data-eur="2040.85">
          <span class="box">✓</span>
          <span class="rn">Wohnzimmer
            <span>14,7 m² · Wände, Decke, Zierprofile, Fensterleibung, 1 Zarge · Steckdosen und Schalter geprüft</span></span>
          <span class="re">2.040,85 €</span>
        </button>
        <button class="rw" type="button" aria-pressed="true" data-eur="1600.55">
          <span class="box">✓</span>
          <span class="rn">Küche
            <span>8,5 m² · abwaschbare Latexfarbe, neue Spülenarmatur · Einbauküche bleibt stehen und wird abgedeckt</span></span>
          <span class="re">1.600,55 €</span>
        </button>
        <button class="rw" type="button" aria-pressed="true" data-eur="1178.10">
          <span class="box">✓</span>
          <span class="rn">Flur
            <span>4,4 m² · Wände, Decke, Zierprofile, Wohnungstür innen lackiert</span></span>
          <span class="re">1.178,10 €</span>
        </button>
      </div>
      <div class="hint" id="roomHint">Räume abwählen, wenn Sie das Budget anpassen möchten — der Preis rechnet sich sofort neu.</div>

      <h2>Wann sollen wir kommen?</h2>
      <div class="cal">
        <div class="cal-top">
          <span class="m">Oktober 2026</span>
          <span class="legend">frei wählbar · grau = belegt</span>
        </div>
        <div class="grid" id="calGrid"></div>
        <div class="cal-out">
          <div><span class="lbl">Beginn</span><b id="startTxt">Mo, 5. Oktober</b></div>
          <div><span class="lbl">Fertig</span><b id="endTxt">Fr, 16. Oktober</b></div>
          <div><span class="lbl">Dauer</span><b id="durTxt">10 Werktage</b></div>
        </div>
        <div class="phases">
          <span class="ph"><b>Tag 1</b> Sanitär und Elektro, Rohinstallation</span>
          <span class="ph"><b>Tag 2</b> Vorwand geschlossen</span>
          <span class="ph"><b>Tag 3–5</b> Fliesen und Abdichtung</span>
          <span class="ph"><b>Tag 6–8</b> Malerarbeiten</span>
          <span class="ph"><b>Tag 9–10</b> Endmontage und Messung</span>
        </div>
      </div>

      <div class="total">
        <div>
          <div class="lbl">Festpreis, alles inklusive</div>
          <div class="big" id="grand">20.492,11 €</div>
        </div>
        <div class="vat">inkl. 19 % MwSt.<br><span id="net">17.220,26 €</span> netto</div>
      </div>

      <button class="cta" id="order" type="button">Leistung beauftragen</button>
      <div class="sub-cta">Verbindlich zum Festpreis · 14 Tage Widerrufsrecht</div>

      <div class="done" id="done">
        <b>Beauftragt.</b>
        <span id="doneTxt">Wir haben den Termin für Sie reserviert und melden uns mit der Auftragsbestätigung.</span>
      </div>

      <h2>Leistungsumfang</h2>
      <div class="scope">
        <div class="panel in">
          <div class="panel-head"><span class="mark">✓</span> Im Festpreis enthalten</div>
          <ul>
            <li>Bad vollständig zurückgebaut und entsorgt</li>
            <li>Verbundabdichtung nach DIN 18534, Wand- und Bodenfliesen</li>
            <li>Wand-WC spülrandlos mit Vorwandmodul, Waschtisch, Dusche mit Gleittür</li>
            <li>Alle Armaturen im Bad, neue Spülenarmatur in der Küche</li>
            <li>Wände und Decken aller Räume, zwei Anstriche, wischbeständig</li>
            <li>Küche und Bad mit abwaschbarer Latexfarbe</li>
            <li>Fünf Türzargen und Türblätter lackiert</li>
            <li>Fehlerstromschutzschalter nachgerüstet, Bad-Elektrik neu</li>
            <li>Messung und Prüfung nach DIN&nbsp;VDE&nbsp;0100-600 mit Protokoll</li>
            <li>Boden, Küche, Heizkörper, Fenster und Leuchten abgedeckt</li>
            <li>Endreinigung, Bauschutt mitgenommen</li>
            <li>Ein Ansprechpartner für alle fünf Gewerke</li>
          </ul>
        </div>
        <div class="panel out">
          <div class="panel-head"><span class="mark">–</span> Nicht enthalten</div>
          <ul>
            <li>Bodenbelag — Ihr Parkett bleibt unverändert</li>
            <li>Arbeiten an der Einbauküche außer der Spülenarmatur</li>
            <li>Leuchten und Schalterprogramm — Auslass und Anschluss sind enthalten</li>
            <li>Heizkörper lackieren oder tauschen</li>
            <li>Möbel ein- und ausräumen</li>
            <li>Arbeiten an tragenden Bauteilen</li>
            <li>Genehmigungen, Gebühren, Zwischenmiete</li>
          </ul>
        </div>
      </div>

      <div class="callout accent" style="margin-top:1.4rem">
        <span class="t">Ein Punkt, den wir noch nicht wissen können</span>
        <p><strong>Unterverteilung.</strong> Wir haben Ihre Elektroinstallation bisher nur auf Fotos
          gesehen. Zeigt die Messung am ersten Tag, dass die Unterverteilung erneuert werden muss,
          sind das 1.230 bis 2.140 € brutto zusätzlich. Wir melden das vor Ausführung an — Sie
          entscheiden, wir fangen nicht einfach an.</p>
      </div>

      <h2>Wovon wir ausgehen</h2>
      <dl class="assume">
        <dt>Zustand der Wände</dt>
        <dd>Glatt gestrichen, keine Tapete, einzelne Dübellöcher. Keine Risse, keine Feuchteschäden,
          keine Nikotinspuren. Fleckspachtelung genügt.</dd>
        <dt>Maße</dt>
        <dd>44 m² Wohnfläche, 2,55 m Raumhöhe, rund 115 m² streichbare Wandfläche — aus Ihren Fotos
          und dem Grundriss ermittelt, ohne Ortstermin.</dd>
        <dt>Bad</dt>
        <dd>2,9 m², Dusche 80 × 80 mit Gleittür. Die Abtrennung begrenzt die hohe
          Abdichtungsklasse auf die Duschzone. Ohne sie steigt sie auf die gesamte Bodenfläche.</dd>
        <dt>Übergabe</dt>
        <dd>Die Wohnung ist leer geräumt. Der Bodenbelag und die Einbauküche bleiben und werden
          über die gesamte Bauzeit geschützt.</dd>
      </dl>
      <p style="font-size:.88rem; margin-top:.6rem">Trifft etwas davon nicht zu, sagen wir Ihnen das
        <strong>vor Beginn</strong> und stimmen die Mehrkosten mit Ihnen ab — wir fangen nicht an und
        rechnen hinterher ab.</p>

      <h2>Was wir von Ihnen brauchen</h2>
      <div class="scope">
        <div class="panel in">
          <div class="panel-head"><span class="mark">✓</span> Bis zum Starttag</div>
          <ul>
            <li>Wohnung leer geräumt, Gardinen, Lampen und Bilder abgenommen</li>
            <li>Zugang ab 7 Uhr, Schlüsselübergabe eine Woche vorher</li>
            <li>Zugang zum Zählerschrank und zur Hauptverteilung</li>
            <li>Strom und Wasser nutzbar</li>
          </ul>
        </div>
        <div class="panel in">
          <div class="panel-head"><span class="mark">✓</span> Zehn Tage vorher</div>
          <ul>
            <li>Fliesen, Sanitärobjekte und Armaturen verbindlich gewählt</li>
            <li>Wandfarbe festgelegt — davon hängt die Materialbestellung ab</li>
            <li>Bekannte Schäden oder Feuchtigkeit genannt</li>
          </ul>
        </div>
      </div>

      <div class="callout accent" style="margin-top:1.4rem">
        <span class="t"><span id="taxBack">1.200,00 €</span> holen Sie über die Steuer zurück</span>
        <p>Der Lohnanteil beträgt <span id="laborTxt">12.705,11 €</span>. Davon sind 20 % als
          Handwerkerleistung nach § 35a EStG absetzbar — begrenzt auf 1.200 € im Jahr, und diese
          Grenze ist hier erreicht. Ihr tatsächlicher Aufwand sinkt damit auf
          <strong id="effTxt">19.292,11 €</strong>. Die Rechnung weist den Lohnanteil getrennt aus.</p>
      </div>

      <div class="callout" style="margin-top:1rem">
        <span class="t">Zahlung in drei Raten</span>
        <p>30 % bei Auftragserteilung, 50 % nach Abschluss der Fliesenarbeiten, 20 % nach Abnahme.
          Gewährleistung vier Jahre nach BGB.</p>
      </div>
    </div>
  </div>

  <div class="composer"><span class="field">Antworten …</span><span>↑</span></div>
</div>

<script>
(function(){
  var fmt = function(n){ return n.toLocaleString('de-DE',{minimumFractionDigits:2,maximumFractionDigits:2}) + ' €'; };
  var rooms = [].slice.call(document.querySelectorAll('.rw'));
  var grand = document.getElementById('grand'), net = document.getElementById('net');
  var taxBack = document.getElementById('taxBack'), laborTxt = document.getElementById('laborTxt');
  var effTxt = document.getElementById('effTxt'), hint = document.getElementById('roomHint');
  var order = document.getElementById('order'), done = document.getElementById('done'), doneTxt = document.getElementById('doneTxt');
  var durTxt = document.getElementById('durTxt');

  var DUR_FULL = 10, DUR_MIN = 3;
  var dur = DUR_FULL;

  function recalc(){
    var sum = 0, n = 0, badOn = false;
    rooms.forEach(function(r){
      if (r.getAttribute('aria-pressed') === 'true'){
        sum += parseFloat(r.dataset.eur); n++;
        if (r.dataset.core) badOn = true;
      }
    });
    grand.textContent = fmt(sum);
    net.textContent = fmt(sum / 1.19);
    var labor = sum * 0.62, back = Math.min(labor * 0.2, 1200);
    laborTxt.textContent = fmt(labor);
    taxBack.textContent = fmt(back);
    effTxt.textContent = fmt(sum - back);

    dur = badOn ? (n <= 2 ? 8 : DUR_FULL) : (n === 0 ? 0 : DUR_MIN);
    durTxt.textContent = dur + ' Werktage';

    if (n === rooms.length){
      hint.textContent = 'Räume abwählen, wenn Sie das Budget anpassen möchten — der Preis rechnet sich sofort neu.';
    } else if (n === 0){
      hint.textContent = 'Bitte wählen Sie mindestens einen Raum.';
    } else if (!badOn){
      hint.textContent = 'Ohne das Bad bleiben reine Malerarbeiten — drei Werktage statt zehn. Die Prüfung von Elektrik und Sanitär entfällt dann ebenfalls.';
    } else {
      hint.textContent = n + ' von ' + rooms.length + ' Räumen gewählt. Bei Teilbeauftragung verteilen sich Anfahrt und Rüstkosten auf weniger Fläche — der Quadratmeterpreis steigt dadurch leicht.';
    }
    order.disabled = (n === 0);
    paint();
  }
  rooms.forEach(function(r){
    r.addEventListener('click', function(){
      r.setAttribute('aria-pressed', r.getAttribute('aria-pressed') === 'true' ? 'false' : 'true');
      recalc();
      done.classList.remove('on');
    });
  });

  // Oktober 2026: der 1. ist ein Donnerstag
  var dows = ['Mo','Di','Mi','Do','Fr','Sa','So'];
  var belegt = [1,2,20,21];
  var grid = document.getElementById('calGrid');
  var startTxt = document.getElementById('startTxt'), endTxt = document.getElementById('endTxt');
  var chosen = 5;

  dows.forEach(function(d){
    var e = document.createElement('div'); e.className = 'dow'; e.textContent = d; grid.appendChild(e);
  });
  for (var i=0;i<3;i++){ var s=document.createElement('div'); s.className='day out'; grid.appendChild(s); }

  function wd(day){ return (day + 2) % 7; }
  function isWorkday(day){ return wd(day) < 5; }
  function avail(day){ return isWorkday(day) && belegt.indexOf(day) === -1; }
  function finish(day){
    var left = dur, d = day;
    if (left < 1) return day;
    while (left > 1){ d++; if (avail(d)) left--; }
    return d;
  }
  function label(day){
    var m = day > 31 ? 'November' : 'Oktober';
    var dd = day > 31 ? day - 31 : day;
    return dows[wd(day)] + ', ' + dd + '. ' + m;
  }
  function paint(){
    var end = finish(chosen);
    [].slice.call(grid.querySelectorAll('.day[data-d]')).forEach(function(el){
      var d = parseInt(el.dataset.d,10);
      el.classList.remove('sel','span');
      if (d === chosen) el.classList.add('sel');
      else if (d > chosen && d <= end && avail(d)) el.classList.add('span');
    });
    startTxt.textContent = label(chosen);
    endTxt.textContent = label(end);
  }
  for (var day=1; day<=31; day++){
    var btn = document.createElement('button');
    btn.type='button'; btn.className='day'; btn.textContent=day; btn.dataset.d=day;
    if (avail(day) && day >= 5 && day <= 19){
      btn.classList.add('free');
      btn.setAttribute('aria-label','Beginn am ' + label(day));
      btn.addEventListener('click', function(){
        chosen = parseInt(this.dataset.d,10); paint(); done.classList.remove('on');
      });
    } else { btn.disabled = true; }
    grid.appendChild(btn);
  }
  recalc();

  order.addEventListener('click', function(){
    done.classList.add('on');
    doneTxt.textContent = 'Beginn ' + label(chosen) + ', fertig ' + label(finish(chosen)) +
      '. Wir haben den Termin reserviert und melden uns mit der Auftragsbestätigung und dem Ablaufplan.';
    done.scrollIntoView({behavior:'smooth', block:'nearest'});
  });
})();
</script>

