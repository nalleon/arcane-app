<template>
    <div class="container mt-4">
        <div class="row">
            <div class="col-12 col-xl-6 mt-5 mb-5">
                <div class="card">
                    <div class="card-header">
                        <h4 class="fw-bold text-uppercase">Agregar Personaje</h4>
                    </div>
                    <div class="card-body">
                        <form @submit.prevent="addCharacter">
                            <div class="row">
                                <div class="col-6 form-group">
                                    <label for="name" class="fw-bold text-uppercase">Nombre</label>
                                    <input type="text" class="form-control custom-input" id="name" v-model="name" placeholder="Nombre del personaje" required />
                                </div>
                                <div class="col-6 form-group">
                                    <label for="origin" class="fw-bold text-uppercase">Origen</label>
                                    <input type="text" class="form-control custom-input" id="origin" v-model="origins" placeholder="Origen del personaje"  required />
                                </div>
                            </div>
        
                            <div class="col-12 form-group mt-3">
                                <label for="specialAbility" class="fw-bold text-uppercase">Habilidad especial</label>
                                <input type="text" class="form-control custom-input" id="specialAbility" v-model="specialAbility" placeholder="Habilidad única/especial del personaje"  required />
                            </div>
                            <div class="row">
                                <div class="col-12 mt-3 mb-3">
                                    <label class="form-check-label fw-bold text-uppercase" for="missionFulfilled" >Misión cumplida: </label>
                                    <input class="form-check-input ms-1 custom-input custom-checkbox" type="checkbox" value="true" id="missionFulfilled">
                                    <label class="form-check-label ms-2" for="missionFulfilled">
                                        Sí
                                    </label>
                                </div>
                            </div>
                            <div class="col-12 form-group mb-3">
                                <label for="allies" class="fw-bold text-uppercase">Aliados</label>
                                <input type="text" class="form-control custom-input" id="allies" v-model="allies" placeholder="Aliados del personaje"  required />
                            </div>
                            
                            <div class="col-12">
                                <button type="submit" class="btn btn-success custom-btn">Añadir</button>
                            </div>
                        </form>
                    </div>
                </div>
            </div>

            <!-- Table -->
            <div class="col-12 col-xl-6 mt-5 mb-5">
                <div class="card">
                    <div class="card-header">
                        <h4 class="fw-bold text-uppercase"> Registrados</h4>
                    </div>
                    <div class="card-body">
                        <table class="table table-striped table-bordered table-hover table-success">
                            <thead>
                                <tr>
                                    <th>Nombre</th>
                                    <th>Origen</th>
                                    <th>Habilidad especial</th>
                                    <th>Aliados</th>
                                    <th>Misión cumplida</th>
                                </tr>
                            </thead>
                            <tbody>
                                <tr v-for="ch in characters" :key="ch.name">
                                    <td>{{ ch.name }}</td>
                                    <td>{{ ch.origins }}</td>
                                    <td>{{ ch.specialAbility }}</td>
                                    <td>{{ ch.allies.join(', ') }}</td>
                                    <td>{{ ch.missionFulfilled ? 'Sí' : 'No' }}</td>
                                </tr>
                            </tbody>
                        </table>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup>
    import { ref } from 'vue';

    /**
     * Properties
     */
    const characters = ref([
        {
            name: 'Jinx',
            origins: 'Piltover',
            specialAbility: 'Manipulación de explosivos',
            allies: ['Ekko'],
            missionFulfilled: true
        },
        {
            name: 'Vi',
            origins: 'Zaun',
            specialAbility: 'Combate cuerpo a cuerpo',
            allies: ['Caitlyn'],
            missionFulfilled: false
        }
    ]);

    const name = ref('');
    const origins = ref('');
    const specialAbility = ref('');
    const allies = ref([]);
    const missionFulfilled = ref(false);

    /**
     * Function to add a character to the array of characters
     */
    const addCharacter = () => {
        const alliesList = allies.value.split(',').map(allie => allie.trim());

        const newCharacter = {
            name: name.value,
            origins: origins.value,
            specialAbility: specialAbility.value,
            allies: alliesList,
            missionFulfilled: missionFulfilled.value,
        };

        characters.value.push(newCharacter);

        putDefaultValues();
    };


    /**
     * Function to reset the form inputs and set default values
     */
    const putDefaultValues = () => {
        name.value = '';
        origins.value = '';
        specialAbility.value = '';
        allies.value = '';
        missionFulfilled.value = false;
    }

</script>

<style scoped>
.custom-btn {
    background-color: rgb(94, 147, 94);
    border-radius: 30px;
    padding: 10px 20px;
    cursor: pointer;
    transition: transform 0.3s ease, box-shadow 0.3s ease; 

}

.custom-btn:hover{
    transform: scale(1.1); 
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.3);
}

.custom-input{
    border-radius: 10px;
    padding: 5px 10px;
    border: 1px solid #ababab;
    transition: border-color 0.3s ease;
}

.custom-input:focus{
    border-color: rgb(94, 147, 94);
    border-width: 2px;
}

.custom-input:hover{
    transform: scale(1.03); 
    box-shadow: 1px 4px 20px rgba(0, 0, 0, 0.3);
}

.custom-checkbox:checked{
    background-color: rgb(94, 147, 94);
    border-color: rgb(94, 147, 94);
}

</style>
