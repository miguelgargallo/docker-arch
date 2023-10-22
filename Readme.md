Open bash, got to the directory you want to create the Dockerfile and
Abre bash, ve al directorio donde quieres crear el Dockerfile y

```bash
nano Dockerfile
```

Here is the content of the Dockerfile
Este es el contenido del Dockerfile

```Dockerfile
# Use the base Arch Linux image
FROM archlinux:latest

# Update the system
RUN pacman -Syu --noconfirm

# Install necessary packages (like sudo, openssh, etc.)
RUN pacman -S --noconfirm sudo openssh

# Setup SSHD config to allow root login
RUN echo 'PermitRootLogin yes' >> /etc/ssh/sshd_config
RUN echo 'root:root' | chpasswd

# Setup SSH keys (required for SSH to work)
RUN ssh-keygen -A

# Expose the SSH port
EXPOSE 22

# Setup a permanent volume
VOLUME ["/mydata"]

# Run the SSH server
CMD ["/usr/sbin/sshd", "-D"]
```

Build it
Constrúyelo

```bash
    docker build -t my_arch_machine .
```

Run it
Arráncalo

```bash
docker run --name arch_container -p 2222:22 -v $(pwd):/mydata -d my_arch_machine
```

Enter with your bash
Entro con tu bash

```bash
ssh root@localhost -p 2222
```

```bash
(password input) root
```
