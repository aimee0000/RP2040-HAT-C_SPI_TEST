# RP2040-HAT-C_SPI_TEST
test for using pio for spi interface with w5500 chip.

### Test Case 1
```
.program wiznet_spi_write_read
.side_set 1

public write_bits:
    out pins, 1             side 0
    jmp x-- write_bits      side 1
    set pins 0              side 0
public write_end:
read_byte_delay:
    set pindirs 0           side 0 [1] 
read_byte:
    set x 6                 side 1
read_bits:
    in pins, 1              side 0
    jmp x-- read_bits       side 1
    in pins, 1              side 0
    jmp y-- read_byte_delay side 0
public read_end:
```
#### Run Loopback code (clock 16.6MHz)
![image](https://github.com/aimee0000/RP2040-HAT-C_SPI_TEST/assets/150221423/118d6083-e5bc-4544-afd3-4a4fc5844256)


### Test Case 2
```
.program wiznet_spi_write_read
.side_set 1

public write_bits:
    out pins, 1             side 0
    jmp x-- write_bits      side 1
    set pins 0              side 0
public write_end:
read_byte_delay:
    set pindirs 0           side 0 
read_byte:
    set x 6                 side 1
read_bits:
    in pins, 1              side 0
    jmp x-- read_bits       side 1
    in pins, 1              side 0
    jmp y-- read_byte_delay side 0
public read_end:
```
#### Run Loopback code (clock 16.6MHz)
![image](https://github.com/aimee0000/RP2040-HAT-C_SPI_TEST/assets/150221423/1fe8e323-7678-4795-aa7c-07a39f9750e8)


### Test Case 3
```
.program wiznet_spi_write_read
.side_set 1

public write_bits:
    out pins, 1             side 0
    jmp x-- write_bits      side 1
    set pins 0              side 0
public write_end:
read_byte_delay:
    set pindirs 0           side 0
read_byte:
    set x 6                 side 1
read_bits:
    in pins, 1              side 0
    jmp x-- read_bits       side 1
    in pins, 1              side 0
    jmp y-- read_byte       side 0
public read_end:
```
#### Run Loopback code (clock 16.6MHz)

