<template>
    <div v-if="links.length > 3">
        <div class="flex flex-wrap -mb-1">
            <template v-for="(link, key) in links">
                <div
                    v-if="link.url === null"
                    :key="key"
                    class="
                        px-4
                        py-3
                        mb-1
                        mr-1
                        text-sm
                        leading-4
                        text-gray-400
                        border
                        rounded
                    "
                    v-html="link.label"
                />
                <Link
                    v-else
                    class="
                        px-4
                        py-3
                        mb-1
                        mr-1
                        text-sm
                        leading-4
                        border
                        rounded
                        hover:bg-white
                        focus:border-indigo-500 focus:text-indigo-500
                        text-gray-500 px-1
                    "
                    :class="{ 'bg-red': link.active }"
                    :href="link.url"
                    v-html="link.label"
                />
            </template>
        </div>
    </div>
</template>

<script>

export default {

    props: {
        links: Array,
    },
};
</script>
