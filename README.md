# Plutus Bitcoin Brute Forcer

Welcome to Plutus! This tool is designed to hunt for Bitcoin wallets that contain funds. It works by generating random private keys, converting them to addresses, and checking them against a database of known funded addresses.

# Like This Project? Give It A Star

[![](https://img.shields.io/github/stars/Isaacdelly/Plutus.svg)](https://github.com/Isaacdelly/Plutus)

## Installation

1.  **Install Python**: You need Python 3.9 or newer. [Download it here](https://www.python.org/downloads/).
2.  **Get the Code**:
    ```bash
    git clone https://github.com/Isaacdelly/Plutus.git plutus
    cd plutus
    ```
3.  **Install Requirements**:
    ```bash
    pip3 install -r requirements.txt
    ```

## Quick Start

To start the brute forcer with default settings (fastest mode), simply run:

```bash
python3 plutus.py
```

## Parameters & Options

You can customize how Plutus runs using command-line arguments.

### 1. Verbose Mode (`-v` or `--verbose`)
By default, Plutus runs silently and only shows a speed counter. If you want to see every single Bitcoin address being generated in real-time, use this flag.
*   **Usage**: `python3 plutus.py -v 1`
*   **Note**: This significantly slows down the program because printing to the screen takes time.

### 2. CPU Core Count (`-c` or `--cpu-count`)
Plutus uses **all available CPU cores minus one** by default. This ensures your computer remains responsive while the program runs. If you want to use a specific number of cores (or all of them), you can specify it here.
*   **Usage**: `python3 plutus.py -c 4` (Runs on 4 cores)

### 3. Speed Test (`time`)
Want to know how fast your computer generates a single address? Run the speed test.
*   **Usage**: `python3 plutus.py time`

### 4. Help (`help`)
Shows the help menu.
*   **Usage**: `python3 plutus.py help`

## How It Works

1.  **Generate**: The program creates a random 32-byte private key.
2.  **Convert**: It calculates the public key and the Bitcoin address (P2PKH).
3.  **Check**: It instantly checks if this address is in the database of funded wallets using a Bloom Filter (a super-fast memory structure).
4.  **Save**: If a match is found, the private key, public key, and address are saved to a file named `plutus.txt`.

## Expected Output

When running normally, you will see the database loading, followed by a live speed counter:
```
reading database files...
Progress: 100.00%
DONE
database size: 21568445
processes spawned: 15
Speed: 185000 keys/sec
```

If a wallet with money is found, it saves to `plutus.txt`:
```text
hex private key: 5A4F3F...
WIF private key: 5JW4RC...
public key: 04393B...
address: 1Kz2CT...
```

## Recent Improvements & TODO

<a href="https://github.com/Isaacdelly/Plutus/issues">Create an issue</a> so I can add more stuff to improve