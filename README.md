#include <stdio.h>
#include "pico/stdlib.h"

Valentin Franco 4º1º Avionica 
Albornoz Thiago Erbino Sebastian

int main() {
  stdio_init_all();
  
  // 0000 0000 0000 0000 0000 0011 1000 0000 
  
  uint8_t contador = 0;

  gpio_init_mask(0x3ff);
  gpio_set_dir_in_masked(0x380);
  gpio_set_dir_out_masked(0x7f);

  uint8_t digitos []={
    0x7e,
    0x30,
    0x6d,
    0x79,
    0x33,
    0x5b,
    0x5f,
    0x70,
    0x7f,
    0x73,
  };  
  
  while (true) {
 
    if(gpio_get(7)) { contador++; }
    else if(gpio_get(8)) { contador--; }
    else if(gpio_get(9)) { contador = 0; }

    gpio_put_masked(0x7f, digitos[contador]);
    sleep_ms(1000);
  }
}
