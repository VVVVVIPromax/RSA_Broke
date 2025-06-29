
# RSA Factoring Demonstrator

This repository contains a simple Python script that demonstrates the logic behind breaking RSA encryption by factoring its public modulus, `n`.

It is intended as an educational tool to visually answer the question: "If we know how RSA works, why can't we just reverse the process to break it?" This script succeeds on a miniature scale and, in doing so, powerfully illustrates why this same method is computationally impossible against modern, real-world RSA key sizes.

## The Concept

The security of the RSA algorithm relies on the fact that while it is easy for a computer to multiply two large prime numbers (`p` and `q`) together to get a public modulus (`n`), it is extraordinarily difficult to take `n` and find the original `p` and `q`. This is known as the **Integer Factorisation Problem**.

This script attempts to solve this problem using the most direct method imaginable: a brute-force attack.

## How It Works

The script operates in a few simple steps:

1.  **Define a Target**: A small, "insecure" RSA modulus `n` is hard-coded into the script. This number is the product of two 3-digit primes.
2.  **Generate Primes**: It generates a complete list of all prime numbers within a given range (e.g., all 3-digit primes from 100 to 999).
3.  **Brute-Force Search**: It iterates through every possible pair of primes from the list, multiplies them together, and checks if the product equals the target `n`.
4.  **Find Factors**: If a match is found, the script has successfully "cracked" the weak key and prints the two prime factors.

## How to Run

To run the demonstration on your own machine:

1.  **Clone the repository:**

    ```bash
    git clone https://github.com/your-username/your-repository-name.git
    ```

2.  **Navigate to the directory:**

    ```bash
    cd your-repository-name
    ```

3.  **Run the Python script:**

    ```bash
    python rsa_cracker_demo.py
    ```

    *(Assuming you have named the Python file `rsa_cracker_demo.py`)*

## Example Output

When you run the script, you will see the following output:

```
Step 1: Finding all 3-digit prime numbers (between 100 and 999)...
Done! Found 143 3-digit prime numbers. Time taken: 0.0031 seconds

Step 2: Starting brute-force attack. Target modulus n = 145919

Success! Cracked the RSA modulus 145919
Its prime factors are p = 317 and q = 461
Cracking process took: 0.0053 seconds
```

## The Crucial Lesson: Why This Can't Break Real RSA

The script succeeds in seconds because its target is tiny. A real-world **RSA-2048** key does not use 3-digit primes; it uses primes that are approximately **309 decimal digits** long.

Attempting to scale this script up to attack a 2048-bit key would fail for two fundamental reasons:

1.  **The Number of Primes is Astronomical**: The number of 309-digit prime numbers is estimated to be around **10³⁰⁶**. For context, the number of atoms in the observable universe is "only" about 10⁸⁰. You would not have enough storage in the world to even hold the list of prime numbers you need to check.

2.  **The Computation Time is Longer Than the Age of the Universe**: If you had the list of primes, the number of multiplication operations required would be roughly **10⁶¹²**. Even if you could harness the power of the world's fastest supercomputer, the time required to complete this calculation would exceed the age of the universe by an unimaginable margin.

This enormous gap between what is possible for a small number and what is possible for a large one is the entire basis for the security of modern public-key cryptography.

## License

This project is licensed under the MIT License - see the `LICENSE` file for details.

-----

**Suggestion:** For the `LICENSE` part, you can create another file in your repository named `LICENSE` (no extension) and paste the standard [MIT License text](https://opensource.org/licenses/MIT) into it. This is standard practice for open-source projects.
