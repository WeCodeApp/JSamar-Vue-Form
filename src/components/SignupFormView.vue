<template>
    <div class="signup-form-view flex items-center justify-center min-h-screen bg-gray-100">
        <div class="flex bg-white rounded-lg shadow-lg w-full max-w-4xl">
            <div class="bg-gradient-to-r from-pink-300 via-pink-400 to-pink-500 p-8 rounded-l-lg w-1/2 animate-gradient-wave pt-20">
                <h1 class="text-2xl font-bold text-center mb-6 text-white">Signup Form</h1>
                <form @submit.prevent="handleSubmit" class="space-y-4">
                    <div>
                        <label for="username" class="block text-sm font-medium text-white">Username:</label>
                        <input 
                            type="text" 
                            id="username" 
                            v-model="username" 
                            required 
                            class="mt-1 block w-full px-4 py-2 border border-gray-300 rounded-md shadow-sm focus:ring-blue-500 focus:border-blue-500"
                        />
                    </div>
                    <div>
                        <label for="email" class="block text-sm font-medium text-white">Email:</label>
                        <input 
                            type="email" 
                            id="email" 
                            v-model="email" 
                            required 
                            class="mt-1 block w-full px-4 py-2 border border-gray-300 rounded-md shadow-sm focus:ring-blue-500 focus:border-blue-500"
                        />
                    </div>
                    <div>
                        <label for="password" class="block text-sm font-medium text-white">Password:</label>
                        <input 
                            type="password" 
                            id="password" 
                            v-model="password" 
                            required 
                            class="mt-1 block w-full px-4 py-2 border border-gray-300 rounded-md shadow-sm focus:ring-blue-500 focus:border-blue-500"
                        />
                    </div>
                    
                <div>
                    <label for="role" class="block text-sm font-medium text-white">Role:</label>
                    <select
                        type="role" 
                        id="role" 
                        v-model="role" 
                        required 
                        class="mt-1 block w-full px-4 py-2 border border-red-200  rounded-md shadow-sm focus:ring-blue-500 focus:border-blue-500"
                    >
                        <option value="" disabled selected>Select your role</option>
                        <option value="admin">Core</option>
                        <option value="user">Gold</option>
                        <option value="guest">Angela</option>
                        <option value="guest">Exp</option>
                        <option value="guest">Mid</option>
                    </select>

                    <label class="block text-sm font-medium text-white">Skills: </label>
                    <input type="text" v-model="tempSkill" @keyup="addSkill" placeholder="Enter your skills" class="mt-1 block w-full px-4 py-2 border border-gray-300 rounded-md shadow-sm focus:ring-blue-500 focus:border-blue-500"/>
                    <div v-for="skill in skills" :key="skill" @mousedown="removeSkill" class="mt-2 rounded-md bg-gray-200 px-2 py-1 text-md text-gray-700 mr-2 mb-2 inline-block">
                        {{ skill }}
                    </div>
                </div>
                
                    <button 
                        type="submit" 
                        class="w-full bg-red-700 text-white py-2 px-4 rounded-md hover:bg-red-300 focus:outline-none focus:ring-2 focus:ring-red-600 focus:ring-offset-2"
                    >
                        Submit
                    </button>
                </form>

                <div class="mt-4 flex items-center justify-center">
                <input type="checkbox" v-model="terms" id="terms" required class="mr-2"/>
                <label for="terms" class="text-sm text-white">I agree to the terms and conditions</label>
            </div>
            <div>
                <input type="checkbox" v-model="names" id="names" required class="mr-2"/>
                <label for="names" class="text-sm text-white">Kimmy</label>
            </div>

            <div>
                <input type="checkbox" v-model="names" id="names" required class="mr-2"/>
                <label for="names" class="text-sm text-white">ALdous</label>
            </div>

            <div>
                <input type="checkbox" v-model="names" id="names" required class="mr-2"/>
                <label for="names" class="text-sm text-white">Roger's coming</label>
            </div>
            </div>

            <!-- Image Section -->
            <div class="w-1/2">
                <img 
                    src="@/assets/alucard.jpg" 
                    alt="Signup Illustration" 
                    class="h-full w-full object-cover rounded-r-lg"
                />
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'SignupFormView',
    data() {
        return {
            username: '',
            email: '',
            password: '',
            terms: false,
            names: [],
            skills: [],
        };
    },
    methods: {
        handleSubmit() {
            console.log('Form submitted:', {
                username: this.username,
                email: this.email,
                password: this.password
            });
        },
        addSkill(e) {
            let tempSkill = this.tempSkill.slice(0, -1);
            if (e.key === '.' && this.tempSkill) {
                if (!this.skills.includes(tempSkill)){
                    this.skills.push(tempSkill);
                }
                this.tempSkill = '';
            }
        },
        removeSkill(e) {
            const clickedSkill = e.target.textContent.trim();
            this.skills = this.skills.filter(skill => skill !== clickedSkill);
        }
    }
}
</script>

<style>
/* Add the gradient animation */
@keyframes gradient-wave {
    0% {
        background-position: 0% 50%;
    }
    50% {
        background-position: 100% 50%;
    }
    100% {
        background-position: 0% 50%;
    }
}

.animate-gradient-wave {
    background-size: 200% 200%;
    animation: gradient-wave 6s ease infinite;
}
</style>