<script>
	import Fa from "svelte-fa";
    import { faX } from '@fortawesome/free-solid-svg-icons'
	import { searchResult } from "$lib";

    let available_categories = []
    for ( let i = 0; i < searchResult.length; i++ ) {
        console.log(searchResult)
        available_categories.push(searchResult[i]["category"])
    }
    let categories_set = new Set(available_categories);

    function clear_name_input() {
        // document.getElementById("name_input").value = "";
    }

</script>

<section id="container">

    <section id="categories">
        <h3>
            Kategorie
        </h3>
        <div id="categories_container">
            {#each categories_set as cat}
                <div class="category_name">
                    {cat}
                </div>
            {/each}
        </div>
    </section>
    <section id="find_by_author">
        <h3>
            Autor
        </h3>
        <div id="input_and_button">
            <input type="text" id="name_input">
            <div class="icon" on:click={clear_name_input}>
                <Fa icon={ faX } color="antiquewhite"/>
            </div>
        </div>
    </section>

    <section id="find_by_publish_date">
        <h3>
            Data publikacji
        </h3>
        <p>
            <span>Od <input type="date" class="date_input"></span> <span>Do <input type="date" class="date_input"></span> </p>

    </section>
</section>

<style>
    #container {
        width: 75%;
    }
    h3, input, p {
        color: antiquewhite;
    }
    #find_by_publish_date p span {
        margin-top: 5px;
    }
    input {
        background: #303133;
        border: 2px solid antiquewhite;
        border-radius: 20px;
        text-align: left;
        color: #f9f1ff;
        font-size: 13px;
        font-family: "DM Sans";
        box-shadow: none;
        transition: box-shadow 0.3s;
        font-weight: 600;
        padding: 2px;
        &:focus {
            outline: none;
            -webkit-box-shadow: 1px 9px 15px -5px rgba(25, 25, 25, 1);
            -moz-box-shadow: 1px 9px 15px -5px rgba(25, 25, 25, 1);
            box-shadow: 1px 9px 15px -5px rgba(25, 25, 25, 1);
        }
        }
    .number_input {
        width: 50px;
        margin-left: 10px;
    }
    .icon {
        margin-left: 5px;
        cursor: pointer;
    }

    #find_by_publish_date p {
        margin-left: 15px;
        display: flex;
        flex-direction: column;
        justify-content: center;
    }

    #categories_container {
        display: flex;
        flex-wrap: wrap;
    }
    .category_name {
        color: #c4c4c4;
        border-radius: 20px;
        padding: 5px;
        margin: 5px;
        background: rgb(2,0,36);
        background: linear-gradient(90deg, rgba(2,0,36,1) 0%, rgba(199,70,70,1) 0%, rgba(201,45,75,1) 100%);
        border: solid 3px #751207;
        cursor: pointer;
    }
    .category_name:hover {
        filter: brightness(120%);
    }
    #input_and_button {
        display: flex;
    }
</style>