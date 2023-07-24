# How-to-deploy-Laravel-app-cPanel-the-right-way
Uploading and deployment of Laravel application to cPanel step by step guide.
1. Create new folder(laravelapp) in the root directory at the same level with public_html<br>
2. zip your project files and then upload to the laravelapp folder and unzip there except the public folder in your project
3. upload your public folder files to the public_html
4. change your index.php file content in the line 34 and 47 as follows:<br>
<code> 34:  require __DIR__.'/../laravelapp/vendor/autoload.php';</code><br>
<code> 47: $app = require_once __DIR__.'/../laravelapp/bootstrap/app.php';</code><br>
5. Check all your assets files are working well if not check the path and give correct path.
6. Create the database and user for it.
7. Give the credentials in the .env file and also change the app_url to your domain name and app_debug as follows: <br>
<code> APP_DEBUG=false
APP_URL=https://example.com 
DB_DATABASE=database
DB_USERNAME=dbuser
DB_PASSWORD=kH34Kf01@kd

</code>

        -------------------Done! Enjoy your application deployed successfully.-----------------------
# How to create symlink and link your Storage/app/public folder to your public_html/Storage folder.
1. Modify your filesyste.php file and check it in the repository. This file is located in your config folder of your project.<br>
2. If you can't run the artisan commands then you can create a rout as follows and run in your browser it will run the command to create link.<br>
<code> Route::get("/storage-link", function () {
    $targetFolder = storage_path("app/public");
    $linkFolder = $_SERVER['DOCUMENT_ROOT'] . '/storage';

    if (!is_link($linkFolder)) {
        symlink($targetFolder, $linkFolder);
        return '<h1>Storage linked successfully</h1>';
    } else {
        return '<h1>Storage link already exists</h1>';
    }
});     </code>

3. Now your Storage/app/public will be linked to your public_html/Storage folder and if your images or Storage directory is giving the persmission error then you must check your permission where for the Storage the permission should be 0777, for the sub folder 0755 and for the images and files 0644 should be the correct permissions to access.
   #Note
Check the files in the repository for more details.
   --------Done! Enjoy the show-------------- 
