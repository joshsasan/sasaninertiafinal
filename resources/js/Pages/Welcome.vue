<script setup>
import { Head, Link } from '@inertiajs/vue3';

defineProps({
    canLogin: {
        type: Boolean,
    },
    canRegister: {
        type: Boolean,
    },
    laravelVersion: {
        type: String,
        required: true,
    },
    phpVersion: {
        type: String,
        required: true,
    },
});

function handleImageError() {
    document.getElementById('screenshot-container')?.classList.add('!hidden');
    document.getElementById('docs-card')?.classList.add('!row-span-1');
    document.getElementById('docs-card-content')?.classList.add('!flex-row');
    document.getElementById('background')?.classList.add('!hidden');
}
</script>

<template>
    <Head title="Welcome" />
    <div class="bg-blue-300 text-white relative min-h-screen flex flex-col justify-between">
        <div class="relative w-full max-w-2xl px-6 lg:max-w-7xl mx-auto">
            <header class="flex justify-between items-center py-10">
                <div class="flex">
                    <svg
                        class="h-12 w-auto lg:h-16"
                        viewBox="0 0 62 65"
                        fill="none"
                        xmlns="http://www.w3.org/2000/svg"
                    >
                        <!-- SVG content -->
                    </svg>
                </div>
            </header>

            <div class="flex justify-center items-center">
                <div class="shadow-md p-8 rounded-md bg-white dark:bg-gray-500 w-full max-w-md">
                    <nav v-if="canLogin" class="flex flex-col items-center space-y-4">
                        <Link
                            v-if="$page.props.auth.user"
                            :href="route('dashboard')"
                            class="block w-full text-center rounded-md px-3 py-2 text-black ring-1 ring-transparent transition hover:text-black/70 focus:outline-none focus-visible:ring-[#FF2D20] dark:text-white dark:hover:text-white/80 dark:focus-visible:ring-white"
                        >
                            Dashboard
                        </Link>

                        <template v-else>
                            <Link
                                :href="route('login')"
                                class="block w-full text-center rounded-md px-3 py-2 text-black ring-1 ring-transparent transition hover:text-black/70 focus:outline-none focus-visible:ring-[#FF2D20] dark:text-white dark:hover:text-white/80 dark:focus-visible:ring-white"
                            >
                                Log in
                            </Link>

                            <Link

                                v-if="canRegister"
                                :href="route('register')"
                                class="block w-full text-center rounded-md px-3 py-2 text-black ring-1 ring-transparent transition hover:text-black/70 focus:outline-none focus-visible:ring-[#FF2D20] dark:text-white dark:hover:text-white/80 dark:focus-visible:ring-white"
                            >
                                Register
                            </Link>
                        </template>
                    </nav>
                </div>
            </div>

            <footer class="py-6 text-center text-sm text-black dark:text-white/70">
                All rights reserve Inertia Final Project 2024
            </footer>
        </div>
    </div>
</template>
