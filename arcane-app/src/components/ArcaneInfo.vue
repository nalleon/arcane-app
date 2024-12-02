<template>
    <div class="container">
        <div class="row">
            <div class="col-sm-12 col-md-6">
                <form action="">
                    <div class="form-group">
                        <label for="name">Nombre</label>
                        <input type="text" class="form-control" id="name" v-model="ArcaneCharacter.name">
                    </div>
                    <div class="form-group">
                        <label for="origin">Origen</label>
                        <input type="text" class="form-control" id="origin" v-model="ArcaneCharacter.origins">
                    </div>
                    <div class="form-group">
                        <label for="specialAbility">Habilidad especial</label>
                        <input type="text" class="form-control" id="specialAbility" v-model="ArcaneCharacter.specialAbility">
                    </div>
                    <div class="form-group">
                        <label for="allies">Aliados</label>
                        <input type="text" class="form-control" id="allies" v-model="ArcaneCharacter.allies">
                    </div>
                    <div class="form-group">
                        <label for="missionFulfilled">Misión cumplida</label>
                        <input type="text" class="form-control" id="missionFulfilled" v-model="ArcaneCharacter.missionFulfilled">
                    </div>

                    <button type="submit" class="btn btn-sucess">Add character</button>

                </form>
            </div>

            <!--
                Table of registered characters
            -->
            <div class="col-sm-12 col-md-6">
                <table style="border: 1px solid black;">
                    <!--Header-->
                    <tr>
                        <th>Nombre</th>
                        <th>Origen</th>
                        <th>Habilidad especial</th>
                        <th>Lista de Aliados</th>
                        <th>Misión cumplida</th>
                    </tr>
                    <!--Data-->
                    <tr v-for="ch in characters" :key="ch.id">
                        <td>{{ ch.name }}</td>
                        <td>{{ ch.origins }}</td>
                        <td>{{ ch.specialAbility }}</td>
                        <td>{{ ch.allies }}</td>
                        <td>{{ ch.missionFulfilled }}</td>
                    </tr>
                </table>
            </div>
        </div>
    </div>
</template>

<script>
    import { DefineComponent } from 'vue';
    export default defineComponent({
        name:'ArcaneInfo',

        setup() {
            
            type ArcaneCharacter = {
                name: string,
                origins: string,
                specialAbility: string,
                allies: string,
                missionFulfilled: boolean
            } 

            
        }
    });
</script>

<style>
</style>