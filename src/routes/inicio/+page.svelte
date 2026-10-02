<script>
    import Navbar from "../../lib/components/Navbar.svelte";
    import Footer from "../../lib/components/Footer.svelte";
    import { onMount } from 'svelte';

    let todos = [];
    let loading = true;
    let error = null;

    onMount(async () => {
        try {
            const response = await fetch('https://jsonplaceholder.typicode.com/todos');
            if (!response.ok) throw new Error('Error al cargar los datos');
            todos = await response.json();
        } catch (e) {
            error = e.message;
        } finally {
            loading = false;
        }
    });
</script>

<Navbar/>

<div class="container p-4">
    <h2 class="mb-4">Lista de Tareas</h2>
    {#if loading}
        <p class="text-center">Cargando datos...</p>
    {:else if error}
        <p class="text-red-500">Error: {error}</p>
    {:else}
        <div class="overflow-x-auto">
            <table class="min-w-full bg-white border border-gray-300">
                <thead class="bg-gray-100">
                    <tr>
                        <th class="px-4 py-2 border">ID</th>
                        <th class="px-4 py-2 border">Usuario ID</th>
                        <th class="px-4 py-2 border">Título</th>
                        <th class="px-4 py-2 border">Completado</th>
                    </tr>
                </thead>
                <tbody>
                    {#each todos as todo}
                        <tr class="hover:bg-gray-50">
                            <td class="px-4 py-2 border">{todo.id}</td>
                            <td class="px-4 py-2 border">{todo.userId}</td>
                            <td class="px-4 py-2 border">{todo.title}</td>
                            <td class="px-4 py-2 border">
                                <span class={todo.completed ? "text-green-600" : "text-red-600"}>
                                    {todo.completed ? "Sí" : "No"}
                                </span>
                            </td>
                        </tr>
                    {/each}
                </tbody>
            </table>
        </div>
    {/if}
</div>

<Footer/>