<template>
    <div class="small-container">
        <h1>Employee Form</h1>
        <employee-form @add:employee="addemployee" />
        <h1>Employee Details</h1>
        <employee-table :employeedata="employees"></employee-table>
    </div>
</template>

<script>
import EmployeeTable from "./components/EmployeeTable.vue";
import EmployeeForm from "./components/EmployeeForm.vue";

export default {
    name: "App",
    components: {
        EmployeeTable,
        EmployeeForm
    },
    data() {
        return {
            employees: [
                {
                    id: 1,
                    name: "Thiyagu K",
                    email: "thiyagu@gmail.com",
                    phone: 8667081150,
                    salary: 25900,
					role: 'Information Technology',
                    date_join: "26-10-2024",
                },
            ],
        };
    },
    methods: {
        addemployee(employee) {
            const lastId = this.employees.length > 0 ? this.employees[this.employees.length - 1].id : 0;
            const id = lastId + 1;
            const newEmployee = { ...employee, id, date_join: employee.date };
            this.employees = [...this.employees, newEmployee];
        }
    },
};
</script>

<style>
button {
    background: #009435;
    border: 1px solid #009435;
    color: white;
    padding: 10px 15px;
    cursor: pointer;
    font-size: 14px;
    border-radius: 5px;
}

button:hover {
    background-color: #007a2c;
}

.small-container {
    /* max-width: 680px; */
    margin: 0 auto;
    font-family: Arial, sans-serif;
}

h1 {
    color: #333;
    text-align: center;
}
</style>
