<template>
   <div id="burger-table">
    <div>
        <div id="burger-table-heading">
            <div class="order-id">#:</div>
            <div>Cliente:</div>
            <div>Pão:</div>
            <div>Carne:</div>
            <div>Opcionais:</div>
            <div>Ações</div>
        </div>
        <div id="burger-table-rows">
            <div class="burger-table-row">
                <div class="order-number">1</div>
                <div>Nome</div>
                <div>Pão</div>
                <div>Carne</div>
                <div>
                    <ul>
                        <li>Salame</li>
                        <li>Tomate</li>
                    </ul>
                </div>
                <div>
                    <select name="status" class="status">
                        <option value="">Selecione</option>
                    </select>
                    <button class="delete-btn">Cancelar</button>
                </div>
            </div>
        </div>

        <div id="burger-table-rows">
            <div class="burger-table-row">
                <div class="order-number">1</div>
                <div>Nome</div>
                <div>Pão</div>
                <div>Carne</div>
                <div>
                    <ul>
                        <li>Salame</li>
                        <li>Tomate</li>
                    </ul>
                </div>
                <div>
                    <select name="status" class="status">
                        <option value="">Selecione</option>
                    </select>
                    <button class="delete-btn">Cancelar</button>
                </div>
            </div>
        </div>
    </div>
   </div>
</template>

<script>
export default {
    name: "Dashboard"
}
</script>

<style scoped>
    #burger-table {
        max-width: 1200px;
        margin: 0 auto;
        height: 100vh;
    }

    #burger-table-heading,
    #burger-table-rows,
    .burger-table-row {
        display: flex;
        flex-wrap: wrap;
    }

    #burger-table-heading {
        font-weight: bold;
        padding: 12px;
        border-bottom: 3px solid #9e6e26;
    }

    #burger-table-heading div,
    .burger-table-row div {
        width: 19%;
    }

    .burger-table-row {
        width: 100%;
        padding: 12px;
        border-bottom: 1px solid #9e6e26;
    }

     #burger-table-heading .order-id,
     .burger-table-row .order-number {
        width: 5%;
     }

     select {
        padding: 8px 3px;
        margin-right: 12px;
     }

     .delete-btn {
        background-color: #c29045;
        color: #222;
        border: 1px solid #222;
        padding: 7px;
        font-size: 16px;
        margin: 0 auto;
        cursor: pointer;
        letter-spacing: 1px;
        font-weight: bold;
         transition: .5s;
     }

     .delete-btn:hover {
        color: rgb(7, 7, 7);
     }

</style>