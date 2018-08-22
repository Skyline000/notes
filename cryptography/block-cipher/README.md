# Block Cipher

![](../../.gitbook/assets/image%20%284%29.png)

* A block cipher takes a block of plaintext and a secret key, produces a block of ciphertext. 
* The key is _**reused**_ for different plaintext blocks 
* Typical block sizes: 64 bits, 128 bits, 192 bits, 256 bits 
* Key sizes: 56 bits \(DES\), 128/192/256 bits \(AES\) 
* Popular block ciphers: DES, 3DES, AES, Twofish, Serpent

## Properties of good block cipher algorithms

### Confusion

* A small change in the key should be able to change 50% of the ciphertext 
* An attacker using a bruteforce attack shouldn’t receive any signs that he is getting closer to the correct key

### Diffusion

* A small change in the plaintext should cause 50% of the ciphertext to change 
* Hide any statistical relation between the plaintext and the ciphertext

### Completion

* Each bit of the ciphertext depends on each bit of the key 
* The attacker won’t be able to find valid parts of the key using divide and conquer methods



## Example

{% page-ref page="des-data-encryption-standard.md" %}

{% page-ref page="3des-triple-des-and-desx.md" %}

{% page-ref page="aes-advanced-encryption-standard.md" %}

{% page-ref page="electronic-codebook-ecb-mode.md" %}

{% page-ref page="cipher-block-chaining-cbc-mode.md" %}

{% page-ref page="counter-mode-ctr-mode.md" %}

{% page-ref page="cipher-feedback-mode-cfb.md" %}

