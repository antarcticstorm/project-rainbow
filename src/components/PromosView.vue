<template>
    <p>{{promoType}}</p>
    <table id="search-table">
        <thead>
            <tr>
                <th>
                    <span class="flex items-center">
                        Name
                    </span>
                </th>
                <th>
                    <span class="flex items-center">
                        Ticker
                    </span>
                </th>
                <th>
                    <span class="flex items-center">
                        Stock Price
                    </span>
                </th>
                <th>
                    <span class="flex items-center">
                        Market Capitalization
                    </span>
                </th>
            </tr>
        </thead>
        <tbody>
            <template v-for="promo in promos" :key="promo.id">
                <tr v-if="promo.approved == 'Yes' && promo.promo_type == promoType">
                    <td class="font-medium text-gray-900 whitespace-nowrap dark:text-white" @click="showModal(promo)">{{promo.name}}</td>
                    <PopupModal v-model="dialog" ref="modal" :key="promo.id" :isOpen="isOpen" :popupType="popupType" :popupData="promo"></PopupModal>
                </tr>
            </template>
        </tbody>
    </table>

</template>

<script>
import promoData from '@/json/promos.json'
import PopupModal from '@/components/PopupModal.vue'
export default {
    name: 'PromosView',
    props: {
        promoType: String
    },
    data() {
        return { 
            promos: promoData,
            isOpen: false,
            popupType: "promo",
            popupData: {}
        }
    },
    components: {
        PopupModal,
    },
    methods: {
        modalId(x) {
            return x.slug + "-" + x.id;
        },
        showModal(json) {
            this.isOpen = true,
            this.popupType = "promo",
            this.popupData = '{' + json + '}'
        }
    }
}
</script>