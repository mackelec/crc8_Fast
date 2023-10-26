# Fast CRC8x 

This repository contains a fast implementation for CRC8-based corruption checks, primarily suited for EEPROM and basic serial communications.

## Description

The provided code offers a rapid method to compute the CRC8 checksum of a byte array. Using optimized lookup tables, this method is especially useful for checking data integrity in storage mediums like EEPROM or during data transfers in serial communications.

## Table of Contents

1. [Usage](#usage)
2. [Dependencies](#dependencies)
3. [Contribute](#contribute)
4. [License](#license)

## Usage

Below is the code for the Fast CRC8x EEPROM Checker:

```
static uint8_t const crc8x_table[] = {
    // ... (the array content)
};

uint8_t crc8x_fast( uint8_t mem[], int len) {
    uint8_t crc;
    uint8_t p;
    crc = 55;
    for (int i=0; i<len; i++) {
        p = crc ^ mem[i];
        crc = crc8x_table[p];
    }
    return crc;
}
```

To quickly compute the CRC8 checksum for a byte array, use the `crc8x_fast` function. Here's a basic example:

```
int main() {
    uint8_t data[] = {0x12, 0x34, 0x56, 0x78};
    int len = sizeof(data) / sizeof(data[0]);

    uint8_t checksum = crc8x_fast(data, len);
    printf("Checksum: %02X\n", checksum);

    return 0;
}
```

