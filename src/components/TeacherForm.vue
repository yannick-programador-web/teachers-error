<template>
  <section>
    <h3>Añadir professor</h3>
    <div><label>Nombre:</label> <input type="text" v-model="teacher.teacherName" /></div>
    <div><label>Apellidos:</label> <input type="text" v-model="teacher.surname" /></div>
    <div><label>DNI / NIE:</label> <input type="text" v-model="teacher.dni" /></div>
    <div>
      <label>Materias:</label> <input type="text" v-model="subject" />
      <button @click="handleSubject()">Agregar</button>
    </div>
    <div>
      <ul>
        <li v-for="(elm, index) in teacher.subjects" v-bind:key="index">{{ elm }}</li>
      </ul>
    </div>
    <input type="checkbox" v-model="teacher.doc" />Documentacion agregada
    <button @click="handleAddTeacher()">Agregar</button>
  </section>
</template>

<script lang="ts" setup>
import { Ref, ref } from 'vue'

interface ITeacher {
  teacherName: string
  surname: string
  dni: string
  subjects: Array<string>
  doc: boolean
}

let teacher: Ref<ITeacher> = ref({
  teacherName: '',
  surname: '',
  dni: '',
  subjects: [],
  doc: false
})

let teachers: Ref<Array<ITeacher>> = ref([])

let subject: Ref<string> = ref('')

const handleSubject = () => {
  teacher.value.subjects.push(subject.value)
  subject.value = ''
}

const handleAddTeacher = () => {
  teachers.value.push(teacher.value)
  teacher.value.teacherName = ''
  teacher.value.surname = ''
  teacher.value.dni = ''
  teacher.value.subjects = []
  teacher.value.doc = false
}
</script>

<style scoped></style>
