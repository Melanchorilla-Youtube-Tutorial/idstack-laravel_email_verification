## Step buat app:

1. Install laravel

2. php artisan make:auth
   dan konfig mail di file .env

3. php artisan migrate
   php artisan make:migration add_activation_columns_to_users --table=users
   isi migration add_activation_columns_to_users
   php artisan migrate
   override LoginUsers.php ke LoginController.php (edit LoginController.php)

4. override RegisterUsers.php ke RegisterController.php (edit RegisterController.php)
   Buat folder di resources/views/layouts/ dengan nama "partials"
   beri nama \_alert.blade.php dan isi alert bootstrap

5. edit method create di RegisterController.php dan User.php
   buat event dengan perintah php artisan make:event Auth\\UserActivationEmail
   edit Event UserActivationEmail.php dan panggil di RegisterController.php
   buat listener dengan perintah php artisan make:listener Auth\\SendActivationEmail --event=Auth\\UserActivationEmail
   edit listener SendActivationEmail.php
   edit EventServiceProvider.php untuk me-list event yang baru dibuat

6. aktifkan fungsi email di laravel dengan perintah php artisan make:mail Auth\\ActivationEmail --markdown=emails.auth.activation
   edit activation.blade.php
   edit SendActivationEmail.php
   edit ActivationEmail.php
   buat controller dengan perintah php artisan make:controller Auth\\ActivationController
   list di routes web.php

7. Edit controller ActivationController.php
   (optional) edit model User.php dan controller ActivationController.php

8. buat controller baru dengan perintah php artisan make:controller Auth\\ActivationResendController
   edit controller ActivationResendController.php
   buat file views di resources\views\Auth\activate dengan nama file resend.blade.php
   copy login.blade.php dan paste di resend.blade.php dan edit
   buat routes baru web.php
   edit controller ActivationResendController.php

9. copy method resetPassword() dan sendResetResponse() di ResetsPasword.php ke ResetPasswordController.php
   edit ResetPasswordController.php
