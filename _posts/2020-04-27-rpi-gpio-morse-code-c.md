---
title:  "Simple Raspberry Pi Morse Code LED - C  "
date:   2020-03-19 00:00:00
description: "I made a simple morse code blinking LED program using C programming."
categories: [electronics]
tags: [raspberry pi, c programming]
---

I've decided to expand my C programming knowledge with devices larger than a 16 bit MSP430, the micro-processor of choice in my prior projects.

## Morse Code LED Program

After running through some basic C programming 101 tutorials to refresh my 2 year hiatus I dove into the [BCM2835 GPIO Library](http://www.airspayce.com/mikem/bcm2835/) and created a quick text to morse code LED blink program. [This program](https://github.com/kb1lqd/rpi_c_learning/blob/master/GPIO/morse_blink_file.c) toggles a Raspberry Pi GPIO output with properly spaced morse code at a variable speed. Although it is a visual output, this simple program could be updated to output a tone either externally or I imagine via audio output.

[![Rapsberry Pi 3 GPIO Morse Code Blinking Video](https://img.youtube.com/vi/OCHYAyD_-Wk/0.jpg)](https://www.youtube.com/watch?v=OCHYAyD_-Wk "Rapsberry Pi 3 GPIO Morse Code Blinking Video")

## Key Code Components

Morse code dit, dah, and space timing is the key to correct transmission. Using [Morse Code World](https://morsecode.world/international/timing.html) as a reference for for the character, character spacing, and word spacing it is straight forward to implement a single "dit" timing based on a desired words-per-minute (WPM) speed.

First, defining the time relationship between the smallest interval (a 'dit') and other time parameters.

``` c 

#define MORSE_DIT_UNIT 1
#define MORSE_DAH_UNIT 3
#define MORSE_INTRACHAR_UNIT 1
#define MORSE_INTERCHAR_UNIT 3
#define MORSE_INTERWORD_UNIT 7

```

Convieniently, the word "PARIS" is exactly 50 "dit" lengths long when considering dits, dahs, and character/word spacings. Multiplying 50 by the WPM value then deviding this number into 60 seconds returns the duration of a single dit in milliseconds. 

```c
	float calc_tdit_ms(float user_wpm)
	{
		//This function returns the time in ms of a dit.
		float temp;
		temp = 60/(50*user_wpm);
		return temp;
	}
	
``` 

The next challenge was encoding each morse code dit/dah pattern into memory and incorporating a method to translate this into properly lengthed ON/OFF periods for the GPIO pin. I did this by using a visual period and dash representation that is common to text interpretations of morse code and then running this string through a function that decoded the effective ON/OFF and space timing.

``` c
char* morse_char(char input_char)
{
	//This function inputs a single character and transmits its morse code value
	switch(input_char)
	{
		case 'a':
			return ".-";
		case 'b':
			return "-...";
		case 'c':
			return "-.-.";
	
```

`blink_led()` decodes the character string and directlyl toggles the GPIO pin.

``` c
void blink_led(char* morse_char_str, int morse_char_len ,int dit_time_ms)
{
	
	//printf("Character: %s\n", morse_char_str);
	
	//Check if character is space between word or a valid character
	if(morse_char_str[0]==' ')
	{
		printf("-SPACE-\n");
		bcm2835_delay(dit_time_ms*MORSE_INTERWORD_UNIT);
	}
	else
	{
		int i;
		for(i=0;i<morse_char_len;i++)
		{
			switch(morse_char_str[i])
			{
				case '.':
					bcm2835_gpio_write(PIN, HIGH);
					bcm2835_delay(dit_time_ms*MORSE_DIT_UNIT);
					bcm2835_gpio_write(PIN, LOW);
					bcm2835_delay(dit_time_ms*MORSE_INTRACHAR_UNIT);
					break;
				case '-':
					bcm2835_gpio_write(PIN, HIGH);
					bcm2835_delay(dit_time_ms*MORSE_DAH_UNIT);
					bcm2835_gpio_write(PIN, LOW);
					bcm2835_delay(dit_time_ms*MORSE_INTRACHAR_UNIT);
					break;
				default:
					printf("UNKNOWN CHARACTER!");
			}
		}
		//Delay the standard time between each character in a word
		bcm2835_delay(dit_time_ms*MORSE_INTERCHAR_UNIT);
	}
}
```

This was a pretty simple project that was a fun introduction to using my raspberry pi 3's GPIO pins via C programming. I'm leaving the project here in its current state, maybe I'll pick it up in the future and add audio output via the headphone jack at a later date.
 



