<!DOCTYPE html>
<html lang="sk">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Môj tréningový plán</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #f5f5f5;
      margin: 0;
      padding: 1rem;
    }
    h1, h2 {
      text-align: center;
    }
    .week-selector {
      display: flex;
      justify-content: center;
      margin-bottom: 1rem;
    }
    .week-selector button {
      margin: 0 0.5rem;
      padding: 0.5rem 1rem;
      border: none;
      background: #007bff;
      color: white;
      border-radius: 5px;
      cursor: pointer;
    }
    .week-selector button.active {
      background: #0056b3;
    }
    .day {
      background: white;
      padding: 1rem;
      margin-bottom: 1rem;
      border-radius: 8px;
      box-shadow: 0 0 5px rgba(0,0,0,0.1);
    }
    label {
      display: block;
      margin: 0.5rem 0;
    }
    .note {
      margin-top: 1rem;
    }
    textarea {
      width: 100%;
      height: 60px;
      border-radius: 5px;
      padding: 0.5rem;
      border: 1px solid #ccc;
    }
  </style>
</head>
<body>
  <h1>Tréning & Strava</h1>
  <div class="week-selector">
    <button onclick="showWeek(1)" class="active">Týždeň 1</button>
    <button onclick="showWeek(2)">Týždeň 2</button>
    <button onclick="showWeek(3)">Týždeň 3</button>
  </div>

  <div id="plan-container"></div>

  <script>
    const plan = {
      1: {
        'Pondelok': {
          trening: ['Mobilita krčnej chrbtice', 'Hip thrust 4x12', 'Glute bridge', 'Plank 3x30s'],
          strava: ['Raňajky: Herbalife + ovocie', 'Obed: tortilla + cottage', 'Večera: tuniak + špenát']
        },
        'Utorok': {
          trening: ['Kardio 20 min', 'Drepy s vlastnou váhou', 'Strečing'],
          strava: ['Raňajky: ovsené vločky + orechy', 'Obed: kuracie mäso + zelenina', 'Večera: cottage + vajcia']
        },
        'Streda': {
          trening: ['Horná časť: tlaky, sťahovanie kladky, biceps s gumou', 'Core: plank + leg raises'],
          strava: ['Raňajky: Herbalife + banán', 'Obed: ryža + tofu', 'Večera: šalát + vajcia']
        },
        'Štvrtok': {
          trening: ['Voľno / aktívna regenerácia', 'Strečing krčnej chrbtice'],
          strava: ['Raňajky: smoothie + vločky', 'Obed: tortilla + cottage + zelenina', 'Večera: ryba + špenát']
        },
        'Piatok': {
          trening: ['Dolná časť: Hip thrust, výpady, zakopávanie, lýtka', 'Core'],
          strava: ['Raňajky: Herbalife + ovocie', 'Obed: mäso + quinoa', 'Večera: šalát + tuniak']
        }
      },
      2: {
        'Pondelok': {
          trening: ['Silový tréning: drep s činkou, rumunský mŕtvy ťah', 'Core: plank'],
          strava: ['Herbalife + ovocie', 'Obed: kuracie mäso + ryža', 'Večera: cottage + špenát']
        },
        'Utorok': {
          trening: ['Strečing + mobilita + kardio 30 min'],
          strava: ['Ovsená kaša + orechy', 'Tortilla + tuniak', 'Večera: ryba + zelenina']
        },
        // ... pokračovanie podľa potreby
      },
      3: {
        'Pondelok': {
          trening: ['Testovanie sily', 'Zápis pokroku', 'Jemná mobilita'],
          strava: ['Herbalife + vločky', 'Kuracie mäso + šalát', 'Vajcia + cottage']
        },
        // ... ďalšie dni
      }
    };

    function showWeek(weekNum) {
      document.querySelectorAll('.week-selector button').forEach(btn => btn.classList.remove('active'));
      document.querySelectorAll('.week-selector button')[weekNum - 1].classList.add('active');
      const container = document.getElementById('plan-container');
      container.innerHTML = '';
      const week = plan[weekNum];
      for (const day in week) {
        const data = week[day];
        const el = document.createElement('div');
        el.className = 'day';
        el.innerHTML = `<h2>${day}</h2>
          <strong>Tréning:</strong>
          ${data.trening.map((t, i) => `
            <label><input type="checkbox"> ${t}</label>`).join('')}
          <strong>Strava:</strong>
          ${data.strava.map((s, i) => `
            <label><input type="checkbox"> ${s}</label>`).join('')}
          <div class="note">
            <strong>Poznámky:</strong>
            <textarea placeholder="Záznam tréningu alebo stravy..."></textarea>
          </div>`;
        container.appendChild(el);
      }
    }

    // Zobraziť hneď Týždeň 1
    showWeek(1);
  </script>
</body>
</html>
