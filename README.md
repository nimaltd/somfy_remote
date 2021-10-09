## SOMFY library for STM32
* http://www.github.com/NimaLTD   
* https://www.instagram.com/github.nimaltd/   
* https://www.youtube.com/channel/UCUhY7qY1klJm1d2kulr9ckw   

* Choose a pin and enable external interrupt on both edge.
* Set enable a timer with 100us tick and maximum value "65535". example: 4800-1 for 48 MHz timer clock 
* Add callback function in pinchange interrupt routine.
* Create your struct. 
* Call somfy_init().

Example:

```
#include "somfy.h"
somfy_t rf;

uint8_t ctrl = 0;
uint16_t rolling;
uint8_t key;
uint8_t address[3];

void main()
{

  somfy_init(&rf, &htim1, GPIOC, GPIO_PIN_7);
  if (somfy_available(&rf))
  {
    ctrl = somfy_read(&rf, &rolling, address, &key);
    somfy_reset_available(&rf);
  }  
}
```
