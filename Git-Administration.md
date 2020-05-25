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
