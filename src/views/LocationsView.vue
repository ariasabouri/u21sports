<template>
    <div class="locations">
        <div class="locations-content">
            <h1>Unsere Standorte</h1>

            <section class="location-section main-location">
                <h2>BASE - Unser Hauptstandort</h2>
                <div class="location-details">
                    <p>Unser Haupttrainingsgelände bietet optimale Bedingungen für alle Altersgruppen:</p>
                    <ul>
                        <li>Moderne Kunstrasenplätze</li>
                        <li>Athletikbereich für Fitnesstraining</li>
                        <li>Umkleidekabinen und Duschen</li>
                        <li>Ausreichend Parkplätze</li>
                    </ul>
                </div>
            </section>

            <section class="location-section">
                <h2>Weitere Trainingsstandorte</h2>
                <div class="location-details">
                    <h3>Hallentraining (Winter)</h3>
                    <p>In den Wintermonaten nutzen wir moderne Sporthallen für:</p>
                    <ul>
                        <li>Techniktraining</li>
                        <li>Koordinationsübungen</li>
                        <li>Athletikeinheiten</li>
                    </ul>

                    <h3>Kooperationspartner</h3>
                    <p>Durch Partnerschaften mit lokalen Vereinen haben wir Zugang zu:</p>
                    <ul>
                        <li>Zusätzlichen Trainingsplätzen</li>
                        <li>Wettkampfanlagen</li>
                        <li>Speziellen Trainingseinrichtungen</li>
                    </ul>
                </div>
            </section>

            <section class="location-section schedule">
                <h2>Trainingszeiten</h2>
                <div class="schedule-grid">
                    <div class="schedule-item">
                        <h3>U10-U11</h3>
                        <ul>
                            <li>Montag & Mittwoch: 16:00 - 17:00</li>
                            <li>Freitag: 15:30 - 16:30</li>
                        </ul>
                    </div>
                    <div class="schedule-item">
                        <h3>U12-U13</h3>
                        <ul>
                            <li>Montag & Mittwoch: 17:15 - 18:15</li>
                            <li>Freitag: 16:45 - 17:45</li>
                        </ul>
                    </div>
                    <div class="schedule-item">
                        <h3>U14-U15</h3>
                        <ul>
                            <li>Dienstag & Donnerstag: 17:00 - 18:00</li>
                            <li>Freitag: 18:00 - 19:00</li>
                        </ul>
                    </div>
                </div>
            </section>

            <section class="location-section cta-section">
                <h2>Kostenlos vorbeischauen</h2>
                <p>Besuche uns an einem unserer Standorte und überzeuge dich selbst von der Qualität unseres Trainings.
                </p>
                <button class="cta-button" @click="handleCtaClick">Probetraining buchen</button>
            </section>
        </div>
    </div>
</template>

<script setup lang="ts">
const handleCtaClick = () => {
    // Implement booking logic
    console.log('Location CTA clicked')
}
</script>

<style scoped>
.locations {
    min-height: 100vh;
    padding: 40px 8%;
    background-color: #0a2025;
    color: #ffffff;
}

.locations-content {
    max-width: 800px;
    margin: 0 auto;
}

h1 {
    font-family: "Roboto-Bold", Helvetica, sans-serif;
    font-size: 32px;
    margin-bottom: 40px;
    color: #ffffff;
    text-align: center;
}

.location-section {
    margin-bottom: 50px;
    padding: 30px;
    border-radius: 10px;
    background-color: rgba(255, 255, 255, 0.05);
}

h2 {
    font-family: "Roboto-Bold", Helvetica, sans-serif;
    font-size: 24px;
    margin-bottom: 20px;
    color: #ffffff;
}

h3 {
    font-family: "Roboto-SemiBold", Helvetica, sans-serif;
    font-size: 18px;
    margin: 20px 0 15px;
    color: #ffffff;
}

.location-details {
    margin-top: 20px;
}

p {
    font-family: "Roboto-Regular", Helvetica, sans-serif;
    font-size: 16px;
    line-height: 1.6;
    margin-bottom: 20px;
    color: #ffffff;
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
    color: #ffffff;
}

.schedule-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: 30px;
    margin-top: 20px;
}

.schedule-item {
    padding: 20px;
    background-color: rgba(255, 255, 255, 0.05);
    border-radius: 8px;
}

.schedule-item h3 {
    margin-top: 0;
}

.schedule-item ul {
    margin-bottom: 0;
}

.cta-section {
    text-align: center;
    background-color: #3e9d26;
}

.cta-section h2,
.cta-section p {
    color: #ffffff;
}

.cta-button {
    all: unset;
    display: inline-flex;
    align-items: center;
    justify-content: center;
    padding: 12px 30px;
    border-radius: 10px;
    cursor: pointer;
    transition: opacity 0.2s ease;
    background-color: #ffffff;
    color: #3e9d26;
    font-family: "Roboto-SemiBold", Helvetica, sans-serif;
    font-size: 14px;
    font-weight: 600;
    margin-top: 20px;
}

.cta-button:hover {
    opacity: 0.9;
}

@media (max-width: 768px) {
    .locations {
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

    h3 {
        font-size: 16px;
    }

    .location-section {
        padding: 20px;
        margin-bottom: 30px;
    }

    .schedule-grid {
        gap: 20px;
    }

    .schedule-item {
        padding: 15px;
    }
}

@media (max-width: 480px) {
    .locations {
        padding: 20px 4%;
    }

    h1 {
        font-size: 24px;
        margin-bottom: 25px;
    }

    h2 {
        font-size: 18px;
    }

    h3 {
        font-size: 15px;
    }

    p,
    li {
        font-size: 14px;
    }

    .location-section {
        padding: 15px;
        margin-bottom: 20px;
    }
}
</style>