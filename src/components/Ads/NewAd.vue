<template>
    <v-container>
        <v-layout row>
            <v-flex xs12 sm6 offset-sm3>
                <h1 class="text--secondary mb-3">Create new ad</h1>
                <v-form
                        ref="form"
                        v-model="valid"
                        validation
                        class="mb-3"
                >
                    <v-text-field
                            ref="title"
                            label="Ad title"
                            type="text"
                            v-model="title"
                            :rules="[() => !!title || 'Title is required']"
                    />

                    <!--<v-text-field
                            ref="description"
                            label="Ad description"
                            type="text"
                            v-model="description"
                            :rules="[() => !!description || 'Description is required']"
                    />-->
                    <v-textarea
                            ref="description"
                            label="Ad description"
                            v-model="description"
                            :rules="[() => !!description || 'Description is required']"
                    >

                    </v-textarea>
                </v-form>
                <v-layout row class="mb-3">
                    <v-flex xs12>
                        <v-btn class="warning ma-2">
                            Upload
                            <v-icon right dark>mdi-cloud-upload</v-icon>
                        </v-btn>
                    </v-flex>
                </v-layout>

                <v-layout row>
                    <v-flex xs12>
                        <img src="" height="100">
                    </v-flex>
                </v-layout>
                <v-layout row>
                    <v-flex xs12>
                        <v-switch
                                class="ma-2"
                                label="Add to promo?"
                                v-model="promo"
                                color="primary"
                        ></v-switch>
                    </v-flex>
                </v-layout>
                <v-layout row>
                    <v-flex xs12>
                        <v-spacer></v-spacer>
                        <v-btn
                                :disabled="!valid"
                                class="success ma-2"
                                @click="createAd"
                        >Create ad
                        </v-btn>
                    </v-flex>
                </v-layout>
            </v-flex>
        </v-layout>
    </v-container>
</template>

<script>
    export default {
        data:  () => ({
            title: '',
            description: '',
            promo: false,
            valid: false
        }),
        methods: {
            createAd () {
                if (this.$refs.form.validate()) {
                    // logic
                    const ad = {
                        title: this.title,
                        description: this.description,
                        promo: this.promo
                    }

                    console.log(ad)
                }
            }
        }
    }
</script>