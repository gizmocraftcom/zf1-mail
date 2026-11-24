# Changelog

## 2.0.0

Fork of `diablomedia/zendframework1-mail`, published as `gizmocraft/zendframework1-mail`.

### Breaking changes

- Requires PHP `>=8.5`. Tested on PHP 8.5 and 8.6.
- Package renamed from `diablomedia/zendframework1-mail` to `gizmocraft/zendframework1-mail`. It now requires `gizmocraft/zendframework1-exception` `^2.0.0`, `gizmocraft/zendframework1-config` `^3.0.0`, `gizmocraft/zendframework1-loader` `^2.0.0`, `gizmocraft/zendframework1-mime` `^2.0.0`, `gizmocraft/zendframework1-validate` `^2.0.0` and `gizmocraft/zendframework1-date` `^2.0.0`.

### Fixes for PHP 8.5 and 8.6

- `Zend_Mail_Storage_Writable_Maildir`: `readdir()` was called without the directory handle while computing the quota (deprecated since PHP 8.6, "Passing null"). The handle is passed now.
- `Zend_Mail_Storage_Writable_Maildir`: a blank line in `maildirsize` (the trailing newline) caused an "Undefined array key" warning and a `TypeError` (`int + string`) in the quota calculation. Blank lines are skipped.
- `Zend_Mail_Storage_Maildir`: `ctype_digit()` was called with `null` and `explode()` with a `null` string for Maildir file names without size or flags (deprecated). Both cases are guarded.
- `Zend_Mail_Transport_Sendmail`: the temporary error handler for `mail()` is restored in a `finally` block, also when `mail()` throws.
- No public signature changes.

### Other changes

- Dev dependencies upgraded (PHPUnit 13, PHPStan 2.3, php-cs-fixer 3.95, GrumPHP 2.27). Dropped `composer-require-checker`, which has no release for PHP 8.6.
- Tests migrated to PHPUnit 13 attributes (`#[Group]`, `#[DataProvider]`, `#[Depends]`, `#[DoesNotPerformAssertions]`).
- CI runs PHP 8.5 and 8.6.
