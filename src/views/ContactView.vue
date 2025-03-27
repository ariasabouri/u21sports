<template>
    <div class="contact">
        <div class="contact-content">
            <h1>Kontakt</h1>
            <div class="contact-grid">
                <Section class="form-section">
                    <template #header>
                        <h2>Schreib uns</h2>
                    </template>

                    <form class="contact-form" @submit.prevent="handleSubmit">
                        <FormInput v-model="formData.name" id="name" label="Name" type="text" placeholder="Dein Name"
                            required />

                        <FormInput v-model="formData.email" id="email" label="E-Mail" type="email"
                            placeholder="deine@email.de" required />

                        <FormInput v-model="formData.phone" id="phone" label="Telefon (optional)" type="tel"
                            placeholder="+49 123 45678990" />

                        <FormInput v-model="formData.subject" id="subject" label="Betreff" type="select"
                            placeholder="Bitte wählen" :options="subjectOptions" required />

                        <FormInput v-model="formData.message" id="message" label="Nachricht" type="textarea"
                            placeholder="Deine Nachricht an uns..." :rows="5" required />

                        <Button type="primary" backgroundColor="transparent" text="Nachricht senden"
                            @click="handleSubmit" />
                    </form>
                </Section>

                <Section class="info-section">
                    <div class="info-block">
                        <h2>Kontaktinformationen</h2>
                        <div class="contact-info">
                            <div class="info-item">
                                <strong>Telefon:</strong>
                                <p>+49 (0) 123 456789</p>
                            </div>
                            <div class="info-item">
                                <strong>E-Mail:</strong>
                                <p>info@u21sports.de</p>
                            </div>
                            <div class="info-item">
                                <strong>Trainingszeiten:</strong>
                                <p>Montag - Freitag: 15:00 - 20:00 Uhr</p>
                                <p>Samstag: 10:00 - 14:00 Uhr</p>
                            </div>
                        </div>
                    </div>

                    <div class="info-block">
                        <h2>Hauptstandort</h2>
                        <div class="location-info">
                            <p>U21 Sports BASE</p>
                            <p>Musterstraße 123</p>
                            <p>12345 Berlin</p>
                        </div>
                    </div>

                    <div class="social-links">
                        <h2>Social Media</h2>
                        <div class="social-icons">
                            <SocialIcon network="instagram" />
                            <SocialIcon network="facebook" />
                            <SocialIcon network="twitter" />
                            <SocialIcon network="youtube" />
                        </div>
                    </div>
                </Section>
            </div>
        </div>
    </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';
import Button from '@/components/UI/Button.vue';
import FormInput from '@/components/UI/FormInput.vue';
import Section from '@/components/UI/Section.vue';
import SocialIcon from '@/components/UI/SocialIcon.vue';
import HighlightSection from '@/components/UI/HighlightSection.vue';

interface FormData {
    name: string;
    email: string;
    phone: string;
    subject: string;
    message: string;
}

const formData = ref<FormData>({
    name: '',
    email: '',
    phone: '',
    subject: '',
    message: ''
});

const subjectOptions = [
    { label: 'Probetraining', value: 'trial' },
    { label: 'Buchungsanfrage', value: 'booking' },
    { label: 'Allgemeine Information', value: 'info' },
    { label: 'Sonstiges', value: 'other' }
];

const handleSubmit = () => {
    // Implement form submission logic
    console.log('Form submitted:', formData.value);
};

const handleSocialClick = (network: string) => {
    console.log(`Clicked ${network} social icon`);
    // Add social media redirect logic here
};
</script>

<style scoped>
.contact {
    min-height: 100vh;
    padding: 40px 8%;
    background-color: var(--color-background);
    color: var(--color-text);
}

.contact-content {
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

.contact-grid {
    display: grid;
    grid-template-columns: 3fr 2fr;
    gap: 40px;
}

.form-section,
.info-section {
    border-radius: 10px;
    background-color: var(--color-background-soft);
}

h2 {
    font-family: "Roboto-Bold", Helvetica, sans-serif;
    font-size: 24px;
    margin-bottom: 30px;
    color: var(--color-text);
}

.contact-form {
    display: flex;
    flex-direction: column;
    gap: 5px;
}

.info-section {
    display: flex;
    flex-direction: column;
    gap: 40px;
}

.info-block {
    margin-bottom: 30px;
}

.contact-info,
.location-info {
    display: flex;
    flex-direction: column;
    gap: 15px;
}

.info-item {
    margin-bottom: 15px;
}

strong {
    font-family: "Roboto-SemiBold", Helvetica, sans-serif;
    color: var(--color-text);
    display: block;
    margin-bottom: 5px;
}

p {
    font-family: "Roboto-Regular", Helvetica, sans-serif;
    font-size: 16px;
    line-height: 1.6;
    margin: 0;
    color: var(--color-text);
}

.social-icons {
    display: flex;
    gap: 20px;
    margin-top: 15px;
}

@media (max-width: 968px) {
    .contact-grid {
        grid-template-columns: 1fr;
    }
}

@media (max-width: 768px) {
    .contact {
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
}

@media (max-width: 480px) {
    .contact {
        padding: 20px 4%;
    }

    h1 {
        font-size: 24px;
        margin-bottom: 25px;
    }

    h2 {
        font-size: 18px;
    }

    .social-icons {
        gap: 15px;
    }
}

.info-section h2,
.info-section p,
.info-section strong {
    color: var(--color-text);
}
</style>