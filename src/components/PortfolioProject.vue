<template>
    <v-flex xs12 sm10 md6 lg6>
        <v-card class="ma-3" dark>

            <v-card-title class="grad-blue-ldl justify-center title font-weight-bold">
                {{ title }}
            </v-card-title>

            <v-card-text class="description pa-4">
                <p>{{ description }}</p>
            </v-card-text>

            <v-card-actions class="grad-blue-ldl">
                <v-flex>
                    <v-btn 
                    v-for="tag in tags" 
                    :key="tag.name" 
                    round 
                    left 
                    class="grad-blue-dl mt-3 mr-3 mb-2 pr-2"  
                    :href="tag.link" target="_blank" rel="noopener noreferrer"
                    :title="tag.name">

                        <v-icon 
                        v-if="tag.icon_origin === 'mdi'" 
                        class="mr-1">
                            {{ tag.icon }}
                        </v-icon>

                        <i 
                        v-else-if="is_fa(tag.icon_origin)" 
                        :class="get_fa_class(tag.icon_origin, tag.icon)"
                        class="mr-1">
                        </i>

                        <img 
                        v-else-if="tag.icon_origin === 'assets'" 
                        class="icon mr-1" 
                        :src="require('../assets/' + tag.icon)" 
                        :alt="tag.name" />

                        {{tag.name}}
                    </v-btn>
                </v-flex>
            </v-card-actions>
        </v-card>
    </v-flex>
</template>

<script>
import AssetSourceManager from '../mixins/AssetSourceManager.js'

export default {
    name: 'PortfolioProject',
    props: {
        project: {
            type: Object,
            required: true
        }
    },
    data() {
        return {
            title: this.project.title,
            description: this.project.description,
            tags: this.project.tags
        }
    },
    mixins: [AssetSourceManager]
}
</script>