## Git Administration

## Git Protocol

- Local Protocol
- Remote Protocol

## Git Local Protocol

- Can be used if team has access to a shared file mount
- Authentication and Authorization handled through filesystem permissions
- Can be inefficient if volumes are mounted remotely

### Cloning using the Git local Protocol

```
# Using path
git clone /var/repos/sample_project.git

# Using file protocol explictly
git clone file:///var/repos/sample_project.git
```

### Steps to test Git local protocol

```
mkdir -p server/repo.git
cd server/repo.git/
git --bare init
cd
git clone ~/server/repo.git/
cd repo
echo "New Project" >> README.md
git add .
git commit -m "Initial Commit"
git push origin master
```

## Git Remote Protocols

- _SSH Protocol_ - Enables remote communication for Git via SSH connection
- _HTTP/S Protocol_ - Enables remote communication for Git over HTTP or HTTPS
- _Git Protocol_ - Enables a specific protocol for Git via deamon on server

### Cloning using the Git SSH Protocol

```
# Using standard SSH syntax
git clone ssh://user@server:/repos/sample_project.git

# Using SCP-style syntax
git clone user@server:repos/sample_project.git
```

## Git HTTP/S Protocol

- Requires configuring a web server to serve Git repositories
- Encrypts traffic to and from the server if HTTPS is used
- Enables encrypted anonymous user access if desired
- Provides inefficient data transfer

### Cloning using the Git HTTP/S Protocol

```
# using HTTPS
git clone https://gitserver/repos/sample_project.git
```

## Git Protocol

- Provides the most efficient transfer of data between the client and the server
- Lacks authentication support
- Requires additional configuration over other protocol
- Does not encrypt traffic between the client and server
- Commonly used for public access to repositories

### Cloning using the Git Protocol

```
# using Git protocol
git clone git://gitserver/repos/sample_project.git
```

## Git SSH Protocol

- Utilizes SSH Authentication
- Does not require a Git specific deamon
- Encrypts all Git traffic to and from the server
- Requires an authenticated user
- Most used of all Git protocols

### Git SSH Configuration Approach

- Create a initial Repository - bare repository
- Decide Authentication Approach
- Configure Access for Users
- Configure SSH to Limit Access

### SSH Authentication Approach

- Multi-user Approach - Server user per Git users for authentication

```
git clone user@server:repos/sample_project.git
```

- Single User Approach - Single server user for all Git users for authentication

```
git clone git@server:repos/sample_project.git
```

- Using a single server user does not affect Git attribution
- Most of the Saas Git providers are using the single user approach
- Single user approach enables a single purpose user account for Git
- Users will authenticate using public keys for either approach

### Configure SSH Access

- Create client user account
- Create user for Git access on the server
- Push data to the Git server using the SSH protocol

### Git Client

```
# Add new user
sudo adduser tamilsweet

# Add the user to sudo group
sudo usermod -aG sudo tamilsweet

# Switch to new user
su - tamilsweet

# Set git configuration
git config --global user.name "Tamilmozhi Gunasekar"
git config --global user.email "tamilmozhi.gunasekar@gmail.com"

# Create ssh config dir
mkdir ~/.ssh
# Limit permissions
chmod 700 ~/.ssh

# Generate key to authenticate with server
ssh-keygen

# Copy public key
cat ~/.ssh/id_rsa.pub
```

### Git Server

```
# Create git user
sudo adduser git

# Add to sudoers group
sudo usermod -aG sudo git

# Switch to git user
su - git

# Create ssh directory
mkdir ~/.ssh
# Limit permissions
chmod 700 ~/.ssh

# Add the client key to authorized key list
vi ~/.ssh/authorized_keys
# Limit permission
chmod 600 ~/.ssh/authorized_keys

# Create folder for repo
mkdir repo1.git
cd repo1.git
# Create bare repository
git --bare init

# From client clone now
git clone git@serverIP:/home/git/repo1.git
```
