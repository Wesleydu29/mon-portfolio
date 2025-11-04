<template>
    <div class="container">
        <form class="form-group" @submit.prevent="handleSubmit">
            <h3>Envoyez moi un mail et je vous repondrez au plus vite</h3>
            <label for="nom">Nom</label>
            <input type="text" id="nom" v-model="formData.nom" required>
            <label for="prénom">Prénom</label>
            <input type="text"  id="prénom" v-model="formData.prenom" required>
            <label for="email">Email</label>
            <input type="text" id="email" v-model="formData.email" required>
            <label for="message">Message</label>
            <textarea name="" id="message" placeholder="écrivez votre message" v-model="formData.message" required></textarea>

            <button type="submit"
                :disabled="!isFormValid"
                :class="{ disabled: !isFormValid }"
            >
                {{ isSubmitting ? 'Envoi...' : 'Envoyer' }}
            </button>

            <div v-if="submitMessage" :class="['message', submitStatus]">
                    {{ submitMessage }}
            </div>
        </form>

    </div>

</template>

<script setup>
import { ref, computed } from 'vue';
import emailjs from '@emailjs/browser';

const formData = ref({
    nom: '',
    prenom: '',
    email: '',
    message: ''
});

const isSubmitting = ref(false);
const submitMessage = ref('');
const submitStatus = ref('');

const EMAILJS_SERVICE_ID = import.meta.env.VITE_EMAILJS_SERVICE_ID;
const EMAILJS_TEMPLATE_ID = import.meta.env.VITE_EMAILJS_TEMPLATE_ID;
const EMAILJS_PUBLIC_KEY = import.meta.env.VITE_EMAILJS_PUBLIC_KEY;

const isFormValid = computed(() => {
    return formData.value.nom.trim() !== '' &&
           formData.value.prenom.trim() !== '' &&
           formData.value.email.trim() !== '' &&
           formData.value.message.trim() !== '' &&
           isValidEmail(formData.value.email);
});

const isValidEmail = (email) => {
    const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
    return emailRegex.test(email);
};
// Gère l'envoi du formulaire
const handleSubmit = async () => {
    
    if (!isFormValid.value || isSubmitting.value) return;
    
    isSubmitting.value = true;
    submitMessage.value = '';
    
    try {
         const response = await emailjs.send(
            EMAILJS_SERVICE_ID,
            EMAILJS_TEMPLATE_ID,
            {
                from_name: `${formData.value.prenom} ${formData.value.nom}`,
                from_email: formData.value.email,
                 message: formData.value.message
             },
             EMAILJS_PUBLIC_KEY, 
         );
        
        formData.value = {
            nom: '',
            prenom: '',
            email: '',
            message: ''
        };
        
    } catch (error) {
        console.error('Erreur lors de l\'envoi:', error);
        submitMessage.value = 'Une erreur est survenue. Veuillez réessayer.';
        submitStatus.value = 'error';
    } finally {
        isSubmitting.value = false;
        setTimeout(() => {
            submitMessage.value = '';
        }, 5000);
    }
};

</script>

<style scoped>
* {
    box-sizing: border-box;
}
.container {
    width: 100%;
    display: flex;
    flex-direction: column;
    align-items: center ;

}
.form-group {
    width: 580px;
    padding: 10px;
    margin-bottom: 1rem;
    border-radius: 25px;
    box-shadow: 0 15px 35px rgba(0, 0, 0, 0.2);
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    color: white;

}
.form-group h3 {
    text-align: center;
}
label {
    align-self: flex-start;
}
input {
    height: 2rem;
    margin-bottom: 1rem;
}
input, textarea {
    width: 100%;
}
textarea {
    height: 100px;
}
input:focus,
textarea:focus {
    outline: 3px solid rgba(255, 255, 255, 0.5);
}
Button {
    width: 120px;
    height: 2.5rem;
    border-radius: 15px;
    border: none;
    font-size: 1rem;
    transition: transform 0.3s ease, filter 0.3s ease;
    margin: 1rem auto 0;
    display: block;
    margin-top: 2rem;
    margin-bottom: 1rem;
}

button:hover:not(.disabled) {
    transform: scale(1.05);
    filter: brightness(0.95);
    cursor: pointer;
}

button.disabled {
    opacity: 0.5;
    cursor: not-allowed;
}
</style>