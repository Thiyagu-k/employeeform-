<template>
    <div id="employee-form">
        <form @submit.prevent="handleSubmit">
            <label>Name</label>
            <input 
                type="text" 
                v-model="employee.name" 
                placeholder="Enter your name" 
                :class="{'has-error': submitting && invalidName}"
                @focus="clearStatus"
                @keypress="clearStatus"
            />
            
            <label>Email</label>
            <input 
                type="email" 
                v-model="employee.email" 
                placeholder="Enter your email" 
                :class="{'has-error': submitting && invalidEmail}"
                @focus="clearStatus"
                @keypress="clearStatus"
            />

            <label>Phone Number</label>
            <input 
                type="text" 
                v-model="employee.phone" 
                placeholder="Enter your mobile number" 
                maxlength="10"
                @focus="clearStatus"
                @keypress="clearStatus"
            />

            <label>Salary</label>
            <input 
                type="number" 
                v-model="employee.salary" 
                placeholder="Enter your salary"
                @focus="clearStatus"
                @keypress="clearStatus"
            />

            <label>Role</label>
            <input 
                type="text" 
                v-model="employee.role" 
                placeholder="Enter your role" 
                @focus="clearStatus"
                @keypress="clearStatus"
            />

            <label>Date</label>
            <input 
                type="date" 
                v-model="employee.date" 
                placeholder="Select your joining date"
                @focus="clearStatus"
            />

            <button type="submit">Add Employee</button>

            <p v-if="success" class="success-message">Employee added successfully!</p>
            <p v-if="error" class="error-message">Please fill out all required fields.</p>
        </form>
    </div>
</template>

<script>
export default {
    name: 'EmployeeForm',
    data() {
        return {
            submitting: false,
            success: false,
            error: false,
            employee: {
                name: '',
                email: '',
                phone: '',
                salary: '',
                role : '',
                date: ''
            }
        }
    },
    methods: {
        handleSubmit() {
            this.submitting = true;
            this.clearStatus();

            if (this.invalidName || this.invalidEmail) {
                this.error = true;
                return;
            }

            this.$emit("add:employee", this.employee);
            this.employee = {
                name: '',
                email: '',
                phone: '',
                salary: '',
                role: '',
                date: ''
            };

            this.success = true;
            this.error = false;
        },
        clearStatus() {
            this.success = false;
            this.error = false;
            this.submitting = false;
        }
    },
    computed: {
        invalidName() {
            return this.employee.name.trim() === '';
        },
        invalidEmail() {
            return this.employee.email.trim() === '';
        }
    }
}
</script>

<style scoped>
#employee-form {
    width: 300px;
    margin: 20px auto;
    font-family: Arial, sans-serif;
}

form {
    display: flex;
    flex-direction: column;
}

label {
    margin-bottom: 5px;
    font-weight: bold;
}

input[type="text"],
input[type="email"],
input[type="number"],
input[type="date"] {
    padding: 8px;
    margin-bottom: 10px;
    border: 1px solid #ccc;
    border-radius: 4px;
}

button {
    padding: 10px;
    background-color: #4CAF50;
    color: white;
    border: none;
    border-radius: 4px;
    cursor: pointer;
    font-size: 16px;
}

button:hover {
    background-color: #45a049;
}

.has-error {
    border-color: red;
}

.success-message {
    color: green;
    margin-top: 10px;
    font-weight: bold;
}

.error-message {
    color: red;
    margin-top: 10px;
    font-weight: bold;
}
</style>
