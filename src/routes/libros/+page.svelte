<script>
    import Navbar from "../../lib/components/Navbar.svelte";
    import Footer from "../../lib/components/Footer.svelte";

    let numeros = $state({
        numero1: 0,
        numero2: 0
    });

    let resultado = $state(0);
    let mostrarResultado = $state(false);

    function calcularSuma() {
        resultado = Number(numeros.numero1) + Number(numeros.numero2);
        mostrarResultado = true;
    }
</script>

<Navbar/>

<div class="container">
    <h2 class="mb-4">Calculadora de Suma</h2>

    <form class="mb-4">
        <div class="mb-3">
            <label for="numero1" class="form-label">Primer número:</label>
            <input
                type="number"
                id="numero1"
                bind:value={numeros.numero1}
                class="form-control"
                required
            />
        </div>

        <div class="mb-3">
            <label for="numero2" class="form-label">Segundo número:</label>
            <input
                type="number"
                id="numero2"
                bind:value={numeros.numero2}
                class="form-control"
                required
            />
        </div>

        <button
            type="button"
            onclick={calcularSuma}
            class="btn btn-primary"
        >
            Calcular Suma
        </button>
    </form>

    {#if mostrarResultado}
        <div>
            <h2 class="text-xl font-bold mb-2">Resultado:</h2>
            <p><strong>La suma de {numeros.numero1} + {numeros.numero2} es:</strong> {resultado}</p>
        </div>
    {/if}
</div>

<Footer/>