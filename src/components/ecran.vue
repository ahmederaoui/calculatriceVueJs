<template>
    <tr>
        <td colspan="5">
            <input type="text"  id="ecran"  size="12"  v-model="this.val" >
        </td>
    </tr>
</template>

<script>
export default {
    props:['val'],

    

}
</script>

<style>
#ecran{
    background: black;
    color: white;
    box-sizing: border-box;
    padding: 6px;
    text-align: right;
    font-size: 1.5em;
    width: 100%;
}


</style>