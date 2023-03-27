
<script setup>
import { format, formatDistance, formatRelative, subDays } from 'date-fns'
const formattedDate = format(new Date(), 'yyyy-MM-dd HH:mm:ss')
</script >

<template>
    <p> Date and Time: {{ formattedDate }} </p>
</template>

<style scoped>
p{
    right: 74%;
    bottom: 44%;
}
</style>
