# Programmable gain amplifier (MCP6S2X)

this class implements the interfaces the functions for the programmable gain amplifier and executes the SPI configuration and communication. The class is defined in MCP6S2X.h.
The following code exhibits the SPI setup to establish SPI communication with MCP6S2X device.

```C
inline static void MCP6S2X_init_spi(void)
{
	while (!GET_POXI_SPI_TRANSMISSION_DONE);
	SET_POXI_SPI_SLAVE_SELECT(POXI_SPI_PGA_CS);
	SET_POXI_SPI_DATA_LENGTH(POXI_SPI_DATA_LENGTH_16_BITS);
	SET_POXI_SPI_BAUD_RATE_DIVIDER(MCP6S2X_SPI_BAUD_RATE);
	SET_POXI_SPI_CLOCK_POLARITY(1);
	SET_POXI_SPI_CLOCK_PHASE(1);
}
```

In the previous code it can be seen the SPI configuration, CPOL = 1, CPHA = 1, 16 bits.

The instance of this class does not need to be initialized.
In the next line is shown the code to set the gain in the PGA.

```C
Poxi_PGA->set_gain(value);
```

The next table enlists the defined values accessible for the device (the only parameter of the set_gain function).

```C
typedef enum
{
	GAIN_1 = 0,
	GAIN_2 = 1,
	GAIN_4 = 2,
	GAIN_5 = 3,
	GAIN_8 = 4,
	GAIN_10 = 5,
	GAIN_16 = 6,
	GAIN_32 = 7
} MCP6S2X_GAIN;
```

The next function shuts down the PGA device.

```C
Poxi_PGA->shutdown();
```

For detailed information it can be referred the actual code.


Best regards,

-Yarib Nevárez
