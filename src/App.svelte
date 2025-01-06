<script>
    import { onMount } from 'svelte';
    let fechaInicio = '';
    let fechaFin = '';
    let gastos = [];

    // Función para obtener los datos de la API
    const filtrarGastos = async () => {
        if (!fechaInicio || !fechaFin) {
            alert("Por favor, selecciona las fechas");
            return;
        }

        try {
            const response = await fetch(`https://coregastos20250105182941.azurewebsites.net/api/gastos/filtrar?fechaInicio=${fechaInicio}&fechaFin=${fechaFin}`);
            if (!response.ok) throw new Error("Error al obtener los datos");
            gastos = await response.json();
        } catch (error) {
            console.error(error);
            alert("No se pudieron obtener los datos");
        }
    };
</script>

<main>
    <h1>Gestión de Gastos</h1>
    <div>
        <label for="fechaInicio">Fecha Inicio:</label>
        <input type="date" bind:value={fechaInicio} id="fechaInicio" />

        <label for="fechaFin">Fecha Fin:</label>
        <input type="date" bind:value={fechaFin} id="fechaFin" />

        <button on:click={filtrarGastos}>Filtrar</button>
    </div>

    <table>
        <thead>
            <tr>
                <th>Departamento</th>
                <th>Total</th>
            </tr>
        </thead>
        <tbody>
            {#each gastos as gasto}
                <tr>
                    <td>{gasto.departamento}</td>
                    <td>${gasto.total.toFixed(2)}</td>
                </tr>
            {/each}
        </tbody>
    </table>
</main>

<style>
    main {
        font-family: Arial, sans-serif;
        padding: 20px;
    }

    table {
        width: 100%;
        border-collapse: collapse;
        margin-top: 20px;
    }

    th, td {
        border: 1px solid #ddd;
        padding: 8px;
        text-align: left;
    }

    th {
        background-color: #f4f4f4;
    }
</style>
