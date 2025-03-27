<template>
    <div class="contact">
        <div class="contact-content">
            <h1>Kontakt</h1>

            <div class="contact-grid">
                <section class="contact-section form-section">
                    <h2>Schreib uns</h2>
                    <form class="contact-form" @submit.prevent="handleSubmit">
                        <div class="form-group">
                            <label for="name">Name</label>
                            <input type="text" id="name" v-model="formData.name" required placeholder="Dein Name">
                        </div>

                        <div class="form-group">
                            <label for="email">E-Mail</label>
                            <input type="email" id="email" v-model="formData.email" required
                                placeholder="deine@email.de">
                        </div>

                        <div class="form-group">
                            <label for="phone">Telefon (optional)</label>
                            <input type="tel" id="phone" v-model="formData.phone" placeholder="+49 123 45678990">
                        </div>

                        <div class="form-group">
                            <label for="subject">Betreff</label>
                            <select id="subject" v-model="formData.subject" required>
                                <option value="">Bitte wählen</option>
                                <option value="trial">Probetraining</option>
                                <option value="booking">Buchungsanfrage</option>
                                <option value="info">Allgemeine Information</option>
                                <option value="other">Sonstiges</option>
                            </select>
                        </div>

                        <div class="form-group">
                            <label for="message">Nachricht</label>
                            <textarea id="message" v-model="formData.message" required
                                placeholder="Deine Nachricht an uns..." rows="5"></textarea>
                        </div>

                        <Button type="primary" backgroundColor="transparent" text="Nachricht senden"
                            @click="handleSubmit" />
                    </form>
                </section>

                <HighlightSection>
                    <template #content>
                        <div class="info-section">
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
                                    <a href="#" class="social-icon" title="Instagram">
                                        <img src="@/assets/icons/ph-instagram-logo.svg" alt="Instagram">
                                    </a>
                                    <a href="#" class="social-icon" title="Facebook">
                                        <img src="@/assets/icons/ph-facebook-logo.svg" alt="Facebook">
                                    </a>
                                    <a href="#" class="social-icon" title="Twitter">
                                        <img src="@/assets/icons/ph-twitter-logo.svg" alt="Twitter">
                                    </a>
                                    <a href="#" class="social-icon" title="YouTube">
                                        <img src="@/assets/icons/ph-youtube-logo.svg" alt="YouTube">
                                    </a>
                                </div>
                            </div>
                        </div>
                    </template>
                </HighlightSection>
            </div>
        </div>
    </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import Button from '@/components/UI/Button.vue';
import HighlightSection from '@/components/UI/HighlightSection.vue';

interface FormData {
    name: string
    email: string
    phone: string
    subject: string
    message: string
}

const formData = ref<FormData>({
    name: '',
    email: '',
    phone: '',
    subject: '',
    message: ''
})

const handleSubmit = () => {
    // Implement form submission logic
    console.log('Form submitted:', formData.value)
}
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

.contact-section {
    padding: 30px;
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
    gap: 20px;
}

.form-group {
    display: flex;
    flex-direction: column;
    gap: 8px;
}

label {
    font-family: "Roboto-SemiBold", Helvetica, sans-serif;
    font-size: 14px;
    color: var(--color-text);
}

input,
select,
textarea {
    padding: 12px;
    border: 1px solid rgba(255, 255, 255, 0.3);
    border-radius: 8px;
    background-color: var(--color-background);
    color: var(--color-text);
    font-family: "Roboto-Regular", Helvetica, sans-serif;
    font-size: 16px;
}

input:focus,
select:focus,
textarea:focus {
    outline: none;
    border-color: var(--color-primary);
    box-shadow: 0 0 0 1px var(--color-primary);
}

.submit-button {
    all: unset;
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 12px 30px;
    border-radius: 10px;
    cursor: pointer;
    transition: opacity 0.2s ease;
    background-color: var(--color-primary);
    color: var(--color-text);
    font-family: "Roboto-SemiBold", Helvetica, sans-serif;
    font-size: 14px;
    font-weight: 600;
    margin-top: 10px;
}

.submit-button:hover {
    opacity: 0.9;
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

.social-icon {
    display: flex;
    align-items: center;
    justify-content: center;
    width: 40px;
    height: 40px;
    border-radius: 50%;
    background-color: var(--color-background-soft);
    transition: all 0.2s ease;
}

.social-icon img {
    width: 24px;
    height: 24px;
}

.social-icon:hover {
    background-color: var(--color-primary);
    transform: scale(1.1);
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

    .contact-section {
        padding: 20px;
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

    .contact-section {
        padding: 15px;
    }

    .social-icons {
        gap: 15px;
    }

    .social-icon {
        width: 36px;
        height: 36px;
    }

    .social-icon img {
        width: 20px;
        height: 20px;
    }
}

.info-section h2,
.info-section p,
.info-section strong {
    color: var(--color-text-secondary);
}
</style>