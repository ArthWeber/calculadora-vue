<script setup>

const props = defineProps(["num1", "num2", "operacao"]);
const emit = defineEmits(["update:num1", "update:num2", "update:operacao"]);
</script>

<template>
    <div class="row align-items-center g-3 text-center">
        <!-- Primeiro valor -->
        <div class="col-5">
            <input type="number" class="form-control form-control-lg text-end fw-bold" :value="props.num1"
                @input="emit('update:num1', $event.target.valueAsNumber)" placeholder="Primeiro valor" />
        </div>

        <!-- Operação -->
        <div class="col-2 d-flex justify-content-center">
            <select class="form-select form-select-lg fw-bold bg-dark text-light text-center w-75"
                :value="props.operacao" @change="emit('update:operacao', $event.target.value)">
                <option value="soma">+</option>
                <option value="subtracao">-</option>
                <option value="multiplicacao">×</option>
                <option value="divisao">÷</option>
            </select>
        </div>

        <!-- Segundo valor -->
        <div class="col-5">
            <input type="number" class="form-control form-control-lg text-end fw-bold" :value="props.num2"
                @input="emit('update:num2', $event.target.valueAsNumber)" placeholder="Segundo valor" />
        </div>
    </div>
</template>