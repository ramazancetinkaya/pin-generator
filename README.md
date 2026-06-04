[![MIT License](https://img.shields.io/github/license/ramazancetinkaya/pin-generator?style=flat-square)](LICENSE)
[![GitHub issues](https://img.shields.io/github/issues/ramazancetinkaya/pin-generator?style=flat-square)](https://github.com/ramazancetinkaya/pin-generator/issues)
[![GitHub stars](https://img.shields.io/github/stars/ramazancetinkaya/pin-generator?style=flat-square)](https://github.com/ramazancetinkaya/pin-generator/stargazers)
[![GitHub forks](https://img.shields.io/github/forks/ramazancetinkaya/pin-generator?style=flat-square)](https://github.com/ramazancetinkaya/pin-generator/network/members)

## myp1n Secure PIN Generator

myp1n is an offline, browser-based PIN generator. It uses the Web Cryptography API to ensure cryptographically secure randomness and applies strict structural filters to reject sequential, repeating, or easily guessable patterns.

## Security Model and Filters

The application avoids predictable random number generators like Math.random() and instead uses window.crypto.getRandomValues(). Every generated PIN must pass specific validation filters before being displayed.

### 1. Global Filters (All PIN Lengths)

Cryptographic Randomness: Uses secure hardware-backed entropy to prevent algorithmic predictability.

- Direct Repeater Prevention: Blocks adjacent duplicate digits (e.g., rejecting xxyy or 1123).

- Sequential Sequence Prevention: Blocks ascending or descending runs (e.g., rejecting 1234 or 9876).

### 2. Strict 4-Digit Filters

Because 4-digit PINs have a small pool of options ($10,000$ combinations), additional restrictions are applied:

- Adjacent Distance Rule: The difference between any two adjacent digits must be 2 or more ($|x_i - x_{i+1}| \geq 2$). This blocks tight runs and patterns like 1289 or 4390.

- Unique Digits Only: All four digits must be different.

- Leaked PIN Blacklist: Matches candidates against a list of frequently guessed PINs (e.g., 2580, 1111, 1212, popular years) and discards matches.

### 3. Long-PIN Filters (6 to 16 Digits)

For longer PINs, rules are applied to prevent common human patterns:

- Digit Frequency Limits: Restricts how often any single digit can appear based on the total PIN length (capped at 25-30% of the length).

- Alternation Prevention: Rejects repeating patterns and symmetric blocks (e.g., rejecting 121212 or 345345).

## Operational Features

- No Network Activity: Runs strictly client-side. No data is stored, tracked, or sent to a server.

- Tactile Shuffling: A quick digit-rolling animation plays during generation. Controls are locked during this animation to prevent spamming.

- Overflow Management: PINs up to 16 digits scale and wrap in a scrollable display container. Users can scroll through the PIN using touch-drag, mouse-drag, A/D keys, or arrow keys.

## Installation

There are two methods to get this project up and running on your local machine.

### Prerequisites

- A modern web browser (Chrome, Edge, Firefox, Safari, etc.)
- Download [Git](https://git-scm.com/) *(optional, if you choose to clone the repository)*

### 1. Clone the Repository

If you have Git installed, you can clone the repository by following these steps:

1. Open your **terminal** or **command prompt**.

2. Run the following command:
   
    ```bash
    git clone https://github.com/ramazancetinkaya/pin-generator.git
    ```

4. Navigate into the project directory:

    ```bash
    cd pin-generator
    ```

### 2. Download as ZIP

If you prefer not to use Git, you can download the project as a ZIP file:

1. Go to the GitHub repository page in your web browser.
2. Click the green **"Code"** button at the top right of the repository's file list.
3. Select **"Download ZIP"** from the dropdown menu.
4. Once the ZIP file is downloaded, extract it to your desired location.

## Usage

This is a standard frontend project, so you can run it directly in your web browser without any complex setup or server configuration:

1. Open the project folder on your computer.
2. Locate the `index.html` file.
3. **Double-click** the `index.html` file to launch it in your default web browser.

*Alternative Method:* You can also drag and drop the `index.html` file directly into any open browser tab (Chrome, Firefox, Safari, Edge, etc.).

## Browser Compatibility

Tested and working on:
- Chrome (latest)
- Firefox (latest)
- Safari (latest)
- Edge (latest)
- Mobile browsers (iOS Safari, Android Chrome)

## Contributing

Contributions are welcome! Please feel free to submit a pull request or open an issue for any enhancements or bug fixes.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more details.

## Contact

Whether you need to report an issue, propose a new feature, require setup and integration guidance, or submit a security disclosure, please reach out directly:

📧 **Contact Email**: `ramazancetinkayasolutions@protonmail.com`
