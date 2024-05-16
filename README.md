## Overview
This GitHub repository contains a standard implementation of the Advanced Encryption Standard (AES) with a focus on AES-256 CBC (Cipher Block Chaining) encryption. AES-256 is a highly secure encryption standard due to its 256-bit key size, providing robust protection for sensitive data. CBC mode ensures increased security by chaining each plaintext block to the previous ciphertext block before encryption, making it resistant to certain cryptographic attacks.

## Features
- **Header-only:** No need for external dependencies, simplifying integration into existing projects.
- **AES-256-CBC support:** Enables robust encryption and decryption using the Advanced Encryption Standard with a 256-bit key size and Cipher Block Chaining mode.
- **Seamless integration:** Provides straightforward usage examples for effortless incorporation into applications.
- **Compatibility:** Data encrypted using this standard AES-256 CBC algorithm can be decrypted using any compliant AES-256 CBC decryption implementation.
- 
## Usage Example
```c
#include <stdio.h>
#include <stdint.h>
#include <string.h>
#include "AES_256_CBC.h"

// Function to print data in hexadecimal format
void output(const char* title, uint8_t *data, uint32_t size) {
    printf("%s", title);
    for (uint8_t index = 0; index < size; index++) {
        printf("%02x", data[index]);
    }
    printf("\n");
}

int main() {
    // Key, IV, and data initialization
    uint8_t key[32];
    uint8_t iv[16];
    uint8_t data[16];
    memset(key, 0x79, 32);
    memset(iv, 0x79, 16);
    memset(data, 0x79, 16);

    // Output original data blocks
    output("original: 0x", data, 16);
    
    // AES context initialization
    AES_CTX ctx;
    AES_EncryptInit(&ctx, key, iv);

    // Encrypt data blocks
    AES_Encrypt(&ctx, data, data);
    
    // Output encrypted data blocks
    output("encrypted: 0x", data, 16);

    // AES context initialization for decryption
    AES_DecryptInit(&ctx, key, iv);

    // Decrypt data blocks
    AES_Decrypt(&ctx, data, data);
    
    // Output decrypted data blocks
    output("decrypted: 0x", data, 16);

    // Free AES context
    AES_CTX_Free(&ctx);

    return 0;
}
```

## Integration Steps
1. Copy `AES_256_CBC.h` into your project directory.
2. Include the header in your source code:
   ```c
   #include "AES_256_CBC.h"
   ```
3. Utilize the provided functions as demonstrated in the example.

## Functions and Context

### `AES_CTX` Structure
- Represents the context for AES encryption and decryption.

### `void AES_EncryptInit(AES_CTX *ctx, const unsigned char *key, const unsigned char *iv)`
- Initializes the AES encryption context.

### `void AES_DecryptInit(AES_CTX *ctx, const unsigned char *key, const unsigned char *iv)`
- Initializes the AES decryption context.

### `void AES_Encrypt(AES_CTX *ctx, const unsigned char in_data[AES_BLOCK_SIZE], unsigned char out_data[AES_BLOCK_SIZE])`
- Encrypts a single block of data.

### `void AES_Decrypt(AES_CTX *ctx, const unsigned char in_data[AES_BLOCK_SIZE], unsigned char out_data[AES_BLOCK_SIZE])`
- Decrypts a single block of data.

### `void AES_CTX_Free(AES_CTX *ctx)`
- Frees resources associated with the AES context.

## Notes
- Ensure key and IV sizes match the algorithm requirements.
- This implementation does not support padding; input data must be in blocks of 16 bytes.

## Single Block Encryption/Decryption
For a single block of data, use the `AES_Encrypt` and `AES_Decrypt` functions.

## Multiple Blocks Encryption/Decryption
For multiple blocks, use a loop. Example:
```c
for (unsigned int offset = 0; offset < data_length_multi_block; offset += 16) {
    AES_Encrypt(&ctx, data + offset, data + offset);
}
```

## License
This AES-256-CBC implementation is released under the MIT License.
