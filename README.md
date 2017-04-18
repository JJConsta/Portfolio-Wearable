# Portfolio-Wearable
/* 
Portfolio-Wearable 
Justice Stacey
Wearable Computing GDES-3015-001
OCAD University 
Created on 
April 11, 2017
Based on:
* Neopixel Library
* https://www.digikey.com/en/maker/blogs/connecting-the-photon-to-ifttt/50596c045e0144129d6da3e31feec3fe
*/

// This #include statement was automatically added by the Particle IDE.
#include "Particle.h"
#include "neopixel.h"

#define PIXEL_PIN  D7
#define PIXEL_COUNT 3
#define PIXEL_TYPE WS2812B

Adafruit_NeoPixel strip(PIXEL_COUNT, PIXEL_PIN, PIXEL_TYPE);

void setup()
{
pinMode(PIXEL_PIN, OUTPUT);
Particle.function("Twitter1", Twitter1); //function allows for audiance interaction
Particle.function("Twitter2", Twitter2); //function allows for commincation with world
strip.begin();
strip.show(); // Initialize all pixels to 'off'
}
 
void loop()
{

}
 
// this function automagically gets called upon a tweet mention
int Twitter1(String command) 
{
if (command == "suffering") {
 for(int i=0;i<PIXEL_COUNT;i++){
  strip.setPixelColor(i, strip.Color(150,150,150)); // Moderately bright green color.
  strip.show();
}
}

else {
 for(int i=0;i<PIXEL_COUNT;i++){
  strip.setPixelColor(i, strip.Color(0,150,150)); // Moderately bright green color.
  strip.show();
}
}
}

int Twitter2(String command) 
{
 for(int i=0;i<PIXEL_COUNT;i++){
  strip.setPixelColor(i, strip.Color(0,0,150)); //(39, 47, 58)
  strip.show();
}
}
