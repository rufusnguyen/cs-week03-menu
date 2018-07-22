<template>
    <div>
        <h1>Accessible Drop Down Menu</h1>
        <nav role="navigation">
            <ul class="access-menu">
                <li>
                    <a href="#" v-on:mouseover="displayMenu('womens')" v-on:mouseout="hideMenu('womens')">Womens</a>
                    <ul class="access-submenu"
                        v-bind:class="{ 'display-menu': displayControls.womens }">
                        <li><a href="#">Featured</a></li>
                        <li><a href="#">Shoes</a></li>
                        <li><a href="#">Clothing</a></li>
                        <li><a href="#">Accessories</a></li>
                        <li><a href="#">Sports</a></li>
                        <li><a href="#">Sale</a></li>
                    </ul>
                </li>
                <li>
                    <a href="#" v-on:mouseover="displayMenu('mens')" v-on:mouseout="hideMenu('mens')">Mens</a>
                    <ul class="access-submenu"
                        v-bind:class="{ 'display-menu': displayControls.mens }">
                        <li><a href="#">Featured</a></li>
                        <li><a href="#">Shoes</a></li>
                        <li><a href="#">Clothing</a></li>
                        <li><a href="#">Accessories</a></li>
                        <li><a href="#">Sports</a></li>
                        <li><a href="#">Sale</a></li>
                    </ul>
                </li>
                <li>
                    <a href="#" v-on:mouseover="displayMenu('kids')" v-on:mouseout="hideMenu('kids')">Kids</a>
                    <ul class="access-submenu"
                        v-bind:class="{ 'display-menu': displayControls.kids }">
                        <li><a href="#">Featured</a></li>
                        <li><a href="#">Boys</a></li>
                        <li><a href="#">Girls</a></li>
                        <li><a href="#">Infant</a></li>
                        <li><a href="#">Sale</a></li>
                    </ul>
                </li>
                <li>
                    <a href="#" v-on:mouseover="displayMenu('sale')" v-on:mouseout="hideMenu('sale')">Sale</a>
                    <ul class="access-submenu"
                        v-bind:class="{ 'display-menu': displayControls.sale }">
                        <li><a href="#">Men's Sale</a></li>
                        <li><a href="#">Women's Sale</a></li>
                        <li><a href="#">Plus Sale</a></li>
                        <li><a href="#">Kids' Sale</a></li>
                    </ul>
                </li>
            </ul>
        </nav>
    </div>
</template>
<script>
    export default {
    name: 'Menu',
    data () {
        return {
            displayControls: {
                womens: false,
                mens: false,
                kids: false,
                sale: false
            }
        }
    },
    methods: {
        displayMenu(sectionName) {
            let section = '';
            this.displayControls[sectionName] = true;
            for (section in this.displayControls) {
                if (section === sectionName) {
                    this.displayControls[section] = true;
                } else {
                    this.displayControls[section] = false;
                }
            }
        },
        hideMenu (sectionName) {
            this.displayControls[sectionName] = false;
        }
    },
    mounted() {
        this.displayControls = {
                womens: false,
                mens: false,
                kids: false,
                sale: false
            };
    }
}
</script>
<style>
    * {
            -webkit-box-sizing: border-box;
            -moz-box-sizing: border-box;
            box-sizing: border-box;
        }

        body {
            font-family: 'calibri', sans-serif;
        }

        h1 {
            margin: 2em 0 0;
            text-align: center;
            text-transform: uppercase;
        }

        p {
            text-align: center;
            margin: 0;
        }

        nav ul {
            list-style: none;
            margin: 0;
            padding: 0;
        }

        .access-menu {
            display: table;
            margin: 1em auto;
        }

        .access-menu>li {
            background: #333;
            display: inline-block;
            position: relative;
        }

        .access-menu>li+li {
            border-left: solid 1px #000;
        }

        .access-menu a {
            color: #eee;
            display: block;
            padding: .5em 2em;
            text-decoration: none;
            -webkit-transition: all .2s linear;
            -moz-transition: all .2s linear;
            -ms-transition: all .2s linear;
            -o-transition: all .2s linear;
            transition: all .2s linear;
        }

        .access-submenu {
            background: #444;
            top: 100%;
            left: auto;
            position: absolute;
            width: 150%;
            display: none;
        }

        .access-submenu.display-menu {
            display: block!important;
        }

        .access-submenu>li+li {
            border-top: solid 1px #000;
        }

        .access-submenu>li :last-child {
            border-bottom: solid 3px #000;
        }

        .access-submenu a {
            padding: .5em 1em;
        }

        .is-show {
            left: auto;
            top: 100%;
        }
</style>

