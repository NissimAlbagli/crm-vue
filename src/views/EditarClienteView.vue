<script setup>
    import ClienteService from '../services/ClienteService';
    import { FormKit} from '@formkit/vue';
    import {useRouter} from 'vue-router';
    import RouterLink from '../components/UI/RouterLink.vue';
    import Heading from '../components/UI/Heading.vue';

    const router = useRouter();

    defineProps({
        titulo: {
            type: String
        }
    })

    const handleSubmit = (data) => {
        
    }
</script>

<template>
    <div>
        <div class="flex justify-end">
            <RouterLink to='listado-clientes'>
                Volver
            </RouterLink>
        </div>

        <Heading>{{  titulo  }}</Heading>

        <div class="mx-auto mt-10 bg-white shadow">
            <div class="mx-auto md:w-2/3 py-20 px-6">
            <FormKit
                type="form"
                submit-label="Agregar Cliente"
                incomplete-message="No se pudo enviar, revisa los mensajes"
                @submit="handleSubmit"
            >

                <FormKit 
                    type="text"
                    label="Nombre"
                    name="nombre"
                    placeholder="Nombre del Cliente"
                    validation="required"
                    :validation-messages="{required: 'El Nombre del Cliente es Obligatorio'}"
                />

                <FormKit 
                    type="text"
                    label="Apellido"
                    name="apellido"
                    placeholder="Apellido del Cliente"
                    validation="required"
                    :validation-messages="{required: 'El Apellido del Cliente es Obligatorio'}"
                />

                <FormKit 
                    type="text"
                    label="Email"
                    name="email"
                    placeholder="Email del Cliente"
                    validation="required|email"
                    :validation-messages="{required: 'El Email del Cliente es Obligatorio', email: 'Coloca un Email valido'}"
                />

                <FormKit 
                    type="text"
                    label="Teléfono"
                    name="telefono"
                    placeholder="Teléfono: XXX-XXX-XXXX"
                    validation="?matches:/^[0-9]{3}-[0-9]{3}-[0-9]{4}$/"
                    :validation-messages="{ matches: 'El Formato no es valido'}"
                />

                <FormKit 
                    type="text"
                    label="Empresa"
                    name="empresa"
                    placeholder="Empresa del Cliente"
                />

                <FormKit 
                    type="text"
                    label="Puesto"
                    name="puesto"
                    placeholder="Puesto del Cliente"
                />

                </FormKit>
            </div>
        </div>
    </div>
</template>

<style>
    .formkit-wrapper {
        max-width: 100%;
    }
</style>