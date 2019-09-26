# Email Signature Maker

Email signature generator written with Vue and compiled with Parcel. Provides options for different variations approved by University Marketing.

Requires Node.

## Setup Usage

`npm install`  
for initial setup

`npm run dev`  
Tell parcel to build files and set up a testing server.

`npm run build`  
Parcel will bundle all dependancies into /dist

## Usage in OUCampus
* The compiled files will appear in /dist.
* Use main.css in the headcode of the OU page.
* Place main.js in the footcode with defer="defer" attribute on the script tag.
* In the page's main content, place an empty div with the ID of "app". This app will all take place inside this div.