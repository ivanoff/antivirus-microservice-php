![antivirus-microservice](./assets/logo2.png)

## Antivirus Microservice PHP Client

This is a PHP client for the free and fully functional [Antivirus Microservice Server](https://github.com/ivanoff/Antivirus-Microservice). It allows you to easily integrate virus scanning capabilities into your PHP applications.

## Table of Contents

- [Antivirus Microservice PHP Client](#antivirus-microservice-php-client)
- [Table of Contents](#table-of-contents)
- [Installation](#installation)
- [Usage](#usage)
- [API](#api)
- [Configuration](#configuration)
- [Error Handling](#error-handling)
- [Requirements](#requirements)
- [Contributing](#contributing)
- [License](#license)
- [Support](#support)
- [Created by](#created-by)

## Installation

You can install this package via Composer:

```bash
composer require ivanoff/antivirus-microservice
```

## Usage

Here's a basic example of how to use the Antivirus Microservice client:

```php
<?php

require_once 'vendor/autoload.php';

$antivirus = new AntivirusMicroservice('http://localhost:3000');
$result = $antivirus->checkFile('/path/to/your/file.txt');

if ($result['ok']) {
    echo "File is clean\n";
} else {
    echo "File is infected: " . implode(', ', $result['viruses']) . "\n";
}
```

## API

The `AntivirusMicroservice` class provides the following method:

- `checkFile($filePath)`: Scans the provided file for viruses. Returns an array with:
  - `ok`: boolean indicating whether the file is clean (`true`) or infected (`false`)
  - `viruses`: an array of detected virus names (only present if `ok` is `false`)

## Configuration

When initializing the `AntivirusMicroservice` class, you can specify the URL of your Antivirus Microservice server. By default, it uses `http://localhost:3000`.

```php
$antivirus = new AntivirusMicroservice('http://your-custom-url:port');
```

## Error Handling

The client handles basic errors:
- If the file is not found, it returns `['ok' => false, 'viruses' => ['File not found']]`.
- If there's an error communicating with the server, it returns `['ok' => false, 'viruses' => ['Error checking file']]`.

## Requirements

- PHP 7.0 or higher
- cURL extension enabled

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

This project is open-sourced software licensed under the [MIT license](https://opensource.org/licenses/MIT).

## Support

If you encounter any problems or have questions, please open an issue in the [project repository](https://github.com/ivanoff/antivirus-microservice-php).

## Created by

Dimitry Ivanov <2@ivanoff.org.ua> # curl -A cv ivanoff.org.ua
