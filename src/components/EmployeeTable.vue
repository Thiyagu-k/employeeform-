<template>
    <div class="employee-table">
        <table>
            <thead>
                <tr>
                    <th>S.No</th>
                    <th>Name</th>
                    <th>Email</th>
                    <th>Mobile Number</th>
                    <th>Salary</th>
                    <th>Role</th>
                    <th>Date</th>
                </tr>
            </thead>
            <tbody>
            <tr v-for="(employee, i ) in employeedata" :key="employee.id">
                <td>{{ i + 1 }}</td>
                <td>{{ employee.name }}</td>
                <td>{{ employee.email }}</td>
                <td>{{ employee.phone }}</td>
                <td>₹ {{ employee.salary }}.00</td>
                <td>{{ employee.role }}</td>
                <td>{{ employee.date_join }}</td>
            </tr>
            </tbody>
        </table>
    </div>
</template>

<script>
export default {
    name: 'EmployeeTable',
    props : {
        employeedata : Array
    }
};
</script>

<style scoped>
.employee-table table {
    width: 100%;
    border-collapse: collapse;
}

.employee-table th,
.employee-table td {
    padding: 8px;
    border: 1px solid #ddd;
    text-align: center;
}
</style>