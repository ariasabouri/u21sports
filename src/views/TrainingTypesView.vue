<template>
    <div class="training-types">
        <div class="training-types-content">
            <h1>Trainingsarten</h1>

            <section class="training-type-section">
                <h2>Fußballtraining (60 Min)</h2>
                <div class="training-details">
                    <h3>Schwerpunkte:</h3>
                    <ul>
                        <li>Technische Grundlagen und Weiterentwicklung</li>
                        <li>Ballbeherrschung und Koordination</li>
                        <li>Taktisches Verständnis</li>
                        <li>Spielsituationen und Matchpraxis</li>
                    </ul>
                    <h3>Vorteile:</h3>
                    <ul>
                        <li>Individuelle Betreuung in Kleingruppen</li>
                        <li>Altersgerechte Trainingsmethoden</li>
                        <li>Regelmäßige Fortschrittskontrolle</li>
                        <li>Modernste Trainingsausrüstung</li>
                    </ul>
                </div>
            </section>

            <section class="training-type-section">
                <h2>Athletiktraining (60 Min)</h2>
                <div class="training-details">
                    <h3>Schwerpunkte:</h3>
                    <ul>
                        <li>Kraft und Explosivität</li>
                        <li>Ausdauer und Schnelligkeit</li>
                        <li>Beweglichkeit und Koordination</li>
                        <li>Verletzungsprävention</li>
                    </ul>
                    <h3>Vorteile:</h3>
                    <ul>
                        <li>Fußballspezifische Übungen</li>
                        <li>Professionelle Ausrüstung</li>
                        <li>Individuelle Belastungssteuerung</li>
                        <li>Leistungsdiagnostik</li>
                    </ul>
                </div>
            </section>

            <section class="training-type-section">
                <h2>Kombi-Training (90-120 Min)</h2>
                <div class="training-details">
                    <h3>Schwerpunkte:</h3>
                    <ul>
                        <li>Integriertes Fußball- und Athletiktraining</li>
                        <li>Ganzheitliche Entwicklung</li>
                        <li>Optimale Belastungssteuerung</li>
                        <li>Wettkampfvorbereitung</li>
                    </ul>
                    <h3>Vorteile:</h3>
                    <ul>
                        <li>Maximaler Trainingseffekt</li>
                        <li>Effiziente Zeitnutzung</li>
                        <li>Ausgewogenes Training</li>
                        <li>Intensive Betreuung</li>
                    </ul>
                </div>
            </section>

            <section class="training-type-section cta-section">
                <h2>Finde dein passendes Training</h2>
                <p>Wir beraten dich gerne bei der Auswahl des optimalen Trainings für deine Ziele.</p>
                <button class="cta-button" @click="handleCtaClick">Kostenlose Beratung</button>
            </section>
        </div>
    </div>
</template>

<script setup lang="ts">
const handleCtaClick = () => {
    // Implement consultation booking logic
    console.log('Training consultation requested')
}
</script>

<style scoped>
.training-types {
    min-height: 100vh;
    padding: 40px 8%;
    background-color: #0a2025;
    color: #ffffff;
}

.training-types-content {
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

.training-type-section {
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

.training-details {
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

.cta-section {
    text-align: center;
    background-color: #3e9d26;
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
    .training-types {
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

    .training-type-section {
        padding: 20px;
        margin-bottom: 30px;
    }
}

@media (max-width: 480px) {
    .training-types {
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

    .training-type-section {
        padding: 15px;
        margin-bottom: 20px;
    }
}
</style>