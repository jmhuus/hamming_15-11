## Hamming 15-11 ECC

This module is my own implementation of Hamming's 15-11 error correction
Code. This code only works for data that can fit into 16 bits and 16 
bits only. It can locate up to maximum of a 1-bit error and correct it.

Most Hamming ECC implementations seem to grow or shrink
depending on the data size by calculating the required number of parity
bits. This script doesn't attempt to provide such a feature in an effort
to keep this simple and robust for another project, 
github.com/jmhuus/OpticNerve.


### Example:
```
# Serialize to binary - include parity bits for error detection
binary_data = encode_data_to_hamming_binary_array("hello world")

# Purposefully cause a bit error
packet_with_error = list(binary_data[0])
packet_with_error[5] = '1' if packet_with_error[5]=='0' else '0'
binary_data[0] = ''.join(packet_with_error)

# Detect errors and decode the data
import pprint; pprint.pprint(binary_data)
print(decode_hamming_binary(binary_data))


>> ['1101010111010001',
>>  '1100000011001010',
>>  '1001000011011000',
>>  '1001000011011000',
>>  '0101000011011110',
>>  '1001000001000001',
>>  '1000000111101110',
>>  '0101000011011110',
>>  '0001000111100100',
>>  '1001000011011000',
>>  '0001000111001001']
>> Bit error found and corrected at position 6, packet 1. Fixed.
>> hello world
```

### Todo:
    * Implement feature for detecting 2-bit error - without correction.
