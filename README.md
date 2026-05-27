# Week11_Advanced_Web_Development_Maningo

# 🛡️ Anti-Hacker Lab

A hands-on web security lab demonstrating **CSRF Protection** and **XSS Prevention** using CodeIgniter 4.

## 📋 Lab Tasks Completed

| Task | Description | Status |
|------|-------------|--------|
| TASK 01 | Enable CSRF Filter in `app/Config/Filters.php` | ✅ |
| TASK 02 | Add CSRF Token to Form with `<?= csrf_field() ?>` | ✅ |
| TASK 03 | Escape User Output with `<?= esc($data) ?>` | ✅ |

## 🧪 How to Test

### Test CSRF Filter Enabled (TASK 01)
1. Open `app/Config/Filters.php`
2. Check that `'csrf'` is inside the `$globals['before']` array
3. The code should look like this:
///```php
public $globals = [
    'before' => [
        'csrf',
    ],
    'after' => [
        'toolbar',
    ],
]; ///

### Test CSRF Protection (TASK 02)
1. Open `app/Views/form_view.php`
2. Comment out `<?= csrf_field() ?>`
3. Submit the form → You'll see a **403 Forbidden** error
4. Uncomment the line to restore normal function

### Test XSS Protection (TASK 03)
1. Type `<b>John</b>` in the Name field
2. Submit → Shows as plain text, NOT bold
3. Type `<script>alert('XSS')</script>` in the Comment field
4. Submit → No popup alert appears

## 🚀 Installation

///bash
git clone https://github.com/YOUR_USERNAME/antihackerlab.git
cd antihackerlab
composer install
cp env .env
php spark serve///
