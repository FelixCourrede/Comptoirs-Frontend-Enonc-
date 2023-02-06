<script setup>
    function getCat(){
        const url='https://springajax.herokuapp.com/api';
        let fetchOptions = { method: "GET"};
        fetch(url, fetchOptions)
        .then((response) => {
           console.log(response)
           return response.json();
        })
        .then((datajson) => {
            console.log(datajson)
            let categories=datajson;
            console.log(categories)
            let html="";
            for(let k of categories){
                html+='<tr><td>'+categories.libelle+'</td><td>'+categories.description+'</td></tr>';
            }
            document.getElementById('corps').innerHTML=html;
        })
    }
    getCat();
</script>

<template>
    <table>
        <thead>
            <tr>
                <th>Nom</th>
                <th>Prix</th>
                <th>Stock</th>
                <th>Commandés</th>
            </tr>
        </thead>
        <tbody id="corps">

        </tbody>
    </table>
</template>