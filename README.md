# Guide-for-Drupal-Site-Development-in-Docker-with-ddev


Before starting development of drupal site inside docker with ddev: <br>
we need to first know what docker is and what ddev is used for? <br><br>
<h3>In simple way:</h3>
<h2>Docker: </h2> Docker is like a magic box that packs everything an application needs (code, settings, tools) so it runs the same anywhere—on your computer, a server, or the cloud—without any setup headaches.<br> It's like carrying your kitchen with you so you can cook your favorite dish anywhere!
<br> Docker is a tool that packages the app + dependencies into a container that runs the same way on any system. It introduces the concept of containerization of applications.
<br><strong>Problem that docker solve: </strong> Often due to difference in OS and dependencies, missing libraries, we developers have a problem of our application failed running on another system. Now, docker solve this problem: If an application works inside a docker container on a developer's machine, it will work anywhere.<br><br>
<h2>Ddev: </h2>
DDEV is like a ready-to-use kitchen for web development—it sets up everything (Docker, databases, servers) so you can quickly start working on projects without manual setup<br>
Technically, DDEV is a tool that simplifies local development inside Docker using simple commands.🚀<br> It manage the complete setup and operation of a web application inside Docker.<br>
<b>DDEV wraps Docker, making it easy to:</b>
<br>

* Start and stop project environments. <br>

* Use built-in PHP, MySQL, and Apache/Nginx. <br>

* Manage different PHP versions per project.<br>

* Run CLI tools like Drush (for Drupal). <br>

Simply, using ddev simple commands we can easily develop our application inside docker. 🚀
<br><br>
Currently we would learn to start development of drupal website inside docker using ddev...<br><br>
<h2>Steps to starting drupal site development inside docker using ddev </h2> <br>

<b>Step1:</b> First we need to install docker desktop, ddev and enable wsl2 (for windows).<br>
* Docker runs natively on Linux (Ubuntu, Debian, Fedora, CentOS, etc.).<br>
* No need for virtualization since Docker uses Linux kernel features directly.
<br><br>
<h4>For running docker on Windows</h4>
* Docker requires WSL (Windows Sub system for Linux) or Hyper-V. <br><br>

So first using windows powershells in administrator mode,<br>
we will install:<br>
1. <b> chocolatey package installer</b> (if not installed, we can check using choco --version) <br>
Using: <br>
<code>Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
</code> <br>

2. <b>ddev</b> <br>
Using:<br>
<code>choco install ddev -y</code><br>
3. <b>Docker desktop: </b><br>
Using:<br>
<code>choco install docker-desktop -y</code><br>
After installation, we need to restart our system<br><br>

4. <b> Enable wsl</b><br>
Using: <br>
<code>wsl --install</code><br>
when we run <code>wsl --install</code>, it installs Ubuntu as the default Linux distribution in our system.<br><br>

<b>Step2:</b> Open Docker desktop app, and it will start the docker engine. <br>
<b>Step3:</b> Open Ubuntu.<br>
<b>Step4:</b> Create your drupal project.
<br>Steps:
<br> 1. Create a directory for storing your sites. using: <code>mkdir Sites cd Sites</code>
<br> 2. run <code> ddev config --project-type=drupal --docroot=web --php-version=<php_version_your_project_require> </code>
<br> [ It will setup the required environment for the drupal project that is  php, web server, database etc.
<br> And add a <b>web</b> and <b>ddev</b> directory in our project folder. </b>
<br> web will be the docroot of our project.
<br> and ddev will contain all the config file.
<br> In ddev there will be an important file <b>config.yaml</b>, that will store the all information about the project like db information, php version, web server info etc. 
<br> By default ddev add the database of project : db, username : db and password db ]
<br>
<br>3. Run <code>ddev start </code> 
<br> [ It will start a container for our project].
<br>
<br>4. Download a drupal site or clone from github repository. For downloading: run <code> ddev composer create drupal/recommended-project:^version</code>
<br>
<br> 5. Install Drush using composer. Using: <code>ddev composer require drush/drush</code>
<br> <b>Note:</b> For running any drush/composer command outside the container, we need to use ddev before the command.
<br>
<br> 6. Using drush, install your drupal site and set your admin username and password.
<br> Using: <code>ddev drush site:install --account-name=admin --account-pass=admin -y</code>
<br>[ It will install our drupal site and we will also get the url to open our site.
<br>
<b>Last Step</b>
<br> Run <code> ddev launch </code>
<br> [ This command open the browser and open our site there ]

<br><br><br>
<br>Opening phpmyadmin for accessing database.
<br>First we need to install phpmyadmin using: <code> ddev add-on get ddev/ddev-phpmyadmin </code>
<br>
<br>After installing phpmyadmin, we need to restart ddev using: <code>ddev restart</code>
<br> Then launch phpmyadmin using: <code>ddev launch phpmyadmin</code>

<br> <h4> Now our drupal site is installed and running successfully in docker container,</h4>
<br> Now we can install and use any required drupal themes/module using <code> ddev composer </code> or using drush <code> ddev drush </code> 







 



   















