<script>
    import moment from "moment";
    import {
        SvelteGantt,
        SvelteGanttTable,
        MomentSvelteGanttDateAdapter,
        SvelteGanttDependencies,
    } from "svelte-gantt/svelte";

    let currentStart = time("06:00");
    let currentEnd = time("18:00");

    export const data = {
        rows: [
            {
                id: 1,
                label: "Room 1",
                draggable: false,
            },
            {
                id: 2,
                label: "Room 2",
                draggable: false,
            },
            {
                id: 3,
                label: "Room 3",
                draggable: false,
            },
            {
                id: 4,
                label: "Room 4",
                draggable: false,
            },
            {
                id: 5,
                label: "Room 5",
                draggable: false,
            },
        ],
        tasks: [
            {
                id: 3,
                resourceId: 1,
                html: `
                <div class="w-full h-full flex justify-between items-center">
                    <div class="flex flex-col justify-center gap-2">
                        <span class="text-black font-bold">Strapi Test</span> 
                        <p class="text-xs">09:30AM - 11:00AM</p>
                    </div>

                    <div class="flex -space-x-2">
                        <img class="inline-block size-8 rounded-full ring-2 ring-white" src="https://images.unsplash.com/photo-1568602471122-7832951cc4c5?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=facearea&facepad=2&w=300&h=300&q=80" alt="Avatar">
                        <img class="inline-block size-8 rounded-full ring-2 ring-white" src="https://images.unsplash.com/photo-1531927557220-a9e23c1e4794?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=facearea&facepad=2&w=300&h=300&q=80" alt="Avatar">
                        <img class="inline-block size-8 rounded-full ring-2 ring-white" src="https://images.unsplash.com/photo-1541101767792-f9b2b1c4f127?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&&auto=format&fit=facearea&facepad=3&w=300&h=300&q=80" alt="Avatar">
                    </div>
                </div>
                `,
                from: time("09:30"),
                to: time("12:00"),
                classes: "bg-white border border-black !rounded-lg w-full truncate",
                resizable: false,
            },
            {
                id: 4,
                resourceId: 2,
                html: `
                <div class="w-full h-full flex justify-between items-center">
                    <div class="flex flex-col justify-center gap-2">
                        <span class="text-black font-bold">Strapi Test 1</span> 
                        <p class="text-xs">08:00AM - 10:00AM</p>
                    </div>

                    <div class="flex -space-x-2">
                        <img class="inline-block size-8 rounded-full ring-2 ring-white" src="https://images.unsplash.com/photo-1568602471122-7832951cc4c5?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=facearea&facepad=2&w=300&h=300&q=80" alt="Avatar">
                        <img class="inline-block size-8 rounded-full ring-2 ring-white" src="https://images.unsplash.com/photo-1531927557220-a9e23c1e4794?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=facearea&facepad=2&w=300&h=300&q=80" alt="Avatar">
                        <img class="inline-block size-8 rounded-full ring-2 ring-white" src="https://images.unsplash.com/photo-1541101767792-f9b2b1c4f127?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&&auto=format&fit=facearea&facepad=3&w=300&h=300&q=80" alt="Avatar">
                    </div>
                </div>
                `,
                from: time("08:00"),
                to: time("10:00"),
                classes: "bg-white border border-black !rounded-lg w-full truncate",
                resizable: false,
            },
            {
                id: 5,
                resourceId: 1,
                html: `
                <div class="w-full h-full flex justify-between items-center">
                    <div class="flex flex-col justify-center gap-2">
                        <span class="text-black font-bold">Strapi Test 2</span> 
                        <p class="text-xs">13:00AM - 14:00AM</p>
                    </div>

                    <div class="flex -space-x-2">
                        <img class="inline-block size-8 rounded-full ring-2 ring-white" src="https://images.unsplash.com/photo-1568602471122-7832951cc4c5?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=facearea&facepad=2&w=300&h=300&q=80" alt="Avatar">
                        <img class="inline-block size-8 rounded-full ring-2 ring-white" src="https://images.unsplash.com/photo-1531927557220-a9e23c1e4794?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=facearea&facepad=2&w=300&h=300&q=80" alt="Avatar">
                        <img class="inline-block size-8 rounded-full ring-2 ring-white" src="https://images.unsplash.com/photo-1541101767792-f9b2b1c4f127?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&&auto=format&fit=facearea&facepad=3&w=300&h=300&q=80" alt="Avatar">
                    </div>
                </div>
                `,
                from: time("13:00"),
                to: time("14:00"),
                classes: "bg-white border border-black !rounded-lg w-full truncate",
                resizable: false,
            },
            {
                id: 6,
                resourceId: 3,
                html: `
                <div class="w-full h-full flex justify-between items-center">
                    <div class="flex flex-col justify-center gap-2">
                        <span class="text-black font-bold">Strapi Test 3</span> 
                        <p class="text-xs">09:00AM - 11:00AM</p>
                    </div>

                    <div class="flex -space-x-2">
                        <img class="inline-block size-8 rounded-full ring-2 ring-white" src="https://images.unsplash.com/photo-1568602471122-7832951cc4c5?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=facearea&facepad=2&w=300&h=300&q=80" alt="Avatar">
                        <img class="inline-block size-8 rounded-full ring-2 ring-white" src="https://images.unsplash.com/photo-1531927557220-a9e23c1e4794?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=facearea&facepad=2&w=300&h=300&q=80" alt="Avatar">
                        <img class="inline-block size-8 rounded-full ring-2 ring-white" src="https://images.unsplash.com/photo-1541101767792-f9b2b1c4f127?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&&auto=format&fit=facearea&facepad=3&w=300&h=300&q=80" alt="Avatar">
                    </div>
                </div>
                `,
                from: time("09:00"),
                to: time("11:00"),
                classes: "bg-white border border-black !rounded-lg w-full truncate",
                resizable: false,
            },
        ],
        dependencies: [],
    };

    var options = {
        dateAdapter: new MomentSvelteGanttDateAdapter(moment),
        rows: data.rows,
        tasks: data.tasks,
        dependencies: data.dependencies,
        timeRanges: [],
        columnUnit: "minute",
        columnOffset: 30,
        magnetOffset: 15,
        rowHeight: 75,
        rowPadding: 5,
        layout: "expand",
        headers: [
            { unit: "day", format: "MMMM Do", sticky: true },
            { unit: "hour", format: "H:mm", sticky: true },
        ],
        fitWidth: true,
        minWidth: 800,
        from: currentStart,
        to: currentEnd,
        tableHeaders: [
            { title: "All Rooms", property: "label", width: 140, type: "tree" },
        ],
        tableWidth: 100,
        ganttTableModules: [SvelteGanttTable],
        ganttBodyModules: [SvelteGanttDependencies],
    };

    function time(input) {
        return moment(input, "HH:mm");
    }
</script>

<main class="w-full">
    <SvelteGantt {...options}></SvelteGantt>
</main>

<style scoped>
    :global(.header-container) {
        pointer-events: none;
    }

    :global(.sg-task-content) {
        width: 100%;
        padding-right: 14px;
    }
</style>
