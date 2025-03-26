<template>
    <div class="pricing">
        <div class="pricing-content">
            <h1>Preise & Mitgliedschaft</h1>
            <section class="pricing-section">
                <h2>Flexible Optionen</h2>
                <div class="pricing-grid">
                    <div class="pricing-card">
                        <h3>Einzeltraining</h3>
                        <div class="price">25€</div>
                        <p class="price-period">pro Training</p>
                        <ul>
                            <li>60 Minuten Training</li>
                            <li>Alle Altersgruppen</li>
                            <li>Keine Bindung</li>
                            <li>Flexible Buchung</li>
                        </ul>
                        <Button text="Jetzt buchen" @click="handleBooking('single')" />
                    </div>
                    <div class="pricing-card featured">
                        <div class="featured-badge">Beliebt</div>
                        <h3>10er-Karte</h3>
                        <div class="price">200€</div>
                        <p class="price-period">gültig 3 Monate</p>
                        <ul>
                            <li>10x 60 Minuten Training</li>
                            <li>20€ pro Einheit</li>
                            <li>Frei kombinierbar</li>
                            <li>Übertragbar</li>
                        </ul>
                        <Button text="Jetzt buchen" @click="handleBooking('tenner')" />
                    </div>
                    <div class="pricing-card">
                        <h3>Monatsabo</h3>
                        <div class="price">75€</div>
                        <p class="price-period">pro Monat</p>
                        <ul>
                            <li>Unbegrenzte Teilnahme</li>
                            <li>3 Monate Mindestlaufzeit</li>
                            <li>Alle Trainingsarten</li>
                            <li>Monatlich kündbar</li>
                        </ul>
                        <Button text="Jetzt buchen" @click="handleBooking('monthly')" />
                    </div>
                </div>
            </section>

            <HighlightSection title="Urban Sports Club">
                <template #content>
                    <div class="usc-content">
                        <p>Du bist Urban Sports Club Mitglied? Perfekt! Nutze deine Mitgliedschaft für unser Training:
                        </p>
                        <ul>
                            <li>Einfache Buchung über die USC-App</li>
                            <li>Flexible Teilnahme an allen Trainingseinheiten</li>
                            <li>Keine zusätzlichen Kosten (abhängig von deiner USC-Mitgliedschaft)</li>
                        </ul>
                        <Button text="Mehr zu Urban Sports Club" @click="handleUSC" />
                    </div>
                </template>
            </HighlightSection>

            <HighlightSection title="Kostenlose Probestunde">
                <template #content>
                    <div class="trial-content">
                        <p>Überzeuge dich selbst von der Qualität unseres Trainings. Vereinbare jetzt dein kostenloses
                            Probetraining!</p>
                        <Button text="Probetraining buchen" @click="handleTrial" />
                    </div>
                </template>
            </HighlightSection>
        </div>
    </div>
</template>

<script setup lang="ts">
import HighlightSection from '@/components/UI/HighlightSection.vue';
import Button from '@/components/UI/Button.vue';

const handleBooking = (type: 'single' | 'tenner' | 'monthly') => {
    // Implement booking logic
    console.log(`Booking ${type} package`)
}

const handleUSC = () => {
    // Redirect to USC info or partner page
    console.log('USC info requested')
}

const handleTrial = () => {
    // Implement trial booking
    console.log('Trial booking requested')
}
</script>

<style scoped>
.pricing {
    min-height: 100vh;
    padding: 40px 8%;
    background-color: var(--color-background);
    color: var(--color-text);
}

.pricing-content {
    max-width: 1200px;
    margin: 0 auto;
}

h1 {
    font-family: "Roboto-Bold", Helvetica, sans-serif;
    font-size: 32px;
    margin-bottom: 40px;
    color: var(--color-text);
    text-align: center;
}

.pricing-section {
    margin-bottom: 50px;
    padding: 30px;
    border-radius: 10px;
    background-color: var(--color-background-soft);
}

h2 {
    font-family: "Roboto-Bold", Helvetica, sans-serif;
    font-size: 24px;
    margin-bottom: 30px;
    color: var(--color-text);
    text-align: center;
}

.pricing-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
    gap: 30px;
    margin-top: 30px;
}

.pricing-card {
    padding: 30px;
    border-radius: 10px;
    background-color: var(--color-background-soft);
    position: relative;
    display: flex;
    flex-direction: column;
    gap: 20px;
}

.featured {
    border: 2px solid var(--color-primary);
    transform: scale(1.05);
}

.featured-badge {
    position: absolute;
    top: -12px;
    right: 20px;
    background-color: var(--color-primary);
    color: var(--color-text);
    padding: 4px 12px;
    border-radius: 20px;
    font-size: 14px;
    font-family: "Roboto-SemiBold", Helvetica, sans-serif;
}

h3 {
    font-family: "Roboto-Bold", Helvetica, sans-serif;
    font-size: 20px;
    color: var(--color-text);
    text-align: center;
}

.price {
    font-family: "Roboto-Bold", Helvetica, sans-serif;
    font-size: 36px;
    color: var(--color-primary);
    text-align: center;
}

.price-period {
    font-family: "Roboto-Regular", Helvetica, sans-serif;
    font-size: 14px;
    color: var(--color-text-muted);
    text-align: center;
    margin-top: -15px;
    opacity: 0.8;
}

ul {
    list-style-type: none;
    padding: 0;
    margin: 20px 0;
}

li {
    font-family: "Roboto-Regular", Helvetica, sans-serif;
    font-size: 16px;
    line-height: 1.6;
    margin-bottom: 10px;
    color: var(--color-text);
    padding-left: 24px;
    position: relative;
}

li::before {
    content: "✓";
    position: absolute;
    left: 0;
    color: var(--color-primary);
}

.pricing-button,
.usc-button,
.trial-button {
    all: unset;
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 12px 30px;
    border-radius: 10px;
    cursor: pointer;
    transition: opacity 0.2s ease;
    font-family: "Roboto-SemiBold", Helvetica, sans-serif;
    font-size: 14px;
    font-weight: 600;
    margin-top: auto;
}

.pricing-button {
    background-color: var(--color-primary);
    color: var(--color-text);
}

.usc-button {
    background-color: var(--color-text);
    color: var(--color-primary);
}

.trial-button {
    background-color: var(--color-primary);
    color: var(--color-text);
    margin: 20px auto 0;
}

.pricing-button:hover,
.usc-button:hover,
.trial-button:hover {
    opacity: 0.9;
}

.usc-section {
    background-color: var(--color-primary);
}

.usc-section h2,
.usc-section p,
.usc-section li {
    color: var(--color-text);
}

.usc-section li::before {
    color: var(--color-text);
}

.usc-content,
.trial-content {
    text-align: center;
}

p {
    font-family: "Roboto-Regular", Helvetica, sans-serif;
    font-size: 16px;
    line-height: 1.6;
    margin-bottom: 20px;
    color: var(--color-text);
}

@media (max-width: 768px) {
    .pricing {
        padding: 30px 5%;
    }

    h1 {
        font-size: 28px;
        margin-bottom: 30px;
    }

    h2 {
        font-size: 20px;
        margin-bottom: 20px;
    }

    .pricing-section {
        padding: 20px;
        margin-bottom: 30px;
    }

    .pricing-grid {
        gap: 20px;
    }

    .featured {
        transform: none;
    }
}

@media (max-width: 480px) {
    .pricing {
        padding: 20px 4%;
    }

    h1 {
        font-size: 24px;
        margin-bottom: 25px;
    }

    h2 {
        font-size: 18px;
    }

    .pricing-section {
        padding: 15px;
        margin-bottom: 20px;
    }

    .pricing-card {
        padding: 20px;
    }

    .price {
        font-size: 32px;
    }
}
</style>