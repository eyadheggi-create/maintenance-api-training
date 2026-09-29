# Maintenance API

Laravel 13, PHP 8.3, MySQL 8, Sanctum authentication.
API-only application. No Blade views.

## Commands

- Test: `php artisan test`
- Lint: `./vendor/bin/pint`
- Static analysis: `./vendor/bin/phpstan analyse`

## Structure

- Controllers are thin.
- Business logic belongs in `app/Actions/`.
- Every endpoint uses a Form Request in `app/Http/Requests/`.
- Every API response uses a Resource in `app/Http/Resources/`.
- Authorization uses Policies.
- Never place authorization checks directly in controllers.

## Rules

- Follow PSR-12.
- Run Pint before finishing a task.
- Every new endpoint requires a Feature test.
- Store timestamps in UTC.
- Expose dates through Resources using ISO 8601.
- Use validation in Form Requests, not Controllers.
- Business rules belong in Actions.
- Use Resources for API serialization.

## Prohibitions

- Never add Composer packages without approval.
- Never modify existing migrations.
- Create new migrations instead.
- Do not edit `database/migrations/0001_*`.
- Do not edit `config/sanctum.php`.
