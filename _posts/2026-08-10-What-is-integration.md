---
layout: post
title: "What is integration?"
tags: politics misc
---

Not so long ago I've learned what does it mean "integration", at least now I think I know. I've learned it from Anka and later on I did a quick research. The thing I've learned was introduced in 1980 by John W. Berry, canadian psychologist and known as [Acculturation Model](https://open.maricopa.edu/culturepsychology/chapter/berrys-model-of-acculturation/). Yes, that's probably not new for someone with non-engineer education but for me it was new.  

It could be described by simple matrix.  
<img width="400" src='/assets/images/2026-08-10/Multicultural_acculturation-e1657405870340.png' style="display:block; margin:0 auto;">

So Integration — being able to leave in host culture, while preserve value and maintain your own and it's quite different from Assimilation, which is often mixed. At least for me it was the case — I've mixed up those two terms frequently.

But devil is in details — apparently we, immigrants, persue different strategy in private and public life. We are not simply sitting in one quadrant. Also in some researches it's shown that variation among same nationalities are huge. A 2024 study on Turkish immigrant parents in England, Germany, the Netherlands, and Norway found four distinct profiles across all four countries — but their sizes differed significantly. In England, with its relatively multicultural national policy, the integration profile was more prominent, while in countries with a stronger emphasis on assimilation (like the Netherlands and Norway), the profile distribution shifted. [2025](https://doi.org/10.1007/s12134-024-01185-2) 

From my own experience I can tell — even during the week, sometimes within the day even, my strategy might change. It could be as simple decision as about having a lunch at 11:30-12:00 or later ;)

A 2024 study from Finland gives interesting breakdown consdiering generations. Among immigrant-origin youth surveyed in 2023, 71% belonged to high- or medium-integration profiles. The full breakdown was: Medium integration 49%, High integration 22%, "Neo-culture kid" 15%, Separation 6%, Assimilation 6%, and Marginalization the smallest group.[2025](https://doi.org/10.1007/s12134-024-01194-1)

Is it good to be integrated? Yes. People have better school adaption, better work performance, higher wellbeing. Also people with separation have higher levels of depressive symptoms compared to integration. Even though "integration is best" is widely supported, I also think so btw. There is reverse-causality argument: people with good mental health and adaptive social skills going to integrate more likely. 

There is recent Migrant Integration Policy Index data [2025](https://www.mipex.eu/key-findings-2025) which are quite interesting to explore. For example, EU-average is 54/100 and post-2004 member states (Czech Republic, Estonia, Latvia, Lithuania, Hungary, Poland, Slovakia, Slovenia, Cyprus, Malta, Bulgaria, Romania, Croatia) are on average 44 vs. 63 for pre-2004 countries. However it should be remembered — it measures how much the host country *enables* integration, not how immigrants actually end up. 

<div id="mipex-wrap" style="width: 100%; overflow-x: auto;">

<h4 class="sr-only" styel="font-weight:bold;">MIPEX 2025 — EU country scores on migrant integration policy, with breakdowns across eight policy areas</h4>

<style>
  .mipex-wrap { padding: 1rem 0; font-family: var(--font-sans); }
  .controls { display: flex; flex-wrap: wrap; gap: 8px; margin-bottom: 1.5rem; align-items: center; }
  .pill-btn { font-size: 12px; padding: 5px 12px; border-radius: 20px; border: 0.5px solid var(--color-border-secondary); background: var(--color-background-primary); color: var(--color-text-secondary); cursor: pointer; transition: all .15s; }
  .pill-btn.active { background: #185FA5; border-color: #185FA5; color: #fff; }
  .pill-btn:hover:not(.active) { background: var(--color-background-secondary); }
  .tier-legend { display: flex; flex-wrap: wrap; gap: 10px; margin-bottom: 1.25rem; font-size: 11px; color: var(--color-text-secondary); }
  .tier-dot { width: 9px; height: 9px; border-radius: 50%; display: inline-block; margin-right: 4px; vertical-align: middle; }
  .note { font-size: 11px; color: var(--color-text-tertiary); margin-top: 1rem; }
</style>

<div class="mipex-wrap">
  <div class="controls" id="controls"></div>
  <div class="tier-legend">
    <span><span class="tier-dot" style="background:#1D9E75"></span>Favourable (80–100)</span>
    <span><span class="tier-dot" style="background:#378ADD"></span>Slightly favourable (60–79)</span>
    <span><span class="tier-dot" style="background:#EF9F27"></span>Halfway favourable (41–59)</span>
    <span><span class="tier-dot" style="background:#E24B4A"></span>Slightly unfavourable (21–40)</span>
  </div>
  <div style="position:relative; width:100%;">
    <canvas id="mipexChart" role="img" aria-label="Horizontal bar chart of MIPEX 2025 scores for 27 EU countries across selected policy areas"></canvas>
  </div>
  <p class="note">Source: MIPEX 2025 (Migration Policy Group). Policy scores measure legal frameworks, not actual immigrant outcomes. EU-27 average overall: 54/100.</p>
</div>

<script src="https://cdnjs.cloudflare.com/ajax/libs/Chart.js/4.4.1/chart.umd.js"></script>
<script>
const areas = {
  overall: { label: 'Overall score', data: { SE:86,FI:84,PT:83,BE:70,ES:64,DE:61,LU:61,IE:59,IT:58,NL:57,FR:56,RO:52,SI:52,EE:51,CZ:49,DK:49,EL:49,MT:48,AT:47,HR:44,PL:44,CY:41,HU:41,BG:39,SK:39,LT:37,LV:36 }},
  labour:  { label: 'Labour market mobility', data: { PT:94,FI:91,SE:91,DE:81,EL:72,EE:69,IT:67,ES:67,DK:65,NL:65,AT:59,BE:56,CZ:54,FR:52,LT:52,HR:50,BG:48,MT:48,SI:48,RO:46,PL:43,LU:41,HU:37,LV:33,CY:30,IE:22,SK:17 }},
  family:  { label: 'Family reunion', data: { PT:93,EE:76,SE:71,FI:67,RO:67,HR:65,IT:64,CZ:63,ES:63,SI:63,SK:59,HU:58,EL:52,LU:52,PL:50,BE:48,LV:47,IE:46,FR:43,LT:43,DE:42,BG:38,AT:36,MT:36,CY:35,NL:30,DK:25 }},
  education:{ label: 'Education', data: { SE:93,FI:88,BE:74,PT:74,EE:69,AT:64,LU:64,CZ:62,NL:57,DE:55,SI:53,EL:50,RO:50,ES:50,PL:48,DK:45,FR:43,IT:43,LT:43,HR:40,CY:40,MT:40,IE:38,LV:26,SK:26,BG:21,HU:21 }},
  political:{ label: 'Political participation', data: { FI:85,PT:80,SE:80,LU:65,BE:65,DK:60,DE:60,IE:60,ES:55,NL:50,FR:45,SI:40,MT:35,CY:25,IT:25,AT:20,HR:20,EE:20,EL:20,LV:20,PL:20,HU:15,CZ:10,LT:5,RO:5,SK:5,BG:5 }},
  residence:{ label: 'Permanent residence', data: { FI:96,SE:90,HU:81,BE:79,ES:75,PT:71,BG:69,EE:67,IT:67,SK:65,SI:58,LU:58,RO:56,FR:54,HR:54,DE:54,LT:52,NL:52,AT:50,CY:50,CZ:50,IE:50,PL:50,EL:46,LV:46,MT:46,DK:42 }},
  Nationality:{ label: 'Access to nationality', data: { PT:86,SE:83,LU:79,IE:79,FI:74,FR:70,DE:67,BE:65,MT:63,NL:52,CY:50,PL:50,DK:41,EL:40,IT:40,RO:38,CZ:36,ES:30,SK:28,HU:25,LV:24,LT:22,SI:22,HR:19,EE:16,AT:13,BG:9 }},
  antidisc: { label: 'Anti-discrimination', data: { BE:100,BG:100,FI:100,PT:100,RO:100,ES:100,SE:100,SI:96,HU:92,IE:90,NL:85,LU:80,FR:79,SK:79,IT:78,HR:74,DE:70,EL:67,LV:67,CZ:64,MT:63,CY:62,PL:56,AT:53,EE:52,DK:51,LT:51 }},
  health:   { label: 'Health', data: { IE:85,SE:83,AT:81,IT:79,ES:75,BE:73,FI:73,PT:71,NL:65,DE:63,DK:60,FR:60,MT:56,RO:54,CZ:52,LU:50,EL:46,EE:40,CY:36,SK:36,PL:33,SI:33,LT:31,BG:29,HR:29,LV:25,HU:17 }}
};

const countryNames = {
  SE:'Sweden',FI:'Finland',PT:'Portugal',BE:'Belgium',ES:'Spain',DE:'Germany',LU:'Luxembourg',IE:'Ireland',IT:'Italy',NL:'Netherlands',FR:'France',RO:'Romania',SI:'Slovenia',EE:'Estonia',CZ:'Czechia',DK:'Denmark',EL:'Greece',MT:'Malta',AT:'Austria',HR:'Croatia',PL:'Poland',CY:'Cyprus',HU:'Hungary',BG:'Bulgaria',SK:'Slovakia',LT:'Lithuania',LV:'Latvia'
};

function getColor(score) {
  if (score >= 80) return '#1D9E75';
  if (score >= 60) return '#378ADD';
  if (score >= 41) return '#EF9F27';
  return '#E24B4A';
}

let currentArea = 'overall';
let chart;

function buildChart(areaKey) {
  const area = areas[areaKey];
  const sorted = Object.entries(area.data).sort((a,b) => b[1]-a[1]);
  const labels = sorted.map(([k]) => countryNames[k]);
  const values = sorted.map(([,v]) => v);
  const colors = values.map(v => getColor(v));
  const wrapperH = Math.max(sorted.length * 34 + 60, 200);
  document.getElementById('mipexChart').parentElement.style.height = wrapperH + 'px';

  if (chart) chart.destroy();
  const isDark = matchMedia('(prefers-color-scheme: dark)').matches;
  const gridColor = isDark ? 'rgba(255,255,255,0.08)' : 'rgba(0,0,0,0.07)';
  const textColor = isDark ? '#aaa' : '#666';

  chart = new Chart(document.getElementById('mipexChart'), {
    type: 'bar',
    data: {
      labels,
      datasets: [{
        data: values,
        backgroundColor: colors,
        borderWidth: 0,
        barThickness: 20
      }]
    },
    options: {
      indexAxis: 'y',
      responsive: true,
      maintainAspectRatio: false,
      plugins: {
        legend: { display: false },
        tooltip: {
          callbacks: {
            title: (items) => items[0].label,
            label: (item) => ` ${item.raw}/100 — ${area.label}`
          }
        }
      },
      scales: {
        x: {
          min: 0, max: 100,
          grid: { color: gridColor },
          ticks: { color: textColor, font: { size: 11 }, stepSize: 20 },
          border: { display: false }
        },
        y: {
          grid: { display: false },
          ticks: { color: textColor, font: { size: 11 }, autoSkip: false },
          border: { display: false }
        }
      }
    }
  });
}

const controls = document.getElementById('controls');
Object.entries(areas).forEach(([key, val]) => {
  const btn = document.createElement('button');
  btn.className = 'pill-btn' + (key === 'overall' ? ' active' : '');
  btn.textContent = key === 'overall' ? 'Overall' : val.label.replace('Access to ', '').replace('Anti-discrimination','Anti-discrim.').replace('Political participation','Political partic.').replace('Permanent residence','Perm. residence').replace('Labour market mobility','Labour market').replace('Family reunion','Family reunion');
  btn.onclick = () => {
    document.querySelectorAll('.pill-btn').forEach(b => b.classList.remove('active'));
    btn.classList.add('active');
    currentArea = key;
    buildChart(key);
  };
  controls.appendChild(btn);
});

buildChart('overall');
</script>

</div>

But again — better policy push immigrants towards integration but it's not a guarantee.