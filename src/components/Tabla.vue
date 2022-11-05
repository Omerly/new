<template>
    <v-data-table
    :headers="headers"
    :items="lectores"
    :search="search"
    >
        <template v-slot:top>
        <v-toolbar >
            <v-toolbar-title>Lectores</v-toolbar-title>
            <v-divider
            class="mx-4"
            inset
            vertical
            ></v-divider>
            <v-spacer></v-spacer>
            <v-text-field class="text-xs-center" v-model="search" append-icon="search" label="Buscar" single-line="" hide-details=""></v-text-field>
            <v-spacer></v-spacer>
            <v-dialog v-model="dialog" max-width="500px">
            <!--<template v-slot:activator="{ on }">
                <v-btn color="primary" dark class="mb-2" v-on="on">Nuevo Lector</v-btn>
            </template>-->
            <v-card>
                <v-card-title>
                <span class="headline">{{ formTitle }}</span>
                </v-card-title>

                <v-card-text>
                <v-container>
                    <v-row>
                    <v-col cols="12" sm="6" md="4">
                        <v-text-field  label="Id"></v-text-field>
                    </v-col>
                    <v-col cols="12" sm="6" md="4">
                        <v-text-field label="Nombre"></v-text-field>
                    </v-col>
                    <v-col cols="12" sm="6" md="4">
                        <v-text-field label="Apellido"></v-text-field>
                    </v-col>
                    <v-col cols="12" sm="6" md="4">
                        <v-text-field label="Libros Leídos"></v-text-field>
                    </v-col>
                    <v-col cols="12" sm="6" md="4">
                        <v-text-field label="Libros por leer"></v-text-field>
                    </v-col>
                    </v-row>
                </v-container>
                </v-card-text>

                <v-card-actions>
                <v-spacer></v-spacer>
                <!--<v-btn color="blue darken-1" text @click="">Cancelar</v-btn>
                <v-btn color="blue darken-1" text @click="">Guardar</v-btn>-->
                </v-card-actions>
            </v-card>
            </v-dialog>
        </v-toolbar>
        </template>
        <template v-slot:item.action="{}">
            <v-icon
            small
            class="mr-2"
            @click=""
            >
            create
            </v-icon>
                <v-icon
                small
                @click=""
                >
                delete
                </v-icon>
        </template>
        <template v-slot:no-data>
        <v-btn color="primary" @click="initialize">Reset</v-btn>
        </template>
    </v-data-table>
</template>

<script>
    export default{
        data: () => ({
            dialog: false,
            headers: [              
                { text: 'Id', value: 'id' },
                { text: 'Nombre', value: 'nombre' },
                { text: 'Apellido', value: 'apellido' },
                { text: 'Libros Leídos', value: 'leidos' },
                { text: 'Libros por leer', value: 'porleer' },
                { text: 'Acciones', value: 'action', sortable: false },
            ],
            lectores: [],
            search: '',
        }),

        created () {
        this.initialize()
        },
        
        methods: {
            initialize () {
            this.lectores = [
                {
                id: '0102',
                nombre: 'Adrián',
                apellido: 'Sanderson',
                leidos: 10,
                porleer: 23,
                },
                {
                id: '0154',
                nombre: 'Manuel',
                apellido: 'Soto',
                leidos: 4,
                porleer: 89,
                },
                {
                id: '0905',
                nombre: 'Karla',
                apellido: 'Valero',
                leidos: 42,
                porleer: 45,
                },
                {
                id: '0402',
                nombre: 'Milo',
                apellido: 'Villagil',
                leidos: 8,
                porleer: 68,
                },
                {
                id: '0408',
                nombre: 'John',
                apellido: 'Lincon',
                leidos: 70,
                porleer: 30,
                }
            ]
             },
        },
    }
</script>