# practice-Vue-projects

## Shopping cart

This repository consists of  Vue JS projects I learnt through online tutorials.

Shopping cart Project Credits and course which taught me Vue JS:
[Vue JS beginner course from Gwen Faraday and Freecodecamp](https://www.youtube.com/watch?v=FXpIoQ_rT_c)

product-and-cart is a non Vue-CLI version of the project which is supposed to be run on live server. App.html is the main HTML file to be run on live server.

product-and-cart-cli-version is a Vue-CLI and Vue Router version of the project. To run it navigate to the project directory in windows powershell and run the following commands

npm install vue 

npm install -g @vue/cli

npm install serve

## Qwitter 

Qwitter Project Credits and course which taught me Quasar:
[A basic Twitter Clone with Vue.js and Quasar](https://www.youtube.com/watch?v=la-0ulfn0_M)

To run the project do the following steps:

Download the qwitter project and after navigating to the project folder

Download and refer Quasar CLI from [Quasar documentation](https://quasar.dev/start/quasar-cli)

npm install

npm i -g @quasar/cli

npx quasar dev



To deploy the project in electron, run the following commands

First in package, in quasar conf file, make sure the packager has "win32" platform.

npx quasar dev -m electron

