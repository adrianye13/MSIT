<template>
<body class="bg-gray-800 w-full h-full">
    

    <!-- Barra de navegación -->
    <ul class=" flex items-center justify-center bg-gray-800 space-x-4 h-16">
      <li>
        <div class="flex space-x-4">
          <h1 class="text-center text-cyan-800 text-2xl font-['centaur'] font-bold sm:text-4xl">INSTITUTO TECNOLOGICO SUPERIOR DE MOTUL</h1>
        </div>
      </li>
    </ul>

    <br>
    <br>
    
    <img src="/sit.png" alt="" class=" mx-auto mt-4 w-16 h-16 sm:w-32 sm:h-32" />
    <p class="text-center font-['centaur'] sm:text-2xl">Estado de la evaluación tutor</p>
    
  <!-- Contenedor principal -->
  <div class="flex flex-row items-center justify-center">
    <div v-if="isLoading" class="loading">Cargando...</div>
    <div v-else>
      <!-- Contenido -->
      <div class="w-full p-1">
        <!-- Primer bloque -->
   
          <div class="text-1xl text-center font-['centaur'] font-bold mb-0 text-cyan-800 sm:text-3xl">
            {{ customTitles.periodo }}</div>
          
          <div class="text-1xl font-['centaur'] text-center mb-4 text-white sm:text-2xl">{{ info.periodo }}</div>

          <div class="sm:text-3xl">
    <div class="font-['centaur'] text-center text-1xl font-bold  text-cyan-800">
      <p>Horas restantes</p>
    </div>
    <div class="font-['centaur'] text-1xl text-center mb-4 text-white sm:text-2xl">{{ calculateHoursRemaining(info.fin) }}</div>
    
  </div>
        

          <div class="flex space-x-4">
  <!-- Primer bloque -->
  <div class=" rounded-lg p-6 sm:text-3xl">
    <div class="font-['centaur'] text-center text-1xl font-bold mb-4 text-cyan-800">
      {{ customTitles.inicio }}
    </div>
    <div class="font-['centaur'] text-1xl text-center mb-4 text-white sm:text-2xl">{{ formatDate(info.inicio) }}</div>
  </div>
  <img src="/tiempo.png" alt="" class="mx-auto mt-4 w-14 h-14 sm:w-16 sm:h-16" />
  <!-- Segundo bloque -->
  <div class= "rounded-lg  p-6 sm:text-3xl">
    <div class="font-['centaur'] text-center text-1xl font-bold mb-4 text-cyan-800">
      {{ customTitles.fin }}
    </div>
    <div class="font-['centaur'] text-1xl text-center mb-4 text-white sm:text-2xl">{{ formatDate(info.fin) }}</div>
  </div>
  </div>



  
    <!-- Contenido adicional de tu aplicación aquí -->
    <div class="flex space-x-4">
    <div class="bg-cyan-800 rounded-full  p-6 w-44 h-44 sm:w-72 sm:h-72 mx-auto" >
  <div class="text-lg font-bold font-['centaur'] text-center mb-2 text-gray-800 sm:text-3xl">
    {{ customTitles.ISC }}
  </div>
  <img src="/sistema.png" alt="" class=" mx-auto mt-4 w-0 h-0 sm:w-20 sm:h-20" />
  <div class="text-1xl mb-2 font-['centaur'] text-center text-white sm:text-1xl">{{ formatValue(info.ISC) }}

<!-- Porcentaje en Números y Barra de Progreso -->
<div class="flex flex-col items-center justify-center h-full">
  <div class="relative w-32 h-8 mb-2 overflow-hidden rounded-full">
    <div :style="{ width: calculateProgress(info.ISC) + '%' }" class="absolute top-0 left-0 h-full bg-gray-800 sm:bg-teal-900 rounded-full"></div>
    <div class="w-full h-full bg-gray-300 rounded-full"></div>
  </div>
  <div class="text-sm font-bold text-gray-800">
    {{ Math.round(calculateProgress(info.ISC)) }}%
  </div>
</div>
  </div>
</div>


<div class="bg-cyan-800 rounded-full shadow-md p-6 w-44 h-44 sm:w-72 sm:h-72  ">
  <div class="text-lg font-bold font-['centaur'] text-center mb-2 text-gray-800 sm:text-3xl">
    {{ customTitles.II }}
  </div>
  <img src="/proceso.png" alt="" class=" mx-auto mt-4 w-0 h-0 sm:w-20 sm:h-20" />
  <div class="text-1xl mb-2 font-['centaur'] text-center text-white">{{ formatValue(info.II) }}

<!-- Porcentaje en Números y Barra de Progreso -->
<div class="flex flex-col items-center justify-center h-full">
  <div class="relative w-32 h-8 mb-2 overflow-hidden rounded-full">
    <div :style="{ width: calculateProgress(info.II) + '%' }" class="absolute top-0 left-0 h-full bg-gray-800 sm:bg-teal-900 rounded-full"></div>
    <div class="w-full h-full bg-gray-300 rounded-full"></div>
  </div>
  <div class="text-sm font-bold text-gray-800">
    {{ Math.round(calculateProgress(info.II)) }}%
  </div>
</div>
  </div>
</div>
</div>

<br>

<div class="flex space-x-4">
    <div class="bg-cyan-800 rounded-full shadow-md p-6 w-44 h-44 sm:w-72 sm:h-72  mx-auto">
  <div class="text-lg font-bold font-['centaur'] text-center mb-2 text-gray-800 sm:text-3xl">
    {{ customTitles.IE }}
  </div>
  <img src="/electronica.png" alt="" class=" mx-auto mt-4 w-0 h-0 sm:w-20 sm:h-20" />
  <div class="text-1xl mb-2 font-['centaur'] text-center text-white">{{ formatValue(info.IE) }}

<!-- Porcentaje en Números y Barra de Progreso -->
<div class="flex flex-col items-center justify-center h-full">
  <div class="relative w-32 h-8 mb-2 overflow-hidden rounded-full">
    <div :style="{ width: calculateProgress(info.IE) + '%' }" class="absolute top-0 left-0 h-full bg-gray-800 sm:bg-teal-900 rounded-full"></div>
    <div class="w-full h-full bg-gray-300 rounded-full"></div>
  </div>
  <div class="text-sm font-bold text-gray-800">
    {{ Math.round(calculateProgress(info.IE)) }}%
  </div>
</div>
  </div>
</div>


<div class="bg-cyan-800 rounded-full shadow-md p-6 w-44 h-44 sm:w-72 sm:h-72 ">
  <div class="text-lg font-bold font-['centaur'] text-center mb-2 text-gray-800 sm:text-3xl">
    {{ customTitles.IEM }}
  </div>
  <img src="/electro.png" alt="" class=" mx-auto mt-4 w-0 h-0 sm:w-20 sm:h-20" />
  <div class="text-1xl mb-2 font-['centaur'] text-center text-white">{{ formatValue(info.IEM) }}

<!-- Porcentaje en Números y Barra de Progreso -->
<div class="flex flex-col items-center justify-center h-full">
  <div class="relative w-32 h-8 mb-2 overflow-hidden rounded-full">
    <div :style="{ width: calculateProgress(info.IEM) + '%' }" class="absolute top-0 left-0 h-full bg-gray-800 sm:bg-teal-900 rounded-full"></div>
    <div class="w-full h-full bg-gray-300 rounded-full"></div>
  </div>
  <div class="text-sm font-bold text-gray-800">
    {{ Math.round(calculateProgress(info.IEM)) }}%
  </div>
</div>
  </div>
</div>
</div>
</div>

<div class="bg-cyan-800 rounded-full shadow-md p-6 w-44 h-44 sm:w-72 sm:h-72 mx-auto">
  <div class="text-lg font-bold font-['centaur'] text-center mb-2 text-gray-800 sm:text-3xl">
    {{ customTitles.IER }}
  </div>
  <img src="/renova.png" alt="" class=" mx-auto mt-4 w-0 h-0 sm:w-20 sm:h-20" />
  <div class="text-1xl mb-2 font-['centaur'] text-center text-white">{{ formatValue(info.IER) }}

<!-- Porcentaje en Números y Barra de Progreso -->
<div class="flex flex-col items-center justify-center h-full">
  <div class="relative w-32 h-8 mb-2 overflow-hidden rounded-full">
    <div :style="{ width: calculateProgress(info.IER) + '%' }" class="absolute top-0 left-0 h-full bg-gray-800 sm:bg-teal-900 rounded-full"></div>
    <div class="w-full h-full bg-gray-300 rounded-full"></div>
  </div>
  <div class="text-sm font-bold text-gray-800">
    {{ Math.round(calculateProgress(info.IER)) }}%

  </div>
</div>
</div>
</div>
</div>
</div>
</body>
</template>

<script setup>
import { onMounted, ref } from 'vue';


const info = ref('');
const isLoading = ref(true);
const customTitles = {
  periodo: 'Periodo',
  inicio: 'Inicio de evaluación',
  fin: 'Fin de evaluación',
  alTotal: 'Total de alumnos',
  alEvaluados: 'Total de evaluaciones',
  alListas: 'Evaluaciones Listas',
  alFaltantes: 'Evaluaciones Faltantes',
  ISC: 'ISC',
  II: 'II',
  IEM: 'IEM',
  IER: 'IER',
  IE: 'IE'
};

async function fetchData() {
  try {
    const response1 = await fetch('https://sitmotul.com.mx/api/statusEval');
    const data1 = await response1.json();

    const response2 = await fetch('https://sitmotul.com.mx/api/statusEvalIng');
    const data2 = await response2.json();

    // Combina los datos de ambas API
    info.value = {
      ...data1,
      ...data2,
    };

    isLoading.value = false;
  } catch (error) {
    console.error('Error al obtener datos:', error);
  }
}

function formatValue(value) {
if (typeof value === 'object') {
  const sum = value.faltantes + value.listas;
  const remaining = sum - value.listas;
  return `${value.listas} de ${sum} completadas`;
} else {
  return value;
}
}

function calculateHoursRemaining(deadline) {
  const fechaLimite = new Date(deadline);
  const ahora = new Date();

  // Calcula la diferencia en horas
  const diferenciaHoras = Math.floor((fechaLimite - ahora) / (1000 * 60 * 60));

  return `${diferenciaHoras} horas`;
}

function formatDate(dateString) {
// Convierte la cadena de fecha a objeto Date
const dateObject = new Date(dateString);

// Obtiene el año, mes y día
const year = dateObject.getFullYear();
const month = (dateObject.getMonth() + 1).toString().padStart(2, '0'); // Añade cero al principio si es necesario
const day = dateObject.getDate().toString().padStart(2, '0'); // Añade cero al principio si es necesario

// Formatea la fecha como "YYYY-MM-DD"
const formattedDate = `${year}-${month}-${day}`;

return formattedDate;
}

function calculateProgress(metric) {
if (typeof metric === 'object') {
  const sum = metric.faltantes + metric.listas;
  const progress = (metric.listas / sum) * 100;
  return progress;
} else {
  // Si no es un objeto, asumimos que es un valor directo y retornamos el valor mismo
  return metric;
}
}


onMounted(() => {
  fetchData();
});
</script>
