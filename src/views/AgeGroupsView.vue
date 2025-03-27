<template>
    <div class="age-groups">
        <div class="age-groups-content">
            <h1>Altersgruppen</h1>

            <section class="age-group-section">
                <h2>U10-U11 (9-11 Jahre)</h2>
                <div class="age-group-details">
                    <h3>Schwerpunkte</h3>
                    <ul>
                        <li>Grundlegende Techniken und Ballgefühl</li>
                        <li>Koordinative Fähigkeiten</li>
                        <li>Spielerisches Lernen</li>
                        <li>Erste taktische Grundlagen</li>
                    </ul>
                    <h3>Trainingsmethodik</h3>
                    <p>In dieser Altersgruppe steht der Spaß am Fußball im Vordergrund. Durch altersgerechte Übungen und
                        Spielformen entwickeln die Kinder ihre motorischen Fähigkeiten und ein grundlegendes Verständnis
                        für das Spiel.</p>
                </div>
            </section>

            <section class="age-group-section">
                <h2>U12-U13 (11-13 Jahre)</h2>
                <div class="age-group-details">
                    <h3>Schwerpunkte</h3>
                    <ul>
                        <li>Technische Perfektion</li>
                        <li>Taktisches Grundverständnis</li>
                        <li>Spielpositionen und -rollen</li>
                        <li>Athletische Grundlagen</li>
                    </ul>
                    <h3>Trainingsmethodik</h3>
                    <p>Das Training wird anspruchsvoller und zielgerichteter. Wir fördern das Verständnis für
                        verschiedene Spielsituationen und führen erste positionsspezifische Übungen ein.</p>
                </div>
            </section>

            <section class="age-group-section">
                <h2>U14-U15 (13-15 Jahre)</h2>
                <div class="age-group-details">
                    <h3>Schwerpunkte</h3>
                    <ul>
                        <li>Komplexe Technik unter Druck</li>
                        <li>Taktische Spielkonzepte</li>
                        <li>Positionsspezifisches Training</li>
                        <li>Athletik und Kondition</li>
                    </ul>
                    <h3>Trainingsmethodik</h3>
                    <p>Das Training orientiert sich am Leistungssport. Wir arbeiten an individuellen Stärken und
                        bereiten die Spieler auf höhere Anforderungen vor.</p>
                </div>
            </section>

            <HighlightSection title="Die richtige Gruppe finden"
                text="Unsere erfahrenen Trainer helfen dabei, die passende Altersgruppe und das richtige Leistungsniveau zu finden."
                :buttons="[{ label: 'Beratungsgespräch vereinbaren', onClick: handleCtaClick }]" />
        </div>
    </div>
</template>

<script setup lang="ts">
import HighlightSection from '@/components/UI/HighlightSection.vue';
import Button from '@/components/UI/Button.vue';

const handleCtaClick = () => {
    // Implement consultation booking logic
    console.log('Consultation CTA clicked')
}
</script>

<style scoped>
.age-groups {
    min-height: 100vh;
    padding: 40px 8%;
    background-color: var(--color-background);
    color: var(--color-text);
}

.age-groups-content {
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

.age-group-section {
    margin-bottom: 50px;
    padding: 30px;
    border-radius: 10px;
    background-color: var(--color-background-soft);
}

h2 {
    font-family: "Roboto-Bold", Helvetica, sans-serif;
    font-size: 24px;
    margin-bottom: 20px;
    color: var(--color-text);
}

h3 {
    font-family: "Roboto-SemiBold", Helvetica, sans-serif;
    font-size: 18px;
    margin: 20px 0 15px;
    color: var(--color-text);
}

.age-group-details {
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

@media (max-width: 768px) {
    .age-groups {
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

    .age-group-section {
        padding: 20px;
        margin-bottom: 30px;
    }
}

@media (max-width: 480px) {
    .age-groups {
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

    .age-group-section {
        padding: 15px;
        margin-bottom: 20px;
    }
}
</style>