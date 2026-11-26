# Fork Baseline & Local QA Notes

- **Upstream**: `https://github.com/jolicode/secret-santa`
- **Fork**: `https://github.com/dzjadzka/secret-santa`
- **Approved Baseline (`main`)**: `ac4aa537903993a114536c7bc6f06e6adbf99f12`

## Local Setup & QA

1. Use a symlink-capable checkout (Linux, WSL2, or container checkout) so `tools/bin/phpstan` and `tools/bin/php-cs-fixer` remain valid symlinks.
2. Build and start the local Docker stack:
   ```bash
   castor start
   ```
3. Run the canonical QA checks:
   ```bash
   castor qa:phpunit
   castor qa:phpstan
   castor qa:cs --dry-run
   castor qa:security-audit
   castor docker:builder -- bin/console lint:twig templates
   ```

## Safety Notes

- Do **not** run `castor deploy` from the fork; it pushes to the upstream Clever Cloud remote.
- Keep all tests and development runs strictly on synthetic data.
