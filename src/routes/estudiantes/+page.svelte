<script>
    import Navbar from "../../lib/components/Navbar.svelte";
    import Footer from "../../lib/components/Footer.svelte";

    let estudiante = {
        nombre: '',
        apellido: '',
        edad: ''
    };

    let mostrarDatos = false;

    function handleClick() {
        mostrarDatos = true;
    }
</script>

<Navbar/>

<div class="container">
    <h2 class=" mb-4">Registro de Estudiante</h2>

    <form class="mb-4">
        <div class="mb-3">
            <label for="nombre" class="form-label">Nombre:</label>
            <input
                type="text"
                id="nombre"
                bind:value={estudiante.nombre}
                class="form-control"
                required
            />
        </div>

        <div class="mb-3">
            <label for="apellido" class="form-label">Apellido:</label>
            <input
                type="text"
                id="apellido"
                bind:value={estudiante.apellido}
                class="form-control"
                required
            />
        </div>

        <div class="mb-3">
            <label for="edad" class="form-label">Edad:</label>
            <input
                type="number"
                id="edad"
                bind:value={estudiante.edad}
                class="form-control"
                required
            />
        </div>

        <button
            type="button"
            on:click={handleClick}
            class="btn btn-primary"
        >
            Guardar Datos
        </button>
    </form>

    {#if mostrarDatos}
        <div >
            <h2 class="mb-2">Datos del Estudiante:</h2>
            <p><strong>Nombre:</strong> {estudiante.nombre}</p>
            <p><strong>Apellido:</strong> {estudiante.apellido}</p>
            <p><strong>Edad:</strong> {estudiante.edad} años</p>
        </div>
    {/if}
</div>

<Footer/>