# WordPress Development Stubs

A Composer package that provides PHP stubs for WordPress, WooCommerce, and Advanced Custom Fields (ACF) along with comprehensive PHP CodeSniffer rules for linting WordPress projects.

## What's Included

This package includes:

- **WordPress Core Stubs** (`php-stubs/wordpress-stubs`) - PHP stubs for WordPress 6.4+
- **WooCommerce Stubs** (`php-stubs/woocommerce-stubs`) - PHP stubs for WooCommerce 8.9+
- **ACF Pro Stubs** (`php-stubs/acf-pro-stubs`) - PHP stubs for Advanced Custom Fields 6.0+
- **WordPress Coding Standards** (`wp-coding-standards/wpcs`) - Official WordPress coding standards
- **PHP Compatibility** (`phpcompatibility/php-compatibility`) - PHP version compatibility checking
- **PHP CodeSniffer** (`squizlabs/php_codesniffer`) - The underlying code analysis tool

## Installation

Install this package as a development dependency in your WordPress project:

```bash
composer require --dev fwestdev/wp-stubs:dev-main
```

## Usage

### Running PHP CodeSniffer

After installation, you can run the linting tools using the provided Composer scripts:

```bash
# Check code for violations
composer run phpcs

# Automatically fix code violations (where possible)
composer run phpcbf
```

### Manual PHPCS Commands

You can also run PHPCS directly with custom options:

```bash
# Check specific files or directories
vendor/bin/phpcs path/to/your/files

# Check with specific standards
vendor/bin/phpcs --standard=WordPress path/to/your/files

# Generate a detailed report
vendor/bin/phpcs --report=full path/to/your/files
```

### IDE Integration

The stubs will automatically be available to your IDE's intellisense and static analysis tools. Popular IDEs like PhpStorm, VS Code (with PHP extensions), and others will recognize WordPress, WooCommerce, and ACF functions without requiring the actual plugins to be installed.

## Configuration

### Default Configuration

The package includes a pre-configured `phpcs.xml.dist` file that:

- Uses WordPress, WordPress-Extra, and WordPress-Docs coding standards
- Sets minimum PHP version to 8.0+
- Sets minimum WordPress version to 6.0+
- Includes custom rules for WooCommerce and ACF functions
- Excludes common directories (`vendor`, `node_modules`, `tests`, `build`, `dist`)
- Allows modern PHP syntax (short arrays, short ternary operators)

### Customizing for Your Project

To customize the configuration for your specific project:

1. Copy `phpcs.xml.dist` to `phpcs.xml`
2. Modify the rules as needed for your project
3. Update the prefixes in the `WordPress.NamingConventions.PrefixAllGlobals` rule
4. Adjust the text domain in the `WordPress.WP.I18n` rule

Example customization:

```xml
<!-- Update prefixes for your project -->
<rule ref="WordPress.NamingConventions.PrefixAllGlobals">
    <properties>
        <property name="prefixes" type="array">
            <element value="your_prefix"/>
            <element value="YourPrefix"/>
        </property>
    </properties>
</rule>

<!-- Update text domain -->
<rule ref="WordPress.WP.I18n">
    <properties>
        <property name="text_domain" type="array">
            <element value="your-text-domain"/>
        </property>
    </properties>
</rule>
```

## Benefits

### For Development

- **Improved IDE Support**: Get full autocomplete and documentation for WordPress, WooCommerce, and ACF functions
- **Static Analysis**: Catch errors before runtime without requiring WordPress installation
- **Code Quality**: Enforce WordPress coding standards automatically
- **PHP Compatibility**: Ensure your code works across different PHP versions

### For CI/CD

Perfect for continuous integration pipelines:

```yaml
# Example GitHub Actions workflow
- name: Install dependencies
  run: composer install --no-dev --optimize-autoloader

- name: Run PHPCS
  run: composer run phpcs
```

## Supported Versions

- **PHP**: 8.0+
- **WordPress**: 6.0+
- **WooCommerce**: 8.9+
- **ACF Pro**: 6.0+

## Contributing

If you find issues with the configuration or have suggestions for improvements, please open an issue or submit a pull request.

## License

This package configuration is open source. Please refer to the individual stub packages for their respective licenses:

- [WordPress Stubs](https://github.com/php-stubs/wordpress-stubs)
- [WooCommerce Stubs](https://github.com/php-stubs/woocommerce-stubs)  
- [ACF Pro Stubs](https://github.com/php-stubs/acf-pro-stubs)
- [WordPress Coding Standards](https://github.com/WordPress/WordPress-Coding-Standards)
