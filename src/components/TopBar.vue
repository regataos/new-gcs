<template>
    <div class="top-bar">
        <div class='top-bar-arrow' onclick='voltar(); back_button_pages();' title='Voltar'>
            <span class='svg svg-arrow-left'>
                <svg enable-background='new 0 0 14 26' height='16px' id='svg4-Layer_1' version='1.1' viewBox='0 0 14 26' width='14px' x='0px' xml:space='preserve' xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink' y='0px'>
                    <path d='M13,26c-0.256,0-0.512-0.098-0.707-0.293l-12-12c-0.391-0.391-0.391-1.023,0-1.414l12-12c0.391-0.391,1.023-0.391,1.414,0s0.391,1.023,0,1.414L2.414,13l11.293,11.293c0.391,0.391,0.391,1.023,0,1.414C13.512,25.902,13.256,26,13,26z'/>
                </svg>
            <span class='alt sr-only'></span>
            </span>
        </div>

        <ul id='top-menu'>
            <li class="p-home-li">
                <a class='p-home' onclick="go_home();">Game Access</a>
            </li><li class="p-installed-li">
                <a class='p-installed' onclick="go_installed();">Instalados</a>
            </li><li class="p-allgames-li">
                <a class='p-allgames' onclick="go_allgames();">Todos os jogos</a>
            </li><li class="p-steam-li">
                <a class='p-steam' onclick="go_steam();">Jogos do Steam</a>
            </li><li class="p-settings-li">
                <a class='p-settings' onclick="go_settings();">Configurações</a>
            </li>
        </ul>

        <div id='search'>
            <form id="form">
                <div><input id='field' name='q' onblur='if (this.value == "") {this.value = "Pesquisar jogos";}' onfocus='if (this.value == "Pesquisar jogos") {this.value = "";}' type='text' value='Pesquisar jogos'/>
                <input class='submit' name='submit' type='submit' value='Pesquisar jogos'/></div>
            </form>
        </div>
    </div>
</template>

<style>
/* Top Bar */
.top-bar {
    float: left;
    left: 0px;
    width: 100%;
    height: 50px;
    margin-left: 245px;
    border-bottom: 0px solid #1f1f1f;
    position: fixed;
    top: 0px;
    user-select: none;
    z-index: 30000;
    box-shadow: 0px 1px 2px rgba(0, 0, 0, 0.2);
    background-color: rgba(4, 4, 4, 0.68);
    -webkit-backdrop-filter: blur(10px);
    backdrop-filter: blur(10px);
}

/* Top Bar - Back Arrow */
.top-bar-arrow {
	display: none;
	float: left;
	color: #fff;
	cursor: pointer;
	margin-top: 12px;
	margin-left: 15px;
	padding-left: 10px;
	padding-right: 10px;
	opacity: 1;
	animation-name: example;
	animation-duration: .3s;
}

.svg {
	fill: #ffffff;
}

/* Top Bar - Menu */
ul#top-menu li {
	display: none;
	padding-top: 0px;
	padding-bottom: 11px;
	margin-right: 40px;
	margin-top: 0px;
    float: left;
	transition: all .3s;
}

li.p-home-li {
	display: inline-block !important;
}

li.p-settings-li {
	display: inline-block !important;
}

li.p-allgames-li {
	display: inline-block !important;
}

ul#top-menu li a {
	text-transform: uppercase;
	font-size: 15px;
	font-family: 'Roboto', sans-serif;
	color: #fff;
	letter-spacing: 0.05em;
	cursor: pointer;
}

a.p-home {
    font-weight: 700;
}

/* Top Bar - Search */
#search {
    display: block;
    position: absolute;
    top: 9px;
    right: 0;
    margin-right: 265px;
}

#search input#field {
    font-family: 'Roboto', sans-serif;
    font-weight: 400;
    background-position:top right; 
    background-repeat:no-repeat; 
    width: 200px; 
    padding:7px;
    outline: none; 
    font-size: 15px;
    border-radius: 2em;
    border: 2px;
    border-color: rgba(49, 49, 49, 0.3);
    z-index: 1; 
    height:16px; 
    float:left; 
    padding-right:30px;
}

#search input#field:focus {
    background-position:top right; 
    background-repeat:no-repeat;
}

#search input.submit {
    width:auto; 
    height:31px;
    font-weight:normal;
    text-transform: uppercase; 
    float:left; 
    border:none; 
    font-family: 'Roboto', sans-serif;
    font-size: 18px;
    font-weight: 600;
    cursor:pointer; margin:0 0 0 1px;
}

#search input#field {
    background-image:url(https://3.bp.blogspot.com/-1AxrECLYixw/Xggi1BABTtI/AAAAAAAAYB4/jnORAw0WsioSvGbQiroMLunR8k0o3D-tACLcBGAsYHQ/s1600/lupa.png); 
    background-color: rgba(128, 128, 128, 0.3);
    color: #c9c9c9;
    border: 1px solid rgba(49, 49, 49, 0.3);
    transition: border-color .3s,background-color .3s,color .3s,box-shadow .3s;
    padding-left: 10px;
}

#search input#field:focus {
    background-image:url(https://3.bp.blogspot.com/-1AxrECLYixw/Xggi1BABTtI/AAAAAAAAYB4/jnORAw0WsioSvGbQiroMLunR8k0o3D-tACLcBGAsYHQ/s1600/lupa.png); 
    background-color: rgba(228, 228, 228, 0.3);
    color: #fff;
}

#search input.submit {
    display: none;
    background-color:#1a1a1a;
    color:#ccc;
    border: 0px solid #1a1a1a;
    transition: background-color .3s;
}

#search input.submit:hover {
    background-color: #417A9B;
    border: 0px solid #0d547a;
    color: #fff;
}
</style>
