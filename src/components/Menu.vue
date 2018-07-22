<template>
    <div>
        <h1>Accessible Drop Down Menu</h1>
        <nav role="navigation">
            <ul class="access-menu">
                <li>
                    <a href="#"
                        v-on:mouseover="displayMenu('womens')"
                        v-on:mouseout="hideMenu('womens')"
                        v-bind:class="{ 'display-menu': displayControls.womens.isDisplay }">Womens</a>
                    <ul class="access-submenu"
                        v-on:mouseover="displayMenu('womens')"
                        v-on:mouseout="hideMenu('womens')"
                        v-bind:class="{ 'display-menu': displayControls.womens.isDisplay }">
                        <li><a href="#">Featured</a></li>
                        <li><a href="#">Shoes</a></li>
                        <li><a href="#">Clothing</a></li>
                        <li><a href="#">Accessories</a></li>
                        <li><a href="#">Sports</a></li>
                        <li><a href="#">Sale</a></li>
                    </ul>
                </li>
                <li>
                    <a href="#"
                        v-on:mouseover="displayMenu('mens')"
                        v-on:mouseout="hideMenu('mens')"
                        v-bind:class="{ 'display-menu': displayControls.mens.isDisplay }">Mens</a>
                    <ul class="access-submenu"
                        v-on:mouseover="displayMenu('mens')"
                        v-on:mouseout="hideMenu('mens')"
                        v-bind:class="{ 'display-menu': displayControls.mens.isDisplay }">
                        <li><a href="#">Featured</a></li>
                        <li><a href="#">Shoes</a></li>
                        <li><a href="#">Clothing</a></li>
                        <li><a href="#">Accessories</a></li>
                        <li><a href="#">Sports</a></li>
                        <li><a href="#">Sale</a></li>
                    </ul>
                </li>
                <li>
                    <a href="#"
                        v-on:mouseover="displayMenu('kids')"
                        v-on:mouseout="hideMenu('kids')"
                        v-bind:class="{ 'display-menu': displayControls.kids.isDisplay }">Kids</a>
                    <ul class="access-submenu"
                        v-on:mouseover="displayMenu('kids')"
                        v-on:mouseout="hideMenu('kids')"
                        v-bind:class="{ 'display-menu': displayControls.kids.isDisplay }">
                        <li><a href="#">Featured</a></li>
                        <li><a href="#">Boys</a></li>
                        <li><a href="#">Girls</a></li>
                        <li><a href="#">Infant</a></li>
                        <li><a href="#">Sale</a></li>
                    </ul>
                </li>
                <li>
                    <a href="#"
                        v-on:mouseover="displayMenu('sale')"
                        v-on:mouseout="hideMenu('sale')"
                        v-bind:class="{ 'display-menu': displayControls.sale.isDisplay }">Sale</a>
                    <ul class="access-submenu"
                        v-on:mouseover="displayMenu('sale')"
                        v-on:mouseout="hideMenu('sale')"
                        v-bind:class="{ 'display-menu': displayControls.sale.isDisplay }">
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
                womens: {
                    isDisplay: false,
                    sucMenus: {
                        
                    }
                },
                mens: {
                    isDisplay: false
                },
                kids: {
                    isDisplay: false
                },
                sale: {
                    isDisplay: false
                }
            }
        }
    },
    methods: {
        displayMenu(sectionName) {
            let section = '';
            for (section in this.displayControls) {
                if (section === sectionName) {
                    this.displayControls[section].isDisplay = true;
                } else {
                    this.displayControls[section].isDisplay = false;
                }
            }
        },
        hideMenu (sectionName) {
            this.displayControls[sectionName].isDisplay = false;
        }
    },
    mounted() {
        this.displayControls = {
                womens: {
                    isDisplay: false,
                    sucMenus: {
                        
                    }
                },
                mens: {
                    isDisplay: false
                },
                kids: {
                    isDisplay: false
                },
                sale: {
                    isDisplay: false
                }
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

        .access-menu a.display-menu {
            background-color: cadetblue;
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

