<template>
    <v-container>
        <v-row>
            <v-col cols="12">
                <v-card class="mt-5">
                    <v-img height="300px" :src="ad.src"></v-img>
                    <v-card-text>
                        <v-card-text>
                            <v-text-field name="title" label="Title" type="text" v-model="editedTitle">
                            </v-text-field>
                            <v-textarea name="desc" label="Description" type="text" v-model="editedDesc"
                                class="mb-3"></v-textarea>
                        </v-card-text>
                        <h1 class="text--primary mb-3">{{ ad.title }}</h1>
                        <p>{{ ad.desc }}</p>
                    </v-card-text>
                    <v-card-actions>
                        <v-spacer></v-spacer>
                        <modal-dialog :ad="ad" v-if="isOwner"></modal-dialog>
                        <buy-ad-modal :ad="ad"></buy-ad-modal>
                    </v-card-actions>
                </v-card>
            </v-col>
        </v-row>
    </v-container>
</template>

<script>
import EditAdModal from './EditAdModal'
export default {
    props: ['id'],
    computed: {
        ad() {
            const id = this.id
            return this.$store.getters.adById(id)
        }
    },
    components: {
        'modal-dialog': EditAdModal
    }
} 
</script>