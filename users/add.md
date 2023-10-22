Add a New User: Use the useradd command to create a new user named "hagrid".
Añadir un nuevo usuario: Utilice el comando useradd para crear un nuevo usuario llamado "hagrid".

sudo useradd -m hagrid

Set a Password: To set or change the password for the newly created user, use the 'passwd' command.
Establecer una contraseña: Para establecer o cambiar la contraseña del usuario recién creado, utilice el comando 'passwd'.

sudo passwd hagrid

You'll be prompted to enter a new password for "hagrid".
Se te pedirá que introduzcas una nueva contraseña para "hagrid".

Add User to the sudo Group: To grant "hagrid" sudo privileges, you can add them to the "wheel" group, which is often configured to allow members to execute any command. You can use the gpasswd or usermod command to add the user to the "wheel" group.
Añade el usuario al grupo sudo: Para conceder a "hagrid" privilegios sudo, puedes añadirlo al grupo "wheel", que suele estar configurado para permitir a sus miembros ejecutar cualquier comando. Puede utilizar el comando gpasswd o usermod para añadir el usuario al grupo "wheel".

sudo usermod -aG wheel hagrid

Configure sudo: Make sure that the "wheel" group is allowed to use 'sudo'. Edit the sudoers file using the 'visudo' command:
Configurar sudo: Asegúrate de que el grupo "wheel" tiene permiso para utilizar 'sudo'. Edita el archivo sudoers usando el comando 'visudo':

sudo visudo

Look for a line like this and uncomment it (remove the '#' at the beginning):
Busca una línea como esta y descoméntala (quita el '#' del principio):

# %wheel ALL=(ALL) ALL

to
en

%wheel ALL=(ALL) ALL

Save and exit the editor.
Guarde y salga del editor.

After completing these steps, your new user "hagrid" should be able to run commands with sudo privileges. Keep in mind that they will need to enter their own password to run commands with 'sudo'.
Después de completar estos pasos, tu nuevo usuario "hagrid" debería ser capaz de ejecutar comandos con privilegios sudo. Tenga en cuenta que tendrá que introducir su propia contraseña para ejecutar comandos con 'sudo'.
