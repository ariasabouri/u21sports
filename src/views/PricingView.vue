<template>
    <div class="pricing">
        <div class="pricing-content">
            <h1>Preise & Mitgliedschaft</h1>

            <Section title="Flexible Optionen" class="pricing-section">
                <div class="pricing-grid">
                    <Card title="Einzeltraining">
                        <div class="price">25€</div>
                        <p class="price-period">pro Training</p>
                        <ul>
                            <ListItem text="60 Minuten Training" />
                            <ListItem text="Alle Altersgruppen" />
                            <ListItem text="Keine Bindung" />
                            <ListItem text="Flexible Buchung" />
                        </ul>
                        <template #footer>
                            <Button text="Jetzt buchen" @click="handleBooking('single')" />
                        </template>
                    </Card>

                    <Card title="10er-Karte" featured badgeText="Beliebt">
                        <div class="price">200€</div>
                        <p class="price-period">gültig 3 Monate</p>
                        <ul>
                            <ListItem text="10x 60 Minuten Training" />
                            <ListItem text="20€ pro Einheit" />
                            <ListItem text="Frei kombinierbar" />
                            <ListItem text="Übertragbar" />
                        </ul>
                        <template #footer>
                            <Button text="Jetzt buchen" @click="handleBooking('tenner')" />
                        </template>
                    </Card>

                    <Card title="Monatsabo">
                        <div class="price">75€</div>
                        <p class="price-period">pro Monat</p>
                        <ul>
                            <ListItem text="Unbegrenzte Teilnahme" />
                            <ListItem text="3 Monate Mindestlaufzeit" />
                            <ListItem text="Alle Trainingsarten" />
                            <ListItem text="Monatlich kündbar" />
                        </ul>
                        <template #footer>
                            <Button text="Jetzt buchen" @click="handleBooking('monthly')" />
                        </template>
                    </Card>
                </div>
            </Section>

            <HighlightSection title="Urban Sports Club" backgroundColor="var(--color-primary)"
                text="Du bist Urban Sports Club Mitglied? Perfekt! Nutze deine Mitgliedschaft für unser Training: Einfache Buchung über die USC-App, Flexible Teilnahme an allen Trainingseinheiten, Keine zusätzlichen Kosten (abhängig von deiner USC-Mitgliedschaft)."
                :buttons="[{ label: 'Mehr zu Urban Sports Club', onClick: handleUSC }]" />

            <HighlightSection title="Kostenlose Probestunde" backgroundColor="var(--color-primary)"
                text="Überzeuge dich selbst von der Qualität unseres Trainings. Vereinbare jetzt dein kostenloses Probetraining!"
                :buttons="[{ label: 'Probetraining buchen', onClick: handleTrial }]" />
        </div>
    </div>
</template>

<script setup lang="ts">
import HighlightSection from '@/components/UI/HighlightSection.vue';
import Button from '@/components/UI/Button.vue';
import Card from '@/components/UI/Card.vue';
import Section from '@/components/UI/Section.vue';
import ListItem from '@/components/UI/ListItem.vue';

const handleBooking = (type: 'single' | 'tenner' | 'monthly') => {
    // Implement booking logic
    console.log(`Booking ${type} package`);
};

const handleUSC = () => {
    // Redirect to USC info or partner page
    console.log('USC info requested');
};

const handleTrial = () => {
    // Implement trial booking
    console.log('Trial booking requested');
};
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
}

.pricing-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
    gap: 30px;
    margin-top: 30px;
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
    color: var (--color-text-muted);
    text-align: center;
    margin-top: -15px;
    opacity: 0.8;
}

ul {
    list-style-type: none;
    padding: 0;
    margin: 20px 0;
}

@media (max-width: 768px) {
    .pricing {
        padding: 30px 5%;
    }

    h1 {
        font-size: 28px;
        margin-bottom: 30px;
    }

    .pricing-grid {
        gap: 20px;
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

    .price {
        font-size: 32px;
    }
}
</style>