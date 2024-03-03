#include <HX711_ADC.h>
HX711_ADC HX711(3,2);
float K=-1;
float B=120;
unsigned long myTime;
 
void setup()
{
  Serial.begin(115200);
  HX711.begin();
  HX711.start(1000);
  HX711.setCalFactor(8.58447);
}
float weight;
float zvsh;
void loop()
{
  myTime=millis();
  HX711.update();
  weight=HX711.getData();
  zvsh=weight*K+B;
  Serial.print(zvsh);
  Serial.print(" ");
  Serial.println(myTime);
}
