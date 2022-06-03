# SIT210

// This #include statement was automatically added by the Particle IDE.
#include "lib1.h"

int motion = D6;
int sensorRead = 0; 

void setup() {
    
    //pinMode(detectPin, INPUT);
    Particle.variable("sensorRead", &sensorRead, INT);
    
}

void loop(){
    sensorRead = digitalRead(motion);
    if (sensorRead >= 1)
    {
        
        Particle.publish("motion", "soil is moist");
        Particle.publish("motion", String(motion), PRIVATE);
        delay(1000);
    }
    
    else  {
            
        Particle.publish("motion", "watering is required.");        
        Particle.publish("motion", String(motion), PRIVATE);
        delay(1000);
            
    }
}
