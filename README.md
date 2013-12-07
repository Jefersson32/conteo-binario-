#include <avr/io.h>

#include <avr/interrupt.h>

int main(void)
{
	PORTC.DIR = 0xFF;
	
	PORTD.PIN1CTRL = PORT_ISC_FALLING_gc|PORT_OPC_PULLUP_gc;
	PORTD.PIN2CTRL = PORT_ISC_FALLING_gc|PORT_OPC_PULLDOWN_gc;
	PORTD.INT0MASK = 1;
	PORTD.INT1MASK = 2;
	
	PORTD.INTCTRL = PORT_INT0LVL_LO_gc;
	PORTD.INTCTRL = PORT_INT1LVL_MED_gc;
	
	PMIC.CTRL = PMIC_LOLVLEN_bm;
	
	sei();
	
    while(1)
    {
        //TODO:: Please write your application code 
    }
}

ISR(PORTC_INT0_vect)

{

	PORTC.OUT += 1;
	
}

ISR(PORTC_INT1_vect)

{

	PORTC.OUT -= 1;
	
}
