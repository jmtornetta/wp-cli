# Readme
## Simple Installation
Ensure that you have php installed (e.g. through xampp) first!
### MacOS
Simply move the wp-cli.phar file to "/usr/local/bin/wp"
### Windows
Copy the wp-cli directory somewhere safe (e.g. /xampp/php/)
Add the wp-cli directory to your PATH
1. Hit the Windows button > type "path"
2. Select Edit System Environment Variables > Environment Variables... > System Variables 
3. Select Edit... > New > type in the location of your wp-cli directory (e.g. E:xampp\php\wp-cli\)
## Extended Installation
### MacOS
#### 1. Launch terminal and run commands:
```
curl -O https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar
php wp-cli.phar --info
chmod +x wp-cli.phar
sudo mv wp-cli.phar /usr/local/bin/wp
```
### Windows
#### 1. Setup a wp-cli directory
#### 2. Install wp-cli.phar to this directory
```
curl -O https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.pha
php wp-cli.phar --info
chmod +x wp-cli.phar
```
#### 3. Setup a wp-cli directory that contains:
##### wp-cli.phar (original file)
##### wp (for Git Bash)
```
#!/usr/bin/env sh

dir=$(d=${0%[/\\]*}; cd "$d"; pwd)
 
# See if we are running in Cygwin by checking for cygpath program
if command -v 'cygpath' >/dev/null 2>&1; then
   # Cygwin paths start with /cygdrive/ which will break windows PHP,
   # so we need to translate the dir path to windows format. However
   # we could be using cygwin PHP which does not require this, so we
   # test if the path to PHP starts with /cygdrive/ rather than /usr/bin
   if [[ $(which php) == /cygdrive/* ]]; then
       dir=$(cygpath -m $dir);
   fi
fi
 
dir=$(echo $dir | sed 's/ /\ /g')
"${dir}/wp-cli.phar" "$@"
```
##### wp.cmd (for CMD)
``` 
@ECHO OFF
php "%~dp0wp-cli.phar" %*
```
## Files
### wp
Shortcut file that initializes the "wp" alias command in Bash terminals for Windows, Linux and MacOS. Simply type "wp" in Terminal and you will be able to run wp-cli.
### wp.cmd
Shortcut file that initiallizes the "wp" alias command in CMD terminals for Windows. Simply type "wp" in Terminal and you will be able to run wp-cli.
### wp-cli.phar
The wp-cli file which contains the Wordpress Command Line commands.
