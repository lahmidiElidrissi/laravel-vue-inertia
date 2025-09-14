<script setup lang="ts">
import AppLayout from '@/layouts/AppLayout.vue';
import { dashboard } from '@/routes';
import { type BreadcrumbItem } from '@/types';
import { Head } from '@inertiajs/vue3';
import PlaceholderPattern from '../components/PlaceholderPattern.vue';

const breadcrumbs: BreadcrumbItem[] = [
    {
        title: 'Dashboard',
        href: dashboard().url,
    },
];

defineProps<{ products: { id: number; name: string; price: number }[] }>();
</script>

<template>
    <Head title="Products" />
    <AppLayout :breadcrumbs="breadcrumbs">

        <div class="flex h-full flex-1 flex-col gap-4 overflow-x-auto rounded-xl p-4">
            <div v-if="products.length > 0">
                <ul class="list-inside list-disc space-y-2">
                    <li v-for="product in products" :key="product.id">
                        {{ product.id }} - {{ product.name }} - {{ product.price }}
                    </li>
                </ul>
            </div>
            <div v-else>
                <PlaceholderPattern />
            </div>
        </div>
    </AppLayout>
</template>
