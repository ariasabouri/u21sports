<template>
    <div class="training">
        <div class="training-content">
            <h1>Unser Training</h1>

            <section class="training-section">
                <h2>Fußballtraining (60 Min)</h2>
                <div class="training-details">
                    <p>Unser Kernprogramm fokussiert sich auf:</p>
                    <ul>
                        <li>Technische Grundlagen und Weiterentwicklung</li>
                        <li>Taktisches Verständnis und Spielintelligenz</li>
                        <li>Ballbeherrschung und Koordination</li>
                        <li>Spielsituationen und Matchpraxis</li>
                    </ul>
                </div>
            </section>

            <section class="training-section">
                <h2>Athletiktraining (60 Min)</h2>
                <div class="training-details">
                    <p>Spezifisches Fitnesstraining für Fußballer:</p>
                    <ul>
                        <li>Kraft und Explosivität</li>
                        <li>Ausdauer und Schnelligkeit</li>
                        <li>Beweglichkeit und Koordination</li>
                        <li>Verletzungsprävention</li>
                    </ul>
                </div>
            </section>

            <section class="training-section">
                <h2>Kombi-Training (90-120 Min)</h2>
                <div class="training-details">
                    <p>Die perfekte Kombination für maximalen Fortschritt:</p>
                    <ul>
                        <li>Integriertes Fußball- und Athletiktraining</li>
                        <li>Optimale Belastungssteuerung</li>
                        <li>Ganzheitliche Entwicklung</li>
                        <li>Intensive Betreuung</li>
                    </ul>
                </div>
            </section>

            <section class="training-section cta-section">
                <h2>Jetzt Probetraining vereinbaren</h2>
                <p>Erlebe unser professionelles Training selbst und überzeuge dich von unserer Qualität.</p>
                <button class="cta-button" @click="handleCtaClick">Probetraining buchen</button>
            </section>
        </div>
    </div>
</template>

<script setup lang="ts">
const handleCtaClick = () => {
    // Implement booking logic or navigation
    console.log('CTA clicked')
}
</script>

<style scoped>
.training {
    min-height: 100vh;
    padding: 40px 8%;
    background-color: var(--color-background);
}

.training-content {
    max-width: 800px;
    margin: 0 auto;
}

h1 {
    font-family: "Roboto-Bold", Helvetica, sans-serif;
    font-size: 32px;
    margin-bottom: 40px;
    color: var(--color-heading);
}

.training-section {
    margin-bottom: 50px;
    padding: 30px;
    border-radius: 10px;
    background-color: var(--color-background-soft);
}

h2 {
    font-family: "Roboto-Bold", Helvetica, sans-serif;
    font-size: 24px;
    margin-bottom: 20px;
    color: var(--color-heading);
}

.training-details {
    margin-top: 20px;
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

.cta-section {
    text-align: center;
    background-color: #3e9d26;
    color: white;
}

.cta-section h2,
.cta-section p {
    color: white;
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
    background-color: white;
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
    .training {
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

    .training-section {
        padding: 20px;
        margin-bottom: 30px;
    }
}

@media (max-width: 480px) {
    .training {
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

    .training-section {
        padding: 15px;
        margin-bottom: 20px;
    }
}
</style>