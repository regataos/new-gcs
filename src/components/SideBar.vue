<template>
    <div id="side-bar">
        <div class="icon-regataos" style="background-image:url(src/assets/logo-gcs.png);"></div>

        <div id="block-home">
            <div class="block-title">Launchers disponíveis</div>
        </div>

        <div class="progress-bar">
            <iframe src="progress-bar/progress-bar.html" frameborder="0" class="iframe_pb" id="iframepb"></iframe>
        </div>
    </div>
</template>

<style>
#side-bar {
    top: 0px;
    left: 0px;
    width: 245px;
    height: 100%;
    position: fixed;
    background-color: rgba(4, 4, 4, 0.68);
    -webkit-backdrop-filter: blur(10px);
    backdrop-filter: blur(10px);
    box-shadow: 0px 0px 6px 0px rgba(8, 13, 18, 0.5);
    z-index: 20000;
}

.icon-regataos {
    height: 50px;
    width: 50px;
    background-position: 50% 50%;
    background-size: 100% 100%;
    background-repeat: no-repeat;
    margin-top: 20px;
    margin-left: 20px;
}

#block-home {
	display: block;
    width: 230px;
    margin-left: auto;
    margin-right: auto;
    margin-top: 30px;
	opacity: 1;
	animation-name: example;
	animation-duration: .5s;
}

.block-title {
    color: #fff;
    text-align: left;
	font-size: 14px;
    margin-bottom: 20px;
}
</style>
