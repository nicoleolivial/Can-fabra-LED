# Códigos de Nicole

Aquí se sube lo que ha hecho Nicole

Enlace a Luis Llamas

https://www.luisllamas.es/arduino-teclado-matricial/

Lo que llevo de código 4/2/25:


#include <Keypad.h>
 
const byte rowsCount = 4;
const byte columsCount = 4;
 
char keys[rowsCount][columsCount] = {
   { '1','2','3', 'A' },
   { '4','5','6', 'B' },
   { '7','8','9', 'C' },
   { '#','0','*', 'D' }
};
 
const byte rowPins[rowsCount] = { 11, 10, 9, 8 };
const byte columnPins[columsCount] = { 7, 6, 5, 4 };

#11/2/25

Este es el código:
#include <Keypad.h>

const byte rowsCount = 4; const byte columsCount = 4;
char keys[rowsCount][columsCount] = { { '1','2','3', 'A' }, { '4','5','6', 'B' }, { '7','8','9', 'C' }, { '#','0','*', 'D' } };
const byte rowPins[rowsCount] = { 11, 10, 9, 8 }; const byte columnPins[columsCount] = { 7, 6, 5, 4 };

String password = "16A5";
int caracteresAcertados = 0;
Keypad keypad = Keypad(makeKeymap(keys), rowPins, columnPins, rowsCount, columsCount);

void corrector(char tecla){
 Serial.println(tecla);
 if (tecla == password[caracteresAcertados]){
    caracteresAcertados++;
    Serial.println("caracter correcto"+ caracteresAcertados);
  }
  else{
    caracteresAcertados = 0;
    Serial.println("caracter incorrecto"+ caracteresAcertados);
  }
  if(caracteresAcertados > 3){
    Serial.println("Contraseña correcta");
    caracteresAcertados = 0;
  }
}
 
Keypad keypad = Keypad(makeKeymap(keys), rowPins, columnPins, rowsCount, columsCount);
 
void setup() {

11/2/25
Hoy se consiguió el objetivo del proyecto de crear una contraseña
Este es el código:
#include <Keypad.h>

const byte rowsCount = 4; const byte columsCount = 4;
char keys[rowsCount][columsCount] = { { '1','2','3', 'A' }, { '4','5','6', 'B' }, { '7','8','9', 'C' }, { '#','0','*', 'D' } };
const byte rowPins[rowsCount] = { 11, 10, 9, 8 }; const byte columnPins[columsCount] = { 7, 6, 5, 4 };

String password = "16A5";
int caracteresAcertados = 0;
Keypad keypad = Keypad(makeKeymap(keys), rowPins, columnPins, rowsCount, columsCount);

void corrector(char tecla){
 Serial.println(tecla);
 if (tecla == password[caracteresAcertados]){
    caracteresAcertados++;
    Serial.println("caracter correcto"+ caracteresAcertados);
  }
  else{
    caracteresAcertados = 0;
    Serial.println("caracter incorrecto"+ caracteresAcertados);
  }
  if(caracteresAcertados > 3){
    Serial.println("Contraseña correcta");
    caracteresAcertados = 0;
  }
}
   Serial.begin(9600);
}
 
void loop() {
   char key = keypad.getKey();
 
   if (key) {
      Serial.println(key);
   }

}
LEDS 18/2/25
#define NUM_LEDS 120
#define DATA_PIN 3
CRGB leds[NUM_LEDS];
void setup() { 
    FastLED.addLeds<NEOPIXEL, DATA_PIN>(leds, NUM_LEDS); 
}
void loop() { 
  for ( int indiceLed = 0; indiceLed < NUM_LEDS; indiceLed ++){
    leds[indiceLed] = CRGB::Red;
    FastLED.show();
    delay (250);

  }  
for ( int indiceLed = 0; indiceLed < NUM_LEDS; indiceLed ++){
    leds[indiceLed] = CRGB::Black;


  }    
    FastLED.show();
    delay (1250);
}
