# How-to-deploy-Laravel-app-cPanel-the-right-way
Uploading and deployment of Laravel application to cPanel step by step guide.
1. Create new folder(laravelapp) in the root directory at the same level with public_html<br>
2. zip your project files and then upload to the laravelapp folder and unzip there except the public folder in your project
3. upload your public folder files to the public_html
4. change your index.php file content in the line 34 and 47 as follows:
5.34: <code> require __DIR__.'/../laravelapp/vendor/autoload.php';<br> 47: $app = require_once __DIR__.'/../laravelapp/bootstrap/app.php';<br>
        -------------------Enjoy your application deployed successfully.-----------------------
