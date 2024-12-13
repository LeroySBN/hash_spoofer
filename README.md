# Image Hash Spoof Tool

## Overview
The **Image Hash Spoof Tool** is a Python-based utility that modifies an image file to produce a cryptographic hash (e.g., SHA-512) with a specified hexadecimal prefix. The tool ensures that the visual appearance of the image remains unchanged to the human eye while altering the file to match the desired hash prefix.

## Features
- Modifies an image imperceptibly using least significant bit (LSB) adjustments.
- Supports SHA-512 hashing for secure and robust hash matching.
- Outputs an altered image that retains the original's visual quality.

## Requirements
- Python 3.7+
- Required Python libraries:
  - `Pillow`
  - `hashlib`

## Installation
1. Clone the repository or download the script:
   ```bash
   git clone https://github.com/LeroySBN/hash_spoofer.git
   cd hash_spoofer
   ```
2. Install the required Python libraries:
   ```bash
   pip install Pillow
   ```

## Usage
The tool is executed via the command line with the following syntax:

```bash
./spoof <hex_prefix> <input_image> <output_image>
```

### Parameters
- `<hex_prefix>`: The desired starting hexadecimal prefix of the hash (e.g., `0x24`).
- `<input_image>`: The path to the original image file.
- `<output_image>`: The path to save the modified image.

### Example
To modify `original.jpg` such that its SHA-512 hash starts with `0x24`, and save the result as `altered.jpg`:

```bash
./spoof 0x24 original.jpg altered.jpg
```

Upon completion, the script outputs:
- The modified image file: `altered.jpg`
- The matched hash for verification.

### Sample Output
```bash
Match found: 2448a6512f[...more bytes...]93de43f4b5b
Modified image saved as altered.jpg
```

## How It Works
1. The script adjusts the least significant bit of random pixels in the image to introduce subtle changes that are imperceptible to human vision.
2. After each modification, the script calculates the SHA-512 hash of the image.
3. This process repeats until the hash matches the specified prefix.

## Performance Considerations
- Matching a hash with a long prefix may require a significant number of iterations, increasing runtime.
- For better performance, shorter prefixes are recommended.

## Limitations
- The current implementation supports SHA-512 hashing but can be extended to other hash functions.
- Images with strict encoding (e.g., heavily compressed formats) may require additional handling.

## License
This project is licensed under the MIT License.

---

For questions or contributions, please feel free to open an issue or submit a pull request!
