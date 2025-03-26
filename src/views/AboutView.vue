<template>
  <div class="about">
    <div class="about-content">
      <h1>Über U21 Sports</h1>

      <section class="about-section">
        <h2>Unsere Vision</h2>
        <p>U21 Sports steht für professionelles Fußballtraining der nächsten Generation. Wir bieten strukturiertes
          Training für verschiedene Altersgruppen und Leistungsniveaus, um jeden Spieler individuell zu fördern und
          weiterzuentwickeln.</p>
      </section>

      <section class="about-section">
        <h2>Unser Angebot</h2>
        <ul>
          <li>Fußballtraining (60 Min) für U10-U11, U12-U13, U14-U15</li>
          <li>Athletiktraining (60 Min) für alle Altersgruppen</li>
          <li>Kombi-Sessions für ganzheitliche Entwicklung</li>
          <li>Professionelle Trainer mit langjähriger Erfahrung</li>
          <li>Kleine Gruppengrößen für optimale Betreuung</li>
        </ul>
      </section>

      <section class="about-section highlight-section">
        <h2>Urban Sports Club Partner</h2>
        <p>Als Partner von Urban Sports Club bieten wir flexible Buchungsmöglichkeiten für unsere Trainingseinheiten.
          USC-Mitglieder können einfach über die App buchen und teilnehmen.</p>
      </section>

      <section class="about-section">
        <h2>Standorte</h2>
        <p>Wir nutzen moderne Sportanlagen in der Stadt und kooperieren mit lokalen Vereinen, um optimale
          Trainingsbedingungen zu gewährleisten.</p>
      </section>
    </div>
  </div>
</template>

<style scoped>
.about {
  min-height: 100vh;
  padding: 40px 8%;
  background-color: var(--color-background);
  color: var(--color-text);
}

.about-content {
  max-width: 800px;
  margin: 0 auto;
}

h1 {
  font-family: "Roboto-Bold", Helvetica, sans-serif;
  font-size: 32px;
  margin-bottom: 40px;
  color: var(--color-text);
  text-align: center;
}

.about-section {
  margin-bottom: 40px;
  padding: 30px;
  border-radius: 10px;
  background-color: var(--color-background-soft);
}

.highlight-section {
  background-color: var(--color-primary);
}

h2 {
  font-family: "Roboto-Bold", Helvetica, sans-serif;
  font-size: 24px;
  margin-bottom: 20px;
  color: var(--color-text);
}

p {
  font-family: "Roboto-Regular", Helvetica, sans-serif;
  font-size: 16px;
  line-height: 1.6;
  margin-bottom: 20px;
  color: var(--color-text);
}

ul {
  list-style-type: disc;
  padding-left: 20px;
  margin-bottom: 20px;
}

li {
  font-family: "Roboto-Regular", Helvetica, sans-serif;
  font-size: 16px;
  line-height: 1.6;
  margin-bottom: 10px;
  color: var(--color-text);
}

@media (max-width: 768px) {
  .about {
    padding: 30px 5%;
  }

  h1 {
    font-size: 28px;
    margin-bottom: 30px;
  }

  h2 {
    font-size: 20px;
    margin-bottom: 15px;
  }

  .about-section {
    margin-bottom: 30px;
    padding: 20px;
  }
}

@media (max-width: 480px) {
  .about {
    padding: 20px 4%;
  }

  h1 {
    font-size: 24px;
    margin-bottom: 25px;
  }

  h2 {
    font-size: 18px;
  }

  p,
  li {
    font-size: 14px;
  }

  .about-section {
    padding: 15px;
    margin-bottom: 20px;
  }
}
</style>
