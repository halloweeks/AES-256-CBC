## Overview
This GitHub repository contains a standard implementation of the Advanced Encryption Standard (AES) with a focus on AES-256 CBC (Cipher Block Chaining) encryption. AES-256 is a highly secure encryption standard due to its 256-bit key size, providing robust protection for sensitive data. CBC mode ensures increased security by chaining each plaintext block to the previous ciphertext block before encryption, making it resistant to certain cryptographic attacks.

## Features
- **Header-only:** No need for external dependencies, simplifying integration into existing projects.
- **AES-256-CBC support:** Enables robust encryption and decryption using the Advanced Encryption Standard with a 256-bit key size and Cipher Block Chaining mode.
- **Seamless integration:** Provides straightforward usage examples for effortless incorporation into applications.
- **Compatibility:** Data encrypted using this standard AES-256 CBC algorithm can be decrypted using any compliant AES-256 CBC decryption implementation.

## Usage

To utilize this standard AES-256 CBC implementation, follow the instructions provided below:

### Including "AES_256_CBC.h" Header

Before utilizing the AES encryption and decryption functions, ensure that you've included the "AES_256_CBC.h" header in your code. This header provides access to the AES functionality.

```c
#include "AES_256_CBC.h"
```


### AES Context Initialization

To perform AES encryption and decryption, you must initialize an AES context. This context serves as a container for maintaining the encryption and decryption state.

```c
AES_CTX ctx;
```

### Initialize Encryption

To perform encryption, initialize the AES context and provide the encryption key and iv.

```c
AES_EncryptInit(&ctx, key, iv);
```



### Encryption Function

The AES encryption function allows you to encrypt a single blocks of data, and this implementation does not support padding. Ensure that you provide data blocks of precisely 16 bytes.

```c
AES_Encrypt(&ctx, plaintext, ciphertext);
```


### Initialize Decryption

To perform decryption, initialize the AES context with the same key used for encryption.

```c
AES_DecryptInit(&ctx, key, iv);
```

### Decryption Function

The AES decryption function allows you to decrypt a single blocks of data, and this implementation does not support padding. Ensure that you provide ciphertext blocks of precisely 16 bytes.

```c
AES_Decrypt(&ctx, ciphertext, plaintext);
```

### Encryption and Decryption Function Completion

After you have finished using the AES encryption and decryption functions and no longer require the AES context, it's essential to clear sensitive information from memory. Use the following function to achieve this:

```c
AES_CTX_Free(&ctx);
```


## Contributions

Contributions and feedback are welcome! If you find issues or have ideas for improvements, please open an issue or submit a pull request.

## License

This standard AES-256 CBC implementation is provided under the [MIT License](./LICENSE).

