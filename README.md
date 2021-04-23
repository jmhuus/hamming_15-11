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

>```binary_data = encode_data_to_hamming_binary_array("hello world")
>   import pprint; pprint.pprint(binary_data)
>   print(decode_hamming_binary(binary_data))
>```

### Todo:
* Implement feature for detecting 2-bit error - without correction.
