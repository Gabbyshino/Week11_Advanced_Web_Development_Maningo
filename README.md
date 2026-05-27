# Week11_Advanced_Web_Development_Maningo

# 🛡️ Anti-Hacker Lab

A hands-on web security lab demonstrating CSRF Protection and XSS Prevention using CodeIgniter 4.

## 📋 Lab Tasks Completed

| Task | Description | Status |
|------|-------------|--------|
| TASK 01 | Enable CSRF Filter in app/Config/Filters.php | ✅ |
| TASK 02 | Add CSRF Token to Form with <?= csrf_field() ?> | ✅ |
| TASK 03 | Escape User Output with <?= esc($data) ?> | ✅ |

## 🧪 How to Test

**Test TASK 01 - CSRF Filter Enabled**

1. Open app/Config/Filters.php
2. Check that 'csrf' is inside the $globals['before'] array
3. The code should look like this:

    public $globals = [
        'before' => [
            'csrf',
        ],
        'after' => [
            'toolbar',
        ],
    ];

**Test TASK 02 - CSRF Protection**

1. Open app/Views/form_view.php
2. Comment out <?= csrf_field() ?>
3. Submit the form → You will see a 403 Forbidden error
4. Uncomment the line to restore normal function

**Test TASK 03 - XSS Protection**

1. Type <b>John</b> in the Name field
2. Submit → Shows as plain text, NOT bold
3. Type <script>alert('XSS')</script> in the Comment field
4. Submit → No popup alert appears

## 🚀 Installation

    git clone https://github.com/YOUR_USERNAME/antihackerlab.git
    cd antihackerlab
    composer install
    cp env .env
    php spark serve

Then visit http://localhost:8080

## 📁 Project Structure

    antihackerlab/
    ├── app/
    │   ├── Config/
    │   │   ├── Filters.php
    │   │   └── Routes.php
    │   ├── Controllers/
    │   │   └── HomeController.php
    │   └── Views/
    │       └── form_view.php
    ├── public/
    │   └── index.php
    └── .env

## 💬 Discussion Questions

**Q1: Can CSRF attacks happen with GET requests?**

Yes. If a website uses GET requests to change data, attackers can hide malicious links in images or hyperlinks. When the victim clicks or loads them, the request goes through with their session cookies.

**Q2: What if an attacker guesses the CSRF token?**

Practically impossible. CSRF tokens use cryptographically secure random values with billions of possible combinations. An attacker would need more than a lifetime of non-stop guessing to find a valid token.

**Q3: Why isn't validating input enough to stop XSS?**

Input validation breaks legitimate user data. Output escaping is the reliable solution because it converts dangerous characters to harmless text regardless of what the user types.

## 🛠️ Technologies Used

- CodeIgniter 4
- PHP 7.4+
- HTML5 & CSS3

## 📄 License

MIT
